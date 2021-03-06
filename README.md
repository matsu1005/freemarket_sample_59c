# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation
# freemarket_sample_59c DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false|
|first_name|string|null: false|
|last_name|string|null: false|
|first_name_kana|string|null: false|
|last_name_kana|string|null: false|
|birth_year|integer|null: false|
|birth_month|integer|null: false|
|birth_day|integer|null: false|
|profile_text|string|
|icon_img|string|
### Association
- has_many :comments, dependent: :destroy
- has_many :addresses, dependent: :destroy
- has_many :items, dependent: :destroy
- has_many :credit_payments, dependent: :destroy
- has_many :sns_authentications, dependent: :destroy

## addressesテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|post_number|integer|null: false|
|prefecture|string|null: false|
|city|string|null: false|
|address_line|integer|null: false|
|building|string|
### Association
- belongs_to :user

## sns_authenticationsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|google_authentications|string|
|facebook_authentications|string|
### Association
- belongs_to :user

## credit_paymentsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|number|integer|null: false|
|cvc|integer|null: false|
|exp_month|integer|null: false|
|exp_year|integer|null: false|
### Association
- belongs_to :user


## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|
|user_id|references|null: false, foreign_key: true|
|item_id|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :product

## itemsテーブル
|Column|Type|Options|
|------|----|-------|
|users_id|references|null: false, foreign_key: true|
|categorie_id|references|null: false, foreign_key: true|
|brand_id|references|null: false, foreign_key: true|
|image_id|references|foreign_key: true|
|condition|string|null: false|
|name|string|null: false|
|detail|text|
|shipping_charge_fee|integer|null: false|
|shipping_method|string|null: false|
|shipping_origin|string|null: false|
|days_to_shipping|string|null: false|
|price|integer|null: false|
### Association
- belongs_to :user
- belongs_to :brand
- belongs_to :category
- has_many :images, dependent: :destroy

## imagesテーブル
|Column|Type|Options|
|------|----|-------|
|item_id|references|null: false, foreign_key: true|
|image|string|
### Association
- belongs_to :item

## brandsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :items


## categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|parent_id|integer|null: true|
### Association
- has_many :items



* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
