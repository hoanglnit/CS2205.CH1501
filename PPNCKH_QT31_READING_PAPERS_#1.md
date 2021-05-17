1. Bài toán mà bài báo giải quyết là gì? Minh hoạ input/output (tìm hình ảnh có trong bài báo để minh hoạ)

 + Shot segmentation
 
 ![ảnh](https://user-images.githubusercontent.com/68372495/118488254-c1623f80-b745-11eb-8a6d-deb28bfdf925.png)

  
2. Các câu hỏi đặt ra là gì? Đã giải quyết được đến đâu?

 + Các phương pháp này không tận dụng được hết cấu trúc video và thường dẫn đến kết quả phân đoạn cảnh quay không đúng. Sự phân đoạn không chính xác gây ra hỗn loạn thông tin, tức là mất thông tin của một cảnh quay nhất định và hỗn hợp thông tin của một số cảnh quay liền kề, làm hỏng tính toàn vẹn và độc lập của các hoạt động trong video.
 (Phương pháp Long Single LSTM)
 
 + Để cải tiến khắc phục các vấn đề trên, Nhóm phát minh ra trượt 2 chiều (sliding bidirectional LSTM) sử dụng Hierarchical Structure-Adaptive RNN (HSA-RNN) có thể cùng khai thác cấu trúc video và tóm tắt nội dung video.
 + Kết quả trên bốn bộ dữ liệu phổ biến, tức là SumMe [12], TVum [29], CoSum [5] và VTW [35], đã chứng minh rằng phương pháp của chúng tôi cải thiện đáng kể hiệu suất trên phân đoạn cảnh quay và tóm tắt video. Tăng thêm từ 9.3% đến 14.2% so với trung bình các giải pháp hiện có.
 
 3. Ý tưởng giải quyết là gì? Minh hoạ trực quan (diễn giải bằng lời hoặc hình ảnh)
  + Chia để trị.


  ![ảnh](https://user-images.githubusercontent.com/68372495/118488905-6a109f00-b746-11eb-85fe-0bbefbf1058d.png)
