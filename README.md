GitHub Copilot
==============

[](https://github.com/posheng/copilot/edit/main/README.md#github-copilot)

1.  使用者設定

-   GitHub Copilot - 一般設定

    -   `github.copilot.enable`

        設定在所有檔案啟用 GitHub Copilot 功能，但停用「純文字」檔案類型。

    -   `github.copilot.selectedCompletionModel` 設定為 `gpt-4o-copilot`

        GitHub Copilot 預設自動補全的模型為 `gpt-4o-copilot` 模型。

        > 你也可以用 `F1` > `GitHub Copilot: Change Completion Model` 選擇。

    -   `github.copilot.nextEditSuggestions.enabled` 設定為 `true` (預覽功能)

        在編輯器中啟用下一個編輯建議(NES)功能。

        > NES = Next Edit Suggestions

    -   `editor.inlineSuggest.edits.showCollapsed` 設定為 `true`

        在啟用下一個編輯建議(NES)功能之後，編輯器會經常提醒你要不要按下 Tab 貼上建議的程式碼。但是預設這些建議都會直接在編輯器上占空間，有時候非常干擾我們的開發心流，所以我個人建議將這個設定調整為 `true`，他就不會一直跳出來顯示你要按下 Tab 會被加入的內容了。

-   GitHub Copilot Chat

    -   `github.copilot.chat.followUps` 設定為 `firstOnly` 或 `always`

        是否要在聊天中建議跟進訊息，提供你下一個提示的建議。

    -   `github.copilot.chat.localeOverride` 設定為 `zh-TW`

        設定 GitHub Copilot Chat 的回應語言預設為繁體中文

    -   `github.copilot.chat.scopeSelection` 設定為 `true`

        如果使用者使用 `/explain` 並且使用中編輯器沒有選取，是否提示使用者選取特定符號範圍。

    -   `chat.detectParticipant.enabled` 設定為 `false`

        在 Chat View 聊天的時候自動偵測適合的聊天參與者來執行你的需求，因此你可以不用特別透過 `@` 叫用聊天參與者。

        如果設定為 `true` 的話，如果呼喚出錯誤的聊天參與者，可以按下 `rerun without` 重跑一次，這時就會交給 Copilot 來回答。([說明](https://code.visualstudio.com/updates/v1_93#_automatic-chat-participant-detection-in-chat-view-experimental))

        依照我的過往經驗，設定為 `true` 的時候，經常會叫錯聊天參與者，所以我個人是建議將該設定調整為 `false` 比較好。

    -   `chat.promptFiles` 設定為 `true` (實驗性功能)

        啟用提示檔案(prompts)功能，讓您可以在 VS Code 建立可分享、可重複使用的提示指令，並附加額外的上下文。

        可運用在 Chat View, Edit View, Agent Mode, Inline Chat 等環境下。

        詳見 [Reusable prompt files (experimental)](https://code.visualstudio.com/docs/copilot/copilot-customization#_reusable-prompt-files-experimental)

    -   `github.copilot.chat.agent.thinkingTool` 設定為 `true`

        啟用這個思考工具設定，能讓 Copilot 能夠在代理模式下深入思考您的請求，然後再生成回應。

-   GitHub Copilot Chat - 內嵌聊天 (Inline Chat)

    -   `github.copilot.chat.editor.temporalContext.enabled` 設定為 `true`

        是否要在 Copilot 要求中包含最近檢視及編輯過的檔案。

    -   `inlineChat.holdToSpeech` 設定為 `true`

        按住不放 `Ctrl+U` 或 `Ctrl+I` 開始語音對話

    -   `inlineChat.finishOnType` 設定為 `false`

        在編輯器中輸入時，不會自動結束 Inline Chat 對話

-   GitHub Copilot Chat - 偵錯相關設定

    -   `github.copilot.chat.startDebugging.enabled` 設定為 `true`

        在 Chat View 啟用實驗性的 `/startDebugging` 命令，幫你快速在 VS Code 初始化偵錯相關設定。

-   GitHub Copilot Chat - 測試相關設定

    -   `github.copilot.chat.setupTests.enabled` 設定為 `true`

        啟用實驗性的 `/setupTests` 命令，幫你在 VS Code 快速初始化單元測試相關設定。

    -   `github.copilot.chat.generateTests.codeLens` 設定為 `true` (實驗性功能)

        讓你在編輯器中遇到某一個函式或方法沒有涵蓋到測試範圍時，自動產生 `Generate tests` 的 Code lens 建議。

    -   `github.copilot.chat.testGeneration.instructions` 設定為以下內容：

        ```
        "github.copilot.chat.testGeneration.instructions": [
          {
            "file": ".copilot-test-instructions.md"
          },
          {
            "text": "Always try uniting related tests in a suite."
          }
        ],

        ```

-   GitHub Copilot Chat - 自訂提示

    -   `github.copilot.chat.codeGeneration.useInstructionFiles` 設定為 `true`

        使用 `.github/copilot-instructions.md` 文件來自訂程式碼生成邏輯

    -   `github.copilot.chat.codeGeneration.instructions` 設定為以下內容：

        ```
        "github.copilot.chat.codeGeneration.instructions": [
          {
            "text": "Always response in #zh-tw."
          },
          {
            "text": "When outputing any text, use the following translation mappings: create = 建立, object = 物件, queue = 佇列, stack = 堆疊, information = 資訊, invocation = 呼叫, code = 程式碼, running = 執行, library = 函式庫, schematics = 原理圖, building = 建構, Setting up = 設定, package = 套件, video = 影片, for loop = for 迴圈, class = 類別, Concurrency = 平行處理, Transaction = 交易, Transactional = 交易式, Code Snippet = 程式碼片段, Code Generation = 程式碼產生器, Any Class = 任意類別, Scalability = 延展性, Dependency Package = 相依套件, Dependency Injection = 相依性注入, Reserved Keywords = 保留字, Metadata =  Metadata, Clone = 複製, Memory = 記憶體, Built-in = 內建, Global = 全域, Compatibility = 相容性, Function = 函式, Refresh = 重新整理, document = 文件, example = 範例, demo = 展示, quality = 品質, tutorial = 指南, recipes = 秘訣, byte = 位元組, bit = 位元"
          },
          {
              "file": ".copilot-instructions.md"
          }
        ],

        ```

    -   `github.copilot.chat.reviewSelection.instructions` 設定為以下內容：

        ```
        "github.copilot.chat.reviewSelection.instructions": [
            {
                "file": ".copilot-review-instructions.md"
            }
        ],

        ```

    -   `github.copilot.chat.commitMessageGeneration.instructions` 設定為以下內容：

        ```
        "github.copilot.chat.commitMessageGeneration.instructions": [
          {
            "file": ".copilot-commit-message-instructions.md"
          }
        ],

        ```

    -   `github.copilot.chat.pullRequestDescriptionGeneration.instructions` 設定為以下內容：

        ```
        "github.copilot.chat.pullRequestDescriptionGeneration.instructions": [
          {
            "file": ".copilot-pull-request-description-instructions.md"
          }
        ],

        ```

-   GitHub Copilot Edit

    -   `github.copilot.chat.edits.suggestRelatedFilesForTests` 設定為 `true`

        該功能會在你編輯程式碼時，建議與測試相關的檔案。這對於開發者來說非常有用，因為它可以幫助你快速找到並編輯與當前程式碼變更相關的測試檔案，從而確保程式碼的品質和可靠性。

    -   `github.copilot.chat.edits.suggestRelatedFilesFromGitHistory` 設定為 `true`

        該功能會根據 Git 歷史紀錄來建議相關的檔案。這意味著當你編輯某個檔案時，GitHub Copilot Chat 會根據過去的 Git 提交紀錄，建議可能與當前編輯相關的其他檔案。這有助於你更全面地理解程式碼變更的影響範圍，並確保所有相關檔案都得到了適當的更新。

    -   `chat.editing.confirmEditRequestRemoval` 設定為 `true`

        該功能會在你嘗試刪除由 GitHub Copilot Chat 生成的程式碼變更時，提示你確認是否要刪除。這樣可以避免意外刪除程式碼變更，並確保你的程式碼變更是正確的。

    -   `chat.editing.confirmEditRequestRetry` 設定為 `true`

        該功能會在你嘗試重新生成由 GitHub Copilot Chat 生成的程式碼變更時，提示你確認是否要重新生成。這樣可以避免意外重新生成程式碼變更，並確保你的程式碼變更是正確的。

-   Accessibility (Voice)

    -   `accessibility.voice.speechLanguage` 設定為 `zh-TW`

        設定語音輸入的語言為繁體中文。

    -   `accessibility.voice.autoSynthesize` 設定為 `off`

        在 Copilot 回應時自動合成語音，但有時候太吵了，建議關閉！XD

    -   `accessibility.voice.keywordActivation` 設定為 `chatInContext`

        代表你在說 `Hey Code` 時會在 Copilot 聊天視窗互動。可設定 `off` 關閉此功能。

    -   `accessibility.voice.speechTimeout` 設定為 `1200`

        設定語音輸入後可停頓的時間為 1200 毫秒。

        有些人講話比較慢，一句話講到一半會想很久，這時就要調高一點，不然只要停頓 1.2 秒就送出了！

    -   `accessibility.voice.ignoreCodeBlocks` 設定為 `true` (Insiders)

        避免在合成語音的時候去讀程式碼區塊的內容

2.  鍵盤設定

    -   常用快速鍵 (內建)

        -   開啟 Copilot Chat 視窗，可以按下 `Ctrl+Alt+I`

        -   若在 Copilot Edit 視窗，可以按下 `Ctrl+.` 快速切換 Ask Mode、Edit Mode 與 Agent Mode

        -   若在 Copilot Chat 或 Copilot Edit 可以按下 `Ctrl+/` 連結內容 (Attach Context)

        -   若在 Copilot Chat 或 Copilot Edit 可以按下 `Ctrl+L` 清空現在的對話記錄

        -   若在 Copilot 的代理模式可以按下 `Ctrl+Enter` 讓終端機的命令自動執行 (不用碰滑鼠)

        -   Pick Model 可以按下 `Ctrl+Alt+.` 進行切換

    -   語音對話 (Chat View)

        -   按下 `Ctrl+U` 開始語音對話

        -   按下 `Ctrl+U` 結束語音對話

        -   長按 `Ctrl+U` 可直接說話，放開快速鍵就可以送出提示
