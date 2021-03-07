# テーブル設計

## users テーブル

| Column                | Type   | Option     |
| --------------------- | ------ | ---------- |
| nickname              | string | null:false |
| password              | string | null:false |
| password_confirmation | string | null:false |
| last_name             | string | null:false |
| first_name            | string | null:false |
| furigana_last_name    | string | null:false |
| furigana_first_name   | string | null:false |
| birthday              | date   | null:false |

### Association

- has_many :items
- has_many :purchases

## items テーブル

| Column    | Type       | Option                         |
| --------- | ---------- | ------------------------------ |
| picture   |            |                                |
| price     | integer    | null: false                    |
| item_name | string     | null: false                    |
| user      | references | null: false, foreign_key: true |

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

## destination テーブル

| Column       | Type    | Option                         |
| ------------ | ------- | ------------------------------ |
| postal_code  |         |                                |
| prefecture   | integer | null: false                    |
| city         | string  | null: false                    |
| address      | text    | null: false, foreign_key: true |
| phone_number | integer | null: false                    |

### Association

- belongs_to :purchase

