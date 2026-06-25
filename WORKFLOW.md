# GitHub Pages 开发工作流

## 已有项目日常更新（first-page / www.wsjmain.xyz）

```bash
# 1. 拉最新代码
cd ~/Desktop/Claude\ code/first-page
git pull

# 2. 改代码
# 编辑 index.html 或其他文件...

# 3. 本地预览（可选）
open index.html

# 4. 提交 + 推送
git add .
git commit -m "描述本次改了什么"
git push

# 5. 等 1-2 分钟，刷新 https://www.wsjmain.xyz 看效果
```

---

## 新建项目（新网站 / 新子域名）

### 第一步：GitHub 上建仓库

1. 在 GitHub 新建仓库，命名如 `blog` 或 `portfolio`
2. 仓库 Settings → Pages → Source 选 `main` 分支 → Save
3. 得到默认地址 `https://weishijie11.github.io/新仓库名/`

### 第二步：本地克隆到桌面

```bash
git clone https://github.com/weishijie11/新仓库名.git ~/Desktop/Claude\ code/新仓库名
```

### 第三步：添加 CNAME 文件

在项目根目录新建 `CNAME` 文件，内容写你要的子域名：

```
blog.wsjmain.xyz
```

推上去后 GitHub Pages 会自动识别。

### 第四步：腾讯云 DNS 添加 CNAME 记录

| 主机记录 | 记录类型 | 记录值                 |
|----------|----------|------------------------|
| `blog`   | CNAME    | `weishijie11.github.io` |

等几分钟 DNS 生效，就通过 `https://blog.wsjmain.xyz` 访问了。

> **关键点**：同一域名下新增子站点，只需要①GitHub 建仓库 ②放 CNAME 文件 ③腾讯云加一条 CNAME。不用再配 TXT 验证和 A 记录。

---

## 附：常用 git 命令

| 场景             | 命令                                          |
|------------------|-----------------------------------------------|
| 查看改了啥       | `git status`                                  |
| 看具体改动       | `git diff`                                    |
| 撤销某个文件改动 | `git checkout -- 文件名`                       |
| 回退到上次提交   | `git reset --hard HEAD`                       |
| 看提交历史       | `git log --oneline`                            |
| 推不上去先拉     | `git pull --rebase` 再 `git push`              |
