# テーブル設計

## users テーブル

| Column                   | Type   | Options     |
| -----------------------  | ------ | ----------- |
| nickname                 | string | null: false |
| email                    | string | null: false |
| encrypted_password       | string | null: false |
| last-name                | string | null: false |
| first-name               | string | null: false |
| last-name-kana           | string | null: false |
| first-name-kana          | string | null: false |
| user_birth_year          | integer| null: false |
| user_birth_month         | integer| null: false |
| user_birth_day           | integer| null: false |

### Association
- has_many :items
- has_many :buyers

***
### items テーブル
| Column                   | Type       | Options     |
| -----------------------  | ---------- | ----------- |
| item-name                | string     | null: false |
| item-image               | string     | null: false |
| item-info                | text       | null: false |
| item-category            | string     | null: false |
| item-sales-status        | string     | null: false |
| item-shipping-fee-status | string     | null: false |
| item-scheduled-delivery  | integer    | null: false |
| item-price               | integer    | null: false |
| user                     | references | null: false |

### Association
- belongs_to :users
- has_one :buyers

***
### buyers テーブル
 Column                   | Type       | Options     |
| -----------------------  | ---------- | ----------- |
| card-number              | integer    | null: false |
| card-exp-number          | integer    | null: false |
| card-exp-year            | integer    | null: false |
| card-cvc                 | integer    | null: false |
| postal-code              | integer    | null: false |
| prefecture               | string     | null: false |
| city                     | string     | null: false |
| addresses                | string     | null: false |
| building                 | string     |             |
| phone-number             | integer    | null: false |
| item                     | references | null: false |
| user                     | references | null: false |

### Association
- belongs_to :items
- belongs_to :users