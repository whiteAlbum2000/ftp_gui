FTP_GUI

這是一個仿 FileZilla 的純 C++ Qt 桌面介面，用 Layout 動態建構雙欄樹狀架構，並實作了目錄樹與路徑下拉選單的雙向狀態同步。


<img width="401" height="300" alt="image" src="https://github.com/user-attachments/assets/01f03695-55ad-4da8-bfeb-3e371e2f516b" />

1. 用 new QVBoxLayout()（垂直排版）和 new QHBoxLayout()（水平排版）一層一層把元件塞進去（addWidget）。這樣寫的好處是視窗拉大縮小時，裡面的格子會跟著自動伸縮，不會跑版。
2. 雙欄樹狀架構：
畫面上分成「左邊本地端（local_site）、右邊遠端（remote_site）」兩欄，並且兩邊都用 QTreeWidget 做成可以一層層展開資料夾的樹狀圖。
3. 目錄樹與路徑下拉選單的雙向狀態同步：
   點擊上方目錄樹某個資料夾時，會觸發 click_item_inDir()，把那個資料夾名稱自動加進上面的 QComboBox 下拉選單並切換顯示。方反過來，當使用者切換上面的 QComboBox 下拉選單時，會觸發 dir_combo_changed()，程式會去搜尋底下的樹狀圖，把對應的資料夾反白選取（setCurrentItem）並展開（setExpanded(true)）。
