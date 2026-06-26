---
title: AEM Content AI 概觀
description: 了解什麼是 AEM Content AI、其為何重要，以及如何開始為您的 AEM as a Cloud Service 環境啟用和控制之。
topic: Overview
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM Content AI、概觀、內容來源、語意搜尋、贏取、Cloud Manager
source-git-commit: 2ff1bbdd3ff224e2a6b389243c78af5fd228d5ee
workflow-type: ht
source-wordcount: '716'
ht-degree: 100%

---


# AEM Content AI - 簡介

## 智慧型內容，透過設計提供 AI 功能 {#ai-ready}

客戶甚至在造訪網站之前，便開始透過 AI 與品牌互動。所有聊天助理、AI 概觀、代理、交談式搜尋、AI 服務人員都會進行品牌擷取、摘要，並且呈現品牌內容。他們所說的內容是否準確、即時以及符合品牌形象，取決於他們所能觸及的內容。
這就是為 AEM Content AI 建置的轉移。其將品牌內容視為 AI 體驗執行時用到的基礎事實，並為 AEM 客戶提供工具，讓作者端更快速地建立基礎事實，並在發佈端為面向消費者的 AI 驅動體驗提供簡潔的呈現。

**在作者端**，AEM Content AI 以核准的品牌來源作為創作的依據。 AI 輔助創作、各現有頁面內容、片段和資產的自然語言探索，以及品牌感知生成，讓團隊不需離開 AEM，也不會偏離已核准的部分，即可為新客群、地區和管道產生變化版本。

**在發佈端**，相同的內容會結構化、受控管且可定址，以供 AI 使用。 片段、後設資料、分類法和核准的來源會以檢索系統、代理和對話介面可信賴使用的外觀顯示，因此當 AI 代表品牌時，會說出品牌上的真相。

### 對 AEM 客戶的意義 {#what-it-means}

核准內容是品牌避免幻覺的防禦措施。當 AI 以受管控的 AEM 內容為根據時，依預設會保持準確、最新和符合品牌形象。
製作跟上了 AI 時代的需求。團隊會產生副本和影像，以供更多客群和製作體驗中的更多時機點使用，得以從核准的來源繪圖而不是從空白開始。
Discovery 的運作方式與人和機器實際詢問的方式相同。各個資產、片段、頁面和表單的自然語言和以意圖為基礎的搜尋可將現有內容轉換為可重複使用的內容供應。
個人化可透過重複使用而非複製進行擴充。受管控的元件會重新組合成變體，而不是增加成無法追蹤的副本數量。
發佈管道現在包含 AI 表面。內容會以人類、代理和 AI 中介的體驗都可以使用的外觀傳遞，而各自無需單獨的管道。

**更重要的一點：現有受信任的品牌內容比以往更有價值。 每個已存在於 AEM 中的已核准片段、資產和頁面都成為 AI 驅動體驗所依賴的基本事實，而 AEM Content AI 讓該資料庫可重複使用、可探索，並準備就緒以支援後續工作。**

## AEM Content AI 一覽 {#at-a-glance}

AEM Content AI 的結構為四層堆疊，每層皆建置在底下的一層上，從基礎的受信任內容到頂層支援的代理式體驗。

![四層 AEM Content AI 架構堆疊的圖表：Content AI 來源作為基礎、Content AI 基礎服務、代理式內容協調流程和代理式體驗協調流程位居頂層](../assets/content-ai-four-layer-architecture-stack.png)

*自下而上讀取堆疊 - 從基礎的信任內容到其支援的最頂層之代理式體驗。*

1. Content AI 來源
內容來源是 AEM Content AI 中連線到獲信任內容主體的受管理實體。 內容來源可參考 AEM 控管的內容類別，例如資產、內容片段、頁面、表單、後設資料和分類法，以及如第三方網站、知識庫或文件入口網站等非 AEM 來源。 每個內容來源都會自動向量化，並在語意上擴充，以強化檢索性、扎實和對話式 AI 體驗。 只需定義一次內容來源，並透過內建的自動保持內容新鮮度和更新，在各個 Content AI API 中重複使用。

1. Content AI 基礎服務
API 和服務，可在品牌內容的背景中啟用語意智慧和生成式 AI。 使用 Content AI 來源時，這些服務可促進檢索、生成、品牌感知變化和最佳化，全部以客戶核准的內容為基礎。

1. 代理式內容協調流程
透過自然語言，MCP 與代理可將以使用案例為導向的內容需求，轉化為協調的動作。 此層級可讓作者和其他代理以純文字描述他們所需的內容，並協調正確的基礎服務以實現此功能。

1. 代理式體驗協調流程
若智慧型品牌內容大規模符合 AI 需求，就會湧現出創新的使用案例。 AEM 解決方案本身就是建構在這些基本服務上，而客戶可以直接使用相同的 API，在自己的內容之上建構他們的代理式體驗。 從 AI 驅動的內容供應鏈到對話式使用者歷程，此層級代表控管內容成為競爭優勢。

這些層級是透過設計連線的：每個 AI 服務都是從內容基礎中提取，並且產生的所有內容都會流回相同的控管系統。因此，作者端的建立和發佈端的傳遞會共用一個信任來源。

## AEM Content AI 運作中 {#action}

開始使用 Content AI 整合涉及兩項工作：

### &#x200B;1. 為您的 AEM 環境啟用 Content AI {#enable}

**先決條件：**&#x200B;開始使用 Content AI 之前，您需要將 API 認證設定範圍至您的 AEM as a Cloud Service 環境。 請參閱[設定 Adobe Developer Console 專案](setup-adc-project.md)。

### &#x200B;2. 控制您的 Content AI 來源 {#control}

設定並管理您的 Content AI 來源，以啟用基於 AI 的體驗，請參閱[控制您的內容來源](contentsources.md)以取得更多資訊。

## 了解 Content AI API  {#apis}

探索 AEM Content AI 的功能廣度，這些 API 充分展示平台的潛力。 請參閱 [Content AI API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/)。
