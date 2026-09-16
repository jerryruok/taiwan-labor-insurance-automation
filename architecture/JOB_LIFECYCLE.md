# Job Lifecycle

## 1. Job 的角色

在 LaborInsuranceAutomation 中，Job 代表一次需要由 Automation Client 執行的工作。

Job 不只是單純的「執行指令」，同時也是系統追蹤：

* 工作來源
* 執行狀態
* 執行歷程
* Automation Version
* 最終結果

的主要單位。

---

## 2. 基本流程

整體流程可以簡化為：

```text
Local Data
    │
    ▼
Windows Client
    │
    ▼
Request Job
    │
    ▼
Server Validation
    │
    ▼
Authorized Job
    │
    ▼
Automation Execution
    │
    ▼
Execution Result
```

Windows Client 負責發現需要處理的工作。

Server 則負責確認該工作是否符合執行條件，並建立或取得對應的 Job。

---

## 3. Server Authority

Job 的重要狀態由 Server 統一管理。

Windows Client 的主要責任是：

* 執行工作
* 回報執行結果
* 回報執行過程中的事實

Server 則負責維護整體 Job 狀態。

```text
Windows Client
      │
      │ Report Execution Result
      ▼
    Server
      │
      └── Maintain Job State
```

這樣可以避免不同 Client 因版本或執行環境差異，而各自產生不同的狀態判斷。

---

## 4. Job 與 Execution Attempt

一次 Job 不一定只會有一次實際執行。

因此系統將：

```text
Job
```

與：

```text
Execution Attempt
```

分開管理。

概念上：

```text
Job
 ├── Attempt 1
 ├── Attempt 2
 └── Attempt ...
```

Job 代表：

> 要完成的工作。

Attempt 代表：

> 某一次實際執行這份工作的紀錄。

這樣可以保留完整的執行歷程，而不是只保存最後一次結果。

---

## 5. Automation Version Traceability

每一個 Job 都會與對應的 Automation Version 建立關聯。

因此 Automation 流程即使後續更新，歷史 Job 仍能知道當時使用的是哪一個流程版本。

例如：

```text
Automation V1
      │
      └── Job A

Automation V2
      │
      ├── Job B
      └── Job C
```

這讓系統具備歷史追蹤與版本辨識能力。

---

## 6. Duplicate Work Control

在實際 Automation 環境中，同一份來源資料可能因為：

* Client 重啟
* 重複掃描
* 網路異常
* 使用者重新執行

而再次被發現。

因此系統需要能辨識：

> 這是一份已存在的工作，還是一份新的工作。

同時，如果來源內容真的發生改變，也必須能被視為新的工作版本。

實際識別規則由系統內部管理。

---

## 7. Execution Recovery

Automation 執行過程可能受到：

* 網路中斷
* Browser 異常
* Client 關閉
* 外部系統暫時不可用

等因素影響。

因此 Job Lifecycle 不假設每一個工作都會一次完成。

系統會保留必要的執行狀態與歷程，讓後續處理可以依照目前已知狀態進行。

---

## 8. Safe Retry Principle

並不是所有 Automation 失敗都適合立即重新執行。

如果系統無法確認前一次操作對外部系統造成的實際結果，直接再次執行可能產生：

* 重複處理
* 重複提交
* 不一致狀態

因此 LaborInsuranceAutomation 的原則是：

> 是否可以重新執行，必須建立在可確認的工作狀態上，而不是單純因為程式發生錯誤就直接重試。

實際判定規則屬於系統內部實作。

---

## 9. Execution History

Job Lifecycle 會保留工作與執行歷程，讓系統可以回答：

* 這份工作是否執行過
* 執行了幾次
* 最後結果是什麼
* 當時使用哪個 Automation Version
* 是否曾經發生執行異常

這些資訊除了提供系統控制之外，也能作為後續問題追蹤與維運依據。

---

## 10. Job Lifecycle 的核心目標

Job Lifecycle 的目的不是單純建立一筆 Queue 資料。

它主要解決的是：

```text
Work Discovery
      │
      ▼
Authorization
      │
      ▼
Execution
      │
      ▼
Tracking
      │
      ▼
Recovery
      │
      ▼
Final Result
```

讓每一次 Automation 工作都具備：

* 可識別
* 可追蹤
* 可恢復
* 可版本追溯

的執行生命週期。
