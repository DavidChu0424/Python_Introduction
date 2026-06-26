## 目錄

1. Python 基本概念
2. 變數與資料型別
3. 運算子
4. 條件判斷
5. 迴圈
6. 函式 Function
7. 參數傳遞方式
8. 關鍵字參數 Keyword Argument
9. 例外處理
10. 檔案讀寫
11. 模組與套件
12. 型別提示 Type Hint
13. 物件導向 OOP
14. `__init__` 與 `self`
15. 屬性 Attribute
16. 方法 Method
17. 封裝 Encapsulation
18. `property`
19. 繼承 Inheritance
20. 覆寫 Override
21. `super()`
22. 多型 Polymorphism
23. 組合 Composition
24. `classmethod`
25. `staticmethod`
26. `classmethod` 是否需要實例化
27. `dataclass`
28. 魔術方法 Magic Method
29. 實際範例：User 與 Report 權限設計
---

# 1. Python 基本概念

Python 是直譯式語言，程式通常由上往下執行。

```python
print("Hello Python")
```

輸出：

```text
Hello Python
```

Python 不需要在每行結尾加分號 `;`，但非常重視縮排。

```python
if True:
    print("這行在 if 裡面")
```

如果縮排錯誤，Python 會直接報錯。

---

# 2. 變數與資料型別

變數是用來存放資料的名稱。

```python
name = "David"
age = 30
is_admin = True
```

Python 不需要事先宣告型別，會根據你給的值自動判斷。

```python
x = 10        # int
x = "hello"   # str
```

雖然 Python 可以讓同一個變數改成不同型別，但實務上不建議這樣寫，因為會降低可讀性。

---

## 2.1 int：整數

```python
age = 30
```

---

## 2.2 float：小數

```python
price = 99.5
```

---

## 2.3 str：字串

```python
name = "David"
message = "Hello Python"
```

可以使用 f-string 組合字串：

```python
name = "David"
print(f"Hello {name}")
```

輸出：

```text
Hello David
```

---

## 2.4 bool：布林值

```python
is_login = True
is_admin = False
```

常用於條件判斷。

---

## 2.5 list：清單，可修改

```python
users = ["David", "Amy", "Tom"]

print(users[0])   # David

users.append("Jack")
```

list 的 index 從 0 開始。

```python
print(users[0])  # 第一個
print(users[1])  # 第二個
```

---

## 2.6 tuple：元組，不可修改

```python
point = (10, 20)

print(point[0])   # 10
```

tuple 建立後內容不能修改，適合放固定資料。

---

## 2.7 dict：字典，key-value 結構

```python
user = {
    "name": "David",
    "age": 30,
    "role": "admin"
}

print(user["name"])  # David
```

也可以新增資料：

```python
user["email"] = "david@example.com"
```

---

## 2.8 set：集合，不重複

```python
tags = {"python", "flask", "python"}

print(tags)
```

`set` 裡面不會有重複資料。

---

# 3. 運算子

## 3.1 數學運算

```python
a = 10
b = 3

print(a + b)   # 13
print(a - b)   # 7
print(a * b)   # 30
print(a / b)   # 3.333...
print(a // b)  # 3，整除
print(a % b)   # 1，餘數
print(a ** b)  # 1000，次方
```

---

## 3.2 比較運算

```python
print(10 > 5)    # True
print(10 < 5)    # False
print(10 == 5)   # False
print(10 != 5)   # True
```

---

## 3.3 邏輯運算

```python
age = 30
is_admin = True

if age >= 18 and is_admin:
    print("可以進入後台")
```

常見邏輯運算：

```text
and  而且，兩邊都要成立
or   或者，其中一邊成立即可
not  反向
```

---

# 4. 條件判斷 if

```python
score = 85

if score >= 90:
    print("A")
elif score >= 80:
    print("B")
else:
    print("C")
```

執行邏輯：

```text
if 條件成立
    執行 if 區塊
elif 條件成立
    執行 elif 區塊
else
    前面都不成立時執行
```

---

# 5. 迴圈 Loop

## 5.1 for 迴圈

適合處理固定數量或清單資料。

```python
users = ["David", "Amy", "Tom"]

for user in users:
    print(user)
```

---

## 5.2 range()

```python
for i in range(5):
    print(i)
```

輸出：

```text
0
1
2
3
4
```

`range(5)` 代表從 0 到 4，不包含 5。

---

## 5.3 while 迴圈

適合條件成立時持續執行。

```python
count = 0

while count < 3:
    print(count)
    count += 1
```

---

## 5.4 break

`break` 會直接結束迴圈。

```python
for i in range(10):
    if i == 5:
        break
    print(i)
```

---

## 5.5 continue

`continue` 會跳過本次迴圈，直接進入下一圈。

```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

---

# 6. 函式 Function

函式是把一段邏輯包起來，方便重複使用。

```python
def say_hello():
    print("Hello")
```

呼叫函式：

```python
say_hello()
```

---

## 6.1 有參數的函式

```python
def say_hello(name):
    print(f"Hello {name}")

say_hello("David")
```

輸出：

```text
Hello David
```

---

## 6.2 有回傳值的函式

```python
def add(a, b):
    return a + b

result = add(10, 20)
print(result)
```

輸出：

```text
30
```

`return` 會把結果回傳給呼叫者。

---

# 7. 參數傳遞方式

Python 函式常見參數傳遞方式有：

```text
1. 位置參數 positional argument
2. 關鍵字參數 keyword argument
3. 預設參數 default argument
4. 混合使用
```

---

## 7.1 位置參數 positional argument

位置參數要照順序。

```python
def create_user(name, age, role):
    print(name, age, role)

create_user("David", 30, "admin")
```

對應關係是：

```text
name = "David"
age = 30
role = "admin"
```

如果順序放錯：

```python
create_user(30, "admin", "David")
```

會變成：

```text
name = 30
age = "admin"
role = "David"
```

程式不一定報錯，但邏輯會錯。

---

# 8. 關鍵字參數 Keyword Argument

關鍵字參數是呼叫函式時指定參數名稱。

```python
create_user(
    name="David",
    age=30,
    role="admin"
)
```

這種寫法的好處是清楚、不容易放錯順序。

---

## 8.1 關鍵字參數可以不照順序

下面三種寫法都可以：

```python
create_user(
    name="David",
    age=30,
    role="admin"
)
```

```python
create_user(
    age=30,
    role="admin",
    name="David"
)
```

```python
create_user(
    role="admin",
    name="David",
    age=30
)
```

因為 Python 是根據左邊的參數名稱判斷，不是根據順序。

---

## 8.2 混合使用位置參數與關鍵字參數

可以這樣：

```python
create_user("David", age=30, role="admin")
```

意思是：

```text
第一個位置參數 → name
age=30
role="admin"
```

但是不能這樣：

```python
create_user(name="David", 30, "admin")
```

這會報錯：

```text
SyntaxError: positional argument follows keyword argument
```

規則是：

```text
位置參數一定要放在關鍵字參數前面
```

---

## 8.3 預設參數 default argument

```python
def create_user(name, role="user"):
    print(name, role)

create_user("David")
create_user("Amy", role="admin")
```

輸出：

```text
David user
Amy admin
```

---

# 9. 例外處理 try except

例外處理可以避免程式因為錯誤直接中斷。

```python
try:
    number = int("abc")
except ValueError:
    print("轉換失敗")
```

---

## 10.1 實際例子

```python
try:
    age = int(input("請輸入年齡："))
    print(f"你的年齡是 {age}")
except ValueError:
    print("請輸入數字")
```

---

# 10. 檔案讀寫

## 11.1 讀檔案

```python
with open("data.txt", "r", encoding="utf-8") as file:
    content = file.read()

print(content)
```

---

## 11.2 寫檔案

```python
with open("data.txt", "w", encoding="utf-8") as file:
    file.write("Hello Python")
```

---

## 11.3 追加內容

```python
with open("data.txt", "a", encoding="utf-8") as file:
    file.write("\nNew Line")
```

`with open()` 的好處是檔案使用完會自動關閉。

---

# 11. 模組與套件

## 12.1 自己建立 module

假設有一個檔案叫 `math_utils.py`：

```python
def add(a, b):
    return a + b
```

另一個 Python 檔案可以這樣使用：

```python
from math_utils import add

print(add(10, 20))
```

或：

```python
import math_utils

print(math_utils.add(10, 20))
```

---

## 12.2 pip 安裝套件

安裝 Flask：

```bash
pip install flask
```

列出目前安裝套件：

```bash
pip list
```

輸出套件清單：

```bash
pip freeze > requirements.txt
```

根據 requirements 安裝：

```bash
pip install -r requirements.txt
```

---

# 12. 型別提示 Type Hint

型別提示可以讓程式更容易閱讀，也方便 IDE 或工具檢查。

```python
def add(a: int, b: int) -> int:
    return a + b
```

這裡代表：

```text
a 是 int
b 是 int
回傳值是 int
```

另一個例子：

```python
def get_user_name(user_id: int) -> str:
    return "David"
```

型別提示不會在執行時強制限制型別，但對維護很有幫助。

---

# 13. 物件導向 OOP

OOP 全名是 Object-Oriented Programming，中文是物件導向程式設計。

核心概念：

```text
class      類別，設計圖
object     物件，根據 class 建立出來的實體
attribute  屬性，物件的資料
method     方法，物件可以做的事情
```

可以想成：

```text
class = 車子的設計圖
object = 實際做出來的一台車
attribute = 顏色、品牌、速度
method = 啟動、煞車、加速
```

---

# 14. class 與 object

```python
class User:
    pass

user1 = User()
user2 = User()
```

這裡：

```text
User 是 class
user1、user2 是 object
```

---

# 15. `__init__()` 與 `self`

`__init__()` 是建構子，會在建立物件時自動執行。

```python
class User:
    def __init__(self, name, age):
        self.name = name
        self.age = age

user = User("David", 30)

print(user.name)
print(user.age)
```

輸出：

```text
David
30
```

---

## 16.1 self 是什麼？

`self` 代表「目前這個物件自己」。

```python
class User:
    def __init__(self, name):
        self.name = name
```

意思是：

```text
把傳進來的 name
存到這個物件自己的 name 屬性裡
```

例如：

```python
user1 = User("David")
user2 = User("Amy")
```

實際上是：

```text
user1.name = "David"
user2.name = "Amy"
```

---

# 16. 屬性 Attribute

## 17.1 instance attribute：物件屬性

每個物件各自擁有。

```python
class User:
    def __init__(self, name):
        self.name = name

user1 = User("David")
user2 = User("Amy")

print(user1.name)  # David
print(user2.name)  # Amy
```

---

## 17.2 class attribute：類別屬性

所有物件共用。

```python
class User:
    default_role = "user"

    def __init__(self, name):
        self.name = name

user1 = User("David")
user2 = User("Amy")

print(user1.default_role)
print(user2.default_role)
```

輸出：

```text
user
user
```

---

# 17. 方法 Method

方法就是 class 裡面的函式。

```python
class User:
    def __init__(self, name):
        self.name = name

    def say_hello(self):
        print(f"Hello, I am {self.name}")

user = User("David")
user.say_hello()
```

輸出：

```text
Hello, I am David
```

---

# 18. 封裝 Encapsulation

封裝是把資料和操作資料的方法包在一起。

```python
class BankAccount:
    def __init__(self, owner, balance):
        self.owner = owner
        self.__balance = balance

    def deposit(self, amount):
        if amount <= 0:
            raise ValueError("金額必須大於 0")
        self.__balance += amount

    def get_balance(self):
        return self.__balance
```

使用：

```python
account = BankAccount("David", 1000)

account.deposit(500)
print(account.get_balance())
```

`__balance` 前面有兩個底線，代表不希望外部直接存取。

---

# 19. property

`property` 可以讓你像讀屬性一樣呼叫方法。

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance

    @property
    def balance(self):
        return self.__balance
```

使用：

```python
account = BankAccount(1000)

print(account.balance)
```

注意不是：

```python
account.balance()
```

而是：

```python
account.balance
```

---

# 20. 繼承 Inheritance

繼承可以讓一個 class 使用另一個 class 的功能。

```python
class Animal:
    def eat(self):
        print("正在吃東西")

class Dog(Animal):
    def bark(self):
        print("汪汪")

dog = Dog()
dog.eat()
dog.bark()
```

輸出：

```text
正在吃東西
汪汪
```

這裡：

```text
Animal 是父類別
Dog 是子類別
Dog 繼承 Animal
```

---

# 21. 覆寫 Override

子類別可以改寫父類別的方法。

```python
class Animal:
    def speak(self):
        print("動物發出聲音")

class Dog(Animal):
    def speak(self):
        print("汪汪")

class Cat(Animal):
    def speak(self):
        print("喵喵")

dog = Dog()
cat = Cat()

dog.speak()
cat.speak()
```

輸出：

```text
汪汪
喵喵
```

---

# 22. super()

`super()` 可以呼叫父類別的方法。

```python
class User:
    def __init__(self, name):
        self.name = name

class AdminUser(User):
    def __init__(self, name, permissions):
        super().__init__(name)
        self.permissions = permissions
```

使用：

```python
admin = AdminUser("David", ["read", "write", "delete"])

print(admin.name)
print(admin.permissions)
```

---

# 23. 多型 Polymorphism

不同物件可以使用同一個方法名稱，但行為不同。

```python
class Dog:
    def speak(self):
        return "汪汪"

class Cat:
    def speak(self):
        return "喵喵"

animals = [Dog(), Cat()]

for animal in animals:
    print(animal.speak())
```

輸出：

```text
汪汪
喵喵
```

重點是：

```text
同樣呼叫 speak()
不同物件有不同結果
```

---

# 24. 組合 Composition

組合是「一個物件裡面包含另一個物件」。

```python
class Engine:
    def start(self):
        print("引擎啟動")

class Car:
    def __init__(self):
        self.engine = Engine()

    def start(self):
        self.engine.start()
        print("車子啟動")

car = Car()
car.start()
```

這裡是：

```text
Car 有一個 Engine
```

不是：

```text
Car 是一個 Engine
```

實務上，組合比繼承更常用，也比較彈性。

---

# 25. classmethod

`classmethod` 是類別方法，第一個參數是 `cls`，代表 class 本身。

```python
class User:
    default_role = "user"

    @classmethod
    def get_default_role(cls):
        return cls.default_role

print(User.get_default_role())
```

輸出：

```text
user
```

這裡：

```python
cls.default_role
```

等於：

```python
User.default_role
```

---

# 26. staticmethod

`staticmethod` 不需要 `self`，也不需要 `cls`。

```python
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b

print(MathUtils.add(10, 20))
```

輸出：

```text
30
```

適合放跟 class 有關，但不需要使用物件狀態或 class 狀態的方法。

---

# 27. `classmethod` 是否需要先實例化？

不用。

例如：

```python
class User:
    default_role = "user"

    @classmethod
    def get_default_role(cls):
        return cls.default_role

print(User.get_default_role())
```

這可以直接執行，不需要：

```python
user = User()
```

因為 `@classmethod` 是用 class 本身呼叫。

---

## 28.1 instance method 需要先實例化

```python
class User:
    def say_hello(self):
        print("Hello")

user = User()
user.say_hello()
```

這裡 `say_hello()` 是 instance method，第一個參數是 `self`，所以要先建立物件。

---

## 28.2 classmethod 不需要先實例化

```python
class User:
    default_role = "user"

    @classmethod
    def get_default_role(cls):
        return cls.default_role

print(User.get_default_role())
```

`cls` 代表 class 本身，也就是 `User`。

---

## 28.3 也可以用物件呼叫 classmethod，但不建議

```python
user = User()
print(user.get_default_role())
```

雖然可以執行，但比較標準的寫法是：

```python
User.get_default_role()
```

---

## 28.4 三種 method 差異整理

```python
class User:
    default_role = "user"

    def instance_method(self):
        return "需要物件呼叫"

    @classmethod
    def class_method(cls):
        return cls.default_role

    @staticmethod
    def static_method():
        return "不需要 self，也不需要 cls"
```

呼叫方式：

```python
user = User()

user.instance_method()   # instance method，要先建立物件

User.class_method()      # classmethod，不用建立物件

User.static_method()     # staticmethod，也不用建立物件
```

整理：

```text
self  = 物件本身，要先實例化
cls   = 類別本身，不用先實例化
```

---

# 28. dataclass

如果 class 主要只是拿來存資料，可以用 `dataclass`。

```python
from dataclasses import dataclass

@dataclass
class User:
    name: str
    age: int
    role: str

user = User("David", 30, "admin")

print(user)
```

輸出：

```text
User(name='David', age=30, role='admin')
```

使用 `dataclass` 可以減少很多重複程式碼，例如不用自己寫 `__init__()`。

---

# 29. 魔術方法 Magic Method

魔術方法通常是前後都有雙底線的方法，例如：

```text
__init__
__str__
__repr__
__len__
```

---

## 30.1 `__str__`

決定 `print(object)` 時要顯示什麼。

```python
class User:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"User name is {self.name}"

user = User("David")

print(user)
```

輸出：

```text
User name is David
```

---

# 30. 實際範例：User 與 Report 權限設計

這個範例接近 Flask API 權限檢查的概念。

```python
class User:
    def __init__(self, user_id, name, role):
        self.id = user_id
        self.name = name
        self.role = role

    def is_admin(self):
        return self.role == "admin"


class Report:
    def __init__(self, report_id, owner_id, title):
        self.id = report_id
        self.owner_id = owner_id
        self.title = title

    def can_view(self, user):
        return self.owner_id == user.id or user.is_admin()
```

使用：

```python
user = User(1, "David", "user")
admin = User(2, "Admin", "admin")

report = Report(100, owner_id=1, title="Server Test Report")

print(report.can_view(user))   # True
print(report.can_view(admin))  # True
```

如果是其他使用者：

```python
other_user = User(3, "Tom", "user")

print(report.can_view(other_user))  # False
```

這裡的設計概念是：

```text
User 負責使用者資料與角色判斷
Report 負責報告資料與可不可查看
```

不要把所有邏輯都塞在同一個 function 裡。

---

# 31. Flask API 權限檢查範例

```python
@app.route("/api/report/<int:report_id>")
@login_required
def get_report(report_id):
    report = Report.query.filter_by(
        id=report_id,
        owner_id=current_user.id
    ).first_or_404()

    return jsonify(report.to_dict())
```

這段有兩層檢查：

```python
@login_required
```

代表：

```text
檢查使用者有沒有登入
```

這段：

```python
owner_id=current_user.id
```

代表：

```text
檢查這筆 report 是不是屬於目前登入者
```

所以完整邏輯是：

```text
1. 使用者必須先登入
2. 只能查詢 owner_id 等於 current_user.id 的 report
3. 如果 report_id 存在但不是你的，也會找不到
```

這可以防止 IDOR，也就是使用者猜別人的 ID 來看資料。

---

# 32. Python 寫程式建議

## 33.1 變數名稱要清楚

不好：

```python
x = "David"
y = 30
```

比較好：

```python
user_name = "David"
user_age = 30
```

---

## 33.2 函式只做一件事

不好：

```python
def process():
    # 登入
    # 查資料
    # 寫檔
    # 寄信
    pass
```

比較好：

```python
def login_user():
    pass

def get_report():
    pass

def write_log():
    pass

def send_email():
    pass
```

---

## 33.3 class 不要亂用

不是所有東西都要寫成 class。

適合用 function：

```python
def add(a, b):
    return a + b
```

適合用 class：

```python
class User:
    def __init__(self, name, role):
        self.name = name
        self.role = role

    def is_admin(self):
        return self.role == "admin"
```

判斷原則：

```text
只有單純動作 → function
有資料狀態 + 行為 → class
```

---

# 33. 學習順序建議

建議照這個順序學：

```text
1. 變數
2. 資料型別
3. if 判斷
4. for / while 迴圈
5. list / dict
6. function
7. 位置參數 / 關鍵字參數
8. try except
9. module / import
10. file read/write
11. class / object
12. __init__ / self
13. attribute / method
14. class attribute / instance attribute
15. classmethod / staticmethod
16. inheritance
17. composition
18. dataclass / property
```

---

# 34. 一句話總結

Python 基礎是在學：

```text
怎麼控制資料與流程
```

物件導向是在學：

```text
怎麼把資料與行為整理成可維護的結構
```

最核心差異：

```python
# function 寫法
def can_view_report(user_id, report_owner_id):
    return user_id == report_owner_id
```

物件導向寫法：

```python
class Report:
    def __init__(self, owner_id):
        self.owner_id = owner_id

    def can_view(self, user):
        return self.owner_id == user.id
```

物件導向不是比較高級，而是當程式變大時，讓資料、邏輯、權限、狀態比較好管理。

---

# 35. 快速總表

| 主題 | 重點 |
|---|---|
| 變數 | 存資料的名稱 |
| list | 有順序、可修改 |
| tuple | 有順序、不可修改 |
| dict | key-value 結構 |
| function | 重複使用邏輯 |
| positional argument | 根據順序傳參數 |
| keyword argument | 根據參數名稱傳參數 |
| class | 類別，設計圖 |
| object | 物件，class 建立出來的實體 |
| self | 目前這個物件 |
| cls | 目前這個 class |
| instance method | 需要物件呼叫 |
| classmethod | 可直接用 class 呼叫 |
| staticmethod | 不需要 self / cls |
| inheritance | 繼承父類別功能 |
| composition | 一個物件包含另一個物件 |
| dataclass | 快速建立資料型 class |

---

# 36. 常見錯誤整理

## 37.1 忘記縮排

錯誤：

```python
if True:
print("Hello")
```

正確：

```python
if True:
    print("Hello")
```

---

## 37.2 位置參數放在關鍵字參數後面

錯誤：

```python
create_user(name="David", 30, "admin")
```

正確：

```python
create_user("David", age=30, role="admin")
```

---

## 37.3 instance method 沒有建立物件就呼叫

錯誤：

```python
class User:
    def say_hello(self):
        print("Hello")

User.say_hello()
```

正確：

```python
user = User()
user.say_hello()
```

---

## 37.4 classmethod 誤以為要建立物件

其實不用：

```python
class User:
    default_role = "user"

    @classmethod
    def get_default_role(cls):
        return cls.default_role

print(User.get_default_role())
```

---

# 37. 建議練習題

## 練習 1：基本函式

寫一個 `add(a, b)`，回傳兩個數字相加結果。

```python
def add(a, b):
    return a + b

print(add(10, 20))
```

---

## 練習 2：使用關鍵字參數

```python
def create_user(name, age, role):
    print(f"name={name}, age={age}, role={role}")

create_user(
    role="admin",
    name="David",
    age=30
)
```

---

## 練習 3：建立 User class

```python
class User:
    def __init__(self, name, role):
        self.name = name
        self.role = role

    def is_admin(self):
        return self.role == "admin"

user = User("David", "admin")

print(user.name)
print(user.is_admin())
```

---

## 練習 4：建立 Report 權限檢查

```python
class User:
    def __init__(self, user_id, role):
        self.id = user_id
        self.role = role

    def is_admin(self):
        return self.role == "admin"


class Report:
    def __init__(self, owner_id):
        self.owner_id = owner_id

    def can_view(self, user):
        return self.owner_id == user.id or user.is_admin()


user = User(1, "user")
admin = User(2, "admin")
report = Report(owner_id=1)

print(report.can_view(user))   # True
print(report.can_view(admin))  # True
```

---

## 練習 5：比較 instance method、classmethod、staticmethod

```python
class User:
    default_role = "user"

    def __init__(self, name):
        self.name = name

    def instance_method(self):
        return self.name

    @classmethod
    def class_method(cls):
        return cls.default_role

    @staticmethod
    def static_method():
        return "static method"


user = User("David")

print(user.instance_method())
print(User.class_method())
print(User.static_method())
```

---