## 自然語言處理可視化

+ 目的：為了在[祐生基金會](https://www.archilife.org)報告[Text Analytics with Python: A Practical Real-World Approach to Gaining Actionable Insights from your Data](https://www.amazon.com/Text-Analytics-Python-Real-World-Actionable/dp/148422387X)，實作了一遍書中介紹的各種NLP操作，並將結果以視覺化的圖表呈現。

+ 主要工具：
  + `pandas`
  + `NLTK`
  + `scikit-learn`
  + `spaCy`
  + `gensim`
  + `fastHan`
  + `scattertext`

+ 文本來源：祐生基金會的例行活動公開紀錄文，包含 `國政聯誼會` 57篇及 `見識之旅` 44篇，兩種文類合計 **101** 篇。文本包含中文原文及英文譯文。
  + 按[文章分類](https://github.com/haowen-howard/Archilife-NLP/blob/master/DataFrame_by_articles_101rows.pkl)，共101個資料點
  + 按[段落分類](https://github.com/haowen-howard/Archilife-NLP/blob/master/DataFrame_by_paragraphs_412rows.pkl)，共412個資料點

+ 文本預處理：
  + 中文斷詞跟NER都使用`fastHan`，斷詞風格依據中研院`as`
  + 英文斷詞跟NER都使用`spaCy`

## 靜態可視化

### 依據中文文本
- __文本類別分佈__ - 使用PCA將文本向量降至2維，這裡的類別是文本實際的類別（`國政聯誼會` = Meeting， `見識之旅` = Trip）
![PCA](https://haowen-howard.github.io/Archilife-NLP/PCA%20Archilife%20events.png)
- __文本聚類分佈__ - 使用Kmeans計算文本向量之間的距離，預先設定2個聚類中心，這裡的類別是根據Kmeans計算出來的類別(即`0` 或 `1`)
![Kmeans](https://haowen-howard.github.io/Archilife-NLP/Kmeans%20Archilife%20events.png)
- __文本相似度__ - 使用餘弦相似性計算語料庫內的文本相似度，樹狀圖末梢標示文本事件的年、月以及文本類型（`國政聯誼會` = M， `見識之旅` = T）
![DocSim](https://haowen-howard.github.io/Archilife-NLP/Similarity%20across%20documents%20in%20the%20corpus_dendrogram.png)
- __句子相似度__ - 使用餘弦相似性計算單一文本內的句子相似度，每個節點代表一個句子。後續導入`PageRank`，設定句子數量後即獲得文本摘要
![SentSim](https://haowen-howard.github.io/Archilife-NLP/Similarity%20across%20sentences%20in%20a%20document_network.png)

### 依據英文文本
- __文本類別分佈__ - 使用PCA將文本向量降至2維，這裡的類別是文本實際的類別（`國政聯誼會` = Meeting， `見識之旅` = Trip）
![PCA](https://haowen-howard.github.io/Archilife-NLP/PCA%20Archilife%20events.png)

## 動態可視化
---
每一張圖表裡的文字都可以點選，也可以搜尋喔 :wink: 

### 依據中文文本
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_scattertext_fromCH_CleanTokens.html)__ - 文類1 vs. 文類2
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_characteristic_fromCH_CleanTokens.html)__ - 特徵詞 vs. 文類
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_scattertext_fromCH_NER_Label.html)__ - 文類1 vs. 文類2
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_characteristic_fromCH_NER_Label.html)__ - 特徵詞 vs. 文類

### 依據英文文本
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_scattertext_fromEN.html.html)__ - 文類1 vs. 文類2
- __[所有詞](https://haowen-howard.github.io/Archilife-NLP/term_characteristic_fromEN.html)__ - 特徵詞 vs. 文類
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_scattertext_fromEN_NER_Label.html)__ - 文類1 vs. 文類2
- __[命名實體詞](https://haowen-howard.github.io/Archilife-NLP/NER_characteristic_fromEN_NER_Label.html)__ - 特徵詞 vs. 文類
- __[主題](https://haowen-howard.github.io/Archilife-NLP/Empath_topics_fromEN.html)__ - 文類1 vs. 文類2
- __[文本相似度](https://haowen-howard.github.io/Archilife-NLP/tfidf_embeddings_across_docs_fromEN.html)__ - TF-IDF詞嵌入

---
![Minion](https://octodex.github.com/images/minion.png)
