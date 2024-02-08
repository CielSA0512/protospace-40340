#テーブル設計

## users テーブル

| column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false |
| name               | string | null: false |
| profile            | string | null: false |
| occupation         | string | null: false |
| position           | string | null: false |

### Association

- has_many :comments
- has_many :prototypes

## prototypes テーブル

| column     | Type       | Options     |
| ---------- | ---------- | ----------- |
| title      | string     | null: false |
| catch_copy | text       | null: false |
| concept    | text       | null: false |
| user       | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_many :comments

## comments テーブル

| column    | Type       | Options     |
| --------- | ---------- | ----------- |
| content   | text       | null: false |
| prototype | references | null: false, foreign_key: true |
| user      | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :prototype