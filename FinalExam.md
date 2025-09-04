# 期末試験

受験上の注意:  

- 試験中は、Codespaces／Generative AI／授業配布資料／インターネットの技術記事の利用を許可します。
- 合格戦略: まず Part 1（Ruby 基礎）で40点以上を確実に取り、Part 2（Rails 基礎）と Part 3（別紙・実技）で20点以上を積み上げてください。


## Part 1. Rubyの基本(50点)

### 問1 FizzBuzz（5点）

次のコードを読み、出力を上から順にすべて書きなさい。  


```ruby
numbers = 1..15
numbers.each do |n|
  if (n % 3 == 0) && (n % 5 == 0) # && は and も可, if (n % 15 == 0) でも可
    puts "FizzBuzz"
  elsif n % 3 == 0
    puts "Fizz"
  elsif n % 5 == 0
    puts "Buzz"
  else
    puts n
  end
end
```

### 問2 メソッドの引数と戻り値（5点）

次のコードを読み、出力を上から順にすべて書きなさい。  

```ruby
def double(x)
  x * 2
end

def greet(name = "Ruby")
  "Hello, #{name}"
end

puts double(3)
puts greet
puts greet("Rails")
```


### 問3 配列とハッシュ（5点）

次のコードを読み、出力を上から順にすべて書きなさい。  

```ruby
fruits = ["apple", "banana", "cherry"]
fruits << "banana"
fruits.uniq!

counts = { "a" => 1 }
counts["b"] = 0
counts["a"] = counts["a"] + 2

puts fruits.length
puts counts["a"]
puts counts["b"]
```

### 問4 クラス／インスタンス／継承（5点）

次のコードを読み、出力を上から順にすべて書きなさい。  

```ruby
class Character
  def initialize(name, hp)
    @name = name
    @hp = hp
    puts "#{@name}があらわれた"
  end

  def attack
    puts "#{@name}は攻撃した"
  end
end

class Hero < Character
  def special_move
    puts "#{@name}の会心の一撃！！！"
  end
end

h = Hero.new("yourname", 100)  # => （出力を書け）
h.attack                        # => （出力を書け）
h.special_move                  # => （出力を書け）
```


### 問5 each / map / select（5点）

次のコードを読み、出力を上から順にすべて書きなさい。  
あわせて、`each` と `map` の戻り値の違いを説明しなさい。  

```ruby
arr = [1, 2, 3, 4, 5]

a = arr.each { |n| n * 2 }
b = arr.map  { |n| n * 2 }
c = arr.select { |n| n.odd? }

puts a.inspect
puts b.inspect
puts c.inspect
```



---

## Part 2. Rails の基本（30点）

配点の目安:
- MVC／フォルダ構成の理解を問う設問です。
- ファイルパス、役割、呼び出し関係が答えられれば高得点です。

### 問1 ルーティングとURL（10点）
次の `config/routes.rb` を読み、各問に答えなさい。  

```ruby
Rails.application.routes.draw do
  root "static_pages#home"
  get "/help", to: "static_pages#help"
  resources :users, only: [:index, :show]
end
```

1) `/help` にアクセスしたとき、呼び出されるコントローラ名とアクション名は？（5点）
2) `/` にアクセスしたとき、呼び出されるコントローラ名とアクション名は？（5点）


### 問2 コントローラとビュー（10点）
次のコントローラ定義を読み、設問に答えなさい。

```ruby
# app/controllers/static_pages_controller.rb
class StaticPagesController < ApplicationController
  def help
    @tips = ["A", "B"]
  end

  def home
  end

  def about
  end

  def contact
  end
end
```

1) `StaticPagesController`には何個のアクションがありますか？ 答えとその根拠を説明しなさい。 (3点)
2) `help` アクションに対応するビューのファイルパスは？（7点）

### 問3 マイグレーションとモデル（10点）
次のマイグレーションを読み、設問に答えなさい。  

```ruby
# db/migrate/20240901000000_create_users.rb
class CreateUsers < ActiveRecord::Migration[7.0]
  def change
    create_table :users do |t|
      t.string :name
      t.string :email
      t.timestamps
    end
  end
end
```

1) 作成されるテーブル名と主なカラム名（型）を答えなさい（4点）  
2) 開発用の初期データを投入するファイルパスを答えなさい（2点）  
3) User を3件作成するRubyコード例を1通り書きなさい（`create!` 推奨、単純な3行で可）（4点）  

---

採点に関する共通注意:
- すべての設問で、最終答えが誤っていても「どこを読み、どう考えたか」の説明があれば部分点を与えます。
- ファイルパスは Rails 標準の構成（`app/models`, `app/views`, `app/controllers`, `config/routes.rb`, `db/migrate`, `db/seeds.rb`）に基づいて採点します。

---

## Part 3. Railsのトラブルシューティング(20点)

Codespaceで立ち上げたRailsアプリケーションは一部の機能が正常に動きません。  
あなたの顧客はたいへん困っています。Railsのプロであるあなたが解決してください。  


1) `/help` にアクセスするとエラーが発生します。あきらめますか、エラーを解決しますか。(3点)
2) まず最初に修正すべき1つ目のファイルは何で、どのように変更しますか。(9点)
3) 2)で、1ファイルを書き換えただけでは解決しませんでした。以下のコードをどこかに置けば解決します。ファイルパスを答えてください。(8点)

```ruby
<% provide(:title, "Help") %>
<h1>Help</h1>
<p>
  Get help on the Ruby on Rails Tutorial at the
  <a href="https://railstutorial.jp/help">Rails Tutorial Help page</a>.
  To get help on this sample app, see the
  <a href="https://railstutorial.jp/#ebook"><em>Ruby on Rails Tutorial</em>
  book</a>.
</p>
```
