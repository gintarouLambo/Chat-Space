# ChatSpace DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false|

### Association
- has_many :messages
- has_many :groups_users
- has_many :group, through: :groups_users
- has_many :groups

## Groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :groups_users
- has_many :user, through: :groups_users
- has_many :users, has_many :messages

## Groups_Usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

## Messageテーブル
|Column|Type|Options|
|------|----|-------|
|text|text||
|image|text||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

