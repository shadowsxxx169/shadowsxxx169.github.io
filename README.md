我找ds弄的,感觉没一点技术含量

安装与初始化 Hexo（5分钟）
安装 Hexo 框架
在命令行中执行（国内用户建议先配置淘宝镜像加速⏩）：

bash
npm config set registry http://registry.npm.taobao.org  # 切换国内源
npm install -g hexo-cli  # 全局安装Hexo
hexo -v                  # 验证安装
💡 若报权限错误，Windows 用管理员身份运行命令行；Mac 加 sudo13。

初始化博客项目

bash
hexo init my-blog     # 创建文件夹并初始化
cd my-blog            # 进入项目目录
npm install           # 安装依赖
二、本地预览与配置（5分钟）
启动本地服务器

bash
hexo s  # 启动服务，访问 http://localhost:4000
网页打开后可见默认主题和 "Hello World" 示例文章。

修改基础配置
用文本编辑器（如 VS Code）打开项目根目录的 _config.yml 文件，修改以下字段：

yaml
title: 你的博客名       # 例如 "小明的技术笔记"
subtitle: 副标题        # 简短描述
author: 你的名字        # 显示在文章底部
language: zh-CN        # 中文界面
timezone: Asia/Shanghai
⚠️ 注意：每个冒号后必须加一个空格！。

三、部署到 GitHub Pages（5分钟）
创建 GitHub 仓库

仓库名必须为 你的用户名.github.io（例如 AliceSmith.github.io）。

配置部署信息
在 _config.yml 末尾添加：

yaml
deploy:
  type: git
  repo: https://github.com/你的用户名/你的用户名.github.io.git
  branch: main
安装部署插件并发布

bash
npm install hexo-deployer-git --save  # 安装插件
hexo clean   # 清理缓存
hexo g       # 生成静态网页
hexo d       # 部署到GitHub
首次部署需输入 GitHub 账号密码。完成后访问 https://你的用户名.github.io 即可看到博客！

四、内容创作与主题更换（可选）
写新文章

bash
hexo n "我的第一篇文章"  # 在 `source/_posts` 生成Markdown文件
用 Markdown 语法编辑内容，保存后执行 hexo g -d 自动部署。

更换主题（如 Next）

bash
git clone https://github.com/theme-next/hexo-theme-next themes/next
修改 _config.yml 中的 theme: landscape → theme: next。

五、进阶优化（后续探索）
绑定自定义域名：在域名商处添加 CNAME 指向 用户名.github.io，仓库中新建 CNAME 文件写入域名。

启用评论系统：使用 Gitalk（基于 GitHub Issue）。

SEO 优化：安装 hexo-generator-sitemap 插件生成站点地图
