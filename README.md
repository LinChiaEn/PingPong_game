# PingPong_game
## Introduction
### 作業題目
作業內容:以ML模式 自己(1P)跟自己(2P)對打HARD等級的乒乓球比賽
遊戲進行方式: 
設定rule，以rule based model 進行比賽，並以此取得data
從數據中提取特徵，以機器學習模型對特徵進行training
將訓練model放進線上遊戲平台之中進行線上比賽
### 觀察到的現象
隨著來回接球，球速會逐漸增加，大於板子移動的速度，即便球往下掉接近板子位置時，板子不一定能趕上接到球
當球一往下掉可能會撞牆折返很多次，使板子一直大幅度的左右移動
有障礙物時，1P和2P均須考慮往上和往下球的落點位置
## Method
### Rule-1P
先求球往下掉時的落點位置
假設球往上但side=1P時，代表會碰到障礙物，此時需算出落點位置並確認是否碰到障礙物，若碰到才要求反彈時回到platform_1的位置並移動platform
![image](https://github.com/LinChiaEn/PingPong_game/assets/93340978/8a8b0ae7-39ba-4e84-96d6-4fb61f66b3f7)
![image](https://github.com/LinChiaEn/PingPong_game/assets/93340978/90978239-82b2-4458-9011-dd8b98c5e54e)
### Rule-2P
先求球往上跑時的落點位置
假設球往下但side=2P時，代表會碰到障礙物，此時需算出落點位置並確認是否碰到障礙物，若碰到才要求反彈時回到platform_2的位置並移動platform
![image](https://github.com/LinChiaEn/PingPong_game/assets/93340978/ea2ec0c7-3085-4e39-a457-48d5773ece8b)
![image](https://github.com/LinChiaEn/PingPong_game/assets/93340978/cc7a3da0-d513-496d-b166-2917a5b320a9)
### 提取之特徵
Ball_x 
Ball_y 
Ball_speed_x 
Ball_speed_y 
Platform_1P
Platform_2P
Command
### 機器模型
KNN
## Result
NORMAL目前測試速度皆超過15
HARD有少部分速度會落在13、14，其他皆可超過15
## Discussion
來回及求次數(速度)隨著資料量的增加而變多，但速度達到一定時不會隨著資料量的增加而變快
![image](https://github.com/LinChiaEn/PingPong_game/assets/93340978/511ec0aa-0906-42c8-bf25-039bad0377f0)
KNN V.S. K-means
![image](https://github.com/LinChiaEn/PingPong_game/assets/93340978/c11bf446-4f1e-4a6b-ac3c-306ad28d0300)
訓練出來的模型跟選取特徵的多寡和資料數的多少有關，前提是rule有寫完整，之前因為沒有解決板子左右晃動的問題，即便輸入多筆資料數，速度仍無法增加，在改善此問題後，資料數減少也能過關
由於特徵提取的項目都維持固定，所以這次無法得出特徵數與破關數之間的關聯


