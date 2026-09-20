# CHÚ GIẢI VÀ BỘ 200 TEST CASES CHO HỆ THỐNG CABSYSTEM

---

## I. CHÚ GIẢI CÁC CỘT (LEGEND & GLOSSARY)

| Tên Cột | Ý Nghĩa / Định Nghĩa | Ví Dụ Chi Tiết |
| :--- | :--- | :--- |
| **Test Case ID** | Mã định danh duy nhất cho từng trường hợp kiểm thử, quy hoạch theo Module | `TC-AUTH-001`, `TC-BOOK-015`, `TC-PAY-008` |
| **Test Scenario** | Ngữ cảnh / Tình huống kiểm thử tổng quát cần đánh giá | *Kiểm tra đăng nhập với thông tin hợp lệ*, *Kiểm tra áp dụng mã giảm giá hết hạn* |
| **Test Case** | Mô tả mục tiêu cụ thể của trường hợp kiểm thử | *Đăng nhập thành công khi nhập đúng Username và Password* |
| **Preconditions** | Điều kiện tiên quyết cần có trước khi thực hiện test | *Tài khoản khách hàng đã đăng ký và ở trạng thái Active* |
| **Test Steps** | Các bước thao tác chi tiết theo thứ tự của tester | 1. Truy cập màn hình Đăng nhập<br>2. Nhập Username<br>3. Nhập Password<br>4. Nhấn nút Đăng nhập |
| **Test Data** | Dữ liệu đầu vào dùng để kiểm thử | `Username: customer01`, `Password: Pass@1234` |
| **Expected Result** | Kết quả mong đợi hệ thống trả về đúng như thiết kế SRS | *Đăng nhập thành công, chuyển hướng vào màn hình Trang chủ và hiển thị Avatar* |
| **Priority** | Mức độ ưu tiên kiểm thử (`High` / `Medium` / `Low`) | `High` (Các chức năng cốt lõi), `Medium` (Logic phụ), `Low` (Giao diện UI) |

---

## II. BỘ 200 TEST CASES HỆ THỐNG CABSYSTEM

---

### MODULE 1: AUTHENTICATION & USER PROFILE (TÀI KHOẢN & XÁC THỰC) - 35 TEST CASES

| ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `TC-AUTH-001` | Đăng nhập hợp lệ | Đăng nhập thành công với Username/Password chính xác | Tài khoản `user01` đã tồn tại | 1. Mở app<br>2. Nhập Username & Password<br>3. Bấm Đăng nhập | `user01` / `Pass@123` | Đăng nhập thành công, mở Trang chủ | High |
| `TC-AUTH-002` | Đăng nhập hợp lệ | Đăng nhập thành công bằng Email đã đăng ký | Email `user01@gmail.com` tồn tại | 1. Nhập Email & Password<br>2. Bấm Đăng nhập | `user01@gmail.com` / `Pass@123` | Đăng nhập thành công, vào Trang chủ | High |
| `TC-AUTH-003` | Đăng nhập hợp lệ | Đăng nhập thành công khi nhấn phím Enter | Đang ở màn hình đăng nhập | 1. Nhập Username & Password<br>2. Nhấn phím Enter | `user01` / `Pass@123` | Hệ thống submit form và đăng nhập | Medium |
| `TC-AUTH-004` | Xác thực sai | Đăng nhập với Username không tồn tại | Chưa có tài khoản `nosuchuser` | 1. Nhập Username lạ & Password<br>2. Bấm Đăng nhập | `nosuchuser` / `Pass@123` | Báo lỗi: "Tài khoản hoặc mật khẩu không đúng" | High |
| `TC-AUTH-005` | Xác thực sai | Đăng nhập đúng Username nhưng sai Password | Tài khoản `user01` tồn tại | 1. Nhập Username đúng & Password sai<br>2. Bấm Đăng nhập | `user01` / `WrongPass` | Báo lỗi: "Tài khoản hoặc mật khẩu không đúng" | High |
| `TC-AUTH-006` | Trạng thái TK | Đăng nhập vào Tài khoản đang bị Khóa | Tài khoản `locked_user` bị khóa | 1. Nhập tài khoản bị khóa & Password<br>2. Bấm Đăng nhập | `locked_user` / `Pass@123` | Báo lỗi: "Tài khoản đã bị khóa, liên hệ CSKH" | High |
| `TC-AUTH-007` | Trạng thái TK | Đăng nhập vào Tài khoản chưa kích hoạt OTP | Tài khoản mới tạo chưa nhập OTP | 1. Nhập thông tin đăng nhập<br>2. Bấm Đăng nhập | `unactive_user` / `Pass@123` | Chuyển hướng sang màn hình Xác thực OTP | High |
| `TC-AUTH-008` | Mật khẩu ngắn | Nhập mật khẩu dưới 5 ký tự (<5 chars) | Màn hình đăng nhập | 1. Nhập Username<br>2. Nhập Password 4 ký tự<br>3. Bấm Đăng nhập | `user01` / `1234` | Báo lỗi: "Mật khẩu phải từ 5 ký tự trở lên" | High |
| `TC-AUTH-009` | Cận biên MK | Nhập mật khẩu đạt độ dài tối thiểu (5 ký tự) | Mật khẩu tài khoản là `12345` | 1. Nhập Username & Pass 5 ký tự<br>2. Bấm Đăng nhập | `user_5char` / `12345` | Đăng nhập thành công | Medium |
| `TC-AUTH-010` | Độ dài cực đại | Nhập Username/Pass dài vượt mức (>100 ký tự) | Màn hình đăng nhập | 1. Nhập Chuỗi 150 ký tự vào Username/Pass<br>2. Bấm Đăng nhập | Chuỗi 150 ký tự | Ô nhập chặn không cho gõ quá 100 ký tự hoặc báo lỗi | Medium |
| `TC-AUTH-011` | Trường trống | Đăng nhập để trống cả Username và Password | Màn hình đăng nhập | 1. Để trống 2 ô<br>2. Bấm Đăng nhập | Trống | Báo lỗi bắt buộc nhập Username và Password | High |
| `TC-AUTH-012` | Trường trống | Đăng nhập nhập Username, để trống Password | Màn hình đăng nhập | 1. Nhập Username<br>2. Để trống Password<br>3. Bấm Đăng nhập | `user01` / Trống | Báo lỗi: "Vui lòng nhập mật khẩu" | High |
| `TC-AUTH-013` | Trường trống | Đăng nhập để trống Username, chỉ nhập Pass | Màn hình đăng nhập | 1. Để trống Username<br>2. Nhập Password<br>3. Bấm Đăng nhập | Trống / `Pass@123` | Báo lỗi: "Vui lòng nhập tên đăng nhập" | High |
| `TC-AUTH-014` | Whitespace | Nhập toàn khoảng trắng vào ô Đăng nhập | Màn hình đăng nhập | 1. Nhập `   ` vào Username và Pass<br>2. Bấm Đăng nhập | `   ` / `   ` | Trim khoảng trắng và báo lỗi chưa nhập dữ liệu | Medium |
| `TC-AUTH-015` | Case-sensitive | Phân biệt chữ hoa/thường ở ô Mật khẩu | Mật khẩu là `PassWord123` | 1. Nhập Username<br>2. Nhập Pass toàn chữ thường `password123`<br>3. Bấm Đăng nhập | `user01` / `password123` | Báo lỗi mật khẩu không chính xác | High |
| `TC-AUTH-016` | Format Email | Đăng nhập bằng Email sai định dạng | Màn hình đăng nhập | 1. Nhập Email thiếu dấu `@` hoặc tên miền<br>2. Bấm Đăng nhập | `user01gmail.com` / `Pass@123` | Báo lỗi: "Email không đúng định dạng" | Medium |
| `TC-AUTH-017` | SQL Injection | Tấn công SQL Injection vào ô Đăng nhập | Màn hình đăng nhập | 1. Nhập mã SQL vào Username<br>2. Bấm Đăng nhập | `' OR '1'='1` / `anything` | Hệ thống chặn, báo lỗi thông tin không hợp lệ | High |
| `TC-AUTH-018` | XSS Attack | Tấn công XSS vào ô Đăng nhập | Màn hình đăng nhập | 1. Nhập mã Script vào ô Username<br>2. Bấm Đăng nhập | `<script>alert('xss')</script>` | Mã không được thực thi, báo lỗi dữ liệu | High |
| `TC-AUTH-019` | Password Masking | Bật/Tắt ẩn hiện mật khẩu (Icon Eye) | Đã nhập mật khẩu vào ô | 1. Nhập Mật khẩu<br>2. Toggle icon con mắt | `MyPass123` | Mật khẩu chuyên đổi giữa dạng `***` và text rõ | Low |
| `TC-AUTH-020` | Brute Force | Khóa tài khoản sau 5 lần nhập sai liên tiếp | Tài khoản `user01` đang Active | 1. Nhập sai mật khẩu 5 lần liên tiếp | `user01` / `WrongPass` | Tài khoản bị khóa tạm thời 15 phút | High |
| `TC-AUTH-021` | Đăng ký mới | Đăng ký tài khoản thành công với thông tin đúng | SĐT chưa từng đăng ký | 1. Nhập SĐT, Họ tên, Pass<br>2. Bấm Đăng ký | `0901234567` / `User A` / `Pass@123` | Gửi mã OTP về SĐT để xác minh | High |
| `TC-AUTH-022` | Đăng ký trùng | Đăng ký với SĐT đã tồn tại | SĐT `0901234567` đã có | 1. Nhập SĐT đã tồn tại<br>2. Bấm Đăng ký | `0901234567` / `User B` / `Pass@123` | Báo lỗi: "Số điện thoại đã được sử dụng" | High |
| `TC-AUTH-023` | Xác thực OTP | Nhập đúng mã OTP trong thời gian hiệu lực | Đã nhận OTP (Hạn 60s) | 1. Nhập đúng 6 số OTP<br>2. Bấm Xác nhận | `123456` | Xác minh thành công, hoàn tất đăng ký | High |
| `TC-AUTH-024` | Xác thực OTP | Nhập sai mã OTP | Đang ở màn hình OTP | 1. Nhập mã OTP sai<br>2. Bấm Xác nhận | `000000` | Báo lỗi: "Mã OTP không chính xác" | High |
| `TC-AUTH-025` | Hết hạn OTP | Nhập mã OTP sau khi hết thời gian hiệu lực | Đã quá 60s kể từ lúc gửi OTP | 1. Chờ hết 60s<br>2. Nhập OTP chính xác<br>3. Bấm Xác nhận | `123456` | Báo lỗi: "Mã OTP đã hết hạn, vui lòng lấy mã mới" | Medium |
| `TC-AUTH-026` | Quên MK | Yêu cầu khôi phục mật khẩu qua SĐT | SĐT tồn tại trên hệ thống | 1. Nhập SĐT quên MK<br>2. Bấm Gửi yêu cầu | `0901234567` | Hệ thống gửi OTP reset mật khẩu | High |
| `TC-AUTH-027` | Đổi MK | Đổi mật khẩu thành công khi nhập đúng MK cũ | Đã đăng nhập app | 1. Nhập MK cũ, MK mới hợp lệ<br>2. Bấm Lưu | Old: `Pass@123`, New: `NewPass@456` | Đổi MK thành công, yêu cầu đăng nhập lại | High |
| `TC-AUTH-028` | Đổi MK | Đổi mật khẩu thất bại khi MK mới trùng MK cũ | Đã đăng nhập app | 1. Nhập MK mới giống hệt MK cũ<br>2. Bấm Lưu | Old: `Pass@123`, New: `Pass@123` | Báo lỗi: "Mật khẩu mới không được trùng mật khẩu cũ" | Medium |
| `TC-AUTH-029` | Đổi MK | Mật khẩu mới và Nhập lại mật khẩu không khớp | Đã đăng nhập app | 1. Nhập MK mới và Nhập lại MK khác nhau<br>2. Bấm Lưu | New: `NewPass@1`, Confirm: `NewPass@2` | Báo lỗi: "Mật khẩu xác nhận không khớp" | High |
| `TC-AUTH-030` | Update Profile | Cập nhật Avatar thành công (.PNG, .JPG < 5MB) | Đã đăng nhập | 1. Chọn file ảnh JPG 2MB<br>2. Bấm Tải lên | `profile.jpg` | Avatar được cập nhật hiển thị mới | Low |
| `TC-AUTH-031` | Update Profile | Cập nhật Avatar sai định dạng (.PDF, .EXE) | Đã đăng nhập | 1. Chọn file đuôi .pdf<br>2. Bấm Tải lên | `document.pdf` | Báo lỗi: "Định dạng file không hỗ trợ" | Low |
| `TC-AUTH-032` | Update Profile | Cập nhật Avatar dung lượng vượt quá quy định (>10MB) | Đã đăng nhập | 1. Chọn file ảnh 15MB<br>2. Bấm Tải lên | `huge_photo.png` (15MB) | Báo lỗi: "Dung lượng ảnh không quá 5MB" | Low |
| `TC-AUTH-033` | Quản lý Sessions | Đăng xuất khỏi hệ thống thành công | Đã đăng nhập | 1. Vào Menu -> Chọn Đăng xuất | N/A | Xóa Session/Token, chuyển về màn Login | High |
| `TC-AUTH-034` | Multi-device | Đăng nhập trên thiết bị thứ 2 (Đá thiết bị cũ) | Đang đăng nhập thiết bị A | 1. Dùng thiết bị B đăng nhập cùng tài khoản | `user01` / `Pass@123` | Thiết bị A nhận thông báo bị đăng xuất | Medium |
| `TC-AUTH-035` | Token Expired | Thao tác app khi Access Token hết hạn | Token đã hết hạn | 1. Thực hiện thao tác bất kỳ | N/A | Tự động làm mới Token (Refresh) hoặc đẩy về Login | High |

---

### MODULE 2: BOOKING & FARE CALCULATION (ĐẶT CHUYẾN & TÍNH GIÁ) - 45 TEST CASES

| ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `TC-BOOK-001` | Đặt xe ngay | Đặt chuyến Cab4 thành công điểm đi/đến hợp lệ | Đã bật vị trí GPS | 1. Chọn điểm đi, điểm đến<br>2. Chọn loại xe Cab4<br>3. Bấm Đặt xe | Pick: Landmark 81<br>Drop: Bến Thành | Hệ thống hiển thị màn hình tìm tài xế | High |
| `TC-BOOK-002` | Đặt xe ngay | Đặt chuyến Cab7 thành công | Đã có vị trí | 1. Chọn lộ trình<br>2. Chọn Cab7<br>3. Bấm Đặt xe | Lộ trình 10km | Hệ thống tính đúng giá cho Cab7 và tìm xe | High |
| `TC-BOOK-003` | Đặt xe ngay | Đặt chuyến CabBike thành công | Đã có vị trí | 1. Chọn lộ trình<br>2. Chọn CabBike<br>3. Bấm Đặt xe | Lộ trình 3km | Tìm tài xế xe máy thành công | High |
| `TC-BOOK-004` | Điểm đi/đến trùng | Chọn điểm đón và điểm trả trùng nhau | Màn hình booking | 1. Nhập điểm đón trùng điểm trả<br>2. Bấm Đặt xe | Pick = Drop = "Sân bay Tân Sơn Nhất" | Báo lỗi: "Điểm đến không được trùng điểm đón" | High |
| `TC-BOOK-005` | Khoảng cách ngắn | Đặt xe khoảng cách cực ngắn (<200m) | Màn hình booking | 1. Chọn 2 địa điểm cách nhau 100m<br>2. Bấm Đặt xe | Distance = 100m | Áp dụng giá cước tối thiểu (Minimum Fare) | Medium |
| `TC-BOOK-006` | Khoảng cách xa | Đặt xe đi tỉnh khoảng cách xa (>100km) | Màn hình booking | 1. Chọn điểm đến cách 150km<br>2. Xem tính giá | Pick: TP.HCM<br>Drop: Vũng Tàu | Áp dụng bảng giá đường dài theo SRS | High |
| `TC-BOOK-007` | Đặt lịch trước | Đặt chuyến trước 2 tiếng (Hợp lệ) | Thời gian hiện tại 10:00 | 1. Chọn Đặt lịch<br>2. Chọn giờ đón 12:00 hôm nay<br>3. Xác nhận | Time: 12:00 Today | Tạo chuyến hẹn giờ thành công | High |
| `TC-BOOK-008` | Đặt lịch trước | Đặt chuyến trước dưới 30 phút (Không hợp lệ) | Thời gian hiện tại 10:00 | 1. Chọn Đặt lịch<br>2. Chọn giờ đón 10:15<br>3. Xác nhận | Time: 10:15 Today | Báo lỗi: "Thời gian hẹn giờ phải sau ít nhất 30 phút" | High |
| `TC-BOOK-009` | Đặt lịch trước | Đặt chuyến trước quá 30 ngày (Không hợp lệ) | Ngày hiện tại: 01/10 | 1. Chọn Đặt lịch ngày 15/11 (>30 ngày)<br>2. Bấm Đặt xe | Date: 15/11 | Báo lỗi: "Không được đặt trước quá 30 ngày" | Medium |
| `TC-BOOK-010` | Mã giảm giá | Áp dụng Mã giảm giá hợp lệ còn lượt | Có mã `CABNEW` giảm 20k | 1. Nhập mã `CABNEW`<br>2. Bấm Áp dụng | Code: `CABNEW` | Giá chuyến đi giảm đúng 20.000 VNĐ | High |
| `TC-BOOK-011` | Mã giảm giá | Áp dụng Mã giảm giá đã hết hạn sử dụng | Mã `SUMMER2023` hết hạn | 1. Nhập mã hết hạn<br>2. Bấm Áp dụng | Code: `SUMMER2023` | Báo lỗi: "Mã giảm giá đã hết hạn" | Medium |
| `TC-BOOK-012` | Mã giảm giá | Áp dụng Mã giảm giá khi chưa đủ giá trị tối thiểu | Mã áp dụng cho chuyến >100k, chuyến đi 50k | 1. Chọn chuyến 50k<br>2. Nhập mã<br>3. Bấm Áp dụng | Code: `BIG100` | Báo lỗi: "Chuyến đi chưa đạt giá trị tối thiểu 100.000đ" | High |
| `TC-BOOK-013` | Mã giảm giá | Áp dụng Mã giảm giá đã hết lượt sử dụng chung | Mã bị dùng hết lượt | 1. Nhập mã hết lượt<br>2. Bấm Áp dụng | Code: `HOTDEAL` | Báo lỗi: "Mã giảm giá đã hết số lượng lượt dùng" | Medium |
| `TC-BOOK-014` | Mã giảm giá | Nhập Mã giảm giá không tồn tại | Màn hình checkout | 1. Nhập mã ngẫu nhiên không có thật<br>2. Bấm Áp dụng | Code: `FAKECODE123` | Báo lỗi: "Mã giảm giá không hợp lệ" | High |
| `TC-BOOK-015` | Phụ phí Surge | Tính cước giờ cao điểm (Surge Pricing 1.5x) | Khung giờ 17:30-19:00 | 1. Chọn lộ trình tiêu chuẩn<br>2. Xem bảng chi tiết cước | Time: 18:00 | Giá cước cơ bản nhân hệ số Surge 1.5 | High |
| `TC-BOOK-016` | Phụ phí Thời tiết | Tính phụ phí khi thời tiết mưa lớn | Hệ thống bật Surge Weather | 1. Đặt xe lúc trời mưa<br>2. Kiểm tra hóa đơn tạm tính | Weather: Rain | Hiển thị thêm dòng "Phụ phí thời tiết xấu" | High |
| `TC-BOOK-017` | Phụ phí Lễ Tết | Tính phụ phí ngày Lễ Tết | Ngày Tết Âm Lịch | 1. Đặt xe ngày mùng 1 Tết<br>2. Kiểm tra cước | Date: 1 Tết | Tự động cộng phụ phí Ngày lễ theo quy định | Medium |
| `TC-BOOK-018` | Phụ phí Phí đường | Tính phí cầu đường/bến bãi tự động | Lộ trình qua trạm BOT | 1. Chọn lộ trình qua BOT Điện Biên Phủ | Route: Qua BOT | Cước chuyến đi cộng thêm phí BOT | Medium |
| `TC-BOOK-019` | Điểm dừng phụ | Đặt chuyến đi có thêm 1 điểm dừng trung gian | Màn hình booking | 1. Chọn điểm đi -> Chọn Stop 1 -> Chọn điểm trả<br>2. Bấm Đặt xe | Stop 1: Q3, Drop: Q7 | Giá cước cộng thêm phí dừng điểm phụ | High |
| `TC-BOOK-020` | Giới hạn điểm dừng| Thêm vượt quá số điểm dừng tối đa (>3 điểm) | Màn hình booking | 1. Thêm liên tiếp 4 điểm dừng phụ | 4 Stops | Hệ thống ẩn nút thêm điểm dừng hoặc báo lỗi | Low |
| `TC-BOOK-021` | Ghi chú tài xế | Đặt xe kèm Ghi chú đặc biệt cho tài xế | Màn hình checkout | 1. Nhập ghi chú "Có mang theo thú cưng"<br>2. Bấm Đặt xe | Note: "Mang theo cún nhỏ" | Ghi chú hiển thị trên màn hình nhận chuyến của tài xế | Low |
| `TC-BOOK-022` | Ghi chú quá dài | Ghi chú dài vượt quá 200 ký tự | Màn hình checkout | 1. Nhập ghi chú 250 ký tự<br>2. Bấm Đặt xe | Text >200 chars | Cắt bớt tại ký tự thứ 200 hoặc báo lỗi | Low |
| `TC-BOOK-023` | Đổi phương thức | Thay đổi phương thức thanh toán trước khi bấm đặt | Màn hình checkout | 1. Chuyển từ Tiền mặt sang Ví MoMo<br>2. Bấm Đặt xe | Wallet: MoMo | Chuyến đi ghi nhận phương thức MoMo | High |
| `TC-BOOK-024` | Không tìm thấy xe| Hệ thống xử lý khi không tìm thấy tài xế xung quanh | Khu vực hẻo lánh không có xe | 1. Đặt xe ở vùng không có driver<br>2. Chờ Hết thời gian tìm (3 phút) | No driver nearby | Báo lỗi: "Hiện không có xe gần bạn, vui lòng thử lại" | High |
| `TC-BOOK-025` | Timeout đặt xe | Hết thời gian chờ phản hồi tìm xe (Timeout 180s) | Đang trong trạng thái Tìm xe | 1. Không tài xế nào nhận chuyến trong 3 phút | Timeout 180s | Tự động hủy tìm kiếm và đề xuất tăng giá hoặc thử lại | Medium |
| `TC-BOOK-026` | Chọn sai loại xe | Chọn loại xe không phù hợp số hành khách (5 người chọn Bike)| Màn hình booking | 1. Chọn 5 hành khách<br>2. Chọn loại xe CabBike | Passengers: 5, Type: Bike | Hệ thống cảnh báo loại xe không đủ chỗ | Low |
| `TC-BOOK-027` | Bản đồ GPS yếu | Đặt xe khi tín hiệu GPS yếu / Không chính xác | GPS bị chập chờn | 1. Đặt xe khi GPS báo sai vị trí 2km<br>2. Kéo pin thủ công trên bản đồ | Manual Pin | Hệ thống lấy đúng tọa độ pin người dùng ghim | Medium |
| `TC-BOOK-028` | Format Tiền tệ | Hiển thị định dạng tiền tệ VNĐ chuẩn | Màn hình giá | 1. Xem giá cước tính toán | Price: 150000 | Hiển thị dạng `150.000 VNĐ` hoặc `150.000 đ` | Medium |
| `TC-BOOK-029` | Đơn vị Khoảng cách| Hiển thị định dạng khoảng cách (Km / m) | Màn hình giá | 1. Chọn đường đi 850m<br>2. Chọn đường 3.5km | Distance | Hiển thị `850 m` và `3.5 km` chuẩn định dạng | Low |
| `TC-BOOK-030` | Lập lịch trùng | Đặt lịch trước bị trùng giờ với một chuyến khác | Đã có chuyến đặt hẹn 14:00 | 1. Đặt tiếp 1 chuyến hẹn lúc 14:15 | Time: 14:15 | Báo lỗi: "Bạn đã có một chuyến đi đặt trước vào khoảng thời gian này" | High |
| `TC-BOOK-031` | Đặt hộ người thân| Đặt chuyến xe cho người khác (Nhập SĐT người đi) | Màn hình booking | 1. Chọn "Đặt cho người thân"<br>2. Nhập SĐT & Tên người đi | Phone: `0988776655`, Name: `B` | Thông báo chuyến đi được gửi đến SĐT người đi | Medium |
| `TC-BOOK-032` | Đặt hộ SĐT sai | Đặt xe cho người khác nhưng nhập SĐT sai định dạng | Màn hình book hộ | 1. Nhập SĐT thiếu số | Phone: `09123` | Báo lỗi: "Số điện thoại người đi không hợp lệ" | Medium |
| `TC-BOOK-033` | Hủy đặt xe | Người dùng bấm Hủy tìm xe khi đang trong quá trình tìm | Đang tìm tài xế | 1. Bấm nút "Hủy tìm xe" | Action: Cancel | Ngừng tìm kiếm ngay lập tức và trả về trang chủ | High |
| `TC-BOOK-034` | Re-book | Đặt lại chuyến đi từ Lịch sử chuyến đi (Re-book) | Đã có chuyến đi cũ thành công | 1. Vào Lịch sử -> Bấm "Đặt lại" | Old trip ID | Tự động điền lại điểm đi và điểm đến | Medium |
| `TC-BOOK-035` | Đảo ngược lộ trình| Bấm nút Đảo chiều điểm đi và điểm đến | Màn hình booking | 1. Nhập Pick A, Drop B<br>2. Nhấn icon Đảo chiều | Action: Swap | Lộ trình chuyển thành Pick B, Drop A và tính lại giá | Low |
| `TC-BOOK-036` | Giá thay đổi | Cập nhật lại giá cước khi người dùng đổi điểm đến | Đang chọn chuyến đi | 1. Đổi điểm trả sang vị trí xa hơn | New Drop location | Cước phí hiển thị được tính toán lại ngay lập tức | High |
| `TC-BOOK-037` | Kiểm tra VAT | Chọn xuất hóa đơn GTGT (VAT) khi đặt chuyến | Tài khoản Doanh nghiệp | 1. Tích chọn "Xung xuất hóa đơn VAT"<br>2. Đặt xe | Company Tax Info | Hệ thống lưu thông tin VAT vào chi tiết hóa đơn | Medium |
| `TC-BOOK-038` | Offline booking | Bấm Đặt xe khi thiết bị mất kết nối Internet | Tắt Wifi/4G | 1. Bấm Đặt xe | No Internet | Hiển thị thông báo: "Không có kết nối mạng, vui lòng kiểm tra lại" | High |
| `TC-BOOK-039` | Lưu địa điểm | Chọn điểm đi từ Danh sách địa chỉ đã lưu (Nhà/Cty) | Đã lưu địa chỉ Nhà | 1. Chọn icon "Nhà"<br>2. Chọn điểm đến | Favorite: Home | Tự động điền chính xác địa chỉ Nhà đã lưu | Low |
| `TC-BOOK-040` | Xóa điểm đã lưu | Xóa địa chỉ khỏi danh sách yêu thích | Đã lưu địa chỉ | 1. Vô Quản lý địa điểm -> Bấm Xóa | Delete "Home" | Địa điểm bị xóa khỏi danh sách gợi ý | Low |
| `TC-BOOK-041` | Đặt nhiều xe | Đặt đồng thời 2 chuyến xe cùng lúc trên 1 tài khoản | Đang có 1 chuyến xe chưa hoàn thành | 1. Thử thực hiện đặt thêm chuyến thứ 2 | Active trip exists | Báo lỗi: "Bạn đang có chuyến đi chưa hoàn thành, không thể đặt thêm" | High |
| `TC-BOOK-042` | Đặt xe giờ đêm | Đặt xe trong khung giờ đêm (22:00 - 05:00) | Khung giờ đêm | 1. Đặt xe lúc 23:30 | Time: 23:30 | Áp dụng phụ phí đi đêm Night Fee theo SRS | Medium |
| `TC-BOOK-043` | Ước tính thời gian| Hiển thị ước tính thời gian tài xế đến đón (ETA) | Tài xế đã nhận chuyến | 1. Xem màn hình tracking | ETA display | Hiển thị chính xác thời gian dự kiến (Ví dụ: 5 phút) | High |
| `TC-BOOK-044` | Hạn mức Voucher | Nhập Voucher áp dụng giới hạn mức giảm tối đa | Voucher giảm 50% tối đa 30k | 1. Chuyến đi 100k (50% = 50k)<br>2. Áp Voucher | Max discount: 30k | Số tiền giảm thực tế đúng 30.000 VNĐ | High |
| `TC-BOOK-045` | Xóa Voucher | Bỏ chọn Mã giảm giá đã áp dụng | Đã áp mã giảm giá thành công | 1. Bấm nút "Bỏ chọn mã"<br>2. Xem lại giá | Remove promo | Cước phí quay về giá nguyên bản ban đầu | Medium |

---

### MODULE 3: TRIP EXECUTION & DISPATCH (ĐIỀU PHỐI & CHUYẾN ĐI) - 35 TEST CASES

| ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `TC-TRIP-001` | Tài xế nhận chuyến| Tài xế nhận chuyến đi thành công | Tài xế đang Online, nhận notification | 1. Tài xế vuốt/bấm "Nhận chuyến" | Trip ID #101 | Chuyến đi đổi trạng thái sang "Driver Accepted" | High |
| `TC-TRIP-002` | Tài xế từ chối | Tài xế bỏ qua / Từ chối chuyến đi được phát | Phát chuyến cho Tài xế A | 1. Tài xế bấm "Bỏ qua" | Reject Trip | Chuyến đi tự động chuyển phát cho Tài xế B gần đó | High |
| `TC-TRIP-003` | Trạng thái Đã đến | Tài xế cập nhật trạng thái "Đã đến điểm đón" | Chuyến đi ở trạng thái Accepted | 1. Tài xế tới vị trí -> Bấm "Đã đến" | Driver Location = Pick Location | Khách hàng nhận thông báo "Tài xế đã tới điểm đón" | High |
| `TC-TRIP-004` | Trạng thái Bắt đầu| Tài xế cập nhật "Bắt đầu chuyến đi" | Đã đến điểm đón | 1. Khách lên xe -> Tài xế bấm "Bắt đầu" | Start Trip | Trạng thái chuyển sang "In Progress", tính giờ chuyến | High |
| `TC-TRIP-005` | Trạng thái Kết thúc| Tài xế cập nhật "Hoàn thành chuyến đi" | Chuyến đi đang In Progress | 1. Đã tới điểm trả -> Bấm "Kết thúc" | End Trip | Chuyển sang màn hình thanh toán hóa đơn | High |
| `TC-TRIP-006` | Khách hủy miễn phí| Khách hàng hủy chuyến trong vòng 2 phút đầu | Chuyến vừa nhận <2 phút | 1. Khách bấm Hủy chuyến -> Chọn lý do | Time < 2 mins | Hủy chuyến thành công, không mất phí hủy | High |
| `TC-TRIP-007` | Khách hủy mất phí | Khách hàng hủy chuyến sau 5 phút kể từ khi TX nhận | Tài xế đã di chuyển >5 phút | 1. Khách bấm Hủy chuyến | Time > 5 mins | Hủy chuyến thành công, trừ phí phạt hủy (ví dụ: 10.000đ) | High |
| `TC-TRIP-008` | Tài xế hủy chuyến| Tài xế hủy chuyến với lý do Khách không xuất hiện | Tài xế đã chờ >10 phút | 1. Bấm Hủy -> Lý do "Không liên lạc được khách" | Waiting time > 10m | Chuyến bị hủy, khách có thể bị phạt phí chờ | High |
| `TC-TRIP-009` | Tracking GPS | Kiểm tra cập nhật vị trí Real-time của Tài xế | Chuyến đi đang diễn ra | 1. Mở map người dùng xem vị trí xe di chuyển | GPS movement | Biểu tượng xe di chuyển mượt mà trên bản đồ real-time | High |
| `TC-TRIP-010` | In-App Call | Thực hiện cuộc gọi Free-call In-App giữa Khách & TX | Chuyến đi active | 1. Bấm icon Gọi điện trên app | VoIP Call | Kết nối cuộc gọi thoại thành công | Medium |
| `TC-TRIP-011` | In-App Chat | Gửi tin nhắn In-App cho Tài xế | Chuyến đi active | 1. Nhập tin "Tôi đang đứng trước cửa A"<br>2. Bấm Gửi | Message text | Tài xế nhận được tin nhắn tức thì | Medium |
| `TC-TRIP-012` | Chat tin mẫu | Chọn các mẫu tin nhắn nhanh có sẵn | Chuyến đi active | 1. Bấm chọn mẫu "Tôi đang tới" | Quick template | Tin nhắn gửi đi thành công | Low |
| `TC-TRIP-013` | Nút SOS | Bấm nút Khẩn cấp (SOS) trong chuyến đi | Chuyến đi In Progress | 1. Nhấn nút SOS khẩn cấp<br>2. Xác nhận | Emergency trigger | Gửi cảnh báo tọa độ tới CSKH & SĐT khẩn cấp đã lưu | High |
| `TC-TRIP-014` | Thay đổi điểm trả| Khách thay đổi điểm trả trong khi đang di chuyển | Chuyến đi In Progress | 1. Khách đổi điểm trả mới trên app | New Drop location | Hệ thống tính lại cước phí phát sinh và báo Tài xế | High |
| `TC-TRIP-015` | Mất mạng giữa chừng| Mất kết nối Internet khi đang trong chuyến đi | Chuyến đi In Progress | 1. Tắt 4G thiết bị Khách | Offline mode | App lưu trạng thái chuyến đi, sync lại khi có mạng | High |
| `TC-TRIP-016` | Tài xế đi sai đường| Cảnh báo khi Tài xế đi lệch xa khỏi lộ trình gợi ý | Chuyến đi In Progress | 1. Tài xế rẽ sai đường lệch >2km | Devinated Route | App hiển thị cảnh báo route mới và tính toán lại | Medium |
| `TC-TRIP-017` | Chờ quá giờ | Bắt đầu tính Phí chờ đợi nếu tài xế phải chờ >5p | Tài xế đã ở điểm đón 5 phút | 1. Khách chưa lên xe sau 5p chờ | Waiting > 5 mins | Tự động cộng Phí chờ vào tổng tiền chuyến đi | Medium |
| `TC-TRIP-018` | Chia sẻ chuyến đi| Chia sẻ vị trí chuyến đi cho người thân qua Link | Chuyến đi In Progress | 1. Bấm "Chia sẻ hành trình"<br>2. Gửi link Zalo | Shareable URL | Người nhận click link xem được vị trí xe trên Web | Medium |
| `TC-TRIP-019` | Crash App | App bị crash ngắt đột ngột khi đang di chuyển | Chuyến đi In Progress | 1. Force kill ứng dụng<br>2. Mở lại app | Re-open App | App tự động khôi phục đúng màn hình tracking chuyến đi | High |
| `TC-TRIP-020` | Hết pin thiết bị| Máy khách hàng hết pin tắt nguồn trong chuyến đi | Chuyến đi In Progress | 1. Tắt nguồn điện thoại khách | Device Off | Chuyến đi vẫn tiếp tục bình thường phía Tài xế | Medium |
| `TC-TRIP-021` | Nhận chuyến kép | Hệ thống không phát thêm chuyến cho TX đang chạy | Tài xế đang có chuyến In Progress | 1. Khách khác đặt xe gần đó | Dispatch algorithm | Tài xế đang chạy không nhận được popup chuyến mới | High |
| `TC-TRIP-022` | Hủy tự động | Tự động hủy chuyến nếu Khách hàng không lên xe | Tài xế chờ >15 phút | 1. Hết 15p chờ không có phản hồi | Auto-cancel | Chuyến bị hủy tự động, ghi nhận lỗi do Khách | Medium |
| `TC-TRIP-023` | Lịch sử chuyến đi| Kiểm tra chuyến đi hiển thị đúng trong Lịch sử | Chuyến đi đã Hoàn thành | 1. Vào Lịch sử chuyến đi | Completed Trip ID | Hiển thị đúng đầy đủ Pick, Drop, Giá tiền, Tài xế | High |
| `TC-TRIP-024` | Xem lại hóa đơn| Xem chi tiết hóa đơn cước phí chuyến đi đã hoàn tất| Chuyến đi đã hoàn thành | 1. Click chọn chuyến đi cũ | Invoice details | Hiển thị chi tiết: Cước gốc, Surge, Phụ phí, MGG, Tổng | Medium |
| `TC-TRIP-025` | Gửi Email Invoice| Tự động gửi Email hóa đơn sau khi hoàn thành chuyến| Khách có đăng ký Email | 1. Hoàn thành chuyến đi | Check Email | Email hóa đơn PDF được gửi thành công | Low |
| `TC-TRIP-026` | TX Bật/Tắt App | Tài xế chuyển trạng thái Offline | Tài xế đang Online | 1. Gạt switch sang Offline | Status: Offline | Tài xế không còn nhận được các chuyến đi mới phát | High |
| `TC-TRIP-027` | TX Bắt buộc nghỉ| Cảnh báo/Khóa tài xế chạy liên tục >12 tiếng | Tài xế chạy 12h liên tục | 1. Hết 12 tiếng lái xe | Drive time > 12h | Tự động chuyển Offline, bắt buộc nghỉ ngơi 6 tiếng | Medium |
| `TC-TRIP-028` | Đánh giá Driver | Hệ thống chặn TX có rating trung bình quá thấp | Rating TX < 3.0 star | 1. Rating giảm xuống 2.9 | Rating = 2.9 | Tự động tạm khóa tài khoản tài xế để đào tạo lại | High |
| `TC-TRIP-029` | Ghép chuyến | Tính năng đi chung xe (CabShare - nếu SRS có) | 2 khách đặt trùng đường | 1. Khách A đặt, Khách B đặt ghép | Shared Route | Hệ thống ghép 2 khách chung 1 xe, giảm giá | Low |
| `TC-TRIP-030` | Phạt hủy nhiều lần| Cảnh báo Khách hủy chuyến quá 3 lần/ngày | Khách đã hủy 3 chuyến/ngày| 1. Thử bấm Đặt chuyến thứ 4 | Cancel count = 3 | Khóa tính năng đặt xe của khách trong 24h | Medium |
| `TC-TRIP-031` | Sai lệch khoảng cách| Xử lý khi GPS tính sai quãng đường thực tế | Chuyến đi kết thúc | 1. Quãng đường thực tế 5km, GPS tính 20km | GPS glitch | Cảnh báo sai lệch cước bất thường cho Admin kiểm tra | High |
| `TC-TRIP-032` | Tốc độ bất thường| Cảnh báo Tài xế di chuyển vượt quá tốc độ an toàn | Chuyến đi In Progress | 1. Xe chạy >100km/h trong nội thành | Speed > 100km/h | Hệ thống gửi cảnh báo an toàn tới app Tài xế | Low |
| `TC-TRIP-033` | Quên đồ trên xe| Gửi yêu cầu hỗ trợ "Tìm đồ thất lạc" trên chuyến | Chuyến đã hoàn thành | 1. Vào Chi tiết chuyến -> Bấm "Báo mất đồ" | Lost item report | Tạo ticket chăm sóc khách hàng tự động | Medium |
| `TC-TRIP-034` | Reconnect mạng | Khôi phục kết nối mạng thành công khi đang đi | Vừa mất mạng 2 phút | 1. Bật lại 4G/Wifi | Re-connected | Đồng bộ lại vị trí và cước phí chính xác ngay | High |
| `TC-TRIP-035` | Chuyến xe hẹn giờ| Hệ thống phát chuyến hẹn giờ trước 15 phút đón | Chuyến đặt lịch 14:00 | 1. Đến mốc thời gian 13:45 | Time = 13:45 | Tự động quét và phát chuyến cho tài xế gần đó | High |

---

### MODULE 4: PAYMENT & WALLET SYSTEM (THANH TOÁN & VÍ DỰ TRỮ) - 30 TEST CASES

| ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `TC-PAY-001` | Tiền mặt | Thanh toán chuyến đi bằng Tiền mặt | Chọn PTTT: Cash | 1. Chuyến kết thúc<br>2. Khách trả tiền mặt cho TX<br>3. TX bấm "Đã thu tiền" | Cash payment | Chuyến đi hoàn tất, cập nhật trạng thái đã thanh toán | High |
| `TC-PAY-002` | Ví MoMo | Thanh toán thành công qua Ví MoMo liên kết | Đã liên kết Ví MoMo | 1. Chuyến kết thúc<br>2. Tự động trừ tiền Ví MoMo | Wallet: MoMo | Trừ tiền tài khoản MoMo thành công, báo Hóa đơn | High |
| `TC-PAY-003` | Ví MoMo không đủ | Thanh toán MoMo thất bại do Số dư ví không đủ | Số dư MoMo < Tiền chuyến | 1. Kết thúc chuyến đi<br>2. Trừ tiền MoMo | Insufficient balance | Báo lỗi trừ tiền thất bại, yêu cầu chọn PTTT Tiền mặt | High |
| `TC-PAY-004` | Thẻ Visa/Master | Thanh toán thành công bằng Thẻ tín dụng quốc tế | Đã thêm thẻ Visa hợp lệ | 1. Chuyến kết thúc<br>2. Trừ tiền qua cổng Payment | Visa Card | Giao dịch thành công, gửi SMS Banking | High |
| `TC-PAY-005` | Thẻ hết hạn | Thanh toán bằng Thẻ Visa đã hết hạn | Thẻ đã hết hạn | 1. Chọn thanh toán bằng thẻ hết hạn | Expired Card | Báo lỗi: "Thẻ đã hết hạn sử dụng, vui lòng chọn PTTT khác" | Medium |
| `TC-PAY-006` | Nạp tiền vào ví | Nạp tiền vào Ví CAB System thành công | Tài khoản ngân hàng có tiền | 1. Vào Ví -> Chọn Nạp tiền<br>2. Nhập 200.000đ<br>3. Xác nhận OTP | Amount: 200,000 VNĐ | Số dư ví CAB tăng lên 200.000 VNĐ | High |
| `TC-PAY-007` | Nạp tiền âm | Nạp tiền vào ví với số tiền âm hoặc bằng 0 | Màn hình nạp tiền | 1. Nhập số tiền `-50000` hoặc `0`<br>2. Bấm Tiếp tục | Amount: -50000 | Báo lỗi: "Số tiền nạp phải lớn hơn 10.000 VNĐ" | High |
| `TC-PAY-008` | Nạp tiền nhỏ hơn | Nạp tiền dưới mức tối thiểu quy định (<10.000đ) | Màn hình nạp tiền | 1. Nhập số tiền `5000` | Amount: 5000 | Báo lỗi: "Số tiền nạp tối thiểu là 10.000 VNĐ" | Medium |
| `TC-PAY-009` | Nạp tiền quá hạn | Nạp tiền vượt hạn mức tối đa 1 lần (>10 triệu) | Màn hình nạp tiền | 1. Nhập số tiền `20.000.000` | Amount: 20M | Báo lỗi: "Số tiền nạp vượt quá hạn mức 10.000.000 VNĐ/giao dịch" | Medium |
| `TC-PAY-010` | Rút tiền ví | Rút tiền từ Ví CAB về Ngân hàng liên kết | Số dư ví = 500.000đ | 1. Vào Rút tiền<br>2. Nhập 200.000đ<br>3. Xác nhận PIN | Amount: 200,000 | Số dư ví giảm 200k, tiền chuyển về tài khoản NH | High |
| `TC-PAY-011` | Rút tiền quá số dư| Rút số tiền lớn hơn số dư hiện có trong ví | Số dư ví = 100.000đ | 1. Nhập số tiền rút `300.000` | Amount: 300,000 | Báo lỗi: "Số dư tài khoản không đủ để thực hiện" | High |
| `TC-PAY-012` | Hoàn tiền (Refund)| Hoàn tiền tự động khi Khách hủy chuyến hợp lệ | Đã trừ tiền trước qua Ví | 1. Hủy chuyến trong thời gian miễn phí | Cancel valid | Tiền cước được tự động hoàn trả vào Ví trong 30s | High |
| `TC-PAY-013` | Lịch sử giao dịch| Kiểm tra hiển thị Lịch sử giao dịch Ví chính xác | Đã thực hiện nạp/rút/trừ | 1. Vào Menu Ví -> Lịch sử giao dịch | Transaction log | Hiển thị đầy đủ Mã GD, Thời gian, Số tiền (+/-), Trạng thái | High |
| `TC-PAY-014` | Mã PIN bảo mật | Mã hóa và yêu cầu nhập Mã PIN khi dùng Ví CAB | Đã cài mã PIN Ví | 1. Thanh toán bằng Ví CAB<br>2. Nhập Mã PIN | PIN Code | Nhập đúng mới cho phép hoàn tất giao dịch | High |
| `TC-PAY-015` | Sai PIN quá 3 lần| Khóa tính năng Ví khi nhập sai Mã PIN 3 lần | Đã cài mã PIN | 1. Nhập sai PIN 3 lần liên tiếp | Wrong PIN x3 | Tạm khóa giao dịch Ví trong 24h để bảo mật | High |
| `TC-PAY-016` | Tiền TIP tài xế | Thêm tiền TIP cho Tài xế sau khi hoàn tất chuyến | Chuyến đi đã thanh toán | 1. Chọn mức TIP (10k, 20k, 50k)<br>2. Bấm Xác nhận | Tip: 20,000 VNĐ | Tiền TIP được trừ vào tài khoản khách và cộng cho TX | Medium |
| `TC-PAY-017` | Tiền TIP âm | Nhập số tiền TIP là số âm | Màn hình đánh giá/TIP | 1. Tùy chỉnh số tiền TIP `-20000` | Tip: -20000 | Chặn không cho nhập số âm | Low |
| `TC-PAY-018` | Hóa đơn chi tiết | Hiển thị chi tiết từng khoản tiền trong Hóa đơn | Kết thúc chuyến đi | 1. Xem màn hình Payment Summary | Invoice details | Hiển thị rõ: Cước chuyến, Phụ phí, Giảm giá, Tổng thu | Medium |
| `TC-PAY-019` | Trừ phí hủy chuyến| Trừ phí hủy chuyến vào lần đặt xe tiếp theo | Nợ phí hủy 10.000đ | 1. Đặt chuyến xe mới | Unpaid fee: 10k | Tổng tiền chuyến mới cộng thêm 10k phí nợ cũ | High |
| `TC-PAY-020` | Cổng TT bảo trì | Xử lý khi Cổng thanh toán ZaloPay/MoMo bị bảo trì| Gateway Maintenance | 1. Chọn thanh toán qua ZaloPay | Gate unavailable | Báo lỗi: "Cổng thanh toán đang bảo trì, vui lòng chọn PTTT khác" | High |
| `TC-PAY-021` | Xóa liên kết ví | Hủy liên kết Ví MoMo/ZaloPay khỏi ứng dụng | Đã liên kết ví | 1. Vào Cài đặt thanh toán -> Chọn Hủy liên kết | Unlink action | Hủy liên kết thành công, xóa token thanh toán | Medium |
| `TC-PAY-022` | Thêm thẻ trùng | Thêm lại một thẻ Visa đã được liên kết trước đó| Thẻ Visa A đã có | 1. Nhập thông tin thẻ Visa A lần nữa | Duplicate Card | Báo lỗi: "Thẻ này đã được thêm trên hệ thống" | Medium |
| `TC-PAY-023` | Liên kết thẻ sai | Thêm thẻ Visa với mã CVC/CVV sai | Màn hình thêm thẻ | 1. Nhập số thẻ đúng, mã CVV sai | Wrong CVV | Báo lỗi: "Thông tin xác thực thẻ không chính xác" | High |
| `TC-PAY-024` | Thanh toán nợ | Yêu cầu thanh toán Nợ cũ trước khi đặt chuyến mới| Tài khoản đang nợ cước | 1. Bấm Đặt xe | Unpaid debt | Yêu cầu thanh toán hết nợ cũ mới cho phép đặt xe | High |
| `TC-PAY-025` | Cashout Tài xế | Tài xế rút tiền thu nhập từ Ví Driver về Ngân hàng| Số dư ví TX > 200k | 1. TX bấm Rút tiền về Vietcombank | Driver withdrawal | Tiền trừ khỏi ví TX và chuyển về ngân hàng thành công | High |
| `TC-PAY-026` | Chiết khấu ứng dụng| Tự động trừ % Chiết khấu hệ thống vào ví Tài xế | Chuyến đi 100k (Chiết khấu 20%)| 1. Hoàn thành chuyến đi | App commission: 20% | Ví tài xế tự động bị trừ 20.000đ tiền phí nền tảng | High |
| `TC-PAY-027` | Đồng tiền tệ | Kiểm tra xử lý đồng tiền VNĐ (Không hỗ trợ lẻ cent)| Màn hình thanh toán | 1. Kiểm tra tính toán cước phí | Currency: VND | Tất cả giá tiền đều được làm tròn đến hàng đơn vị Đồng | Low |
| `TC-PAY-028` | Timeout GD | Hết thời gian chờ thanh toán Online (Gateway Timeout)| Đang ở trang thanh toán VNPAY | 1. Không thao tác quá 15 phút | Timeout 15m | Hủy giao dịch thanh toán và thông báo về ứng dụng | Medium |
| `TC-PAY-029` | Double Payment | Chống trừ tiền trùng lặp (Double Deduction) | Mạng chập chờn khi bấm | 1. Bấm nút Thanh toán 2 lần liên tiếp thật nhanh | Double click | Hệ thống chỉ ghi nhận và trừ tiền 1 lần duy nhất | High |
| `TC-PAY-030` | Lỗi kết nối Bank | Xử lý sự cố ngân hàng từ chối giao dịch | Ngân hàng lỗi System | 1. Thanh toán bằng thẻ ATM Napas | Bank error | Hiển thị thông báo: "Giao dịch bị từ chối bởi Ngân hàng phát hành" | Medium |

---

### MODULE 5: RATING, FEEDBACK & NOTIFICATION (ĐÁNH GIÁ & CẢNH BÁO) - 20 TEST CASES

| ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `TC-RATE-001` | Đánh giá 5 sao | Khách đánh giá 5 sao kèm nhận xét khen ngợi | Chuyến đi vừa kết thúc | 1. Chọn 5 sao<br>2. Nhập "Tài xế thân thiện"<br>3. Bấm Gửi | 5 Stars / Good | Lưu đánh giá thành công, tăng Rating trung bình của TX | High |
| `TC-RATE-002` | Đánh giá 1 sao | Khách đánh giá 1 sao kèm chọn các Tag lý do tiêu cực | Chuyến đi vừa kết thúc | 1. Chọn 1 sao<br>2. Tích chọn "Chạy ẩu", "Mất lịch sự"<br>3. Bấm Gửi | 1 Star / Bad tags | Lưu đánh giá, giảm Rating TX và gửi alert cho CSKH | High |
| `TC-RATE-003` | Bỏ qua Đánh giá | Khách bấm "Bỏ qua" không thực hiện đánh giá | Chuyến đi vừa kết thúc | 1. Bấm nút "Bỏ qua" hoặc icon "X" | Skip action | Bỏ qua màn đánh giá, quay về Trang chủ | Medium |
| `TC-RATE-004` | Nhận xét chứa từ cấm| Nhập nội dung nhận xét chứa từ ngữ thô tục | Màn hình đánh giá | 1. Nhập từ ngữ xúc phạm/thô tục<br>2. Bấm Gửi | Bad words | Hệ thống chặn hoặc tự động che bằng dấu `***` | Medium |
| `TC-RATE-005` | Đánh giá quá dài | Nhập đoạn văn nhận xét dài quá 500 ký tự | Màn hình đánh giá | 1. Nhập chuỗi 600 ký tự<br>2. Bấm Gửi | Text >500 chars | Giới hạn không cho gõ quá 500 ký tự | Low |
| `TC-RATE-006` | Sửa đánh giá | Chỉnh sửa lại đánh giá trong vòng 24h | Đã gửi đánh giá trước đó | 1. Vào Chi tiết chuyến -> Bấm "Sửa đánh giá"<br>2. Đổi từ 3 sao lên 5 sao | Change to 5 stars | Cập nhật lại số sao và nhận xét mới | Low |
| `TC-RATE-007` | Tài xế đánh giá Khách| Tài xế thực hiện đánh giá Khách hàng (1-5 sao) | Chuyến đi vừa kết thúc | 1. Tài xế chọn 5 sao cho Khách<br>2. Bấm Gửi | Driver rates User | Lưu điểm uy tín cho tài khoản Khách hàng | Medium |
| `TC-RATE-008` | Báo cáo khiếu nại | Báo cáo sự cố "Tài xế thu thừa tiền" | Chuyến đi đã xong | 1. Chọn "Gửi khiếu nại"<br>2. Chọn lý do "Thu sai tiền"<br>3. Bấm Gửi | Complaint: Overcharge | Tạo Ticket hỗ trợ trên trang Admin CSKH | High |
| `TC-RATE-009` | Khắc phục sự cố | Khách gửi ảnh chụp màn hình bằng chứng khiếu nại | Màn hình gửi khiếu nại | 1. Đính kèm 2 ảnh bằng chứng (.JPG)<br>2. Bấm Gửi | Attach images | Tải ảnh lên hệ thống CSKH thành công | Medium |
| `TC-RATE-010` | Push Notification | Nhận Push Notification khi Tài xế nhận chuyến | App ở chế độ background | 1. Tài xế nhấn nhận chuyến | System Push | Điện thoại khách nhận thông báo đẩy: "Tài xế A đã nhận chuyến" | High |
| `TC-RATE-011` | Push Notification | Nhận Push Notification khi Tài xế đã tới nơi | App đang tắt | 1. Tài xế nhấn "Đã đến" | System Push | Điện thoại khách đổ chuông thông báo xe đã tới | High |
| `TC-RATE-012` | Push Promo | Nhận thông báo Khuyến mãi/Marketing từ hệ thống | Admin phát thông báo | 1. Admin gửi Broadcast Promo | Marketing Push | Nhận thông báo ưu đãi giảm giá trong Notification Center | Low |
| `TC-RATE-013` | Tắt Thông báo | Tắt nhận Push Notification trong Cài đặt App | Cài đặt ứng dụng | 1. Bật Tắt "Nhận thông báo Khuyến mãi" | Switch OFF | Không nhận các thông báo Marketing nữa | Low |
| `TC-RATE-014` | Đọc tất cả | Bấm "Đánh dấu tất cả là đã đọc" trong Hộp thư | Có 5 thông báo chưa đọc | 1. Bấm icon "Đọc tất cả" | Mark as read | Tất cả thông báo chuyển sang trạng thái Đã đọc | Low |
| `TC-RATE-015` | Xóa thông báo | Xóa 1 thông báo khỏi Hộp thư ứng dụng | Danh sách thông báo | 1. Vuốt sang trái thông báo -> Chọn Xóa | Delete item | Thông báo bị xóa khỏi danh sách | Low |
| `TC-RATE-016` | Cảnh báo An toàn | Nhận cảnh báo SOS khi chuyến đi có bất thường | Kích hoạt SOS | 1. Nút SOS được kích hoạt | Emergency Alert | Đổ chuông thông báo âm lượng cao tới người thân | High |
| `TC-RATE-017` | Báo cáo tài xế giả | Khởi tạo báo cáo "Bảng số xe không khớp thực tế" | Trước khi lên xe | 1. Chọn Báo cáo -> "Biển số xe khác với App" | Incident Report | Hệ thống ghi nhận sự cố và đề xuất hủy chuyến miễn phí | High |
| `TC-RATE-018` | Đánh giá App Store | Nhắc nhở người dùng Đánh giá App sau 5 chuyến thành công | Đã đi đủ 5 chuyến | 1. Hoàn thành chuyến thứ 5 | In-App Review | Hiển thị Popup mời đánh giá App trên AppStore/CHPlay | Low |
| `TC-RATE-019` | Phản hồi CSKH | Nhận thông báo khi CSKH phản hồi Ticket khiếu nại | CSKH đã trả lời Ticket | 1. CSKH bấm gửi câu trả lời | Ticket resolved | Khách nhận Notification & Email kết quả xử lý | Medium |
| `TC-RATE-020` | Khảo sát trải nghiệm| Hiển thị Form khảo sát ngắn sau khi dùng dịch vụ 1 tháng | Tài khoản dùng 30 ngày | 1. Mở app vào ngày thứ 30 | Survey Popup | Hiển thị bảng khảo sát trải nghiệm dịch vụ | Low |

---

### MODULE 6: ADMIN PORTAL & SYSTEM MANAGEMENT (TRANG QUẢN TRỊ ADMIN) - 35 TEST CASES

| ID | Test Scenario | Test Case | Preconditions | Test Steps | Test Data | Expected Result | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `TC-ADM-001` | Admin Login | Đăng nhập Admin Portal với tài khoản Quản trị viên | Tài khoản Admin tồn tại | 1. Nhập Username/Pass Admin<br>2. Bấm Login | Admin / `AdminPass@123` | Đăng nhập thành công, vào Dashboard Dashboard | High |
| `TC-ADM-002` | Admin Login sai | Đăng nhập Admin Portal với sai Mật khẩu | Màn hình Login Admin | 1. Nhập sai Pass Admin<br>2. Bấm Login | Admin / `WrongPass` | Báo lỗi đăng nhập thất bại | High |
| `TC-ADM-003` | Duyệt Tài xế | Admin duyệt Hồ sơ Tài xế mới đăng ký hợp lệ | Tài xế đã upload đủ GPLX, Căn cước | 1. Mở xem chi tiết hồ sơ<br>2. Bấm nút "Duyệt" | Driver Status: Pending | Tài xế chuyển sang trạng thái Approved, có thể nhận chuyến | High |
| `TC-ADM-004` | Từ chối Tài xế | Admin từ chối Hồ sơ Tài xế do mờ ảnh GPLX | Hồ sơ bị mờ | 1. Bấm "Từ chối"<br>2. Nhập lý do "Bằng lái bị mờ"<br>3. Bấm Gửi | Reject Reason | Tài xế nhận thông báo yêu cầu chụp lại GPLX | High |
| `TC-ADM-005` | Khóa Tài xế | Admin thực hiện Khóa tài khoản Tài xế vi phạm | Tài xế bị tố cáo | 1. Chọn tài khoản TX<br>2. Bấm "Khóa tài khoản"<br>3. Chọn "Khóa 7 ngày" | Lock Driver | Tài xế bị đăng xuất và không thể đăng nhập trong 7 ngày | High |
| `TC-ADM-006` | Mở khóa Tài khoản| Admin Mở khóa cho tài khoản Người dùng / Tài xế | Tài khoản đang bị Locked | 1. Chọn tài khoản -> Bấm "Mở khóa" | Unlock Account | Tài khoản quay lại trạng thái Active bình thường | Medium |
| `TC-ADM-007` | Cấu hình Bảng giá| Admin thay đổi Giá cước cơ bản của dịch vụ Cab4 | Màn hình Pricing Config | 1. Nhập Giá mở cửa mới: `12.000đ`<br>2. Bấm "Lưu thay đổi" | New Base Price: 12k | Hệ thống áp dụng bảng giá mới cho toàn bộ chuyến đặt sau đó | High |
| `TC-ADM-008` | Cấu hình Surge | Admin kích hoạt hệ số Surge Pricing thủ công theo khu vực | Màn hình Surge Config | 1. Chọn khu vực Quận 1<br>2. Đặt hệ số `1.8x`<br>3. Bấm Kích hoạt | Zone: Q1, Ratio: 1.8 | Toàn bộ chuyến xe ở Quận 1 nhân giá 1.8x | High |
| `TC-ADM-009` | Tạo Mã giảm giá | Admin tạo MGG mới áp dụng toàn hệ thống | Màn hình Campaign | 1. Nhập mã `TET2026`, giảm 30%, Hạn 31/01<br>2. Bấm "Tạo MGG" | Promo Config | Mã giảm giá được lưu và cho phép người dùng áp dụng | High |
| `TC-ADM-010` | Xóa Mã giảm giá | Admin Tắt/Hủy mã giảm giá đang chạy trước thời hạn | Mã `SUMMER` đang Active | 1. Bấm "Vô hiệu hóa" mã `SUMMER` | Disable Code | Người dùng không thể áp dụng mã này nữa | Medium |
| `TC-ADM-011` | Phân quyền Admin | Admin Master tạo tài khoản CSKH (Giới hạn quyền) | Quyền Admin Master | 1. Tạo user CSKH01<br>2. Gán Role "Support Agent"<br>3. Bấm Lưu | Role: Support Agent | User CSKH01 chỉ xem/xử lý ticket, không chỉnh được Giá cước | High |
| `TC-ADM-012` | Xuất Báo cáo Excel| Xuất Báo cáo Doanh thu theo tháng ra file Excel | Màn hình Report | 1. Chọn Tháng 09/2026<br>2. Bấm "Xuất Excel" | Export Excel | File .XLSX được tải về chứa đầy đủ số liệu | Medium |
| `TC-ADM-013` | Xuất Báo cáo PDF | Xuất Báo cáo danh sách chuyến đi ra file PDF | Màn hình Report | 1. Chọn khoảng ngày<br>2. Bấm "In/Xuất PDF" | Export PDF | File .PDF được tạo đúng định dạng bảng biểu | Low |
| `TC-ADM-014` | Giám sát Realtime| Xem Bản đồ Giám sát vị trí toàn bộ xe đang Online | Màn hình Live Map | 1. Truy cập trang Live Monitoring | Realtime Map | Bản đồ hiển thị vị trí tất cả các xe đang hoạt động | Medium |
| `TC-ADM-015` | Xử lý Ticket | CSKH tiếp nhận và Đóng Ticket khiếu nại của Khách | Ticket đang Open | 1. Mở Ticket #123<br>2. Nhập nội dung xử lý -> Chọn "Resolved" | Status: Resolved | Ticket đóng, gửi thông báo kết quả cho Khách | High |
| `TC-ADM-016` | Cộng tiền ví CSKH| CSKH hoàn tiền đền bù vào Ví người dùng | Khiếu nại đúng | 1. Nhập số tiền đền bù `50.000đ`<br>2. Nhập lý do<br>3. Bấm "Cộng tiền" | Refund: 50,000 VNĐ | Ví của Khách được cộng 50k, ghi nhận Log đền bù | High |
| `TC-ADM-017` | Tìm kiếm User | Tìm kiếm người dùng theo SĐT hoặc Email trên Admin | Màn hình User List | 1. Nhập SĐT `0901234567` vào ô Tìm kiếm | Search: 0901234567 | Hiển thị chính xác thông tin tài khoản tương ứng | Medium |
| `TC-ADM-018` | Tìm kiếm không thấy| Tìm kiếm thông tin với SĐT không tồn tại | Màn hình User List | 1. Nhập SĐT `0000000000` | Search: 0000000000 | Hiển thị "Không tìm thấy dữ liệu phù hợp" | Low |
| `TC-ADM-019` | Filter Chuyến đi | Lọc danh sách chuyến đi theo Trạng thái (Đã hủy) | Màn hình Trip List | 1. Chọn Filter "Status = Canceled"<br>2. Bấm Lọc | Filter Canceled | Chỉ hiển thị danh sách các chuyến đi bị hủy | Medium |
| `TC-ADM-020` | Broadcast Notification| Admin gửi Thông báo đẩy toàn hệ thống (All Users) | Màn hình Push Center | 1. Nhập Tiêu đề & Nội dung<br>2. Chọn Target: All<br>3. Bấm Gửi | Global Push Notification | Tất cả App Khách hàng nhận được thông báo | Medium |
| `TC-ADM-021` | Xem System Logs | Kiểm tra Nhật ký thao tác của Admin (Audit Logs) | Màn hình Audit Log | 1. Mở xem Lịch sử thao tác Admin | Audit Trail | Hiển thị rõ Admin A đã sửa giá cước vào lúc hh:mm dd/mm | Low |
| `TC-ADM-022` | Quản lý Ban kính | Cấu hình bán kính tối đa phát chuyến đi (Ví dụ 5km) | Màn hình Dispatch Rules | 1. Đặt Radius = 5km<br>2. Bấm Lưu | Radius: 5km | Hệ thống chỉ phát chuyến cho TX trong bán kính 5km | High |
| `TC-ADM-023` | Cấu hình Timeout | Cấu hình thời gian cho TX phản hồi nhận chuyến (15s)| Màn hình Dispatch Rules | 1. Đặt Timeout = 15s<br>2. Bấm Lưu | Timeout: 15s | Popup nhận chuyến trên App TX tự tắt sau 15 giây | Medium |
| `TC-ADM-024` | Đổi Mật khẩu Admin| Admin thực hiện đổi mật khẩu tài khoản quản trị | Đã login Admin | 1. Nhập Pass cũ, Pass mới hợp lệ<br>2. Bấm Đổi MK | Change Pass Admin | Đổi mật khẩu thành công | Medium |
| `TC-ADM-025` | Session Timeout | Tự động đăng xuất Admin nếu không thao tác 30 phút | Admin treo máy 30p | 1. Không di chuyển chuột/bàn phím 30 phút | Inactive 30 mins | Tự động Log out về màn hình Login Admin để bảo mật | High |
| `TC-ADM-026` | Quản lý Loại xe | Thêm mới loại phương tiện phục vụ (Ví dụ: Premium) | Màn hình Vehicle Type | 1. Bấm "Thêm loại xe"<br>2. Nhập CabPremium, định mức giá | New Vehicle Type | Loại xe mới xuất hiện trên ứng dụng người dùng | High |
| `TC-ADM-027` | Báo cáo Vi phạm | Xem danh sách Tài xế bị đánh giá 1 sao nhiều lần | Màn hình Monitoring | 1. Chọn báo cáo "Tài xế cảnh báo" | Warning Driver List | Hiển thị danh sách TX có >3 lượt 1 sao trong tuần | Medium |
| `TC-ADM-028` | Dashboard Doanh thu| Dashboard hiển thị đúng Tổng Doanh thu trong ngày | Có 100 chuyến hoàn tất | 1. Mở xem Dashboard trang chủ Admin | Revenue Chart | Biểu đồ & Số tiền hiển thị chính xác tổng cước | High |
| `TC-ADM-029` | Xóa Dữ liệu | Thử xóa Tài khoản đã có lịch sử chuyến đi | Tài khoản đã đi 10 chuyến| 1. Bấm Xóa tài khoản | Delete User with history | Chặn xóa vĩnh viễn, chỉ chuyển trạng thái Deactive (Soft Delete) | High |
| `TC-ADM-030` | Phân trang (Paging)| Kiểm tra phân trang danh sách (20 record/trang) | Danh sách 100 User | 1. Bấm chuyển sang Trang 2, Trang 3 | Pagination | Hiển thị chính xác 20 kết quả trên mỗi trang | Low |
| `TC-ADM-031` | Sắp xếp dữ liệu | Sắp xếp Danh sách Chuyến đi theo Giá tiền giảm dần | Màn hình Trip List | 1. Click vào cột "Tổng tiền" | Sort Descending | Danh sách tự động sắp xếp chuyến tiền cao nhất lên đầu | Low |
| `TC-ADM-032` | Cấu hình Phạt hủy | Cấu hình Số tiền phạt hủy chuyến đối với Khách | Màn hình Fee Config | 1. Đặt Cancellation Fee = 15.000đ | Fee: 15k | Áp dụng trừ 15k khi khách hủy chuyến muộn | Medium |
| `TC-ADM-033` | Quản lý Khu vực | Thêm mới Tỉnh/Thành phố mở rộng dịch vụ (Đà Nẵng)| Màn hình Geo Config | 1. Bấm Thêm Tỉnh/Thành -> Chọn "Đà Nẵng"<br>2. Bật Active | New Zone: Da Nang | Cho phép người dùng đặt xe tại khu vực Đà Nẵng | Medium |
| `TC-ADM-034` | Backup Dữ liệu | Khởi chạy Sao lưu Dữ liệu hệ thống thủ công | Quản trị Hệ thống | 1. Bấm "Backup Database Now" | Manual Backup | Tạo file Backup cơ sở dữ liệu thành công | High |
| `TC-ADM-035` | SQL Injection Admin| Kiểm tra bảo mật SQL Injection trên thanh Search Admin| Màn hình Admin Search | 1. Nhập `' OR 1=1 --` vào ô Tìm kiếm Admin | SQL Injection String | Chặn truy vấn độc hại, hiển thị không có kết quả | High |

---
*Hoàn tất bộ 200 Test Cases cho hệ thống CABSYSTEM.*
```

I have generated the full set of 200 test cases for the **CABSYSTEM** application into the markdown file `CAB_System_200_Test_Cases.md`.

### Summary of Coverage
- **Module 1: Authentication & User Profile (35 Test Cases):** Positive/Negative logins, Password limits (<5 chars), Whitespace, Security (SQLi/XSS), OTP verification, Profile updates.
- **Module 2: Booking & Fare Calculation (45 Test Cases):** Multi-vehicle types (Cab4, Cab7, Bike), Advance booking limits, Dynamic pricing (Surge/Weather/Holiday), Vouchers, Stops, and Map edge cases.
- **Module 3: Trip Execution & Dispatch (35 Test Cases):** Driver accept/reject flows, Real-time GPS tracking, In-app VoIP/Chat, Emergency SOS, Deviations, Cancellations, and Off-line reconnection.
- **Module 4: Payment & Wallet System (30 Test Cases):** Cash, E-Wallets (MoMo/ZaloPay), Cards (Visa/Master), Refund flows, Top-up/Withdrawal limits, and Driver cashouts.
- **Module 5: Rating, Feedback & Notifications (20 Test Cases):** Star ratings, Bad words filter, In-app ticketing, and Push Notifications.
- **Module 6: Admin Portal & System Management (35 Test Cases):** Driver approvals, Fare & Surge configuration, Voucher campaigns, Role permissions, and Data exports.