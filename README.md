
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

