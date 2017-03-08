# DB design

## messages

#### column

- id|integer|null: false|
- text|text||
- image|text||
- user_id|references|foreign_key: ture|
- group_id|references|foreign_key: true|

#### association

belongs_to :user
belongs_to :group


## users

#### column

- id|integer|null: false|
- name|string|null: false|
- email|text|null:false, add_index|
- password|null: false|

#### association

has_many :messages
has_many :groups, through :group_users


## groups

#### column

- id|integer|null: false|
- name|string|null: false|

#### association

has_many :messages
has_many :users, through :group_users


## group_users

#### column

- id|integer|null: false|
- group_id|references|foreign_key: ture|
- user_id|references|foreign_key: ture|

#### association

belongs_to :user
belongs_to :group