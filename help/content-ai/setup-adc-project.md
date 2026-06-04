---
title: 為AEM Content AI設定Adobe Developer Console專案
description: 瞭解如何使用伺服器對伺服器或API金鑰驗證，設定Adobe Developer Console專案並驗證AEM Content AI服務的API呼叫。
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM Content AI， Adobe Developer Console，驗證，伺服器對伺服器， API金鑰，存取權杖
source-git-commit: 445aeafe64eb8a68d0770c1f1afb54d68e0b054f
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 2%

---


# 設定Adobe Developer Console專案 {#configure-adc-project}

若要呼叫AEM Content AI Services API，您需要由Adobe Developer Console (ADC)專案核發的認證。 此頁面會逐步引導您建立專案、選取驗證方法，以及產生您隨每個API請求包含的認證。

移至[Adobe Developer Console](https://developer.adobe.com/console/)讓您的組織開始。

## 先決條件 {#prerequisites}

開始之前，請確定下列事項：

* 您可以存取貴組織的[Adobe Developer Console](https://developer.adobe.com/console/)。
* 您在&#x200B;**Adobe Admin Console**&#x200B;的AEM Content AI Services產品設定檔中被新增為&#x200B;**開發人員**。 若沒有此角色，**[!UICONTROL AEM Content AI Services]** API卡會顯示為停用，且&#x200B;**[!UICONTROL 伺服器對伺服器]**&#x200B;驗證選項會隱藏。
* 您知道要選取之產品設定檔的程式和環境編號（例如，`AEM User - publish - Program 12345 - Environment 67890`）。

## 選擇驗證方法 {#choose-auth}

AEM Content AI Services支援兩種驗證方法。 挑選符合您整合要求的專案：

| 方法 | 最適合 |
| --- | --- |
| [伺服器對伺服器](#s2s-auth) | 無需使用者互動即可呼叫API的後端服務。 傳回短期存取權杖。 |
| [API金鑰](#api-key-auth) | 直接呼叫API的使用者端或瀏覽器式整合。 傳回範圍設定為允許網域的長效金鑰。 |

## 伺服器對伺服器驗證 {#s2s-auth}

1. 選取&#x200B;**[!UICONTROL API與服務]**，然後選取&#x200B;**[!UICONTROL API]**。

   顯示API和服務的![Developer Console](../assets/e2e-env-setup-28.png)

1. 依&#x200B;**AEM Content AI Services**&#x200B;篩選，然後選取&#x200B;**[!UICONTROL 建立專案]**&#x200B;以開始新專案，或如果您要將服務新增至現有專案，則選取&#x200B;**[!UICONTROL 新增API]**。

   >[!NOTE]
   >
   >如果API卡因「需要授權」訊息而停用，您的AEM as a Cloud Service環境可能無法現代化。 請參閱[AEM as a Cloud Service環境現代化](https://experienceleague.adobe.com/zh-hant/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#modernization-of-aem-as-a-cloud-service-environment)。

1. 在&#x200B;**[!UICONTROL 設定API]**&#x200B;對話方塊中，選取&#x200B;**[!UICONTROL 伺服器對伺服器]**&#x200B;驗證。

   ![已選取伺服器對伺服器設定API對話方塊](../assets/e2e-env-setup-29.png)

   >[!TIP]
   >
   >如果「伺服器對伺服器」選項無法使用，則設定整合的使用者不會以開發人員身分新增至產品設定檔。 請參閱[啟用伺服器對伺服器驗證](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)。

1. 如有需要，請重新命名認證。 選取&#x200B;**[!UICONTROL 「下一步」]**。

   ![Adobe Developer Console步驟，在選取[下一步]之前，重新命名新的伺服器對伺服器認證](../assets/e2e-env-setup-30.png)

1. 選取&#x200B;**[!UICONTROL AEM使用者 — 發佈 — 方案XXX — 環境XXX]**&#x200B;和/或&#x200B;**[!UICONTROL AEM使用者 — 作者 — 方案XXX — 環境XXX]**&#x200B;產品設定檔，然後選取&#x200B;**[!UICONTROL 儲存]**。

   ![產品設定檔選擇器，顯示目標程式和環境的AEM使用者發佈和作者設定檔](../assets/e2e-env-setup-31.png)

1. 檢閱API和驗證設定。

   ![檢閱畫面摘要列出選取的API、驗證型別和認證名稱](../assets/e2e-env-setup-33.png)

   ![檢閱畫面詳細資料，顯示認證的指派產品設定檔](../assets/e2e-env-setup-34.png)

### 產生存取權杖 {#generate-token}

1. 在您的ADC專案中，移至&#x200B;**[!UICONTROL 認證]**&#x200B;並選取&#x200B;**[!UICONTROL 產生存取權杖]**。

   ![認證頁面中的[產生存取權杖]按鈕反白顯示](../assets/e2e-env-setup-32.png)

1. 在每個API請求的`Authorization`標頭中包含權杖：

   ```http
   Authorization: Bearer YOUR_ACCESS_TOKEN
   ```

   >[!WARNING]
   >
   >安全地儲存權杖。 它過期，必須定期重新產生。

## API金鑰驗證 {#api-key-auth}

1. 將AEM Content AI Services API新增至專案時，請在&#x200B;**[!UICONTROL 選取驗證型別]**&#x200B;對話方塊中選取&#x200B;**[!UICONTROL API金鑰]**。

   ![選取API金鑰驗證型別](../assets/onboarding-api-key-01.png)

1. 確認API金鑰認證。

   ![新增API金鑰認證](../assets/onboarding-api-key-02.png)

1. 若要限制可以使用金鑰的原始項，請設定允許的網域。

   ![設定允許的網域](../assets/onboarding-api-key-03.png)

1. 您的API金鑰（使用者端識別碼）會顯示在&#x200B;**[!UICONTROL 已連線的認證]**&#x200B;下。 選取&#x200B;**[!UICONTROL 複製]**。

   ![從連線的認證複製API金鑰](../assets/onboarding-api-key-04.png)

1. 在每個API要求中包含金鑰：

   ```http
   x-api-key: YOUR_API_KEY
   ```

   您的專案現已準備就緒。 將金鑰用於對AEM Content AI服務的每個請求。

## 後續步驟 {#next-steps}

* [控制您的內容來源](contentsources.md) — 在Cloud Manager中設定內容來源並觸發贏取。
* [Content AI API參考](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) — 使用您的存取權杖或API金鑰來查詢已編制索引的內容。
