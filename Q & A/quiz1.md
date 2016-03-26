1. 請說明 Fixnum (整數) 和 Float (浮點數) 之間的差異
  #### Ans:
  ```
  Fixnum (整數)：記憶體中所有位元用以儲存整數
  Float (浮點數)：記憶體中部分位元用以儲存小數點以下之數值
  ``` 

2. 今天有兩個字串：
  ```ruby 
  str1 = "Hallo Welt!" 
  str2 = " NTU Rails 261!"
  ```
請說明以下兩個印出字串的方式的不同處：
  ```ruby
  puts str1 + str2
  puts "#{str1}#{str2}"
  ```
  #### Ans:
  ```  
  puts str1 + str2 => 耗記憶體
  puts "#{str1}#{str2}"  =>  字串內插，較有效率
  ``` 
3. 請解釋 array 和 hash 的不同處
  #### Ans:
  ```  
  相對於array，hash的每一筆資料有相對應的key 
  ``` 

4. 請寫一段 code 從 [1, "a string", 3.14, [1,2,3,4]] 這個陣列找出所有非字串的值
  #### Ans:
  ``` ruby  
  arr = [1, "a string", 3.14, [1,2,3,4]]

  for item in arr
      if !(item.class == String)
          puts item
      end
  end
  ```
  #### Revised
  ``` ruby
  arr = [1, "a string", 3.14, [1,2,3,4]] 
  arr.each {|x| puts "#{x}" if x.class != String}
  ```

5. 請列出兩種產出亂數的方法
  #### Ans:
  ```  
  產生出一個介於1到100之間的隨機數
  #方法一
  n = rand(1..100)
  #方法二
  n = (1..100).to_a.shuffle.first
  ``` 

6. 請把 hoemowrk1 程式碼裡的裡面的使用者輸入兩個數字的方式和輸贏的判斷式改寫成 method
  #### Ans:
 https://github.com/a9421015642/ntu_ror_266_homework/blob/master/Homework_RPS_OOP.rb
 
7. 以下這段程式碼：
  ```ruby
  ((1 > 3)&&(true == true))||(!!!false)
  ```
  會執行出什麼結果？ 請試試不用 irb 算出結果
  #### Ans:  
  ```
 true
  
  ```

8. 請問 binding.pry 是什麼？ 要如何使用它？
  #### Ans:
  ```  
  ruby 程式用以 debug 之 method/function
  使用時置於程式碼之間，程式執行時會在 binding.pry 處中斷，
  並於console中會出現"pry(main)>",
  此時輸入變數名稱，可檢視程式在中斷時，變數之內容。
  ```

9. 下面的一段程式碼，請嘗試用其他方法把 if...else...end 簡化成一行
  ```ruby
  var = 5

  if var >= 5
    return "var is greater than or equal to 5"
  else
    return "var is less than 5"
  end
  ```
  #### ANS:
  ```ruby
  var >= 5? "var is greater than or equal to 5" : "var is less than 5"
  ```