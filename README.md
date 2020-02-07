# EzGift API

## Requirements
 - MySQL
 - Node 8.9.1 or higher
 - Redis server
## Installing
 - npm i
## Development
 - npm run dev
## Test
 - npm test
## Deployment
 - npm run build
 - npm start

## Environment Variables
Make sure to create your empty database `ezgift_local` (and `ezgift_test` if you want `run npm test`) on your computer first if you are working locally. 

At the root of the project, create a `.env` and a `.env.test` with these values (note you need to have a different name for your test database):
```
DB_USER=root
DB_PASSWORD=root
DB_HOST=localhost
DB_NAME=ezgift_local
DB_PORT=3306
APP_NAME=EzGift
JWT_SECRET=secret
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_S3_BUCKET=
SERVER_PORT=3001
```
## Setup Database
Run in Postman or in your browser to delete and setup all the tables in your database. Make sure to set the correct configuration for the database connection in `.env` and create the empty database `ezgift_local`, `ezgift_test`:
```
GET /mysql
```

## Postman
Please import postman collection and environment to use it from the `<root>/postman/` folder.

## Error code Table

| Error code  | Description (EN) | Description (VI) |
| ------------- | ------------- | ------------- | 
| 1  | Permission denied| Không được cấp quyền |
| 2  | Not authorized | Không được cấp phép |
| 3  | Invalid credentials  | Thông tin đăng nhập không hợp lệ |
| 4  | Path not found | Không tìm thấy dẫn |
| 100  | The start date/ end date is invalid or missing. Correct format is  YYYY-MM-DD  | Ngày bắt đầu hoặc ngày dừng chiến dịch không hợp lệ hoặc trống. Định dạng đúng là YYYY-MM-DD |
| 101  | Cannot take any action on actived, paused or completed campaigns | Không thể thao tác trên những chiến dịch đang hoạt động, tạm dừng hoặc đã hoàn thành |
| 102  | The schedule specified is invalid. Possible values are ONCE, EVERY_DAY, EVERY_WEEK, EVERY_MONTH | Lịch trả thưởng không hợp lệ. Các giá trị hợp lệ gồm ONCE, EVERY_DAY, EVERY_WEEK, EVERY_MONTH |
| 103  | The name specified is invalid or empty | Tên chiến dịch không hợp lệ hoặc trống |
| 104  | Campaign not found | Không tìm thấy chiến dịch |
| 105  | This campaign can't be deleted because its status is one of these: ACTIVE, PAUSE or COMPLETED | Không thể xoá chiến dịch này vì trang thái của nó là ACTIVE, PAUSED hoặc COMPLETED |
| 106  | This campaign can't be deleted because its start date is same or before today | Không thể xoá chiến dịch này vì ngày bắt đầu chiến dịch trước thời gian hiện tại |
| 107  | Invalid status | Trạng thái không hợp lệ |
| 108  | Invalid or empty campaign name | Tên chiến dịch không hợp lệ hoặc trống |
| 109  | Permission denied. Only admin or company owner can update campaigns | Chỉ quản trị viên hoặc quản lý công ty có quyền cập nhật các chiến dịch |
| 110  | Permission denied. Only admin or company owner can remove campaigns | Chỉ quản trị viên hoặc quản lý công ty có quyền xoá các chiến dịch |
| 111  | This campaign can't be updated because its status is one of these: ACTIVE, PAUSE or COMPLETED | Không thể cập nhật chiến dịch này vì trang thái của nó là ACTIVE, PAUSED hoặc COMPLETED |
| 112  | This campaign can't be upadted because its start date is same or before today | Không thể cập nhật chiến dịch này vì ngày bắt đầu chiến dịch xảy ra trước hoặc trùng với ngày hiện tại |
| 113  | The campaign cannot be created without recipients | Chiến dịch không thể tạo mà không có người nhận |
| 114  | Invalid quantity. Quantity must be greater than zero | Số lượng không hợp lệ. Số lượng phải lớn hơn 0 |
| 115  | Please select some gifts | Vui lòng chọn quà tặng |
| 116  | No recipient found | Không tìm thấy người nhận |
| 117  | Duplicate phone number or email of recipients | Người nhận bị trùng lặp số điện thoại hoặc email |
| 200  | Permission denied. Only admin or company owner can request a balance | Chỉ quản trị viên hoặc quản lý công ty có quyền yêu cầu 1 số dư |
| 201  | Total budget cannot be empty, zero or negative  | Tổng ngân sách không thể trống, bằng 0 hoặc âm |
| 202  | Permisson denied. Only admin can update balance requests | Chỉ quản trị viên có quyền sửa số dư |
| 203  | Status can't be updated because the balance request has already been processed | Không thể cập nhật trạng thái số dư vì số dư đã hoạt động |
| 204  | Balance request not found | Không tìm thấy số dư |
| 205  | Invalid status. Possible values are APPROVED, DENIED | Trạng thái không hợp lệ. Các giá trị hợp lệ bao gồm APPROVED, DENIED |
| 206  | Permisson denied. Only admin or company owner can view the balance requests | Chỉ quản trị viên hoặc quản lý công ty có quyền xem các số dư được yêu cầu |
| 207  | You can't delete this balance request | Bạn không thể xoá yêu cầu số dư này |
| 208  | Invalid billAt. Correct format is YYYY-MM-DD | Trường billAt không hợp lệ. Định dạng đúng là YYYY-MM-DD |
| 209  | Bill status can only be changed from PENDING to ISSUED | Trạng thái của hoá đơn chỉ có thể thay đổi từ PENDING sang ISSUED | 
| 300  | Permission denied. Only admin can view rewards list | Chỉ quản trị viên có quyền xem danh sách thưởng |
| 400  | Permission denied. Only admin or company owner can view the topups list | Chỉ quản trị viên hoặc quản lý công ty có quyền xem danh sách trả thưởng |
| 500  | Permission denied. Only admin or company owner can create new user | Chỉ quản trị viên hoặc quản lý công ty có quyền tạo người dùng mới |
| 501  | Invalid user role | Vai trò người dùng không hợp lệ |
| 502  | You can't delete yourself, please contact Ad alpha admin | Bạn không thể tự xoá chính mình, vui lòng liên hệ quản tri viên của Ad alpha |
| 503  | You can't delete user from another company | Bạn không thể xoá người dùng của công ty khác |
| 504  | User not found | Không tìm thấy người dùng |
| 505  | Your password does not match the current password | Mật khẩu bạn nhập không trùng mật khẩu hiện tại |
| 506  | Duplicate email  | Trùng lặp email |
| 507  | Confirm password does not match new password | Mật khẩu xác nhận không trùng mật khẩu mới |
| 508  | Invalid password code | Mã mật khẩu không hợp lệ |
| 509  | The partner admin can only create new users who are admin or staff members of their company | Admin đối tác chỉ có thể tạo mới người dùng là admin hoặc nhân viên thuộc công ty của mình |
| 510  | Partner admin can only edit partner admin or partner staff | Quản trị viên đối tác chỉ có thể sửa người dùng là quản trị viên hoặc nhân viên bên mình |
| 511  | You can't edit user from another company | Bạn không thể sửa thông tin người dùng của công ty khác |
| 512  | Only partner admin can create new users for their company | Chỉ Admin đối tác có quyền tạo thêm người dùng mới cho công ty của mình |
| 513  | The industry category is invalid | Danh mục ngành không hợp lệ |
| 514  | Contract end date is invalid or missing. Correct format is YYYY-MM-DD | Ngày hết hạn hợp đồng không hợp lệ hoặc trống. Định dạng đúng là YYYY-MM-DD |
| 515  | The partner type is invalid | Loại đối tác không hợp lệ |
| 516  | Partner not found | Không tìm thấy đối tác |
| 517  | You cannot delete user from another Partner | Bạn không thể xoá người dùng thuộc đối tác khác |
| 518  | You cannot view other Partner information | Bạn không thể xem thông tin của bên đối tác khác |
| 519  | You cannot edit other Partner information | Bạn không thể chỉnh sửa thông tin của bên đối tác khác |
| 520  | Invalid contract date. Correct format is YYYY-MM-DD | Ngày hợp đồng không hợp lệ. Định dạng đúng là YYYY-MM-DD |
| 521  | Unable to approve partner without partner type, contract date, contract number, industry, payment method or address | Không thể duyệt đối tác mà không có kiểu đối tác, ngày hợp đồng, số hợp đồng, ngành, kiểu thanh toán hoặc địa chỉ |
| 522  | Unable to change partner status | Không thể thay đổi trạng thái partners |
| 523  | Only Partner admin can delete users of their company | Chỉ Admin đối tác có quyền xoá nhân viên thuộc công ty của họ |
| 524  | The partner name is missing | Tên partner bị thiếu |
| 600  | Permission denied. Only admin or Ad alpha financial can view the companies list | Chỉ quản trị viên hoặc quản lý tài chính của Ad alpha có quyền xem danh sách các công ty  |
| 601  | Company not found | Không tìm thấy công ty |
| 602  | Only Ad ALpha Admin can change companies status | Chỉ Ad Alpha Admin có quyền thay đổi trạng thái của công ty |
| 603  | Invalid contract end date. Correct format is YYYY-MM-DD | Ngày hết hạn hợp đồng không hợp lệ. Định dạng đúng là YYYY-MM-DD |
| 604  | Invalid field isVATRequired. isVATRequired can only be boolean | Trường isVATRequired không hợp lệ. isVATRequired chỉ có định dạng boolean |
| 605  | Pending companies can only be changed to Approved or Disapproved | Các công ty đang chờ xử lý chỉ có thể được thay đổi thành đã phê duyệt hoặc không được phê duyệt |
| 606  | Only Ad Alpha Admin and the owner of company can edit company information | Chỉ quản trị viên và chủ công ty có quyền thay đổi thông tin công ty |
| 607  | The company admin can only create new users who are admin or staff members of their company | Admin công ty chỉ có thể tạo mới người dùng là admin hoặc staff thuộc công ty của mình |
| 608  | Only company admin can create new users for their company | Chỉ admin của công ty có quyền tạo mới người dùng cho công ty của họ |
| 609  | The company name is invalid or missing | Tên công ty không hợp lệ hoặc bị thiếu |
| 610  | Invalid field contractNumber. Contract number is required | Số hợp đồng không hợp lệ. Đây là trường bắt buộc |
| 611  | Invalid field address. Address is required | Địa chỉ không hợp lệ. Đây là trương bắt buộc |
| 612  | Invalid field taxCode. Tax code is required | Mã số thuế không hợp lệ. Đây là trường bắt buộc |
| 700  | Permission denied. Only admin or company owner can see this group | Chỉ quản trị viên hoặc quản lý công ty có quyền xem thông tin nhóm |
| 701  | Permission denied. Only admin or company owner can delete groups | Chỉ quản trị viên hoặc quản lý công ty có quyền xoá nhóm |
| 702  | Permission denied. Only admin or company owner can update groups | Chỉ quản trị viên hoặc quản lý công ty có quyền xoá nhóm  |
| 703  | Group employee not found | Không tìm thấy nhóm nhân viên |
| 704  | Group not found | Không tìm thấy nhóm |
| 705  | Group client not found | Không tìm thấy nhóm khách hàng |
| 706  | Group name already exists. Please enter another name | Tên nhóm đã tồn tại. Vui lòng đặt tên khác |
| 707  | Please choose group type | Xin vui lòng chọn loại nhóm |
| 708  | Please enter group name | Xin vui lòng nhập tên nhóm |
| 800  | Permission denied. Only admin or company owner can remove an employee from its group | Chỉ quản trị viên và quản lý công ty có quyền xoá 1 nhân viên khỏi nhóm |
| 801  | Permission denied. Only admin or company owner can create new employees | Chỉ quản trị viên và quản lý công ty có quyền tạo 1 nhân viên mới |
| 802  | Invalid or missing birth date/ employee date. Correct format is YYYY-MM-DD | Ngày sinh hoặc ngày bắt đầu làm việc  không hợp lệ hoặc trống. Định dạng đúng là YYYY-MM-DD |
| 803  | |  |
| 804  | Employee not found | Không tìm thấy nhân viên |
| 805  | Permission denied. Only admin or company owner can remove employees | Chỉ quản trị viên và quản lý công ty có quyền xoá nhân viên |
| 806  | Permission denied. Only admin or company owner can update employees | Chỉ quản trị viên và quản lý công ty có quyền cập nhật nhân viên |
| 807  | There may be employees with duplicate emails or phone numbers | Có thể có nhân viên bị trùng lặp email hoặc số điện thoại |
| 900  | Permission denied. Only admin or company owner can remove a client from its group | Chỉ quản trị viên và quản lý có quyền xoá 1 khách hàng khỏi nhóm |
| 901  | Permission denied. Only admin or company owner can create new clients | Chỉ quản trị viên và quản lý có quyền tạo 1 khách hàng mới |
| 902  | Invalid or missing birth date. Correct format is YYYY-MM-DD | Ngày sinh không hợp lệ hoặc trống. Định dạng đúng là YYYY-MM-DD |
| 903  | Permission denied. Only admin or company owner can delete clients | Chỉ quản trị viện hoặc quản lý công ty có quyền xoá khách hàng  |
| 904  | Client not found| Không tìm thấy khách hàng |
| 905  | Permission denied. Only admin or company owner can update clients | Chỉ quản trị viên và quản lý có quyền cập nhật khách hàng |
| 906  | There may be employees with duplicate emails or phone numbers | Có thể có nhân viên bị trùng lặp email hoặc số điện thoại |
| 1000  | Invalid file type. Possible types are CAMPAIGN_ATTACHMENT, CLIENT_ATTACHMENT, EMPLOYEE_ATTACHMENT|  Loại file không hợp lệ. Các loại file hợp lệ là CAMPAIGN_ATTACHMENT, CLIENT_ATTACHMENT, EMPLOYEE_ATTACHMENT |
| 1001  | Permission denied. You can't download sheets from another companies | Bạn không thể tải sheets của công ty khác |
| 1002  | The file does not exists | Không tồn tại file |
| 1100  | The redeem location is invalid | Vị trí đổi quà không hợp lệ |
| 1101  | Only Adalpha Admin or partner can view this voucher | Chỉ Adalpha admin hoặc đối tác có thể xem voucher này |
| 1102  | Only Partner admin can delete this voucher | Chỉ Partner admin có thể xoá voucher này |
| 1103  | Only Ad Alpha Admin and Partner admin can edit this voucher | Chỉ Adalpha admin hoặc admin đối tác có thể sửa voucher này |
| 1104  | Voucher not found | Không tìm thấy voucher |
| 1105  | Only Ad Alpha Admin or partner can view list voucher | Chỉ Adalpha admin hoặc đối tác có thể xem danh sách voucher |
| 1106  | Only Ad Alpha Admin or partner can create new voucher | Chỉ Adalpha admin hoặc đối tác có thể tạo mới voucher |
| 1107  | Schedule date is invalid or missing. Correct format is YYYY-MM-DD | Ngày chạy voucher không hợp lệ hoặc trống. Định dạng đúng là YYYY-MM-DD |
| 1108  | Expiration date cannot before today or schedule date | Ngày hết hạn không thể trước hôm nay hoặc lịch chạy |
| 1109  | Brand voucher not found | Không tìm thấy brand voucher |
| 1110  | Customer voucher not found | Không tìm thấy customer voucher |
| 1111  | Open link date is invalid or missing. Correct format is YYYY-MM-DD | Ngày mở liên kết không hợp lệ hoặc rỗng. Định dạng đúng là YYYY-MM-DD |
| 1112  | Scan QR date is invalid or missing. Correct format is YYYY-MM-DD | Ngày quét mã QR không hợp lệ hoặc rỗng. Định dạng đúng là YYYY-MM-DD |
| 1113  | Can only edit information of draft, expired or disapproved vouchers | Chỉ có thể thay đổi thông tin của những voucher ở trạng thái bản nháp, hết hạn hoặc không được phê duyệt | 
| 1114  | Current status cannot be changed | Trạng thái hiện tại không thể thay đổi | 
| 1115  | Partner admin can only change status of a voucher from draft to submitted | Quản trị viên đối tác chỉ có thể đổi trạng thái của voucher từ bản nháp sang đã submit | 
| 1116  | Ad Alpha admin can only change status of a voucher to submitted if it expires | Ad Alpha admin chỉ có thể đổi trạng thái của voucher sang đã submit nếu nó đã hết hạn |
| 1117  | Ad Alpha admin can only approve or disapprove submitted vouchers | Ad Alpha admin chỉ có thể duyệt hoặc từ chối những voucher đã submit |
| 1118  | Ad Alpha admin can only activate approved vouchers | Ad Alpha admin chỉ có thể kích hoạt những voucher đã được phê duyệt |
| 1119  | Only Ad Alpha admin can edit priceEzgift | Chỉ Ad Alpha admin có quyền sửa priceEzgift |
| 1120  | Price cannot be empty, zero or negative | Giá không thể để trống, bằng 0 hoặc âm |
| 1121  | Only Draft and Disapproved vouchers can be deleted | Chỉ có thể xoá những voucher ở trạng thái Draft hoặc Disapproved |
| 1122  | Permission denied. Only admin or partner can see statements | Chỉ admin hoặc đối tác có thể xem được các báo cáo |
| 1123  | Not found report file | Không tìm thấy file báo cáo |
| 1124  | Not found statement | Không tìm thấy báo cáo |
| 1125  | Bill issued. Unable to update | Hóa đơn đã phát hành. Không thể cập nhật |
| 1126  | You don't have permission to scan this voucher | Bạn không được phép quét voucher này |
| 1127  | The end date is invalid or missing. Correct format is YYYY-MM-DD | Ngày kết thúc không hợp lệ hoặc chưa điền. Định dạng đúng là YYYY-MM-DD |
| 1128  | Ad Alpha admin can only update a voucher once it has been submitted | Ad Alpha admin chỉ có thể cập nhật voucher sau khi nó đã được gửi |
| 1129  | Partner cannot edit submitted vouchers | Đối tác không thể chỉnh sửa voucher đã được gửi |
| 1130  | Invalid stock status | Trạng thái kho không hợp lệ |
| 1131  | Invalid voucher status. Possible values are SUBMITTED, APPROVED, DISAPPROVED, ACTIVE, EXPIRED | Trạng thái voucher không hợp lệ. Các giá trị hợp lệ bao gồm SUBMITTED, APPROVED, DISAPPROVED, ACTIVE, EXPIRED |
| 1132  | The voucher value is invalid | Giá trị voucher không hợp lệ |
| 1133  | Bill ID is empty or invalid | Mã hoá đơn trống hoặc không hợp lệ |
| 1134  | Bill date is invalid or empty | Ngày lập hoá đơn trống hoặc không hợp lệ |
| 1135  | Voucher is out of stock | Voucher đã hết hàng |
| 1136  | Quantity cannot be lowered | Không thể hạ thấp số lượng | 
| 1137  | EZGIFT price is missing or invalid | Giá EZGIFT bị thiếu hoặc không hợp lệ |
