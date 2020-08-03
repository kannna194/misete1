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

# Misete DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false, unique: true|
|password|string|null: false|
|name|string|null: false, index: true, unique: true|

### Association
- has_many :members
- has_many :groups, through: :members
- has_many :posts
- has_many :kids

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true, unique: true|
### Association
- has_many :users, through: :members
- has_many :members
- has_many :posts

## membersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belong_to :user
- belong_to :group

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
|text|text||
|image|text||

### Association
- belongs_to :user
- belongs_to :group

## kidsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true, unique: true|
### Association
- belongs_to :user
- has_many :group
- has_many :posts