# passenger-hotspot-prediction
## Motivation
載客熱點預測係經由分析計程車乘客之歷史乘車時間與地點資料，預測未來特定時間、特定地點的乘車需求。妥善運用合宜的預測模型可有效媒合司機與乘客、增加計程車載客率、降低乘客等車時間，進而減少道路上計程空車、降低空汙廢氣排放等，提升交通服務品質，做為發展與經營智慧城市之重要參考。

## Demand
預測內湖區在特定時段、各地點的乘車需求。

## Data
![image](https://github.com/jack830503/passenger-hotspot-prediction/blob/main/data/zones.png) <br>
- train_gps_points.csv：乘客上車GPS點位記錄，此資料乃經由篩選計程車錶於內湖區範圍內的啟動記錄而得，並且將計程車錶啟動時間與地點視為乘客上車點，共4,118,812筆資料。
    - Datetime：計程車錶啟動時間 (台北時間 GMT+8:00)
    - Longitude_X：GPS記錄經度 (WGS84座標)
    - Latitude_Y：GPS記錄緯度 (WGS84座標)

- test_hire_stats.csv：乘車需求預測。
    - Test_ID：乘車需求之流水序號，共672筆
    - Date：預測日期，格式 YYYY-mm-dd，如2017-02-01
    - Hour_slot：預測時段，以一小時計，本欄位的值為0~23
    - Hire_count：內湖區該時段的乘車需求預測數量。

## Code
main.ipynb為主要程式碼。
- 資料前處理 ：
  1. ＥＤＡ分析
  2. 額外加入該時段天氣資訊並分析相關性。
  3. 特徵選擇
- 建立模型，分割資料集 (選擇ＬＳＴＭ)
- 訓練模型
- 預測test_hire_stats.csv中Hire_count

## Ranking
依RMSE(Root-Mean-Square Error)計算分數與排名。
<br>
Score : 7.2039617
<br>
Rank : 7th/35
