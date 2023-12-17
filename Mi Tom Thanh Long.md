Challenge cho ta trang web về MÌ TÔM THANH LONG.

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/297f03f4-6528-46fb-8fad-d6ddc40a00b7)

Bài này ko có gì đặc biệt, mình dùng tool dirsearch để scan file và phát hiện ra có file `flag.txt` sau đó wget rồi lấy flag thôi.

Hoặc có thể sử dụng theo cách lfi, ban đầu test thử đề dò file `../../../etc/payload` thì xuất hiện thông báo lỗi 

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/5d8b2923-a5c9-4729-833f-6db56322c8e6)

Tiếp theo mình sử dụng php wrapper để đọc flag

Payload:`?page=php://filter/convert.base64-encode/resource=pages/flag.php`

Kết qua cho ra chuỗi base64, đem đi decode ta được flag

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/510b2880-a1cf-4ca6-8ece-9e7b915bd64f)

