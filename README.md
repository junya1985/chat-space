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

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, add_index: true|
|email|string| null: false, unique: true|

### Association
- has_many :groups_users
- has_many :groups, through: groups_users
- has_many :messages


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|

### Association
- has_many :groups_users
- has_many :users, through: groups_users
- has_many :messages



## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|----|
|image|string|----|
|user_id => user|nmber|null: false, foreign_key: true|
|group_id => group|nmber|null: false, foreign_key: true|

create_table :messages do |t|
      t.references :user_id => user, null: false, foreign_key: true,
      t.references :group_id => group, null: false, foreign_key: true
    end

  
### Association
- belongs_to :group
- belongs_to :user


## groups_usersテーブル
|Column|Type|Options|
|user_id => user|nmber|null: false, foreign_key: true|
|group_id => group|nmber|ull: false, foreign_key: true|

create_table : groups_users do |t|
      t.references :user_id => user, null: false, foreign_key: true,
      t.references :group_id => group, null: false, foreign_key: true


##Association|
- belongs_to :group
- belongs_to :user

