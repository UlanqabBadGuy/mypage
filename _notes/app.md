---
layout: note
title: "App Key Points"
date: 2025-05-09
categories: [介绍]
tags: [考试]
---

# 考试重点

## 往年考卷的考点

### 📱 Android 开发

#### 1. 核心组件与架构

* 四大组件：Activity, Service, BroadcastReceiver, ContentProvider
* Android 架构层次：Linux Kernel → HAL → Libraries/ART → Application Framework → Apps

#### 2. UI 布局与属性

* 常见属性：

  * `match_parent`：填满父容器
  * `wrap_content`：刚好包住内容
* 常用控件：`TextView`, `EditText`, `Button`, `ImageView`
* `findViewById(R.id.xxx)` 的使用
* `OnClickListener` 的设定方式
* XML 结构书写示例

#### 3. 事件处理与多线程

* UI 控件事件绑定：`setOnClickListener()`
* 网络请求不能在主线程完成 → 使用线程/`Handler`/`View.post(Runnable)`
* `Handler` vs `Thread` 区别：

  * `Thread`：创建后台线程
  * `Handler`：主线程与子线程通信

#### 4. AndroidManifest.xml 内容

* 应用组件声明（Activity, Service）
* 权限（e.g. `<uses-permission android:name="android.permission.INTERNET"/>`）
* SDK 版本、屏幕适配等信息

#### 5. Android 特殊工具与概念

* Monkey 测试工具（模拟点击测试）
* versionCode vs versionName 区别
* ART vs Dalvik（ART为AOT编译器，提升性能）
* App 签名（keystore 签名 vs Apple 证书）

---

### 🍎 iOS 开发（Swift）

#### 1. Swift 基础语法

* 可选型声明：`var x: Int?`

* 强制类型转换：`as!`

* 函数定义和调用：

  ```swift
  func compute(num1 n1: Int, n2: Int) { }
  compute(num1: 7506, n2: 2022)

  func compute(_ n1: Int, _ n2: Int) { }
  compute(7506, 2022)
  ```

* 设置默认参数值：

  ```swift
  func Sum(num1: Int32, num2: Int32 = 0) -> Int32 { ... }
  ```

#### 2. Storyboard 与 UIKit

* 常用控件：`UILabel`, `UITextField`, `UIButton`
* IBOutlet 与 IBAction 连接方式
* `weak` 意义：防止循环引用（retention cycle）

### 3. 实例功能

* UI 更新：读取 `UITextField.text` → 转换为 `Int` → 显示在 `UILabel`
* 数独验证、计数器更新（+=1 / 重置）

---

### 🌐 混合知识点

#### 1. JSON 处理

* 使用 `JSONObject.getString()` 读取字段
* 使用 `JSONArray` 遍历列表字段

#### 2. Sensor 类别

* 硬件传感器：加速度计 Accelerometer
* 软件传感器：步数计 Step Counter
* Proximity Sensor：靠近检测（如关掉通话屏幕）

#### 3. Android 权限机制

* 网络访问：`INTERNET` 权限
* 读取外部存储等需申请运行时权限

---

### ☁️ 应用发布与签名

| 项目   | Android            | iOS                          |
| ---- | ------------------ | ---------------------------- |
| 开发工具 | Android Studio     | Xcode                        |
| 签名方式 | keystore 文件 + 签名脚本 | Apple 证书 + Provision Profile |
| 发布市场 | Google Play Store  | Apple App Store              |
| 费用   | 一次性 25 USD         | 每年 99 USD                    |
| 文件格式 | .apk / .aab        | .ipa                         |

---

## 该写在cheat sheet上的东西

### 第七章

第七章主要讲了图片音频和视频开发

Image：有下面这么几种类型 （分别是压缩类型，多少位的色深，特点...）

- JPEG （Joint Photographic Experts Group）(lossy compression，8-bit color depth，高质量但小文件，照片和网页照片，高性能压缩) 总色彩 = 256×256×256 = 16,777,216

- PNG （Portable Network Graphics）（lossless compression，same，增加对alpha通道的支持，所以非常适合透明图像，含文字的网页图像或要清晰边缘的图像） 总色彩 = 256×256×256 = 16,777,216
- GIF（Graphics Interchange Format）（lossless compression，八位色彩256种颜色，色彩有限，支持动画和透明，简单动画和图标类网页图像）
- TIFF（Tagged Image File Format）
