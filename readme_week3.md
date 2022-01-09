### 清楚記載這個專案的目的和結果，最後的推薦分數是多少，是否有成功
分別用以下三種實作 collaborative filtering 的方法，找出你會推薦 top 10 的商品＆分數，並比較這三種方法產生的結果。
- User-based collaborative filtering: 0.0
- Item-based collaborative filtering: 0.003424657534246575
- 套件 surprise 實作 collaborative filtering: 0.0017123287671232876

### 簡明清楚的使用說明：用了哪些工具和方法？為什麼？
這次的練習是單就 collaborative filtering 的三種方式進行
因為有過去有購買紀錄的使用者只有38位，所以可以有歷史紀錄可以參考推薦的比例本來就很少，結果不好感覺是預料中的事情，不過就資料部分三者都有先進行處理，包含挑出beauty類別，過濾重複資料等等，surprise 的方法因為計算量太大的關係，還有另外濾除只出現一次評分的商品紀錄和只評分過一項商品的使用者。
