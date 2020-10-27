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
I. Lệnh awk  

- Lệnh `awk` dùng để tìm kiếm và xử lý dữ liệu văn bản trên Linux. Câu lệnh có đầu vào bao gồm 1 `pattern` là biểu thức chính quy, 1 `file input` đầu vào và 1 `action` là hành động thực hiện trên file đó dựa trên `pattern`.
- Cấu trúc của lệnh `awk`:  
`awk pattern action file`  
- Lệnh này có thể hoạt động trên nhiều cột và nhiều dòng dữ liệu cũng như nhiều file đầu vào.
- Cách lệnh `awk` hoạt động:  
```
 - Lệnh đọc dữ liệu từ file đầu vào từ trên xuống dưới. Sau đó khi dòng nào có dữ liệu trùng khớp với `pattern` thì lệnh sẽ thực hiện `action`. Nếu khi tìm hết tất cả các dòng rồi mà không có `pattern` nào được tìm thấy thì sẽ không có `action` nào được thực hiên. 
 - Bắt buộc phải có ít nhất một trong hai thành phần là `pattern` hoặc `action`. Nếu không có `pattern` thì nó sẽ thực hiện đối với từng dòng dữ liệu còn nếu không có `action` thì lệnh sẽ in tất cả các dòng có chứa `pattern`.
```

- Thực hiện một ví dụ in ra tất cả các dòng của `file data.txt`. Nếu không có "pattern' thì lệnh `awk` mặc định sẽ giống như lệnh `cat` :  
<img src="https://i.imgur.com/xOL5Sp3.png">  


