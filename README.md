# StudyPath---Doanchuyennganh
Mã nguồn, tài liệu 
# Ứng dụng thu thập và phân tích dữ liệu học tập tự động: StudyPath

## 1. Tổng quan Dự án

StudyPath là một hệ thống thu thập và phân tích dữ liệu học tập tự động, được phát triển nhằm hỗ trợ sinh viên theo dõi tình trạng học tập và lập kế hoạch học tập cho các kỳ tiếp theo.

Hệ thống được phát triển bằng **Python và Playwright**, sử dụng Playwright để tự động đăng nhập và thu thập dữ liệu từ **Cổng thông tin đào tạo**.

Mục tiêu của hệ thống:

* Tự động thu thập dữ liệu học tập của sinh viên.
* Phân tích và đối chiếu chương trình đào tạo với bảng điểm.
* Tính GPA và xác định tình trạng các học phần.
* Xác định các môn đã học, các môn đủ điều kiện đăng ký và các môn còn bị khóa.
* Gợi ý lộ trình học tập phù hợp cho từng kỳ.

---

## 2. Chức năng Cốt lõi

### A. Tự động đăng nhập & Thu thập dữ liệu

* **Tự động đăng nhập:** Sử dụng Playwright để tự động hóa trình duyệt và đăng nhập vào Cổng thông tin đào tạo.
* **Thu thập dữ liệu:** Tự động thu thập các dữ liệu cần thiết phục vụ quá trình phân tích.
* **Dữ liệu chương trình đào tạo:** Thu thập thông tin về chương trình đào tạo và các học phần.
* **Dữ liệu bảng điểm:** Thu thập thông tin kết quả học tập của sinh viên.
* **Dữ liệu đăng ký học phần hiện tại:** Thu thập thông tin các học phần sinh viên đang đăng ký trong kỳ hiện hành, phục vụ việc loại trừ khỏi danh sách gợi ý.

---

### B. Phân tích & Đối chiếu dữ liệu

* **Đối chiếu chương trình đào tạo và bảng điểm:** So sánh dữ liệu chương trình đào tạo với bảng điểm của sinh viên.
* **Phân tích dữ liệu học tập:** Xác định tình trạng học tập dựa trên dữ liệu đã thu thập.
* **Tính GPA:** Tính toán GPA (thang điểm 4 và thang điểm 10) dựa trên dữ liệu điểm quy đổi chính thức của bảng điểm, loại trừ đúng các học phần đánh giá Đạt/Không đạt (như Giáo dục thể chất) khỏi việc tính GPA theo đúng quy chế đào tạo.
* **Xác định môn đã học:** Xác định các học phần sinh viên đã hoàn thành hoặc đã học.
* **Xử lý khối kiến thức tự chọn:** Phân biệt khối kiến thức bắt buộc phải hoàn thành toàn bộ và khối kiến thức tự chọn (chỉ cần đạt đủ số tín chỉ yêu cầu, ví dụ khối Giáo dục thể chất), tránh gợi ý sinh viên học thêm các học phần không còn cần thiết.
* **Nhận diện học phần đang đăng ký trong kỳ hiện tại:** Xác định các học phần sinh viên đã đăng ký nhưng chưa có kết quả, để không đưa các học phần này vào danh sách gợi ý đăng ký trùng lặp.

---

### C. Xác định tình trạng học phần

* **Môn đủ điều kiện đăng ký:** Xác định các học phần mà sinh viên đủ điều kiện đăng ký.
* **Môn còn bị khóa:** Xác định các học phần mà sinh viên chưa đủ điều kiện đăng ký (do chưa hoàn thành học phần tiên quyết), kèm theo thông tin cụ thể về các học phần còn thiếu.
* **Môn không bắt buộc:** Xác định các học phần thuộc khối kiến thức tự chọn mà sinh viên đã đạt đủ yêu cầu tín chỉ, không cần đăng ký thêm.
* **Tình trạng học tập:** Tổng hợp thông tin về các học phần đã học và các học phần còn cần hoàn thành.

---

### D. Hỗ trợ lập kế hoạch học tập

* **Phân tích tình trạng học tập:** Dựa trên chương trình đào tạo và bảng điểm của sinh viên.
* **Xác định môn có thể đăng ký:** Dựa trên tình trạng học tập và điều kiện của học phần.
* **Gợi ý lộ trình học tập:** Đề xuất lộ trình học tập phù hợp cho sinh viên theo từng kỳ, dựa trên thuật toán xếp hạng ưu tiên kết hợp 4 tiêu chí:

  1. **Độ trễ tiến độ** — mức độ chênh lệch giữa học kỳ hiện tại và học kỳ dự kiến theo khung chương trình.
  2. **Tác động mở khóa** — số lượng học phần khác sẽ được mở ra để đăng ký nếu hoàn thành học phần này.
  3. **Vị trí trên lộ trình tốt nghiệp** — mức độ ưu tiên cao hơn cho các học phần thuộc nhóm chuyên ngành bắt buộc, đồ án và thực tập tốt nghiệp.
  4. **Cân bằng giữa các khối kiến thức** — ưu tiên các khối kiến thức có tỷ lệ hoàn thành thấp để tránh dồn học phần vào giai đoạn cuối khóa học.

---

## 3. Công nghệ sử dụng

* **Ngôn ngữ lập trình:** Python
* **Công cụ tự động hóa trình duyệt:** Playwright
* **Thư viện xử lý dữ liệu HTML:** BeautifulSoup4

Các công nghệ hỗ trợ khác sẽ được cập nhật trong quá trình phát triển dự án.

---

## 4. Quy trình hoạt động

* **Bước 1:** Tự động đăng nhập vào Cổng thông tin đào tạo.
* **Bước 2:** Thu thập dữ liệu chương trình đào tạo, bảng điểm và thông tin học phần.
* **Bước 3:** Phân tích và đối chiếu chương trình đào tạo với bảng điểm.
* **Bước 4:** Tính GPA và xác định tình trạng các học phần.
* **Bước 5:** Xác định các môn đã học, các môn đủ điều kiện đăng ký và các môn còn bị khóa.
* **Bước 6:** Gợi ý lộ trình học tập phù hợp cho từng kỳ.

---

## 5. Thành viên nhóm

* **Nguyễn Phương Ngân** – 23010450
* **Đỗ Nguyên Anh Vũ** – 23010334
