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
|id|integer|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## userテーブル
|Columu|Type|Options|
|------|----|------|
|id|integer|null: false|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false|
### Association
- has_many :groups_users
- has_many :tweet
- has_many :group through:  :group_users

## tweetテーブル
|Columu|Type|Options|
|------|----|------|
|image|text||
|text|text||
|user-id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groupテーブル
|Column|Type|Options|
|------|----|------|
|id|integer|null: false|
|group_name|text|null: false|
### Association
- has_many :groups_users
- has_many :tweet
- has_many :user through:  :group_users
