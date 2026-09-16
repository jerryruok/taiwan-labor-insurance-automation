# LaborInsuranceAutomation

## 1. 產品概述

LaborInsuranceAutomation 是一套協助處理重複性勞保作業的自動化平台。

系統的目標不是單純模擬人工點擊，而是將日常勞保作業轉換成可以：

* 管理
* 執行
* 追蹤
* 維護

的自動化工作流程。

---

## 2. 解決的問題

在實際的人資與會計作業中，勞保相關操作往往具有以下特性：

* 操作頻率高
* 重複性高
* 需要處理大量資料
* 依賴外部系統
* 執行失敗後需要確認處理狀態
* 外部流程可能隨時間改變

當作業量增加後，單純依賴人工處理容易增加：

* 重複輸入
* 作業遺漏
* 操作錯誤
* 執行狀態不清楚
* 問題追蹤成本
* 長期維護成本

LaborInsuranceAutomation 希望將這些問題交由系統化方式管理。

---

## 3. 主要能力

### Automation Execution

Windows Client 負責執行實際 Automation 工作。

Client 提供通用執行能力，讓不同業務流程可以透過平台管理，而不是將所有操作直接寫死在應用程式中。

---

### Job Management

每一份需要執行的工作都可以被系統追蹤。

系統可以保留：

* 工作狀態
* 執行歷程
* 執行結果
* Automation Version

讓 Automation 不再只是一次性的背景操作。

---

### Centralized Management

Automation 流程與 Client 可以由平台集中管理。

這讓流程調整、Client 維護與執行追蹤不需要分散在不同使用者環境中處理。

---

### Client Lifecycle Management

Windows Client 除了執行 Automation，也包含：

* 本機設定
* 版本管理
* 更新
* 執行狀態回報

讓 Client 能夠長期部署與持續維護。

---

## 4. 系統組成

LaborInsuranceAutomation 主要由三個部分組成。

### Windows Client

安裝於實際執行 Automation 的使用者環境。

主要負責：

* 發現需要處理的工作
* 執行 Automation
* 管理本機設定
* 回報執行結果
* Client 維護

---

### Cloud Platform

提供：

* Client 授權
* Job Management
* Automation Management
* Execution Tracking
* Version Management

並作為 Client 與 Web 之間的核心服務。

---

### Web

Web 提供：

* 公開產品資訊
* 客戶操作介面
* 內部管理與維運功能

---

## 5. 與一般 Browser Macro 的差異

一般 Browser Macro 通常著重於：

```text id="uxdw9v"
執行一連串操作
```

LaborInsuranceAutomation 則同時管理：

```text id="sikhnx"
Automation Execution
        +
Job Management
        +
Execution Tracking
        +
Version Management
        +
Client Management
```

因此系統不只關心：

> Automation 能不能跑。

也關心：

> 這份工作有沒有執行、執行結果是什麼，以及之後是否還能被追蹤與維護。

---

## 6. Reliability

外部系統 Automation 在實際執行時可能遇到：

* 網路異常
* Browser 異常
* Client 中斷
* 外部服務暫時不可使用
* 外部流程變更
* 執行狀態無法立即確認

因此系統設計不假設每一次 Automation 都一定可以一次完成。

LaborInsuranceAutomation 會保留必要的執行資訊，讓工作可以被持續管理與追蹤。

當系統無法可靠確認目前狀態時，以避免產生不可預期操作為優先。

---

## 7. Security

系統設計遵循以下基本原則：

* 敏感資訊盡可能保留於使用者端
* 本機敏感資訊不以明文形式保存
* Server 不收集不必要的本機資料
* 重要工作狀態由平台統一管理
* Automation 執行具有歷史與版本追蹤能力

---

## 8. 產品定位

LaborInsuranceAutomation 的定位不是單一腳本或一次性的 RPA 工具。

產品希望建立的是：

> **可管理、可追蹤、可維護的勞保作業自動化平台。**

核心價值在於將外部系統操作從單純的「自動點擊」，轉換成具有完整工作生命週期的 Automation。

---

## 9. 目前開發階段

目前專案正在持續開發 Generic Automation Platform。

現階段主要方向包括：

* Automation Runtime
* Client Configuration
* Client Lifecycle Management
* Execution Reliability
* Production Workflow Validation

產品功能與流程會依實際使用與驗證結果持續調整。

---

## 10. Disclaimer

LaborInsuranceAutomation 為獨立開發之軟體產品。

本產品並非政府機關官方系統，亦不代表任何政府機關提供、維護、認可或背書。
