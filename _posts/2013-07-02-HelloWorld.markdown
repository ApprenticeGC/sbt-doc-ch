---
layout: default
title: 生成簡單專案
permalink: HelloWorld
---

閱讀這頁之前需要先了解[安裝(Installed sbt)][1001]。

# 產生帶有程式碼的專案目錄 #

一個含有單一程式碼檔案的目錄可以被視為有效的sbt專案。試著產生夾帶著hw.scala檔案名稱為hello的目錄，並於hw.scala裡寫入以下的程式碼：

    object Hi {
      def main(args: Array[String]) = println("Hi!")
    }

將目錄切換到hello目錄下，並輸入指令sbt，待sbt的互動命令提示啓動後，鍵入run。在Linux或是OS X，上述提及的指令會看起來如下：

    $ mkdir hello
    $ cd hello
    $ echo 'object Hi { def main(args: Array[String]) = println("Hi!") }' > hw.scala
    $ sbt
    ...
    > run
    ...
    Hi!

在這個範例裡，sbt是依照慣例而執行。sbt會依序自動找尋：

    - 在基本目錄下的所有程式碼
    - 在src/main/scala或是src/main/java下的所有程式碼
    - 在src/test/scala或是src/test/java下的所有測試碼
    - 在src/main/resources或是src/test/resources下的所有資料檔
    - 在lib下的所有jar檔

預設上，sbt會用和啓動所需的scala相同的版本建置專案。

可於sbt互動模式裡使用sbt run或是進入Scala REPL模式時執行專案。sbt互動模式會將專案裡的class path設定好，所以可以在專案裡直接嚐試即時的版段scala程式。

## 建置定義 ##

大多數的專案需要進行手動設定。基本的建置定義必需寫在放在專案根目錄裡命名為的build.stb檔案。

舉例來說，如果專案是放在名為hello的目錄裡，則在hello/buld.sbt檔案中，可輸入：

    name:="hello"

    version:="1.0"

    scalaVersion:="2.9.1"

特別注意到每個項目都會額外用一行空白來區分。這不是為了要清楚的突顯每個項目所以特地空一行，而是在sbt的寫法下，一定要在項目和項目中間以空一行的方式撰寫。在.sbt建置定義(.sbt build definition)那，會有更多詳細的介紹。

如果有將專案打包成jar檔，至少會需要將專案名稱和版本資訊填入build.sbt。

## 設定sbt版本資訊 ##

如果需要強制使用個特定的sbt版本，可以額外產生hello/project/build.properties檔案。並在檔案裡寫入：

    sbt.version=0.12.0

雖然sbt是99%和之前的版本相容，但強制sbt某特定版本的使用可以避免發生難以預期的問題。


## 進入下一階段 ##

學習sbt專案裡的[檔案和目錄結構(file and directory layout)][1002]。

[1001]: ../Setup "Setup"
[1002]: ../Welcome "Welcome"