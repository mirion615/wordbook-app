## usersテーブル
| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |


### Association
- has_many : books


## booksテーブル
| Column             | Type       | Options           |
| ------------------ | ---------- | ----------------- |
| title              | string     | null: false       |
| user_id            | references | foreign_key: true |

### Association
- has_many    : book_words
- has_many    : book_languages
- belongs_to : user


## addressesテーブル
| Column        | Type       | Options           |
| ------------- | ---------- | ----------------- |
| postal_code   | string     | null: false       |
| ship_from_id  | integer    | null: false       |
| city          | string     | null: false       |
| house_number  | string     | null: false       |
| building_name | string     |
| phone_number  | string     | null: false       |
| purchase      | references | foreign_key: true |

### Association
- belongs_to : purchase


## purchasesテーブル
| Column        | Type       | Options           |
| ------------- | ---------- | ----------------- |
| user          | references | foreign_key: true |
| item          | references | foreign_key: true |

### Association
- has_one    : address
- belongs_to : user
- belongs_to : item