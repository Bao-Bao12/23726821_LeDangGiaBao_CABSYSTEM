1. GIỚI THIỆU
1.1. Mục đích tài liệu
Tài liệu này mô tả các yêu cầu đối với hệ thống CAB System – nền tảng đặt xe trực tuyến của Công ty ABC. Tài liệu là cơ sở để khách hàng, Business Analyst, nhóm phát triển, nhóm kiểm thử và các bên liên quan thống nhất về phạm vi, chức năng và chất lượng của hệ thống.
1.2. Bối cảnh
Hiện tại, khách hàng có thể liên hệ với tổng đài hoặc sử dụng một ứng dụng đơn giản để yêu cầu xe. Tuy nhiên, việc phân công tài xế chủ yếu được thực hiện thủ công, khách hàng khó theo dõi trạng thái chuyến đi, thông tin thanh toán chưa được quản lý tập trung và bộ phận vận hành gặp khó khăn khi mở rộng hệ thống.
1.3. Mục tiêu
•	Xây dựng nền tảng đặt xe có khả năng phục vụ số lượng lớn khách hàng và tài xế.
•	Số hóa quy trình từ khi khách hàng tạo yêu cầu đến khi chuyến đi hoàn thành.
•	Tự động hỗ trợ tìm kiếm và phân công tài xế phù hợp.
•	Cho phép khách hàng và tài xế theo dõi, cập nhật trạng thái chuyến đi.
•	Quản lý tập trung cước phí, thanh toán, thông báo và lịch sử giao dịch.
•	Cung cấp giao diện quản trị và báo cáo cho bộ phận vận hành.
•	Đảm bảo hệ thống ổn định, bảo mật, dễ mở rộng và có thể triển khai từng phần.
2. TỔNG QUAN HỆ THỐNG
CAB System là nền tảng trực tuyến kết nối khách hàng, tài xế và nhân viên vận hành. Khách hàng tạo yêu cầu đặt xe; hệ thống tìm kiếm tài xế phù hợp dựa trên vị trí, trạng thái sẵn sàng và các tiêu chí vận hành. Sau khi tài xế nhận chuyến, hệ thống hỗ trợ theo dõi chuyến đi, tính cước, thanh toán, gửi thông báo và lưu trữ lịch sử.
3. CÁC TÁC NHÂN VÀ BÊN LIÊN QUAN
•	Khách hàng: Đăng ký tài khoản, đặt xe, theo dõi chuyến, thanh toán, xem lịch sử và đánh giá tài xế.
•	Tài xế: Quản lý hồ sơ và phương tiện, bật trạng thái sẵn sàng, nhận chuyến và cập nhật trạng thái chuyến.
•	Nhân viên vận hành: Theo dõi chuyến đi, kiểm tra trạng thái tài xế, quản lý dữ liệu và hỗ trợ xử lý sự cố.
•	Quản trị viên: Quản lý quyền truy cập và thực hiện các thao tác quản trị nhạy cảm.
•	Ban lãnh đạo: Theo dõi báo cáo về số lượng chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả tài xế.
•	Nhà cung cấp thanh toán: Xử lý các giao dịch thanh toán điện tử bên ngoài CAB.
•	Nhà cung cấp thông báo: Cung cấp các kênh gửi thông báo cho khách hàng và tài xế.
4. PHẠM VI HỆ THỐNG
4.1. Các chức năng thuộc phạm vi
•	Quản lý tài khoản và thông tin cá nhân.
•	Quản lý hồ sơ tài xế, phương tiện và trạng thái hoạt động.
•	Tạo và tiếp nhận yêu cầu đặt xe.
•	Tìm kiếm và phân công tài xế.
•	Theo dõi và cập nhật trạng thái chuyến đi.
•	Lưu thông tin vị trí của tài xế.
•	Tính cước và hỗ trợ thanh toán bằng tiền mặt hoặc phương thức điện tử.
•	Gửi thông báo theo các sự kiện quan trọng.
•	Xem lịch sử chuyến đi, lịch sử giao dịch và đánh giá tài xế.
•	Quản trị, phân quyền, lưu vết thao tác và báo cáo.
4.2. Các nội dung chưa được chốt
•	Công thức tính cước.
•	Tiêu chí và trọng số ưu tiên tài xế.
•	Thời gian tài xế phải phản hồi.
•	Chính sách hủy chuyến.
•	Cách xử lý khi mất kết nối mạng.
•	Thời gian lưu trữ dữ liệu.
•	Các chỉ tiêu cụ thể về hiệu năng và độ sẵn sàng.
5. YÊU CẦU CHỨC NĂNG
FR-01 – Đăng ký tài khoản khách hàng: Hệ thống phải cho phép khách hàng tạo tài khoản theo thông tin do doanh nghiệp quy định.
FR-02 – Đăng nhập và xác thực: Hệ thống phải xác thực khách hàng, tài xế và nhân viên trước khi sử dụng các chức năng yêu cầu tài khoản.
FR-03 – Quản lý thông tin cá nhân: Khách hàng và tài xế có thể xem và cập nhật thông tin cá nhân theo quyền được cấp.
FR-04 – Quản lý tài khoản tài xế: Tài xế có thể đăng ký hoặc được nhân viên vận hành tạo tài khoản.
FR-05 – Quản lý phương tiện: Hệ thống phải cho phép lưu trữ và cập nhật thông tin phương tiện của tài xế.
FR-06 – Quản lý trạng thái tài xế: Tài xế có thể chuyển sang trạng thái sẵn sàng hoặc không sẵn sàng nhận chuyến.
FR-07 – Tạo yêu cầu đặt xe: Khách hàng nhập điểm đón, điểm đến, loại xe và gửi yêu cầu đặt xe.
FR-08 – Tiếp nhận yêu cầu: Hệ thống phải ghi nhận yêu cầu và thông báo cho khách hàng rằng yêu cầu đã được tiếp nhận.
FR-09 – Tìm kiếm tài xế: Hệ thống xác định các tài xế phù hợp dựa trên vị trí, trạng thái sẵn sàng và các tiêu chí vận hành.
FR-10 – Phân công lại tài xế: Nếu tài xế không phản hồi hoặc từ chối, hệ thống phải tiếp tục tìm tài xế khác mà không yêu cầu khách hàng tạo lại yêu cầu.
FR-11 – Thông báo chuyến mới: Tài xế phù hợp phải nhận được thông báo về chuyến mới.
FR-12 – Chấp nhận hoặc từ chối chuyến: Tài xế có thể chấp nhận hoặc từ chối chuyến được đề xuất.
FR-13 – Theo dõi trạng thái chuyến: Khách hàng có thể xem trạng thái tìm tài xế, đã có tài xế, tài xế đến, đang di chuyển và hoàn thành.
FR-14 – Cập nhật trạng thái chuyến: Tài xế có thể cập nhật trạng thái đã đến điểm đón, đã đón khách, đang di chuyển và hoàn thành chuyến.
FR-15 – Lưu thông tin vị trí: Hệ thống lưu thông tin vị trí tài xế để hỗ trợ tìm kiếm và ước tính thời gian đến.
FR-16 – Tính cước: Sau khi chuyến đi hoàn thành, hệ thống phải xác định số tiền khách hàng phải trả.
FR-17 – Thanh toán tiền mặt: Hệ thống phải ghi nhận kết quả thanh toán bằng tiền mặt theo quy trình của doanh nghiệp.
FR-18 – Thanh toán điện tử: Hệ thống tích hợp với nhà cung cấp thanh toán bên ngoài và không lưu trực tiếp dữ liệu nhạy cảm của thẻ hoặc tài khoản.
FR-19 – Xử lý thanh toán thất bại: Khi thanh toán điện tử thất bại, hệ thống phải thông báo cho khách hàng và cho phép xử lý lại theo chính sách.
FR-20 – Thông báo sự kiện: Hệ thống gửi thông báo khi yêu cầu được tiếp nhận, có tài xế, tài xế đến, chuyến hoàn thành và thanh toán có kết quả.
FR-21 – Lịch sử chuyến đi: Khách hàng có thể xem lịch sử chuyến đi, trạng thái và số tiền phải trả.
FR-22 – Đánh giá tài xế: Khách hàng có thể đánh giá tài xế sau khi chuyến đi hoàn thành.
FR-23 – Quản lý dữ liệu vận hành: Nhân viên vận hành có thể quản lý khách hàng, tài xế, phương tiện và chuyến đi.
FR-24 – Giám sát chuyến đi: Nhân viên vận hành có thể xem các chuyến đang diễn ra và trạng thái tài xế.
FR-25 – Xử lý chuyến bị lỗi: Nhân viên vận hành có thể kiểm tra và hỗ trợ xử lý các trường hợp chuyến bị lỗi.
FR-26 – Tra cứu giao dịch: Nhân viên vận hành có thể tra cứu lịch sử thanh toán và giao dịch.
FR-27 – Phân quyền quản trị: Hệ thống phải giới hạn các thao tác nhạy cảm theo vai trò và quyền được cấp.
FR-28 – Báo cáo: Hệ thống cung cấp báo cáo về số lượng chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả hoạt động của tài xế.
FR-29 – Lưu vết thao tác: Hệ thống phải ghi nhận các thao tác quan trọng để phục vụ kiểm tra và xử lý sự cố.
6. YÊU CẦU PHI CHỨC NĂNG
NFR-01 – Hiệu năng: Hệ thống phải có khả năng phục vụ số lượng lớn khách hàng và tài xế. Các chỉ tiêu thời gian phản hồi cụ thể cần được xác nhận.
NFR-02 – Tính ổn định: Hệ thống phải hoạt động ổn định vào những thời điểm nhu cầu tăng cao.
NFR-03 – Khả năng chịu lỗi: Lỗi xảy ra ở chức năng thanh toán hoặc thông báo không được làm toàn bộ hệ thống đặt xe ngừng hoạt động.
NFR-04 – Khả năng mở rộng: Các thành phần của hệ thống phải có khả năng mở rộng độc lập khi tải tăng.
NFR-05 – Triển khai từng phần: Chức năng mới có thể được triển khai từng phần và hạn chế ảnh hưởng đến các chức năng đang hoạt động.
NFR-06 – Xác thực: Khách hàng và tài xế phải được xác thực trước khi sử dụng các chức năng yêu cầu tài khoản.
NFR-07 – Phân quyền: Các thao tác quản trị phải được kiểm soát theo vai trò và quyền truy cập.
NFR-08 – Bảo vệ dữ liệu: Thông tin cá nhân, thông tin phương tiện, dữ liệu vị trí và dữ liệu giao dịch phải được bảo vệ.
NFR-09 – Bảo vệ dữ liệu thanh toán: Thông tin nhạy cảm của thẻ hoặc tài khoản thanh toán không được lưu trực tiếp trong hệ thống CAB.
NFR-10 – Khả năng tích hợp: Hệ thống phải có khả năng bổ sung phương thức thanh toán, nhà cung cấp thông báo và các thành phần kỹ thuật mới.
NFR-11 – Kiểm toán: Các thao tác quan trọng phải được lưu vết để phục vụ kiểm tra khi có sự cố.
NFR-12 – Khả năng bảo trì: Kiến trúc hệ thống phải linh hoạt, dễ bảo trì, thay đổi và phát triển thêm các loại dịch vụ.
7. QUY TẮC NGHIỆP VỤ
1.	BR-01: Chỉ tài xế ở trạng thái sẵn sàng mới được xem xét phân công chuyến.
2.	BR-02: Tài xế có thể chấp nhận hoặc từ chối chuyến được đề xuất.
3.	BR-03: Khi tài xế từ chối hoặc không phản hồi, hệ thống phải tiếp tục tìm tài xế khác.
4.	BR-04: Khách hàng không phải tạo lại yêu cầu khi hệ thống phân công lại tài xế.
5.	BR-05: Nếu không tìm được tài xế, hệ thống phải thông báo rõ ràng cho khách hàng.
6.	BR-06: Chỉ chuyến đi đã hoàn thành mới được chuyển sang bước tính cước và đánh giá.
7.	BR-07: Thanh toán điện tử phải được thực hiện thông qua nhà cung cấp bên ngoài.
8.	BR-08: Khi thanh toán thất bại, hệ thống phải thông báo và hỗ trợ xử lý lại theo chính sách.
9.	BR-09: Thao tác quản trị nhạy cảm chỉ được thực hiện bởi người có quyền.
10.	BR-10: Các sự kiện quan trọng của chuyến đi và thanh toán phải tạo thông báo tương ứng.
8. QUY TRÌNH NGHIỆP VỤ CHÍNH
8.1. Quy trình đặt xe
11.	Khách hàng đăng nhập hệ thống.
12.	Khách hàng nhập điểm đón, điểm đến và loại xe.
13.	Khách hàng gửi yêu cầu đặt xe.
14.	Hệ thống tiếp nhận và lưu yêu cầu.
15.	Hệ thống tìm kiếm tài xế phù hợp.
16.	Hệ thống gửi đề xuất chuyến cho tài xế.
17.	Tài xế chấp nhận, từ chối hoặc không phản hồi.
18.	Nếu cần, hệ thống tiếp tục đề xuất chuyến cho tài xế khác.
19.	Hệ thống thông báo kết quả cho khách hàng.
8.2. Quy trình thực hiện chuyến
20.	Tài xế nhận chuyến.
21.	Tài xế di chuyển đến điểm đón.
22.	Tài xế cập nhật đã đến điểm đón.
23.	Tài xế cập nhật đã đón khách.
24.	Tài xế cập nhật đang di chuyển.
25.	Tài xế cập nhật hoàn thành chuyến.
26.	Hệ thống tính cước và chuyển sang bước thanh toán.
8.3. Quy trình thanh toán
27.	Hệ thống xác định số tiền khách hàng phải trả.
28.	Khách hàng chọn thanh toán tiền mặt hoặc thanh toán điện tử.
29.	Nếu thanh toán điện tử, hệ thống gửi yêu cầu đến nhà cung cấp bên ngoài.
30.	Hệ thống nhận kết quả giao dịch.
31.	Hệ thống thông báo kết quả cho khách hàng.
32.	Hệ thống lưu lịch sử giao dịch.
33.	Nếu giao dịch thất bại, khách hàng được phép xử lý lại theo chính sách.
9. CÁC TRƯỜNG HỢP NGOẠI LỆ
•	EX-01: Không có tài xế phù hợp. Hệ thống thông báo cho khách hàng và lưu trạng thái yêu cầu không được phục vụ.
•	EX-02: Tài xế từ chối chuyến. Hệ thống chuyển sang tìm tài xế tiếp theo.
•	EX-03: Tài xế không phản hồi. Hệ thống chờ theo thời gian được doanh nghiệp xác nhận rồi chuyển đề xuất.
•	EX-04: Thanh toán điện tử thất bại. Hệ thống thông báo lỗi, lưu kết quả và cho phép thử lại.
•	EX-05: Dịch vụ thông báo gặp lỗi. Hệ thống không được dừng toàn bộ quy trình đặt xe; thông báo có thể được lưu để gửi lại.
•	EX-06: Người dùng mất kết nối mạng. Cần xác định cơ chế đồng bộ, thử lại và xử lý trạng thái.
•	EX-07: Chuyến đi bị lỗi. Nhân viên vận hành kiểm tra và hỗ trợ xử lý.
•	EX-08: Người dùng thực hiện thao tác không có quyền. Hệ thống từ chối thao tác và ghi nhận sự kiện.
10. DỮ LIỆU VÀ TÍCH HỢP
10.1. Các nhóm dữ liệu chính
•	Tài khoản và thông tin khách hàng.
•	Tài khoản, hồ sơ và trạng thái tài xế.
•	Thông tin phương tiện.
•	Thông tin yêu cầu đặt xe và chuyến đi.
•	Điểm đón, điểm đến và dữ liệu vị trí tài xế.
•	Thông tin loại xe và loại dịch vụ.
•	Thông tin cước phí.
•	Thông tin thanh toán và lịch sử giao dịch.
•	Thông báo và trạng thái gửi thông báo.
•	Đánh giá tài xế.
•	Nhật ký thao tác và dữ liệu báo cáo.
10.2. Các hệ thống tích hợp
•	Nhà cung cấp thanh toán: Xử lý thanh toán điện tử. Dữ liệu nhạy cảm không được lưu trực tiếp trong CAB.
•	Nhà cung cấp thông báo: Gửi thông báo và hỗ trợ mở rộng thêm các kênh thông báo.
•	Dịch vụ bản đồ hoặc vị trí: Hỗ trợ xác định vị trí, tìm tài xế gần và ước tính thời gian đến.
11. BẢO MẬT VÀ PHÂN QUYỀN
•	Khách hàng: Quản lý tài khoản, đặt và theo dõi chuyến của mình, thanh toán và đánh giá.
•	Tài xế: Quản lý hồ sơ, phương tiện, trạng thái và các chuyến được giao.
•	Nhân viên vận hành: Theo dõi và xử lý dữ liệu vận hành theo quyền được cấp.
•	Quản trị viên: Quản lý quyền, cấu hình và các thao tác nhạy cảm.
•	Ban lãnh đạo: Xem báo cáo theo phạm vi được cấp.
•	Mọi chức năng yêu cầu tài khoản phải kiểm tra xác thực.
•	Mọi thao tác quản trị phải kiểm tra phân quyền.
•	Dữ liệu cá nhân, vị trí và giao dịch phải được bảo vệ khi lưu trữ và truyền tải.
•	Các thao tác quan trọng phải được ghi log.
•	Không lưu trực tiếp thông tin nhạy cảm của thẻ hoặc tài khoản thanh toán.
12. TIÊU CHÍ NGHIỆM THU SƠ BỘ
•	Khách hàng có thể đăng ký, đăng nhập và tạo yêu cầu đặt xe.
•	Hệ thống có thể tìm và đề xuất tài xế phù hợp.
•	Hệ thống tiếp tục tìm tài xế khác khi tài xế từ chối hoặc không phản hồi.
•	Khách hàng có thể theo dõi trạng thái chuyến đi.
•	Tài xế có thể cập nhật các trạng thái trong quá trình thực hiện chuyến.
•	Hệ thống tính cước sau khi chuyến hoàn thành.
•	Hệ thống ghi nhận thanh toán tiền mặt và thanh toán điện tử.
•	Lỗi thanh toán hoặc thông báo không làm dừng toàn bộ hệ thống.
•	Nhân viên vận hành có thể quản lý và tra cứu dữ liệu.
•	Phân quyền và lưu vết thao tác hoạt động đúng.
•	Hệ thống có khả năng mở rộng và triển khai từng phần.
13. CÁC VẤN ĐỀ CẦN XÁC NHẬN
•	Cách tính cước: Cước được tính theo quãng đường, thời gian, loại xe, phụ phí hay kết hợp các yếu tố nào?
•	Tiêu chí ưu tiên tài xế: Hệ thống ưu tiên dựa trên khoảng cách, thời gian chờ, đánh giá, khu vực hay yếu tố khác?
•	Thời gian phản hồi: Tài xế có bao nhiêu giây hoặc phút để phản hồi?
•	Chính sách hủy chuyến: Ai được hủy, thời điểm nào được hủy và có phí hủy hay không?
•	Mất kết nối mạng: Hệ thống xử lý như thế nào khi khách hàng hoặc tài xế mất kết nối?
•	Thời gian lưu trữ: Dữ liệu chuyến đi, giao dịch, vị trí và nhật ký được lưu trong bao lâu?
•	Thông báo: Kênh thông báo ban đầu là ứng dụng, SMS, email hay kênh khác?
•	Định vị: Tần suất cập nhật vị trí và thời gian lưu dữ liệu vị trí là bao nhiêu?
•	Báo cáo: Báo cáo cần theo ngày, tuần, tháng, chi nhánh hay theo tài xế?
•	Hiệu năng: Số người dùng đồng thời, thời gian phản hồi và độ sẵn sàng yêu cầu là bao nhiêu?
•	Phân quyền: Có những vai trò quản trị nào và vai trò nào được thực hiện thao tác nhạy cảm?
•	Kế hoạch 7 tuần: Chức năng nào bắt buộc trong phiên bản đầu và chức năng nào có thể triển khai sau?
14. GIẢ ĐỊNH VÀ RÀNG BUỘC
•	Thời gian xây dựng và triển khai dự kiến là 7 tuần.
•	Doanh nghiệp sẽ xác nhận các chính sách và tiêu chí còn thiếu trước khi phát triển.
•	Nhà cung cấp thanh toán và thông báo phải cung cấp tài liệu tích hợp và môi trường kiểm thử.
•	Hệ thống cần có kiến trúc mô-đun, linh hoạt và có thể mở rộng.
•	Các yêu cầu chưa được xác nhận không được xem là yêu cầu đã chốt.
•	Các chỉ tiêu định lượng về hiệu năng, độ sẵn sàng và thời gian phản hồi chưa được cung cấp.
15. KẾT LUẬN
CAB System là nền tảng đặt xe phục vụ khách hàng, tài xế và bộ phận vận hành. Hệ thống phải hỗ trợ đầy đủ quy trình đặt xe, điều phối, thực hiện chuyến, tính cước, thanh toán, thông báo và đánh giá. Đồng thời, hệ thống phải bảo đảm tính ổn định, khả năng mở rộng, bảo mật, phân quyền và khả năng tích hợp. Những nội dung chưa được chốt cần được Business Analyst xác nhận với các bên liên quan trước khi nhóm phát triển thiết kế và triển khai giải pháp.
