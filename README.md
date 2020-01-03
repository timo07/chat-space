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

## groups_usersテーブル

|Columu|Type|Options|
|------|----|------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## userテーブル
|Columu|Type|Options|
|------|----|------|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false, index: true|
### Association
- has_many :groups_users
- has_many :tweets
- has_many :groups, through:  :group_users

## tweetテーブル
|Columu|Type|Options|
|------|----|------|
|image|text||
|text|text||
|user-id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groupテーブル
|Column|Type|Options|
|------|----|------|
|name|text|null: false|
### Association
- has_many :groups_users
- has_many :tweets
- has_many :users, through:  :group_users
