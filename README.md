# Những lệnh cơ bản cần hiểu rõ trên Linux

## Mục lục
  
[I. Lệnh awk](#awk)

[II. Lệnh ps](#ps)  

[III. Lệnh dig](#dig)  

[IV. Lệnh tr, tee, wc, cut](#trteewccut)  
- [1. Lệnh tr](#tr)
- [2. Lệnh tee](#tee)
- [3. Lệnh wc](#wc)
- [4. Lệnh cut](#cut)  

[V. Lệnh grep](#grep)  

[VI. Lệnh sed](#sed)


===============================  

<a name="awk"></a>  
# I. Lệnh awk  

- Lệnh **awk** dùng để tìm kiếm và xử lý dữ liệu văn bản trên Linux. Câu lệnh có đầu vào bao gồm 1 `pattern` là biểu thức chính quy, 1 `file input` đầu vào và 1 `action` là hành động thực hiện trên file đó dựa trên `pattern`.
- Cấu trúc của lệnh `awk`:  
`awk pattern action file`  
- Lệnh này có thể hoạt động trên nhiều cột và nhiều dòng dữ liệu cũng như nhiều file đầu vào.
- Cách lệnh `awk` hoạt động:  
```
 - Lệnh đọc dữ liệu từ file đầu vào từ trên xuống dưới. Sau đó khi dòng nào có dữ liệu trùng khớp với `pattern` thì lệnh sẽ thực hiện `action`. Nếu khi tìm hết tất cả các dòng rồi mà không có `pattern` nào được tìm thấy thì sẽ không có `action` nào được thực hiên. 
 - Bắt buộc phải có ít nhất một trong hai thành phần là `pattern` hoặc `action`. Nếu không có `pattern` thì nó sẽ thực hiện đối với từng dòng dữ liệu còn nếu không có `action` thì lệnh sẽ in tất cả các dòng có chứa `pattern`.
```

- Thực hiện một ví dụ in ra tất cả các dòng của `file data.txt`. Nếu không có `pattern` thì lệnh `awk` mặc định sẽ giống như lệnh `cat` :  
<img src="https://i.imgur.com/xOL5Sp3.png">  
- Tìm kiếm với 'pattern' là $1=="1" và in tất cả những dòng có điều kiện thỏa mãn yêu cầu này. Kết quả có 1 dòng thỏa mãi STT= 1 :   
<img src="https://i.imgur.com/BJvAHRP.png">  
- Dùng điều kiện so sánh để tìm ra học sinh có học phí cao hơn 6.000.000 đồng. Chúng ta sẽ bỏ action `print` cũng vẫn được:  
<img src="https://i.imgur.com/ZpDfJIV.png">
- Nếu không muốn in ra tất cả các dòng thì ta thực hiện như sau để chỉ in ra một số dòng cần thiết:  
<img src="https://i.imgur.com/wVCJKE9.png">  

<a name="ps"></a>
# II. Lệnh ps  

- Lệnh **ps** được sử dụng để liệt kê và hiển thị tất cả các tiến trình đang chạy trên hệ thống kèm với các thông số có sẵn.  
- Ta có thể sử dụng các [option] để lọc ra các tiến trình theo điều kiện của tính trình. Cú pháp của lệnh `ps` như sau:  
` ps [option] `  
- Dưới đây là lệnh chi tiết:  
<img src="https://i.imgur.com/DVVJewZ.png">  
- Trên đây ta có thấy `PID` chính là ID của tiến trình, `TTY` là thông tin loại terminal mà người dùng sử dụng để đăng nhập, `TIME` chính là thời gian sử dụng CPU, `CMD` là lệnh dùng để khởi động tiến trình đó.
- Khi thêm option `-ef` vào thì chúng ta sẽ có tất cả các tiến trình đang có trên hệ thống:  
<img src="https://i.imgur.com/OYdQ7nh.png">  
- Ta có thể sử dụng [option] để lọc theo Username, tên tiến trình, ID tiến trình, ... Đây là ví dụ lọc theo username `root`:  
<img src="https://i.imgur.com/4Q5QMZQ.png">  
- Thực hiện hiển thị ra một số cột cần thiết như `pid, ppid, cmd` với option như sau:  
<img src="https://i.imgur.com/w9AVExJ.png">  

<a name="dig"></a>  
III. Lệnh dig  

- Lệnh **dig** dùng để truy vấn thông tin về máy chủ tên miền DNS. Những thông tin này có thể là `host addresses, mail exchanges hay name servers`, ...  
- Cú pháp của lệnh `dig`: 
` dig [server]`  
- Thử truy vấn dữ liệu với tên miền `facebook.com` :  
<img src="https://i.imgur.com/LeQ85Sq.png"></a>  
- Phân tích kết quả trả về ta nhận được một số thông tin như sau: 
	> 





