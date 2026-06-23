---
title: 設定及管理您的 Content AI 來源
description: 了解如何透過設定您的第一個內容來源並觸發贏取，在 Cloud Manager 中設定 AEM Content AI。
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM Content AI、Content AI 來源、贏取、Cloud Manager、Adobe Developer Console
source-git-commit: 2ff1bbdd3ff224e2a6b389243c78af5fd228d5ee
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 72%

---


# 設定及管理您的 Content AI 來源

本指南會逐步帶您了解如何在 Cloud Manager 中設定 Content AI 來源，從滿足必要條件到建立內容來源並確認其已編製索引和可供使用。

## 先決條件 {#prerequisites}

開始之前，請確定已符合下列條件：

* 您有一個使用中的 Cloud Manager 程式，其中包含至少一個 AEM as a Cloud Service 環境。
* 您的使用者已指派給目標環境的&#x200B;**AEM使用者**&#x200B;產品設定檔，讓使用者可檢視內容來源。
* 您的使用者已指派給目標環境的&#x200B;**AEM管理員**&#x200B;產品設定檔，這可讓使用者建立和編輯內容來源。 僅存取Cloud Manager是不夠的 — 請參閱下方的[將使用者指派給AEM產品設定檔](#assign-product-profile)。
* 已在&#x200B;**Adobe Admin Console**&#x200B;中布建環境產品設定檔。

## 將使用者指派至AEM產品設定檔 {#assign-product-profile}

使用此程式可針對特定環境授與使用者[!DNL Adobe Experience Manager] as a Cloud Service的存取權。 指派符合使用者需求存取權的設定檔：

* **[!UICONTROL AEM使用者]** — 檢視內容來源。
* **[!UICONTROL AEM管理員]** — 建立和編輯內容來源。

>[!NOTE]
>
>使用者必須屬於AEM產品設定檔，例如&#x200B;**[!UICONTROL AEM使用者]**&#x200B;或&#x200B;**[!UICONTROL AEM管理員]**，才能存取AEM。 光是存取Cloud Manager是不夠的。

若要指派這些設定檔，您必須是具有[!UICONTROL 業務負責人] Cloud Manager產品設定檔的系統管理員。 備妥使用者名稱和電子郵件地址。

1. 在[Cloud Manager](https://my.cloudmanager.adobe.com/)中，瀏覽至您的程式，並為目標環境選取&#x200B;**[!UICONTROL 管理存取權]**。 新索引標籤會針對該環境開啟[!DNL Adobe Admin Console]。
1. 選取&#x200B;**發佈**&#x200B;層的&#x200B;**[!UICONTROL AEM使用者]**&#x200B;或&#x200B;**[!UICONTROL AEM管理員]**&#x200B;產品設定檔 — 例如`AEM Administrators - publish - Program 12345 - Environment 67890`。 Content AI會編制已發佈內容的索引，因此設定檔必須在發佈層級（而非作者）指派。
1. 選取&#x200B;**[!UICONTROL 新增使用者]**。
1. 輸入使用者名稱和電子郵件地址，然後儲存變更。 使用者會新增至產品設定檔。

對使用者需要存取的每個環境（例如開發、預備或生產）重複這些步驟。

>[!CAUTION]
>
>請勿編輯或刪除名為&#x200B;**[!UICONTROL AEM管理員]**&#x200B;或&#x200B;**[!UICONTROL AEM使用者]**&#x200B;的預設產品設定檔。 重新命名&#x200B;**[!UICONTROL AEM管理員]**&#x200B;會移除指派給它的每個人的管理員許可權。

### 驗證指派 {#verify-assignment}

驗證指派是否成功：

1. 在[!DNL Admin Console]中，重新開啟您指派的產品設定檔。
1. 確認使用者出現在成員清單中。

如果您要疑難排解存取或權杖問題，請確認使用者已直接新增至產品設定檔，而非僅透過群組。

## 步驟 1 - 開啟「Content AI 設定」索引標籤 {#open-tab}

1. 登入 [Cloud Manager](https://my.cloudmanager.adobe.com/)  並選取您的程式。

   ![Cloud Manager 主頁顯示程式卡片](../assets/content-ai-onboarding-step-1.png)

1. 從&#x200B;**[!UICONTROL 程式概觀]**，找到&#x200B;**[!UICONTROL 環境]**&#x200B;區段，然後選取您要設定的環境。

   ![醒目提示生產環境的程式概觀](../assets/content-ai-onboarding-step-2.png)

1. 在環境詳細資訊頁面上，選取「**[!UICONTROL Content AI 設定]**」索引標籤。

   ![環境詳細資訊頁面，其中醒目提示 Content AI 設定索引標籤](../assets/content-ai-onboarding-step-3.png)

## 步驟 2 - 建立 Content AI 來源 {#create-source}

內容來源會定義 Content AI 抓取和編製索引的網站。

1. 在「**[!UICONTROL Content AI 設定]**」索引標籤上，選取「**[!UICONTROL 建立來源]**」。

   ![顯示建立來源按鈕的「Content AI 設定」索引標籤](../assets/content-ai-onboarding-step-4.png)

1. 在「**[!UICONTROL 建立/新增 Content AI 來源]**」對話框中，填寫欄位：

   | 欄位 | 說明 |
   | --- | --- |
   | **[!UICONTROL Content AI 設定]** | 此來源的唯一識別碼 (例如 `my-site-index`)。 建立後即無法變更。 |
   | **[!UICONTROL 說明]** | *(選擇性)* 內容來源的簡短說明。 |
   | **[!UICONTROL 網站位址]** | 要抓取之網站的根 URL (例如 `https://www.example.com/`)。 |
   | **[!UICONTROL 排除 URL]** | *(選擇性)* 抓取期間要略過的 URL 模式。 |
   | **[!UICONTROL 重新整理頻率]** | Content AI 重新抓取來源的頻率：每週、每日、每日 4×、60 分鐘或 15 分鐘。 |

   ![建立 Content AI 來源對話框，其中填寫了名稱和網站位址欄位，並醒目提示「建立來源」按鈕](../assets/content-ai-onboarding-step-5-0.png)

   ![重新整理頻率下拉式選單，顯示可用的選項](../assets/content-ai-onboarding-step-5-1.png)

1. 選取「**[!UICONTROL 建立來源]**」。

## 步驟 3 - 觸發贏取 {#trigger-acquisition}

建立來源之後，其狀態為&#x200B;**新增**。 執行初始贏取以開始建立索引。

1. 在來源清單中，選取來源旁的「**更多動作**  (...)」圖示，然後選取「**[!UICONTROL 觸發贏取]**」。

   ![開啟了更多動作選單並醒目提示觸發贏取的 Content AI 來源清單](../assets/content-ai-onboarding-step-7.png)

1. 在「**[!UICONTROL 觸發贏取]**」對話框中，審閱來源詳細資料：**[!UICONTROL 內容來源]**、**[!UICONTROL 上次執行]**&#x200B;及&#x200B;**[!UICONTROL 下次排程執行]**，並選取「**[!UICONTROL 觸發]**」。

   ![觸發贏取確認對話框](../assets/content-ai-onboarding-step-8.png)

## 步驟 4 - 監視索引狀態 {#monitor-status}

贏取開始後，來源狀態會即時更新。

| 狀態 | 含義 |
| --- | --- |
| **新增** | 來源已建立；尚未執行任何贏取。 |
| **建立索引** | 正在贏取；正在抓取內容並編製索引。 |
| **可用** | 索引已完成；來源已準備好提供搜尋查詢。 |

![內容來源清單顯示索引狀態](../assets/content-ai-onboarding-step-9.png)

![顯示可用狀態的內容來源清單](../assets/content-ai-onboarding-step-10.png)

在搜尋索引或測試 API 之前，請等候狀態達到&#x200B;**可用**。

## 步驟 5 - 搜尋索引內容 {#search-content}

一旦來源狀態為&#x200B;**可用**，您就可以直接從 Cloud Manager 執行搜尋查詢，以確認內容已正確編製索引。

1. 在來源清單中，選取來源旁的「**[!UICONTROL 搜尋]**」。

   ![在可用來源上醒目提示「搜尋」按鈕的內容來源清單](../assets/content-ai-onboarding-step-13.png)

1. 在搜尋欄位中輸入查詢。 結果會顯示具有相符評分和內容類型的相符項目清單 (例如 **PAGE** 或 **PDF**)。 選取結果會在右側開啟預覽。

   ![搜尋面板包含查詢、比對結果和分數，以及排名最高的結果的預覽窗格](../assets/content-ai-onboarding-step-14.png)

## 修改或刪除來源 {#modify-source}

在建立來源之後將其設定更新：

1. 在來源清單中，選取來源旁的「**更多動作** (...)」圖示，然後選取「**[!UICONTROL 編輯]**」。

   ![內容來源清單，其中開啟了更多動作選單並醒目提示「編輯」](../assets/content-ai-onboarding-step-11.png)

1. 在「**[!UICONTROL 修改 Content AI 來源]**」對話框中，視需要更新&#x200B;**[!UICONTROL 說明]**、**[!UICONTROL 網站位址]**、**[!UICONTROL 排除 URL]** 或&#x200B;**[!UICONTROL 重新整理頻率]**。 **[!UICONTROL Content AI 設定名稱]**&#x200B;是唯讀的，無法變更。

1. 選取「**[!UICONTROL 儲存]**」以套用變更，或選取對話框左下角的「**[!UICONTROL 刪除]**」以完全移除來源。

   >[!WARNING]
   >
   >刪除來源是永久操作。 該來源的所有索引內容都會移除，且無法再提供搜尋查詢。

   ![修改 Content AI 來源對話框，醒目提示出可編輯的欄位，並在左下方反白顯示「刪除」按鈕](../assets/content-ai-onboarding-step-12.png)

來源清單會更新，反映出您的變更。 如果您刪除了來源，就不會再出現在清單中。

## 後續步驟 {#next-steps}

* [設定 Adobe Developer Console 專案](setup-adc-project.md)  - 建立呼叫 API 所需的 ADC 專案和認證。
* [Content AI API 參考](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) - 使用語意、全文或混合式搜尋端點查詢您的索引內容。

## 疑難排解 {#troubleshooting}

* **來源會在[!UICONTROL 索引]中長時間保留。** 從 (...) 選單重試贏取。 如果狀態在第二次執行後未前進，請確認&#x200B;**[!UICONTROL 網站位址]**&#x200B;可公開存取，且&#x200B;**[!UICONTROL 排除 URL]** 模式不會篩選出每個頁面。
* **來源在執行後移回[!UICONTROL 新增]。** 爬蟲無法從設定的根 URL 擷取任何頁面。 確認 URL 以 `200 OK` 回應，且網站未封鎖自動要求。
* **[!UICONTROL 搜尋]未傳回[!UICONTROL 可用]來源的結果。** 索引成功，但沒有符合查詢的內容。 請嘗試更廣泛的查詢，或檢查抓取的 URL 是否包含您期望的頁面。
