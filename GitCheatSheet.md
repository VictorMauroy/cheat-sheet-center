**Cheat Sheet Git et Github**

That cheat sheet is about how to create a git project and how to use a simple version of git.
A list of ***Basics Commands***.

**1) How to start a repository**

Go to your Github account, mine is [VictorMauroy](https://github.com/VictorMauroy).
Then, go to Your Profile ==> Repositories ==> New.
Open it, clone it. Have you set an SSH key ? Yes ? Then Clone with the SSH link.

Take a terminal, go to the folder you want to import your project.
Use `git clone <you SSH project link>`.
Good, it's ready.

If you don't clone a project, you must use `git init`, to initialize the current repository as a git repository.

**2) Add, Save & Check**

| Command | Description |
| --- | --- |
| `git add <nom du fichier>` | Add a file as it his now to your next commit |
|`git commit`| Open a temporary text interface to enter your commit text and prepare your staging content to be send |
|`git commit -m "Description/reasons"`| One line commit without opening a text interface|
|`git log`|Show the last commits with their descriptions|
|`git diff`|Show the modifications between your currents files and the last commit|

**3) Send, Receive & Remote**

| Command | Description |
| --- | --- |
| `git push` | git |
| `git pull` | git |
| `git fetch` | git |

**4) Manage branchs**

**5) Remove & Revert**

**6) Merge & Rebase**

**7) Others : must know**

**8) Upstream**