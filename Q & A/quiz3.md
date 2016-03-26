1. 請解釋 database.yml, routes.rb, 和 Gemifle 分別是什麼？ 他們分別在一個 Rails 專案裡的什麼位置？ 他們為什麼對一個 Rails 專案如此重要？
  #### ANS: 
  ```ruby
  # 假設在一個名為 ror_project 的專案底下

*database.yml: 
Rails 專案與 database 連結的設定檔
development 是用於開發時的設定
test 是用於執行自動測試時的設定
production 是用於正式環境上的設定

*routes.rb:
設定 URL 的檔案
設定一個 Rails 專案 API (應用程序介面) 

*Gemifle:
宣告在這個 Rails 專案中使用的 gem ( Ruby 套件)
bundler 會依據 gemfile 安裝該專案需要的套件
  ```
2. MVC 架構裡的 M, V, 和 C 分別代表什麼？ 

  #### ANS: 
  ```ruby
    Model:封裝資料與商業邏輯，與資料庫裡的資料表對應
    View:使用者介面，顯示及編輯表單，可內嵌Ruby語法
    Controller:負責將資料送進送出Model，處理從外界(也就是瀏覽器)來的HTTP Request請求，與Model互動後輸出View(也就是HTML) 
  ```
3. 請解釋 CRUD 是哪四個字的縮寫？  

  #### ANS: 
  ```ruby
  C: Create (建立)
  R: Read (讀取)
  U: Update (更新)
  D: Delete (刪除)
  ```
4. 請問在 routes.rb 裡面加入以下程式碼會產生出哪一些 url？ (提示：在 browser 輸入```http://localhost:3000/rails/info/routes```)
  ```ruby
  resources :users
  ```
  #### ANS: 
  ```ruby
users_path  ,GET ,  users#index
,POST, users#create
new_user_path , GET, users#new
edit_user_path , GET , users#edit
user_path , GET ,  users#show
,PATCH ,  users#update
,PUT , users#update
,DELETE  ,  users#destroy
  ```
5. 請解釋 model 檔案和 migration 檔案的差別

  #### ANS: 
  ```ruby
  Model 檔: 
  - 類別繼承 ActiveRecord::Base。
  - 在 model 檔中設定與資料表之間的關聯(一對一 / 一對多 / 多對多)，或基本 CRUD 的操作、資料驗證等。
  - 可直接編輯，存檔生效。若是在 rails console 的狀態下修改 model 檔，執行 $ reload! 載入。

  Migration 檔: 資料庫遷移。
  - 類別繼承 ActiveRecord::Migration 的子類別。
  - 用來進行資料庫的管理，建立資料表及欄位。
  - 無法直接編輯 migration 檔。如果要變更 migration，必須執行 $ rake db:rollback 後編輯，再次執行 $ rake db:rollback 後，編輯的內容才會生效。
  ```
6. 若今天發現一個 migration 檔寫錯，請問我應該用什麼指令回復到上一個版本的 migration? 
  
  #### ANS: 
  ```ruby
  $ rake db:rollback

  如果要回到上 n 個 migration，則用: $ rake db:rollback STEP=n
  ```
7. 假設今天
  * 我要在資料庫裡產出一個叫 group 的資料表
  * 裡面包括的欄位名稱和相對應的資料型別是： 
    **name (string)**,
    **description (text)**,
    **members (integer)**
    * 請寫出一個能產生出以上需求的 migration 檔

  #### ANS: 
  ```ruby
  class AddGroupTable < ActiveRecord::Migration
    def change
      create_table :posts do |t|
        t.string :name
        t.text :description
        t.integer :members

        t.timestamps
      end
    end
  end
  ```
8. 請解釋什麼是 ActiveRecord? 

  #### ANS: 
  ```ruby
  ActiveRecord: Rails 的 Models 基礎。
  每一個 model 檔是繼承於 Active Record 的 class  
  Active Record 的衍生類別 (model檔) 例用慣例決定應該對應到哪些資料庫中的表。
  此慣例即將類別名稱轉成複數名詞。
  ```
9. 若今天需要為 ```Project``` 和 ```Issue``` 這兩個 Model 建立一對多的關係，請寫出實作上所需要的 migratiion 和 model 檔案 
  #### ANS: 
  ```ruby
  # migration files   add_projects.rb
  class AddProjects < ActiveRecord::Migration
    def change
      create_table :projects do |t|
      t.string :name            

      t.timestamps
      end
    end
  end
  ``` 
  ```ruby
  # migration files   add_issues.rb
  class AddIssues < ActiveRecord::Migration
    def change
      create_table :issues do |t|
      t.string :contents
      t.project_id            

      t.timestamps
      end
    end
  end
  ```  
  ```ruby
  #model files   project.rb
  class Project < ActiveRecord::Base
    has_many :issues  
  end
  ```
  ```ruby
  #model files  Issue.rb
 class Issue < ActiveRecord::Base
  belongs_to :project
end
  ```    
10. 若今天我有以下 model 檔：

  ```ruby
  class User < ActiveRecord::Base
    has_many :groups_users
    has_many :groups, through: :groups_users 
  end
  ```
  請寫出和這個 model 檔相關連的 model 檔，以及這些 model 檔所需要的資料庫欄位

  #### ANS: 
  ```ruby
    # migration files  add_groups_table.rb
class AddGroupsTable < ActiveRecord::Migration
  def change
    create_table :groups do |t|
      t.string :group_name

      t.timestamps
    end

    # Create a join table: post_tagship
    create_table :group_users do |t|
      t.integer :group_id
      t.integer :user_id
    end
  end
end
  ```
  ```ruby
    # migration files  add_users_table.rb
class AddUsersTable < ActiveRecord::Migration
  def change
    create_table :users do |t|
      t.string :user_name
      
      t.timestamps
    end
  end
end
  ```
  ```ruby
    # models files  group_user.rb
  class GroupUser < ActiveRecord::Base
    belongs_to :group
    belongs_to :user
  end
  ```
  ```ruby
    # models files  group.rb
  class Group < ActiveRecord::Base
    has_many :group_users
  end
  ```
11. 延續第10題，如果需要讓一個叫 "Bob" 的使用者產生一個名字叫做 "Rails is Fun" 的社團，應該如何在 rails console 裡實作出來？

  #### ANS: 
  ```ruby
  # 開啟 rails console
  $ rails c

  # 建立 "Bob" 及 "Rails Is Fun"，各自存於 user 及 group 的變數。 
  @user = User.create(user_name: "Bob")
  @group = Group.create(group_name: "Rails Is Fun")
  
  # 綁定
  @user.groups << @group

  # 檢查多對多關聯
  @user.groups
  @group.users
  ```
12. 延續第11題，請寫一段程式碼確保使用者在建立新社團時社團名不可以是空白，而且不能超過50個字
  #### ANS:
  ```ruby
  # group.rb
    class Group < ActiveRecord::Base        
      # Validation
      validates :groupname, presence: true;
      validates :groupname, length: { maximum: 50 }
    end
  ```