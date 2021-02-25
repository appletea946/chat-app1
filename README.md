# テーブル設計

## usersテーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_many: room_users
- has_many: rooms, through: room_users
- has_many: messages

## roomsテーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many: room_users
- has_many: users, through: room_users
- has_many: messages

## room_usersテーブル

| Column  | Type    | Options                        |
| ------- | ------- | ------------------------------ |
| user_id | integer | null: false, foreign_key: true |
| room_id | integer | null: false, foreign_key: true |

### Association

- belongs_to: user
- belongs_to: room


## messagesテーブル

| Column  | Type      | Options                        |
| ------- | --------- | ------------------------------ |
| content | string    |                                |
| user    | reference | null: false, foreign_key: true |
| room    | reference | null: false, foreign_key: true |

### Association

- belongs_to: user
- belongs_to: room

