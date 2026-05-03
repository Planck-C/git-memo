## Git学習メモ
### Gitコマンド

### 使えるShellコマンド一覧

> エディターで新規作成する代わりに、簡単にできますね。先に器（入れ物）を作ってからあれこれする文化だからこのようなコマンドがあるんですね。shellのコマンドがほとんど使えるんですか？

とても良いところに気づいています 🙂  
その理解は **UNIX / Linux / Git文化のど真ん中** です。

では核心に答えます。

***

## 結論：

### ✅ **「かなりの範囲で shell のコマンドが使えます」**

ただし、

> ✅ ほとんど使える  
> ❌ すべて同一ではない（環境差がある）

というのが正確な答えです。

***

## なぜ「ほとんど使える」のか

### 背景にあるのは **POSIX** という共通規格です

UNIX系OS（Linux / macOS / BSD / WSL など）は  
**POSIX（Portable Operating System Interface）** という標準に基づいています。

*   `ls`
*   `cd`
*   `mkdir`
*   `touch`
*   `cp`
*   `mv`
*   `rm`
*   `cat`
*   `grep`
*   `sed`
*   `awk`

こういった基本コマンドは  
**POSIXで「共通にあるべきもの」と定義されたコマンド**です。 [\[en.wikipedia.org\]](https://en.wikipedia.org/wiki/List_of_POSIX_commands)

👉 だから

*   Linuxでも
*   macOSでも
*   Git Bash（Windows）でも

**ほぼ同じ感覚で使える**わけです。

***

## shellには「3種類のコマンド」がある

実は、shellで打っているコマンドは全部同じ正体ではありません。

### ① shell組み込み（built-in）

shellそのものの機能

例：

*   `cd`
*   `pwd`
*   `echo`
*   `type`

→ どの環境でもほぼ同じ [\[gnu.org\]](https://www.gnu.org/software/bash/manual/bash.html)

***

### ② 外部コマンド（PATH上の実行ファイル）

いわゆる「UNIXコマンド」

例：

*   `ls`
*   `touch`
*   `mkdir`
*   `grep`

→ POSIX準拠で高い互換性 [\[geeksforgeeks.org\]](https://www.geeksforgeeks.org/linux-unix/basic-shell-commands-in-linux/)

***

### ③ 環境依存コマンド

OSやディストリビューション特有

例：

*   `apt`（Ubuntu系）
*   `dnf`（Fedora系）
*   `brew`（macOS）
*   `powershell`（Windows）

→ これは **その環境限定**

***

## Git Bash / WSL / macOS での違い（実感ポイント）

| コマンド           | 動作                     |
| -------------- | ---------------------- |
| `touch file`   | ✅ どこでも同じ               |
| `ls -l`        | ✅ 同じ                   |
| `grep`         | ✅ 同じ                   |
| `sed`          | ⚠ macOSとLinuxでオプション差あり |
| `apt install`  | ❌ Linux限定              |
| `brew install` | ❌ macOS限定              |

***

## 「器を先に作る文化」と shell の相性

あなたが感じたこの部分、

> 先に器（入れ物）を作ってからあれこれする文化

これは **そのまま shell 設計思想**です。

*   ファイル = ただの「箱」
*   中身は後から
*   パイプ（`|`）で流す
*   小さい道具を組み合わせる

UNIX哲学の有名な考え方です：

> **“Write programs that do one thing and do it well.”**

shellコマンドは  
「1つのことしかしない小道具」を  
**組み合わせて使う前提**で作られています。 [\[pubs.opengroup.org\]](https://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html)

***

## だから Git / 開発と相性が良い

*   Git は「ファイルの存在・差分・履歴」を扱う
*   shell は「ファイルを作る・移動する・比較する」が得意

✅ 思想が一致している  
✅ だから Git Bash が自然に使える

***

## 実務での感覚的な割合

体感ベースですが、現場では：

*   **8割の操作**：POSIXコマンド（どこでも同じ）
*   **1割**：環境固有
*   **1割**：高度なオプション差

という感じです。

***

## ここから先のステップ

今の理解レベルだと、次に進むと気持ちよく繋がります。

1️⃣ `git status` が「ファイルの器」をどう見ているか  
2️⃣ `add → commit` が「器にラベルを貼る」感覚  
3️⃣ `rm` や `mv` が Git 履歴にどう影響するか

次はどれを見たいですか？

*   **「git statusを読めるようになりたい」**
*   **「最初のcommitをやってみたい」**

どちらでもすぐ続けられます 👍
ここから
ここまで
１２３
