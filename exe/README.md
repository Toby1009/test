# 程式使用說明
## How To Run
- 載入盤面檔：MineSweeper.exe CommandFile <輸入指令檔> <輸出檔>
- 輸入指令模式：MineSweeper.exe CommandInput
- GUI：Minesweeper.exe GUI
> 如果想直接進入GUI也可以直接點擊minesweeper.exe
## CommandFile
- 輸入指令檔，將所有輸出寫入輸出檔
- 格式：MineSweeper.exe CommandFile <輸入指令檔> <輸出檔>
- EX：MineSweeper.exe CommandFile command.txt output.txt
## CommandInput
- 用cin輸入指令，cout輸出結果
- 格式：MineSweeper.exe CommandInput
### 三種模式
- 指定盤面檔
- 指定炸彈數量盤面檔
- 指定炸彈生成率盤面檔
#### 指定盤面檔
- Load BoardFile <盤面檔相對路徑>
- EX : Load BoardFile board.txt
#### 指定炸彈數量盤面
- Load RandomCount <M> <N> <炸彈數量>
- EX : Load RandomCount 9 9 7
#### 指定炸彈生成率盤面
- Load RandomRate <M> <N> <炸彈生成機率>
- EX : Load RandomRate 9 9 0.3
### StartGame
- 成功載入盤面後，才可開始遊戲
- 此指令執行後，進入遊玩狀態
### Left/RightClick
#### 開啟格子
- 格式 : LeftClick <row> <col>
- EX : LeftClick 2 3
#### 標注旗幟/問號，若被標註為旗幟，則不能被開啟
- 第一次右鍵標註旗幟，第二次右鍵標註問號，第三次右鍵回復無標註
- 格式 : RightClick <row> <col>
- EX : RightClick 2 3
### Print
- GameBoard：顯示當前玩家盤面狀態
- GameState：顯示當前遊戲狀態
- GameAnswer：顯示遊戲盤面答案
- BombCount：顯示總炸彈數量
- FlagCount：顯示旗幟數量
- OpenBlankCount：當前打開格子數量
- RemainBlankCount：為打開的空白格子數量，此值為零則獲勝
### Replay
- 在遊戲結束後，重新進行新一輪的遊戲
### Quit
- 在遊戲結束後，關閉整個程式
### 輸出格式
- 除了Print指令外，其餘指令需印出該指令是否執行成功(防呆機制)
- 格式 : <指令> : Success/Failed
- 當遊戲獲勝或失敗時，輸出You win/lose the game
## GUI
### 三種模式
- 指定盤面檔
- 指定炸彈數量盤面
- 指定炸彈生成率盤面
> 點載入類型即可切換
### Load
- 按下Load才能讀取所設定之參數，如Load成功，輸出Success，否則輸出Failed
- 如Load 失敗，可能為所輸入之參數不合法或找不到該資料
### 輸出三種狀態按鈕
- Print GameBoard：輸出當前遊戲玩家盤面
- Print GameAnswer：輸出當前遊戲答案盤面
- Print GameState：輸出當前遊戲狀態
> GameBaord 與 GameAnswer 需按下Load並Success之後方能輸出，否則為空
### StartGame
- 開始遊戲之按鈕
> 如未Load，StartGame輸出Failed，如Load成功，輸出Success，並進入遊戲畫面
### 遊戲開始
- 成功StartGame即可進入
- 點右鍵放置旗子圖片，如已有旗子則轉為？圖面，再次點擊？圖片則恢復為原來的格子
- 點擊左鍵揭開該格子，揭開後的數字代表旁邊炸彈數量，如為零則往外八格擴散，如為炸彈則輸，該格子會有爆炸動畫，並揭開所有格子，有炸彈的會有炸彈圖片，如已設為旗子，則無法由左鍵或擴散揭開該格子，如所有沒炸彈的格子皆揭開則贏下遊戲
> 贏或輸遊戲，跳出提示視窗，可選擇重玩或結束
### 問題
- 目前只有在qt command line 上才能看到print，exe檔打開無法出現cmd
