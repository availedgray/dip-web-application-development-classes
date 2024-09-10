既然现有目录中已经有原始仓库，你可以将它配置为跟踪你自己的 fork 分支，而不是直接克隆。以下是步骤：

### 1. **进入现有目录**

```bash
cd dip-web-application-development-classes
```

### 2. **更新远程仓库地址**

1. **查看当前的远程仓库配置：**

   ```bash
   git remote -v
   ```

   你应该看到类似于以下内容：

   ```
   origin  https://github.com/dip-web-application-development-classes/dip-web-application-development-classes.git (fetch)
   origin  https://github.com/dip-web-application-development-classes/dip-web-application-development-classes.git (push)
   ```

2. **更改 `origin` 远程仓库地址为你的 fork：**

   ```bash
   git remote set-url origin https://github.com/availedgray/dip-web-application-development-classes.git
   ```

3. **添加原始仓库作为 `upstream`（如果还没有）：**

   ```bash
   git remote add upstream https://github.com/dip-web-application-development-classes/dip-web-application-development-classes.git
   ```

### 3. **获取和切换到你需要的分支**

1. **获取所有远程分支：**

   ```bash
   git fetch --all
   ```

2. **切换到你需要的分支：**

   ```bash
   git checkout new-branch-name
   ```

   如果分支 `new-branch-name` 不存在，你可以创建一个新的分支：

   ```bash
   git checkout -b new-branch-name origin/new-branch-name
   ```

### 4. **推送到你的 fork**

在新的分支上进行工作并推送更改：

```bash
git add .
git commit -m "Your commit message"
git push origin new-branch-name
```

### 5. **保持同步**

如果你需要从原始仓库（`upstream`）拉取更新：

1. **获取更新：**

   ```bash
   git fetch upstream
   ```

2. **合并原始仓库的更新到你的本地分支：**

   ```bash
   git checkout main
   git merge upstream/main
   ```

3. **推送更新到你的 fork：**

   ```bash
   git push origin main
   ```

通过这些步骤，你可以在现有的目录中工作，并确保你的本地仓库与原始仓库和你的 fork 保持同步。

//Response 2

如果现有目录中包含的是原始仓库（即你之前克隆的 `main origin`），并且你想在这个目录中切换到你 fork 的分支或与新的 fork 工作，你可以按照以下步骤进行操作：

### 1. **更改远程仓库地址**

你需要将现有仓库的远程地址更新为你自己的 fork，以便你可以从你的 fork 推送和拉取更新：

1. **更新远程地址：**

   ```bash
   git remote set-url origin https://github.com/availedgray/dip-web-application-development-classes.git
   ```

2. **（可选）检查并删除旧的 `upstream` 远程地址：**

   如果已经存在 `upstream` 指向原始仓库，你可以移除它或保持：

   ```bash
   git remote remove upstream
   ```

### 2. **拉取远程分支**

获取你 fork 中的所有远程分支，并切换到你需要的分支：

1. **获取所有远程分支：**

   ```bash
   git fetch origin
   ```

2. **切换到你 fork 中的目标分支：**

   ```bash
   git checkout new-branch-name
   ```

   如果分支不存在于本地，但存在于远程，你可能需要创建并切换到该分支：

   ```bash
   git checkout -b new-branch-name origin/new-branch-name
   ```

### 3. **处理本地更改（如果有）**

如果你在原始仓库中有未提交的更改，确保在切换分支前处理这些更改。你可以选择将它们提交、存储（stash）或丢弃：

1. **查看本地更改：**

   ```bash
   git status
   ```

2. **提交更改（如果适用）：**

   ```bash
   git add .
   git commit -m "Your commit message"
   ```

3. **将更改存储（stash）：**

   ```bash
   git stash
   ```

4. **丢弃更改（如果确定不需要）：**

   ```bash
   git reset --hard
   ```

### 4. **同步更新**

如果你想将原始仓库的更新同步到你自己的 fork，并将这些更新合并到你的分支中：

1. **添加原始仓库为 `upstream`（如果尚未添加）：**

   ```bash
   git remote add upstream https://github.com/dip-web-application-development-classes/dip-web-application-development-classes.git
   ```

2. **获取原始仓库的更新：**

   ```bash
   git fetch upstream
   ```

3. **合并更新到你的分支（例如 `main` 分支）：**

   ```bash
   git checkout main
   git merge upstream/main
   ```

4. **推送更新到你的 fork：**

   ```bash
   git push origin main
   ```

### 总结
- 更新远程地址为你的 fork。
- 获取并切换到你需要的分支。
- 处理本地更改。
- 根据需要同步原始仓库的更新。

这样你可以在现有的目录中顺利地切换和工作。