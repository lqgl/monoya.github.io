# 博客-学习记录

## Git

```bash
git clone git@github.com:lqgl/monoya.github.io.git
```

## 安装依赖

```bash
npm install
```

## 本地查看

```bash
hexo c && hexo g && hexo s

```

## 发布博客

### 安装 hexo git 部署工具

```bash
npm install hexo-deployer-git --save
```
### 将博客发布到 github pages 

```bash
hexo c && hexo g && hexo d
```

## 将源文件推送到 github

```bash
git push origin hexo:hexo
```
