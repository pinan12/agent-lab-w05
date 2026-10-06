# NDHU Agent Lab · practice repo（東華校園實作・練習 repo）

Practice files for **Campus Agent Lab**. The handout is on the website: https://ndhu-campus-agent-lab.tedc.chatgpt.site (click **EN**).
校園實作的練習檔。講義在網站上（上面的網址）。

All files are fictional teaching data. Do not add real names, student IDs, grades, private photos or passwords.
全部是虛構的教學資料；不要放真名、學號、成績、私人照片或密碼。

## 1 Make your own copy（建自己的 repo）

Click **Use this template → Create a new repository**. Name it `agent-lab-w05`, choose **Public**, then **Create repository**.
按 **Use this template → Create a new repository**，名稱 `agent-lab-w05`、選 **Public**，按 **Create repository**。

## 2 Clone it with Codex（用 Codex 把它 clone 下來）

Make an empty folder, for example `Documents\lab`. In Codex: **Add new project** → choose that folder → permission **Ask for approval**. Paste this, with your GitHub username:
先建一個空資料夾（例如 `Documents\lab`），Codex 用 **Add new project** 選它、權限選 **Ask for approval**，貼下面這段（換成你的 GitHub 帳號）：

```text
This is a classroom lab. Check whether git works (git --version). If it does not, stop and tell me; do not install anything.
If it works, clone https://github.com/[your-username]/agent-lab-w05.git into this empty folder itself (git clone <url> .), so this folder becomes the repository.
In that repository only, set user.name to [your-username] and user.email to [your-username]@users.noreply.github.com.
Then tell me the full path of practice/01-club-files.
```

No git on this computer? Use the web route in section 4.
這台電腦沒有 git：改走第 4 節的網頁路線。

## 3 Commit and push after every task（每做完一題就 commit＋push）

Do tasks A, B and D on the website in this same Codex project. Use the full paths inside your repo; card B has no path, so start it with one line: `Work in [full path of practice/02-campus-picker].` After each task, paste:
照網站做 A、B、D，都在同一個 Codex 專案裡，路徑用 repo 裡面的；B 卡沒有路徑，第一行先加 `Work in [02-campus-picker 的完整路徑].`。每做完一題貼這段：

```text
Commit only the files for this task with the message "[message]", then push to origin. Show me the commit.
```

| After 做完 | Message 訊息 | What is in it 內容 |
|---|---|---|
| A | `A: organize club files` | `practice/01-club-files/output/` |
| B first version 第一版 | `B v1: activity picker` | `practice/02-campus-picker/output/index.html` |
| B revision 修改後 | `B v2: [what you changed]` | the same file, changed 同一個檔改過 |
| D | `D: rejection` | `practice/04-review/my-rejection.md` (write your rejection here 退回訊息寫在這) |
| End 最後 | `record: learning record and screenshots` | `evidence/`: exported `learning-record.md`, TM screenshots, filled `submission-template.md` |

The B revision is a new commit, so you do not need `index-v1.html`: GitHub keeps the first version, and you can compare the two commits.
B 的修改是新的 commit，不必另存 `index-v1.html`：第一版留在歷史裡，兩個 commit 可以直接比。

When an approval window appears for `git push`, check that it pushes to **your** `agent-lab-w05` before approving. The first push may ask you to sign in to GitHub in the browser.
`git push` 跳出核准視窗時，先看是不是推到**你自己的** `agent-lab-w05` 再按；第一次 push 可能要在瀏覽器登入 GitHub。

## 4 Web route, no git（網頁路線：沒有 git 時）

On your repo page: **Code → Download ZIP**, extract it, and work in that folder. After each task, open the same folder on GitHub (for example `practice/01-club-files`) → **Add file → Upload files** → drag your `output` folder in → write the message from the table → **Commit changes**.
在你的 repo 頁面按 **Code → Download ZIP**，解壓後在那個資料夾做。每做完一題，到 GitHub 上同一層資料夾（例如 `practice/01-club-files`）→ **Add file → Upload files** → 把 `output` 拖進去 → 照上表寫訊息 → **Commit changes**。

## 5 Before you leave（離開前）

Check that your repo page shows every commit, then log out of GitHub, ChatGPT and the browser. Classroom PCs reset after a restart.
到 repo 頁面確認每一個 commit 都在，再登出 GitHub、ChatGPT 和瀏覽器。教室電腦重開就清空。
