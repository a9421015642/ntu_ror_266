1. 請用簡單的方式敘述以下每一行程式碼：

  ```ruby 
  a = 1 
  @a = 2
  @@a = 5
  user = User.new
  user.name
  user.name = "Joe"
  ```
  #### ANS:
  ```ruby
  a = 1              # 將值 1 指派(assign)給區域變數(local variable) a。
  @a = 2             # 將值 2 指派給實例變數(instance variable) a。
  @@a = 5            # 將值 5 指派給類別變數(class variable) a。
  user = User.new    # 用 User 類別創造一個新物件 user。
  user.name          # 使用名為 name 的 method。
  user.name = "Joe"  # 將字串 "Joe" 指派給 user.name。
  ```

2. 什麼是 module? 請寫一段程式碼說明一個 class 要如何使用一個 module 裡面的 method?

  #### Ans:
  ```
  module: 存放會可能會重複使用的 method
  module為存放程式碼的區塊，使用時使用include關鍵字。
  ```

Module: 存放會可能會重複使用的 method；class 要使用關鍵字 include 後，才能使用 module 內的 method。

3. 請說明 class variable 和 instance variable 之間的差別

  #### ANS:
  ```
  Class variable: 類別變數，class 本身的資料。
  Instance variable: 實例變數，實例建立後使用。
  ```
4. 請說明 class method 和 instance method 之間的差別

  #### Ans:
  ```
  instance method 需要由物件呼叫;
  class method 使用時不須經由物件。
  ```

5. 如果今天我為一個叫 User 的 class 產生一個新物件的方式是:
  ```ruby
  User.new("Bob", "male", "Engineer")
  ```
請寫出 User class 的 initialize method
  #### ANS:
  ```ruby
  class User
    def initialize(name, gender, position)
      @name = name
      @gender = gender
      @position = position
    end
  end
  ```

6. 在：
  A.  一個 class 裡，method 外面
  B.  一個 class 裡，instance method 裡
  self 分別是指向什麼?
  #### ANS: 
  ```
  self 在 method 外面 - 指向物件本身
  self 在 method 裡面 - 指向物件的變數
  ```
7. attr_accessor 的功能是什麼，它和 attr_reader、attr_writer 之間的差別是什麼？
  #### ANS: 
  ```
  Ruby 不允許物件外部使用實體變數，如要使用，需定義方法。
  attr_accessor: 讀取及寫入 , 初始值為nil 。
  attr_reader 是讀取(屬性唯讀)。
  attr_writer 是寫入(屬性唯寫)。
  ```

8. 請說明 public 和 private method 之間的不同
 #### Ans:
  ```
  public moethod 預設，完全公開 , 可供繼承之類別使用 , 可用物件呼叫
  private method 有存取限制 , 只可在類別內使用。
  ```
9. 請說明 Inheritance 和 Module 之間的差別，它們分別是用於哪些情況？ 請舉例說明
  #### ANS:
  ```
  Inheritance  類別繼承: 繼承，子類別能呼叫父類別的方法。
  Module 模組: 不能用 .new，也不能被繼承。需要使用關鍵字 include 來使用 module 的 method。
  ```
10. 若今天有一個 class 有 include 一個 module，他的 parent class 和 sub class 是否可以使用該 module 裡的 method?
  #### ANS:
  ```。
  Parent class 不能使用。
  sub class 因為繼承了該 class，所以可以使用。
  ```

11. 請間單說明什麼是 Relational Database，什麼是 SQL
  #### ANS:
  ```
  Relational Database: 關聯式資料庫。有關聯的數個資料表，資料表之間由主鍵(Primal Key)和連外鍵(Foreign Key)來建立關聯。
  SQL: Structured Query Language(SQL)，用來操作資料庫的程式語言 , 資料庫管理的程式語言。
  ```