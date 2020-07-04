# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# chatspace DB設計
## users テーブル
|Column|Type|Options|
|———|——|———-|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :posts
- hsa_many :users_groups
- has_many  :groups,  through:  :users_groups

## groups テーブル
|Column|Type|Options|
|———|——|———-|
|title|string|null: false|
### Association
- has_many :users_groups
- has_many  :users,  through:  :users_groups

## users_groups テーブル
|Column|Type|Options|
|———|——|———-|
|user-id|integer|null: false, foreign_key: true|
|group-id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## postsテーブル
|Column|Type|Options|
|———|——|———-|
|text|text||
|image|text||
|user-id|integer|null: false, foreign_key: true|
|group-id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group