---
title: TryHackMe Linux write up
published: 2026-01-23
description: "tryhackme linux"
tags: ["linux"]
category: Guides
draft: false
---
### 學習目標 : 學習Linux的語法及操作
---
# Linux 1
### 任務四 Running Your First few Commands(執行你的前幾個指令)

如同我們之前討論過，使用 Ubuntu 這類作業系統的一大賣點是它們的輕量化。當然，這也不是沒有缺點，例如，通常沒有圖形使用者介面（GUI）或所謂的桌面環境可以用來與機器互動（除非已安裝）。與這些系統互動很大一部分是使用「終端機」。

「終端機」純粹是文字系統，起初讓人感到畏懼。不過，如果我們拆解一些指令，過一段時間後，你很快就會熟悉終端機的使用！

![image](https://hackmd.io/_uploads/SJx9bMy8be.png)

我們需要能做基本功能，比如瀏覽檔案、輸出檔案內容和建立檔案！這些指令不言自明（當然，前提是你知道它們是什麼......）

讓我們從我已在下表中拆解的兩個前幾句指令開始：
```
Command      |   Description                              |
-------------|--------------------------------------------|
             |                                            |
  echo       | Output any text that we provide            |
             | 輸出我們提供的任何文字                       |
-------------|--------------------------------------------|
             |                                            |
  whoami     |Find out what user we're currently logged   |
             |in as!    查出我們目前登入的使用者是哪個！     |
-------------|--------------------------------------------|
```
請參考下方的片段，了解每個指令的使用範例 : 
![image](https://hackmd.io/_uploads/ry15QGkIbg.png)

如上方終端機所示，如果我們想「回聲」一個單字，就不需要使用雙引號，例如回聲 Hello。然而，若存在一個或多個空格，例如回聲「Hello World」，則應將字串包在雙引號內。

whoami可以知道目前的使用者名稱
![image](https://hackmd.io/_uploads/r1ExVM1I-x.png)

---
#### 題目 

1. If we wanted to output the text "TryHackMe", what    would our command be?
   如果我們想輸出文字「TryHackMe」，我們的指令會是什麼？

A : echo TryHackMe

2. What is the username of who you're logged in as on    your deployed Linux machine?
   你在部署的 Linux 電腦上登入的用戶名是什麼？
   
  輸入whoami就會顯示tryhackme
  
 A : tryhackme

---
### 任務五 Interacting With the Filesystem!(與檔案系統互動！)

到目前為止，我們只涵蓋了「echo」和「whoami」指令。但考慮到我們需要做的事情——包括瀏覽檔案系統、讀寫檔案——這些功能就沒那麼實用了。

在這個任務中，我們將學習指令，以便能夠做到這一點。就像前面的任務一樣，我會在下一個標題的表格中顯示指令，並展示這些指令的實際使用範例。

#### Interacting With the Filesystem (與檔案系統互動)

如我之前所說，能夠在不依賴桌面環境的情況下操作你已登入的機器非常重要。畢竟，如果我們哪裡都去不了，登入又有什麼意義呢？
``` 
Command       |    Full Name           |
--------------|------------------------|
   ls         |      listing           |
--------------|------------------------|
   cd         | change directory       |
--------------|------------------------|
   cat        |  concatenate           |
--------------|------------------------|
   pwd        | print working directory|
--------------|------------------------|
```
---
#### Listing Files in Our Current Directory (ls)   |   在我們目前目錄中列出檔案 （ls）

在我們能做任何事情，例如找出檔案或資料夾的內容之前，首先需要知道存在什麼。這可以透過「ls」指令（listing 的縮寫）來完成
![image](https://hackmd.io/_uploads/SJuRLGy8-g.png)

在上方截圖中，我們可以看到以下目錄/資料夾：

* access.log
* folder1
* folder2
* folder3
* folder4

太好了！你可以從資料夾名稱猜到它會包含什麼。

專業提示：你可以用 ls 和目錄名稱來列出目錄內容，而不必直接導航到那裡。也就是說，ls folder1

---

#### Changing Our Current Directory (cd) | 改變我們目前的目錄（CD）

既然我們知道有哪些資料夾存在，我們需要使用 “cd” 指令 （change directory 的縮寫）來切換到該目錄。假設我想打開「folder1」目錄，我會選擇「cd folder1」。我們同樣想知道這個「folder1」目錄的內容，為此我們會再次使用「ls」：
![image](https://hackmd.io/_uploads/BJik_M1L-x.png)

---

#### Outputting the Contents of a File (cat) | 輸出檔案內容（cat）

雖然知道檔案存在固然重要，但除非我們能看到檔案內容，否則其實沒什麼用。

我們稍後會在房間裡討論一些可用工具，這些工具讓我們能從一台機器轉移到另一台機器。但現在，我們先談談使用一個叫做「cat」 的指令來查看文字檔的內容。

「Cat」是 concatenating 的縮寫，是我們輸出檔案內容（不只是文字檔！）的絕佳方式。

在下面的截圖中，你可以看到我如何結合使用「ls」來列出一個名為「folder4」的目錄中的檔案：
![image](https://hackmd.io/_uploads/SkbPYMyUZl.png)


1. 用「ls」來告訴我們這台機器的「folder4」資料夾裡有哪些檔案可    用。在這裡，它被稱為「note.txt」。

2. 接著我們用 cat note.txt 將這個「note.txt」檔案的內容串    接/輸出，內容是「Hello World!」


專業提示：你可以用 cat 輸出目錄內檔案的內容，而不必透過 cat 和目錄名稱來導航。也就是說，   
```
 cat /home/tryhackme/folder4/note.txt
```

有時候像是使用者名稱、密碼（是的，真的有......）、旗標或設定會儲存在檔案中，這些「cat」可以用來取回這些資料。

---
#### Finding out the full Path to our Current Working Directory (pwd) | 了解我們目前工作目錄（pwd）的完整路徑

你會注意到，隨著你在 Linux 機器上的操作進行，終端機中會顯示你目前使用的目錄名稱。

用之前的範例機器，我們目前在「folder4」資料夾——但這在 Linux 機器的檔案系統中到底在哪裡？我們可以用下面截圖中的「pwd」指令找到答案：

![image](https://hackmd.io/_uploads/r1BDcMJUbl.png)

1. 我們已經知道我們已經在「文件」裡，因為我們的終端機，但目前我    們完全不知道「文件」存放在哪裡，未來還能輕鬆回去查看。

2. 我用「pwd」（print working directory）指令找到這個        「folder4」資料夾的完整檔案路徑。

3. Linux 很貼心地告訴我們， 這個「folder4」目錄儲存在機器      上的「/home/tryhackme/folder4」——這點真是太好了！

4. 未來如果我們身處不同地點，可以用 cd                        /home/tryhackme/folder4 將工作目錄改成這個「folder4」    目錄。

---

#### 題目

1. On the Linux machine that you deploy, how many        folders are there?
   你部署的 Linux 機器上，有多少個資料夾？

A : 5

2. Which directory contains a file? 
   哪個目錄包含檔案？
   
A : folder4

3. What is the contents of this file?
   這個檔案的內容是什麼？

A : Hello World!

4. Use the cd command to navigate to this file and      find out the new current working directory. What      is the path?
   使用 cd 指令前往此檔案，找出新的目前工作目錄。這條路是什麼？

A : /home/tryhackme/folder4

---

### 任務六 Searching for Files (搜尋檔案)

雖然目前看起來還不像，但 Linux 的一個優點就是你能非常有效率地使用它。當然，你能有效率的程度取決於你對它的熟悉程度。隨著你與 Ubuntu 等作業系統互動，像我們之前提到的那些基本指令會逐漸成為肌肉記憶。

一個很棒的方式是用一組指令快速搜尋使用者能存取的整個系統檔案。不需要一直用 cd 和 ls 來找出哪裡。相反地，我們可以用像 find 這類指令 來自動化這類事情！

這時 Linux 開始變得有點令人畏懼——但我們會拆解並讓你慢慢適應。

#### Using Find

尋找指令非常棒，因為它可以非常簡單地使用，也可以相當複雜，取決於你想做什麼。不過，我們還是先從基本原則談談。

請看以下片段;我們可以看到可供使用的目錄清單：

![image](https://hackmd.io/_uploads/HJ-pnz1I-g.png)

* access.log
* folder1
* folder2
* folder3
* folder4

當然，目錄本身可以包含更多目錄。當我們必須逐一翻閱每個檔案，只為了找特定的檔案時，這會讓人頭痛。我們就能用 find 幫我們做到這件事！

我們先從簡單開始，假設我們已經知道要找的檔案名稱——但卻不記得它確切在哪裡！在這個案例中，我們尋找的是「note.txt」

如果我們記得檔名，就可以直接使用 find -name note.txt，指令會像這樣在我們目前目錄中搜尋該特定檔案的每個資料夾：
![image](https://hackmd.io/_uploads/H14ZCMk8be.png)

「Find」成功找到了檔案——結果它位於 folder4/note.txt ——真是太棒了。但假設我們不知道檔案名稱，或想搜尋所有副檔名如「.txt」的檔案。找到，讓我們也這麼做！

我們可以簡單地使用所謂的萬用符（*）來搜尋任何末尾有.txt 的符號。以我們的情況來說，我們想找到目前目錄中所有的.txt 檔案。我們會構造一個指令，例如 find -name *.txt 。其中「Find」能夠找到所有.txt 檔案，並告訴我們每個檔案的位置：
![image](https://hackmd.io/_uploads/S1K8AfJLZg.png)

---
#### Using Grep

另一個很棒且值得學習的實用工具是 grep 的使用。grep 指令讓我們能在檔案內容中搜尋特定想要的值。

舉例來說，網頁伺服器的存取日誌。在這種情況下，網頁伺服器的 access.log 有 302 個條目。
![image](https://hackmd.io/_uploads/ryM30MJUZg.png)

用像 cat 這種指令在這裡不太合適。舉例來說，如果我們想搜尋這個日誌檔，看看某個使用者或 IP 位址造訪了哪些東西？在 302 個項目中查看效率不高，因為我們想找到特定的數值。

我們可以使用 grep 搜尋整個檔案內容，找出我們正在搜尋的值的任何條目。以網頁伺服器的存取日誌為例，我們希望看到 IP 位址「81.143.211.90」造訪過的所有資料（請注意這是虛構的）

「Grep」已經搜尋過這個檔案，並向我們展示了我們提供的任何條目，這些都包含在這個 IP 的日誌檔中。

#### Searching Recursively with grep (使用 grep 遞迴搜尋)

有時候，我們要找的資訊分散在目錄內的多個檔案中。我們不必逐個檢查每個檔案，而是可以告訴 grep 遞迴搜尋所有檔案和子目錄。

為此，我們使用 -R（遞迴）選項。

例如，要在目前目錄及其子資料夾中的所有檔案中搜尋變數，我們可以執行：
```
grep -R "PRETTY_NAME" /etc/
```

這將：

* Search every file in the current directory
搜尋目前目錄中的每個檔案

* Search all subdirectories
搜尋所有子目錄

* Show where the PRETTY_NAME appears
顯示 PRETTY_NAME 出現的位置

---
#### 題目

1. 在「access.log」上用 grep 找出前綴為「THM」的旗標。那面    旗幟是什麼？ 註：「access.log」檔案位於                    「/home/tryhackme/」目錄中。

輸入 grep -R "THM" access.log
就會看到flag

A : THM{ACCESS}

---

### 任務七 An Introduction to Shell Operators (運算子入門)

Linux 運算子是提升你使用 Linux 知識的絕佳方式。有幾位重要的運算子值得一提。我們會先講基礎，並將它們拆解成一小塊。

在概覽中，我將展示以下運算子 : 
```
Symbol / Operator   |  Description                 |
--------------------|------------------------------|
                    | This operator allows you to  |
       &            |run commands in the background| 
                    |of your terminal.這個運算子允許 |
                    |你在終端機背景執行指令。         |
--------------------|------------------------------|
                    | This operator allows you to  |
                    |combine multiple command      |
       &&           |together in one line of your  | 
                    |terminal. 這個運算子讓你能在終端| 
                    |機的一行中組合多個指令。         |
--------------------|------------------------------|
                    |This operator is a redirector |
                    |- meaning that we can take the| 
                    |output from a command (such as|
                    |using cat to output a file)   |
       >            |and direct it elsewhere.      |
                    |這個運算子是重定向器——意思是我們可|
                    |以從指令（例如用 cat 輸出檔案）的|
                    |輸出中，導向其他地方。          |
--------------------|------------------------------|
                    |This operator does the same   |
                    |function of the > operator but|
                    |appends the output rather than|
       >>           |replacing (meaning nothing is |
                    |overwritten).此運算子執行與 >   |
                    |運算子相同的功能，但會附加輸出而非|
                    |替換（即不會被覆蓋）            |
--------------------|------------------------------| 
```

讓我們更詳細地介紹這些問題。

---

#### Operator "&" ( 運算子 " & " )

這個運算子讓我們能在背景執行指令。舉例來說，假設我們想要複製一個大型檔案。這顯然會花很長時間，且在檔案成功複製之前，我們無法做其他事情。

「&」shell 操作符讓我們能執行指令並在背景執行（例如這個檔案副本），讓我們能做其他事情！

---
#### Operator "&&"  ( 運算子 " && " )

這個 shell 運算子在對伴「&」的熟悉度上有點誤導。與「&」運算子不同，我們可以用「&&」來建立執行指令的清單，例如 command1 & command2。不過值得注意的是，command2 只有在 command1 成功時才會執行。

---
#### Operator ">"  ( 運算子 " > " )

這個運算子就是所謂的輸出重定向器。這基本上就是說，我們會把執行指令的輸出輸出送到其他地方。

一個很好的例子是我們在任務四學到的echo指令輸出。當然，執行像 echo hello 這類的指令會把「howdy」回回終端——這其實沒什麼用。我們可以做的是將「howdy」導向到像是新檔案之類的訊息！

假設我們想建立一個名為「welcome」的檔案，並帶有「hey」的訊息。我們可以執行 echo hey > welcome，讓檔案內容像這樣寫成「hey」：
```
echo hey > welcome
```

注意 : 檔案裡若已有訊息會被覆蓋

---
#### Operator ">>" ( 運算子 " >> " )

這個運算子同時也是輸出重定向器，就像我們之前討論過的運算子（>）一樣。然而，這個運算子的不同之處在於，它不是覆蓋檔案中的任何內容，而是直接將輸出放在最後。

接著我們之前的例子，裡面有「welcome」這個檔案，裡面有「hey」的內容。如果用 Echo 用 > 運算子在檔案中加上「hello」，檔案就會只有「hello」，沒有「hey」。

" >> "運算子允許將輸出附加到檔案底部

---
#### 題目

1. If we wanted to run a command in the background,      what operator would we want to use?
   如果我們想在背景執行指令，會用哪個運算元？

   A : &
   
2. If I wanted to replace the contents of a file        named "passwords" with the word "password123",        what would my command be?
   如果我想把一個名為「passwords」的檔案內容替換成           「password123」這個字，我的指令會是什麼？
   
   A : echo password123 > passwords
   
3. Now if I wanted to add "tryhackme" to this file      named "passwords" but also keep "passwords123",      what would my command be
   如果我想在這個名為「passwords」的檔案中加入                「tryhackme」，但同時保留「passwords123」，我的指令會是    什麼？
   
   A : echo tryhackme >> passwords
   
---
### 任務八 Conclusions & Summaries (結論與摘要)

你能走到這一步，真是太棒了！我們為你首次接觸 Linux 的內容涵蓋了不少內容。然而，這些是你每次與 Linux 機器互動時最基本/會用到的功能。

簡單回顧一下，我們已經介紹了以下內容：
* Interacting with your first-ever Linux machine!
  與你人生中的第一台 Linux 機器互動！
  
* Ran some of the most fundamental commands
  執行了一些最基本的指令
  
* Had an introduction to navigating around the         filesystem & how we can use commands like find and   grep to make finding data even more efficient!
  我開始學習如何在檔案系統中操作，以及如何使用像 find 和 grep   這類指令讓查找資料更有效率！
  
* Power up your commands by learning about some of     the important shell operators.
  透過了解一些重要的運算子來提升你的指令能力。

---
### END

---
# Linux 2

### 任務二 Accessing Your Linux Machine Using SSH (Deploy)  (使用 SSH（部署）存取您的 Linux 機器)

瀏覽器內建功能在 Linux 基礎學第一部分中被使用，讓你能毫無困難地直接連接到你的第一台 Linux 機器。

事實上，瀏覽器內的功能使用了我們今天將使用的完全相同的協定。此協定稱為 Secure Shell 或簡稱 SSH，是連接遠端 Linux 機器命令列的常用方式。

我們將在這個房間部署兩台機器：

* Your Linux machine
  你的 Linux 電腦
  
* The TryHackMe AttackBox  
  TryHackMe 攻擊盒
  
#### What is SSH & how Does it Work? (什麼是 SSH 以及它是如何運作的？)

Secure Shell 或 SSH 簡單來說是一種裝置間加密形式的協定。利用密碼學，我們傳送的任何人讀格式輸入都會加密，以便透過網路傳輸——一旦抵達遠端機器，就會解除加密，如下圖所示。

![image](https://hackmd.io/_uploads/HJD1i8lUbl.png)

你可以在 TryHackMe 的房間裡學習各種加密方式。但目前，我們只需要明白：
* SSH allows us to remotely execute commands on         another device remotely.
  SSH 允許我們遠端執行另一台裝置的指令。
  
* Any data sent between the devices is encrypted when   it is sent over a network such as the Internet
  裝置間傳送的任何資料在透過網路（如網際網路）時都會被加密

---
#### Using SSH to Login to Your Linux Machine (使用 SSH 登入你的 Linux 機器)

使用 SSH 的語法非常簡單。我們只需要提供兩點：

1. 遠端機器的 IP 位址

2. 正確輸入有效帳號的憑證，以便在遠端機器上登入

在這個房間裡，我們將以「tryhackme」登入，密碼是「tryhackme」，沒有引號（「」）。我們用房間頂端卡片上顯示的機器 IP 位址作為 IP 位址，並用這個使用者來設計一個指令，用 SSH 登入遠端機器。指令是 ssh，然後是帳號的使用者名稱，@ 然後機器的 IP 位址。

例如：
```
ssh tryhackme@10.49.154.212
```
把 IP 位址替換成你 Linux 目標機器的 IP 位址。執行後，我們會被要求信任主機，並提供「tryhackme」的密碼，密碼就是tryhackme。

##### 註： 當你在 ssh 登入提示輸入密碼時，不會看到任何文字或符號。 不過它仍然有效，所以只要輸入密碼並按 Enter 就能登入。

---

### 任務三 Introduction to Flags and Switches (旗幟與交換器簡介)

大多數指令允許提供參數。這些參數以連字號和一個稱為旗標或開關的特定關鍵字來識別。

我們稍後會討論如何辨識哪些指令允許提供參數，以及這些指令的具體作用。

使用指令時，除非另有說明，否則會執行預設行為。例如，ls 列出工作目錄的內容。然而，隱藏檔案並未被顯示。我們可以使用旗標和開關來擴展指令的行為。

以我們的 ls 範例來說，ls 告訴我們只有一個名為「folder1」的資料夾，如下方截圖中標示的 。 請注意，以下截圖的內容僅為範例。
![image](https://hackmd.io/_uploads/ryN33Ux8Zl.png)

然而，在使用 -a 參數（-all 的縮寫）後 ，我們突然產生了一個包含更多檔案和資料夾的輸出，例如「.hiddenfolder」。帶有「.」的檔案和資料夾是隱藏檔案。
![image](https://hackmd.io/_uploads/H19ep8l8-e.png)


接受這些指令的指令也會有一個 --help 選項。此選項會列出指令可接受的可能選項，並提供簡短說明及使用範例。
![image](https://hackmd.io/_uploads/SyHM6IeUbe.png)

這個選項實際上是所謂的 man page（手冊的縮寫）格式化輸出，裡面包含了 Linux 指令和應用程式的文件。

---
#### The Man(ual) Page

手冊頁面是系統指令與應用程式的絕佳資訊來源，無論是在 Linux 機器上都能存取，且可線上存取。

要存取這些文件，我們可以先使用 man 指令，然後提供我們想要閱讀文件的指令。以我們的 ls 為例，我們會使用 man ls 來查看 ls 的說明頁，如下：
![image](https://hackmd.io/_uploads/Sy_9pUg8-x.png)

---
#### 題目

1. What directional arrow key would we use to navigate    down the manual page?
   我們應該用什麼方向鍵來往下移動說明書頁面？
   
   A : down
   
2. What flag would we use to display the output in a      "human-readable" way?
   我們會用什麼旗標來以「人類可讀」的方式顯示輸出？
   
   查看說明書會看到 : 
   ![image](https://hackmd.io/_uploads/rkaPgvgLWx.png)

   A : -h
   
---
### 任務四 Filesystem Interaction Continued (檔案系統互動持續)

我們涵蓋了在 Linux 機器上與檔案系統互動時最基本的指令。例如，我們教了如何使用 ls 列出和查找資料夾內容，以及 使用 cd 來 find  和導航檔案系統。

在這個任務中，我們將學習更多與檔案系統互動的指令，讓我們能夠：

* create files and folders  建立檔案與資料夾


* move files and folders  移動檔案與資料夾


* delete files and folders  刪除檔案與資料夾

更具體地說，以下指令：
```
  Command    | Full Name          | Purpose  目的                   |
-------------|--------------------|---------------------------------|
  touch      | touch              |Create file  建立檔案             |
-------------|--------------------|---------------------------------|
  mkdir      | make directory     |Create a folder  建立資料夾       |
-------------|--------------------|---------------------------------|
    cp       | copy               |Copy a file or folder            |
             |                    |複製檔案或資料夾                   |  
-------------|--------------------|---------------------------------|
    mv       | move               |Move a file or folder            |
             |                    |移動檔案或資料夾                   |
-------------|--------------------|---------------------------------|
    rm       | remove             |Remove a file or folder          |
             |                    |移除檔案或資料夾                   |
-------------|--------------------|---------------------------------|
    file     | file               |Determine the type of a file     |
             |                    |確定檔案的類型                     |
-------------|--------------------|---------------------------------|
``` 

##### 小技巧：類似使用 cat，我們可以提供完整的檔案路徑，例如 directory1/directory2/note 來執行所有這些指令

---
#### Creating Files and Folders (touch, mkdir)

在 Linux 上建立檔案和資料夾是一個簡單的過程。首先，我們會介紹如何建立檔案。觸控指令只會取一個參數——也就是我們想給檔案命名的名稱。例如，我們可以用 touch note 建立「note」這個檔案。值得注意的是，觸控其實只是產生一個空白檔案。 你需要使用像 echo 這類指令，或像 nano 這類文字編輯器，才能將內容加入空白檔案。
![image](https://hackmd.io/_uploads/ryLUNwx8bl.png)

這和建立資料夾的過程類似，只要使用 mkdir 指令，再提供我們想要指派給目錄的名稱。例如，使用 mkdir mydirectory 建立目錄「mydirectory」。
![image](https://hackmd.io/_uploads/BkeFNvlLbx.png)

---
#### Removing Files and Folders (rm) (移除檔案與資料夾（rm）)

在我們目前討論的指揮中，RM 非常出色。你可以直接用 rm 移除檔案。不過，你需要在想移除的目錄名稱旁邊提供 -R 。
![image](https://hackmd.io/_uploads/B1YJHDg8Wl.png)

---
#### Copying and Moving Files and Folders (cp, mv) (複製與移動檔案與資料夾（cp、mv）)

複製與移動檔案是 Linux 機器上一項重要的功能。從 cp 開始，此指令包含兩個參數：

1. 現有檔案名稱

2. 複製時希望指派給新檔案的名稱

CP 會將現有檔案的全部內容複製到新檔案中。在下面的截圖中，我們正在將「note」複製到「note2」。
![image](https://hackmd.io/_uploads/B1PdDPlIZg.png)

移動檔案需要兩個參數，就像 cp 指令一樣。然而，mv 不會複製或建立新檔案，而是會合併或修改我們作為參數提供的第二個檔案。你不僅可以用 mv 將檔案移到新資料夾，還能用 mv 重新命名檔案或資料夾。舉例來說，在下面的截圖中，我們將檔案「note2」改名為「note3」。「Note3」現在會包含「Note2」的內容。 
![image](https://hackmd.io/_uploads/HkB6PvlUWe.png)

#### Determining File Type  決定檔案類型

常常誤導且讓人誤會的是，從檔案中對其用途或內容做出假設。檔案通常會有所謂的副檔名，讓這件事更簡單。例如，文字檔通常副檔名為「.txt」。但這並非必要。

到目前為止，我們在範例中使用的檔案還沒有副檔名。如果不知道檔案為何存在，我們其實也不知道它的用途。輸入 file 指令。此指令只包含一個參數。舉例來說，我們會用 file 來確認範例中的「note」檔是否真的是文字檔，就像 file note 一樣。

---
#### 題目

1. How would you create the file named "newnote"?
   你會怎麼建立名為「newnote」的檔案？
 
   A : touch newnote
   
2. On the deployable machine, what is the file type      of "unknown1" in "tryhackme's" home directory?
   在可部署的機器上，「tryhackme」主目錄中「unknown1」的檔案 類型是什麼？
   
   輸入 file unknown1
![image](https://hackmd.io/_uploads/BJc6OPe8Ze.png)
就換看到檔案類型是ASCII text
   
   A : ASCII text
   
3. How would we move the file "myfile" to the          directory "myfolder" 
   我們要怎麼把「myfile」這個檔案移到「myfolder」這個目錄？
   
   A : mv myfile myfolder
   
4. What are the contents of this file?
   這個檔案的內容是什麼？
   
   我們可以直接用 cat 看到檔案內容
   ![image](https://hackmd.io/_uploads/ByJfqPeLWl.png)
   
---
### 任務五 Permissions 101

你現在應該已經發現，某些使用者無法存取某些檔案或資料夾。我們之前已經探索過一些指令，可以用來判斷我們擁有哪些存取權限以及它會帶我們去哪裡。

在之前的任務中，我們學會了如何透過旗標和開關來擴展指令的使用。舉例來說，ls 指令會列出目前目錄的內容。使用 -l 開關時，我們可以看到十欄，如下圖所示。不過，我們只對前三欄感興趣：
![image](https://hackmd.io/_uploads/B1jvcDgIWe.png)

雖然令人畏懼，但這三欄對於判斷檔案或資料夾的某些特性以及我們是否能存取它非常重要。檔案或資料夾可以有幾個特性，決定允許哪些動作，以及哪個使用者或群組有能力執行該動作——例如以下幾點：

* Read  閱讀
* Write  寫
* Execute  執行

---
#### Briefly: The Differences Between Users & Groups (簡要說明：使用者與團體的差異)

Linux 的優點是權限可以非常細緻，雖然使用者技術上擁有檔案，但如果權限被設定好，一群使用者也能擁有相同或不同的權限，而不會影響檔案擁有者本身。

讓我們把這件事放在現實世界的脈絡中來談談;運行網頁伺服器的系統使用者必須擁有讀寫檔案的權限，才能有效運作網頁應用程式。然而，像是網頁主機公司這類公司，必須允許客戶上傳自己的網站檔案，而不必成為網路伺服器系統的使用者——這將危及其他客戶的安全。

我們會在下面學習切換使用者所需的指令。

---
#### Switching Between Users  使用者切換

在 Linux 安裝中切換使用者非常簡單，這都要歸功於 su 指令。除非你是 root 使用者（或透過 sudo 使用 root 權限），否則你需要知道兩件事來促進使用者帳號的轉移：

* The user we wish to switch to
  我們想切換的使用者

* The user's password  使用者的密碼

su 指令需要幾個開關，可能對你有幫助。例如，登入後執行指令或指定特定 shell。  我建議你閱讀 su 的 man 頁面 以了解更多。不過，我會介紹 -l 或 --login 切換。

簡單來說，透過將 -l 切換到 su，我們啟動了一個更接近實際使用者登入系統的 shell——我們繼承了新使用者更多的屬性，例如環境變數等。  

例如，當使用 su 切換到 “user2” 時，我們的新會話會把我們丟到前一個使用者的家目錄。  
![image](https://hackmd.io/_uploads/ryx9oPxIbx.png)

現在，在使用 -l 後 ，我們的新工作階段自動將我們丟入「user」的主目錄。
![image](https://hackmd.io/_uploads/SySioPlLZl.png)

#### Understanding File Permissions in Numeric Format (以數字格式理解檔案權限)

在 Linux 中，每個檔案和目錄都有一組權限，控制誰可以讀、寫或執行。這些權限通常以符號格式顯示，例如：
![image](https://hackmd.io/_uploads/Sy_e3wxUWx.png)

此格式分為三組：
```
Section      | Applies To      | Example     |
-------------|-----------------|-------------|
First 3      | Owner           | rwx         |
-------------|-----------------|-------------|
Next  3      | Group           | rwx         |
-------------|-----------------|-------------|
Last  3      | Others          | rwx         |
-------------|-----------------|-------------|
```

每個字母代表一種特定的許可：

* r = read 
* w = write 
* x = execute 

---
#### Converting Symbolic Permissions to Numbers (將符號權限轉換為數字)

每個權限都有一個數值：
```
Permission    | Value    |
--------------|----------|
Read (r)      |   4      |
--------------|----------|
Write (w)     |   2      |
--------------|----------|
Execute (x)   |   1      |
--------------|----------|
```

為了計算數值，我們將每個群組的數值相加 。
```
Group     |	Permissions  |	Calculation  |	Value  |
----------|------------------|---------------|---------|
Owner     |     rwx	     |   4 + 2 + 1   |   7     |
----------|------------------|---------------|---------|
Group     |  	rwx	     |   4 + 2 + 1   |   7     |
----------|------------------|---------------|---------|
Others    | 	rwx	     |   4 + 2 + 1   |   7     |
----------|------------------|---------------|---------|
```

所以：
```
rwxrwxrwx = 777
```

---
#### More Common Examples (更多常見範例)

```
Symbolic        | Numeric | Meaning                    |
----------------|---------|----------------------------|
rwxr-xr-x       | 755     |Owner can do everything,    | 
                |         |others can read and execute |
                |         |擁有者什麼都能做，其他人則能閱讀|
                |         |和執行                       |
----------------|---------|----------------------------|
rw-r--r--       | 644     |Owner can read/write, others| 
                |         |can only read               |
                |         |擁有者能讀寫，其他人只能讀     |
----------------|---------|----------------------------|
rwx------       | 700     |Only the owner has access   |
                |         |只有擁有者有權限              |
----------------|---------|----------------------------|
```

##### Why This Matters  為什麼這很重要

理解數值權限很重要，因為：

* Many Linux commands use numeric values (e.g. chmod   755 file)
  許多 Linux 指令使用數值（例如 chmod 755 檔案 ）

* You can quickly identify security risks
  你可以快速識別安全風險

* You can control who can access sensitive files
  你可以控制誰能存取敏感檔案
  
例如：
```
chmod 750 system_overview.txt
```

這意味著：
* Owner: full access  
  擁有者：完全存取權

* Group: read + execute
  群組：讀取 + 執行
  
* Others: no access  
  其他：無法進入
  
---
#### 題目

1. On the deployable machine, who is the owner of      "important"?
   在可部署的機器上，「重要」的擁有者是誰？
   
   A : user2

2. What would the command be to switch to the user      "user2"?
   切換到使用者「user2」的指令是什麼？
   
   A : su user2   (密碼 : user2 )
   
3. Output the contents of "important", what is the      flag?
   輸出「重要」的內容，那是什麼旗幟？
   
   輸入 cat important 就會出現了
   ![image](https://hackmd.io/_uploads/BJrVPYeLZe.png)

   A : THM{SU_USER2}
   
---
### 任務六 Common Directories  通用目錄

#### /etc

這個根目錄是你系統中最重要的根目錄之一。etc 資料夾（etcetera 的縮寫）是你作業系統常用來存放系統檔案的地方。

例如，下面截圖中標示的 sudoers 檔案包含了有權限執行 sudo 或一組指令的使用者與群組，作為根使用者。

下方也標示了「passwd」和「shadow」檔案。這兩個檔案對 Linux 特別重要，因為它們展示了系統如何以稱為 sha512 的加密格式儲存每位使用者的密碼。
![image](https://hackmd.io/_uploads/BkNb_tgLWg.png)

---
#### /var

「/var」目錄，其中「var」是變數資料的縮寫，是 Linux 安裝中主要的根目錄之一。這個資料夾儲存系統上服務或應用程式經常存取或撰寫的資料。例如，執行中的服務和應用程式的日誌檔案會寫在這裡（/var/log），或其他不一定與特定使用者相關聯的資料（例如資料庫等）
![image](https://hackmd.io/_uploads/BJK9OKgLWe.png)

---
#### /root

與 /home 目錄不同，/root 資料夾實際上是「root」系統使用者的家。這個資料夾裡沒有其他東西，只是讓你知道這是「root」使用者的主目錄。不過，值得一提的是，邏輯上該使用者的資料預設會放在像「/home/root」這樣的目錄中。

---
#### /tmp

這是 Linux 安裝中唯一存在的根目錄。/tmp 目錄是 「temporary」的縮寫，具有揮發性，用於儲存只需存取一兩次的資料。就像你電腦的記憶體一樣，一旦重新啟動，這個資料夾的內容會被清空。

對我們滲透測試有用的是，任何使用者預設都可以寫入這個資料夾。也就是說，一旦我們有機器，它就成為存放像是列舉腳本這類資料的好地方。

![image](https://hackmd.io/_uploads/BJv-YKeLZg.png)

---
#### 題目

1. What is the directory path that would we expect      logs to be stored in?
   我們預期日誌會儲存在哪條目錄路徑中？
   
   A : /var/log
   
2. What root directory is similar to how RAM on a      computer works?
   哪個根目錄和電腦記憶體的運作方式相似？
   
   A : /tmp
   
3. Name the home directory of the root user 
   命名根使用者的主目錄
   
   A : /root
   
---
### 任務七 Conclusions and Summaries (結論與摘要)

做得好！這個教室理論內容相當豐富，涵蓋了讓你熟悉 Linux 的各種基礎知識。簡單回顧一下，這個房間教了你：

* How to connect to a Linux machine remotely using     SSH
  如何使用 SSH 遠端連接 Linux 機器

* Advancing your use of commands by providing flags,   switches and where you can go to learn about these   for each command (man pages)
  透過提供旗標、開關以及你在哪裡學習每個指令的指令（man 頁     面），   來提升你的指令使用。

* Some more commands that you'll frequently be using   to interact with the filesystem and its contents
  還有一些你經常用來與檔案系統及其內容互動的指令

* A brief introduction to file permissions &           switching users
  檔案權限與使用者切換的簡要介紹

* A summary paragraph of the important root           directories on a Ubuntu Linux install and how we     may be able to use the data stored within these.
  以下是 Ubuntu Linux 安裝中重要根目錄的摘要段落，以及我們如   何利用這些目錄中儲存的資料。
  
我鼓勵你再來一兩次這個房間，熟悉這些概念。畢竟，熟能生巧！ 

---

### END

---

# Linux 3
### 任務二 Deploy Your Linux Machine
Use The Following Credentials:
IP Address: MACHINE_IP
Username: tryhackme
Password: tryhackme

登陸tryhackme Linux

---
### 任務三 Terminal Text Editors
#### Nano
要使用 nano 建立或編輯檔案，我們只需使用
```
nano filename
```
將「filename」替換成你想編輯的檔案名稱

---
#### VIM
![image](https://hackmd.io/_uploads/ByLaPcoSWg.png)
VIM 是一款更進階的文字編輯器 
#### VIM的優點有:
VIM 適用於所有未安裝 nano 的虛擬機
有很多資源，例如速查表 、教學，以及你可以使用的各種工具


如果你想了解更多關於這個編輯的資訊，TryHackMe有一個介紹VIM的房間
https://tryhackme.com/room/toolboxvim

---
#### 題目
1. 用 Nano 編輯「tryhackme」主目錄裡的「task3」。裡面的旗幟是什麼？

輸入
```
nano task3
```
裡面就有
```
THM{TEXT_EDITORS}
```

---
### 任務四 General/Useful Utilities
#### Downloading Files (Wget)
wget 的使用
這個指令讓我們能透過 HTTP 從網頁下載檔案。我們只需要提供想要下載的資源地址即可


如果我想下載一個名為「myfile.txt」的檔案到我的電腦，假設我知道它的網址——它會長這樣：
```
wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt
```
---
#### Transferring Files From Your Host - SCP (SSH)
與一般的 cp 指令不同，這個指令允許你使用 SSH 協定在兩台電腦間傳輸檔案，以提供認證與加密功能
#### SCP可以
* 將檔案和目錄從你目前的系統複製到遠端系統
 
* 將遠端系統的檔案和目錄複製到你目前的系統


前提是我們知道你目前系統上使用者和遠端系統使用者的使用者名稱和密碼
我們從我們的機器複製一個範例檔案到遠端機器:
```
Variable                             |  Value        |
The IP address of the remote system  |  192.168.1.30 |
遠端系統的 IP 位址                     |               |
------------------------------------ |---------------|     
User on the remote system            |  ubuntu       |
遠端系統使用者                         |               |
-------------------------------------|---------------|
Name of the file on the local system |  important.txt|
本地系統檔案名稱                       |               |
-------------------------------------|---------------|
Name that we wish to store the file  |               |
as on the remote system              |transferred.txt|
我們想在遠端系統中儲存檔案的名稱         |               |
-------------------------------------|---------------| 
```
有了這些資訊，讓我們來擬定 SCP 指令（記得 SCP 的格式只有 SOURCE 和 DESTINATION）
```
scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
```

---
現在我們反過來，重新配置語法，讓 scp 從我們未登入 的遠端電腦複製檔案
```
Variable                             |  Value        |
The IP address of the remote system  |  192.168.1.30 |
遠端系統的 IP 位址                     |               |
------------------------------------ |---------------|     
User on the remote system            |  ubuntu       |
遠端系統使用者                         |               |
-------------------------------------|---------------|
Name of the file on the local system | documents.txt |
本地系統檔案名稱                       |               |
-------------------------------------|---------------|
Name of the file on the remote system|  notes.txt    |
我們想在系統中儲存檔案的名稱            |               |
-------------------------------------|---------------|     
```
指令現在會呈現如下樣貌：
```
scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt 
```
---
#### Serving Files From Your Host - WEB
Ubuntu 機器預設有 python3。Python 很貼心地提供了一個輕量且易於使用的模組，稱為「HTTPServer」。這個模組能把你的電腦變成一個快速又簡單的網頁伺服器，你可以用來提供自己的檔案，然後其他電腦可以用 curl 和 wget 等指令下載檔案。


Python3 的「HTTPServer」會將檔案提供在執行指令的目錄中，但可以透過手冊頁面中提供的選項來更改。簡單來說，我們只需要在終端機裡執行 
```
python3 -m  http.server
```
就能啟動模組！以下片段中，我們從一個名為「webserver」的目錄提供服務，該目錄只有一個名為「檔案」的單一檔案。
![image](https://hackmd.io/_uploads/ryy9JjTSbg.png)

現在，我們用 wget 下載檔案，地址是 10.49.143.25 和檔案名稱。記得，因為 python3 伺服器是運行 8000 埠，你需要在 wget 指令中指定這點
![image](https://hackmd.io/_uploads/S1Viyj6H-e.png)

注意，你需要開啟一個新的終端機才能使用 wget，並保留你啟動 Python3 網頁伺服器的那個終端機。因為一旦你啟動 Python3 網頁伺服器，它會在該終端機中運行，直到你取消它為止。


下面的片段作為範例
![image](https://hackmd.io/_uploads/BJ1elopBZl.png)

記得 ，你需要在另一個終端機執行 wget 指令（同時保持運行 Python3 伺服器的終端機活躍）。以下是 TryHackMe AttackBox 上的一個範例：
![image](https://hackmd.io/_uploads/r1xHesTS-l.png)

這個模組的一個缺點是你無法進行索引，所以你必須知道你想使用的檔案的確切名稱和位置。

---
#### 題目
1. Download the file http://10.49.143.25:8000/.flag.txt onto the TryHackMe AttackBox. Remember, you will need to do this in a new terminal.

要先打開一台終端機輸入
```
python3 -m  http.server
```

接著再打開一台終端機(原本那台要保留不能關)

接著輸入
```
wget http://10.49.143.25:8000/.flag.txt
```
就會跑出
![image](https://hackmd.io/_uploads/B1Y7rj6SZx.png)


然後輸入
```
cat .flag.txt
```
就會出現flag了
THM{WGET_WEBSERVER}

---
### 任務五 Processes 101
程序是運行在你機器上的程式。它們由核心管理，每個程序都會有一個 ID，也就是它的 PID。PID 依照程序開始的順序遞增。也就是說，第 60 個流程的 PID 會是 60。

#### Viewing Processes(觀看流程)

我們可以使用'ps'指令，提供執行中的程序清單，作為使用者的會話，以及一些額外資訊，例如狀態碼、執行該程序的會話、CPU 使用時間，以及實際執行的程式或指令名稱：
![image](https://hackmd.io/_uploads/rJ5yY6pHWx.png)
請注意上方截圖中，第二個程序的 PID 是 204，而在它下面的指令中，PID 會增加到 205。

要查看其他使用者執行的程序，以及非從會話執行的程序（例如系統程序），我們需要為 ps 指令提供 aux 碼，例如：ps aux
![image](https://hackmd.io/_uploads/HyIAtaaS-e.png)
大概長這樣

另一個非常有用的指令是最高指令 top 提供系統上執行的程序的即時統計數據，而非一次性檢視。這些統計數據每 10 秒刷新一次，但使用方向鍵瀏覽各列時也會刷新。另一個能深入了解系統的好指令是使用 'top' 指令
![image](https://hackmd.io/_uploads/HyIAqppHZe.png)

---
#### Managing Processes(流程管理)

你可以發送終止程序的訊號;有多種類型的訊號，會與核對該過程的「乾淨度」精確相關。要終止指令，我們可以使用適當命名的 kill 指令和我們想要終止的相關 PID。也就是說，要殺死 PID 1337，我們會用 'kill 1337'。

以下是當程序被終止時，我們可以發送的一些訊號：
* SIGTERM - 終止程序，但允許它事先完成一些清理任務

* SIGKILL - 終止流程 - 不會在事後做任何清理

* SIGSTOP - 停止/暫停程序

---
#### How do Processes Start?(流程是如何開始的？)

我們先從命名空間開始談起。作業系統（OS）利用命名空間來最終將電腦上可用的資源（如 CPU、RAM 和優先權）分配給程序。可以把它想像成把電腦切成幾片——就像蛋糕一樣。該切片內的程序會使用一定的運算能力，但這只是每個程序實際可用運算資源的一小部分。

命名空間對安全性非常有利，因為它能將程序與其他程序隔離——只有在同一命名空間中的程序才能彼此看到。

我們之前談過 PID 的運作方式，這正是它發揮作用的地方。ID 為 0 的程序是在系統啟動時啟動的程序。此程序是系統在 Ubuntu 上的初始化程序，例如 systemd，用於管理使用者的程序，並位於作業系統與使用者之間。

例如，一旦系統啟動並初始化，systemd 是最早啟動的程序之一。我們想啟動的任何程式或軟體，都會從所謂的 systemd 子程序開始。這表示它由 systemd 控制，但會以獨立程序運行（雖然共享 systemd 的資源），以便我們更容易辨識及類似的資訊。
![image](https://hackmd.io/_uploads/B1wD6apHbx.png)

---
 #### Getting Processes/Services to Start on Boot(啟動時啟動程序/服務)
 
有些應用程式可以在我們擁有的系統開機時啟動。例如，網頁伺服器、資料庫伺服器或檔案傳輸伺服器。此軟體通常至關重要，管理員常指示在系統開機時啟動。

在這個例子中，我們會告訴 Apache 網頁伺服器手動啟動 Apache，然後告訴系統在開機時啟動 apache2。
 
這時就有了 systemctl 的使用——這個指令讓我們能與 systemd 的程序/守護程序互動。繼續以我們的例子，systemctl 是一個易於使用的指令，格式如下：
```
systemctl [選項] [服務]
```

例如，要告訴 apache 啟動，我們會使用 ' systemctl start apache2 '。看起來很簡單，對吧？同樣地，如果我們想停止 Apache，我們只要把 [選項] 換成 stop（而不是我們提供的 start）。

我們可以用 systemctl 做四個選項：

* Start 開始

* Stop 停止

* Enable 啟用

* Disable 停用

---

#### An Introduction to Backgrounding and Foregrounding in Linux(Linux 背景與前景導)

程序可以有兩種狀態：背景與前景。例如，你在終端機執行的指令，如「echo」或類似的指令，會在終端機的前景執行，因為這是唯一沒有被指示要在背景執行的指令。「Echo」就是一個很好的例子，因為 echo 的輸出會在前景回傳給你，但不會在背景出現——舉例來說，下面有張截圖。
![image](https://hackmd.io/_uploads/rkwL1gkI-e.png)


這裡我們執行的是 echo「Hi THM」 ，期望輸出能像一開始一樣回傳給我們。但在指令中加入 & 運算子後，我們只會得到 echo 程序的 ID，而非實際輸出——因為它是在背景執行。

這對於像複製檔案這類指令非常棒，因為這代表我們可以在背景執行該指令，並繼續執行想要執行的後續指令（而不必先等檔案複製完成）

執行像腳本這類東西時，我們也可以做同樣的事——不用 & 運算子，而是用鍵盤上的 Ctrl + Z 來背景處理程序。它也是一種有效的「暫停」腳本或指令執行方式，如下方範例所示：
![image](https://hackmd.io/_uploads/SJnXxeJIbx.png)

這個腳本會一直重複「這會一直循環直到我停止！」直到我停止或暫停這個程序為止。透過使用 Ctrl + Z (圖片上的T^Z) 來停止

---

#### Foregrounding a process  (強調一個過程)

現在我們有一個程序在背景執行，例如我們的腳本「background.sh」，可以用 ps aux 指令確認，我們可以倒退，將這個程序重新帶回前景進行互動。
![image](https://hackmd.io/_uploads/SkSkWgyUbe.png)

當我們的程序用 Ctrl + Z 或 & 運算子來做背景設定時，我們可以用 fg 把它拉回焦點，就像下面一樣，可以看到 fg 指令正在終端機上重新啟用背景程序，腳本的輸出也會回傳給我們。

![image](https://hackmd.io/_uploads/rJGRbxJ8-e.png)
![image](https://hackmd.io/_uploads/BJtA-lkUWl.png)

---
#### 題目

1. 如果我們啟動一個程序，之前的 ID 是「300」，這個新流程的 ID 會是什麼？

下一個就會變301
A : 301

2. 如果我們想 cleanly 終止一個進程，要輸入什麼指令?

A : SIGTERM

3. 找出已部署實例上正在執行的程序（10.49.181.82）。給了什麼旗幟？

直接輸入 ps aux 就會有一個flag

A : THM{PROCESSES}

4. 我們會用什麼指令來停止服務「myservice」？

A : systemctl stop myservice

5. 我們要用什麼指令在系統開機時啟動同一個服務？

A : systemctl enable myservice

6. 我們會用什麼指令來讓原本背景的流程重新浮現？

A : fg

---

### 任務六 Maintaining Your System: Automation(維護你的系統：自動化)

使用者可能希望排程某個動作或任務在系統啟動後執行。舉例來說，執行指令、備份檔案，或啟動你喜愛的程式，例如 Spotify 或 Google Chrome。

我們將討論 cron 過程，但更具體來說，是如何透過使用 crontabs 來與之互動。Crontab 是開機時啟動的程序之一，負責促進並管理 cron 工作。
![image](https://hackmd.io/_uploads/SkcC7l18Wx.png)

crontab 只是一個帶有格式化的特殊檔案，cron 程序能辨識它，逐步執行每行。Crontabs 需要六個特定值：
```
Value             |    Description                     |
------------------|------------------------------------|
                  |                                    |
 MIN              | What minute to execute at          | 
                  |  執行的時刻是幾分鐘                  |
------------------|------------------------------------|
                  |                                    |
 HOUR             | What hour to execute at            |
                  | 執行的時刻是幾小時                   |
 -----------------|------------------------------------|
                  |                                    |
  DOM             |What day of the month to execute at |  
                  |     執行的日期是每月幾天             |
------------------|------------------------------------|
                  |                                    |
  MON             |What month of the year to execute at|
                  | 一年中的哪個月份執行                 |
------------------|------------------------------------|
                  |                                    |
  DOW             |What day of the week to execute at  |       
                  | 該在星期幾執行                       |
------------------|------------------------------------|
                  |                                    |                  
  CMD             |The actual command that will be     |
                  |executed     實際執行的指令。         |
------------------|------------------------------------|
```
我們以備份檔案為例。你可能想每 12 小時備份一次「cmnatic」的「文件」。我們會使用以下格式：
```
0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
```

crontab 的一個有趣特性是它們也支援萬用字元或星號（*）。如果我們不想為該欄位提供值，也就是說我們不在乎它執行的是哪個月、哪天或哪一年——只要每 12 小時執行一次，我們就直接加上星號。

這一開始可能會讓人感到困惑，因此有一些很棒的資源，例如線上「Crontab 產生器 」，讓你能用友善的應用程式自動生成格式！還有網站「Cron Guru」！
* Crontab 產生器 : https://crontab-generator.org/
* Cron Guru : https://crontab.guru/

Crontab 可以透過使用 crontab -e 編輯，並選擇編輯器（例如 Nano）來編輯你的 crontab
![image](https://hackmd.io/_uploads/r15UAg1U-l.png)

---

#### 題目

1. When will the crontab on the deployed instance (10.49.181.82) run?

輸入 crontab -e 往下會就會找到@reboot

A : @reboot

---

### 任務七 Maintaining Your System: Package Management(維護你的系統：套件管理)

#### Introducing Packages & Software Repos(介紹套件與軟體倉庫)

當開發者想向社群提交軟體時，他們會將其提交到 「apt」儲存庫。若獲批准，他們的程式與工具將公開發布。 Linux 最值得肯定的兩項特點在此凸顯：使用者無障礙性與開源工具的價值。

在 Ubuntu 20.04 Linux 機器上使用 ls 指令時，這些檔案會作為閘道/登錄檔
![image](https://hackmd.io/_uploads/HJ44WZJU-x.png)

![image](https://hackmd.io/_uploads/BkjVbWyUWx.png)

作業系統廠商會維護自己的倉庫，你也可以將社群倉庫加入你的清單！這讓你能擴充作業系統的功能。可以透過 ' add-apt-repository ' 指令或列出其他提供者來新增更多儲存庫！例如，有些廠商會有一個離其地理位置較近的儲存庫。

---

#### Managing Your Repositories (Adding and Removing) |  管理你的儲存庫（新增與移除）

通常我們會用 apt 指令來安裝軟體到 Ubuntu 系統上。apt 指令是同名套件管理軟體的一部分。Apt 包含一整套工具，讓我們能管理軟體的套件與來源，並同時安裝或移除軟體。

新增倉庫的一種方法是使用我們前面提到的 add-apt-repository 指令，但我們會  手動說明如何新增和移除儲存庫 。雖然你可以透過像 dpkg 這類套件安裝程式安裝軟體， 但 apt 的好處是，當我們更新系統時，包含我們新增軟體的儲存庫也會被檢查更新狀況。

在這個例子中，我們將將文字編輯器 Sublime Text 加入我們的 Ubuntu 機器作為儲存庫，因為它不屬於預設的 Ubuntu 倉庫。新增軟體時，我們下載的內容的完整性會透過所謂的 GPG（Gnu Privacy Guard）金鑰來保證。這些金鑰本質上是開發者的安全檢查，說「這是我們的軟體」。如果金鑰與系統信任的與開發者使用的金鑰不符，軟體就不會被下載。

首先，我們需要為 Sublime Text 3 的開發者加入 GPG 金鑰。（請注意，TryHackMe 實例沒有網路連線，因此我們不期望你在部署的機器上加入這個功能，因為這樣會失敗。）

1. 讓我們下載 GPG 金鑰並使用 apt-key 來信任它：
```
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
```

2. 現在我們將此金鑰加入信任清單，現在可以將 Sublime Text 3 的資料庫加入我們的 apt source 清單。一個好做法是為每個新增的社群或第三方倉庫分別建立獨立檔案。

2.1. 我們在 /etc/apt/sources.list.d 建立一個名為 sublime-text.list 的檔案，並輸入儲存庫資訊如下：
![image](https://hackmd.io/_uploads/B1ORfbyIWx.png)

2.2. 現在可以使用 Nano 或你選擇的文字編輯器，將 Sublime Text 3 的儲存庫新增並儲存到這個新建立的檔案中：
![image](https://hackmd.io/_uploads/ByabmbkUWe.png)

2.3. 新增此條目後，需更新 apt 以識別此新條目——此操作使用 apt update 指令

2.4. 一旦成功更新，我們就可以繼續使用 apt install sublime-text 安裝我們信任並新增到 apt 的軟體

移除包裹就像撤銷一樣簡單。這個過程可以透過使用 add-apt-repository --remove ppa:PPA_Name/ppa 指令或手動刪除我們之前新增的檔案來完成。一旦移除，我們就可以直接使用 apt remove [software-name-here] ，例如 apt remove sublime-text。

---

### 任務八 Maintaining Your System: Logs(維護系統：日誌)

我們在 Linux 基礎學第一部分中簡要提及了日誌檔案及其所在。不過，讓我們快速回顧一下。這些檔案和資料夾位於 /var/log 目錄中，包含系統上執行的應用程式與服務的日誌資訊。作業系統 （OS）已經相當擅長自動管理這些日誌，並以一種稱為「輪替」的程序進行。

我標示了一些來自三個在 Ubuntu 機器上運行服務的日誌：

* An Apache2 web server  一台 Apache2 網頁伺服器

* Logs for the fail2ban service, which is used to monitor attempted brute forces, for example
例如，fail2ban 服務的日誌用來監控暴力破解嘗試

* The UFW service which is used as a firewall
UFW 服務作為防火牆

![image](https://hackmd.io/_uploads/rkq4E-yLZe.png)

這些服務和日誌是監控系統健康狀況並保護系統的絕佳方式。不僅如此，像是網頁伺服器這類服務的日誌還包含每一個請求的資訊，讓開發者或管理員能診斷效能問題或調查入侵者的活動。例如，以下兩種值得關注的日誌檔案類型：
* access log  存取記錄

* error log  錯誤日誌

![image](https://hackmd.io/_uploads/r1-FVbyIbg.png)

當然，也有日誌記錄作業系統自身的運作狀況，以及使用者執行的操作，例如驗證嘗試。

---
#### 題目

1. What is the IP address of the user who visited the site?
造訪該網站的使用者的 IP 位址是什麼？

先cd到 /var/log/apache2

輸入 ls 有一個access.log.1的檔案
![image](https://hackmd.io/_uploads/S1xn8byIbg.png)

然後用 cat access.log.1 就會看到ip了
![image](https://hackmd.io/_uploads/SJKzPWJLbg.png)

A : 10.9.232.111

2. What file did they access?  他們存取了什麼檔案？
前面其中一行有顯示檔案了

A : catsanddogs.jpg

---

### 任務九 Conclusions & Summaries (結論與摘要)

歡迎來到 Linux 基礎模組的結尾。隨著時間推移，你對 Linux 的熟悉度會提升。Linux 有潛力以相對輕鬆的方式完成非常強大的功能（希望你在這單元中已經發現了這點）

簡單回顧一下，這個房間向你介紹了以下主題：
* Using terminal text editors
使用終端文字編輯器

* General utilities such as downloading and serving contents using a python webserver
一般工具，例如使用 Python 網頁伺服器下載與提供內容

* A look into processes  流程分析

* Maintaining & automating your system by the use of crontabs, package management, and reviewing logs
透過使用 crontabs、套件管理及日誌審查來維護與自動化您的系統

繼續在其他專門介紹 Linux 工具或工具的 TryHackMe 教室學習：

* Bash Scripting - https://tryhackme.com/room/bashscripting

* Regular Expressions - https://tryhackme.com/room/catregex

### END
