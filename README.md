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
Make sure to create your empty database `mflix_local` (and `mflix_test` if you want `run npm test`) on your computer first if you are working locally. 

At the root of the project, create a `.env` and a `.env.test` with these values (note you need to have a different name for your test database):
```
DB_USER=root
DB_PASSWORD=root
DB_HOST=localhost
DB_NAME=mflix_local
DB_PORT=3306
APP_NAME=MFLIX
JWT_SECRET=secret
SERVER_PORT=3001
```
## Setup Database
Run in Postman or in your browser to delete and setup all the tables in your database. Make sure to set the correct configuration for the database connection in `.env` and create the empty database `mflix_local`, `mflix_test`:
```
GET /mysql
```

## Postman
Please import postman collection and environment to use it from the `<root>/postman/` folder.
```
## Error code Table

| Error code  | Description (EN) | Description (VI) |
| ------------- | ------------- | ------------- | 
| 101  | Permission denied| Không được cấp quyền |
| 102  | Not authorized | Không được phép |
| 103  | Invalid credentials  | Thông tin đăng nhập không hợp lệ |
| 104  | Agency is not found | Không tìm thấy đại lý |
| 105  | Campaign is not found | Không tìm thấy chiến dịch |
| 106  | User is not found | Không tìm thấy người dùng |
| 107  | Insertion order is not found | Không tìm thấy đơn hàng |
| 108  | No running campaigns are found | Không tìm thấy chiến dịch nào đang chạy |
| 109  | Pricings is not found | Không tìm thấy mức giá |
| 110  | Telco token is not valid | Telco token không hợp lệ |
| 112  | Contract number is not valid | Số hợp đồng không hợp lệ |
| 113  | Payment type is not valid | Hình thức thanh toán không hợp lệ |
| 114  | Duplicate email | Trùng lặp email |
| 115  | Campaign name is empty | Tên chiến dịch không để trống |
| 116  | The gender is invalid | Giới tính không hợp lệ |
| 117  | The age range is invalid | Độ tuổi không hợp lệ |
| 118  | The phone model is invalid | Loại thiết bị không hợp lệ |
| 119  | The phone os is invalid | Hệ điều hành không hợp lệ |
| 120  | The sim type is invalid | Loại sim không hợp lệ |
| 121  | The arpu is invalid | Doanh thu trung bình trên 1 khách hàng không hợp lệ |
| 122  | The registered service is invalid | Dịch vụ đã đăng ký không hợp lệ |
| 123  | The home location is invalid | Địa chỉ nhà không hợp lệ |
| 124  | The work location is invalid | Địa chỉ nơi làm việc không hợp lệ |
| 125  | The topup reward is invalid | Trả thưởng không hợp lệ |
| 126  | The frequency cap is invalid | Số lượt trả thưởng cho mỗi thuê bao không hợp lệ |
| 127  | The min watching time is invalid | Thời gian xem video tối thiểu không hợp lệ |
| 128  | The campaign status is not valid | Trạng thái chiến dịch không hợp lệ |
| 129  | The insertion order has expired | Đơn hàng đã hết hạn |
| 130  | Campaign end date cannot after insertion order expired date | Thời gian dừng chiến dịch không được sau thời gian hết hạn của đơn hàng |
| 131  | The start date / end date is invalid or missing. The correct format is YYYY-MM-DD | Ngày bắt đầu / ngày kết thúc không hợp lệ hoặc thiếu. Định dạng đúng là YYYY-MM-DD |
| 132  | The video is too short or too long | Thời lượng của video quá ngắn hoặc quá dài |
| 133  | The min watching time cannot be longer than the video length | Thời gian xem video tối thiểu không được dài hơn thời lượng video |
| 134  | No pricing matchs your video length | Không tìm thấy giá tiền phù hợp với độ dài video |
| 135  | The targeted nb view is too big for the current insertion order (only ... VND left)  | Số lượt xem mục tiêu quá nhiều so với ngân sách còn lại (… VND) |
| 136  | The campaign status is not a draft anymore | Chiến dịch không còn ở trạng thái bản nháp |
| 137  | Agency has already been reviewed | Đại lý đã được xem xét |
| 138  | The agency status is invalid | Trạng thái của đại lý không hợp lệ |
| 139  | The insertion order status is invalid | Trạng thái của đơn hàng không hợp lệ |
| 140  | Can not set IO expired date before any campaign end date using the IO | Thời gian hết hạn của đơn hàng không được trước thời gian dừng của bất kỳ chiến dịch nào đang sử dụng nó |
| 141  | The file does not exists | Tập tin không tồn tại |
| 142  | The budget is invalid | Ngân sách không hợp lệ |
| 143  | Insertion order in use | Đơn hàng đang được sử dụng |
| 144  | Discount level is invalid | Mức chiết khấu không hợp lệ |
| 145  | Agency name is invalid | Tên đại lý không hợp lệ |
| 146  | Can not edit insertion order if it has been confirmed | Không thể sửa thông tin đơn hàng nếu nó đã được xác nhận |
```


