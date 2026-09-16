# 系統架構

## 1. 系統目標

LaborInsuranceAutomation 是一套用於協助處理重複性勞保作業的自動化平台。

系統不是單純將瀏覽器操作流程寫死在 Windows Client 中，而是將：

* Client 執行環境
* 自動化流程
* 工作管理
* 使用授權
* 執行紀錄
* Client 維護

分成不同職責。

這種設計讓自動化流程、Client 與 Server 可以各自演進，同時保留集中管理與執行追蹤能力。

---

## 2. 整體架構

```text
┌───────────────────────────────┐
│             Web               │
│                               │
│  Public / User / Admin        │
└───────────────┬───────────────┘
                │ HTTPS
                ▼
┌───────────────────────────────┐
│              API              │
│                               │
│ Authorization                 │
│ Job Management                │
│ Automation Management         │
│ Client Management             │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│          PostgreSQL           │
└───────────────────────────────┘


┌───────────────────────────────┐
│        Windows Client         │
│                               │
│ Local Data Discovery          │
│ Execution Coordinator         │
│ Automation Runtime            │
│ Browser Integration           │
│ Client Update                 │
└───────────────┬───────────────┘
                │ HTTPS
                ▼
             Cloud API
```

---

## 3. Web

Web 介面依使用情境分成三個區域。

### Public

提供一般訪客查看：

* 產品介紹
* 功能說明
* 使用方式
* 系統需求
* 常見問題

### User

提供客戶進行日常操作與查看系統資訊，例如：

* Client 管理
* 執行狀態
* 執行紀錄
* 授權資訊

### Admin

提供內部系統管理與維運功能。

---

## 4. API

API 是 Web、Windows Client 與資料層之間的核心服務。

主要負責：

* 使用者與 Client 授權
* 工作管理
* Automation 管理
* 執行狀態與歷程
* Client 版本管理

重要的工作狀態由 Server 統一管理，避免不同 Client 各自維護不一致的狀態。

---

## 5. Windows Client

Windows Client 安裝於實際執行自動化工作的電腦。

主要負責：

* 發現需要處理的本機資料
* 取得經授權的工作
* 執行自動化流程
* 管理本機設定
* 回報執行結果
* Client 更新

Client 採用通用 Automation Runtime 設計，不將所有業務流程直接寫死在應用程式中。

---

## 6. Automation 架構

LaborInsuranceAutomation 將「執行能力」與「實際流程」分離。

```text
Automation Flow
       │
       ▼
Windows Client
       │
       ▼
Automation Runtime
       │
       ▼
Browser Integration
       │
       ▼
External System
```

Windows Client 提供通用執行能力。

實際業務流程由系統集中管理，而不是散落在不同 Client 中。

這種設計可以降低外部流程改變時對 Client 本身的影響。

---

## 7. 技術架構

目前主要技術包括：

* .NET 8
* ASP.NET Core
* Entity Framework Core
* PostgreSQL
* React
* Windows Desktop Application
* Browser Automation
* Google Cloud

---

## 8. 安全設計原則

系統設計遵循以下基本原則：

* 敏感資訊盡可能留在使用者端
* 敏感資料不以明文形式保存
* Server 不保存不必要的使用者本機資訊
* Automation 執行具有版本與歷程追蹤能力
* 重要工作狀態由 Server 統一管理
* 遇到無法確認的執行狀態時，以安全停止為優先

實際的外部系統操作方式、判定規則與安全處理細節不屬於公開文件範圍。

---

## 9. 設計原則

LaborInsuranceAutomation 將主要責任分成三個部分：

```text
Windows Client
    │
    │ 執行 Automation
    ▼
Automation Layer
    │
    │ 管理流程
    ▼
Cloud Platform
    │
    └── 管理授權、工作與執行狀態
```

核心目標是建立一套：

> 可管理、可追蹤、可維護的勞保作業自動化平台。

---
