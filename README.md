# Labor Insurance Automation

**勞保自動化服務**

Labor Insurance Automation 是一套協助企業處理勞保相關作業的自動化服務。透過 Web 操作介面與企業端 Client，降低重複人工操作、減少輸入錯誤，並提供一致的作業流程與執行記錄。

> **目前狀態：持續開發中／Preview 預覽階段**

## 官方連結

- [產品網站](https://laborinsuranceautomation-134851032186.asia-east1.run.app/)
- [安全性說明](https://laborinsuranceautomation-134851032186.asia-east1.run.app/security)
- [隱私權政策](https://laborinsuranceautomation-134851032186.asia-east1.run.app/privacy)
- [服務條款](https://laborinsuranceautomation-134851032186.asia-east1.run.app/terms)
- [聯絡我們](https://laborinsuranceautomation-134851032186.asia-east1.run.app/contact)
- Email：minotjb@gmail.com

## 產品定位

Labor Insurance Automation 將勞保相關作業拆分為：

1. Web 操作介面
2. 企業端自動化 Client
3. 自動化執行與作業追蹤

使用者可透過簡潔的 Web 介面操作與查看作業；經核准的自動化工作則由企業端 Client 執行。

## 主要功能

- **勞保作業自動化**：將重複性的操作流程標準化並自動執行。
- **企業端 Client**：自動化工作由企業指定電腦上的 Client 執行。
- **作業狀態追蹤**：提供作業執行狀態與歷史記錄。
- **多公司管理**：同一企業帳戶可管理不同公司或作業單位。
- **團隊協作規劃**：產品架構規劃支援多位同事以各自帳號共同使用企業帳戶；完整成員邀請功能仍在開發中。
- **Client 配對**：Web 帳戶與企業端 Client 可透過安全的配對流程建立連線。
- **Client 自動更新**：支援 Client 版本更新與更新流程管理。

## 使用流程

### 1. 建立帳號與企業帳戶

使用者於 Web 建立帳號及企業帳戶。

### 2. 安裝 Client

在企業指定的 Windows 電腦上安裝 Labor Insurance Automation Client。

### 3. 配對 Client

使用 Web 與 Client 的配對流程建立企業帳戶與 Client 的連線。

### 4. 設定作業環境

完成必要的企業端本機設定。

### 5. 執行勞保作業

使用者從 Web 選擇所需作業，由企業端 Client 執行自動化流程。

### 6. 查看結果

於 Web 查看作業狀態與歷史記錄。

## 企業與團隊使用方式

每位使用者應使用自己的帳號。一個企業帳戶可用來管理公司的勞保作業，並規劃支援多位同事共同參與。

未來的成員邀請功能將允許企業管理者透過 Email 邀請其他同事加入同一企業帳戶。使用者也可在產品架構上參與不同企業帳戶，而不需要共用帳號密碼。

## 系統概觀

```text
使用者
  │
  ▼
Web Application
  │
  ▼
Automation Service
  │
  ▼
Enterprise Client
  │
  ▼
Approved Automation Flow
```

- **Web**：提供使用者操作、狀態查看與管理介面。
- **Service**：負責作業管理與 Client 協調。
- **Client**：在企業端執行自動化工作。

## 安全性

- 正式環境的 Web 流量使用 HTTPS。
- 使用者與內部系統管理及維運功能具有獨立的登入與授權區域。
- 自動化 Client 使用獨立的裝置識別與連線機制。
- 敏感的企業端資料不應顯示於一般 Web 操作介面。
- 系統保留必要的作業狀態與歷史資訊，以利追蹤與維運。

[查看安全性說明](https://laborinsuranceautomation-134851032186.asia-east1.run.app/security)

## 專案狀態

Labor Insurance Automation 目前持續開發中。

目前已建立：

- Web Public Website
- USER Web Application 基礎架構
- Admin Core（內部系統管理與維運功能）
- Client activation / pairing
- Client device identity
- Client local configuration
- automation runtime foundation
- operation/job lifecycle
- Client auto-update

部分 USER 勞保業務作業 API 與完整團隊協作功能仍在開發中。

## 公開文件

| 文件 | 說明 |
| --- | --- |
| [Product Overview](product/PRODUCT_OVERVIEW.md) | 產品定位與整體說明 |
| [System Architecture](architecture/SYSTEM_ARCHITECTURE.md) | 高階系統架構 |
| [Automation Runtime](architecture/AUTOMATION_RUNTIME.md) | 自動化執行架構 |
| [Job Lifecycle](architecture/JOB_LIFECYCLE.md) | 作業生命週期 |
| [Client Update](architecture/CLIENT_UPDATE.md) | Client 更新機制 |
| [Roadmap](product/ROADMAP.md) | 公開開發方向 |

## 免責聲明

本專案為獨立開發之軟體服務，並非勞動部勞工保險局或其他政府機關之官方系統，亦不代表與相關政府機關存在合作、授權或背書關係。

使用者應確保其使用方式符合相關法令、規範及自身組織之授權要求。

## 聯絡方式

產品導入、合作或使用上的問題：

- Email：minotjb@gmail.com
- Website：[https://laborinsuranceautomation-134851032186.asia-east1.run.app/](https://laborinsuranceautomation-134851032186.asia-east1.run.app/)
