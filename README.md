# テーブル設計

## users テーブル

| Column                   | Type   | Options                   |
| ------------------------ | ------ | ------------------------- |
| nickname                 | string | null: false               |
| email                    | string | null: false, unique: true |
| encrypted_password       | string | null: false               |
| last_name                | string | null: false               |
| first_name               | string | null: false               |
| last_name_kana           | string | null: false               |
| first_name_kana          | string | null: false               |
| user_birth_date          | integer| null: false               |

### Association
- has_many :items
- has_many :buyers

***
### items テーブル
| Column                   | Type       | Options                             |
| ------------------------ | ---------- | ----------------------------------- |
| item_name                | string     | null: false                         |
| item_info                | text       | null: false                         |
| item_category            | integer    | null: false                         |
| item_sales_status        | integer    | null: false                         |
| item_shipping_fee_status | integer    | null: false                         |
| item_scheduled_delivery  | integer    | null: false                         |
| item_price               | integer    | null: false                         |
| user                     | references | null: false, foreign_key: true      |

### Association
- belongs_to :users
- has_one :buyers

***
### buyers テーブル
| Column                   | Type       | Options                        |
| ------------------------ | ---------- | ------------------------------ |
| item                     | references | null: false, foreign_key: true |
| user                     | references | null: false, foreign_key: true |
| address                  | references | null: false, foreign_key: true |


### Association
- belongs_to :items
- belongs_to :users
- has_one: addresses

***
### addresses テーブル
| Column                   | Type       | Options                        |
| ------------------------ | ---------- | ------------------------------ |
| postal_code              | integer    | null: false                    |
| prefecture               | string     | null: false                    |
| city                     | string     | null: false                    |
| addresses                | string     | null: false                    |
| building                 | string     |                                |
| phone_number             | integer    | null: false                    |
| buyer                    | references | null: false, foreign_key: true |


### Association
- belongs_to :buyers
