TÀI LIỆU ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS)

Tên hệ thống: Website bán hàng trực tuyến
Phiên bản: 1.0
Ngày: 13/09/2026

1. Giới thiệu
1.1. Mục đích

Hệ thống Website bán hàng trực tuyến được xây dựng nhằm hỗ trợ khách hàng tìm kiếm, xem và mua sản phẩm trên Internet. Đồng thời, hệ thống cung cấp cho nhân viên và quản trị viên các chức năng quản lý sản phẩm, đơn hàng và người dùng.

Tài liệu SRS này mô tả các yêu cầu chức năng, yêu cầu phi chức năng, giao diện và các ràng buộc của hệ thống.

1.2. Phạm vi

Hệ thống bao gồm:

Quản lý tài khoản người dùng
Đăng ký và đăng nhập
Xem và tìm kiếm sản phẩm
Quản lý giỏ hàng
Đặt hàng
Thanh toán
Theo dõi đơn hàng
Quản lý sản phẩm
Quản lý đơn hàng
Quản lý người dùng
Thống kê doanh thu

Hệ thống không bao gồm việc trực tiếp vận chuyển hàng hóa. Việc vận chuyển được thực hiện bởi đơn vị giao hàng bên ngoài.

1.3. Đối tượng sử dụng
Người dùng	Quyền
Khách hàng	Xem sản phẩm, mua hàng, quản lý đơn hàng
Nhân viên	Xử lý và cập nhật đơn hàng
Admin	Quản lý toàn bộ hệ thống
2. Mô tả tổng quan
2.1. Mục tiêu hệ thống

Hệ thống cho phép khách hàng thực hiện quá trình mua hàng trực tuyến từ lúc tìm kiếm sản phẩm cho đến khi hoàn tất đặt hàng.

Quy trình cơ bản:

Khách hàng → Đăng nhập/Đăng ký → Tìm kiếm sản phẩm → Xem chi tiết → Thêm vào giỏ hàng → Đặt hàng → Thanh toán → Theo dõi đơn hàng

2.2. Actor
Khách hàng
Đăng ký tài khoản
Đăng nhập
Xem sản phẩm
Tìm kiếm sản phẩm
Thêm sản phẩm vào giỏ hàng
Đặt hàng
Thanh toán
Xem lịch sử mua hàng
Hủy đơn hàng theo điều kiện cho phép
Nhân viên
Đăng nhập trang quản trị
Xem đơn hàng
Xác nhận đơn hàng
Cập nhật trạng thái đơn hàng
Xem thông tin khách hàng
Admin
Quản lý sản phẩm
Quản lý người dùng
Quản lý danh mục
Quản lý đơn hàng
Xem báo cáo doanh thu
Phân quyền người dùng
3. Yêu cầu chức năng
3.1. FR-01 - Đăng ký tài khoản

Mô tả: Hệ thống cho phép khách hàng tạo tài khoản mới.

Dữ liệu nhập:

Họ tên
Email
Số điện thoại
Mật khẩu
Xác nhận mật khẩu

Quy trình:

Người dùng nhập thông tin.
Hệ thống kiểm tra dữ liệu.
Hệ thống kiểm tra email đã tồn tại hay chưa.
Nếu thông tin hợp lệ, hệ thống tạo tài khoản.
Hệ thống thông báo đăng ký thành công.

Ngoại lệ:

Email đã tồn tại → Hiển thị thông báo lỗi.
Mật khẩu xác nhận không trùng → Hiển thị thông báo lỗi.
Thiếu thông tin bắt buộc → Yêu cầu nhập lại.
3.2. FR-02 - Đăng nhập

Mô tả: Hệ thống cho phép người dùng đăng nhập bằng email và mật khẩu.

Quy trình:

Người dùng nhập email và mật khẩu.
Hệ thống kiểm tra thông tin.
Nếu chính xác, hệ thống cho phép đăng nhập.
Nếu không chính xác, hệ thống hiển thị thông báo lỗi.
3.3. FR-03 - Xem sản phẩm

Hệ thống cho phép khách hàng:

Xem danh sách sản phẩm
Xem hình ảnh sản phẩm
Xem tên sản phẩm
Xem giá sản phẩm
Xem số lượng còn lại
Xem mô tả sản phẩm
3.4. FR-04 - Tìm kiếm sản phẩm

Người dùng có thể tìm kiếm sản phẩm theo:

Tên sản phẩm
Danh mục
Khoảng giá

Hệ thống trả về danh sách sản phẩm phù hợp với điều kiện tìm kiếm.

3.5. FR-05 - Quản lý giỏ hàng

Khách hàng có thể:

Thêm sản phẩm vào giỏ hàng
Xóa sản phẩm khỏi giỏ hàng
Tăng số lượng sản phẩm
Giảm số lượng sản phẩm
Xem tổng tiền

Hệ thống phải kiểm tra số lượng sản phẩm trong kho trước khi cho phép thêm hoặc tăng số lượng.

3.6. FR-06 - Đặt hàng

Khách hàng chọn chức năng "Đặt hàng" từ giỏ hàng.

Hệ thống yêu cầu:

Họ tên người nhận
Số điện thoại
Địa chỉ giao hàng
Phương thức thanh toán

Sau khi xác nhận, hệ thống tạo đơn hàng với trạng thái "Chờ xác nhận".

Hệ thống tạo một mã đơn hàng duy nhất cho mỗi đơn hàng.

3.7. FR-07 - Thanh toán

Hệ thống hỗ trợ:

Thanh toán khi nhận hàng (COD)
Thanh toán trực tuyến

Nếu thanh toán trực tuyến thành công, trạng thái thanh toán được cập nhật thành "Đã thanh toán".

Nếu thanh toán thất bại, hệ thống hiển thị thông báo lỗi và cho phép khách hàng thực hiện thanh toán lại.

3.8. FR-08 - Theo dõi đơn hàng

Khách hàng có thể xem trạng thái đơn hàng.

Các trạng thái chính:

Chờ xác nhận
Đã xác nhận
Đang giao
Đã giao
Đã hủy
3.9. FR-09 - Quản lý sản phẩm

Admin có thể:

Thêm sản phẩm
Sửa sản phẩm
Xóa sản phẩm
Cập nhật giá
Cập nhật số lượng
Cập nhật hình ảnh
Cập nhật mô tả
Phân loại sản phẩm
3.10. FR-10 - Quản lý đơn hàng

Nhân viên và Admin có thể:

Xem danh sách đơn hàng
Xem chi tiết đơn hàng
Xác nhận đơn hàng
Cập nhật trạng thái đơn hàng
Hủy đơn hàng khi cần thiết
3.11. FR-11 - Quản lý người dùng

Admin có thể:

Xem danh sách người dùng
Xem thông tin tài khoản
Khóa tài khoản
Mở khóa tài khoản
Phân quyền người dùng
3.12. FR-12 - Thống kê

Admin có thể xem:

Tổng số đơn hàng
Tổng doanh thu
Số lượng sản phẩm đã bán
Doanh thu theo ngày/tháng/năm
Sản phẩm bán chạy
4. Yêu cầu phi chức năng
4.1. NFR-01 - Hiệu năng
Trang web phải phản hồi trong tối đa 2 giây đối với các thao tác thông thường.
Hệ thống phải hỗ trợ nhiều người dùng đồng thời.
Hình ảnh phải được tối ưu để giảm thời gian tải trang.
4.2. NFR-02 - Bảo mật
Mật khẩu người dùng phải được lưu dưới dạng mã hóa/băm an toàn.
Người dùng không được truy cập chức năng Admin nếu không có quyền.
Hệ thống phải kiểm tra dữ liệu đầu vào.
Phiên đăng nhập phải có cơ chế hết hạn.
4.3. NFR-03 - Khả năng sử dụng
Giao diện phải dễ sử dụng.
Các nút chức năng phải có tên rõ ràng.
Website phải hiển thị tốt trên máy tính, tablet và điện thoại.
4.4. NFR-04 - Độ tin cậy
Dữ liệu đơn hàng không được mất khi hệ thống gặp lỗi.
Database phải được sao lưu định kỳ.
Hệ thống phải ghi nhận lỗi để hỗ trợ việc kiểm tra và xử lý.
5. Use Case
5.1. Danh sách Use Case
Khách hàng
UC-01: Đăng ký
UC-02: Đăng nhập
UC-03: Xem sản phẩm
UC-04: Tìm kiếm sản phẩm
UC-05: Quản lý giỏ hàng
UC-06: Đặt hàng
UC-07: Thanh toán
UC-08: Theo dõi đơn hàng
Nhân viên
UC-09: Quản lý đơn hàng
UC-10: Cập nhật trạng thái đơn hàng
Admin
UC-11: Quản lý sản phẩm
UC-12: Quản lý người dùng
UC-13: Quản lý danh mục
UC-14: Thống kê doanh thu
6. Chi tiết Use Case - Đặt hàng

Use Case: UC-06 - Đặt hàng

Actor: Khách hàng

Pre-condition:

Khách hàng đã đăng nhập.
Giỏ hàng có ít nhất một sản phẩm.
Sản phẩm vẫn còn hàng.

Main Flow:

Khách hàng mở giỏ hàng.
Khách hàng chọn "Đặt hàng".
Hệ thống hiển thị thông tin đơn hàng.
Khách hàng nhập địa chỉ giao hàng.
Khách hàng chọn phương thức thanh toán.
Khách hàng xác nhận đặt hàng.
Hệ thống kiểm tra sản phẩm.
Hệ thống tạo đơn hàng.
Hệ thống cập nhật số lượng sản phẩm trong kho.
Hệ thống hiển thị mã đơn hàng.

Alternative Flow:

Nếu sản phẩm hết hàng, hệ thống thông báo và yêu cầu cập nhật giỏ hàng.
Nếu thanh toán thất bại, hệ thống thông báo lỗi.
Nếu thông tin giao hàng không hợp lệ, hệ thống yêu cầu nhập lại.

Post-condition:

Đơn hàng được tạo thành công.
Trạng thái đơn hàng là "Chờ xác nhận".
7. Thiết kế dữ liệu
7.1. Bảng USER
Trường	Kiểu dữ liệu	Mô tả
UserID	INT	Khóa chính
Name	VARCHAR	Họ tên
Email	VARCHAR	Email
Password	VARCHAR	Mật khẩu
Phone	VARCHAR	Số điện thoại
Role	VARCHAR	Quyền người dùng
7.2. Bảng PRODUCT
Trường	Kiểu dữ liệu	Mô tả
ProductID	INT	Khóa chính
ProductName	VARCHAR	Tên sản phẩm
Price	DECIMAL	Giá sản phẩm
Quantity	INT	Số lượng
Description	TEXT	Mô tả
CategoryID	INT	Mã danh mục
7.3. Bảng ORDER
Trường	Kiểu dữ liệu	Mô tả
OrderID	INT	Khóa chính
UserID	INT	Người đặt hàng
OrderDate	DATETIME	Ngày đặt hàng
Total	DECIMAL	Tổng tiền
Status	VARCHAR	Trạng thái
7.4. Bảng ORDER_DETAIL
Trường	Kiểu dữ liệu	Mô tả
OrderID	INT	Mã đơn hàng
ProductID	INT	Mã sản phẩm
Quantity	INT	Số lượng
Price	DECIMAL	Giá bán
7.5. Quan hệ giữa các bảng
USER 1 - N ORDER
ORDER 1 - N ORDER_DETAIL
PRODUCT 1 - N ORDER_DETAIL
CATEGORY 1 - N PRODUCT
8. Yêu cầu giao diện

Hệ thống gồm các màn hình chính:

Trang chủ
Trang đăng ký
Trang đăng nhập
Trang danh sách sản phẩm
Trang chi tiết sản phẩm
Trang giỏ hàng
Trang thanh toán
Trang lịch sử đơn hàng
Trang quản trị
Trang quản lý sản phẩm
Trang quản lý đơn hàng
Trang quản lý người dùng
Trang thống kê
9. Quy tắc nghiệp vụ
Một tài khoản phải có email duy nhất.
Số lượng đặt hàng không được vượt quá số lượng tồn kho.
Chỉ Admin mới được thêm, sửa hoặc xóa sản phẩm.
Chỉ Nhân viên/Admin mới được cập nhật trạng thái đơn hàng.
Khách hàng chỉ được xem đơn hàng của chính mình.
Đơn hàng đã giao không được phép hủy.
Tổng tiền đơn hàng phải bằng tổng giá trị các sản phẩm trong đơn.
Người dùng không có quyền Admin không được truy cập trang quản trị.
10. Tiêu chí nghiệm thu

Hệ thống được xem là đáp ứng yêu cầu khi:

Người dùng đăng ký tài khoản thành công.
Người dùng đăng nhập thành công.
Khách hàng tìm kiếm và xem được sản phẩm.
Khách hàng thêm và xóa sản phẩm khỏi giỏ hàng.
Khách hàng đặt được đơn hàng hợp lệ.
Hệ thống tính tổng tiền chính xác.
Hệ thống cập nhật tồn kho sau khi đặt hàng.
Nhân viên có thể xử lý đơn hàng.
Admin có thể quản lý sản phẩm.
Admin có thể quản lý người dùng.
Người không có quyền không thể truy cập trang Admin.
Dữ liệu được lưu trữ chính xác trong database.
Hệ thống đáp ứng các yêu cầu về hiệu năng và bảo mật.
