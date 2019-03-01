# API Transfer

- [API Transfer](#api-transfer)
  - [Note](#note)
  - [Host : https://haraoes-onapp.sku.vn/hara_oes/admin/api](#host--httpsharaoes-onappskuvnhara_oesadminapi)
  - [List Transfer status](#list-transfer-status)
  - [Xử lý điều chuyển](#xử-lý-điều-chuyển)
    - [Request](#request)
      - [Nhận hàng](#nhận-hàng)
      - [Xử lý nhận thiếu](#xử-lý-nhận-thiếu)
    - [Response](#response)
  - [[ONLY TEST] Tạo điều chuyển](#only-test-tạo-điều-chuyển)
    - [Request](#request-1)
    - [Response](#response-1)

## Note
* [15/01/2019] Thêm thông tin cập nhật số lượng item nhận

## Host : https://haraoes-onapp.sku.vn/hara_oes/admin/api

## List Transfer status

| code | description |
| -    | -           |
| 2    | Đang chuyển |
| 3    | Đã nhận     |
| 6    | Lỗi         |

## Xử lý điều chuyển

### Request

#### Nhận hàng
  * Path        : /transfers/${transfer_id}/receive
  * Simple path : /transfers/100003/receive
  * Method      : PUT
  * Body        : 
 ```json
  {
      "line_items_transfers" : [{
          "variant_id"                 : "101345139",
          "variant_barcode"            : "CUA_L",
          "variant_receive_quantity"   : 50,           // số lượng sản phẩm nhận
          "note"                       : "..."
      }]
  }
  ```
  * Note        : Nếu nhận dư, OES tạo phiếu điều chuyển lượng sản phẩm chênh lệch từ cửa hàng đi đến cửa hàng đến

#### Xử lý nhận thiếu
  * Path        : /transfers/${transfer_id}/handle-miss
  * Simple path : /transfers/100003/handle-miss
  * Method      : PUT
  * Body        : empty
  * Note        : OES tạo phiếu điều chuyển lượng sản phẩm thất thoát về lại cửa hàng đi

### Response

* Success 
  * Status : 200
  * Body   : Updated Transfer
  ```json
  {
    "item": {
        "_id": 100001,
        "method_transfer": 1,
        "has_error": 0,
        "create_by_request": 100000,
        "user_accepted": 1000113120,
        "user_received": 1000113120,
        "user_denied": 0,
        "user_deleted": 0,
        "is_deleted": 0,
        "is_handling": 0,
        "from_store_id": 100002,
        "to_store_id": 100001,
        "line_items_transfers": [
            {
                "addition_item": 0,
                "_id": "5c3816d387681f11c8e4fc2c",
                "product_id": "10000434709",
                "product_title": "Cua thịt sống",
                "product_image": "http://d-static.sku.vn/1000111987/product/upload_e137d8beb07e4b699e22f1da4a43b81b.jpg",
                "variant_sku": "SP021-1",
                "variant_barcode": "CUA_L",
                "variant_title": "L / Xám",
                "variant_id": "101345139",
                "variant_image": "http://d-static.sku.vn/1000111987/product/upload_e137d8beb07e4b699e22f1da4a43b81b.jpg",
                "variant_price": 132700,
                "variant_inventory_policy": "deny",
                "variant_inventory_management": "haravan",
                "variant_inventory_quantity": 414,
                "variant_request_quantity": 100,
                "variant_accept_quantity": 100,
                "note": "",
                "variant_receive_quantity": 50,
                "variant_deviation_quantity": -50
            }
        ],
        "user_created": 1000113120,
        "status": 3,
        "shop_id": 1000111987,
        "user_created_at": "2019-01-11T04:08:51.786Z",
        "user_accepted_at": "2019-01-11T04:08:51.786Z",
        "created_at": "2019-01-11T04:08:51.786Z"
    }
  }
  ```

* Fail 
  * status : 4xx
  * Body : 
  ```json
  {
    "error"   : true,
    "message" : "Có lỗi xảy ra, vui lòng thử lại sau ít phút"
  }
  ```

## [ONLY TEST] Tạo điều chuyển 

### Request 
* Path   : /transfers/create
* Method : POST 
* Body   : 
```json
{
  "from_store_id": "100014",
  "to_store_id": "100013",
  "note": "Hàng lỗi",
  "line_items_transfers": [
      {
          "product_id": 10000439717,
          "product_title": "Hoa Mai",
          "product_image": "http://d-static.sku.vn/1000110989/product/tong-hop-cac-loai-hoa-mang-den-may-man-tot-lanh-trong-ngay-tet-1.jpg",
          "variant_sku": null,
          "variant_barcode": "0477777777",
          "variant_title": "Default Title",
          "variant_id": 101365131,
          "variant_image": "",
          "variant_price": 200000,
          "variant_inventory_policy": "deny",
          "variant_inventory_management": "haravan",
          "variant_inventory_quantity": 5000,
          "variant_request_quantity": 0,
          "variant_accept_quantity": 100,
          "variant_receive_quantity": 0,
          "variant_deviation_quantity": 0,
          "note": "",
          "position": 0,
          "isAutoFixed": false
      }
  ]
}
```

### Response 
* Success :
  * Status : 200
  * Body   : 
  ```json
  {
    "item": {
        "_id": 100141,
        "method_transfer": 1,
        "has_error": 0,
        "create_by_request": 0,
        "user_accepted": 1000112036,
        "user_received": 0,
        "user_denied": 0,
        "user_deleted": 0,
        "is_deleted": 0,
        "is_handling": 0,
        "from_store_id": 100014,
        "to_store_id": 100013,
        "line_items_transfers": [
            {
                "addition_item": 0,
                "_id": "5c385c3eb0337b000b78604d",
                "product_id": "10000439717",
                "product_title": "Hoa Mai",
                "product_image": "http://d-static.sku.vn/1000110989/product/tong-hop-cac-loai-hoa-mang-den-may-man-tot-lanh-trong-ngay-tet-1.jpg",
                "variant_sku": null,
                "variant_barcode": "0477777777",
                "variant_title": "Default Title",
                "variant_id": "101365131",
                "variant_image": "",
                "variant_price": 200000,
                "variant_inventory_policy": "deny",
                "variant_inventory_management": "haravan",
                "variant_inventory_quantity": 5000,
                "variant_request_quantity": 0,
                "variant_accept_quantity": 100,
                "variant_receive_quantity": 0,
                "variant_deviation_quantity": 0,
                "note": ""
            }
        ],
        "note": "Hàng lỗi",
        "created_at": "2019-01-11T09:05:02.159Z",
        "updated_at": "2019-01-11T09:05:04.304Z",
        "user_created": 1000112036,
        "status": 2,
        "shop_id": 1000110989,
        "user_created_at": "2019-01-11T09:05:02.159Z",
        "user_accepted_at": "2019-01-11T09:05:02.159Z",
        "__v": 0
    }
  }
  ```