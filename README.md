# テーブル設計

## users テーブル

| Column                | Type   | Option     |
| --------------------- | ------ | ---------- |
| nickname              | string | null:false |
| email                 | string | null:false |
| password              | string | null:false |
| encrpted_password     | string | null:false |
| last_name             | string | null:false |
| first_name            | string | null:false |
| furigana_last_name    | string | null:false |
| furigana_first_name   | string | null:false |
| birthday              | date   | null:false |

### Association

- has_many :items
- has_many :purchases

## items テーブル

| Column      | Type       | Option                         |
| ----------- | ---------- | ------------------------------ |
| name        | string     | null: false                    |
| category    | string     | null: false                    |
| condition   | string     | null: false                    |
| shipping    | string     | null: false                    |
| region      | string     | null: false                    |
| period      | string     | null: false                    |
| price       | integer    | null: false                    |
| explanation | string     | null: false                    |
| user        | references | null: false, foreign_key: true |

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

| Column       | Type       | Option                         |
| ------------ | ---------- | ------------------------------ |
| postal_code  |            |                                |
| prefecture   | integer    | null: false                    |
| city         | string     | null: false                    |
| address      | string     | null: false                    |
| phone_number | string     | null: false                    |
| building     | string     | null: false                    |
| purchase     | references | null: false, foreign_key: true |

### Association

- belongs_to :purchase

