## DB設計

## usersテーブル
|Column|Type|Option|
|------|----|------|
|password|string|null: false|
|email|string|null: false, unique: true|
|nickname|string|null: false|
|name|string|null: false|
|kana|string|null: false|
|postal|integer|null: false|
|adress|null: false|
|tel|integer|null: false, unique: true|
|text|text|

### Association
- belongs_to:order
- has_many :items


## itemsテーブル
|Column|Type|Option|
|------|----|------|
|user_id|references|null: false, foreign_key: true|
|image|string|null: false|
|name|string|null: false|
|text|text|null: false|
|category_id|references|
|genre_id|references|
|status|text|null: false|
|days|text|null: false|
|price|integer|null: false|
|sold|boolean|default: false|

### Association
- belongs_to :user
- belongs_to :genre
- belongs_to :category
- has one :order



## genresテーブル
|Column|Type|Option|
|------|----|------|
|name|string|

### Association
- has_many :items


## categoriesテーブル
|Column|Type|Option|
|------|----|------|
|name|string|

### Association
- has_many :items


## ordersテーブル
|Column|Type|Option|
|------|----|------|
|user_id|references|null: false, foreign_key: true|
|item_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :item