# API Transfer

- [API Transfer](#api-transfer)
  - [Note](#note)
  - [Host : https://haraoes-onapp.sku.vn/hara_oes/admin/api](#host--httpsharaoes-onappskuvnhara_oesadminapi)
  - [List Transfer status](#list-transfer-status)
  - [Xử lý điều chuyển](#xử-lý-điều-chuyển)
  - [[ONLY TEST] Tạo điều chuyển](#only-test-tạo-điều-chuyển)

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

* Nhận hàng
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
* Xử lý nhận thiếu
  * Path        : /transfers/${transfer_id}/handle-miss
  * Simple path : /transfers/100003/handle-miss
  * Method      : PUT
  * Body        : empty

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
        "created_at": "2019-01-11T04:08:51.786Z",
        "transfer_of_hrv": [
            {
                "message_errors": {
                    "transfer": "",
                    "receive": ""
                },
                "message_erp_errors": {
                    "transfer": null,
                    "receive": null
                },
                "position": 1,
                "retry_times": 0,
                "has_error": 0,
                "transfer_hrv_status": 2,
                "retry_erp_times": 0,
                "has_erp_error": 0,
                "transfer_erp_status": 0,
                "location_erp_code": "",
                "store_erp_code": "",
                "_id": "5c3816d487681f11c8e4fc2e",
                "loc_from": 482708,
                "loc_to": 482669,
                "created_at": "2019-01-11T04:08:52.379Z",
                "updated_at": "2019-01-11T04:08:53.705Z",
                "transfer_data": {
                    "id": 1000110311,
                    "transfer_number": "IT100120",
                    "from_loc_id": 482708,
                    "to_loc_id": 482669,
                    "reason": "transfer",
                    "tran_date": "2019-01-11T04:08:53.059Z",
                    "note": "Chuyển từ phiếu điều chuyển 100001",
                    "total": 100,
                    "created_at": "2019-01-11T04:08:53.071Z",
                    "updated_at": "2019-01-11T04:08:53.071Z",
                    "status": "Active",
                    "actived_at": "2019-01-11T04:08:53.059Z",
                    "received_at": "2017-06-09T17:00:00Z",
                    "created_user": 1000113120,
                    "received_user": null,
                    "tags": null,
                    "line_items": [
                        {
                            "id": 1000133023,
                            "product_id": 10000434709,
                            "product_variant_id": 101345139,
                            "quantity": 100,
                            "sku": "SP021-1",
                            "barcode": "CUA_L",
                            "variant_title": "L / Xám",
                            "product_name": "Cua thịt sống"
                        }
                    ]
                },
                "id": 1000110311
            }
        ],
        "receive_of_hrv": [
            {
                "message_errors": {
                    "transfer": "",
                    "receive": ""
                },
                "message_erp_errors": {
                    "transfer": "",
                    "receive": ""
                },
                "position": 1,
                "retry_times": 0,
                "has_error": 0,
                "transfer_hrv_status": 2,
                "retry_erp_times": 0,
                "has_erp_error": 0,
                "transfer_erp_status": 0,
                "location_erp_code": "",
                "store_erp_code": "",
                "_id": "5c3db39309630b46848d6a49",
                "loc_from": 482669,
                "loc_to": 482668,
                "transfer_data": {
                    "from_loc_id": 482669,
                    "to_loc_id": 482668,
                    "note": "Chuyển từ phiếu điều chuyển 100001",
                    "line_items": [
                        {
                            "product_id": "10000434709",
                            "product_variant_id": "101345139",
                            "quantity": 50
                        }
                    ],
                    "user_id": 1000113120,
                    "reason": "transfer"
                },
                "created_at": "2019-01-15T10:18:59.564Z",
                "updated_at": "2019-01-15T10:19:01.689Z",
                "id": 1000110356
            }
        ],
        "__v": 0,
        "updated_at": "2019-01-15T10:18:59.548Z",
        "status_handle_receive": 2,
        "status_receive": 2,
        "user_received_at": "2019-01-15T10:18:59.548Z",
        "from_store": {
            "hr_code": "ZOBID_DA_NANG",
            "store_type": 2,
            "status": 1,
            "store_loc_wait_handle": 0,
            "shipping_zone_province": [
                "DA"
            ],
            "max_order_online": 1000,
            "area": "MR1",
            "region": "MTU",
            "address_note": "123",
            "address_city_name": "",
            "address_street": "",
            "address_country_name": "VN",
            "address_district_name": "Quận Hải Châu",
            "address_district_code": "DA360",
            "address_province_name": "Đà Nẵng",
            "address_province_code": "DA",
            "address_ward_name": "Phường Hải Châu II",
            "address_ward_code": "20239",
            "user_updated": 1000113120,
            "name": "ZOBID_DA_NANG",
            "name_search": "zobid_da_nang",
            "name_search_exist": "zobid_da_nang",
            "_id": 100002,
            "store_code": "ZOBID_DA_NANG",
            "store_loc_sale": 482708,
            "store_loc_transport": 482709,
            "store_loc_defective": 482710,
            "user_created": 1000113120,
            "shop_id": 1000111987,
            "created_at": "2019-01-04T03:53:09.220Z",
            "updated_at": "2019-01-05T02:43:27.796Z"
        },
        "to_store": {
            "hr_code": "ZOBID_HCM",
            "store_type": 3,
            "status": 1,
            "store_loc_wait_handle": 0,
            "shipping_zone_province": [
                "HC",
                "HI",
                "AG",
                "BV",
                "BG",
                "BK",
                "BL",
                "BN",
                "BT",
                "BD",
                "BI",
                "BP",
                "BU",
                "CM",
                "CN",
                "CB",
                "DA",
                "DC",
                "DO",
                "DB",
                "DN",
                "DT",
                "GL",
                "HG",
                "HM",
                "HT",
                "HD",
                "HP",
                "HU",
                "HO",
                "HY",
                "KH",
                "KG",
                "KT",
                "LI",
                "LD",
                "LS",
                "LO",
                "LA",
                "ND",
                "NA",
                "NB",
                "NT",
                "PQ",
                "PT",
                "PY",
                "QB",
                "QM",
                "QG",
                "QN",
                "QT",
                "ST",
                "SL",
                "TN",
                "TB",
                "TY",
                "TH",
                "TT",
                "TG",
                "TV",
                "TQ",
                "VL",
                "VT",
                "YB"
            ],
            "max_order_online": 10000,
            "area": "",
            "region": "",
            "address_note": "135 Trần Hưng Đạo",
            "address_city_name": "",
            "address_street": "",
            "address_country_name": "VN",
            "address_district_name": "Quận 1",
            "address_district_code": "HC466",
            "address_province_name": "Hồ Chí Minh",
            "address_province_code": "HC",
            "address_ward_name": "Phường Cầu Ông Lãnh",
            "address_ward_code": "26752",
            "user_updated": 0,
            "name": "ZOBID HCM",
            "name_search": "zobid hcm",
            "name_search_exist": "zobid hcm",
            "_id": 100001,
            "store_code": "ZOBID_HCM",
            "store_loc_sale": 482668,
            "store_loc_transport": 482669,
            "store_loc_defective": 482670,
            "user_created": 1000113120,
            "shop_id": 1000111987,
            "created_at": "2019-01-02T03:31:11.393Z",
            "updated_at": "2019-01-02T03:31:20.081Z"
        },
        "user_created_data": {
            "haraoesapp_extend_data": {
                "hr_token": "81b617398965f08e11930305ec03d3ff28643bc5df4d3ebca097ecea13843bc3",
                "user_auto": 0,
                "hr_id": "",
                "erp_id": ""
            },
            "normalized": {
                "username": "hoang.trandinh@haravan.com",
                "email": "hoang.trandinh@haravan.com",
                "displayName": "tran dinh hoang"
            },
            "account": {
                "account_owner": true,
                "bio": null,
                "email": "hoang.trandinh@haravan.com",
                "first_name": "Hoang",
                "id": "1000113120",
                "im": null,
                "last_name": "Tran Dinh",
                "phone": "0968726159",
                "receive_announcements": 1,
                "url": null,
                "user_type": "regular",
                "permissions": [
                    "Full"
                ]
            },
            "firstName": "Hoang",
            "lastName": "Tran Dinh",
            "phone": "0968726159",
            "staff_id": "",
            "email": "hoang.trandinh@haravan.com",
            "password": "@123456aA",
            "active": true,
            "loginFailTimes": 0,
            "loginFailAt": null,
            "is_deleted": false,
            "userType": "user_admin",
            "roles": [],
            "in_stores": [],
            "in_locations": null,
            "in_provinces": null,
            "in_districts": null,
            "shop": "zobid.sku.vn",
            "shop_id": 1000111987,
            "text_search": "Tran Dinh Hoang hoang.trandinh@haravan.com 0968726159 tran dinh hoang hoangtrandinhharavancom 0968726159",
            "_id": "5c25f28958b76d0934934d01",
            "id": "1000113120",
            "created": "2019-01-15T01:42:07.352Z",
            "provider": "local",
            "updated": "2019-01-15T01:42:07.352Z",
            "username": "hoang.trandinh@haravan.com",
            "displayName": "Tran Dinh Hoang"
        }
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
        "transfer_of_hrv": [
            {
                "message_errors": {
                    "transfer": "",
                    "receive": ""
                },
                "message_erp_errors": {
                    "transfer": null,
                    "receive": null
                },
                "position": 1,
                "retry_times": 0,
                "has_error": 0,
                "transfer_hrv_status": 2,
                "retry_erp_times": 0,
                "has_erp_error": 0,
                "transfer_erp_status": 0,
                "location_erp_code": "",
                "store_erp_code": "",
                "_id": "5c385c3eb0337b000b78604f",
                "loc_from": 483756,
                "loc_to": 482559,
                "created_at": "2019-01-11T09:05:02.875Z",
                "updated_at": "2019-01-11T09:05:04.301Z",
                "transfer_data": {
                    "id": 1000110320,
                    "transfer_number": "IT107622",
                    "from_loc_id": 483756,
                    "to_loc_id": 482559,
                    "reason": "transfer",
                    "tran_date": "2019-01-11T09:05:02.389Z",
                    "note": "Chuyển từ phiếu điều chuyển 100141",
                    "total": 100,
                    "created_at": "2019-01-11T09:05:02.402Z",
                    "updated_at": "2019-01-11T09:05:02.402Z",
                    "status": "Active",
                    "actived_at": "2019-01-11T09:05:02.389Z",
                    "received_at": "2017-06-09T17:00:00Z",
                    "created_user": 1000112036,
                    "received_user": null,
                    "tags": null,
                    "line_items": [
                        {
                            "id": 1000133060,
                            "product_id": 10000439717,
                            "product_variant_id": 101365131,
                            "quantity": 100,
                            "sku": null,
                            "barcode": "0477777777",
                            "variant_title": "Default Title",
                            "product_name": "Hoa Mai"
                        }
                    ]
                },
                "id": 1000110320
            }
        ],
        "receive_of_hrv": [],
        "__v": 0
    }
  }
  ```