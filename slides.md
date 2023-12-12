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

<!--
再來就是討論進階一點的，或者可以說是連想都沒有想過的一層，Query Layer。這部分是為Query的過程做封裝。通過引入新的抽象層來減少 Active Record（Rails 的 ORM）的負擔

使用查詢物件（Query Objects）來提取模型中的複雜查詢，而這樣做的原因在於

Rails 中，模型經常承擔著構建和執行數據庫查詢的責任。

當查詢變得複雜時，這可能導致模型變得臃腫且難以維護

但是有Query Object就允許我們將查詢邏輯從模型中分離出來，把它們封裝在專門的類別中。這使得代碼更容易維護，且查詢邏輯可以重複使用
-->

---

# 為什麼要分享？

<div v-click="[1, 2]" class="flex justify-center items-center relative-container">
  <img src="/photo/1.JPG" alt="Description" class="object-contain max-w-full max-h-400px absolute-panel">
</div>

<div v-click="[2, 3]" class="flex justify-center items-center relative-container">
  <img src="/photo/2.JPG" alt="Description" class="object-contain max-w-full max-h-400px absolute-panel">
</div>

<div v-click="[3, 4]" class="flex justify-center items-center relative-container">
  <img src="/photo/3.JPG" alt="Description" class="object-contain max-w-full max-h-400px absolute-panel">
</div>

<div v-click="[4, 5]" class="flex justify-center items-center relative-container">
  <img src="/photo/4.JPG" alt="Description" class="object-contain max-w-full max-h-400px absolute-panel">
</div>

<div v-click="[5, 6]" class="flex justify-center items-center relative-container">
  <img src="/photo/5.JPG" alt="Description" class="object-contain max-w-full max-h-400px absolute-panel">
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

<!--
首先今天想談談這個話題，是因為我的學習歷程就像以下的狀況

click 1

第一次看到同事們這樣寫，完全沒有頭緒，為什麼程式碼要這樣寫，總覺得寫在哪裡都可以，好像沒啥毛病，但經過一次次的code review開始不知道自己在寫什麼

click2

詢問朋友與同事後，還是一整個不知所以然，一點頭緒都沒有的悲慘窘境，讓自己讀完物件導向後處在一個自我懷疑階段

click3

然後參加會議或者讀書會，卻找不到一個滿意的答案，總覺得這一切都是別人經驗一樣，一切都很模糊不清

click4

然後決定繼續看書看medium去找到真正符合我的答案

click5

看了層式設計結構後，我只能說真香，在這設計過程中，發現到另一個世界，從不同角度去解釋了我的困惑
-->

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

<!--
適合對象：
對於Rails有一定的了解，比如MVC架構，還有瞭解物件導向的概念。最好是寫過Rails的，才能對於今天的分享會比較有感受

比較困難的地方或許是在抽象層的建立，因為這部分為了要成為一個通用介面，所以需要使用到Meta Programming的部分

但我覺得今天我最想傳達的概念是：
可以判別程式碼應該要寫在哪邊，這除了需要知道如何判別對的位置，還有他的意義是什麼，而當別人問你為什麼要放那邊時，你不在是說單一職責或者物件導向等來解釋

而今天的流程，會先介紹Rails的旅程，然後討論到抽象層，再來先講到最容易理解而且一開始寫Rails時最先碰到的Service Object。
我記得去年ihower在coscup有講到很多軟體工程師，在不知道程式碼放什麼地方時，就常常會放在service。而我用layer概念去思考時，才發現這裡面的通用性，其實有一定的限制以及規範，也可以理解被濫用得原因，我們在後續會更詳細介紹。

然後帶過一些DDD的基礎概念，再來引入Form以及更進階的Query layer
-->

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
在討論分層設計時，我們先來看看Rails從使用者開始到我們的Application流程，實際上也是一層層的運作

1. 從Browser到OS(Operating system)會將URL轉換成HTTP request
2. 而OS負責處理這些request，包括網路通信
3. 再來就是Web Serve會接收瀏覽器請求，Rails Application的啟程就是從這邊開始，就是我們Puma
4. 然後到了Rake，這地方是Ruby Web的服務街口處理Web服務跟Rails應用程序之間，也負責接收傳遞進來的HTTP request，最後轉發給Rails應用程序處理
5. 然後在Rails接收到這些轉發的request後，會根據route跟controller來決定如何處理這些request
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

<!--
剛剛的整個流程在日常生活中，就很像我們的傳輸帶

我們就把每一個Request就像是一個包裹一樣，會經過每一個工作站進行處理，最後再返回給使用者。


那工作站在網路內的概念其實就是一個個抽象層，而我們將所有抽象層接在一起變成程序線，這樣的設計方式就是一種分層設計。


而我今天要在分享的，就是如何在rails中，用這種設計方法將應用程序分為不同的層，每一層都有特定的職責。


並且可以按照一定的方式鏈接在一起，以構建完整的處理流程。


那如何在我們探討如何設計前，應該要先思考的是，難道MVC架構下已經不足以應付這些流程了嗎？為什麼還需要更多的層去增加App的複雜度？
-->

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

<!--
那就要看看ＭＶＣ這樣的分層設計是否符合良好的抽象層特質。


首先是單一職責：每層的指責可以廣，但不可以重疊。我覺得在小型App之中，這是可以符合的，但在App持續長大的過程，會讓Controller與Model越來越廣，最後形成上帝物件


然後平行的層與層之間，不互相耦合，但是實際上Moled在MVC架構下，有時會需要在意到Controller或者說是介意使用者的參數來決定動作，舉之後會提到一個例子是，我們需要根據使用者的操作來決定callback，這件是情就是model與controller之間的耦合。
然後層與層之間只會單一方向（由上往下）這概念就跟輸送帶一樣，不會逆推


再來介面與實作分離，內最重造的是隱藏內部實現細節，我覺得這裡的介面實作並不只是在繼承鏈上的抽象與實作關係，甚至可以套用在一個物件內開放的公開方法與私有方法，


就像是Service Object一樣，我們呼叫一個call的抽象interface然後讓實作封裝在私有方法內，但在controller內直接操作流程已達到目的，然後將實作全部塞在私有方法內，這會造成fat controller或者是fat model。 


補充一下，想知道interface的概念可以看看Good code Bad code，這解釋得挺好的


獨立測試，這就不用多說了，如果職責拆得越細，單獨測試的範圍就會越精準


那..單純用MVC就沒有優點了嗎？ 當然有，學習曲線會很低
-->

---

# Application Layer - Service

<div class="flex justify-center items-center h-full">
  <img src="/photo/pre-service-layer.png" alt="Description" class="object-fill">
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
然後這是我們今天第一層要分享的Application layer，先讓大家看一下這裡的結構是controller與view屬於使用者的顯示層，也就是presentation layer，然後model屬於domain layer，我們現在是要在MVC架構下，多增加一個Application layer，也就是Service的部分。
-->

---

# Service Object - Definition

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

<!--
首先先說到Service Object的普遍定義，就像我們剛剛提到的他會位於Controller與Model之間，而且只代表單一業務的操作，換言之就是單一職責。

那更嚴格點的定義是Service Objects是個Callable Objects。這意味著這些對象會回應 .call 方法。這就是要讓其他人知道，他可以回覆call方法，所以是Service Objects

但有一種狀況他不會回應call object也可以是Service Objects，就是如果這個操作流程是在背景作完成，例如sidekiq等，那就需要用其他interface來區分差異
-->

---

# Model or Service ? - Model（Domain Layer）

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

<!--
所以到底要怎區分方法放在model還是service？這就要先知道model是在幹嘛的
首先對於基本的數據操作，像是創建、更新、刪除、查詢等，通常應該放在Model層

然後是簡單的業務規則，像是例如數據驗證、計算字段（例如計算年齡或總計）、狀態機管理等，適合放在Model中。

最後是商業邏輯的部分，為了維護數據一致性和完整性的規則的方法也會在model，這是為了確保數據的正確性無論是透過哪種途徑被存取或修改。就像是callback
-->

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

<!--
然後我就開始思考，怎樣的商業邏輯以及一制性可以放在model。


我的結論是當你的方法屬於功能設計，基本上就可以放在model之中，這種屬於單一操作的方法，才可以符合model的設計方式


但我所討論的範圍是限制在哪些方法該放在model，而實際上，model還包括狀態機等物件狀態的操作。


以上的舉例就可以看到，這裡的calculate或者是update等，就是但一功能，裡面並沒有包含程序性的邏輯，那就適合放在model之中
-->

---

# Model or Service ? - Service（Application Layer）

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

<!--
再來討論看看什麼東西該放在Service，第一點其實是二三點的結論，首先是複雜的業務流程，這意思是說在一連串的操作中，需要操作到多個model或者是一系列的操作時，使用Service Objects更合適。

而第二點的意思是，首先是多個model的操作放在service object時，可以減少model之間的相互依賴，因為可以避免在特定model中操作多個其他物件的流程

第三點則表示，特定的業務邏輯，經由封裝就可以重複使用

再來是與後台處理或定時任務相關的複雜邏輯也會放在service內部，因為這類的任務，實際上只跟我們一般認知的service差在後台或者定時等的任務操作，但內部的實踐模式，還是屬於跨model與一系列的業務流程操作相同
-->

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

<!--
所以我就想說，這是不是跟過程式設計概念相同，就是我們把一系列的操作，讓call方法去實踐，然後整個就像是流程一樣，過程中也會與不同的model或者說不同的物件，互相交互來處理特定場景的service
-->

---
clicks: 6
---

# Service Interface

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

<div v-click="[5, 6]" class="absolute-panel">
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

<div v-click="[3, 4]" class="absolute-panel">
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

Presentation -> Application -> Domain
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

<!--
再來討論的是，那service內該如何設計以及如何使用才是正確的方式


click1


第一個就是我們要區分剛剛所提到的背景作業其實也屬於service object的一部分，那我該怎讓大家知道差異，就是當我們看到這物件內的interface時，直接理解到，這是不是屬於背景作業 -> 用perform與call作為區別，前面提到service object是call object，那就應該用call，而向sidekiq等背景作業，其實他們都有perform_later等等一系列的perform方法，所以這類的背景作業，應該公開的是perform的方法，而非call。


click2


再來是呼叫service object的地點該在哪裡？
根據layer design的概念來看，或者從輸送帶的角度來看，對於每一層的操作方向，是單一方向，也就是一開始提到的，使用者開始的presentation layer然後到application再到domain，那呼叫application內的service object就應該在controller內呼叫使用才對。


click3


最後是既然controller呼叫service，那params該在哪裡處理？我覺得這就要回到service職責層面來看，就service而言，他是對於業務邏輯一系列的操作，但並不包含params資料的清洗與處理，這類的邏輯應該由prsentation layer內的controller處理後在將資料傳入service內才正確，這樣service就不需要在意使用者輸入的內容是什麼，來減少application layer跟presentation layer的耦合。
-->

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

<!--
在前面我們都在討論Service Object而還沒提到如何建立抽象層，來創立共通介面。

在這之前所提的其實都還沒有到層的部分，只有在建立完共同規範後，才知道Service layer該如何遵循共同規範。


首先我先創立一個ApplicationService的抽象層，並extend一個dry-monads的套件


這套件其實可以處理很多狀況，例如是maybe/result/與try的情況，我就不多解釋套件使用，這上方有連結，有興趣的可以看看


而我們在這extend的是Dry Initializer，這讓我們在子層只要寫param而省去寫initialize


我覺得這樣的寫法很不錯，因為可以直接知道這service需要params 內哪些參數，而且感覺跟model的schma很像
-->

---

# Layered Design

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

<!--
我覺得剛剛的分享，還無法真正體會到分層設計的好處，我在這裡先再次提醒何謂分層設計，因為接下來的範例會依照這樣的模式去實踐。
首先是分層架構是一種架構模式，該模式意味著將應用程序的組件或功能分成水平的邏輯層，例如剛剛介紹的Application layer。然後使用者數據從上到下流動，因此每一層不依賴於它們頂部的層。

所以重點就是這六點，
單一職責
從上而下且單向流動
便於測試維護
向下依賴
提高維護以及擴展性，而可讀性的話，我覺得不去看抽象層部分的確是有的
-->

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

<!--
然後幫剛剛說的那些特點轉成圖片就是這樣
首先是層層交互應由上而下
但是跨域的層越少越好

而由上而下依序是Presentation layer，用來負責與使用者交互
然後Application layer: 就是剛剛介紹的Service部分，這是負責組織領域對象，以滿足不同的使用情境
然後Domain layer: 主要描述業務實體、業務規則和不變性的定義

最後是Infrastructure layer: 負責處理與數據庫與外部服務等等之類的，那我們今天不會討論到這部分，所以大概提一下
-->

---

# Presentation Layer - Form

<div class="flex justify-center items-center h-full">
  <img src="/photo/pre-form.png" alt="Description" class="object-fill">
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
在前半部我們討論了Presentation Application跟Domain layer，現在我們要在要在Presentation layer多加一個Form layer，我相信大家一定聽過或用過Form Object，但可能有些模糊什麼時候該用，已經不知道如何就夠成一個層，所以接下來就是介紹Form
-->

---

# Before Form

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

<!--
先考慮一個場景，就是我們有一個Controller，並且內部實行的業務是創立使用者並且決定這使用這要不要寄送信件


我覺得一開始的寫法會是在User model內設定attribute，然後讓model根據attribute來決定是不是要觸發callback。


但這樣就會產生一個問題，就是User model需要介意controller內的參數才能實踐相關邏輯這其實就是耦合，是controller與model之間的耦合


而且model真的有需要在意使用者的參數嗎？或者說model的職責有包含考量param這件事情嗎？而這樣日積月累後，很可能造成Fat model


那如果在Service內處理？


但我們剛剛有提到Service不應該顧慮到UI參數，也無法(或者不應該)將驗證或者callback等加入service 之中這反而會導致God Object，所以我們需要Form
-->

---

# Before Form Layer

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

<!--
這張圖可以簡單解釋我剛剛所說的耦合狀況，其實在MVC下App就是處理User所提供的訊息，所以第一個主要是消化近來的資訊，再來就是回應使用者


其中的第一項，所做的事情就是更新或者創立Domain Object，而問題就在於整個流程之中，從使用者輸入訊息到創立或者更新物件就是從View → Model的流程


這是不是就意味著 Model需要在意UI? (例如資料的清洗或著格式轉換等) → 但從層式架構上是不允許的！


而不允許是因為有兩種情境需要考慮
第一點是，處理複雜的表單提交導致太多的業務邏輯直接寫到模型中，例如驗證與數據處理，會導致跨層耦合。

第二個是多個具有上下文的情境，會導致模型充滿了不必要的條件和業務邏輯

所以我們才需要額外架構Form layer來處理這部分
-->

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

<!--
所以我們就來設想，我們需要怎要得一個Form Object才可以解決剛剛提到的兩點，而一般最常見的結構包括

click 1
首先是initialize初始化

click2
再來是validate驗證表單內容

click3
最後就是save提交表單

click4
那如果要有save後的動作就會包含像是after_save等的callback 

click5
所以我們整個FormObject會有以上四個要素，而為了達成這四項，我們就會在抽象層的部分來完成
-->

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

<!--
不過在真正開始之前，我想讓大家先認識一下兩個方法的使用。

首先是yield 的部分一定都很熟悉

但想給大家看的是第二部分的and block的方法使用

這看起來跟yield執行結果一樣，但實際上and block所傳入的block可以變成一個call object

所以那個block就像是參數一樣從這一個方法，傳到下一個方法之中，然後使用.call的方式執行
-->

---

# Form Layer Sub-class

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

<!--
首先我們先看子層的部分，會繼承一個抽象層ApplicationForm

而在子層中會實踐callback after_commit

並且包含驗證validate email的部分

然後將submit!方法放置於private method之中，以確保表單提交過程，會經過ApplicationForm抽象層做處理
-->

---

# Form Abstraction layer
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

<!--
在抽象層的部分，我會先大概說明一下，等等會等在實際應用部分會更近一步解釋

首先我們為了達成跟model相同的callback以及類似schema概念的attribute

所以需要引入ActiveModel中的API與attribute然後定義兩個callback類方法

並且實作表單提交的狀況，在這部分的save是屬於public而子層的submit!會在這裡執行後執行callback
-->

---

# 實際應用

<div id="container" style="height: 100%">
```ruby{monaco-diff}
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
在這一部分就是我實際上在公司專案進行的重構，裡面太多程式碼細節我就不在這裡展示，但在這個controller內引入form object之後，整個方法的總共縮短了25行的空間

click
-->

---

# Form Layer

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

<!--
但我多增加了兩個檔案！再來我就來解釋一下整個程式碼流動過程以及這些方法是幹嘛用的


click1


首先是define_callbacks，save跟commit部分，然後提供可以在子層使用的class method，after_save與after_commit，如螢幕上所示，那對應到sub-class就是使用了after_save來呼叫generate_custom_virtual_event而且這個call_back會根據attribute內tour_params的其中一個參數skip_warnings?來決定要不要觸發

click2


當我在controller內使用form.save時，將整個submit!流程使用transaction來確保資料的一制性，意思是說當A model出錯回滾時，B model也會一起回滾。

而在整個流程完成後，會去run_callbacks
再來搭配一個gem就是AfterCommotEverywhere來確保after_commit後的執行動作。

click3


這就是整個抽象層與子層之間的交互以及程式碼的流動，來達成form.save的流程

以上就是從Form Object到Layer的轉換，這樣的架構可以達到資料一制性以及Domain layer與Presentation layer解耦合，也避免掉fat controller與fat model的產生
-->

---

# Application Layer - Query

<div class="flex justify-center items-center h-full">
  <img src="/photo/pre-query.png" alt="Description" class="object-fill max-w-3/5">
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
再來就是談到Domain Layer如何額外架設更高層的結構，而且我覺得這部分是沒有看過，還真的不會想到會這樣做的一層。

首先我們通過引入新的抽象層來減少 Active Record（Rails 的 ORM）的負擔

使用Query Objects來提取模型中的複雜查詢

而這樣做的原因在於Rails 中，模型經常承擔著構建和執行數據庫查詢的責任。

當查詢變得複雜時，這可能導致模型變得臃腫且難以維護。

Query Object允許我們將查詢邏輯從模型中分離出來，把它們封裝在專門的類別中。這使得代碼更容易維護，且查詢邏輯可以重用。

這層的兩個重點就是重用跟避免fat model
-->

---

# Application Layer - Query Object

Query Object: 用於建置和封裝資料庫查詢。

-> 這個模式的主要目的是將持久層（通常指資料庫操作）與領域邏輯（業務邏輯）分離，從而提高程式碼的可維護性和可重複使用性

簡言之，Query Object它的主要目的是從模型（Model）中提取出複雜的查詢，並將這些查詢封裝在獨立的對象中，來降低model的user-facing features，並且以Domain-level Object作為輸入，來負責特定場景下的查詢狀況。

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

<!--
一般Query的寫法可能是用使用類別方法或者是scope的方式，而如果整個query過程過於繁雜時，其實可以額外抽出一層，來負責管理這類的程式碼
-->

---

# 實際應用

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

<!--
因為這部分困難的部分在於抽象層的架構，所以我們直接進入實際應用，左邊是我們專案內重構前的樣子，然後右邊重構後，就簡潔許多。理所當然的，我減少了程式碼但增加了檔案
-->

---
clicks: 3
---

# Query Layer Abstraction

<div class="flex space-x-6 mt-5">
<div class="w-1/2">

```ruby {all|18-20|16|all} {maxHeight:'400px', lines:true, startLine:1}
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
# scope :with_all_tags, Queries::Student::StudentWithAllTagsQuery[self]

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

<!--
而抽象層以及對應的子層的結構如螢幕所示
首先我們先定義Scope
就像是我們剛剛在model內寫的scope

而這scope內的 self 指向當下的model自己

然後就會觸發我們在抽象層定要的[]方法，而處發流程就是


click1


def [](model)
  Class.new(self).tap { _1.query_model_name = model.name }
end
這個方法會動態創建一個新的匿名類，以這個例子為例，因為呼叫StudentWithAllTagsQuery，所以class.new時會是StudentWithAllTagsQuery。然後，它將剛剛model定義的self傳入，將model的名稱設定為StudentWithAllTagsQuery的 query_model_name


click2


然後當我們呼叫這個scope時，實際上我們是呼叫.call方法，就是StudentWithAllTagsQuery[self].call
然後因為設置alias所以觸發了ApplicationQuery 中的 resolve 方法，所以就我們就在resolve內定義一個new.resolve，這就向是創立StudentWithAllTagsQuery 後調用這實例的resolve方法一樣


click3


然後就回到sub-class的部分，這裡的resolve方法被定義為實際查詢的邏輯，然後讓private method去實踐查詢步驟，當然這部分我就不複雜化，就只有單一步驟而已

執行完之後就會返回查詢結果。

這就是整個Query layer的架構，來讓Query object可以重複使用，因為是利用抽象層內動態生成匿名類的關係而達成，同時也可以降低fat model的產生
-->

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

<!--
我覺得今天介紹內容不是鼓吹使用layer的設計模式，因為不能確保每個人都會遵守這樣的規則去運作，若是被誤用的話，那就像圖片一樣尷尬。

但我從學習layer design的過程中，也漸漸了解到為什麼大家會這樣寫，而有哪些部分是被遺漏的，又該怎麼去建構更好的程式碼，希望大家可以學到這樣的思考模式。
-->

---

# 謝謝大家！

<div class="flex justify-center items-center">
<img src="/photo/dog.gif" alt="Description" class="object-contain max-w-full max-h-400px">
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
