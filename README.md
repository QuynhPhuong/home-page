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
| 200  | Permission denied. Only admin or company owner can request a balance | Chỉ quản trị viên hoặc quản lý công ty có quyền yêu cầu 1 số dư |
| 201  | Total budget cannot be empty, zero or negative  | Tổng ngân sách không thể trống, bằng 0 hoặc âm |
| 202  | Permisson denied. Only admin can update balance requests | Chỉ quản trị viên có quyền sửa số dư |
| 203  | Status can't be updated because the balance request has already been processed | Không thể cập nhật trạng thái số dư vì số dư đã hoạt động |
| 204  | Balance request not found | Không tìm thấy số dư |
| 205  | Invalid status. Possible values are APPROVED, DENIED | Trạng thái không hợp lệ. Các giá trị hợp lệ bao gồm APPROVED, DENIED |
| 206  | Permisson denied. Only admin or company owner can view the balance requests | Chỉ quản trị viên hoặc quản lý công ty có quyền xem các số dư được yêu cầu |
| 207  | You can't delete this balance request | Bạn không thể xoá yêu cầu số dư này |
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
| 600  | Permission denied. Only admin or Ad alpha financial can view the companies list | Chỉ quản trị viên hoặc quản lý tài chính của Ad alpha có quyền xem danh sách các công ty  |
| 700  | Permission denied. Only admin or company owner can see this group | Chỉ quản trị viên hoặc quản lý công ty có quyền xem thông tin nhóm |
| 701  | Permission denied. Only admin or company owner can delete groups | Chỉ quản trị viên hoặc quản lý công ty có quyền xoá nhóm |
| 702  | Permission denied. Only admin or company owner can update groups | Chỉ quản trị viên hoặc quản lý công ty có quyền xoá nhóm  |
| 703  | Group employee not found | Không tìm thấy nhóm nhân viên |
| 704  | Group not found | Không tìm thấy nhóm |
| 705  | Group client not found | Không tìm thấy nhóm khách hàng |
| 800  | Permission denied. Only admin or company owner can remove an employee from its group | Chỉ quản trị viên và quản lý công ty có quyền xoá 1 nhân viên khỏi nhóm |
| 801  | Permission denied. Only admin or company owner can create new employees | Chỉ quản trị viên và quản lý công ty có quyền tạo 1 nhân viên mới |
| 802  | Invalid or missing birth date/ employee date. Correct format is YYYY-MM-DD | Ngày sinh hoặc ngày bắt đầu làm việc  không hợp lệ hoặc trống. Định dạng đúng là YYYY-MM-DD |
| 803  | |  |
| 804  | Employee not found | Không tìm thấy nhân viên |
| 805  | Permission denied. Only admin or company owner can remove employees | Chỉ quản trị viên và quản lý công ty có quyền xoá nhân viên |
| 806  | Permission denied. Only admin or company owner can update employees | Chỉ quản trị viên và quản lý công ty có quyền cập nhật nhân viên |
| 900  | Permission denied. Only admin or company owner can remove a client from its group | Chỉ quản trị viên và quản lý có quyền xoá 1 khách hàng khỏi nhóm |
| 901  | Permission denied. Only admin or company owner can create new clients | Chỉ quản trị viên và quản lý có quyền tạo 1 khách hàng mới |
| 902  | Invalid or missing birth date. Correct format is YYYY-MM-DD | Ngày sinh không hợp lệ hoặc trống. Định dạng đúng là YYYY-MM-DD |
| 903  | Permission denied. Only admin or company owner can delete clients | Chỉ quản trị viện hoặc quản lý công ty có quyền xoá khách hàng  |
| 904  | Client not found| Không tìm thấy khách hàng |
| 905  | Permission denied. Only admin or company owner can update clients | Chỉ quản trị viên và quản lý có quyền cập nhật khách hàng |
| 1000  | Invalid file type. Possible types are CAMPAIGN_ATTACHMENT, CLIENT_ATTACHMENT, EMPLOYEE_ATTACHMENT|  Loại file không hợp lệ. Các loại file hợp lệ là CAMPAIGN_ATTACHMENT, CLIENT_ATTACHMENT, EMPLOYEE_ATTACHMENT |
| 1001  | Permission denied. You can't download sheets from another companies | Bạn không thể tải sheets của công ty khác |
