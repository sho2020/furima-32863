# テーブル設計

## users テーブル

| Column                | Type   | Option                   |
| --------------------- | ------ | ------------------------ |
| nickname              | string | null:false               |
| email                 | string | null:false, unique: true |
| encrpted_password     | string | null:false               |
| last_name             | string | null:false               |
| first_name            | string | null:false               |
| furigana_last_name    | string | null:false               |
| furigana_first_name   | string | null:false               |
| birthday              | date   | null:false               |

### Association

- has_many :items
- has_many :purchases

## items テーブル

| Column       | Type       | Option                         |
| ------------ | ---------- | ------------------------------ |
| name         | string     | null: false                    |
| category_id  | integer    | null: false                    |
| condition_id | integer    | null: false                    |
| shipping_id  | integer    | null: false                    |
| region_id    | integer    | null: false                    |
| period_id    | integer    | null: false                    |
| price        | integer    | null: false                    |
| explanation  | text       | null: false                    |
| user         | references | null: false, foreign_key: true |

### Association

- belongs_to : user
- has_one :purchase

## purchases テーブル

| Column | Type       | Option                         |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| item   | references | null: false, foreign_key: true |

### Association

- belong_to :user
- belong_to :item
- has_one :destination

## destinations テーブル

| Column        | Type       | Option                         |
| ------------- | ---------- | ------------------------------ |
| postal_code   | string     | null: false                    |
| prefecture_id | integer    | null: false                    |
| city          | string     | null: false                    |
| address       | string     | null: false                    |
| phone_number  | string     | null: false                    |
| building      | string     |                                |
| purchase      | references | null: false, foreign_key: true |

### Association

- belongs_to :purchase

