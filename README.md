# 2022-0102-Homework

**專案目的**
透過Amazon購物網站的美妝消費資料，萃取客戶購買之商品、評論歷史資訊、產品基本資訊等影響推薦成效之欄位，建置以內容為基礎的過濾(Content-based)的方式，替指定消費者，依據過去歷史購買的商品，推薦類似的k個商品，並使用是否實際購買推薦商品作為評估recall score成效指標

**使用工具**
Python、 Google Colab

**使用資料**
資料來源
All_beauty.csv
meta_All_Beauty.json.gz

**資料描述：**
All_beauty.csv：提供客戶商品申購、評論歷史資訊

時間區間：2000-01-10 ~ 2018-10-02

訓練資料：2018-03-01 ~ 2018-09-01 (本次僅採用半年資料)

測試資料：2018-09-01 ~ 2018-09-30

**資料整理**
metadata將title重複的資料移除 

這個部分原本有想過將其他資訊(description, brand, also buy...etc)納入一併分析，但相關的遺漏資訊或重複資訊較多，且參雜著無意義雜訊，因此最後決定使用title進行推薦

**TF/IDF：**
TfidfVectorizer計算tf-idf數值
使用cosine_similarity計算相似度矩陣

**推薦規則**
我們先透過title的tf_idf進行推薦，但由於重複的評論者者有限，因此推薦的數量仍不足夠(預設需推薦數量為10)。

一樣結合上次的rule based 的推薦系統，將半年內top10的商品依不足數目進行推補。

**結論**
結合content-based 與 rule-based結果，本次的預測率為0.1，比起上次進步幅度仍屬有限，主因其實也是因為testing users在原本training sample中的比例偏低，因此能給出的預測數目有限。
