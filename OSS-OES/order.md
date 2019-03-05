# Đồng bộ đơn hàng từ OSS => OES 

## Dữ liệu

Gồm 2 phần :

* Seller :
  * tham khảo [Haravan Order API](https://docs.haravan.com/blogs/api-reference/1000018025-order#show)

* Dữ liệu mở rộng của OES :

```js
{
  "reorder_from_order_id"     : { description: 'id của đơn hàng cũ'           , type : Number , default : 0  },
  "reorder_from_order_number" : { description: 'order number của đơn hàng cũ' , type : String , default : "" },
  "user_sale"                 : { description: 'Mã nhân viên bán hàng'        , type : Number , default : 0  },
  'shop_id'                   : { description: 'Mã cửa hàng'                  , type : Number , default : 0  },
  "store_id"                  : { description: 'Mã chi nhánh'                 , type : Number , default : 0  },
  "location_id"               : { description: 'Mã kho'                       , type : Number , default : 0  }, 
  //-------------------------------------- Thông tin xử lý đơn hàng --------------------------------------------------
  "status"                : { description: 'Trạng thái đơn hàng, xem bên dưới'     , type : Number  , default : 0    },
  "assign_employee_at"    : { description: 'Thời gian gán nhân viên xử lý'         , type : Date    , default : null },
  "user_review"           : { description: 'nhân viên xử lý'                       , type : Number  , default : 0    },
  "callback_at"           : { description: 'Thời gian gọi lại'                     , type : Date    , default : null },
  "call_times"            : { description: 'Số lần gọi lại khách hàng'             , type : Number  , default : 0    },
  "user_callback"         : { description: 'Nhân viên gọi lại'                     , type : Number  , default : 0    },
  "customer_confirm_at"   : { description: 'Thòi gian xác nhận khách hàng'         , type : Date    , default : null },
  "user_confirm_customer" : { description: 'Nhân viên xác nhận khách hàng'         , type : Number  , default : 0    },
  "out_of_stock_at"       : { description: 'Thời gian xác nhận hết hàng'           , type : Date    , default : null },
  "user_out_of_stock"     : { description: 'Nhân viên xác nhận hết hàng'           , type : Number  , default : 0    },
  "cancel_at"             : { description: 'Thời gian hủy đơn hàng'                , type : Date    , default : null },
  "user_cancel"           : { description: 'Nhân viên hủy đơn'                     , type : Number  , default : 0    },
  "assign_store_at"       : { description: 'Thời gian gán chi nhánh'               , type : Date    , default : null },
  "user_assign_store"     : { description: 'Nhân viên gán chi nhánh'               , type : Number  , default : 0    },
  "wait_ship_at"          : { description: 'Thời gian chờ giao'                    , type : Date    , default : null },
  "user_wait_ship"        : { description: 'Nhân viên xác nhận chờ giao'           , type : Number  , default : 0    },
  "shipped_at"            : { description: 'Thời gian xác nhận đã giao vận chuyển' , type : Date    , default : null },
  "user_shipped"          : { description: 'Nhân viên xác nhận đã giao vận chuyển' , type : Number  , default : 0    },
  "request_cancel_at"     : { description: 'Thời gian yêu cầu hủy đơn hàng'        , type : Date    , default : null },
  "request_cancel_note"   : { description: 'Ghi chú của yêu cầu hủy đơn hàng'      , type : String  , default : ''   },
  "user_request_cancel"   : { description: 'Nhân viên yếu cầu hủy đơn hàng'        , type : Number  , default : 0    },
  "cancel_return_at"      : { description: 'Thời gian hủy - nhập trả đơn hàng'     , type : Date    , default : null },
  "user_cancel_return"    : { description: 'Nhân viên hủy - nhập trả đơn hàng'     , type : Number  , default : 0    },
  "completed_at"          : { description: 'Thời gian hoàn tất đơn hàng'           , type : Date    , default : null },
  "user_completed"        : { description: 'Nhân viên hoàn tất đơn hàng'           , type : Number  , default : 0    },
  "exchange_at"           : { description: 'Thời gian đổi hàng'                    , type : Date    , default : null },
  "user_exchange"         : { description: 'Nhân viên đổi hàng'                    , type : Number  , default : 0    },
  "exchange_partial_at"   : { description: 'Thời gian đổi hàng một phần'           , type : Date    , default : null },
  "user_exchange_partial" : { description: 'Nhân viên đổi hàng một phần'           , type : Number  , default : 0    },
  "return_at"             : { description: 'Thời gian trả hàng'                    , type : Date    , default : null },
  "user_return"           : { description: 'Nhân viên trả hàng'                    , type : Number  , default : 0    },
  "return_partial_at"     : { description: 'Thời gian trả hàng một phần'           , type : Date    , default : null },
  "user_return_partial"   : { description: 'Nhân viên trả hàng một phần'           , type : Number  , default : 0    },
  "is_refund_all"         : { description: 'đã đổi trả hết'                        , type : Boolean , default : false},
  //--------------------------------------------- Thông tin vận chuyển ---------------------------------------------------
  "shipping_method"       : { description: 'Phương thức vận chuyển', type : Number , default : 0, enum: [
    1, // nhà vận chuyển
    3, // Nhân viên cửa hàng tự giao
    5, // Khách hàng đến lấy
  ]},

  "fulfillment": {
    "carrier_order_id" : { description: 'Mã đơn hàng của đơn vị vận chuyển' , type : Schema.Types.Mixed, default : 0 },
    "tracking_link"    : { description: 'Tracking link'                     , type : String            , default : ''},
    "tracking_code"    : { description: 'Tracking code'                     , type : String            , default : ''},
    "user_shipping"    : { description: 'Mã nhân viên giao hàng \
                                         (phương thức vận chuyển = Nhân viên cửa hàng tự giao)', type : String, default : ''},

    // Thông tin vận chuyển gửi sang seller, chỉ cần khi phương thức vận chuyển = nhà vận chuyển
    "tracking_company"             : { type : String  , default : ''    },
    "shipping_package"             : { type : Number  , default : 0     },
    "carrier_service_package"      : { type : String  , default : 0     },
    "carrier_service_code"         : { type : String  , default : ''    },
    "carrier_service_package_name" : { type : String  , default : ''    },
    "note"                         : { type : String  , default : ''    },
    "notify_customer"              : { type : Boolean , default : false },
    "cod_amount"                   : { type : Number  , default : 0     },
    "transport_type"               : { type : Number  , default : 0     },
    "sender_phone"                 : { type : String  , default : ''    },
    "is_new_service_package"       : { type : Boolean , default : true  },
    "is_view_before"               : { type : Number  , default : 1     },
    "package_length"               : { type : Number  , default : 0     },
    "package_width"                : { type : Number  , default : 0     },
    "package_height"               : { type : Number  , default : 0     },
    "total_weight"                 : { type : Number  , default : 0     },
  },
  //-------------- thông tin đơn hàng trả (thông tin thêm của refund) --------------------
  'order_refund': [     
    {
      'type'        : { description: 'loại : 0 = trả, 1 = yêu cầu trả', type : Number, default : 0},
      "id"          : { description: 'Mã phiếu trả ( refund id )'     , type : Number, default : 0},
      'store_id'    : { description: 'Mã chi nhánh trả hàng'          , type : Number, default : 0},
      'location_id' : { description: 'Mã kho trả hàng'                , type : Number, default : 0},
      'reason'       : { description: 'Lý do trả', enum : [
        1 , // Nhập liệu sai
        3 , // Khách hàng không thích
        5 , // Không vừa size
        7 , // Sản phẩm lỗi
        11, // Đóng gói sai
        9 , // Khác
      ], type : Number, default : 0},
      'requester'    : { description: 'Người yêu cầu trả'             , type : Number, default : 0 },
      'other_reason' : { description: 'Lý do, khi reason = lý do khác', type : String, default : ''},
      'user_id'      : { description: 'Nhân viên trả hàng'            , type : Number, default : 0 },
      "line_items" : [{
        "id"       : { description: 'Mã line item' , type : Number, default : 0},
        "quantity" : { description: 'Số lượng item', type : Number, default : 0},
      }],
      "created_at" : { description: 'Ngày trả', type : Date, default : null},
    }
  ],
  //------------------------- Thông tin đổi hàng ---------------------
  'order_exchange': [
    {
      'type'      : { description: 'loại : 0 = trả, 1 = yêu cầu trả', type : Number, default : 0 },
      'user_id'   : { description: 'Nhân viên đổi hàng'             , type : Number, default : 0 },
      'order_id'  : { description: 'id của đơn hàng mới'            , type : Number, default : 0 },
      'refund_id' : { description: 'id của đơn hàng trả'            , type : Number, default : 0 },
      "line_items"      : [{
        "line_item_id" : { description: 'id line_item của đơn hàng gốc', type : Number, default : 0},
        "variant_id"   : { description: 'id của sản phẩm cần trả'      , type : Number, default : 0},
        "quantity"     : { description: 'Số cần đổi'                   , type : Number, default : 0},
        "item_exchange" : [{
          "id"         : { description: 'id line_item đơn hàng mới', type : Number, default : 0},
          "variant_id" : { description: 'id của sản phẩm mới'      , type : Number, default : 0},
          "quantity"   : { description: 'Số lượng của sản phẩm mới', type : Number, default : 0} 
        }]
      }],
      'store_id'        : { description: 'Mã chi nhánh', type : Number, default : 0},
      'location_id'     : { description: 'Mã kho', type : Number, default : 0},
      'reason'          : { description: 'Lý do đổi', enum : [
        20, // đổi hàng 
        23, // nhập liệu sai
      ], type : Number, default : 0},
      "created_at"      : { description: 'Ngày đổi hàng', type : Date, default   : null},
    }
  ],
  "handle_discount"    : { description: 'Giảm giá tay tổng đơn hàng, theo mẫu : <TYPE=[fixed, percent]>#<VALUE>' example: 'fixed#500000', type : String, default : ''},
}
```

* Danh sách trạng thái đơn hàng của OES :

  | Mã   | Mô tả                  |
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