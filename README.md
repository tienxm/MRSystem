## 第三組 混合實境倉儲管理系統
***

```
組長:李昆達
組員:張鈞瑋
組員:田翔銘
組員:徐毓廷
組員:田先勛
```
## 專題內容概要
>本研究將透過設計思考流程，探索場域包括人員行為模式與背後意涵，並以混合實境作為切入工業4.0資訊傳遞過程的改善實作。了解人員對於混和實境的人機協作過程，以及人員對於系統前後的主觀感受與客觀績效等變化有所掌握情況。


## 甘特圖 hw2

```mermaid
gantt
    title 專案甘特圖

    section 執行任務
    參考資料與收集      :done,    t1, 2024-10-3, 7d
    系統介面設計        :active,  t2, after t1, 21d
    軟體程式撰寫        :        t3, after t2, 30d
    系統測試           :        t4, after t3, 14d
    計畫修改與完成      :        t5, after t4, 7d
```

## 組員任務hw2
| 組員   | 任務   |
| ------- | ------- | 
| 李昆達   | 程式撰寫   |
| 張鈞瑋   | 程式撰寫   | 
| 田翔銘   | 系統測試   | 
| 徐毓廷   | 介面設計   | 
| 田先勛   | 系統測試   | 

### PERT/CPM hw2
```mermaid
graph TD;
    t1[參考資料與收集: 7d] --> t2[系統介面設計: 21d]
    t2 --> t3[軟體程式撰寫: 30d]
    t3 --> t4[系統測試: 14d]
    t4 --> t5[計畫修改與完成: 7d]
```
## 功能性與非功能性需求 hw3
>功能性需求：
 <br>1.用戶註冊：作業人員需要輸入帳號密碼方可登入頁面。
<br>2.貨料資訊：頁面會依照作業人員行爲顯示該貨架或貨格的資訊
<br>3.操作警示：若作業人員放置錯誤地方，頁面會顯示警告頁面提醒人員<br>
>非功能性需求：
 <br>1.效能：系統的頁面加載時間應該不超過 5 秒。
 <br>2.安全性：用戶資料應該以加密的方式儲存，確保安全
 <br>3.承載性：系統要確保流量的穩定，避免應系統線上同時太多人所造成的壅塞狀況

## 功能分解圖FDD hw3
```mermaid
graph TD
    A[倉儲管理系統] --> B[入料]
    A --> C[撿料]
    A --> D[組裝]


    B --> B1[料件編號]
    B --> B2[料件名稱]
    B --> B3[料件位置]
    B --> B4[剩餘數量]

    C --> C1[撿料單號]
    C --> C2[項目數量]
    C --> C3[部門]

    D --> D1[所需料件]
    D --> D2[組裝進度]
    D --> D3[示意圖片]
```

## 使用案例圖 hw3

![409EFE85-0F2F-434D-A89C-EC004912BEF4](https://github.com/user-attachments/assets/513e6d42-6f66-4cdc-900d-5bf1bd062769)

# 使用案例 1：用戶註冊與登入

### 說明：
作業人員必須輸入帳號和密碼，才能登入系統進行操作。

### 主要流程：
1. 作業人員輸入帳號及密碼。
2. 系統驗證用戶的身份。
3. 驗證成功後，系統顯示倉儲管理系統的首頁。


### 例外情況：
- 若帳號或密碼輸入錯誤，系統顯示錯誤提示，並要求重新輸入。
# 使用案例 2：貨料資訊查詢

### 說明：
作業人員根據自己的行為（如入料或撿料）查詢特定貨架或貨格的貨料資訊。

### 主要流程：
1. 作業人員選擇入料、撿料或組裝操作。
2. 系統自動顯示該操作相關的貨架或貨格資訊：
   - **入料**：顯示料件編號、料件名稱、料件位置及剩餘數量。
   - **撿料**：顯示撿料單號、項目數量及部門。
   - **組裝**：顯示所需料件、組裝進度及示意圖片。

### 例外情況：
- 若無法查詢到對應的貨料資訊，系統提示「無對應資料」。

# 使用案例 3：操作警示

### 說明：
作業人員在放置料件時，若放置錯誤的貨架或貨格，系統會自動警示。

### 主要流程：
1. 作業人員放置料件至特定位置。
2. 系統檢查料件的放置位置是否正確。
3. 若正確，系統無提示並繼續。
4. 若錯誤，系統顯示警告頁面，提醒作業人員重新確認放置位置。

### 例外情況：
- 如果系統無法自動檢測放置位置，系統會提示作業人員進行人工檢查。
### 系統環境圖 (System DFD)
![image 2](https://github.com/user-attachments/assets/d135b957-af07-4f70-861b-2d810bbe7ed5)

### 資料流向圖0 (DFD 0)
![image](https://github.com/user-attachments/assets/04be83ee-307d-4d86-beb7-8cc8de39b147)
### 類別圖
![messageImage_1730102957497](https://github.com/user-attachments/assets/49d0c75a-fd05-414a-9c74-5264a04b90b1)

## 使用案例 1：用戶註冊與登入
### 循序圖
```mermaid
sequenceDiagram
    participant User as 作業人員
    participant System as 系統

    User->>System: 輸入帳號和密碼
    System-->>User: 驗證帳號和密碼
    alt 成功
        System-->>User: 登入成功，顯示首頁
    else 失敗
        System-->>User: 顯示錯誤提示
    end
```
### 活動圖
```mermaid
flowchart TD
    A[開始] --> B[輸入帳號和密碼]
    B --> C{帳號和密碼是否正確？}
    C -- 是 --> D[顯示首頁]
    C -- 否 --> E[顯示錯誤提示]
    E --> B
    D --> F[結束]
```
## 使用案例 2：貨料資訊查詢
### 循序圖
```mermaid
sequenceDiagram
    participant User as 作業人員
    participant System as 系統

    User->>System: 選擇操作（入料/撿料/組裝）
    System-->>User: 顯示相關貨料資訊
    alt  資訊存在
        System-->>User: 顯示貨架/貨格資訊
    else 資訊不存在
        System-->>User: 顯示「無對應資料」提示
    end
```
### 活動圖
```mermaid
flowchart TD
    A[開始] --> B[選擇操作（入料/撿料/組裝）]
    B --> C[顯示貨料資訊]
    C --> D{資料是否存在？}
    D -- 是 --> E[顯示貨架/貨格資訊]
    D -- 否 --> F[顯示「無對應資料」提示]
    E --> G[結束]
    F --> G
```
## 使用案例 3：操作警示
### 循序圖
```mermaid
sequenceDiagram
    participant User as 作業人員
    participant System as 系統

    User->>System: 放置料件至特定位置
    System-->>System: 檢查放置位置
    alt 正確位置
        System-->>User: 無提示
    else 錯誤位置
        System-->>User: 顯示警告頁面
    end
```
### 活動圖
```mermaid
flowchart TD
    A[開始] --> B[放置料件至特定位置]
    B --> C[檢查放置位置]
    C --> D{位置是否正確？}
    D -- 是 --> E[無提示]
    D -- 否 --> F[顯示警告頁面]
    E --> G[結束]
    F --> G
```

### 分鏡板：
![圖片1](https://github.com/user-attachments/assets/b24b8ce5-7e61-4109-af29-c317a1b46637)![圖片2](https://github.com/user-attachments/assets/81247e9c-a983-4ea7-b59f-5c8e399930cf)
![圖片3](https://github.com/user-attachments/assets/3bbfe719-e54e-426c-99ca-2815b3009f04)![圖片4](https://github.com/user-attachments/assets/84333f0d-8518-40b9-b619-0a7f95794348)
![圖片5](https://github.com/user-attachments/assets/a7f66cab-1b4c-4de0-bb6a-045f70db3e56)!
![圖片6](https://github.com/user-attachments/assets/8bd7ba7f-48b6-4d0b-bb46-af82f964dabe)![圖片7](https://github.com/user-attachments/assets/1120ff5b-227b-43f2-a7ba-180ea2ebd99d)
### 說明：
1. 系統提供安全的登錄界面，用戶需輸入帳號和密碼才能訪問系統。  
2. 主頁面展示了各種料件的庫存水平，並以顏色顏色標籤（紅色、黃色、綠色）區分狀態（如充足、高庫存、不足）。  
3. 提供快速查看庫存狀況的功能，幫助管理者及時調整庫存策略。  
4. 顯示撿料單號、進料時間、撿料人員、部門、項目數量和狀態。  
5. 列出 CPU 的進貨記錄，包含數量、日期、單價和總價。  
6. 操作完成後，系統會自動返回主頁。 

### ERD
![image](https://github.com/tienxm/MRSystem/blob/main/%E6%9C%AA%E5%91%BD%E5%90%8D.jpg)
