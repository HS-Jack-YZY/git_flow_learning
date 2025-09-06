# Git 学习仓库

本仓库用于学习和练习 Git 的基本操作，包括仓库初始化、分支管理、冲突解决等。你可以跟随本 README 的步骤，亲自实践并理解每个命令的作用和原理。

---

## 一、仓库初始化

1. **初始化本地 Git 仓库**

    ```bash
    git init
    ```

   > 在你的项目目录下初始化 Git，让 Git 开始管理你的项目。

2. **添加远程仓库地址**

    ```bash
    git remote add origin https://github.com/你的用户名/你的仓库名.git
    ```

   > 将本地仓库与远程仓库关联，后续所有 `push/pull` 操作都与此远程仓库交互。

3. **添加和提交本地所有文件**

    ```bash
    git add .
    git commit -m "初始化项目"
    ```

   > `add` 暂存所有更改，`commit` 记录快照。

4. **设置本地分支与远程分支关联**

    ```bash
    git branch -M main
    ```

   > 将本地分支名统一为 main（推荐主分支命名）。

5. **推送本地分支到远程仓库**

    ```bash
    git push -u origin main
    ```

   > `-u` 参数用于建立本地和远程分支的“upstream”关系，方便后续操作。

---

## 二、处理本地与远程分支冲突

如果远程仓库已有内容（如 README），而本地仓库内容不同，直接推送会失败，出现 `non-fast-forward` 错误。

1. **拉取远程分支，并允许合并无共同历史的仓库**

    ```bash
    git pull origin main --allow-unrelated-histories
    ```

   > 此参数允许本地和远程是独立新建的仓库。

2. **解决冲突**

    - 编辑冲突文件（如 `.gitignore`），合并内容并删除冲突标记（如 `<<<<<<<`, `=======`, `>>>>>>>`）。
    - 暂存已解决的文件：

      ```bash
      git add 冲突文件
      ```

    - 如果使用 merge 拉取，提交合并：

      ```bash
      git commit -m "解决合并冲突"
      ```

    - 如果使用 rebase 拉取，继续 rebase：

      ```bash
      git rebase --continue
      ```

3. **完成后推送到远程仓库**

    ```bash
    git push origin main
    ```

---

## 三、常用 Git 原理简述

- **分支（branch）**：用于并行开发和版本管理，主分支一般为 main。
- **upstream（上游分支）**：本地分支与远程分支的关联，便于同步。
- **冲突（conflict）**：本地和远程都修改了同一文件的同一位置，需要人工合并。
- **commit（提交）**：保存项目快照，记录变更历史。
- **merge（合并）**与**rebase（变基）**：两种分支整合方式，merge是把改动合并，rebase是把改动“重新排列”。

---

## 四、参考流程总结

1. 初始化本地仓库并关联远程
2. 本地提交并推送
3. 如有冲突，先拉取远程，解决冲突，再推送

---

本 README 记录了典型 Git 学习场景，欢迎多实践、多提问！
