# 人工智能代理簡介及應用場景

歡迎來到「人工智能代理入門」課程！這門課程將為你提供構建人工智能代理的基礎知識和實際範例。

加入 [Azure AI Discord 社群](https://discord.gg/kzRShWzttr)，與其他學習者和人工智能代理開發者互動，並隨時提問有關本課程的問題。

在課程開始前，我們將首先了解什麼是人工智能代理，以及如何在我們構建的應用程式和工作流程中使用它們。

## 課程介紹

本課程將涵蓋：

- 什麼是人工智能代理？有哪些不同類型的代理？
- 哪些應用場景最適合人工智能代理？它們如何幫助我們？
- 設計代理解決方案時的一些基本組件有哪些？

## 學習目標

完成本課程後，你應該能夠：

- 理解人工智能代理的概念，以及它們與其他 AI 解決方案的區別。
- 高效應用人工智能代理。
- 為用戶和客戶設計具有生產力的代理解決方案。

## 定義人工智能代理及其類型

### 什麼是人工智能代理？

人工智能代理是**系統**，通過為**大型語言模型（LLMs）**提供**工具**和**知識**的訪問權限，來擴展其能力並讓它們**執行操作**。

讓我們將這個定義分解為幾個部分來理解：

- **系統** - 代理不是單一組件，而是一個由多個組件組成的系統。在基礎層面，人工智能代理的組件包括：
  - **環境** - 定義代理運行的空間。例如，如果我們有一個旅行預訂代理，環境可能是代理用來完成任務的旅行預訂系統。
  - **感測器** - 環境提供信息和反饋。代理使用感測器來收集並解釋這些信息，了解環境的當前狀態。在旅行預訂代理的例子中，感測器可能從系統中獲取酒店空房信息或機票價格。
  - **執行器** - 當代理接收到環境的當前狀態後，會決定採取哪些行動來改變環境。例如，旅行預訂代理可能會為用戶預訂一間可用的房間。

![什麼是人工智能代理？](../../../translated_images/what-are-ai-agents.125520f55950b252a429b04a9f41e0152d4dafa1f1bd9081f4f574631acb759e.hk.png?WT.mc_id=academic-105485-koreyst)

**大型語言模型** - 在 LLM 出現之前，代理的概念已經存在。使用 LLM 構建代理的優勢在於其能夠解釋人類語言和數據的能力。這種能力讓 LLM 可以解釋環境信息並制定改變環境的計劃。

**執行操作** - 在代理系統之外，LLM 的行動僅限於根據用戶的提示生成內容或信息。而在代理系統內，LLM 能夠通過解釋用戶請求並使用環境中的工具來完成任務。

**工具訪問** - LLM 可使用的工具取決於 1) 它運行的環境，以及 2) 開發者的設計。例如，在旅行代理的例子中，代理的工具可能僅限於預訂系統提供的操作，或者開發者可以限制代理只能訪問航班的相關工具。

**知識** - 除了環境提供的信息，代理還可以從其他系統、服務、工具甚至其他代理中檢索知識。在旅行代理的例子中，這些知識可能包括客戶數據庫中用戶的旅行偏好信息。

### 不同類型的代理

現在我們已經了解了人工智能代理的基本定義，讓我們看看一些具體的代理類型，以及它們如何應用於旅行預訂代理。

| **代理類型**                 | **描述**                                                                                                                       | **範例**                                                                                                                                                                                                                   |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **簡單反射代理**             | 基於預定義規則執行即時行動。                                                                                                    | 旅行代理解讀電子郵件內容，並將旅行投訴轉發給客戶服務部門。                                                                                                                                                                |
| **基於模型的反射代理**       | 基於對世界的模型及其變化執行行動。                                                                                              | 旅行代理根據歷史價格數據的訪問權限，優先處理價格變動較大的路線。                                                                                                                                                          |
| **目標導向代理**             | 通過解釋目標並確定達成目標的行動來制定計劃。                                                                                      | 旅行代理通過確定從當前位置到目的地所需的旅行安排（如汽車、公車、航班）來完成行程預訂。                                                                                                                                  |
| **效用導向代理**             | 考慮偏好並通過數值權衡取捨來確定如何達成目標。                                                                                  | 旅行代理在預訂行程時通過權衡便利性與成本來最大化效用。                                                                                                                                                                    |
| **學習型代理**               | 通過響應反饋並相應調整行動來隨時間改進。                                                                                        | 旅行代理通過使用客戶在行程後的調查反饋，對未來的預訂進行調整以改進服務。                                                                                                                                                 |
| **分層代理**                 | 包含多個層級代理，高層代理將任務分解為子任務，交由低層代理完成。                                                                | 旅行代理取消行程時，將任務分解為子任務（例如取消具體的預訂），並由低層代理完成，然後向高層代理匯報。                                                                                                                     |
| **多代理系統（MAS）**        | 代理以協作或競爭的方式獨立完成任務。                                                                                            | 協作：多個代理分別預訂特定的旅行服務，如酒店、航班和娛樂活動。競爭：多個代理管理並競爭共享的酒店預訂日曆，為客戶預訂房間。                                                                                              |

## 何時使用人工智能代理

在上一節中，我們使用旅行代理的應用場景來解釋不同類型代理在旅行預訂中的使用方式。在本課程中，我們將繼續使用這個應用場景。

讓我們看看人工智能代理最適合的應用場景類型：

![何時使用人工智能代理？](../../../translated_images/when-to-use-ai-agents.912b9a02e9e0e2af45a3e24faa4e912e334ec23f21f0cf5cb040b7e899b09cd0.hk.png?WT.mc_id=academic-105485-koreyst)

- **開放性問題** - 當任務所需的步驟無法總是硬編碼進工作流程時，允許 LLM 自行決定完成任務所需的步驟。
- **多步驟流程** - 當任務需要一定的複雜性，代理需要通過多次互動使用工具或信息，而非一次性檢索時。
- **隨時間改進** - 當任務需要通過接收來自環境或用戶的反饋來改進，以提供更好的效用時。

我們會在「構建可信賴的人工智能代理」課程中詳細討論使用代理的更多考量。

## 代理解決方案的基礎

### 代理開發

設計人工智能代理系統的第一步是定義工具、行動和行為。在本課程中，我們專注於使用 **Azure AI Agent Service** 來定義代理。它提供以下功能：

- 選擇開放模型，例如 OpenAI、Mistral 和 Llama
- 通過 Tripadvisor 等供應商使用授權數據
- 使用標準化的 OpenAPI 3.0 工具

### 代理模式

與 LLM 的溝通是通過提示完成的。由於人工智能代理具有半自動化的特性，並非總是需要在環境變化後手動重新提示 LLM。我們使用 **代理模式**，以更具規模化的方式在多步驟中提示 LLM。

本課程分為一些當前流行的代理模式進行學習。

### 代理框架

代理框架允許開發者通過程式碼實現代理模式。這些框架提供模板、插件和工具，增強人工智能代理的協作能力。這些優勢使得人工智能代理系統的可觀察性和故障排除能力更強。

在本課程中，我們將探索基於研究的 AutoGen 框架，以及來自 Semantic Kernel 的生產級代理框架。
```

**免責聲明**:  
本文件經由機器翻譯人工智能服務翻譯而成。雖然我們致力於提供準確的翻譯，但請注意，自動翻譯可能包含錯誤或不準確之處。應以原文文件作為權威來源。如涉及關鍵資訊，建議尋求專業人工翻譯。我們對因使用此翻譯而引起的任何誤解或錯誤解釋概不負責。