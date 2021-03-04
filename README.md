# テーブル設計

## users テーブル

| Column             | Type       | Option                    |
| ------------------ | ---------- | ------------------------- |
| nickname           | string     | null: false               |
| email              | string     | null: false, unique: true |
| encrypted_password | string     | null: false               |
| job                | string     | null: false               |
| profile            | string     | null: false               |


### Association

- has_many :tweets
- has_many :comments


## tweets テーブル

| Column          | Type       | Option                         |
| --------------- | ---------- | ------------------------------ |
| user            | references | null: false, foreign_key: true |
| tomorrow_pride  | text       | null: false                    |
| yesterday_pride | text       | null: false                    |


### Association

- belongs_to :user
- has_many :comments


## comments テーブル

| Column       | Type       | Option                         |
| ------------ | -----------| ------------------------------ |
| user         | references | null: false, foreign_key: true |
| tweet        | references | null: false, foreign_key: true |
| text         | text       | null: false                    |


### Association

- belongs_to :user
- belongs_to :tweet