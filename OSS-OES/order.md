# Đồng bộ đơn hàng từ OSS => OES 

- [Đồng bộ đơn hàng từ OSS => OES](#Đồng-bộ-đơn-hàng-từ-oss--oes)
  - [Dữ liệu](#dữ-liệu)
    - [Seller :](#seller-)
    - [Dữ liệu mở rộng của OES :](#dữ-liệu-mở-rộng-của-oes-)
    - [Danh sách trạng thái đơn hàng của OES :](#danh-sách-trạng-thái-đơn-hàng-của-oes-)
    - [Danh sách nguồn đơn hàng ( sources )](#danh-sách-nguồn-đơn-hàng--sources-)

## Dữ liệu

Gồm 2 phần :

* Lưu ý : Dữ liệu bên dưới chú thích `Thông tin sau khi tạo` không bắt buộc, nhưng khuyến khích truyền nếu có dữ liệu

```json
{
  "seller"          : {},
  "oes_extend_data" : {}
}
```

### Seller :
  * tham khảo [Haravan Order API](https://docs.haravan.com/blogs/api-reference/1000018025-order#show)

  ```js
  {
    "user_id"                  : {type: Number, default: null},
    'location_id'              : {type: Number, default: 0},

    'line_items'               : [{
      "id"                     : {type: Number , default: 0    },
      "price"                  : {type: Number , default: 0    , description: 'Giá sau cùng của sản phẩm'},
      "price_original"         : {type: Number , default: 0    , description: 'Giá gốc của sản phẩm'},
      "product_id"             : {type: Number , default: 0    },
      "variant_id"             : {type: Number , default: 0    },
      "quantity"               : {type: Number , default: 0    },
      "gift_card"              : {type: Boolean, default: false},
      "taxable"                : {type: Boolean, default: false},
      "tax_lines"              : {type: String , default: ""   },
      "barcode"                : {type: String , default: ""   },
      "properties"             : [{
        "name"  : { type : String, example: "Khuyến mãi"              },
        "value" : { type : String, example: '1000116957 - KM_HEO_10K' },
      }],
      "total_discount"         : {type: Number, default: 0, description: 'Tổng tiền giảm giá của sản phẩm'},
    }],
    //----------------------- Giảm giá trên đơn hàng --------------
    'total_discounts'          : {type: Number, default: 0},
    'discount_codes'           : [{
      "amount" : { type: Number, example: 50000          },
      "code"   : { type: String, example: "KM_50K"       },
      "type"   : { type: String, example: "fixed_amount" },
    }], 
    //------------------------ Khách hàng --------------------------
    'customer_id'              : {type: Number, default: 0},
    'email'                    : {type: String, default: ""},
    'shipping_address'         : {
      'address1'               : {type: String, default: ""},
      'address2'               : {type: String, default: ""},
      'city'                   : {type: String, default: ""},
      'company'                : {type: String, default: ""},
      'first_name'             : {type: String, default: ""},
      'last_name'              : {type: String, default: ""},
      'phone'                  : {type: String, default: ""},
      'zip'                    : {type: String, default: ""},
      'province_code'          : {type: String, default: ""},
      'country_code'           : {type: String, default: ""},
      'district_code'          : {type: String, default: ""},
      'ward_code'              : {type: String, default: ""},
    },
    'billing_address'          : {
      'address1'               : {type: String, default: ""},
      'address2'               : {type: String, default: ""},
      'city'                   : {type: String, default: ""},
      'company'                : {type: String, default: ""},
      'first_name'             : {type: String, default: ""},
      'id'                     : {type: Number, default: 0},
      'last_name'              : {type: String, default: ""},
      'phone'                  : {type: String, default: ""},
      'zip'                    : {type: String, default: ""},
      'province_code'          : {type: String, default: ""},
      'country_code'           : {type: String, default: ""},
      'district_code'          : {type: String, default: ""},
      'ward_code'              : {type: String, default: ""}
    },
    'shipping_lines'           : [{
      "code"   : { type: String, example: "Giao hàng tận nơi"},
      "price"  : { type: Number, example: 10000              },
      "source" : { type: String                              },
      "title"  : { type: String, example: "Giao hàng tận nơi"},
    }],

    // tham khảo : https://docs.haravan.com/blogs/api-reference/1000018042-transaction
    "transactions" : { description: 'Nếu không truyền, hệ thống tự động sinh ra', type: [{
      //-------------------- Thông tin tạo ------------------------------------
      "amount"         : { type: String  , example: 60000                            },
      "gateway"        : { type: String  , example: "Thanh toán khi giao hàng (COD)" },
      "kind"           : { type: String  , default: "capture"                        },
      "status"         : { type: String  , default: "success"                        },
      "is_cod_gateway" : { type: Boolean , default: false                            },
      //--------------------- Thông tin sau khi tạo -------------------------
      "id"             : { type: Number  , example: 1000484797                       },
      "created_at"     : { type: Date    , example: "2019-03-05T04:53:37.057Z"       },
    }]},

    //------------------------ khác ----------------------------
    'currency'                 : {type: String , default: 'VND' },
    "is_cod_gateway"           : {type: Boolean, default: false },
    'gateway'                  : {type: String , example: "Thanh toán khi giao hàng (COD)" },
    'gateway_code'             : {type: String , lowercase: true, example: "cod" },
    'source'                   : {type: String , default: "31"  }, // Xem danh sách nguồn bên dưới
    'source_name'              : {type: String , default: "pos"  },     
    'note_attributes'          : [],
    'note'                     : {type: String, default: ""},

    //--------------------- Thông tin sau khi tạo -----------------
    'id'                       : {type: Number, require: true, unique: true},
    'order_number'             : {type: String, default: ""},

    ////----------------------- Time ---------------------------
    'cancelled_at'             : {type: Date, default: null},
    'closed_at'                : {type: Date, default: null},
    'created_at'               : {type: Date, default: Date.now},
    'confirmed_at'             : {type: Date, default: Date.now},
    'updated_at'               : {type: Date, default: Date.now},
    'created_at'               : {type: Date, default: Date.now},

    ////------------------------ Status -----------------------
    'cancel_reason'            : {type: String, default: ""},
    'financial_status'         : {type: String, default: ""},
    "closed_status"            : {type: String, default: ""},
    "cancelled_status"         : {type: String, default: ""},
    "confirmed_status"         : {type: String, default: ""},
    'fulfillment_status'       : {type: String, default: ""},
  }
  ```

### Dữ liệu mở rộng của OES :

```js
{
  "reorder_from_order_id"     : { description: 'id của đơn hàng cũ'           , type : Number , default : 0  },
  "reorder_from_order_number" : { description: 'order number của đơn hàng cũ' , type : String , default : "" },
  "user_sale"                 : { description: 'Mã nhân viên bán hàng'        , type : Number , default : 0  },
  'shop_id'                   : { description: 'Mã cửa hàng'                  , type : Number , default : 0  },
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
  "user_shipping"    : { description: 'Mã nhân viên giao hàng \
                                         (phương thức vận chuyển = Nhân viên cửa hàng tự giao)', type : String, default : ''},
  
  //------------------------ Thông tin vận chuyển của seller, chỉ cần khi phương thức vận chuyển = nhà vận chuyển ---------
  //--------------------------- tham khảo : https://docs.haravan.com/blogs/api-reference/1000018043-fulfillment -----------
  "fulfillment" : {
    "carrier_order_id"             : { type : String, description: 'Mã đơn hàng của đơn vị vận chuyển'},
    // ---------------------- Thông tin tạo --------------------------------------------
    "tracking_link"                : { type : String                                       },
    "tracking_code"                : { type : String                                       },
    "tracking_company"             : { type : String  , example: 'Giao Hàng Nhanh 2018'    },
    "shipping_package"             : { type : Number  , example: 11                        },
    "carrier_service_package"      : { type : Number  , example: 53320                     },
    "carrier_service_code"         : { type : String  , example: ''                        },
    "carrier_service_package_name" : { type : String  , example: 'Nhanh'                   },
    "note"                         : { type : String  , example: 'Giao vào buổi chiều'     },
    "notify_customer"              : { type : Boolean , example: false                     },
    "cod_amount"                   : { type : Number  , example: 206200                    },
    "sender_phone"                 : { type : String  , example: '0968726159'              },
    "is_view_before"               : { type : Number  , example: 1                         },
    "package_length"               : { type : Number  , example: 10                        },
    "package_width"                : { type : Number  , example: 10                        },
    "package_height"               : { type : Number  , example: 10                        },
    "total_weight"                 : { type : Number  , example: 500                       },
    //-------------------- Thông tin sau khi tạo ----------------------------------------
    "id"                           : { type : String  , example: 1010151323                },
    "created_at"                   : { type : Date    , example: "2019-03-05T03:47:06.72Z" },
    "status"                       : { type : String  , example: "success"                 },
    "updated_at"                   : { type : Date    , example: "2019-03-05T03:47:06.72Z" },
    "carrier_status_name"          : { type : String  , example: "Chờ lấy hàng"            },
    "carrier_cod_status_name"      : { type : String  , example: "Chưa nhận"               },
    "carrier_status_code"          : { type : String  , example: "readytopick"             },
    "carrier_cod_status_code"      : { type : String  , example: "codpending"              },
    "ready_to_pick_date"           : { type : Date    , example: "2019-03-05T03:47:04Z"    },
    "picking_date"                 : { type : Date    , default: null                      },
    "delivering_date"              : { type : Date    , default: null                      },
    "delivered_date"               : { type : Date    , default: null                      },
    "return_date"                  : { type : Date    , default: null                      },
    "not_meet_customer_date"       : { type : Date    , default: null                      },
    "waiting_for_return_date"      : { type : Date    , default: null                      },
    "cod_paid_date"                : { type : Date    , default: null                      },
    "cod_receipt_date"             : { type : Date    , default: null                      },
    "cod_pending_date"             : { type : Date    , default: null                      },
    "cod_not_receipt_date"         : { type : Date    , default: null                      },
    "cancel_date"                  : { type : Date    , default: null                      },
  },
  //-------------- thông tin đơn hàng trả (thông tin thêm của refund) --------------------
  'order_refund': [     
    {
      'type'        : { description: 'loại : 0 = trả, 1 = yêu cầu trả', type : Number, default : 0},
      "id"          : { description: 'Mã phiếu trả ( refund id )'     , type : Number, default : 0},
      'location_id' : { description: 'Mã kho trả hàng'                , type : Number, default : 0},
      'reason'       : { description: 'Lý do trả', enum : [
        1 , // Nhập liệu sai
        3 , // Khách hàng không thích
        5 , // Không vừa size
        7 , // Sản phẩm lỗi
        11, // Đóng gói sai
        9 , // Khác
      ], type : Number, default : 0},
      'requester'    : { description: 'Người yêu cầu trả, 1 : khách hàng, 3 : đơn vị vận chuyển', type : Number },
      'other_reason' : { description: 'Lý do, khi reason = lý do khác', type : String, default : ''},
      'user_id'      : { description: 'Nhân viên trả hàng'            , type : Number, default : 0 },
      "line_items" : [{
        "id"       : { description: 'Mã line item' , type : Number, default : 0},
        "quantity" : { description: 'Số lượng item', type : Number, default : 0},
      }],
      "note"       : { description: 'Ghi chú', type : String, default : null},
      "restock"       : { description: 'Nhập kho sản phẩm trả ?', type : boolean, default : true},
      "transactions" : { description: 'Nếu không truyền, hệ thống tự động sinh ra', type: [{
        "amount"     : { type: String, example: -60000                           },
        "created_at" : { type: Date  , example: "2019-03-05T04:53:37.057Z"       },
        "gateway"    : { type: String, example: "Thanh toán khi giao hàng (COD)" },
        "id"         : { type: Number, example: 1000484797                       },
        "kind"       : { type: String, default: "refund"                         },
        "status"     : { type: String, default: "success"                        },
      }]},
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
      'location_id'     : { description: 'Mã kho', type : Number, default : 0},
      'reason'          : { description: 'Lý do đổi', enum : [
        20, // đổi hàng 
        23, // nhập liệu sai
      ], type : Number, default : 0},
      "created_at"      : { description: 'Ngày đổi hàng', type : Date, default   : null},
    }
  ],
  "handle_discount"    : { description: 'Giảm giá tay tổng đơn hàng, theo mẫu : <TYPE=[fixed, percent]>#<VALUE>', example: 'fixed#500000', type : String, default : ''},
}
```

### Danh sách trạng thái đơn hàng của OES :

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

### Danh sách nguồn đơn hàng ( sources )
  Mã  | Tên
  -   |-
  1   | guphukien
  3   | masoffer
  5   | deca
  7   | chat
  9   | haravan
  11	| facebook
  13	| lazada
  15	| adayroi
  17	| callcenter
  19	| zalora
  21	| tiki
  23	| lotte
  25	| shoppe
  27	| zalo
  29	| web
  31	| pos
  33	| draft
  35	| staff
  37	| harafunel
  39	| app_android
  41	| app_ios
  43	| harapos
