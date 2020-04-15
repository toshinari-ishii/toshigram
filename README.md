# PhotoRoom

概要
写真やイラストをアップするアプリ
主にアーティストや楽曲のジャケットをアップ

## Function(機能)
ユーザー登録、投稿、削除、いいね、コメント、詳細ページ

## Function Introduction(機能紹介)

投稿機能
![投稿機能](app/assets/images/addphoto.gif)

いいね&コメント機能
![いいね&コメント機能](app/assets/images/comment.gif)

詳細ページ&削除機能
![詳細ページ&削除機能](app/assets/images/delete.gif)


### DB設計

Column|Type|Options


## usersテーブル
email |string |add_index : email, unique : true
encryted_password |string |add_index : email, unique : true
name |string |null: false
### Association
- has_many :posts, dependent: :destroy
- has_many :likes
- has_many :comments


## postテーブル
caption |string
user_id |references |foreign_key: true, null: false
### Association
- belongs_to :user
- has_many :photos, dependent: :destroy
- has_many :likes, dependent: :destroy
- has_many :comments, dependent: :destroy
<!-- - has_many :url, dependent: :destroy -->




## photosテーブル
image | string |null: false
post_id |references |foreign_key: true, null: false

### Association
- belongs_to :post


<!-- ## urlテーブル
url | string |null: false
post_id |references |foreign_key: true, null: false

### Association
- belongs_to :post -->



## likesテーブル
post_id |references |foreign_key: true, null: false
user_id |references |foreign_key: true, null: false
### Association
- belongs_to :user
- belongs_to :post



## commentsテーブル
comment |text
post_id |references |foreign_key: true, null: false
user_id |references |foreign_key: true, null: false

### Association
- belongs_to :user
- belongs_to :post

