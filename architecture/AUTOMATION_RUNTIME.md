# Automation Runtime

## 1. 設計目標

Automation Runtime 是 LaborInsuranceAutomation Windows Client 中負責執行自動化工作的核心元件。

設計上將：

```text
執行能力
```

與：

```text
實際業務流程
```

分離。

Windows Client 提供通用的 Automation 執行環境，而實際流程由系統集中管理。

這樣可以降低外部系統流程改變時，直接修改並重新部署每一台 Windows Client 的需求。

---

## 2. 整體概念

```text
Managed Automation Flow
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

Runtime 的責任是提供穩定且一致的執行環境。

實際業務操作內容則由 Automation Layer 管理。

---

## 3. Generic Runtime

Runtime 採用通用化設計。

它本身不應與單一業務流程強耦合，而是提供自動化執行所需要的基礎能力。

例如高階概念上包含：

* 頁面操作
* 資料輸入
* 狀態確認
* 檔案處理
* 流程控制

這些能力可以組成不同的 Automation Flow。

Public Repository 不公開實際執行指令格式、流程定義格式或外部網站操作內容。

---

## 4. Runtime 與業務流程分離

如果所有流程直接寫在 Client 程式中：

```text
Windows Client
 ├── Business Process A
 ├── Business Process B
 ├── Business Process C
 └── Business Process D
```

當外部流程改變時，Client 程式通常也需要跟著修改。

LaborInsuranceAutomation 採用的方向是：

```text
Windows Client
 └── Generic Automation Runtime

Automation Platform
 └── Managed Automation Flow
```

讓 Client Runtime 與實際業務流程可以各自演進。

---

## 5. Centralized Automation Management

Automation 流程由系統集中管理，而不是散落在不同 Client 環境。

這樣可以提供：

* 統一流程管理
* 版本追蹤
* 執行一致性
* 歷史追蹤
* 集中維護

Client 在執行工作時取得適合該工作的 Automation Flow，再由 Runtime 負責執行。

---

## 6. Version Awareness

Automation Flow 具有版本概念。

這讓系統可以保留：

* 現行流程
* 歷史流程
* 不同工作實際使用的流程版本

因此外部流程更新後，歷史工作仍能保留原本的執行脈絡。

版本管理的詳細機制不在本文件展開。

---

## 7. Runtime Readiness

Automation 不應在執行環境尚未準備完成時直接開始工作。

Runtime 在正式執行前會確認必要的執行條件是否可用。

若執行環境無法安全開始工作，系統應停止該次執行流程，而不是強制繼續。

---

## 8. Safe Execution Principle

外部系統自動化可能遇到：

* 頁面狀態改變
* 網路異常
* Browser 中斷
* 外部服務暫時不可用
* 無法確認目前操作狀態

Runtime 的核心原則是：

> 當系統無法可靠確認目前狀態時，不應猜測下一個操作。

這可以降低在外部系統上產生不可預期副作用的風險。

具體判定與處理規則屬於產品內部實作。

---

## 9. Execution Observability

Automation Runtime 不只是執行操作，也必須讓系統知道執行結果。

因此 Runtime 執行過程會與 Job Management 整合，讓系統能夠追蹤：

* 工作是否開始
* 工作是否完成
* 執行是否發生異常
* 使用哪個 Automation 版本

實際執行資料與錯誤分類方式不在 Public Repository 公開。

---

## 10. Runtime 的角色

Automation Runtime 的角色可以簡化為：

```text
Automation Platform
        │
        │ 提供要執行的流程
        ▼
Windows Client
        │
        │ 提供執行環境
        ▼
Automation Runtime
        │
        │ 執行工作
        ▼
External System
```

Runtime 關注：

> 如何可靠執行 Automation。

Automation Platform 關注：

> 要執行什麼 Automation。

兩者保持分離，是整體架構的重要設計原則。

---
