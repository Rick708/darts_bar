## app名
Darts_bar

## 概要
ダーツバー検索サイト

## 使用技術
【インフラ】
- AWS:EC2,S3
- docker,docker-compose  

【フロントエンド】
- HTML(haml)
- CSS(Sass)
- JavaScript
- jQuery  

【バックエンド】
- Ruby
- Ruby on Rails
- MySQL

【その他】
- git
- GitHub

## 機能一覧  
【ユーザー機能】
- 新規登録
- ログイン
- ログアウト
- 情報変更
- ダーツバー投稿 

【ダーツバー】
- googlemap表示
- 一覧機能
- 検索機能
- 口コミ

## 画像  
No image

# DB設計

## usersテーブル
- ユーザーテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|mail|string|null: false, unique: true|
|password|string|null: false|
|profile|text||

### Association
- has_many :bars
- has_many :comments

## barsテーブル
- shopテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|darts|intger|null:false|
|dartstype|intger|null:false|
|profile|text|null:false|
|tell|string|null:false|
|price|integer|null:false|
|ability|integer|null:false|
|size|intger|null: false|

### enum
- shopステータス
- darts,dartstype,price,ability,size

### Association
- has_many :comments
- has_many :business
- belongs_to :Addresses
- belongs_to :user

## addressesテーブル
- shop住所テーブル

|Column|Type|Options|
|------|----|-------|
|bar_id|intrger|null: false, foreign_key: true|
|address|string|null: false|
|latitude|float||
|longitude|float||
### Association
- belongs_to :user

## imagesテーブル
- shop画像テーブル

|Column|Type|Options|
|------|----|-------|
|image|string||
|bar_id|integer|null: false, foreign_key: true|
### Asociation
- belongs_to :bar

## commentsテーブル
- コメントテーブル

|Column|Type|Options|
|------|----|-------|
|content|text|null: false|
|user_id|integer|null: false, foreign_key: true|
|bar_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :bar
