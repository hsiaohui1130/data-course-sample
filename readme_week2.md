### 清楚記載這個專案的目的和結果，最後的推薦分數是多少，是否有成功

沒有 ：（
不知道為什麼跑recommend_items的時候ram一直爆掉
目前仍是 rule base: 0.00847457627118644

1/3 01:30 補充：剛剛又再試了一下有過了 但是分數一樣是0.00847457627118644 應該是表示目前content base推薦的沒有效果
colab: https://colab.research.google.com/github/hsiaohui1130/data-course-sample/blob/main/sample-content-based-copy.ipynb?hl=zh-tw#scrollTo=jj31R5TKrrKP
Git: https://github.com/hsiaohui1130/data-course-sample/blob/main/sample-content-based-copy.ipynb

### 簡明清楚的使用說明：用了哪些方法？為什麼？

鑑於上回沒很了解資料就埋頭下去做走了很多冤枉路
這次決定先好好探索資料一番　過程中都將字母轉成小寫處理
#### metadata (劃掉的部分是覺得無法使用的)
- ~~category: 僅有一種結果出現32892次~~
- ~~tech1: 總共有32892個結果，其中一個值出現32882次，剩下10個都只出現一次~~
- description: 總共有13251個結果，沒有值的有536次，僅出現一次的有12530次，最多同一value出現59次
- ~~fit: 僅有一種結果出現32892次~~
- title: 總共有32299個結果，僅出現一次的有31766次，最多同一value出現9次
- ~~also_buy: 沒有值的有26295筆~~
- ~~tech2: 僅有一種結果出現32892次~~
- brand: 沒有值的有15673次，僅出現一次的有5252次，總共有7633個結果
- ~~feature: 總共有220個結果，沒有值的有32623筆，最多同一value出現12次~~
- rank_rank: 總共有31877個結果，僅出現一次的有31306次，最多同一value出現3次
- rank_category: 總共有13個結果，最多同一value出現31795次，有些分類跟美妝不相關
- ~~also_view: 沒有值的有24760筆~~
- details: 總共有32329個結果，沒有值的有132筆，最多同一value出現7次
- ~~main_cat: 僅有一種結果出現32892次~~
- ~~similar_item: 沒有值的有31588次，僅出現一次的有1296個，總共有1301個結果~~
- date: 總共有19個結果，沒有值的有32873筆，餘下19種結果都只出現1次
- price: 總共有3530個結果，沒有值的有21433筆，其中有185筆內容是CSS，1986種結果都只出現1次
- asin:總共有32488個結果，其中32084個asin都只出現一次，最多同一asin出現2次
- imageURL: 總共有15543個結果，沒有值的有16351筆，最多同一value出現38次
- imageURLHighRes: 總共有15543個結果，沒有值的有16351筆，最多同一value出現38次


#### ratings
- asin: 總共有32586個asin有被評分，其中13501個只被評分過1次，被評分最多的次數是8672次
- reviewerID: 總共有324038個用戶，其中287784個用戶都只有1次評分商品的紀錄，單個用戶最多評分次數是27次
- overall: 
-- 1分：37994
-- 2分：19887
-- 3分：28960
-- 4分：51242
-- 5分：223718
- unixReviewTime: 
-- asin: train跟test同時出現的asin有331個
-- reviewerID: train跟test同時出現的用戶只有38個


#### 由於新客比例非常高 所以會混用 rule_based 和 content_based

新客: 由於新客沒有購買紀錄 推薦優質熱門商品
- 有圖片
- 評分日期近
- 平均評分>=4
- 評分次數降冪取topN


舊客: 使用下面幾個維度做TF-IDF的運算，並綜合評估 (理想上想這樣完成)
- title
- description
- brand
- rank_category
- details

