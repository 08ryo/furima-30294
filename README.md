#テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| last_name          | string | null: false               |
| first_name         | string | null: false               |
| last_name_kana     | string | null: false               |
| first_name_kana    | string | null: false               |
| birthday           | date   | null: false               |

### Association

- has_many :items
- belongs_to :card

## items テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| name        | string     | null: false                    |
| description | text       | null: false                    |
| status      | text       | null: false                    |
| postage     | string     | null: false                    |
| prefecture  | string     | null: false                    |
| days        | string     | null: false                    |
| price       | string     | null: false                    |
| category_id | references | null: false, foreign_key: true |
| user_id     | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :category
- belongs_to :image

## destination テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| postcode        | string     | null: false                    |
| prefecture      | string     | null: false                    |
| city            | string     | null: false                    |
| block           | string     | null: false                    |
| phone_number    | string     | null: false                    |
| user_id         | references | null: false, foreign_key: true |

### Association

- belongs_to :user

## order テーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| user_id     | references | null: false, foreign_key: true |
| item_id     | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
