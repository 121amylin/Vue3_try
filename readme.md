#### Vue2  VS Vue3
- 引入方式
- 组合式 API / Composition API
 - Vue3 EventBus、Mixins不建議使用
 - 移除$on、$off用法；改用mitt取代EventBus



#### Composition API
- 引入功能組件  ref => data  、 setup 、 return
- 雙向綁定的數據透過ref包裝後，不能透過解構附值得方式取出來；會變成單純的值~沒有雙向綁定的功能
- ref  VS reactive ，[影片:ref 好還是 reactive 好 ?](https://youtu.be/8UgayQaUsuU?list=PLbOfcOk7bN42x3sMxZMHUNb6z8YzJrQJn&t=761) 、[總結](https://youtu.be/8UgayQaUsuU?list=PLbOfcOk7bN42x3sMxZMHUNb6z8YzJrQJn&t=1523)

---
#### Vue3 CLI
- template 根組件不限單一DOM
- 自動引入用到的模塊

- [How used ref with CDN](https://github.com/vuejs/docs/issues/786) 
用ES6解構語法取出來
```javascript
const { ref } = Vue
```

----
### 【Composition API】
[竹白記事本__Vue 3 - Composition API](https://chupai.github.io/posts/2104/compositionapi/)
- setup 選項將作為組合式 API 的入口
- return {} // 這裡返回的任何內容都可以用於組件的其餘部分
- reactive 方法建立響應式物件
  Proxy實現
  深度轉換、監控
- ref 方法建立響應式變數
  資料是物件型別的話，預設不會深度監控，要用{deep:true}  (最好不要這樣用，會整包掃)
  回傳的 Ref 物件在模板中訪問時是被自動解開的，因此不需要在模板中使用 .value
  如果將 Ref 物件分配給響應式物件 的 property 時，Ref 物件會自動解構；但是陣列不會，仍然需要加 .value
- watch(監控參數,callbackFn(newValue,oldValue))
  要監聽物件裡面的特定屬性，要用function方式返回(這樣才是ref或reactive包裝過後可監控的值)
  監控參數可以傳array
- watchEffect(callbackFn)
  初始會執行一次，可以自扺擋掉他
  可以關掉他



---
### 【Vue2 API】
#### provide/inject
-  [聊聊 Vue 中 provide/inject 的應用](https://www.uj5u.com/qiye/175412.html)
- 允許一個祖先組件向其所有子孫后代注入一個依賴，不論組件層次有多深，并在起上下游關系成立的時間里始終生效
- provide出去的資料，只能inject在自己的子組件，兄弟組件不行
- 避免在子組件直接修改provide傳過來inject的值，會報錯。
  Avoid mutating an injected value directly since the changes will be overwritten whenever the provided component re-renders.
  避免直接改變注入的值，因為只要提供的組件重新呈現，更改就會被覆蓋。
- 比較:在子組件直接修改props的值得抱錯:
  Avoid mutating a prop directly since the value will be overwritten whenever the parent component re-renders. Instead, use a data or computed property based on the prop's value. 
  避免直接改變 prop，因為每當父組件重新渲染時，值都會被覆蓋。 相反，根據道具的值使用數據或計算屬性。

<!-- 3533 -->
<!-- 5954 -->

### 【其他】
- [vite: Make web dev fast again. - Kuro Hsu | MOPCON 2020](https://www.youtube.com/watch?v=cZliOi98OZA)
- [Kuro Hsu](https://github.com/kurotanshi?tab=repositories)
