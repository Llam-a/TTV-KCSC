Mở đầu challenge cho ta trang web sumbit tên trainer, và chọn 1 trong 3 pokemon.

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/f71cfb04-e4f9-475b-bdb1-96ff92bfaa9f)

Sau đó mình view source code:

![Screenshot 2023-12-17 163831](https://github.com/Llam-a/TTV-KCSC/assets/115911041/39bdb31e-f9dc-42a3-bdfb-00c1d46ff05d)

Ở file champion.php, nó kiểm tra xem có tồn tại cookie có tên "trainer_data" hay không bằng cách sử dụng hàm isset().Tiếp theo nó gán giá trị của $_COOKIE["trainer_data"] vào biến $base64Encoded, sau đó dùng hàm base64_decode để giải mã chuỗi base64 trong biến $base64Encoded và lưu trong biến $serializedUser.Dùng hàm unserialize() để chuyển đổi chuỗi đã giải mã $serializedUser thành đối tượng của Trainer.Cuối cùng sử dụng hàm isChampion để kiểm tra xem đối tượng $user có phải là một nhà vô địch hay không.Nếu đúng thì nó lấy từ đối tượng $user thông qua phương thức getname() và cho ra chuỗi KCSC flag.

Tiếp theo mình kiểm tra file trainer.php, bởi vì ở file trước nó dùng hàm unserialize() để chuyển thành đối tượng của trainer.

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/9800428d-6d17-4c2d-a4ba-6f4bf4862e01)

Mình chú ý tới method magic __construct() tạo cho lớp "Trainer". Phương thức khởi tạo này được gọi mỗi khi một đối tượng mới của lớp "Trainer" được tạo ra. Phương thức này chấp nhận hai tham số là "$name" và "$starter" và gán giá trị của các tham số này cho các thuộc tính tương ứng của đối tượng được tạo.Vậy thì ta chỉ cần tạo 1 chuỗi serialize có `isChampion : True` là ta có thể xem đối tượng `$user` là nhà vô địch.

Bây giờ ta phải ghi đè qua cookie của challenge bằng cách là base64 cái chuỗi serialize mà ta tạo ra gồm các trường được tạo ra trong lớp Trainer.

source code:

```php
<?php 
class Trainer{
    public $name = "lama";
    public $starter = "Charmander";
    public $isChampion = "True";
}

$a = new Trainer();
echo serialize($a);
?>
//output:O:7:"Trainer":3:{s:4:"name";s:4:"lama";s:7:"starter";s:10:"Charmander";s:10:"isChampion";s:4:"True";}
```

Sau đó ta đem chuỗi đó encode sang base64

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/24951282-8921-40e8-aa95-65ea6c04d548)

Cuối cùng sumbit thử rồi sửa lại cookie, là có được flag.

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/2373cb09-1d8e-474c-a0af-fb236d6f95ae)

Hoặc nếu đơn giản hơn bạn có thể đổi giá trị của cookie sau khi decode như sau.Đổi ở chỗ isChampion từ `b:0` sang `b:1` nghĩa là thành true. Sau đó chỉ việc encode lại chuỗi serialize thành base64 eidt lại cookie là xong.

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/7906d0f0-1f0e-4ffc-9dc4-b2c678634a61)






