Challenge này cho ta một trang web blank chỉ có title KCSC hello fen, guest.

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/4b79d98b-9238-4649-963d-241af0fafdba)

Sau đó thì mình dirsearch ra

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/e79885c2-3b65-4913-af65-af00d8a0b2d5)

Có 3 file mình để ý. Đầu tiên với flag.php, nhưng sau khi thử thì ko có gì, còn với file `composer.json` cho ta biết web đang được build bằng framework `smarty v4.3.4`, vậy trang web này bị lỗi ssti.Tiếp tục check các file khác. Với file robots.txt cho ra content là `?source`, theo đó ta được source code của bài. Các bạn phải sử dụng burp suite mới có thể thấy được.

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/09710cdf-4d7a-4dec-8d5e-f76214c30c5b)

Đế ý phần đầu nó include nội dung từ hai tệp flag1.php và flag2.php, sau đó thì flag1 được định nghĩa một hằng số có tên là FLAG1 với giá trị bằng với giá trị của biến $flag1 thông qua hàm define().Vậy thì ta chỉ cần làm cho nó xuất hiện content của `FLAG1` thông qua tham số name

Payload: `http://103.162.14.116:10007/?name={FLAG1}`

![image](https://github.com/Llam-a/TTV-KCSC/assets/115911041/5de94b91-14bf-4cc1-90dd-ac80c576d799)
