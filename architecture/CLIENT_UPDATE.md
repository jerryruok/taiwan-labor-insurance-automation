# Windows Client 更新架構

## 1. 設計目標

LaborInsuranceAutomation Windows Client 具備版本更新能力。

主要目標是降低不同使用者環境的人工維護成本，並確保 Client 可以持續使用相容版本。

對桌面型 Automation Client 而言，長期維運能力與自動化執行能力同樣重要。

---

## 2. 更新概念

整體更新流程可以簡化為：

```text
Windows Client
      │
      ▼
Check Version
      │
      ▼
Retrieve Update
      │
      ▼
Validate
      │
      ▼
Apply Update
      │
      ▼
Restart
```

Client 會確認目前版本與可用版本，在符合更新條件時進行更新。

---

## 3. Client 與更新元件分離

主要應用程式與更新職責彼此分離。

概念：

```text
Windows Client
      │
      ▼
Update Component
      │
      ▼
New Client Version
```

這樣可以避免正在執行中的應用程式直接處理自身程式檔案更新。

---

## 4. Update Validation

更新內容在正式套用之前會進行必要驗證。

驗證的目的包括：

* 確認更新內容完整
* 避免使用不符合預期的更新內容
* 降低更新過程造成應用程式不可用的風險

驗證失敗時，不應直接套用更新。

---

## 5. Durable Configuration

Client 設定與應用程式本體分開保存。

```text
Application
    │
    └── Executable / Runtime

Local Configuration
    │
    └── Durable User Settings
```

這讓 Client 更新時，不需要因為程式版本改變而重新建立使用者設定。

例如：

* Client 本機設定
* 工作目錄設定
* 使用者偏好
* 其他需要跨版本保留的設定

都應與 Application Binary 分離。

---

## 6. Update Safety

Client Update 遵循以下基本原則：

* 不直接套用未完成驗證的更新內容
* 更新流程與主要 Client 執行職責分離
* 使用者設定不依附於單一程式版本
* 更新失敗不應輕易破壞既有可用環境
* 更新結果應具有可追蹤性

---

## 7. 長期維運

Automation Client 可能長期部署在不同使用者環境中。

因此 Client Update 的目的不只是方便安裝新版本，也包括降低：

* 人工到場維護
* 手動更新錯誤
* 不同 Client 版本不一致
* 長期維運成本

讓 Client 可以隨平台持續演進。

---

## 8. Client Update 的角色

Client Update 並不是 Automation Runtime 本身的核心功能，但它是完整產品不可缺少的維運能力。

其角色可以簡化為：

```text
Automation Platform
       │
       ▼
Version Management
       │
       ▼
Windows Client
       │
       ▼
Maintainable Deployment
```

目標是讓 Windows Client 不只是可以執行 Automation，也能夠被持續、安全地維護。
