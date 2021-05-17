1. Bài toán mà bài báo giải quyết là gì? Minh hoạ input/output (tìm hình ảnh có trong bài báo để minh hoạ)

 + Shot segmentation
 
 ![ảnh](https://user-images.githubusercontent.com/68372495/118488254-c1623f80-b745-11eb-8a6d-deb28bfdf925.png)

  
2. Các câu hỏi đặt ra là gì? Đã giải quyết được đến đâu?

 + Các phương pháp hiện  không tận dụng được hết cấu trúc video và thường dẫn đến kết quả phân đoạn cảnh quay không đúng. Sự phân đoạn không chính xác gây ra hỗn loạn thông tin, tức là mất thông tin của một cảnh quay nhất định và hỗn hợp thông tin của một số cảnh quay liền kề, làm hỏng tính toàn vẹn và độc lập của các hoạt động trong video.
 (Phương pháp Long Single LSTM)
 
 + Để cải tiến khắc phục các vấn đề trên, Nhóm phát minh ra trượt 2 chiều (sliding bidirectional LSTM) sử dụng Hierarchical Structure-Adaptive RNN (HSA-RNN) có thể cùng khai thác cấu trúc video và tóm tắt nội dung video.
 + Kết quả trên bốn bộ dữ liệu phổ biến, tức là SumMe [12], TVum [29], CoSum [5] và VTW [35], đã chứng minh rằng phương pháp của chúng tôi cải thiện đáng kể hiệu suất trên phân đoạn cảnh quay và tóm tắt video. Tăng thêm từ 9.3% đến 14.2% so với trung bình các giải pháp hiện có.
 
 3. Ý tưởng giải quyết là gì? Minh hoạ trực quan (diễn giải bằng lời hoặc hình ảnh)
  + Chia để trị.


  ![ảnh](https://user-images.githubusercontent.com/68372495/118488905-6a109f00-b746-11eb-85fe-0bbefbf1058d.png)


Bài báo cáo:
TRƯỢT 2 CHIỀU LSTM ĐỂ TÌM RA CÁC CẢNH QUAY

Cảnh quay là đơn vị cơ bản để mọi người hiểu các hoạt động trong video.
Segment cảnh quay.

Video được phân đoạn thành các cảnh chỉ đơn giản bằng 
1.	sự thay đổi đột ngột giữa các khung hình
2.	độ lệch độ lớn chuyển động hoặc
3.	độ dài cố định
 
Các phương pháp này không tận dụng được hết cấu trúc video và thường dẫn đến kết quả phân đoạn cảnh quay không đúng. Sự phân đoạn không chính xác gây ra hỗn loạn thông tin, tức là mất thông tin của một cảnh quay nhất định và hỗn hợp thông tin của một số cảnh quay liền kề, làm hỏng tính toàn vẹn và độc lập của các hoạt động trong video.
(Phương pháp Long Single LSTM)

Để cải tiến khắc phục các vấn đề trên, Nhóm phát minh ra trượt 2 chiều (sliding bidirectional LSTM) sử dụng Hierarchical Structure-Adaptive RNN (HSA-RNN) có thể cùng khai thác cấu trúc video và tóm tắt nội dung video.

Kết quả trên bốn bộ dữ liệu phổ biến, tức là SumMe [12], TVum [29], CoSum [5] và VTW [35], đã chứng minh rằng phương pháp của chúng tôi cải thiện đáng kể hiệu suất trên phân đoạn cảnh quay và tóm tắt video. Tăng thêm từ 9.3% đến 14.2% so với trung bình các giải pháp hiện có.

Chi tiết

2 giai đoạn (2 lớp): 

Lớp đầu tiên được phát triển để khai thác cấu trúc video. Cụ thể tìm ra các cảnh khác nhau. (shots boundaries). 
LSTM hai chiều có độ dài cố định hoạt động trên các khung hình video theo cách trượt và cố gắng phát hiện các ranh giới cảnh quay theo từng bước (sải chân ở mỗi bước bằng với độ dài của ảnh được phát hiện trước đó). 
Trong ví dụ ở Figure 2 độ dài cố định là 4.
Một khi Các ranh giới của cảnh quay được phát hiện, các trạng thái ẩn tương ứng với các vị trí của cảnh được lấy làm đặc điểm của cảnh. 
Trong ví dụ của Figure 2 thì có 3 shots boundaries, ở boundaries 1 thì frame 3 là đặc điểm chính. Tương tự là 2 cho shots boundaries 2 và 3 cho shot boundaries 3.
Kế thừa Long Single LSTM để segment ra các boundaries.
Cụ thể được nói ở 3.1 Video Structure Exploitation

Lớp thứ hai được thiết kế để nắm bắt sự phụ thuộc thời gian tiến-lùi giữa các cảnh và dự đoán xác suất của mỗi cảnh có được lựa chọn vào tóm tắt hay không.
Cụ thể được nói ở 3.2. Structure-Adaptive Video Summarization

 

Nói thêm:
Trong Tóm tắt Video thì có 2 dạng là có giám sát và không giám sát.
Không gíam sát là dùng heurstics (theo tính đại diện và đa dạng) để tìm ra các cảnh quan trọng. Tổng hợp tính chất giống nhau của cảnh quay thành 1 cụm và tóm tắt trên các cụm.
Giám sát là dùng thêm các bản tóm tắt có sẵn do con người tạo ra (như nội dung tóm tắt, subtile,..) để tìm ra các cảnh quay và sử dụng điểm đánh giá các cảnh. Điểm càng cao sẽ đưa vào tóm tắt.

Phương pháp nhóm tiếp cận là Không giám sát (non supervised).



![image](https://user-images.githubusercontent.com/42732113/118496989-d7c0c900-b74e-11eb-94b7-74792873b59e.png)

