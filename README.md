## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|password|string|null: false|
|email_address|string|null: false, unique: true|

### Association
- has_many :groups, through: members
- has_many :messages
- has_many :members

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :messages
- has_many :users, through :members
- has_many :members

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|user|references|null: false|
|group|references|null: false|

### Association
- belongs_to :group
- belongs_to :user

## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
