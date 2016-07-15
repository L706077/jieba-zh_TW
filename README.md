# jieba-zh_TW

結巴(jieba)斷詞台灣繁體版本


## 原理

採用和原始jieba相同的演算法，替換其詞庫及HMM機率表製做出針對台灣繁體的jieba斷詞器


## 使用說明

* 相容python2和python3
* 將jieba資料夾放在你程式的資料夾底下
* `import jieba`


## 程式碼範例

操作方法同原始jieba

### 斷詞

```python
import jieba

#如果您的電腦同時要使用兩個版本的jieba，請自訂cache檔名，避免兩個cache互相蓋住對方
#jieba.dt.cache_file = 'jieba.cache.new'

seg_list = jieba.cut("在非洲，每六十秒，就有一分鐘過去") 
print("|".join(seg_list))
# 在|非洲|，|每|六十秒|，|就|有|一分鐘|過去

```

### 關鍵詞抽取
尚未替換機率表，輸出的結果非常不可靠


### 詞性標記
應該是一跑就會噴錯的狀態


## 可靠度探討
拿本份程式碼去和*jieba轉簡體後斷詞*、*jieba直接斷繁體字*這兩個方法，去斷[這篇台灣記者寫的新聞](http://www.appledaily.com.tw/appledaily/article/international/20160715/37308809/)。並以[中研院中文斷詞系統](http://ckipsvr.iis.sinica.edu.tw/)作為標準答案，以詞為單位，去計算這三個方法和中研院的結果的[Edit distance](https://en.wikipedia.org/wiki/Edit_distance)


|Edit distance|第一段(92)|第二段(136)|第三段(75)|第四段(52)|第五段(63)|
|---|---|---|---|---|---|
|jieba zh_TW      |9|20|12|12|9|
|jieba轉簡體後斷詞|44|43|31|23|21|
|jieba直接斷繁體字|53|74|43|34|34|
(括號內為中研院斷出來的詞彙數)


## 感謝

* 中央研究院資訊科學所詞庫小組中文斷詞線上服務

## 注意事項

使用本份程式碼請遵守[中研院斷詞服務之服務條款](http://ckipsvr.iis.sinica.edu.tw/terms.htm)其中的衍生資料相關規定


## 一些問題

詳見我Blog上的這篇文章：[關於結巴(Jieba)斷詞的幾個問題](https://blog.ldkrsi.in/%E9%97%9C%E6%96%BC%E7%B5%90%E5%B7%B4%E6%96%B7%E8%A9%9E%E7%9A%84%E5%B9%BE%E5%80%8B%E5%95%8F%E9%A1%8C/)