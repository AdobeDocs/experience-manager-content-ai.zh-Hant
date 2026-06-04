---
title: AEM Content AI概觀
description: 瞭解什麼是AEM Content AI、其重要原因，以及如何開始為您的AEM as a Cloud Service環境啟用和控制它。
topic: Overview
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM Content AI，總覽，內容來源，語意搜尋，贏取， Cloud Manager
source-git-commit: 9b3c63be1aa95339086ee5994cd4dd7cdfa7e746
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---


# AEM Content AI — 簡介

## 智慧型內容，透過設計提供AI功能 {#ai-ready}

客戶開始透過AI與品牌互動，之後再造訪網站。聊天助理、AI總覽、代理、交談式搜尋、AI服務人員 — 所有這些人員都會代表品牌擷取、摘要及呈現品牌內容。他們所說的內容，取決於他們能觸及的內容是否準確、是否即時以及是否與品牌合作。
這就是為AEM Content AI打造的轉移。它將品牌內容視為AI體驗執行的基礎事實，並為AEM客戶提供工具，讓作者端更快速地建立基礎事實，並在發佈端為面向消費者的AI驅動體驗提供簡潔的呈現。

**在作者端**，在核准的品牌來源中建立AEM Content AI。 AI輔助撰寫、跨現有頁面內容、片段和資產的自然語言探索，以及品牌感知世代，讓團隊不需離開AEM，也不必偏離已核准的專案，即可為新對象、地區和頻道產生變數。

**在發佈端**，相同的內容會結構化、受控管且可定址，以供AI使用。 片段、中繼資料、分類法和核准的來源會以擷取系統、代理和對話介面可信賴使用的形狀顯示，因此當AI代表品牌時，它會說出品牌的真相。

### 對AEM客戶的意義 {#what-it-means}

核准內容是品牌避免幻覺的防禦措施。當AI以受管理的AEM內容為根據時，依預設會保持準確、最新和符合品牌規範。
製作跟上了AI時代的需求。團隊會產生副本和影像，以供製作體驗中的更多對象和時刻使用 — 從核准的來源繪圖而不是從空白開始。
探索的運作方式與人和機器實際詢問的方式相同。跨資產、片段、頁面和表單的自然語言、意圖型搜尋可將現有內容轉換為可重複使用的供應專案。
Personalization可透過重複使用而非複製進行擴充。受管控的元件會重新組合成變體，而不是乘以不受追蹤的副本。
發佈管道現在包含AI表面。內容會以人類、代理人和人工智慧媒介的體驗都可以使用的形狀傳送，沒有各自的單獨管道。

**更重要的一點：現有的信任品牌內容比以往更有價值。 每個已存在於AEM中的已核准片段、資產和頁面都成為AI驅動體驗所依賴的基本事實，而AEM Content AI讓該程式庫可重複使用、可探索，並準備就緒以支援後續工作。**

## AEM Content AI總覽 {#at-a-glance}

AEM Content AI的結構為四層棧疊，每個層棧疊在底下的一個層上，從基礎的受信任內容到頂層支援的代理式體驗。

![四層AEM Content AI架構棧疊的圖表：基礎的Content AI來源、Content AI Foundation Services、Agentic Content Orchestration以及頂端的Agentic Experience Orchestration](../assets/content-ai-four-layer-architecture-stack.png)

*自下而上讀取棧疊 — 從基礎的信任內容到最上方的代理程式體驗。*

1. Content AI來源
內容來源是AEM Content AI中連線到受信任內容主體的受管實體。 內容Source可參考AEM控管的內容型別（例如資產、內容片段、頁面、表單、中繼資料和分類法）以及非AEM來源（例如協力廠商網站、知識庫或檔案入口網站）。 每個內容Source都會自動向量化，並在語義上擴充為電源擷取、接地和對話式AI體驗。 只需定義一次內容來源，並透過內建的自動更新與時效性，在各個Content AI API中重複使用。

1. Content AI基礎服務
API和服務，可在品牌內容的環境中啟用語意智慧和創作AI。 使用Content AI來源時，這些服務會有效擷取、產生、品牌感知變異和最佳化，全都以客戶核准的內容為基礎。

1. 代理式內容協調
透過自然語言將使用案例驅動的內容需求轉換為協調動作的MCP和代理。 此層可讓作者和其他代理程式以純文字描述他們所需的內容，並協調正確的基礎服務以履行此功能。

1. Agentic Experience Orchestration
當智慧型品牌內容大規模符合AI需求時，就會湧現出創新的使用案例。 AEM解決方案本身建置在這些基本服務上，而客戶可以直接使用相同的API來建置他們自己的代理式體驗，涵蓋他們自己的內容。 從AI支援的內容供應鏈到對話式使用者歷程，此層級代表控管內容成為競爭優勢。

這些層是透過設計連線的：每個AI服務都從內容基礎中提取，並且產生的所有內容都會流回相同的控管系統 — 因此，作者端的建立和發佈端的傳遞會共用一個信任來源。

## AEM Content AI運作中 {#action}

開始使用Content AI整合需要兩項工作：

### &#x200B;1. 為您的AEM環境啟用Content AI {#enable}

**先決條件：**&#x200B;開始使用Content AI之前，您需要設定範圍至您AEM as a Cloud Service環境的API認證。 請參閱[設定Adobe Developer Console專案](setup-adc-project.md)。

### &#x200B;2. 控制您的Content AI來源 {#control}

設定並管理您的Content AI來源，以啟用AI型體驗，請參閱[控制您的內容來源](contentsources.md)。

## 瞭解Content AI API  {#apis}

探索AEM Content AI的功能廣度，這些API充分展示平台的潛力。 請參閱[Content AI API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/)。
