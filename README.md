# chatspace DB設計
## users テーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :posts
- has_many :users_groups
- has_many  :groups,  through:  :users_groups

## groups テーブル
|Column|Type|Options|
|------|----|-------|
|title|string|null: false|
### Association
- has_many :users_groups
- has_many  :users,  through:  :users_groups
- has_many :posts

## users_groups テーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text||
|image|text||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group