---
theme: dracula
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
title: Layered Design for Rails
mdc: true
css: windicss
---

<div class="flex justify-center items-center ">
<div class="bg-white rounded-lg shadow-lg min-w-350px">
        <div class="flex justify-center p-4">
            <img src="/photo/DALL·E 2023-12-06 11.07.58 - A comic-style depiction of a young Asian male software engineer working hard, showing signs of fatigue and stress in a humorous way. The engineer is s.png" alt="Profile" class="rounded-full border-4 border-gray-250 h-32 w-32">
        </div>
        <div class="text-center">
          <p class="text-2xl font-semibold text-black">Ken</p>
          <a href="https://github.com/Cheng-Kai-Ming" target="_blank" alt="GitHub" title="Open in GitHub"
            class="group text-xl border-none">
              <carbon-logo-github class="text-black hover:scale-120 transition-transform" />
          </a>
        </div>
        <div class="px-4 py-2">
            <p class="text-sm text-gray-600">
                Layered Design for Rails
                <br>
                Service / Form / Query
            </p>
        </div>
        <div class="flex justify-around py-4 bg-gray-100" @click="$slidev.nav.next" hover="bg-black">
            A software engineer with a bit of front-end and back-end knowledge. 😉
        </div>
        <div class="text-center py-2 bg-gray-200">
            <span class="text-sm text-gray-600">Talk Date: 2023-12-12</span>
        </div>
    </div>
    </div>
---

<div grid="~ cols-2 gap-4">
  <div class="content">
    <h3>適合誰聽？</h3>
    <ul class="custom-list">
      <li>懂MVC</li>
      <li>懂物件導向</li>
    </ul>
    <h3>吃緊的地方</h3>
    <ul class="custom-list">
      <li>會用到一些Meta Programming</li>
    </ul>
      <img src="/photo/wired_cat.jpeg" alt="Description" class="object-fill">
  </div>

  <div class="content text-white p-4">
    <h3 class="text-xl mb-4">流程</h3>
    <ul class="custom-list">
      <li class="process-step">Rails的旅程</li>
      <li class="process-step">良好抽象層的特徵</li>
      <li class="process-step">Service Object -> Layer</li>
      <li class="process-step">DDD</li>
      <li class="process-step">Form Object -> Layer</li>
      <li class="process-step">Query Scope -> Layer</li>
    </ul>
  </div>

</div>

<style>
.content {
  font-family: Arial, sans-serif;
  line-height: 1.6;
}

.content h2, .content h3 {
  margin-bottom: 20px; /* 增加標題下方的間距 */
}

.custom-list {
  list-style-type: none; /* 移除預設的列表符號 */
  padding-left: 0;
  margin-bottom: 30px; /* 增加列表下方的間距 */
}

.custom-list li::before {
  content: '•'; /* 自定義符號 */
  color: #007bff; /* 符號顏色 */
  font-weight: bold; /* 符號粗體 */
  display: inline-block; 
  width: 1em; /* 確保對齊 */
  margin-left: -1em; /* 向左調整以對齊文字 */
}

.process-step {
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
  position: relative;
}

.process-step::after {
  color: #fff;
  position: absolute;
  right: -20px;
  top: 50%;
  transform: translateY(-50%);
}

.process-step:last-child::after {
  content: '';
}

.content {
  font-family: Arial, sans-serif;
}

.custom-list {
  list-style-type: none;
  padding-left: 0;
}


</style>

---

# Ruby & Rails

<div>
<img src="/photo/CH1-1.png" alt="Description" class="object-contain">
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---

# APP的設計

每一個請求可以思考成一個包裹

<div>
<img src="/photo/conveyor.png" alt="Description" class="object-contain">
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

<h1>良好抽象層的特質</h1>
<div class="text-white text-lg space-y-4">
  <p><span class="font-bold">1. 單一職責：</span><br>每層的指責可以廣，但不可以重疊</p>
  <p><span class="font-bold">2. 平行的層與層之間，不互相耦合：</span><br>層與層之間只會單一方向（由上往下）→ 輸送帶不會逆推</p>
  <p><span class="font-bold">3. 介面與實作分離：</span><br>抽象層應該隱藏其內部實現的細節，以確保高度的封裝和隔離，並降低系統中不同部分之間的相依性。</p>
  <p><span class="font-bold">4. 獨立測試</span></p>
</div>

<style>

.text-white {
  color: #fff; /* 白色文本 */
}

.text-lg {
  font-size: 1.125rem; /* 較大的字體大小 */
}

.space-y-4 {
  margin-top: 5rem; /* 每個元素間的垂直間距 */
}

.font-bold {
  font-weight: bold; /* 粗體字體 */
  padding-bottom: 3px;
}

h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

</style>

---

# Service Object

<div class="text-white space-y-4 p-4">
  <h2 class="font-bold">普遍定義:</h2>
  <p>表單一業務操作的對象，位於控制器（Controllers）和模型（Models）之間。這意味著Service Object用於封裝複雜的業務邏輯，而不是將這些邏輯直接放在控制器或模型中。</p>

  <h3 class="font-bold">更嚴格的定義:</h3>
  <p>在一些實踐中，開發者會將所有的Service Objects設計為可調用對象（Callable Objects）。這意味著這些對象應該響應 .call 方法。這種做法使得Service Objects的使用更為統一和一致。</p>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

.font-bold {
  font-weight: bold; /* 粗體字體 */
  padding-bottom: 3px;
}

.text-white {
  color: #fff;
}

.text-lg {
  font-size: 1.125rem;
  line-height: 1.6;
}

.space-y-4 {
  margin-top: 1rem;
}

.p-4 {
  padding: 1rem;
}

.text-rose-500 {
  color: #f43f5e;
}

.text-yellow-500 {
  color: #fbbf24;
}

.text-green-500 {
  color: #10b981;
}

.text-blue-500 {
  color: #3b82f6;
}

.text-xl {
  font-size: 1.25rem;
}

.mb-2 {
  margin-bottom: 0.5rem;
}

</style>

---

# 放Model還是Service ? - Model（領域層）

<div class="text-white text-lg px-4 py-2">
  <h3 class="font-bold mb-2">基本的數據操作:</h3>
  <p class="mb-4">對數據的基本操作，如創建、更新、刪除、查詢等，通常應該放在Model層。</p>
  
  <h3 class="font-bold mb-2">簡單的業務規則:</h3>
  <p class="mb-4">與單個實體或一小組緊密相關的業務邏輯，例如數據驗證、計算字段（例如計算年齡或總計）、狀態機管理等，適合放在Model中。</p>
  
  <h3 class="font-bold mb-2">領域完整性和規則:</h3>
  <p>維護數據一致性和完整性的規則應該是模型的一部分，以確保數據的正確性無論是透過哪種途徑被存取或修改。</p>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

.text-white {
  color: #fff; /* 白色文字 */
}

.text-lg {
  font-size: 1.125rem; /* 較大的字體大小 */
}

.px-4 {
  padding-left: 1rem; /* 左右內間距 */
  padding-right: 1rem;
}

.py-2 {
  padding-top: 0.5rem; /* 上下內間距 */
  padding-bottom: 0.5rem;
}

.mb-2 {
  margin-bottom: 0.5rem; /* 元素下方間距 */
}

.mb-4 {
  margin-bottom: 1rem; /* 元素下方間距 */
}

.text-rose-500 {
  color: #f43f5e; /* 亮粉紅色 */
}

.font-bold {
  font-weight: bold; /* 粗體字 */
}

</style>

---

# 類Functional Design（功能設計）

```ruby
class Order < ApplicationRecord
  # 基本關聯
  belongs_to :user
  has_many :order_items

  # 數據驗證
  validates :total_price, numericality: { greater_than: 0 }

  # 計算總價
  def calculate_total_price
    self.total_price = order_items.sum(&:price)
  end

  # 更新庫存
  def update_inventory
    order_items.each do |item|
      item.product.decrement!(:stock, item.quantity)
    end
  end
end
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# 放Model還是Service ? - Service（應用層）

<div class="text-white text-lg px-4 py-2">
  <h3 class="font-bold mb-2">複雜的業務流程：</h3>
  <p class="mb-4">當您有跨越多個模型或涉及複雜邏輯的流程時，使用Service Objects更合適。這有助於保持模型的簡潔性，並降低各個模型間的耦合。</p>
  
  <h3 class="font-bold mb-2">跨域操作：</h3>
  <p class="mb-4">如果某個業務邏輯在應用程序的多個地方使用，將其封裝在Service Object中可以促進代碼的重用和更好的組織結構。</p>

  <h3 class="font-bold mb-2">重用和組織：</h3>
  <p>與後台處理或定時任務相關的複雜邏輯適合放在Service Objects中。</p>
  
  <h3 class="font-bold mb-2">背景任務和排程作業：</h3>
  <p>與後台處理或定時任務相關的複雜邏輯適合放在Service Objects中。</p>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# 類Procedural Design（過程式設計）

```ruby
class OrderProcessingService
  def initialize(order)
    @order = order
  end

  def call
    return false unless @order.valid?

    ActiveRecord::Base.transaction do
      @order.calculate_total_price
      @order.save!
      @order.update_inventory
      notify_customer
    end

    true
  rescue ActiveRecord::RecordInvalid
    false
  end

  private

  def notify_customer
    # 發送訂單確認郵件給客戶
  end
end
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Service Layer

<div class="relative-container">
<div v-click="[1, 2]" class="absolute-panel">
<h3 class="font-bold mb-2">Perform & call</h3>

<div  class="px-4 py-2">
```ruby
def perform
  process1
  process2
  process3
end
```
</div>

<div class="px-4 py-2">
```ruby
def call
  process1
  process2
  process3
end
```
</div>

</div>

<div v-click="[3, 4]" class="absolute-panel">
<h3 class="font-bold mb-2">params在controller or service處理？</h3>


<div class="px-4 py-2">
```ruby
class OrderProcessingService
  def initialize(user, order, deliver_time)
    @user = user
    @order = order
    @deliver_time = deliver_time
  end
end

OrderProcessingService.new(params)

# or

OrderProcessingService.new(
  user: user,
  oerdr: order,
  deliver_time: deliver_time
)
```
</div>
</div>

<div v-click="[5, 6]" class="absolute-panel">
<h3 class="font-bold mb-2">Service該放在controller or model ?</h3>


<div class="px-4 py-2">
```ruby
class Order
  def update_order
    OrderProcessingService.new(
      user: user,
      oerdr: order,
      deliver_time: deliver_time
    ).call
  end
end

class OrderController
  def update_order
    OrderProcessingService.new(
      user: user,
      oerdr: order,
      deliver_time: deliver_time
    ).call
  end
end
```

presenter -> application -> domain
</div>
</div>


</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

.text-white {
  color: #fff; /* 白色文字 */
}

.text-lg {
  font-size: 1.125rem; /* 較大的字體大小 */
}

.px-4 {
  padding-left: 1rem; /* 左右內間距 */
  padding-right: 1rem;
}

.py-2 {
  padding-top: 0.5rem; /* 上下內間距 */
  padding-bottom: 0.5rem;
}

.mb-2 {
  margin-bottom: 0.5rem; /* 元素下方間距 */
}

.mb-4 {
  margin-bottom: 1rem; /* 元素下方間距 */
}

.text-rose-500 {
  color: #f43f5e; /* 亮粉紅色 */
}

.font-bold {
  font-weight: bold; /* 粗體字 */
}

.relative-container {
  position: relative; /* 父容器使用相對定位 */
}

.absolute-panel {
  position: absolute; /* 子面板使用絕對定位 */
  top: 0; /* 起始位置設定為頂部 */
  left: 0; /* 起始位置設定為左側 */
  width: 100%;
}


</style>

---

# Service Layer

[dry-monads](https://github.com/dry-rb/dry-monads)

```ruby {all} {maxHeight:'400px', lines:true, startLine:1}
class ApplicationService
  extend Dry::Initializer

  def self.call(...) = new(...).call
end

class OrderProcessingService < ApplicationService
  params :order

  def call
    return false unless order.valid?

    ActiveRecord::Base.transaction do
      order.calculate_total_price
      order.save!
      order.update_inventory
      notify_customer
    end

    true
  rescue ActiveRecord::RecordInvalid
    false
  end

  private

  def notify_customer
    # 發送訂單確認郵件給客戶
  end
end
```


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>
---

# 層式架構

<div class="text-white text-lg px-4 py-2">
  <h3 class="font-bold mb-2">1. 每一層都有特定的職責和功能</h3>
  <h3 class="font-bold mb-2">2. 層通常按照特定的邏輯順序堆疊，從上到下，形成一個體系結構</h3>
  <h3 class="font-bold mb-2">3. 數據通常在這些層之間單向流動，從上面的層到下面的層</h3>
  <h3 class="font-bold mb-2">4. 每一層都有特定的功能，而且應該維持一定的獨立性，以便它們可以獨立開發、測試和維護</h3>
  <h3 class="font-bold mb-2">5. 這種架構的一個關鍵特點是每一層不依賴於它上面的層，這意味著每個層都應該只依賴於更底層的層，而不依賴於更高層次的層</h3>
  <h3 class="font-bold mb-2">6. 分層架構有助於提高代碼的可維護性、可擴展性和可讀性，並促使良好的設計實踐。這在大型和複雜的應用程序中尤為重要</h3>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

.text-white {
  color: #fff; /* 白色文字 */
}

.text-lg {
  font-size: 1.125rem; /* 較大的字體大小 */
}

.px-4 {
  padding-left: 1rem; /* 左右內間距 */
  padding-right: 1rem;
}

.py-2 {
  padding-top: 0.5rem; /* 上下內間距 */
  padding-bottom: 0.5rem;
}

.mb-2 {
  margin-bottom: 1.5rem; /* 元素下方間距 */
}

.font-bold {
  font-weight: normal; /* 粗體字 */
}

</style>

---

# DDD
<div class="flex-container">
  <div grid="~ cols-2 gap-4 p-10">
    <div class="content">
      <img src="/photo/rails-layer.png" alt="Description" class="object-scale-down">
    </div>
    <div class="content">
      <ul class="custom-list">
        <li class="process-step">處理使用者的互動並呈現資訊</li>
        <li class="process-step">負責組織領域對象，以滿足所需的使用案例</li>
        <li class="process-step">描述業務實體、業務規則和不變性的定義，並負責維護應用程序的狀態</li>
        <li class="process-step">負責處理與數據庫、外部服務、框架等的交互</li>
      </ul>
    </div>
  </div>
</div>

<style>
.flex-container {
  display: flex;
  justify-content: center; /* 水平居中 */
  align-items: center; /* 垂直居中 */
  height: 70%; /* 容器高度設為100% */
}

h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

.relative-container {
  position: relative; /* 父容器使用相對定位 */
}

.absolute-panel {
  position: absolute; /* 子面板使用絕對定位 */
  top: 0; /* 起始位置設定為頂部 */
  left: 0; /* 起始位置設定為左側 */
  width: 100%;
}

.text-white {
  color: #fff; /* 白色文字 */
}

.text-lg {
  font-size: 1.125rem; /* 較大的字體大小 */
}

.px-4 {
  padding-left: 1rem; /* 左右內間距 */
  padding-right: 1rem;
}

.py-2 {
  padding-top: 0.5rem; /* 上下內間距 */
  padding-bottom: 0.5rem;
}

.mb-2 {
  margin-bottom: 1.5rem; /* 元素下方間距 */
}

.font-bold {
  font-weight: normal; /* 粗體字 */
}

.custom-list {
  list-style-type: none; /* 移除預設的列表符號 */
  padding-left: 0;
  margin-bottom: 20px; /* 增加列表下方的間距 */
}

.custom-list li::before {
  color: #007bff; /* 符號顏色 */
  font-weight: bold; /* 符號粗體 */
  display: inline-block; 
  width: 1em; /* 確保對齊 */
  margin-left: -1em; /* 向左調整以對齊文字 */
}

.process-step {
  padding: 5px;
  margin-bottom: 15px;
  border-radius: 5px;
  position: relative;
}

.process-step::after {
  color: #fff;
  position: absolute;
  right: -20px;
  top: 50%;
  transform: translateY(-50%);
}

.process-step:last-child::after {
  content: '';
}

</style>
---

# Form Object

<div class="code-block mb-6">
```ruby {all} {maxHeight:'200px', lines:true, startLine:1}
class RegistrationsController < ApplicationController
  def create
    @user = User.new(params.require(:user).permit(:email, :name))
    @user.confirmed_at = Time.current
    @user.should_send_welcome_email = true

    if @user.save
      redirect_to root_path
    else
      render :new, status: :unprocessable_entity
    end
  end
end
```
</div>

<div class="code-block">
```ruby {all} {maxHeight:'200px', lines:true, startLine:1}
class User < ApplicationRecord
  validates :email, presence: true, uniqueness: true
  validates :name, presence: true, if: :confirmed?
  
  attribute :should_send_invitation, :boolean
  attribute :should_send_welcome_email, :boolean

  after_create_commit :send_invitation, if: :should_send_invitation
  after_create_commit :send_welcome_email, if: :should_send_welcome_email

  
  def send_invitation
    UserMailer.invite(self).deliver_later
  end

  def send_welcome_email
    UserMailer.welcome(self).deliver_later
  end
end
```
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>


---

# Form Object

<div class="flex justify-center items-center h-full">
  <img src="/photo/model-pre.png" alt="Description" class="object-fill">
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Form Object基本要素

```ruby {all|3-7|19-21|9-15|23-28|all} {maxHeight:'400px', lines:true, startLine:1}
class UserInvitationForm 
  attr_reader :user, :send_copy, :sender
  def initialize(params, send_copy: false, sender: nil)
    @user = User.new(params)
    @send_copy = send_copy.in?(%w[1 t true])
    @sender = sender
  end

  def save
    validate!
    return false if user.errors.any?

    user.save!
    deliver_notifications!
  end

  private

  def validate!
    user.errors.add(:email, :blank) if user.email.blank?
  end

  def deliver_notifications!
    UserMailer.invite(user).deliver_later
    if send_copy
      UserMailer.invite_copy(sender, user).deliver_later
    end
  end
end
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Form Layer

<div class="flex justify-center items-center">
  <img src="/photo/form-layer.png" alt="Description" class="object-contain w-md h-auto">
</div>

<style>

.w-md {
  width: 45rem;
}

h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# 預備知識

<div class="code-block mb-6">
```ruby {all} {maxHeight:'200px', lines:true, startLine:1}
def example_with_yield
  puts "在yield之前"
  yield
  puts "在yield之後"
end

example_with_yield do
  puts "這是傳入的區塊"
end

#在yield之前
#這是傳入的區塊
#在yield之後
```
</div>

<div class="code-block">
```ruby {all} {maxHeight:'200px', lines:true, startLine:1}
def example_with_block(&block)
  puts "在block.call之前"
  block.call
  puts "在block.call之後"
end

example_with_block do
  puts "這是傳入的區塊"
end

#在block.call之前
#這是傳入的區塊
#在block.call之後
```
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# 簡單的例子

```ruby {all} {maxHeight:'450px', lines:true, startLine:1}
class InvitationForm < ApplicationForm
  ＃．．． 
  after_commit :deliver_invitation 
  after_commit :deliver_invitation_copy, if: :send_copy 

  validate :email, presence: true
  
  private 
  
  def submit! 
    @user = User.new(email:)
    user.save! 
  end

  def deliver invitation 
    UserMailer.invite(user).deliver_later 
  end 

  def deliver_invitation_copy
    UserMailer.invite_copy(sender, user).deli ver_later if sender
  end
end
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# 實際應用

```ruby {monaco-diff}
def create
  @tour = @school.tour_registrations.new(tour_params)
  @student = params[:page_student_id] ? @school.students.find(params[:page_student_id]) : @tour.students.first

  if params[:student_id]
    @student = @school.students.find(params[:student_id])
    @tour.student_ids   = @student.id
    @tour.parent_id     = @student.parent_ids.first
    @tour.program_id    = @student.program.try(:id)
    @tour.notify_family = params[:notify_family] == 'true'
  end

  students_count = tour_params[:student_ids] ? tour_params[:student_ids].count(&:present?) : 1
  @tour.attendees_count = [tour_params[:attendees_count].to_i, students_count].max
  @tour.creator = current_user
  @tour.confirmed_by = current_user
  @tour.skip_date_validation = true
  @tour.skip_student_availability_validation = true
  @tour.skip_warnings = tour_params[:skip_warnings] == '1'
  @tour_campuses = @school.campuses.available_for_tours.available_for_programme(@tour.program)

  if @tour.valid?
    if @tour.skip_warnings?
      @tour.save
      generate_custom_virtual_event
      render
    else
      @validation_service = TourRegistrationValidationService.new(@tour)

      @submit_button_title = submit_button_title(@tour)

      if @validation_service.valid?
        @tour.save
        generate_custom_virtual_event
        render
      else
        event_html_id = event_html_id(@tour)
        render_custom_url = @tour.open_day.virtual? && @tour.virtual_event_provider == VirtualEventProvider::OTHER
        render 'warnings',
                locals: { event_html_id: event_html_id, render_custom_url: render_custom_url },
                status: :unprocessable_entity
      end
    end
  else
    @error_msg = (@tour.errors.full_messages[0] == 'Date This field is required.') ? 'Date is required.' : @tour.errors.full_messages
    render "create_failed", status: :unprocessable_entity
  end
end
~~~
def create
  form = FormObject::AdminTourRegistration.new(tour_registration_params)

  result = form.save

  if result[:saved]
    @tour = result[:tour]
    @student = form.student
    @tour_campuses = form.tour_campuses
    render
  else
    @tour = result[:tour]
    @submit_button_title = submit_button_title(@tour)
    @student = form.student
    @tour_campuses = form.tour_campuses
    @validation_service = result[:validation_service]

    if result[:warning]
      event_html_id = event_html_id(@tour)
      render_custom_url = @tour.open_day.virtual? && @tour.virtual_event_provider == VirtualEventProvider::OTHER
      render 'warnings', locals: { event_html_id: event_html_id, render_custom_url: render_custom_url }, status: :unprocessable_entity
    else
      @error_msg = form.errors.full_messages.first
      render "create_failed", status: :unprocessable_entity
    end
  end
end
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# 抽象層
```ruby {all} {maxHeight:'450px', lines:true, startLine:1}
class FormObject::ApplicationForm
  include ActiveModel::API
  include ActiveModel::Attributes

  define_callbacks :save, only: :after
  define_callbacks :commit, only: :after

  class << self
    def after_save(...)
      set_callback(:save, :after, ...)
    end

    def after_commit(...)
      set_callback(:commit, :after, ...)
    end
  end

  def save
    return false unless valid?

    with_transaction do 
      AfterCommitEverywhere.after_commit { run_callbacks :commit }
      run_callbacks(:save) { submit! }
    end
  end

  def merge_errors!(other)
    other.errors.each do |e|
      errors.add(e.attribute, e.type, message: e.message)
    end
  end

  private

  def with_transaction(&)
    ApplicationRecord.transaction(&)
  end

  def submit!
    raise NotImplementedError
  end
end
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Form Object

<div class="flex space-x-6 mt-5">
<div class="w-1/2">
```ruby {all|5-16|21-24|all} {maxHeight:'450px', lines:true, startLine:1}
class FormObject::ApplicationForm
  include ActiveModel::API
  include ActiveModel::Attributes

  define_callbacks :save, only: :after
  define_callbacks :commit, only: :after

  class << self
    def after_save(...)
      set_callback(:save, :after, ...)
    end

    def after_commit(...)
      set_callback(:commit, :after, ...)
    end
  end

  def save
    return false unless valid?

    with_transaction do 
      AfterCommitEverywhere.after_commit { run_callbacks :commit }
      run_callbacks(:save) { submit! }
    end
  end

  def merge_errors!(other)
    other.errors.each do |e|
      errors.add(e.attribute, e.type, message: e.message)
    end
  end

  private

  def with_transaction(&)
    ApplicationRecord.transaction(&)
  end

  def submit!
    raise NotImplementedError
  end
end
```
</div>
<div class="w-1/2">
```ruby {all|2-7|9|75-82|25-48|84-97|all} {maxHeight:'450px', lines:true, startLine:1}
class FormObject::AdminTourRegistration < FormObject::ApplicationForm
  attribute :school
  attribute :tour_params
  attribute :page_student_id
  attribute :student_id
  attribute :notify_family
  attribute :current_user

  after_save :generate_custom_virtual_event, if: -> { @tour.skip_warnings? }

  def tour_campuses
    @tour_campuses ||= school.campuses.available_for_tours.available_for_programme(@tour.program)
  end

  def tour
    @tour
  end

  def student
    @student
  end

  private

  def submit!
    @tour = school.tour_registrations.new(tour_params)
    set_student
    set_additional_attributes

    if @tour.valid?
      if @tour.skip_warnings?
        @tour.save!
        return { saved: true, tour: @tour }
      else
        @validation_service = TourRegistrationValidationService.new(@tour)

        if @validation_service.valid?
          @tour.save!
          return { saved: true, tour: @tour, validation_service: @validation_service }
        else
          return { saved: false, tour: @tour, validation_service: @validation_service, warning: true }
        end
      end
    else
      merge_errors!(@tour)
      return { saved: false, tour: @tour, validation_service: nil }
    end
  end

  def set_student
    student_id = student_id || page_student_id || @tour.students.first&.id
    @student = school.students.find(student_id) if student_id
  end

  def set_additional_attributes
    if @student
      @tour.student_ids = [@student.id]
      @tour.parent_id = @student.parent_ids.first
      @tour.program_id = @student.program.try(:id)
      @tour.notify_family = notify_family == 'true'
    end
    @tour.attendees_count = calculate_attendees_count
    @tour.creator = current_user
    @tour.confirmed_by = current_user
    @tour.skip_date_validation = true
    @tour.skip_student_availability_validation = true
    @tour.skip_warnings = tour_params[:skip_warnings] == '1'
  end

  def calculate_attendees_count
    students_count = tour_params[:student_ids]&.count(&:present?) || 1
    [tour_params[:attendees_count].to_i, students_count].max
  end

  def validate_and_save_or_render
    if @tour.valid?
      @tour.save!
      true
    else
      false
    end
  end

  def generate_custom_virtual_event
    return unless @tour.virtual?
    return unless @tour.open_day.repeatable?

    if @tour.open_day.virtual_event_provider == VirtualEventProvider::ZOOM
      return API::Zoom::CheckTourRegistrationWorker.perform_async(@tour.id)
    end

    if (custom_url = params.dig(:virtual_event_url_attributes, :url)).present?
      VirtualEventUrl
        .find_or_create_by(virtual_event: @tour)
        .update url: custom_url
    end
  end
end
```
</div>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Form Object - Simple

<div class="flex space-x-6 mt-5">
<div class="w-1/2">
```ruby {all|5-16|21-24|all} {maxHeight:'450px', lines:true, startLine:1}
class FormObject::ApplicationForm
  include ActiveModel::API
  include ActiveModel::Attributes

  define_callbacks :save, only: :after
  define_callbacks :commit, only: :after

  class << self
    def after_save(...)
      set_callback(:save, :after, ...)
    end

    def after_commit(...)
      set_callback(:commit, :after, ...)
    end
  end

  def save
    return false unless valid?

    with_transaction do 
      AfterCommitEverywhere.after_commit { run_callbacks :commit }
      run_callbacks(:save) { submit! }
    end
  end

  def merge_errors!(other)
    other.errors.each do |e|
      errors.add(e.attribute, e.type, message: e.message)
    end
  end

  private

  def with_transaction(&)
    ApplicationRecord.transaction(&)
  end

  def submit!
    raise NotImplementedError
  end
end
```
</div>
<div class="w-1/2">
```ruby {all} {maxHeight:'450px', lines:true, startLine:1}
class InvitationForm < ApplicationForm
  ＃．．． 
  after_commit :deliver_invitation 
  after_commit :deliver_invitation_copy, if: :send_copy 

  validate :email, presence: true
  
  private 
  
  def submit! 
    @user = User.new(email:)
    user.save! 
  end

  def deliver invitation 
    UserMailer.invite(user).deliver_later 
  end 

  def deliver_invitation_copy
    UserMailer.invite_copy(sender, user).deli ver_later if sender
  end
end
```
</div>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Query Object

<div class="flex space-x-6 mt-5">
<div class="w-1/2">
```ruby {all} {maxHeight:'400px', lines:true, startLine:1}
class User < ApplicationRecord 
  def self.with_bookmarked_posts(period = :previous_week)
    bookmarked_posts = 
      Post.kept.public_send(period) 
          .where.associated(:bookmarks)
          .select(:user_id).distinct
       with(bookmarked_posts:). joins (:bookmarked_posts
  end
end

User.with_bookmarked_posts 
```
</div>
<div class="w-1/2">
```ruby {all} {maxHeight:'400px', lines:true, startLine:1}
class User < ApplicationRecord
  scope :with_bookmarked_posts, ->(period = :previous_week) {
    bookmarked_posts = Post.kept.public_send(period)
                           .where.associated(:bookmarks)
                           .select(:user_id).distinct

    joins(:bookmarked_posts).merge(bookmarked_posts)
  }
end

```
</div>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Query Layer

<div class="flex justify-center items-center">
  <img src="/photo/form-layer.png" alt="Description" class="object-contain w-md h-auto">
</div>

<style>

.w-md {
  width: 45rem;
}

h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>


---

# Query 重構

```ruby {monaco-diff}
scope :with_any_tags, ->(tag_titles) {
  where(id: StudentsTag.joins(:tag).where(tags: { title: tag_titles }).select(:student_id))
}

scope :with_all_tags, ->(tag_titles) {
  where(id: StudentsTag
              .select(:student_id)
              .joins(:tag)
              .where(tags: { title: tag_titles })
              .group(:student_id)
              .having('COUNT(tag_id) = ?', tag_titles.count))
}
~~~
scope :with_any_tags, Queries::Student::WithAnyTagsQuery[self]

scope :with_all_tags, Queries::Student::StudentWithAllTagsQuery[self]
```


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Query Layer Abstraction

<div class="flex space-x-6 mt-5">
<div class="w-1/2">

```ruby {all} {maxHeight:'400px', lines:true, startLine:1}
class Queries::ApplicationQuery
  class << self
    attr_writer :query_model_name
    def query_model_name
      @query_model_name
    end

    def query_model
      query_model_name.safe_constantize
    end

    # 定義resolve並命名為call
    # ...是指任意接受參數
    # 這方法的調用實際上是調用new.resolve(...)
    # 實際上這是object.call(...)的語法糖
    def resolve(...) = new.resolve(...)

    def [](model)
      Class.new(self).tap { _1.query_model_name = model.name }
    end

    alias_method :call, :resolve
  end

  private attr_reader :relation

  def initialize(relation = self.class.query_model.all)
    @relation = relation
  end

  # resolve方法的實現直接返回relation 
  # 提供子層類別所需的relation
  def resolve(...) = relation
end
```
</div>
<div class="w-1/2">
```ruby {all} {maxHeight:'400px', lines:true, startLine:1}
class Queries::Student::StudentWithAllTagsQuery < Queries::ApplicationQuery
  def resolve(tag_titles)
    student_ids_with_all_tags(tag_titles)
  end

  private

  def student_ids_with_all_tags(tag_titles)
    StudentsTag
      .select(:student_id)
      .joins(:tag)
      .where(tags: { title: tag_titles })
      .group(:student_id)
      .having('COUNT(tag_id) = ?', tag_titles.count)
  end
end
```
</div>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Perfect !!!

<div class="flex justify-center items-center">
  <img src="/photo/make-code-perfect.JPG" alt="Description" class="object-contain max-w-full max-h-400px">
</div>

<style>

h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

--- 

# Note QR code

<style>

h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>
