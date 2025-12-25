## 克隆仓库
在所选文件夹下右键，选择属性，选择 ==git bash here== ，并输入下列指令
```git
git clone 仓库链接 
```

## 同步本地仓库到远程仓库
### 场景 1：首次关联（本地仓库未绑定 GitHub 远程仓库）

#### 步骤 1：初始化本地仓库（若未初始化）

打开终端 / 命令行，进入本地项目文件夹，执行初始化命令：
```bash
# 进入项目目录（替换为你的项目路径）
cd /path/to/your/local/project
# 初始化Git仓库（生成.git隐藏文件夹）
git init
```

### 步骤 2：添加本地文件到暂存区
```bash
# 添加所有文件（推荐，.gitignore文件会自动忽略不需要上传的文件）
git add .
# 若仅添加单个文件，替换为：git add 文件名（如 git add README.md）
```

### 步骤 3：提交暂存区文件到本地仓库
```bash
# -m 后跟随提交说明（必填，描述本次提交内容，便于追溯）
git commit -m "首次提交：初始化项目结构"
```

### 步骤 4：关联 GitHub 远程仓库

复制你在 GitHub 创建的远程仓库地址（支持 HTTPS/SSH，SSH 无需重复输入账号密码，推荐配置）：

- HTTPS 地址示例：`https://github.com/你的用户名/仓库名.git`
- SSH 地址示例：`git@github.com:你的用户名/仓库名.git`

执行关联命令：
```bash
# origin 是远程仓库的别名（可自定义，默认用origin）
git remote add origin 你的GitHub仓库地址
# 验证关联是否成功
git remote -v
```

### 步骤 5：将本地仓库推送到 GitHub 远程仓库
```bash
# 首次推送需指定分支（main是GitHub默认分支，早期为master）
git push -u origin main
# 说明：-u 表示绑定本地main分支和远程origin/main分支，后续推送可简化命令
```

⚠️ 注意：若推送时提示「远程仓库非空」（如已勾选 README 初始化），先拉取远程内容合并：
```bash
git pull --rebase origin main
# 合并后再执行推送
git push -u origin main
```

### 场景 2：日常更新（本地已关联远程仓库，同步最新修改）

当你在本地修改代码后，只需 3 步即可同步到 GitHub：

#### 步骤 1：添加修改后的文件到暂存区
```bash
git add .  # 或指定单个文件
```

### 步骤 2：提交到本地仓库
```bash
git commit -m "更新：修复XXbug / 添加XX功能"
```

### 步骤 3：推送到远程仓库（已绑定分支，简化命令）
```bash
git push  # 等价于 git push origin main（无需再写-u）
```

### 补充场景：拉取远程仓库最新内容（多人协作 / 跨设备同步）

若远程仓库有他人更新（或你在另一台设备提交了代码），先拉取再推送，避免冲突：
```bash
# 拉取远程origin仓库的main分支最新内容并合并到本地
git pull origin main
# 拉取后再执行 git push 推送本地修改
```
