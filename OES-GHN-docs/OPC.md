# API OPC

- [API OPC](#api-opc)
  - [Note](#note)
  - [Host : https://haraoes-onapp.sku.vn/hara_oes/admin/api](#host--httpsharaoes-onappskuvnhara_oesadminapi)
  - [List order status](#list-order-status)
  - [Lấy danh sách đơn hàng](#lấy-danh-sách-đơn-hàng)
  - [Lấy chi tiết đơn hàng](#lấy-chi-tiết-đơn-hàng)
  - [Xử lý đơn hàng](#xử-lý-đơn-hàng)

## Note
* [16/01/2019] Thêm thông hủy - nhập trả đơn hàng : nhập trả một phần

## Host : https://haraoes-onapp.sku.vn/hara_oes/admin/api

## List order status

| code | description            |
| -    | -                      |
| 1    | Mới                    |
| 4    | Đã gán nhân viên       |
| 7    | Gọi lại                |
| 10   | Khách hàng xác nhận    |
| 13   | Gán chi nhánh          |
| 16   | hết hàng               |
| 19   | Hủy                    |
| 22   | Chờ giao               |
| 25   | Đã giao vận chuyển     |
| 28   | Yêu cầu hủy            |
| 31   | Hủy nhập trả           |
| 34   | Hoàn tất               |
| 37   | Đã hoàn trả - Một phần |
| 40   | Đã hoàn trả            |
| 43   | Đã đổi                 |
| 47   | Đã đổi - một phần      |

## Lấy danh sách đơn hàng

### Request

* Path   : /orders/search
* Method : POST
* Body   : 
  * Filter :   

  | field          | type     | simple                     | description                                                                    |
  | -              | -        | -                          | -                                                                              |
  | gte_created_at | Date     | "2018-11-30T17:01:00.686Z" | Thời gian tạo đơn hàng từ ngày ...                                             |
  | lte_created_at | Date     | "2019-01-08T16:59:00.686Z" | Thời gian tạo đơn hàng đến ngày ...                                            |
  | order_status   | [Number] | [13, 22, 25]               | Trạng thái đơn hàng, xem danh sách trạng thái đơn hàng                         |
  | store_id       | Number   | 100002                     | Cửa hàng tạo đơn hàng                                                          |
  | list_store_id  | [Number] | [100002, 100001]           | Danh sách cửa hàng tạo đơn hàng                                                |
  

  * Simple :
  ```json
  {
    "filter": {
      "gte_created_at": "2018-11-30T17:01:00.686Z",
      "lte_created_at": "2019-01-08T16:59:00.686Z",
      "store_id" : 100002,
      "list_store_id": [
        100002,
        100001
      ],
      "order_status": [
        13,
        22,
        25
      ]
    },
    "limit": 20,
    "page": 1
  }
  ```

### Response
* Success 
  * Status : 200
  * Body   :
  ```json
  {
    "total": 1,
    "items": [
      {
        "haraoesapp_extend_data": {
          "fulfillment": {
            "manager": 0,
            "carrier_order_id": 0,
            "location_id": 482668,
            "tracking_link": "",
            "tracking_code": "",
            "tracking_company": "Giao Hàng Nhanh 2018",
            "shipping_package": 11,
            "carrier_service_package": 53319,
            "carrier_service_code": "",
            "carrier_service_package_name": "Nhanh",
            "note": "aaaaaaaaaaaaaa",
            "notify_customer": false,
            "cod_amount": 0,
            "total_weight": 0,
            "transport_type": 0,
            "sender_phone": "",
            "is_new_service_package": true,
            "is_view_before": 1,
            "sync_status": 1,
            "last_time_sync": "2019-01-03T02:46:37.823Z",
            "retry_times": 0,
            "message": ""
          },
          "sync_log": {
            "erp": {
              "sync_status": 3,
              "last_time_sync": "2019-01-03T02:46:38.298Z",
              "retry_time": 0,
              "messages": "Invalid data : [\"barcode is required\"]",
              "line_item_id": 0
            },
            "order_by_line_item": [
              {
                "sync_status": 3,
                "last_time_sync": "2019-01-03T02:46:37.967Z",
                "retry_time": 0,
                "messages": "E11000 duplicate key error collection: hara_oes.hara_oes_order_by_line_items index: _id_ dup key: { : 1000600117 }",
                "line_item_id": 1000600117,
                "_id": "5c2d778d1ac36b1c3c3976b7"
              },
              {
                "sync_status": 3,
                "last_time_sync": "2019-01-03T02:46:37.969Z",
                "retry_time": 0,
                "messages": "E11000 duplicate key error collection: hara_oes.hara_oes_order_by_line_items index: _id_ dup key: { : 1000600118 }",
                "line_item_id": 1000600118,
                "_id": "5c2d778d1ac36b1c3c3976b6"
              }
            ],
            "order_by_line_item_refund": []
          },
          "shipping_method": 1,
          "reorder_from": "",
          "order_merge_from": [],
          "auto_action": 0,
          "transaction_payment_methods": [
            3
          ],
          "is_refund_all": false,
          "full_text_search": "1001140605 Nguyễn Ngọc Như  Lan Nguyễn Ngọc nguyễn ngọc như  lan nguyễn ngọc nhulan@gmail.com nhulan@gmail.com 0126534826",
          "user_sale": 0,
          "status": 22,
          "call_times": 0,
          "shop_id": 1000111987,
          "store_id": 100001,
          "location_id": 0,
          "location_code": 0,
          "store_code": 0,
          "store_hr_code": "",
          "location_hr_code": "",
          "assign_employee_at": "2019-01-03T02:45:58.381Z",
          "user_review": 1000113120,
          "callback_at": null,
          "user_callback": 0,
          "customer_confirm_at": "2019-01-03T02:46:08.259Z",
          "user_confirm_customer": 1000113120,
          "out_of_stock_at": null,
          "user_out_of_stock": 0,
          "cancel_at": null,
          "user_cancel": 0,
          "assign_store_at": "2019-01-03T02:46:25.968Z",
          "user_assign_store": 1000113120,
          "wait_ship_at": "2019-01-03T02:46:37.823Z",
          "user_wait_ship": 1000113120,
          "shipped_at": null,
          "user_shipped": 0,
          "request_cancel_at": null,
          "request_cancel_note": "",
          "user_request_cancel": 0,
          "cancel_return_at": null,
          "user_cancel_return": 0,
          "completed_at": null,
          "user_completed": 0,
          "exchange_at": null,
          "user_exchange": 0,
          "exchange_partial_at": null,
          "user_exchange_partial": 0,
          "return_at": null,
          "user_return": 0,
          "return_partial_at": null,
          "user_return_partial": 0,
          "order_exchange_origin": 0,
          "call_back_customer": 0,
          "customer_pay": 0,
          "customer_card": 0,
          "customer_cash": 0,
          "excess_cash_refund": 0,
          "handle_discount": "",
          "cash_voucher": [],
          "order_number": "0",
          "order_refund": [],
          "order_exchange": []
        },
        "billing_address": {
          "address1": "135 Trần Hưng Đạo",
          "address2": null,
          "city": null,
          "company": null,
          "country": "Vietnam",
          "first_name": "Như  Lan",
          "id": 1000142445,
          "last_name": "Nguyễn Ngọc",
          "phone": "0126534826",
          "province": "Hồ Chí Minh",
          "zip": null,
          "name": "Nguyễn Ngọc Như  Lan",
          "province_code": "HC",
          "country_code": "VN",
          "default": true,
          "district": "Quận 1",
          "district_code": "HC466",
          "ward": "Phường Cầu Ông Lãnh",
          "ward_code": "26752"
        },
        "client_details": {
          "accept_language": null,
          "browser_ip": null,
          "session_hash": null,
          "user_agent": null,
          "browser_height": null,
          "browser_width": null
        },
        "customer": {
          "accepts_marketing": false,
          "addresses": [
            {
              "address1": "135 Trần Hưng Đạo",
              "address2": null,
              "city": null,
              "company": null,
              "country": "Vietnam",
              "first_name": "Như  Lan",
              "id": 1000372591,
              "last_name": "Nguyễn Ngọc",
              "phone": "0126534826",
              "province": "Hồ Chí Minh",
              "zip": "70000",
              "name": "Nguyễn Ngọc Như  Lan",
              "province_code": "HC",
              "country_code": "vn",
              "default": true,
              "district": "Quận 1",
              "district_code": "HC466",
              "ward": "Phường Cầu Ông Lãnh",
              "ward_code": "26752"
            },
            {
              "address1": null,
              "address2": null,
              "city": null,
              "company": null,
              "country": "Vietnam",
              "first_name": "Như  Lan",
              "id": 1000372672,
              "last_name": "Nguyễn Ngọc",
              "phone": "0126534826",
              "province": null,
              "zip": "70000",
              "name": "Nguyễn Ngọc Như  Lan",
              "province_code": null,
              "country_code": "vn",
              "default": false,
              "district": null,
              "district_code": null,
              "ward": null,
              "ward_code": null
            },
            {
              "address1": null,
              "address2": null,
              "city": null,
              "company": null,
              "country": "Vietnam",
              "first_name": "Như  Lan",
              "id": 1000372660,
              "last_name": "Nguyễn Ngọc",
              "phone": "0126534826",
              "province": null,
              "zip": "70000",
              "name": "Nguyễn Ngọc Như  Lan",
              "province_code": null,
              "country_code": "vn",
              "default": false,
              "district": null,
              "district_code": null,
              "ward": null,
              "ward_code": null
            },
            {
              "address1": null,
              "address2": null,
              "city": null,
              "company": null,
              "country": "Vietnam",
              "first_name": "Như  Lan",
              "id": 1000372644,
              "last_name": "Nguyễn Ngọc",
              "phone": "0126534826",
              "province": null,
              "zip": "70000",
              "name": "Nguyễn Ngọc Như  Lan",
              "province_code": null,
              "country_code": "vn",
              "default": false,
              "district": null,
              "district_code": null,
              "ward": null,
              "ward_code": null
            },
            {
              "address1": null,
              "address2": null,
              "city": null,
              "company": null,
              "country": "Vietnam",
              "first_name": "Như  Lan",
              "id": 1000372631,
              "last_name": "Nguyễn Ngọc",
              "phone": "0126534826",
              "province": null,
              "zip": "70000",
              "name": "Nguyễn Ngọc Như  Lan",
              "province_code": null,
              "country_code": "vn",
              "default": false,
              "district": null,
              "district_code": null,
              "ward": null,
              "ward_code": null
            },
            {
              "address1": null,
              "address2": null,
              "city": null,
              "company": null,
              "country": "Vietnam",
              "first_name": "Như  Lan",
              "id": 1000372613,
              "last_name": "Nguyễn Ngọc",
              "phone": "0126534826",
              "province": null,
              "zip": "70000",
              "name": "Nguyễn Ngọc Như  Lan",
              "province_code": null,
              "country_code": "vn",
              "default": false,
              "district": null,
              "district_code": null,
              "ward": null,
              "ward_code": null
            }
          ],
          "created_at": "2019-01-01T16:06:27.811Z",
          "email": "nhulan@gmail.com",
          "first_name": "Như  Lan",
          "id": 1000142445,
          "multipass_identifier": null,
          "last_name": "Nguyễn Ngọc",
          "last_order_id": 1001140614,
          "last_order_name": "#101273",
          "note": null,
          "orders_count": 18,
          "state": "Disabled",
          "tags": null,
          "total_spent": 1702500,
          "total_paid": 0,
          "updated_at": "2019-01-03T01:21:58.000Z",
          "verified_email": false,
          "send_email_invite": false,
          "send_email_welcome": false,
          "password": null,
          "password_confirmation": null,
          "group_name": "",
          "metafields": null,
          "birthday": "1998-10-20T00:00:00.000Z",
          "gender": null,
          "last_order_date": "2019-01-03T01:21:55.000Z",
          "default_address": {
            "address1": "135 Trần Hưng Đạo",
            "address2": null,
            "city": null,
            "company": null,
            "country": "Vietnam",
            "first_name": "Như  Lan",
            "id": 1000372591,
            "last_name": "Nguyễn Ngọc",
            "phone": "0126534826",
            "province": "Hồ Chí Minh",
            "zip": "70000",
            "name": "Nguyễn Ngọc Như  Lan",
            "province_code": "HC",
            "country_code": "vn",
            "default": true,
            "district": "Quận 1",
            "district_code": "HC466",
            "ward": "Phường Cầu Ông Lãnh",
            "ward_code": "26752"
          }
        },
        "shipping_address": {
          "address1": "135 Trần Hưng Đạo",
          "address2": null,
          "city": null,
          "company": null,
          "country": "Vietnam",
          "first_name": "Như  Lan",
          "last_name": "Nguyễn Ngọc",
          "latitude": 0,
          "longitude": 0,
          "phone": "0126534826",
          "province": "Hồ Chí Minh",
          "zip": null,
          "name": "Nguyễn Ngọc Như  Lan",
          "province_code": "HC",
          "country_code": "VN",
          "district_code": "HC466",
          "district": "Quận 1",
          "ward_code": "26752",
          "ward": "Phường Cầu Ông Lãnh"
        },
        "browser_ip": null,
        "buyer_accepts_marketing": false,
        "cancel_reason": null,
        "cancelled_at": null,
        "cart_token": "612f032ffbae4c349e1a8befad1c935f",
        "checkout_token": "612f032ffbae4c349e1a8befad1c935f",
        "closed_at": null,
        "currency": "VND",
        "discount_codes": [],
        "email": "nhulan@gmail.com",
        "financial_status": "pending",
        "fulfillment_status": "fulfilled",
        "tags": "",
        "gateway": "Thanh toán khi giao hàng (COD)",
        "gateway_code": "cod",
        "send_webhooks": "false",
        "landing_site": null,
        "landing_site_ref": null,
        "source": "web",
        "name": "#101272",
        "note": null,
        "location_id": 482663,
        "number": 1001140605,
        "order_number": "#101272",
        "processing_method": null,
        "referring_site": "web",
        "refunds": [],
        "shipping_lines": [
          {
            "code": null,
            "price": 0,
            "source": null,
            "title": null
          }
        ],
        "source_name": "web",
        "subtotal_price": 113800,
        "tax_lines": null,
        "taxes_included": false,
        "token": "612f032ffbae4c349e1a8befad1c935f",
        "total_discounts": 0,
        "total_line_items_price": 113800,
        "total_price": 113800,
        "total_tax": 0,
        "total_weight": 0,
        "transactions": [
          {
            "amount": 113800,
            "authorization": null,
            "created_at": "2019-01-03T01:21:17.448Z",
            "device_id": null,
            "gateway": "Thanh toán khi giao hàng (COD)",
            "id": 1000440025,
            "kind": "Pending",
            "order_id": 1001140605,
            "receipt": null,
            "status": null,
            "test": false,
            "user_id": 1000113120,
            "location_id": 482663,
            "payment_details": null,
            "parent_id": null,
            "currency": null,
            "haravan_transaction_id": null,
            "external_transaction_id": null,
            "send_email": false,
            "is_cod_gateway": false
          }
        ],
        "note_attributes": [],
        "send_receipt": false,
        "send_fulfillment_receipt": false,
        "inventory_behaviour": null,
        "closed_status": "unclosed",
        "cancelled_status": "uncancelled",
        "confirmed_status": "confirmed",
        "user_id": 1000113120,
        "device_id": null,
        "has_promotion": false,
        "is_cod_gateway": false,
        "ref_order_id": 0,
        "ref_order_number": null,
        "utm_source": null,
        "utm_medium": null,
        "utm_campaign": null,
        "utm_term": null,
        "utm_content": null,
        "send_paid": true,
        "_id": "5c2d6459e1de203a2812c563",
        "created_at": "2019-01-03T01:21:17.253Z",
        "fulfillments": [
          {
            "created_at": "2019-01-03T02:46:36.15Z",
            "id": 1010126117,
            "order_id": 1001140605,
            "receipt": null,
            "status": "success",
            "tracking_company": "Giao Hàng Nhanh 2018",
            "tracking_company_code": "ghn2018",
            "tracking_numbers": [
              "4AXQ46LX"
            ],
            "tracking_number": "4AXQ46LX",
            "tracking_url": "https://track.ghn.vn/order/tracking?code=",
            "tracking_urls": [
              "https://track.ghn.vn/order/tracking?code="
            ],
            "updated_at": "2019-01-03T02:46:36.15Z",
            "line_items": [
              {
                "fulfillable_quantity": 1,
                "fulfillment_service": "Thủ công",
                "fulfillment_status": "Đã hoàn thành",
                "grams": 0,
                "id": 1000600117,
                "price": 73500,
                "product_id": 10000434694,
                "quantity": 1,
                "requires_shipping": true,
                "sku": "SP023-2",
                "title": "Bắp bò Úc giá tay",
                "variant_id": 101345087,
                "variant_title": "M / Đỏ",
                "vendor": "Vissan",
                "name": "Bắp bò Úc giá tay",
                "variant_inventory_management": "Haravan",
                "properties": null,
                "product_exists": true
              },
              {
                "fulfillable_quantity": 1,
                "fulfillment_service": "Thủ công",
                "fulfillment_status": "Đã hoàn thành",
                "grams": 0,
                "id": 1000600118,
                "price": 40300,
                "product_id": 10000434705,
                "quantity": 1,
                "requires_shipping": true,
                "sku": "SP020-1",
                "title": "Cánh gà công nghiệp",
                "variant_id": 101345126,
                "variant_title": "L / Trắng",
                "vendor": "Unitek",
                "name": "Cánh gà công nghiệp",
                "variant_inventory_management": "Haravan",
                "properties": null,
                "product_exists": true
              }
            ],
            "notify_customer": false,
            "province": null,
            "province_code": null,
            "district": null,
            "district_code": "HC466",
            "ward": null,
            "ward_code": null,
            "cod_amount": 0,
            "carrier_status_name": "Chờ lấy hàng",
            "carrier_cod_status_name": "Không",
            "carrier_status_code": "readytopick",
            "carrier_cod_status_code": "none",
            "location_id": 482668,
            "shipping_package": 0,
            "note": null,
            "carrier_service_package": 0,
            "carrier_service_package_name": "Nhanh",
            "is_new_service_package": false,
            "coupon_code": null,
            "ready_to_pick_date": "2019-01-03T02:46:31Z",
            "picking_date": null,
            "delivering_date": null,
            "delivered_date": null,
            "return_date": null,
            "not_meet_customer_date": null,
            "waiting_for_return_date": null,
            "cod_paid_date": null,
            "cod_receipt_date": null,
            "cod_pending_date": null,
            "cod_not_receipt_date": null,
            "is_view_before": null,
            "country": null,
            "country_code": null,
            "zip_code": null,
            "city": null,
            "real_shipping_fee": 31900,
            "shipping_notes": "aaaaaaaaaaaaaa CHOXEMHANGKHONGTHU",
            "total_weight": 0,
            "package_length": 0,
            "package_width": 0,
            "package_height": 0,
            "boxme_servicecode": null,
            "transport_type": 0,
            "address": null,
            "sender_phone": null,
            "sender_name": null
          }
        ],
        "id": 1001140605,
        "line_items": [
          {
            "fulfillable_quantity": 0,
            "fulfillment_service": null,
            "fulfillment_status": "fulfilled",
            "grams": 0,
            "id": 1000600117,
            "price": 73500,
            "price_original": 73500,
            "price_promotion": 0,
            "product_id": 10000434694,
            "variant_id": 101345087,
            "quantity": 1,
            "requires_shipping": true,
            "sku": "SP023-2",
            "title": "Bắp bò Úc giá tay",
            "variant_title": "M / Đỏ",
            "vendor": "Vissan",
            "type": "Thịt",
            "name": "Bắp bò Úc giá tay - M / Đỏ",
            "gift_card": false,
            "taxable": true,
            "tax_lines": null,
            "product_exists": true,
            "barcode": null,
            "properties": [],
            "total_discount": 0,
            "applied_discounts": null,
            "not_allow_promotion": false,
            "_id": "5c2d77951ac36b1c3c3976bb",
            "image": {
              "src": "http://d-static.sku.vn/1000111987/product/upload_54318d27bb6446779ec734573f48d008.jpg",
              "attactment": null,
              "filename": null
            }
          },
          {
            "fulfillable_quantity": 0,
            "fulfillment_service": null,
            "fulfillment_status": "fulfilled",
            "grams": 0,
            "id": 1000600118,
            "price": 40300,
            "price_original": 40300,
            "price_promotion": 0,
            "product_id": 10000434705,
            "variant_id": 101345126,
            "quantity": 1,
            "requires_shipping": true,
            "sku": "SP020-1",
            "title": "Cánh gà công nghiệp",
            "variant_title": "L / Trắng",
            "vendor": "Unitek",
            "type": "Thịt",
            "name": "Cánh gà công nghiệp - L / Trắng",
            "gift_card": false,
            "taxable": true,
            "tax_lines": null,
            "product_exists": true,
            "barcode": null,
            "properties": [],
            "total_discount": 0,
            "applied_discounts": null,
            "not_allow_promotion": false,
            "_id": "5c2d77951ac36b1c3c3976ba",
            "image": {
              "src": "http://d-static.sku.vn/1000111987/product/upload_4b5e18c14631401f9f6fc8eac07e5c34.jpg",
              "attactment": null,
              "filename": null
            }
          }
        ],
        "updated_at": "2019-01-03T02:46:38.538Z",
        "confirmed_at": "2019-01-03T01:21:18.369Z"
      }
    ]
  }
  ```

* Fail
  * Status : 4xx
  * Body   :
  ```json
  {
    "error": true,
    "message": [
        "Mã truy cập không hợp lệ"
    ]
  }
  ```

## Lấy chi tiết đơn hàng

### Request
```
* Path        : /orders/${order_id}
* Simple path : /orders/1001145807
* Method      : GET
```

### Response
* Success
  * Status : 200
  * Body   : 
  ```json
  {
    "haraoesapp_extend_data": {
        "fulfillment": {
            "manager": 0,
            "carrier_order_id": 0,
            "location_id": 0,
            "tracking_link": "",
            "tracking_code": "",
            "tracking_company": "",
            "shipping_package": 0,
            "carrier_service_package": 0,
            "carrier_service_code": "",
            "carrier_service_package_name": "",
            "note": "",
            "notify_customer": false,
            "cod_amount": 0,
            "total_weight": 0,
            "transport_type": 0,
            "sender_phone": "",
            "is_new_service_package": true,
            "is_view_before": 1,
            "sync_status": 0,
            "last_time_sync": null,
            "retry_times": 0,
            "message": ""
        },
        "sync_log": {
            "erp": null,
            "order_by_line_item": [],
            "order_by_line_item_refund": []
        },
        "shipping_method": 0,
        "reorder_from": "",
        "order_merge_from": [],
        "auto_action": 0,
        "transaction_payment_methods": [],
        "is_refund_all": false,
        "full_text_search": "1001145807 Nguyễn Ngọc Như  Lan Nguyễn Ngọc nguyễn ngọc như  lan nguyễn ngọc nhulan@gmail.com nhulan@gmail.com 01265348777",
        "user_sale": 1000113120,
        "status": 1,
        "call_times": 0,
        "shop_id": 1000111987,
        "store_id": 0,
        "location_id": 0,
        "location_code": 0,
        "store_code": 0,
        "store_hr_code": "",
        "location_hr_code": "",
        "assign_employee_at": null,
        "user_review": 0,
        "callback_at": null,
        "user_callback": 0,
        "customer_confirm_at": null,
        "user_confirm_customer": 0,
        "out_of_stock_at": null,
        "user_out_of_stock": 0,
        "cancel_at": null,
        "user_cancel": 0,
        "assign_store_at": null,
        "user_assign_store": 0,
        "wait_ship_at": null,
        "user_wait_ship": 0,
        "shipped_at": null,
        "user_shipped": 0,
        "request_cancel_at": null,
        "request_cancel_note": "",
        "user_request_cancel": 0,
        "cancel_return_at": null,
        "user_cancel_return": 0,
        "completed_at": null,
        "user_completed": 0,
        "exchange_at": null,
        "user_exchange": 0,
        "exchange_partial_at": null,
        "user_exchange_partial": 0,
        "return_at": null,
        "user_return": 0,
        "return_partial_at": null,
        "user_return_partial": 0,
        "order_exchange_origin": 0,
        "call_back_customer": 0,
        "customer_pay": 0,
        "customer_card": 0,
        "customer_cash": 0,
        "excess_cash_refund": 0,
        "handle_discount": "",
        "cash_voucher": [],
        "order_refund": [],
        "order_exchange": []
    },
    "billing_address": {
        "address1": null,
        "address2": null,
        "city": null,
        "company": null,
        "country": "Vietnam",
        "first_name": "Như  Lan",
        "id": 1000142445,
        "last_name": "Nguyễn Ngọc",
        "phone": "01265348777",
        "province": null,
        "zip": "70000",
        "name": "Nguyễn Ngọc Như  Lan",
        "province_code": null,
        "country_code": "VN",
        "default": true,
        "district": null,
        "district_code": null,
        "ward": null,
        "ward_code": null
    },
    "client_details": {
        "accept_language": null,
        "browser_ip": null,
        "session_hash": null,
        "user_agent": null,
        "browser_height": null,
        "browser_width": null
    },
    "customer": {
        "accepts_marketing": false,
        "addresses": [
            {
                "address1": "135 Trần Hưng Đạo",
                "address2": null,
                "city": null,
                "company": null,
                "country": "Vietnam",
                "first_name": "Như  Lan",
                "id": 1000372591,
                "last_name": "Nguyễn Ngọc",
                "phone": "01265348777",
                "province": "Hồ Chí Minh",
                "zip": "70000",
                "name": "Nguyễn Ngọc Như  Lan",
                "province_code": "HC",
                "country_code": "vn",
                "default": true,
                "district": "Quận 1",
                "district_code": "HC466",
                "ward": "Phường Cầu Ông Lãnh",
                "ward_code": "26752"
            },
            {
                "address1": null,
                "address2": null,
                "city": null,
                "company": null,
                "country": "Vietnam",
                "first_name": "Như  Lan",
                "id": 1000374874,
                "last_name": "Nguyễn Ngọc",
                "phone": "01265348777",
                "province": null,
                "zip": null,
                "name": "Nguyễn Ngọc Như  Lan",
                "province_code": null,
                "country_code": "vn",
                "default": false,
                "district": null,
                "district_code": null,
                "ward": null,
                "ward_code": null
            },
            {
                "address1": null,
                "address2": null,
                "city": null,
                "company": null,
                "country": "Vietnam",
                "first_name": "Như  Lan",
                "id": 1000373503,
                "last_name": null,
                "phone": "0126534826",
                "province": null,
                "zip": "70000",
                "name": " Như  Lan",
                "province_code": null,
                "country_code": "vn",
                "default": false,
                "district": null,
                "district_code": null,
                "ward": null,
                "ward_code": null
            },
            {
                "address1": null,
                "address2": null,
                "city": null,
                "company": null,
                "country": "Vietnam",
                "first_name": "Như  Lan",
                "id": 1000373502,
                "last_name": null,
                "phone": "0126534826",
                "province": null,
                "zip": "70000",
                "name": " Như  Lan",
                "province_code": null,
                "country_code": "vn",
                "default": false,
                "district": null,
                "district_code": null,
                "ward": null,
                "ward_code": null
            },
            {
                "address1": null,
                "address2": null,
                "city": null,
                "company": null,
                "country": "Vietnam",
                "first_name": "Như  Lan",
                "id": 1000373501,
                "last_name": null,
                "phone": "0126534826",
                "province": null,
                "zip": "70000",
                "name": " Như  Lan",
                "province_code": null,
                "country_code": "vn",
                "default": false,
                "district": null,
                "district_code": null,
                "ward": null,
                "ward_code": null
            },
            {
                "address1": null,
                "address2": null,
                "city": null,
                "company": null,
                "country": "Vietnam",
                "first_name": "Như  Lan",
                "id": 1000373500,
                "last_name": null,
                "phone": "0126534826",
                "province": null,
                "zip": "70000",
                "name": " Như  Lan",
                "province_code": null,
                "country_code": "vn",
                "default": false,
                "district": null,
                "district_code": null,
                "ward": null,
                "ward_code": null
            },
            {
                "address1": null,
                "address2": null,
                "city": null,
                "company": null,
                "country": "Vietnam",
                "first_name": "Như  Lan",
                "id": 1000373499,
                "last_name": null,
                "phone": "0126534826",
                "province": null,
                "zip": "70000",
                "name": " Như  Lan",
                "province_code": null,
                "country_code": "vn",
                "default": false,
                "district": null,
                "district_code": null,
                "ward": null,
                "ward_code": null
            },
            {
                "address1": null,
                "address2": null,
                "city": null,
                "company": null,
                "country": "Vietnam",
                "first_name": "Như  Lan",
                "id": 1000373497,
                "last_name": null,
                "phone": "0126534826",
                "province": null,
                "zip": "70000",
                "name": " Như  Lan",
                "province_code": null,
                "country_code": "vn",
                "default": false,
                "district": null,
                "district_code": null,
                "ward": null,
                "ward_code": null
            },
            {
                "address1": null,
                "address2": null,
                "city": null,
                "company": null,
                "country": "Vietnam",
                "first_name": "Như  Lan",
                "id": 1000373496,
                "last_name": null,
                "phone": "0126534826",
                "province": null,
                "zip": "70000",
                "name": " Như  Lan",
                "province_code": null,
                "country_code": "vn",
                "default": false,
                "district": null,
                "district_code": null,
                "ward": null,
                "ward_code": null
            },
            {
                "address1": null,
                "address2": null,
                "city": null,
                "company": null,
                "country": "Vietnam",
                "first_name": "Như  Lan",
                "id": 1000373486,
                "last_name": null,
                "phone": "0126534826",
                "province": null,
                "zip": "70000",
                "name": " Như  Lan",
                "province_code": null,
                "country_code": "vn",
                "default": false,
                "district": null,
                "district_code": null,
                "ward": null,
                "ward_code": null
            }
        ],
        "created_at": "2019-01-01T16:06:27.811Z",
        "email": "nhulan@gmail.com",
        "first_name": "Như  Lan",
        "id": 1000142445,
        "multipass_identifier": null,
        "last_name": "Nguyễn Ngọc",
        "last_order_id": 1001143419,
        "last_order_name": "#101349",
        "note": null,
        "orders_count": 56,
        "state": "Disabled",
        "tags": null,
        "total_spent": 6163500,
        "total_paid": 0,
        "updated_at": "2019-01-11T07:18:09.760Z",
        "verified_email": false,
        "send_email_invite": false,
        "send_email_welcome": false,
        "password": null,
        "password_confirmation": null,
        "group_name": null,
        "metafields": "",
        "birthday": null,
        "gender": null,
        "last_order_date": null,
        "default_address": {
            "address1": "135 Trần Hưng Đạo",
            "address2": null,
            "city": null,
            "company": null,
            "country": "Vietnam",
            "first_name": "Như  Lan",
            "id": 1000372591,
            "last_name": "Nguyễn Ngọc",
            "phone": "01265348777",
            "province": "Hồ Chí Minh",
            "zip": "70000",
            "name": "Nguyễn Ngọc Như  Lan",
            "province_code": "HC",
            "country_code": "vn",
            "default": true,
            "district": "Quận 1",
            "district_code": "HC466",
            "ward": "Phường Cầu Ông Lãnh",
            "ward_code": "26752"
        }
    },
    "shipping_address": {
        "address1": null,
        "address2": null,
        "city": null,
        "company": null,
        "country": "Vietnam",
        "first_name": "Như  Lan",
        "last_name": "Nguyễn Ngọc",
        "latitude": 0,
        "longitude": 0,
        "phone": "01265348777",
        "province": null,
        "zip": null,
        "name": "Nguyễn Ngọc Như  Lan",
        "province_code": null,
        "country_code": "VN",
        "district_code": null,
        "district": null,
        "ward_code": null,
        "ward": null
    },
    "browser_ip": null,
    "buyer_accepts_marketing": false,
    "cancel_reason": null,
    "cancelled_at": null,
    "cart_token": "a55671c042074e35a48426d7085f47ed",
    "checkout_token": "a55671c042074e35a48426d7085f47ed",
    "closed_at": null,
    "currency": "VND",
    "discount_codes": [],
    "email": "nhulan@gmail.com",
    "financial_status": "pending",
    "fulfillment_status": "notfulfilled",
    "tags": null,
    "gateway": null,
    "gateway_code": null,
    "send_webhooks": "true",
    "landing_site": null,
    "landing_site_ref": null,
    "source": "Online",
    "name": "#101352",
    "note": null,
    "location_id": 482663,
    "number": 1001145807,
    "order_number": "#101352",
    "processing_method": null,
    "referring_site": null,
    "refunds": [],
    "shipping_lines": [
        {
            "code": null,
            "price": 0,
            "source": null,
            "title": null
        }
    ],
    "source_name": "Online",
    "subtotal_price": 392000,
    "tax_lines": null,
    "taxes_included": false,
    "token": "a55671c042074e35a48426d7085f47ed",
    "total_discounts": 0,
    "total_line_items_price": 392000,
    "total_price": 392000,
    "total_tax": 0,
    "total_weight": 0,
    "transactions": [
        {
            "amount": 392000,
            "authorization": null,
            "created_at": "2019-01-11T07:18:11.763Z",
            "device_id": null,
            "gateway": "",
            "id": 1000442440,
            "kind": "pending",
            "order_id": 1001145807,
            "receipt": null,
            "status": null,
            "test": false,
            "user_id": 1000112371,
            "location_id": 482663,
            "payment_details": null,
            "parent_id": null,
            "currency": "VND",
            "haravan_transaction_id": null,
            "external_transaction_id": null,
            "send_email": false
        }
    ],
    "note_attributes": [
        {
            "name": "customer_pay",
            "value": "392000"
        },
        {
            "name": "excess_cash_refund",
            "value": "0"
        }
    ],
    "send_receipt": false,
    "send_fulfillment_receipt": false,
    "inventory_behaviour": "",
    "closed_status": "unclosed",
    "cancelled_status": "uncancelled",
    "confirmed_status": "unconfirmed",
    "user_id": 1000112371,
    "device_id": null,
    "has_promotion": false,
    "is_cod_gateway": false,
    "ref_order_id": 0,
    "ref_order_number": null,
    "utm_source": null,
    "utm_medium": null,
    "utm_campaign": null,
    "utm_term": null,
    "utm_content": null,
    "send_paid": false,
    "_id": "5c38433381d848377806d8eb",
    "created_at": "2019-01-11T07:18:10.007Z",
    "fulfillments": [],
    "id": 1001145807,
    "line_items": [
        {
            "fulfillable_quantity": 10,
            "fulfillment_service": null,
            "fulfillment_status": "notfulfilled",
            "grams": 0,
            "id": 1000602451,
            "price": 39200,
            "price_original": 39200,
            "price_promotion": 0,
            "product_id": 10000434722,
            "variant_id": 101345183,
            "quantity": 10,
            "requires_shipping": true,
            "sku": "SP030-1",
            "title": "Xoài Tứ Quý",
            "variant_title": "L / Xanh",
            "vendor": "VinMart",
            "type": "Rau-Củ-Quả",
            "name": "Xoài Tứ Quý - L / Xanh",
            "gift_card": false,
            "taxable": true,
            "tax_lines": null,
            "product_exists": true,
            "barcode": "XOAI_L",
            "properties": null,
            "total_discount": 0,
            "applied_discounts": [],
            "not_allow_promotion": false,
            "_id": "5c38433381d848377806d8ec",
            "image": {
                "src": "http://d-static.sku.vn/1000111987/product/upload_f0d441f4be5c4dc4bd9e633213124830.jpg",
                "attactment": null,
                "filename": null
            }
        }
    ],
    "updated_at": "2019-01-11T07:18:10.362Z",
    "confirmed_at": null
  }
  ```

## Xử lý đơn hàng

### Request   

*  Đóng gói - Chờ giao  
```
  * Path        : /order-online/${order_id}/wait-ship
  * Simple path : /order-online/1001140437/wait-ship
  * Method      : PUT
  * Body        : None
```

* Đã giao vận chuyển
```
  * Path        : /order-online/${order_id}/shipped
  * Simple path : /order-online/1001140437/shipped
  * Method      : PUT
  * Body        : None
```

* Yêu cầu hủy đơn
```
  * Path        : /order-online/${order_id}/request-cancel
  * Simple path : /order-online/1001140437/request-cancel
  * Method      : PUT
  * Body        : None
```

* Nhập trả đơn hàng đã yêu cầu huỷ
```
  * Path        : /order-online/${order_id}/cancel-refund
  * Simple path : /order-online/1001140437/cancel-refund
  * Method      : PUT
  * Body        : xem bên dưới
```

  * Dữ liệu yêu cầu hủy - nhập trả

    | field | type | example | description |
    |-      |-     |-        |-            |
    | reason | string | "customer" | Lý do hủy đơn hàng, một trong lý do sau : customer (khách hàng đổi ý), inventory (Hết hàng), fraud (Đơn hàng giả mạo), other (còn hàng) |
    | note | string | "Sản phẩm không nguyên tem" | Ghi chú|
    | is_refund_partial | boolean | true | Hoàn trả một phần, nếu đúng, cần đính kèm thông tin hoàn trả, ngược lại toàn bộ sản phẩm sẽ được hoàn trả |
    | refund | object | {} | Thông tin hoàn trả, xem bên dưới |

  * Thông tin hoàn trả

    | field         | type   | example                             | description                                                  |
    |-              |-       |-                                    |-                                                             |
    | refund_reason | number | 7                                   | Mã lý do hoàn trả, xem bảng lý do hoàn trả                   |
    | note          | string | "Sản phẩm không nguyên tem"         | Ghi chú                                                      |
    | amount        | number | 132700                              | Số tiền hoàn trả                                             |
    | line_items    | array  | [{ id : 1000604865, quantity : 1 }] | Danh sách sản phẩm hoàn trả, bao gồm id và số lượng hoàn trả |

  * Lý do hoàn trả

    | code | description            |
    | -    | -                      |
    | 1    | Nhập liệu sai          |
    | 3    | Khách hàng không thích |
    | 5    | Không vừa size         |
    | 7    | Sản phẩm lỗi           |
    | 9    | Khác                   |
    | 11   | Đóng gói sai           |

  * Example
  ```json
  {
    "reason"            : "customer",
    "note"              : "Sản phẩm không nguyên tem",
    "is_refund_partial" : true,
    "refund" : {
        "refund_reason" : 7,
        "note"          : "Sản phẩm không nguyên tem",
        "amount"        : 132700,
        "line_items"    : [{
            "id"        : 1000604865,
            "quantity"  : 1
        }]
    }
  }
  ```

### Response

* Success :
  * Status : 200
  * Body : Updated order, has 'haraoesapp_extend_data.status' change to target status
  ```json
  {
    "haraoesapp_extend_data": {
      "fulfillment": {
        "manager": 0,
        "carrier_order_id": 0,
        "location_id": 482668,
        "tracking_link": "",
        "tracking_code": "",
        "tracking_company": "Giao Hàng Nhanh 2018",
        "shipping_package": 11,
        "carrier_service_package": 53319,
        "carrier_service_code": "",
        "carrier_service_package_name": "Nhanh",
        "note": "",
        "notify_customer": false,
        "cod_amount": 0,
        "total_weight": 0,
        "transport_type": 0,
        "sender_phone": "",
        "is_new_service_package": true,
        "is_view_before": 1,
        "sync_status": 1,
        "last_time_sync": "2019-01-11T03:20:42.130Z",
        "retry_times": 0,
        "message": ""
      },
      "sync_log": {
        "erp": {
          "sync_status": 3,
          "last_time_sync": "2019-01-02T10:20:24.178Z",
          "retry_time": 0,
          "messages": "Invalid data : [\"barcode is required\"]",
          "line_item_id": 0
        },
        "order_by_line_item": [
          {
            "sync_status": 1,
            "last_time_sync": "2019-01-02T10:20:24.167Z",
            "retry_time": 0,
            "messages": "",
            "line_item_id": 1000600059,
            "_id": "5c2c9068e70bc249b079fae2"
          }
        ],
        "order_by_line_item_refund": []
      },
      "shipping_method": 1,
      "reorder_from": "",
      "order_merge_from": [],
      "auto_action": 0,
      "transaction_payment_methods": [
        3
      ],
      "is_refund_all": false,
      "full_text_search": "1001140437 Nguyễn Ngọc Như  Lan Nguyễn Ngọc nguyễn ngọc như  lan nguyễn ngọc nhulan@gmail.com nhulan@gmail.com 0126534826",
      "user_sale": 0,
      "status": 22,
      "call_times": 0,
      "shop_id": 1000111987,
      "store_id": 100001,
      "location_id": 0,
      "location_code": 0,
      "store_code": 0,
      "store_hr_code": "",
      "location_hr_code": "",
      "assign_employee_at": "2019-01-03T02:46:01.839Z",
      "user_review": 1000113120,
      "callback_at": null,
      "user_callback": 0,
      "customer_confirm_at": "2019-01-03T02:47:28.122Z",
      "user_confirm_customer": 1000113120,
      "out_of_stock_at": null,
      "user_out_of_stock": 0,
      "cancel_at": null,
      "user_cancel": 0,
      "assign_store_at": "2019-01-03T02:47:34.228Z",
      "user_assign_store": 1000113120,
      "wait_ship_at": "2019-01-11T03:20:42.130Z",
      "user_wait_ship": 1000113120,
      "shipped_at": null,
      "user_shipped": 0,
      "request_cancel_at": null,
      "request_cancel_note": "",
      "user_request_cancel": 0,
      "cancel_return_at": null,
      "user_cancel_return": 0,
      "completed_at": null,
      "user_completed": 0,
      "exchange_at": null,
      "user_exchange": 0,
      "exchange_partial_at": null,
      "user_exchange_partial": 0,
      "return_at": null,
      "user_return": 0,
      "return_partial_at": null,
      "user_return_partial": 0,
      "order_exchange_origin": 0,
      "call_back_customer": 0,
      "customer_pay": 0,
      "customer_card": 0,
      "customer_cash": 0,
      "excess_cash_refund": 0,
      "handle_discount": "",
      "cash_voucher": [],
      "order_number": "0",
      "order_refund": [],
      "order_exchange": []
    },
    "billing_address": {
      "address1": "135 Trần Hưng Đạo",
      "address2": null,
      "city": null,
      "company": null,
      "country": "Vietnam",
      "first_name": "Như  Lan",
      "id": 1000142445,
      "last_name": "Nguyễn Ngọc",
      "phone": "0126534826",
      "province": "Hồ Chí Minh",
      "zip": null,
      "name": "Nguyễn Ngọc Như  Lan",
      "province_code": "HC",
      "country_code": "VN",
      "default": true,
      "district": "Quận 1",
      "district_code": "HC466",
      "ward": "Phường Cầu Ông Lãnh",
      "ward_code": "26752"
    },
    "client_details": {
      "accept_language": null,
      "browser_ip": null,
      "session_hash": null,
      "user_agent": null,
      "browser_height": null,
      "browser_width": null
    },
    "customer": {
      "accepts_marketing": false,
      "addresses": [
        {
          "address1": "135 Trần Hưng Đạo",
          "address2": null,
          "city": null,
          "company": null,
          "country": "Vietnam",
          "first_name": "Như  Lan",
          "id": 1000372591,
          "last_name": "Nguyễn Ngọc",
          "phone": "0126534826",
          "province": "Hồ Chí Minh",
          "zip": "70000",
          "name": "Nguyễn Ngọc Như  Lan",
          "province_code": "HC",
          "country_code": "vn",
          "default": true,
          "district": "Quận 1",
          "district_code": "HC466",
          "ward": "Phường Cầu Ông Lãnh",
          "ward_code": "26752"
        },
        {
          "address1": null,
          "address2": null,
          "city": null,
          "company": null,
          "country": "Vietnam",
          "first_name": "Như  Lan",
          "id": 1000372672,
          "last_name": "Nguyễn Ngọc",
          "phone": "0126534826",
          "province": null,
          "zip": "70000",
          "name": "Nguyễn Ngọc Như  Lan",
          "province_code": null,
          "country_code": "vn",
          "default": false,
          "district": null,
          "district_code": null,
          "ward": null,
          "ward_code": null
        },
        {
          "address1": null,
          "address2": null,
          "city": null,
          "company": null,
          "country": "Vietnam",
          "first_name": "Như  Lan",
          "id": 1000372660,
          "last_name": "Nguyễn Ngọc",
          "phone": "0126534826",
          "province": null,
          "zip": "70000",
          "name": "Nguyễn Ngọc Như  Lan",
          "province_code": null,
          "country_code": "vn",
          "default": false,
          "district": null,
          "district_code": null,
          "ward": null,
          "ward_code": null
        },
        {
          "address1": null,
          "address2": null,
          "city": null,
          "company": null,
          "country": "Vietnam",
          "first_name": "Như  Lan",
          "id": 1000372644,
          "last_name": "Nguyễn Ngọc",
          "phone": "0126534826",
          "province": null,
          "zip": "70000",
          "name": "Nguyễn Ngọc Như  Lan",
          "province_code": null,
          "country_code": "vn",
          "default": false,
          "district": null,
          "district_code": null,
          "ward": null,
          "ward_code": null
        },
        {
          "address1": null,
          "address2": null,
          "city": null,
          "company": null,
          "country": "Vietnam",
          "first_name": "Như  Lan",
          "id": 1000372631,
          "last_name": "Nguyễn Ngọc",
          "phone": "0126534826",
          "province": null,
          "zip": "70000",
          "name": "Nguyễn Ngọc Như  Lan",
          "province_code": null,
          "country_code": "vn",
          "default": false,
          "district": null,
          "district_code": null,
          "ward": null,
          "ward_code": null
        },
        {
          "address1": null,
          "address2": null,
          "city": null,
          "company": null,
          "country": "Vietnam",
          "first_name": "Như  Lan",
          "id": 1000372613,
          "last_name": "Nguyễn Ngọc",
          "phone": "0126534826",
          "province": null,
          "zip": "70000",
          "name": "Nguyễn Ngọc Như  Lan",
          "province_code": null,
          "country_code": "vn",
          "default": false,
          "district": null,
          "district_code": null,
          "ward": null,
          "ward_code": null
        }
      ],
      "created_at": "2019-01-01T16:06:27.811Z",
      "email": "nhulan@gmail.com",
      "first_name": "Như  Lan",
      "id": 1000142445,
      "multipass_identifier": null,
      "last_name": "Nguyễn Ngọc",
      "last_order_id": 1001140614,
      "last_order_name": "#101273",
      "note": null,
      "orders_count": 18,
      "state": "Disabled",
      "tags": null,
      "total_spent": 1702500,
      "total_paid": 0,
      "updated_at": "2019-01-03T01:21:58.000Z",
      "verified_email": false,
      "send_email_invite": false,
      "send_email_welcome": false,
      "password": null,
      "password_confirmation": null,
      "group_name": "",
      "metafields": null,
      "birthday": "1998-10-20T00:00:00.000Z",
      "gender": null,
      "last_order_date": "2019-01-03T01:21:55.000Z",
      "default_address": {
        "address1": "135 Trần Hưng Đạo",
        "address2": null,
        "city": null,
        "company": null,
        "country": "Vietnam",
        "first_name": "Như  Lan",
        "id": 1000372591,
        "last_name": "Nguyễn Ngọc",
        "phone": "0126534826",
        "province": "Hồ Chí Minh",
        "zip": "70000",
        "name": "Nguyễn Ngọc Như  Lan",
        "province_code": "HC",
        "country_code": "vn",
        "default": true,
        "district": "Quận 1",
        "district_code": "HC466",
        "ward": "Phường Cầu Ông Lãnh",
        "ward_code": "26752"
      }
    },
    "shipping_address": {
      "address1": "135 Trần Hưng Đạo",
      "address2": null,
      "city": null,
      "company": null,
      "country": "Vietnam",
      "first_name": "Như  Lan",
      "last_name": "Nguyễn Ngọc",
      "latitude": 0,
      "longitude": 0,
      "phone": "0126534826",
      "province": "Hồ Chí Minh",
      "zip": null,
      "name": "Nguyễn Ngọc Như  Lan",
      "province_code": "HC",
      "country_code": "VN",
      "district_code": "HC466",
      "district": "Quận 1",
      "ward_code": "26752",
      "ward": "Phường Cầu Ông Lãnh"
    },
    "browser_ip": null,
    "buyer_accepts_marketing": false,
    "cancel_reason": null,
    "cancelled_at": null,
    "cart_token": "48949c0dd9704ad085769e884b6baa5e",
    "checkout_token": "48949c0dd9704ad085769e884b6baa5e",
    "closed_at": null,
    "currency": "VND",
    "discount_codes": [],
    "email": "nhulan@gmail.com",
    "financial_status": "pending",
    "fulfillment_status": "notfulfilled",
    "tags": "",
    "gateway": "Thanh toán khi giao hàng (COD)",
    "gateway_code": "cod",
    "send_webhooks": "false",
    "landing_site": null,
    "landing_site_ref": null,
    "source": "web",
    "name": "#101269",
    "note": null,
    "location_id": 482663,
    "number": 1001140437,
    "order_number": "#101269",
    "processing_method": null,
    "referring_site": "web",
    "refunds": [],
    "shipping_lines": [
      {
        "code": null,
        "price": 0,
        "source": null,
        "title": null
      }
    ],
    "source_name": "web",
    "subtotal_price": 22400,
    "tax_lines": null,
    "taxes_included": false,
    "token": "48949c0dd9704ad085769e884b6baa5e",
    "total_discounts": 0,
    "total_line_items_price": 22400,
    "total_price": 22400,
    "total_tax": 0,
    "total_weight": 0,
    "transactions": [
      {
        "amount": 22400,
        "authorization": null,
        "created_at": "2019-01-02T10:20:17.277Z",
        "device_id": null,
        "gateway": "Thanh toán khi giao hàng (COD)",
        "id": 1000439950,
        "kind": "Pending",
        "order_id": 1001140437,
        "receipt": null,
        "status": null,
        "test": false,
        "user_id": 1000113120,
        "location_id": 482663,
        "payment_details": null,
        "parent_id": null,
        "currency": null,
        "haravan_transaction_id": null,
        "external_transaction_id": null,
        "send_email": false,
        "is_cod_gateway": false
      }
    ],
    "note_attributes": [],
    "send_receipt": false,
    "send_fulfillment_receipt": false,
    "inventory_behaviour": null,
    "closed_status": "unclosed",
    "cancelled_status": "uncancelled",
    "confirmed_status": "confirmed",
    "user_id": 1000113120,
    "device_id": null,
    "has_promotion": false,
    "is_cod_gateway": false,
    "ref_order_id": 0,
    "ref_order_number": null,
    "utm_source": null,
    "utm_medium": null,
    "utm_campaign": null,
    "utm_term": null,
    "utm_content": null,
    "send_paid": true,
    "_id": "5c2c9068e70bc249b079fadf",
    "created_at": "2019-01-02T10:20:17.100Z",
    "fulfillments": {
      "created_at": "2019-01-11T03:20:39.7881166Z",
      "id": 1010126664,
      "order_id": 1001140437,
      "receipt": null,
      "status": "success",
      "tracking_company": "Giao Hàng Nhanh 2018",
      "tracking_company_code": "ghn2018",
      "tracking_numbers": [
        "4AN9YA5R"
      ],
      "tracking_number": "4AN9YA5R",
      "tracking_url": "https://track.ghn.vn/order/tracking?code=",
      "tracking_urls": [
        "https://track.ghn.vn/order/tracking?code="
      ],
      "updated_at": null,
      "line_items": [
        {
          "fulfillable_quantity": 0,
          "fulfillment_service": "Thủ công",
          "fulfillment_status": "Đã hoàn thành",
          "grams": 0,
          "id": 1000600059,
          "price": 22400,
          "product_id": 10000434696,
          "quantity": 1,
          "requires_shipping": true,
          "sku": "SP002-2",
          "title": "Bắp giò heo Vissan",
          "variant_id": 101345094,
          "variant_title": "Đỏ / M",
          "vendor": "Vissan",
          "name": "Bắp giò heo Vissan",
          "variant_inventory_management": null,
          "properties": null,
          "product_exists": true
        }
      ],
      "province": "Hồ Chí Minh",
      "province_code": "HC",
      "district": "Quận 1",
      "district_code": "HC466",
      "ward": "Phường Cầu Ông Lãnh",
      "ward_code": "26752",
      "cod_amount": 0,
      "carrier_status_name": "Chờ lấy hàng",
      "carrier_cod_status_name": "Không",
      "carrier_status_code": "readytopick",
      "carrier_cod_status_code": "none",
      "location_id": 482668,
      "note": null,
      "carrier_service_package": 0,
      "carrier_service_package_name": "Nhanh",
      "is_new_service_package": false,
      "coupon_code": null,
      "ready_to_pick_date": "2019-01-11T03:20:36.1334721Z",
      "picking_date": null,
      "delivering_date": null,
      "delivered_date": null,
      "return_date": null,
      "not_meet_customer_date": null,
      "waiting_for_return_date": null,
      "cod_paid_date": null,
      "cod_receipt_date": null,
      "cod_pending_date": null,
      "cod_not_receipt_date": null,
      "is_view_before": null,
      "country": null,
      "country_code": null,
      "zip_code": null,
      "city": null,
      "real_shipping_fee": 31900,
      "shipping_notes": " CHOXEMHANGKHONGTHU",
      "total_weight": 0,
      "package_length": 0,
      "package_width": 0,
      "package_height": 0,
      "boxme_servicecode": null,
      "transport_type": 0,
      "address": null,
      "sender_phone": null,
      "sender_name": null,
      "carrier_service_code": null
    },
    "id": 1001140437,
    "line_items": [
      {
        "fulfillable_quantity": 1,
        "fulfillment_service": null,
        "fulfillment_status": "notfulfilled",
        "grams": 0,
        "id": 1000600059,
        "price": 22400,
        "price_original": 22400,
        "price_promotion": 0,
        "product_id": 10000434696,
        "variant_id": 101345094,
        "quantity": 1,
        "requires_shipping": true,
        "sku": "SP002-2",
        "title": "Bắp giò heo Vissan",
        "variant_title": "Đỏ / M",
        "vendor": "Vissan",
        "type": "Thịt",
        "name": "Bắp giò heo Vissan - Đỏ / M",
        "gift_card": false,
        "taxable": true,
        "tax_lines": null,
        "product_exists": true,
        "barcode": null,
        "properties": [],
        "total_discount": 0,
        "applied_discounts": null,
        "not_allow_promotion": false,
        "_id": "5c2d6468e1de203a2812c576",
        "image": {
          "src": "http://d-static.sku.vn/1000111987/product/upload_172812391a3f4054898d9ee3a4244f6b.jpg",
          "attactment": null,
          "filename": null
        }
      }
    ],
    "updated_at": "2019-01-03T01:24:51.543Z",
    "confirmed_at": "2019-01-02T10:20:18.610Z"
  }
  ```

* Fail :
  * Status : 4xx
  * Body : 
  ```json
  {
    "error": true,
    "message": [
        "Đơn hàng hiện tại không thể thực hiện tác vụ này"
    ]
  }
  ```