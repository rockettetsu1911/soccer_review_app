## userテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|null:false, unique:true|
|nickname|string|null:false|
|favorite_team|string|null:false|
|favorite_player|string|null:false|
|email|string|null:false|

### Asociation

- has_many: :tweets,dependent: :destroy
- has_many: :comments,dependent: :destroy

## tweetsテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|null:false,unique:true|
|title|string|null:false|
|text|text|
|home_team|string|null:false|
|away_team|string|null:false|
|user_id|

### Asociation
- has_many: :comments,dependent: :destroy
- belongs_to: :user
- has_many: :tags, through: :tweets_tags
- has_many: :tweets_tags

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|null:false,unique:true|
|text|text|null:false|
|user_id|
|tweet_id|


### Asociation

- belongs_to: :tweet
- belongs_to: :user

## tagsテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|null:false,unique:true|
|name|string|null:false,unique:true|

### Asociation

- has_many: :tweets, through: :tweets_tag
- has_many: :tweets_tag

## tweets_tagsテーブル
|Column|Type|Options|
|------|----|-------|
|id|integer|null:false,unique:true|
|tweet_id|
|tag_id|

### Asociation

- belongs_to: :tag
- belongs_to: :tweet