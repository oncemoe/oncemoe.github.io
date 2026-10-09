# QiBlog 网站维护

这个仓库保存网站源码，使用 Hugo 和 PaperMod 主题。GitHub Actions 会在代码推送到 `master` 分支后自动构建并发布到 GitHub Pages。

## 更新网页上的简历

首页的简历按钮对应两个文件：

- `content/en/about/resume.pdf`：英文页面的 Resume 按钮。
- `content/zh/about/resume.pdf`：中文页面的简历按钮。

目前两个入口都提供同一份中文简历。替换 PDF 时保留文件名，按钮链接就不需要修改。

先将编译好的最新版简历复制到网站仓库：

```bash
cd ~/oncemoe.github.io
cp ~/auto-research/resume/cv-2026-cn.pdf content/en/about/resume.pdf
cp content/en/about/resume.pdf content/zh/about/resume.pdf
git diff --stat
```

确认更新内容后，提交并发布：

```bash
git add content/en/about/resume.pdf content/zh/about/resume.pdf README.md
git commit -m "Update resume PDF"
git push origin master
```

推送会更新公开网站。只更新简历时，本机无需安装 Hugo；构建由 GitHub Actions 完成。

打开 [Actions 页面](https://github.com/oncemoe/oncemoe.github.io/actions)，等待 `Deploy QiBlog to Pages` 运行成功，再检查以下两个下载地址：

- [英文页面的简历](https://blog.laoqi.cc/en/about/resume.pdf)
- [中文页面的简历](https://blog.laoqi.cc/zh/about/resume.pdf)

若浏览器仍显示旧版本，刷新或用无痕窗口重新打开。如果 Actions 显示失败，点击对应运行查看报错。

## 其他常用文件

- `content/zh/about/index.md`、`content/en/about/index.md`：关于页面的文字。
- `config/_default/languages.zh.yaml`、`config/_default/languages.en.yaml`：中英文首页按钮和菜单。
- `.github/workflows/gh-pages.yml`：自动构建与发布流程。
- `static/CNAME`：自定义域名 `blog.laoqi.cc`。
