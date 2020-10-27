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
## I. Lệnh awk  

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
## II. Lệnh ps  

- Lệnh **ps** được sử dụng để liệt kê và hiển thị tất cả các tiến trình đang chạy trên hệ thống kèm với các thông số có sẵn.  
- Ta có thể sử dụng các [option] để lọc ra các tiến trình theo điều kiện của tính trình. Cú pháp của lệnh `ps` như sau:  
` ps [option] `  
- Dưới đây là lệnh chi tiết: 
 
<img src="https://i.imgur.com/DVVJewZ.png">  

Trên đây ta có thấy `PID` chính là ID của tiến trình, `TTY` là thông tin loại terminal mà người dùng sử dụng để đăng nhập, `TIME` chính là thời gian sử dụng CPU, `CMD` là lệnh dùng để khởi động tiến trình đó.  

- Khi thêm option `-ef` vào thì chúng ta sẽ có tất cả các tiến trình đang có trên hệ thống:  

<img src="https://i.imgur.com/OYdQ7nh.png">  

- Ta có thể sử dụng [option] để lọc theo Username, tên tiến trình, ID tiến trình, ... Đây là ví dụ lọc theo username `root`:  

<img src="https://i.imgur.com/4Q5QMZQ.png">  

- Thực hiện hiển thị ra một số cột cần thiết như `pid, ppid, cmd` với option như sau:  

<img src="https://i.imgur.com/w9AVExJ.png">  

<a name="dig"></a>  
## III. Lệnh dig  

- Lệnh **dig** dùng để truy vấn thông tin về máy chủ tên miền DNS. Những thông tin này có thể là `host addresses, mail exchanges hay name servers`, ...  

- Cú pháp của lệnh `dig`: 
` dig [server]`  

- Thử truy vấn dữ liệu với tên miền `google.com` :  

<img src="https://i.imgur.com/cU1vJkK.png"></a>  

- Phân tích kết quả trả về ta nhận được một số thông tin như sau: 
	> Dòng đầu tiên sẽ hiển thị thông số phiên bản dig mà chúng ta đang sử dụng  
	> Dòng số 2 sẽ hiển thị các tùy chọn đối với truy vấn hiện tại (mặc định chỉ có +cmd)    
	> Dòng tiếp theo hiển thị opcode, trạng thái truy vấn không xảy ra lỗi **NOERROR**, và ID của chính truy vấn  
	> Phần ANSWER SECTION sẽ cung cấp cho chúng ta tên bản ghi mà `dig` yêu cầu (ở đây là bản ghi A), tên miền là `google.com` và địa chỉ IP ứng với tên miền đó  
	> Phần cuối cùng sẽ hiển thị các thông số liên quan tới truy vấn như thời gian của truy vấn, ngày giờ thực hiện truy vấn, ..

- Nếu thêm tùy chọn `+short` vào phía sau câu truy vấn, ta sẽ chỉ được địa chỉ IP tương ứng với tên miền:  

<img src="https://i.imgur.com/wwp91y1.png">  

- Nếu thêm tùy chọn `+noall` sẽ tắt tất cả các section được hiển thị, sau đó ta thêm tùy chọn `+section` để hiển thị mỗi thành phần ANSWER SECTION liên quan đến tên miền:  

<img src="https://i.imgur.com/xGliJds.png">  

- Ta có thể sử dụng tùy chọn `-f` để import 1 file đầu vào chứa danh sách các tên miền và thực hiện truy vấn hàng loạt:  

<img src="https://i.imgur.com/FLyhiA6.png">  

<a name="trteewccut"></a>  
## IV. Lệnh tr, tee, wc, cut  

<a name="tr"></a>
### 1. Lệnh tr  

- Lệnh **tr** sẽ được dùng để thay thế, xóa bỏ hay dịch các kí tự trong Linux.  
- Cú pháp đơn giản của lệnh tr như sau:  

`tr [option] [s1] [s2]`  

- Nếu như không có [option] thì mặc định các kí tự s1 sẽ được lần lượt thay thế bằng các kí tự s2.

- Ví dụ về thay đổi tất cả các kí tự thường bằng các kí tự in hoa tương ứng : 

<img src="https://i.imgur.com/OEDsEQ5.png">  

- Thay đổi chữ thường bằng chữ in hoa trong một file bất kỳ bằng cách kết hợp lệnh cat và lệnh tr :  

<img src="https://i.imgur.com/S2VGTZO.png">  

- Để xóa 1 kí tự trong chuỗi ta có thể sử dụng thêm option -d vào : 

<img src="https://i.imgur.com/YD34gQi.png">  

<a name="tee"></a>  
### 2. Lệnh tee  

- Lệnh **tee** được dùng để lấy dữ liệu đầu vào từ STDIN, sau đó hiển thị dữ liệu SDTOUT ra màn hình và lưu lại trong file mà người dùng chỉ định.  
- Cú pháp của lệnh **tee** như sau:  

`tee [option] [file]`  

- 