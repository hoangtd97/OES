# API Request Transfer

- [API Request Transfer](#api-request-transfer)
  - [Note](#note)
  - [Host : https://haraoes-onapp.sku.vn/hara_oes/admin/api](#host--httpsharaoes-onappskuvnhara_oesadminapi)
  - [List request transfer status](#list-request-transfer-status)
  - [API Xử lý phiếu yêu cầu chuyển hàng](#api-xử-lý-phiếu-yêu-cầu-chuyển-hàng)
    - [Request](#request)
      - [Duyệt](#duyệt)
      - [Từ chối duyệt](#từ-chối-duyệt)
      - [Tạo điều chuyển](#tạo-điều-chuyển)
    - [Response](#response)
  - [[ONLY TEST] Tạo yêu cầu điều chuyển](#only-test-tạo-yêu-cầu-điều-chuyển)
    - [Request](#request-1)
    - [Response](#response-1)

## Note
* [15/01/2019] Thêm thông tin cập nhật số lượng item điều chuyển

## Host : https://haraoes-onapp.sku.vn/hara_oes/admin/api

## List request transfer status

| code | description     |
| -    | -               |
| 6    | đợi duyệt       |
| 1    | đã duyệt        |
| 3    | từ chối         |
| 7    | đang vận chuyển |
| 4    | đã nhận         |

## API Xử lý phiếu yêu cầu chuyển hàng

### Request 


#### Duyệt
  * Path        : /request-transfers/${request_transfer_id}/approve
  * Simple path : /request-transfers/100002/approve
  * Method      : PUT
  * Body        : None

#### Từ chối duyệt
  * Path        : /request-transfers/${request_transfer_id}/deny
  * Simple path : /request-transfers/100003/deny
  * Method      : PUT
  * Body        : 
  ```json
  {
  	"reason_reject": "Hết hàng"
  }
  ```

#### Tạo điều chuyển
  * Path        : /request-transfers/${request_transfer_id}/create-transfer
  * Simple path : /request-transfers/100000/create-transfer
  * Method      : PUT
  * Body        : 
  ```json
    {
        "line_items_transfers" : [{
            "variant_id"               : "101407454",
            "variant_barcode"          : "HEO_MOI",
            "variant_accept_quantity"  : 50,             // Số lượng duyệt - điều chuyển
            "note"                     : "..."

        }]
    }
  ```

### Response
* Success
  * status : 200
  * Body   : Updated request transfer
  ```json
  {
    "item": {
      "_id": 100009,
      "method_transfer": 1,
      "create_by_transfer": 0,
      "user_accepted": 0,
      "user_accepted_raw": 0,
      "user_accepted_handle": 1000113120,
      "user_delivering": 0,
      "user_received": 0,
      "user_denied": 0,
      "user_deleted": 0,
      "source_type": 0,
      "source_id": 0,
      "is_deleted": 0,
      "is_handling": 0,
      "from_store_id": 100002,
      "to_store_id": 100001,
      "line_items_transfers": [
        {
          "_id": "5c3821d83e754f2cf4fe1e40",
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
          "variant_inventory_quantity": 445,
          "variant_request_quantity": 10,
          "variant_accept_quantity": 0,
          "note": ""
        }
      ],
      "note": "",
      "status": 1,
      "created_at": "2019-01-11T04:55:52.670Z",
      "updated_at": "2019-01-11T04:56:03.440Z",
      "user_created": 1000113120,
      "shop_id": 1000111987,
      "user_created_at": "2019-01-11T04:55:52.670Z",
      "__v": 0,
      "user_accepted_handle_at": "2019-01-11T04:56:03.440Z"
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

## [ONLY TEST] Tạo yêu cầu điều chuyển 

### Request 
* Path   : /request-transfers/create
* Method : POST 
* Body   : 
```json
{
    "from_store_id": "100014",
    "to_store_id": "100013",
    "note": "",
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
            "variant_request_quantity": 100,
            "variant_accept_quantity": 0,
            "note": "",
            "position": 0,
            "isAutoFix": false
        }
    ],
    "status": 6
}
```

### Response 
* Success :
  * Status : 200
  * Body   : 
  ```json
  {
    "item": {
        "method_transfer": 1,
        "create_by_transfer": 0,
        "user_accepted": 0,
        "user_accepted_raw": 0,
        "user_accepted_handle": 0,
        "user_delivering": 0,
        "user_received": 0,
        "user_denied": 0,
        "user_deleted": 0,
        "source_type": 0,
        "source_id": 0,
        "is_deleted": 0,
        "is_handling": 0,
        "from_store_id": 100014,
        "to_store_id": 100013,
        "line_items_transfers": [
            {
                "_id": "5c3859747cce4c000b5974fd",
                "product_id": "10000439717",
                "variant_id": "101365131",
                "variant_inventory_quantity": 5000,
                "variant_request_quantity": 100,
                "variant_accept_quantity": 0
            }
        ],
        "note": "Nhập mới",
        "status": 6,
        "created_at": "2019-01-11T08:53:08.511Z",
        "updated_at": "2019-01-11T08:53:08.508Z",
        "user_created": 9006199142753988,
        "shop_id": 1000110989,
        "user_created_at": "2019-01-11T08:53:08.511Z",
        "_id": 100129,
        "__v": 0
    }
  }
  ```