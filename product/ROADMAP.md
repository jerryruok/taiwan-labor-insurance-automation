# 開發 Roadmap

LaborInsuranceAutomation 目前仍持續開發中。

本 Roadmap 用於說明產品與技術發展方向，不代表固定發布日期，實際內容可能依實際驗證結果調整。

---

## M1 — Project Foundation

**狀態：完成**

建立專案與基礎技術架構。

主要內容包括：

* Backend Foundation
* Web Foundation
* Windows Client Foundation
* Database Foundation
* Cloud Deployment Foundation

---

## M2 — Customer / Client Foundation

**狀態：完成**

建立客戶、保險單位與 Automation Client 的基本管理能力。

主要內容包括：

* Customer Management
* Insurance Unit Management
* Automation Client Management
* Client Identity
* Execution Authorization

---

## M3 — Job Management Platform

**狀態：完成**

建立 Automation 工作管理與執行追蹤能力。

主要內容包括：

* Job Management
* Execution History
* Automation Version Traceability
* Execution State Management
* Historical Tracking

---

## M4 — Generic Automation Platform

**狀態：進行中**

建立可由 Windows Client 執行的通用 Automation Platform。

主要方向包括：

* Generic Automation Runtime
* Browser Integration
* Centralized Automation Management
* Execution Recovery
* Client Configuration
* Client Update
* Production Workflow Validation

核心目標是：

> 讓 Windows Client 維持通用執行能力，而實際 Automation 流程可以由平台集中管理與持續演進。

---

## M5 — Production / Commercial Readiness

**狀態：規劃中**

讓產品具備正式部署至客戶環境所需的完整能力。

主要方向包括：

* Production Validation
* Installation Experience
* Operational Monitoring
* Customer Onboarding
* Subscription / Entitlement
* Deployment Procedures
* Support Process

實際範圍將依前一階段的實際使用與驗證結果調整。

---

## M6 — Product Experience

**狀態：規劃中**

完善 Web 與整體產品使用體驗。

主要分成三個使用區域：

### Public

提供：

* 產品介紹
* 功能說明
* 使用指南
* FAQ

### User

提供客戶日常操作與資訊查詢。

### Admin

提供內部系統管理與維運功能。

---

## 長期方向

LaborInsuranceAutomation 的長期目標不是只完成單一固定 Automation。

系統希望維持：

```text
Generic Runtime
      +
Centralized Automation Management
      +
Job & Execution Tracking
```

讓 Automation 流程可以持續演進，同時保有：

* 可管理性
* 可追蹤性
* 可維護性
* 長期部署能力

最終目標是建立一套能夠穩定支援實際營運的勞保作業自動化平台。
