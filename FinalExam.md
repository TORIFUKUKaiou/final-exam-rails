# 期末試験

受験上の注意:  

- 試験中は、Codespaces／Generative AI／授業配布資料／インターネットの技術記事の利用を許可します。
- 60点以上が合格です。
- 合格戦略: まず Part 1（Ruby 基礎）で40点以上を確実に取り、Part 2（Rails 基礎）と Part 3（実技）で20点以上を積み上げてください。


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

### 問6 条件分岐とループ（5点）

次のコードを読み、出力を上から順にすべて書きなさい。

```ruby
score = 85

if score >= 90
  puts "優秀"
elsif score >= 70
  puts "良好"
else
  puts "要努力"
end

puts "---"

3.times do |i|
  if i % 2 == 0
    puts "#{i}は偶数"
  else
    puts "#{i}は奇数"
  end
end

puts "---"

name = "Ruby"
puts name.length > 3 ? "長い名前" : "短い名前"
```

### 問7 文字列操作（5点）

次のコードを読み、出力を上から順にすべて書きなさい。

```ruby
text = "Hello World"

puts text.upcase
puts text.downcase
puts text.length

puts "---"

words = text.split(" ")
puts words[0]
puts words[1]

puts "---"

message = "Ruby"
puts message + "言語"
puts message * 3

puts "---"

str = "programming"
puts str.include?("gram")
puts str.include?("java")
```

### 問8 カレンダー出力（5点）

次のコードを読み、出力を上から順にすべて書きなさい。

```ruby
require 'date'

today = Date.today
year = today.year
month = today.month

puts "#{year}年#{month}月"
puts "日 月 火 水 木 金 土"

# 今月1日の曜日を取得（0=日曜日）
first_day = Date.new(year, month, 1)
start_wday = first_day.wday

# 今月の日数を取得
last_day = Date.new(year, month, -1).day

# 最初の週の空白を出力
start_wday.times { print "   " }

# 1日から月末まで出力
(1..last_day).each do |day|
  printf "%2d ", day
  
  # 土曜日の後は改行
  if (day + start_wday - 1) % 7 == 6
    puts
  end
end

puts
puts "今月は#{last_day}日まであります"
```

### 問9 配列の基本操作（5点）

次のコードの空欄を埋めて、指定された出力になるようにしなさい。プログラム全体を提出しなさい。

```ruby
numbers = [1, 2, 3, 4, 5]

# 配列の最初の要素を出力
puts numbers[____]

# 配列の最後の要素を出力  
puts numbers[____]

# 配列に6を追加
numbers.____(6)

# 配列の長さを出力
puts numbers.____

# 配列の2番目から3番目の要素を出力
puts numbers[____].inspect
```

期待される出力：
```
1
5
6
[2, 3]
```

### 問10 メソッドの作成（5点）

次の仕様に従って、`greet_user`メソッドを完成させなさい。プログラム全体を提出しなさい。

```ruby
def greet_user(name, age)
  # ここにコードを書く
  # "こんにちは、[name]さん！あなたは[age]歳ですね。" を出力する
end

# テスト用のコード（変更しないこと）
greet_user("田中", 20)
greet_user("佐藤", 25)
```

期待される出力：
```
こんにちは、田中さん！あなたは20歳ですね。
こんにちは、佐藤さん！あなたは25歳ですね。
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

1) `/help` にアクセスしたとき、呼び出されるコントローラ名とアクション名は？ コントローラ名はクラス名で答えなさい。（5点）
2) `/` にアクセスしたとき、呼び出されるコントローラ名とアクション名は？ コントローラ名はクラス名で答えなさい。（5点）


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
3) データベースをマイグレーションするrailsのコマンドを答えなさい（2点）  
4) User を3件作成するRubyコード例を1通り書きなさい（`create!` 推奨、単純な3行で可）（2点）  

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
