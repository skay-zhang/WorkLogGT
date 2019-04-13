# WorkLogGT · 工作日志生成工具

此工具基于 `Node.js` 仅适用于**中文**用户, 因为它的界面和生成内容只有中文的. 欢迎PR~

目录

* [文件结构](#文件结构)
* [工具原理](#工具原理)
* [使用方法](#使用方法)
* [GT-Config 配置](#gt-config-配置)
* [写在最后的话](#写在最后的话)

## 文件结构
```
WorkLogGT-master/
├── gt-config.json 配置文件
├── index.js 窗体相关脚本
├── package-lock.json 依赖包小版本锁定配置
├── package.json 项目基础信息配置
├── page.css 内置页面样式
├── page.html 窗体内置页面
├── script.js 生成相关脚本
```

## 工具原理

1. 根据项目名称生成开篇首句
2. 根据个人身份和跟进阶段, 在配置文件中随机选取适用内容
3. 拆分每行涉及内容, 以此为基础, 遍历内容修饰项, 通过内容修饰项, 在配置文件中随机选取适用内容

Tips: 每个涉及内容都会生成已勾选的内容修饰项哦

## 使用方法

> 我在 `page.html` 用了CDN需要离线使用的请记得修改

WorkLogGT 启动后界面如下

![首屏](https://raw.githubusercontent.com/skai-zhang/WorkLogGT/master/readme-1.png)

你需要提供:
* 项目名称
* 个人身份
  * 项目经理
  * 前端开发
  * 后端开发
* 跟进阶段
  * 刚刚接手
  * 步入正轨
  * 善后收尾
* 涉及内容
* 内容修饰

提供上述内容后点击绿色生成按钮, `script.js` 会根据 `gt-config.json` 中的配置来生成工作日志, 生成结果界面如下

![次屏](https://raw.githubusercontent.com/skai-zhang/WorkLogGT/master/readme-2.png)

在生成结果界面上, 你可以点击绿色复制按钮获取内容, 也可以直接选取文本框内的内容 `Ctrl + C` 复制内容.

## GT-Config 配置

我们先来看下JSON结构, 有两个主要节点 `Basic` 和 `Additional`, `Basic` 是配置的个人情况中的两个下拉框生成内容, `Additional` 配置的是内容修饰项的生成内容, 每个数组均需10条内容, 多了轮不出, 少了会报错.
```json
{
    "Basic": {
        "L1": "项目经理",
        "L2": "前端开发",
        "L3": "后端开发",
        "V1": "刚刚接手",
        "V2": "步入正轨",
        "V3": "善后收尾"
    },
    "Additional": {
        "内容修饰项": "修饰匹配语句, {Text}代表涵盖内容"
    }
}
```

在 `Additional` 中的内容语句, 可以使用 `{Text}` 来代表涵盖内容.

## 写在最后的话

日志这种东西如果不是用来自我总结, 还是留给工具去吧, 节省下的时间可以做不少事情了.
