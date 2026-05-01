# uniapp-douyin

基于 uniapp 开发的抖音小视频实战项目。

## 特性

- 仿抖音短视频界面
- 支持视频播放
- 底部 TabBar 导航
- 城市切换功能
- 消息页面
- 个人中心页面
- 适配微信小程序

## 技术栈

| 分类 | 技术 |
|------|------|
| 框架 | uni-app |
| UI库 | ColorUI |
| 平台 | 微信小程序 |
| 开发工具 | HBuilderX |

## 项目结构

```
uniapp-douyin/
├── colorui/                  # ColorUI 组件库
│   ├── components/          # 组件
│   ├── animation.css       # 动画样式
│   ├── icon.css           # 图标样式
│   └── main.css           # 主样式
├── components/              # 业务组件
│   ├── list/              # 列表组件
│   ├── my/                # 个人组件
│   ├── cu-video.vue       # 视频组件
│   └── index-header.vue   # 头部组件
├── pages/                  # 页面
│   ├── index/            # 首页
│   ├── city/             # 同城
│   ├── msg/              # 消息
│   └── my/               # 我的
├── static/                 # 静态资源
│   ├── img/              # 图片
│   ├── msg/              # 消息图标
│   └── video/            # 视频封面
├── unpackage/             # 编译输出
├── App.vue                # 应用配置
├── main.js                # 入口文件
├── manifest.json          # 应用配置
├── pages.json             # 页面配置
└── uni.scss               # 全局样式变量
```

## 页面说明

| 页面 | 说明 |
|------|------|
| 首页 | 视频列表展示，支持上下滑动切换 |
| 同城 | 城市切换，查看同城视频 |
| 消息 | 消息通知页面 |
| 我的 | 个人中心页面 |

## 功能模块

- 视频播放
- 视频列表滑动切换
- 点赞、评论功能入口
- 城市定位切换
- 消息通知展示
- 个人资料展示

## 快速开始

### 环境要求

- HBuilderX
- Node.js

### 安装依赖

```bash
# 使用 HBuilderX 打开项目
# 点击菜单：运行 -> 运行到小程序模拟器 -> 微信开发者工具
```

### 运行项目

1. 下载项目代码
2. 使用 HBuilderX 打开
3. 点击运行到微信开发者工具

## 相关链接

- [uni-app 官方文档](https://uniapp.dcloud.io/)
- [ColorUI 组件库](https://github.com/weizongguo/colorui)
- [视频教程](https://www.bilibili.com/video/av84293062)

## 联系方式

- QQ：30024167
- QQ群：785794314
- GitHub：https://github.com/chenbool
- 主页：https://chenbool.github.io
