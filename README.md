# SDGO單機版


## 啟動方式
1. 執行伺服器主程式
  * 按下enter可以重新讀取設定檔, 但是客戶端必須重開
2. 把`start-sdgo.bat`放置客戶端根目錄, 接著雙擊執行
3. 登入:
  * 帳號: `11111111111`
  * 密碼: 隨意打
4. 選擇任務頻道
5. 直接進練習場選機體
6. 伺服器主程式視窗輸入指令按下enter
  * `L` 重新載入所有資料
  * `S` 把機庫資料存成robot.txt
  * `R` 強制刷新連上的所有客戶端的機庫資料

## 特別感謝名單
#### 单机版开发，AI制作，翻译传播等:
* CF2P
* 654461754
* Multiply
* 张二虎
* 睡你嘛痺起來嗨
* Spoiled Splash
* 睡去的ZZ
* Unicorn
* 我的电脑
* ☆星辰丨夢の岸辺に☆
* 冰雪飞扬
* MKK
* NonnaNami
* 幻羽未来
* 暴走雷霆
* LikHow
* 移动人头
* 火狐狸

#### 赞助者:
* 迅肖
* ElvisL
* ImissLC
* 贪狼八月
* 空山灵雨
* 古铁
* boya
* 1372877720
* 976301390
* 262447996
* ZZATEE
* 乌曜诺斯
* DDD
* Ayin
* 541655181
* 1027001642
* Sfentami
* 2682596896
* 月明星稀鹊南飞
* 413681666
* 643645277
* 莫里亚蒂
* 1020565699
* Starlis
* Okarin
* 310550380
* 2280919521
* 492730315
* 867949776
* 叔叔我不认识你
* BXFY
* 卖女孩的小蘑菇
* Godowordz
* iantobu
* 冰箱
* 阿修斯
* 龙战星痕
* 纯洁的小镜子
* *夏
* *天琦
* *梓博
* u*n
* *了
* *伟
* *泽恩
* *松
* *英本
* *天
* *福林
* *磊
* *美玲
* 老*o
* *良
* *2
* 路*r
* *咔
* *你
* *1
* *旭
* *辉益
* *磊
* *xi tong
* *天正
* *远昌
* *冠杰
* *Y
* *聪
* *点
* *步
* *文洁
* *方成
* *钊
* b*a
* *王
* *宇劲
* *冠杰
* *一峰
* *乙林
* 393821710
* A*i
* 1198083277
* *嘉俊
* T*u
* H*0
* *!
* T*s
* *然
* *伟金
* z*a
* *振超

## robot.txt
* tab按鍵分隔
* 欄位順序
  1. 機體ID(16進制, LE小端優先, 0000為空位無機體)
  2. 組件(16進制, FF為不安裝)
  3. 合成次數(10進制, 0~5, 超過沒測)
  4. 合成數值(16進制, 第一位不知, 後三位直接對應%數)
  5. 機體等級(10進制, 1~13, 超過沒測)
  6. 機體經驗(10進制, uint32)
  7. 出擊場次(10進制, uint32)
  8. 外掛技能(16進制, BE大端優先, 4 byte, ID待查)
  9. 拋光(16進制, BE大端優先, 2 byte)
  10. 塗裝顏色1~6(16進制, 3 byte, 等同常見顏色編碼網頁)(紅色A1, 綠色B2, 藍色C3 >> A1B2C3) (例外: 000000對應不塗, 000008對應黑色)
* 特殊指令設定參數
  * `!!`開頭, 中間為參數名, 最後為參數值, 使用tab鍵分隔
    * 例如: `!!	ABC	123`, 設定參數`ABC`為值`123`
  * Name 設定自己的名稱, 只測過英數, 中文編碼需另外嘗試
  * GP GP數量
  * GO 出擊的機體是第幾台, 1開始, 暫時最大36
  * SearchID 搜尋好友/察看自己時的使用機體
  * SearchExp 搜尋好友/察看自己時的官階經驗

## egg.txt
* tab按鍵分隔
* 欄位順序
  1. 機體ID(16進制, LE小端優先)
  2. 槽數
  3. 機率(1000 = 1%)
* 沒湊滿100%, 有機會抽出保底機體


### Web API
* 皆為json格式
* 預設網址: `http://127.0.0.1:8080/`
* api測試網址: `http://127.0.0.1:8080/debug/`
* 靜態檔案放置路徑: `./www`
* `/api/do`
  * `POST`, `PUT`:
    * `"R"` 強制刷新
    * `"L"` 載入&強制刷新
    * `"S"` 保存
* `/api/user`
  * `GET`: 讀取
  * `POST`, `PUT`: 更新
  * 格式
```
{"SearchID":"8642","SearchExp":123456,"Name":"God12345","GP":233666999,"PageCount":254,"GO":2}
```
* `/api/egg`
  * `GET`: 讀取
  * `POST`, `PUT`: 更新
  * 格式
```
{
  "list": [
    {
      "P": 5000,
      "ID": "C65D",
      "C": 4
    },
    {
      "P": 15000,
      "ID": "C65D",
      "C": 3
    },
    {
      "P": 10000,
      "ID": "CD5D",
      "C": 4
    },
    {
      "P": 20000,
      "ID": "CD5D",
      "C": 3
    },
    {
      "P": 19000,
      "ID": "0F28",
      "C": 4
    },
    {
      "P": 1000,
      "ID": "C53A",
      "C": 4
    },
    {
      "P": 20000,
      "ID": "8F42",
      "C": 4
    },
    {
      "P": 20000,
      "ID": "8642",
      "C": 4
    }
  ]
}
```
* `/api/bot`
  * `GET`: 讀取
  * `POST`, `PUT`: 更新
  * 格式
```
{
  "list": [
    {
      "ID": "C65D",
      "C": 4,
      "Pos": 1,
      "UUID": "ADDE0001",
      "Lock": false,
      "C4": "4D301020",
      "Wing": 2,
      "WingLv": "00323232",
      "Sess": 66,
      "Lv": 13,
      "Exp": 10,
      "Skill": "124FE",
      "Polish": 50,
      "Color": [
        "F8F860",
        "F8F860",
        "F8F860",
        "F8F860",
        "F8F860",
        "F8F860"
      ],
      "Coat": [
        "3A9DA",
        "3A9DA",
        "3A9DA"
      ],
      "Charge": 2000
    },
    {
      "ID": "C65D",
      "C": 4,
      "Pos": 2,
      "UUID": "ADDE0002",
      "Lock": false,
      "C4": "4D301020",
      "Wing": 2,
      "WingLv": "00323232",
      "Sess": 66,
      "Lv": 13,
      "Exp": 10,
      "Skill": "124FE",
      "Polish": 50,
      "Color": [
        "F8F8E8",
        "F8F8E8",
        "F8F8E8",
        "F8F8E8",
        "F8F8E8",
        "F8F8E8"
      ],
      "Coat": [
        "3A9DA",
        "3A9DA",
        "3A9DA"
      ],
      "Charge": 0
    },
    {
      "ID": "C65D",
      "C": 4,
      "Pos": 3,
      "UUID": "ADDE0003",
      "Lock": false,
      "C4": "4D301020",
      "Wing": 2,
      "WingLv": "00323232",
      "Sess": 66,
      "Lv": 13,
      "Exp": 10,
      "Skill": "124FE",
      "Polish": 50,
      "Color": [
        "F8A028",
        "F8A028",
        "F8A028",
        "F8A028",
        "F8A028",
        "F8A028"
      ],
      "Coat": [
        "3A9DA",
        "3A9DA",
        "3A9DA"
      ],
      "Charge": 2000
    },
    {
      "ID": "C65D",
      "C": 4,
      "Pos": 5,
      "UUID": "ADDE0005",
      "Lock": false,
      "C4": "4D301020",
      "Wing": 2,
      "WingLv": "00323232",
      "Sess": 66,
      "Lv": 13,
      "Exp": 10,
      "Skill": "0",
      "Polish": 0,
      "Color": [
        "000000",
        "000000",
        "000000",
        "000000",
        "000000",
        "000000"
      ],
      "Coat": [
        "0",
        "0",
        "0"
      ],
      "Charge": 2000
    },
    {
      "ID": "402B",
      "C": 4,
      "Pos": 7,
      "UUID": "ADDE0007",
      "Lock": false,
      "C4": "4D301020",
      "Wing": 2,
      "WingLv": "00323232",
      "Sess": 6,
      "Lv": 13,
      "Exp": 0,
      "Skill": "124F9",
      "Polish": 10,
      "Color": [
        "007800",
        "007800",
        "007800",
        "007800",
        "007800",
        "007800"
      ],
      "Coat": [
        "3A9D2",
        "3A9D2",
        "3A9D2"
      ],
      "Charge": 2000
    },
    {
      "ID": "C65D",
      "C": 4,
      "Pos": 8,
      "UUID": "ADDE0008",
      "Lock": false,
      "C4": "30303030",
      "Wing": 2,
      "WingLv": "00323232",
      "Sess": 66,
      "Lv": 12,
      "Exp": 10,
      "Skill": "124FA",
      "Polish": 50,
      "Color": [
        "000000",
        "000000",
        "000000",
        "000000",
        "000000",
        "000000"
      ],
      "Coat": [
        "3A9DA",
        "3A9DA",
        "3A9DA"
      ],
      "Charge": 2000
    },
    {
      "ID": "AB3A",
      "C": 4,
      "Pos": 10,
      "UUID": "ADDE000A",
      "Lock": false,
      "C4": "30501020",
      "Wing": 3,
      "WingLv": "00323232",
      "Sess": 6666,
      "Lv": 10,
      "Exp": 30,
      "Skill": "124FC",
      "Polish": 10,
      "Color": [
        "F80000",
        "F80000",
        "F80000",
        "F80000",
        "F80000",
        "F80000"
      ],
      "Coat": [
        "0",
        "0",
        "0"
      ],
      "Charge": 2000
    },
    {
      "ID": "AB3A",
      "C": 4,
      "Pos": 11,
      "UUID": "ADDE000B",
      "Lock": false,
      "C4": "30501020",
      "Wing": 3,
      "WingLv": "00323232",
      "Sess": 66666,
      "Lv": 9,
      "Exp": 40,
      "Skill": "124FD",
      "Polish": 10,
      "Color": [
        "00F800",
        "00F800",
        "00F800",
        "00F800",
        "00F800",
        "00F800"
      ],
      "Coat": [
        "0",
        "0",
        "0"
      ],
      "Charge": 2000
    },
    {
      "ID": "AB3A",
      "Pos": 12,
      "UUID": "ADDE000C",
      "Lock": false,
      "C": 4,
      "C4": "30501020",
      "Wing": 4,
      "WingLv": "00323232",
      "Sess": 666666,
      "Lv": 8,
      "Exp": 50,
      "Skill": "124FE",
      "Polish": 10,
      "Color": [
        "0000F8",
        "0000F8",
        "0000F8",
        "0000F8",
        "0000F8",
        "0000F8"
      ],
      "Coat": [
        "0",
        "0",
        "0"
      ],
      "Charge": 2000
    },
    {
      "ID": "0228",
      "Pos": 13,
      "UUID": "ADDE000D",
      "Lock": false,
      "C": 4,
      "C4": "4D303030",
      "Wing": 5,
      "WingLv": "022A2C22",
      "Sess": 233,
      "Lv": 7,
      "Exp": 60,
      "Skill": "124FF",
      "Polish": 0,
      "Color": [
        "000000",
        "000000",
        "000000",
        "000000",
        "000000",
        "000000"
      ],
      "Coat": [
        "0",
        "0",
        "0"
      ],
      "Charge": 2000
    }
  ],
  "GO": 2,
  "GP": 233666999,
  "PageCount": 254
}
```


### extra.txt
* 進階自訂封包, 部份已猜出的數值會被`robot.txt`內的設定覆蓋
* 格式解釋
  * `#`開頭為註解
  * `$`開頭至`{`為封包名稱
  * `}`需為獨立一行
  * `{`以及`}`之間為封包資料, 16進制, 有無空格/換行無所謂
* 目前開放自訂的封包:
  * `UNIT1`: 進訓練場的機庫資料
  * `UNIT2`: 初始傳送的機庫資料, 不確定剩下欄位的意義
  * `UserInfo001`: 初始傳送的使用者資料, 有玩家名稱、出擊機體資料、出擊機體之位置、GP, 估計還有MB
  * `UserInfo002`: 搜尋好友/察看自己時的資料, 有玩家名稱、出擊機體、官階經驗、出擊機體資料, 估計還有官階、勳章等


### 組件ID
| 名稱 | ID |
|-----------|------|
|機動2/hp       | 24 |
|機動2/刀圍     | 25 |
|機動2/中彈     | 26 |
|機動2/遠彈     | 26 |
|機動2/噴氣     | 28 |
|機動3/加速     | 30 |
|機動6/實彈速    | 29 |
|機動6/光判      | 2A |
|機動6/索敵      | 2B |
|機動6/盾防      | 2C |
|機動8/降索      | 31 |
|機動8/V降       | 50 |
|機動10/防禦     | 2D |
|機動10/攻擊     | 2E |
|機動10/刀速     | 2F |
|機動10/中射速   | 49 |
|機動10/遠射速   | 4A |
|機動12/衝跳     | 32 |
|機動EX/EX      | 33 |
| | |
|攻擊2/hp        | 04 |
|攻擊2/刀圍      | 05 |
|攻擊2/中彈      | 06 |
|攻擊2/遠彈      | 07 |
|攻擊2/噴氣      | 08 |
|攻擊3/9攻       | 10 |
|攻擊6/實彈速    | 09 |
|攻擊6/光判      | 0A |
|攻擊6/索敵      | 0B |
|攻擊6/盾防      | 0C |
|攻擊8/破甲      | 11 |
|攻擊8/全彈      | 4E |
|攻擊10/防禦     | 0D |
|攻擊10/機動     | 0E |
|攻擊10/刀速     | 0F |
|攻擊10/中射速   | 45 |
|攻擊10/遠射速   | 46 |
|攻擊10/機動     | 0E |
|攻擊12/爆擊     | 12 |
|攻擊13/EX      | 13 |
| | |
|防禦2/hp         | 14 |
|防禦2/刀圍        | 15 |
|防禦2/中彈        | 16 |
|防禦2/遠彈        | 17 |
|防禦2/噴氣        | 18 |
|防禦3/9防        | 20 |
|防禦6/實彈速      | 19 |
|防禦6/光判        | 1A |
|防禦6/索敵        | 1B |
|防禦6/盾防        | 1C |
|防禦8/sp升        | 21 |
|防禦8/雷達        | 4F |
|防禦10/攻擊       | 1D |
|防禦10/機動       | 1E |
|防禦10/刀速       | 1F |
|防禦10/中射速      | 47 |
|防禦10/遠射速      | 48 |
|防禦12/最小化      | 22 |
|防禦EX/EX         | 23 |
| | |
|平衡2/hp          | 34 |
|平衡2/刀圍        | 35 |
|平衡2/中彈        | 36 |
|平衡2/遠彈        | 37 |
|平衡2/噴氣        | 38 |
|平衡3/都加         | 4D |
|平衡6/實彈速      | 39 |
|平衡6/光判        | 3A |
|平衡6/索敵        | 3B |
|平衡6/盾防        | 3C |
|平衡8/降索        | 40 |
|平衡8/sp升        | 41 |
|平衡10/防禦      | 3D |
|平衡10/機動      | 3E |
|平衡10/刀速       | 3F |
|平衡10/3攻        | 44 |
|平衡10/中射速      | 4B |
|平衡10/遠射速      | 4C |
|平衡12/破甲       | 42 |
|平衡EX/EX        | 43 |

### 額外技能ID
| ID | 名稱 | 訓練場能發動 | 原始資料 |
|----|------|-----------|---------|
|F9240100	|	V疫苗	|	X	|	X	|
|FA240100	|	新人類	|	X	|	O	|
|FB240100	|	格鬥術	|	X	|	X	|
|FC240100	|	PS甲	|	X	|	X	|
|FD240100	|	必殺覺醒	|	X	|	X	|
|FE240100	|	I力場	|	X	|	X	|
|FF240100	|	底力爆發	|	X	|	X	|

