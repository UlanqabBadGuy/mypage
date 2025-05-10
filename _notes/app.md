---
layout: note
title: "App Key Points"
date: 2025-05-09
categories: [介绍]
tags: [考试]
---

* Table of Contents
{:toc}


# 考试重点

## 往年考卷的考点

### 22-23 

下面是《COMP7506 Smart Phone Apps Development》2022–2023学年期末考试的标准答案草稿（共100分，按题号顺序）。包含选择题详解及编程题参考答案。

------

#### Question 1 Multiple Choice [20%]

每题2分，共10题。

1. **D**（All of the above）
    理由：i)更易使用、ii)比App加载快、iii)节省手机空间、iv)避免付费，都是用户偏好Web的原因。

2. **B**（0.296 sec）
    计算：37MB = 296Mb，下载时间 = 296Mb / 1000Mbps = **0.296s**

   这个换算是为了把**兆字节（MB）\**转换成\**兆比特（Mb）**，因为网络速度一般是以“比特（bit）”为单位表示的，比如题目里说的 **1 Gbps（1 Giga bit per second）**。

   单位换算关系如下：

   - **1 Byte（字节） = 8 bits（比特）**
   - 所以：**1 MB（Mega Byte）= 8 Mb（Mega bit）**

   回到题目：

   应用大小是 **37MB**
    所以：

   $37 \text{ MB} \times 8 = 296 \text{ Mb}$

   也就是：**37兆字节 = 296兆比特（Mb）**

3. **D**（All of the above）
    解释：

   - i) Android应替换；

   - ii) KitKat仍默认用Dalvik，但支持ART；

   - iii) ART可执行.apk；

   - iv) ART使用AOT编译。

4. **D**（All of the above）
    解释：AndroidManifest包含组件、权限、SDK版本、屏幕支持。

5. **C**（ii) and iv) only）
    解释：Monkey支持真机和模拟器、测试图形/文本输入，但非iOS工具。

6. A我觉得
    解释：

   - i) 小企业方案85:15；

   - ii) 家庭共享支持6人；

   - iii) Xcode仅在Mac上运行；

   - iv) SwiftUI从iOS 13开始支持。

7. **A**（var x: Int?）
    解释：Int? 为可选类型。

8. **B**（as!）
    解释：强制类型转换可能失败，用 as!。

9. **C**（View Controller）
    解释：Storyboard中每一页面为View Controller。

10. **B**（ContentView）
     解释：SwiftUI项目中UI和逻辑默认写在ContentView.swift。

------

#### Question 2 Android: Decimal to Binary App [20%]

(a) **match_parent 与 wrap_content 含义**（2%）

- `match_parent`：拉伸至父容器宽/高。
- `wrap_content`：包裹内容所需最小宽/高。

(b) **布局图**（5%）

```sql
Decimal:
[      EditText        ]
Binary:
[      TextView        ]
[ Convert Button ]
```

(c) **填空题**（6%）
 A: `AppCompatActivity`
 B: `R.layout.activity_main`
 C: `R.id.decimalNumber`
 D: `R.id.binaryNumber`
 E: `R.id.convert`
 F: `new converter()`

(d) **onClick 方法实现**（7%）

```java
public void onClick(View view) {
    String decStr = decimalNumber.getText().toString();
    try {
        int dec = Integer.parseInt(decStr);
        String bin = Integer.toBinaryString(dec);
        binaryNumber.setText(bin);
    } catch (NumberFormatException e) {
        binaryNumber.setText("Invalid input");
    }
}
```

------

#### Question 3 Android UI, Threads, JSON, Permissions [20%]

(a) **两个UI规则与解释**（6%）

- 规则1：**Do not block the UI thread**
   → 保持响应性，避免ANR。
- 规则2：**Only update UI on UI thread**
   → Android UI只能主线程修改，避免崩溃。

(b) **图像是否成功加载与原因**（4%）

- 无法成功显示：主线程中网络操作会抛异常（NetworkOnMainThreadException）
- 修正需使用子线程或AsyncTask等。

(c) **线程 vs Handler 区别**（2%）

- Thread：并行执行任务。
- Handler：用于主线程任务队列通信、延迟/定时执行。

(d) **JSON提取结果**（6%）
 Temp1 = "2023"
 Temp2 = "Priscilla"
 Temp3 = "Ellen"
 Temp4 = "Sonia"
 Array1 = ["Chow Chow", "Ming Ming", "Ben Sir"]

(e) **网络权限**（2%）
 `<uses-permission android:name="android.permission.INTERNET"/>`

------

#### Question 4 iOS Sudoku Game [20%]

(a) **填空题**（5%）
 A: `UIViewController`
 B: `UITextField!`（共9个）
 C: `UILabel!`
 D: `@IBAction`
 E: `viewDidLoad()`

(b) **check() 方法实现**（10%）

```swift
func check() {
    let cells = [
        [cell00, cell01, cell02],
        [cell10, cell11, cell12],
        [cell20, cell21, cell22]
    ]
    var grid = [[Int]]()
    for row in cells {
        var intRow = [Int]()
        for cell in row {
            if let text = cell?.text, let value = Int(text) {
                intRow.append(value)
            } else {
                result.text = "Wrong!"
                return
            }
        }
        grid.append(intRow)
    }

    let targetSum = grid[0].reduce(0, +)
    for i in 0..<3 {
        if grid[i].reduce(0, +) != targetSum { result.text = "Wrong!"; return }
        if (grid[0][i] + grid[1][i] + grid[2][i]) != targetSum { result.text = "Wrong!"; return }
    }

    result.text = "Correct! Sum = \(targetSum)"
}
```

(c) **Storyboard连接方式**（2%）
 按住 Ctrl 拖动控件到 ViewController.swift 中，创建 IBOutlet 或 IBAction。

(d) **weak 含义**（1%）
 防止强引用循环（retain cycle），使内存可被释放。

(e) **SwiftUI优劣势**（2%）

- 优点：代码简洁，响应式，实时预览。
- 缺点：对旧系统版本支持差，复杂UI不如Storyboard灵活。

------

#### Question 5 Swift Functions and App Signing [20%]

(a) **参数标签与内部参数名定义**（2%）

- Argument label：函数外部调用时的参数名
- Parameter name：函数内部使用的变量名

(b) **写出函数调用语句**（6%）
 (i) `Sum(num1: 75, num2: 6)`
 (ii) `Sum(num1: 75, and: 6)`
 (iii) `Sum(75, 6)`

(c) **设置默认参数值**（2%）
 `func Sum(num1: Int32, num2: Int32 = 0) -> Int32`

(d) **为何应从Mac App Store下载Xcode（4%）**

- 1）官方保障：版本完整、无恶意代码；
- 2）自动更新：兼容系统更新，避免开发中断。

(e) **签名过程差异（3%）**

- Android Studio：使用 keystore 自行签名；
- Xcode：需使用Apple Developer证书，较严格、安全性高。

(f) **为何Google Play应用更多（3%）**

- 审核宽松、开放性高、开发门槛低，吸引更多开发者发布。

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

## 该写在cheat sheet上的东西（NOT ALL of THEM）

### 第一章

#### Android架构与运行机制（Architecture）

Android 是一个基于 Linux 的开放移动平台，架构分层如下：

1. **Linux 内核层（Kernel Layer）**
   - 提供核心系统服务，如内存管理、进程管理、网络协议栈、设备驱动（如摄像头、蓝牙、WiFi）

2. **原生库层（Native Libraries）**
   - 由C/C++实现，如：
     - **Surface Manager**：管理显示层次
     - **OpenGL/Skia**：2D/3D图形渲染
     - **SQLite**：轻量级数据库
     - **WebKit**：网页引擎

3. **Android 运行时层**
   - 旧版本为 **Dalvik VM**，采用解释执行+JIT技术
   - 新版本使用 **ART（Android Runtime）**：
     - AOT 编译：安装时将字节码一次性编译为机器码，提升执行效率
     - 优化内存分配与垃圾回收
     - 降低能耗，提升续航

4. **应用框架层（Application Framework）**
   - 提供开发接口，如Activity Manager、Content Provider、Notification Manager等

5. **应用层（Application Layer）**
   - 用户安装的所有App

**安全机制**：

- 每个应用独立运行于单独的进程，由唯一的 UID 标识
- 权限管理系统（如访问通讯录、相机等需显式声明）
- 支持基于URI的精细访问控制

**开发语言**：

- 主流支持：Java / Kotlin（Kotlin为官方推荐）
- 本地层可用C/C++，通过JNI调用

#### MIUI 与 HyperOS：小米移动操作系统的演进

- **MIUI**：基于Android定制的ROM，2010年发布，最早基于Android 2.2
  - 区域版差异显著（中国/全球/EEA/印度等）
  - **中国版本无Google服务**，国际版预装Gmail/Play等，且通过Google认证
- **HyperOS**：2023年起取代MIUI，作为下一代系统
  - 提升性能与电池寿命
  - UI更简洁、响应更快
  - 统一跨设备系统体验（手机+平板+IoT）

#### HarmonyOS（华为鸿蒙系统）

- 首发：2019年9月，由华为开发
- 特点：
  - **分布式操作系统**：可部署在手机、电视、车机、IoT等多种终端
  - App格式为 `.app` 包含 `.hap`（Harmony Ability Package）模块
  - 无需APK，采用“能力驱动”模型

**开发工具包（Kits）示例**：

- **Account Kit**：便捷登录功能
- **Location Kit**：高精度定位
- **Machine Learning Kit**：内嵌AI服务
- **Push Kit**：推送消息
- **Wallet Kit**：数字化票据/支付系统集成

#### iOS 操作系统结构简述

- Apple 旗下系统，发布于2007年，现用于iPhone、iPad、Apple Watch等
- 核心语言：Objective-C（传统）、Swift（现代）
- Game Center 提供游戏社交功能（排行榜、好友对战）
- 与Android不同，**iOS是封闭生态**，App只能通过App Store发布

#### 移动用户体验设计八大原则（UX Design Principles）

1. **去除杂乱**：每屏只展示一个核心动作
2. **直观导航**：用户无需思考即可知道“在哪、去哪”
3. **一致性体验**：手机、平板、桌面使用行为一致
4. **手指友好**：目标控件建议大于7mm，避免误触
5. **可读性**：最小11pt字体，推荐系统默认字体（如Roboto、Helvetica Neue）
6. **对比明确**：遵循W3C推荐，小文字对比度≥4.5:1，大字体≥3:1
7. **手势区友好**：重要按钮放置在拇指舒适区
8. **减少打字**：利用自动补全、默认值等降低输入负担

#### 移动用户体验的约束（UX Constraints）

1. **客户端存储限制**：频率决定存留，功能强≠常驻
2. **屏幕小&输入难**：虚拟键盘劝退用户，注册过长用户可能直接退出
3. **干扰环境多**：易中断，需唤醒机制（如推送）
4. **更新慢**：平台审核流程长、用户必须手动更新，需良好发布管理

#### 移动应用的类型与分类方式

1. **按内容分类**：游戏、社交、购物、导航、资讯、金融等
2. **按技术实现分类**：
   - Native App：原生代码，运行效率高
   - Web App：运行在浏览器中，不占空间
   - Hybrid App：网页 + 原生封装，成本适中
3. **按盈利模式分类**：
   - 免费 + 内购
   - 付费无内购
   - 付费 + 内购

#### 移动应用开发趋势

1. **共享经济驱动App生态**：
   - Airbnb：每人是房东
   - Uber/UberEats：移动出行与外卖生态平台
2. **技术融合趋势**：
   - 区块链 + IoT：增强数据隐私与连接性
   - AI：Chatbot、推荐系统
   - AR/VR：沉浸式体验（如Pokemon Go）
   - 5G：大带宽低延迟，实时多媒体更普及
   - Instant App：Android平台下即点即用
   - IoT集成：多设备、智能家居融合
3. **医疗健康（mHealth）创新**：
   - 支持远程问诊、慢病管理、急诊查询
   - 老年用户是主要增长对象，但接受度低
   - 应对策略：简洁设计 + 趣味交互 + 语音引导

### 第二章

#### 移动应用开发生命周期（Mobile Apps Development Lifecycle）

移动App开发一般划分为五大阶段：

1. Inception（构思）
2. Design（设计）
3. Development（开发）
4. Stabilization（稳定）
5. Deployment（部署）

#### Inception 阶段：构思与需求识别

为了定义和明确一个App的核心定位和功能范围，需思考以下问题：

- 是否存在类似的应用？我们的App有何独特之处？
- 是否需要集成已有的企业系统或API？
- 目标用户是谁？他们在移动场景下有怎样的需求？
- 如何利用设备特性（如相机、定位、传感器）来增加价值？

辅助分析方法：

- 定义 Actor：即用户或角色（如游客、注册用户、管理员）
- 定义 Use Case：即用户意图或操作（如浏览商品、下单、评价）

同时，需设定清晰目标：

- 设计目的是什么？是营销推广、数据采集、服务交互？
- 用户在什么场景下使用它？他们期望完成什么操作？
- 不应试图“一网打尽”，需明确功能边界，聚焦关键价值点。

#### Design 阶段：用户体验与界面设计

设计阶段包含两个层面：用户体验设计（UX）与用户界面设计（UI）

用户体验设计：

- UX 通常通过 wireframe 或 mockup 完成，用于构思功能流程与交互逻辑。
- 不涉及颜色和图像，仅关注功能节点的组织与布局。
- 需考虑目标平台（iOS/Android）的设计指南和用户习惯：

iOS 设计规范：
https://developer.apple.com/design/human-interface-guidelines/

Android Material Design：
https://developer.android.com/design

平台差异示例：

- iOS 无物理返回键，需使用 Navigation Controller 组件引导导航。
- 平板设备可将多页内容合并在一屏，需调整信息密度与布局。

用户界面设计：

- UI 是在UX之上添加颜色、图像、动画、字体等视觉要素。
- 专业的UI能提升App的美感、可读性与品牌识别度。
- 相同App在不同平台UI可能略有不同，但其UX结构应保持一致。

#### Development 阶段：开发与功能构建

- 开发阶段可与设计并行，建议尽早构建原型而非仅停留于概念动画。
- 推荐快速实现一个“可运行原型”，验证功能是否可行并估算工作量。
- 原型不等于最终产品，但可提前发现技术瓶颈和用户流程障碍。
- 原型常用于内部评审、早期测试与向投资人演示。

#### Stabilization 阶段：测试与优化

该阶段目标为提升App稳定性、可用性与性能，常与开发阶段重叠进行。

典型应用状态：

- Prototype：功能不全，仅用于验证思路，Bug很多；
- Alpha：功能大致完成，尚未广泛测试，存在已知严重问题；
- Beta：绝大部分功能完备，进入轻量测试与优化阶段；
- Release Candidate：全部功能完成，准备发布，问题微小。

建议：

- 测试应从Alpha阶段开始介入；
- 不同阶段应明确对应目标与测试策略；
- 可使用TestFlight（iOS）或内测通道（Android）邀请外部用户参与测试。

#### Deployment 阶段：发布与分发

iOS应用发布方式：

- Ad-Hoc：用于开发测试，可部署到有限设备
- In-House：企业分发，不需上架App Store
- App Store：最终用户分发平台

iOS常见证书类型：

| 证书类型                 | 用途描述                            |
| ------------------------ | ----------------------------------- |
| iOS Development          | 调试测试所需证书                    |
| iOS Distribution         | 用于App Store发布或企业In-House部署 |
| Developer ID Application | 用于Mac App非App Store发布          |

Android签名与发布：

- 所有Android App必须签名，通常开发者自签证书。
- 签名文件用于保证App来源、身份验证与版本更新兼容。
- Android生态支持多渠道分发：Google Play、应用宝、APK站等。
- 相关构建与签名细节将在后续章节详细说明。

#### App上线后的分析与优化（Performance Tracking）

上线并不是终点，而是优化迭代的开始。需要进行如下指标追踪：

- 总下载量与活跃用户数（DAU/MAU）
- 平均使用时长、会话深度
- 用户留存率与转化率
- App内收入（如广告、内购）

开发者常采用MVP策略：

- 先发布最小可行版本，尽快收集市场反馈；
- 根据用户意见与数据分析持续优化；
- 敏捷迭代，逐步扩大功能与完善体验；

### 第三章

#### IDE基本概念

- IDE = Integrated Development Environment（集成开发环境）
- 用于在PC上开发移动应用，通常包含：
  - 源代码编辑器
  - 编译器/解释器
  - 调试器
- 写好程序后，可上传到手机运行
- 某些设备需安装专用SDK（如Nokia S60）

#### 常见开发工具分类

- **Android常见工具**：
  - Android Studio、Eclipse、AIDE、App Inventor、DroidScript、CppDroid
- **iOS常见工具**：
  - Xcode、AppCode、CodeRunner、Atom、Sublime Text
- **跨平台工具**：
  - React Native、Flutter、Cordova、Unity、Unreal、Cocos、PhoneGap、Corona 等

#### Android开发IDE

- **Android Studio**：
  - 官方IDE，支持Java与Kotlin（简化语法）
- **Eclipse**：
  - 老牌Java开发工具，曾为主流Android开发环境
- **MIT App Inventor**：
  - 图形化Web工具，适合入门开发者

#### iOS开发IDE

- **Xcode**：
  - 官方IDE，语言为Objective-C / Swift
  - 仅能运行在 macOS 上

#### 云端Mac开发环境推荐

- 若无Mac可选用以下云服务：
  - MacInCloud（$25/月）、XCodeClub、VirtualMacOSX
- 使用浏览器访问，形式为远程桌面

#### Windows Phone开发工具

- **Microsoft XNA**（示例）
  - 使用C#开发
  - 包含加速度计模拟器等特殊功能

#### React Native（跨平台）

- 链接：[React Native](https://facebook.github.io/react-native/)
- 使用JavaScript + React 编写原生App
- 和Android/iOS使用相同的原生UI控件
- 热门企业广泛采用

#### Flutter（跨平台）

- 链接：[Flutter官网](https://flutter.dev/)
- Google推出，2017年发布
- 语言：Dart
- 引擎采用C++开发，支持Skia渲染，跨平台效率高

#### Apache Cordova（跨平台）

- 链接：[cordova.apache.org](https://cordova.apache.org/)
- 使用HTML5 + CSS + JS开发App
- 使用平台封装访问传感器、网络等能力
- 适合Web开发者转向App开发

#### 游戏引擎基础（Game Engine）

组成部分包括：

- 主程序逻辑
- 渲染引擎（2D/3D图像渲染）
- 音频引擎（背景音效）
- 物理引擎（实现真实运动碰撞）
- 人工智能模块（非主程序中）

#### 游戏引擎中的帧概念（Frame）

- 每帧绘制一个完整画面，更新角色/元素
- 所有更新先写入缓冲区，再复制到屏幕
- 保证动画流畅，类似电影的帧机制

#### Cocos引擎

- 链接：[Cocos](https://www.cocos.com/en)
- 开源2D/3D图形引擎 + 内容创作平台
- 支持JavaScript与TypeScript
- 分支版本：
  - Cocos2d-x、Cocos Creator 2.x、3.x（2021+）

#### Unity引擎

- 链接：[Unity](http://unity3d.com/)
- 跨平台游戏开发引擎
- 语言：C#
- 支持Web、PC、移动等多平台

#### Unreal引擎

- 链接：[Unreal Engine](https://www.unrealengine.com/)
- Epic Games开发，图形性能极强
- 语言：C++

#### 小程序（Mini Program）

- 微信、支付宝、百度等平台推出轻应用
- 特点：
  - 无需安装，支持扫码/搜索/分享打开
  - 占用空间小、启动快、体验接近原生App
- 架构：
  - 底层为原生容器
  - 上层为WXML（结构）、WXS（脚本） + JavaScript
  - 类似Web前后端架构

#### 小程序开发工具

- 示例：微信开发者工具
- 链接：[WeChat DevTools](https://developers.weixin.qq.com/miniprogram/en/dev/devtools/devtools.html)

### 第五章 安卓概论

#### XML简介

- XML 与 HTML 都源于 SGML（标准通用标记语言）
- HTML 用于网页显示，XML 用于描述和存储数据结构
- XML 格式规则：
  - 标签成对出现，正确嵌套
  - 单标签要以 `/` 结束
  - 必须有且仅有一个根元素
- XML 结构是一棵树（如 `<person>` 包含 `<name>`, `<email>`）

#### Android Manifest 示例

```xml
<manifest package="com.example.helloandroid">
    <application android:icon="@drawable/icon" android:label="@string/app_name">
        <activity android:name=".HelloAndroid" android:label="@string/app_name">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

#### Hello World 示例

- 使用 ConstraintLayout 居中显示 "Hello World"
- activity_main.xml 中用 TextView，MainActivity.java 中通过 `setContentView()` 绑定布局
- 使用 `EdgeToEdge.enable(this)` 和 `ViewCompat.setOnApplyWindowInsetsListener()` 处理系统窗口边缘

#### Android Layout 基础

- 每个View需要唯一ID，例如：`android:id="@+id/my_button"`
- 常用布局：
  - FrameLayout：控件重叠显示
  - LinearLayout：控件线性排列（水平/垂直）
  - RelativeLayout：控件相对排列（如`layout_below`）
  - TableLayout：按行列布局，支持`layout_column`和`layout_span`
  - ConstraintLayout：最新推荐，支持拖拽与约束定位

#### ConstraintLayout常用约束

```xml
app:layout_constraintTop_toTopOf="parent"
app:layout_constraintLeft_toRightOf="@id/buttonA"
app:layout_constraintHorizontal_bias="0.3"
```

#### ScrollView用法

```xml
<ScrollView android:layout_width="match_parent" android:layout_height="match_parent">
    <RelativeLayout android:layout_width="match_parent" android:layout_height="wrap_content"> ... </RelativeLayout>
</ScrollView>
```

#### HCF Calculator示例（Design 1）

- 全部逻辑写在 `MainActivity.java` 中，结构简单不够模块化
- 通过 `EditText` 获取两个输入并转换为整数
- 使用 `for` 循环遍历求最大公因数（Highest Common Factor）

#### HCF Calculator（Design 2）

- 将HCF计算逻辑抽出封装成 `Tools.java` 类
- 更符合面向对象设计
- 更符合 MVC 架构：
  - Model：`Tools.java`
  - View：布局XML
  - Controller：`MainActivity.java`

#### Android常见设计模式

- MVC（Model-View-Controller）：本章示例采用
- MVP（Model-View-Presenter）
- MVVM（Model-View-ViewModel）

#### 动态布局：ListView基础

- ListView + Adapter + 数据
- Adapter 类型：
  - ArrayAdapter：只支持一行文字
  - SimpleAdapter：支持复杂布局
  - SimpleCursorAdapter：从数据库Cursor读取

#### ListView 示例流程

1. 布局文件使用 `ListView` 控件
2. 每行布局定义在 `simplerow.xml`
3. 主程序创建 `ArrayAdapter` 绑定数据源
4. 调用 `listView.setAdapter(adapter)` 显示内容

```java
String[] planets = {"Mercury", "Venus", "Earth", ...};
ArrayList<String> planetList = new ArrayList<>(Arrays.asList(planets));
ArrayAdapter adapter = new ArrayAdapter<>(this, R.layout.simplerow, planetList);
listView.setAdapter(adapter);
```

#### 尺寸单位说明

| 单位     | 说明                       |
| -------- | -------------------------- |
| px       | 像素                       |
| in       | 英寸                       |
| mm       | 毫米                       |
| pt       | 磅，1/72 英寸              |
| dp / dip | 密度无关像素，推荐用于布局 |
| sp       | 可缩放像素，推荐用于字体   |

例如：

```xml
<dimen name="textsize">15sp</dimen>
```

Java代码中使用：

```java
textView.setTextSize(getResources().getDimension(R.dimen.textsize));
```

### 第六章 安卓基础

#### Android Activity生命周期

- onCreate()：进入内存
- onStart()：变得可见
- onResume()：获得焦点
- onPause()：失去焦点
- onStop()：不可见
- onDestroy()：被销毁，离开内存

注意：一个Activity可见但未必有焦点

#### Activity之间的切换流程

- A启动B：A的onPause()执行 → B的onCreate(), onStart(), onResume()执行 → 若A不再可见，onStop()也会执行
- 写入数据库等应放在onPause()中执行

#### Intent与Filter

- Intent用于Activity、Service、BroadcastReceiver之间通信
- 显式Intent：指定组件类名
- 隐式Intent：指定动作，由系统匹配Filter决定目标

#### 显式与隐式Intent示例

```java
// 显式
Intent intent = new Intent(this, FooActivity.class);
startActivity(intent);

// 隐式
Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(url));
startActivity(intent);
```

#### 传递数据：基本类型

```java
Intent intent = new Intent(this, SecondActivity.class);
intent.putExtra("ID", 7506);
startActivity(intent);

// 接收
int id = getIntent().getIntExtra("ID", 0);
```

#### 传递数组与对象（需序列化）

```java
intent.putExtra("IntArray", myIntArray);
intent.putExtra("Calendar", myCal);
int[] arr = getIntent().getIntArrayExtra("IntArray");
Calendar cal = (Calendar) getIntent().getSerializableExtra("Calendar");
```

#### 安全启动Intent（防止未找到目标组件）

```java
try {
    startActivity(intent);
} catch (ActivityNotFoundException e) {
    // 处理异常
}
```

#### Service服务概念

- Service适合处理后台任务（不可见）
- 与Activity的区别：UI/可见性
- 多个Service可同时运行，Activity只能一个前台

#### Service两种启动方式

| 方式           | 特点                           |
| -------------- | ------------------------------ |
| startService() | 后台任务，无交互，不返回结果   |
| bindService()  | 支持客户端交互，可获取服务对象 |

#### Service生命周期简述

- onCreate(): 初始化
- onStartCommand(): 响应startService()
- onBind(): 响应bindService()
- onDestroy(): 释放资源

#### startService()示例简述

- 创建类继承Service并重写方法
- 定义服务：

```xml
<service android:name=".MyService" />
```

- 启动：

```java
startService(new Intent(this, MyService.class));
```

- 停止：

```java
stopService(new Intent(this, MyService.class));
```

- 可通过返回值控制被杀后是否重启：

```java
return START_STICKY; // 自动重启但不重发Intent
```

#### bindService()示例简述

- 创建ServiceBinder子类返回服务实例
- 创建ServiceConnection对象处理绑定状态
- 调用bindService()和unbindService()

```java
bindService(intent, serviceCon, Context.BIND_AUTO_CREATE);
unbindService(serviceCon);
```

- 可通过服务调用方法交互

#### Data Storage机制

- 跨Activity或App数据共享
- 方法：
  - SharedPreferences（轻量级键值对）
  - File I/O（本地私有文件）

#### SharedPreferences示例

```java
// 读取
SharedPreferences settings = getSharedPreferences("MyPrefs", MODE_PRIVATE);
boolean silent = settings.getBoolean("silentMode", false);

// 写入
SharedPreferences.Editor editor = settings.edit();
editor.putBoolean("silentMode", true);
editor.commit();
```

#### 文件读写（File I/O）

```java
// 写文件
FileOutputStream fos = openFileOutput("hello.txt", Context.MODE_PRIVATE);
fos.write("hello world".getBytes());
fos.close();

// 读文件
FileInputStream fis = openFileInput("hello.txt");
int c = fis.read();
fis.close();
```

#### 简单图形：按钮控制图像左右移动

- 使用RelativeLayout.LayoutParams获取和设置图像位置
- 控制margin并判断边界

```java
par.leftMargin -= 5;  // 向左移动
par.leftMargin += 5;  // 向右移动
image.setLayoutParams(par);
```

- 获取屏幕宽度：

```java
Display display = getWindowManager().getDefaultDisplay();
Point size = new Point();
display.getSize(size);
int screen_width = size.x;
```

#### 触控拖动图像

- 设置OnTouchListener
- 获取触摸位置：`event.getRawX()`, `event.getRawY()`
- 更新图像位置：

```java
par.leftMargin = x - par.width / 2;
par.topMargin = y - par.height / 2;
image.setLayoutParams(par);
```

#### 背景音乐播放（MediaPlayer）

```java
MediaPlayer player = MediaPlayer.create(this, R.raw.xxx);
player.start();      // 播放
player.pause();      // 暂停
player.stop();       // 停止
```

- 音频文件需放入 `res/raw` 目录

#### 音效播放（SoundPool）

- 小于1MB音频可用SoundPool更高效
- 支持 `.ogg` 更好

```java
SoundPool soundPool;
soundPool = new SoundPool.Builder().setMaxStreams(4).build();
soundPoolMap.put(1, soundPool.load(this, R.raw.xxx, 1));
soundPool.play(1, leftVol, rightVol, 1, 0, 1f);
```

- 使用AudioManager获取音量：

```java
AudioManager am = (AudioManager) getSystemService(Context.AUDIO_SERVICE);
float leftVol = am.getStreamVolume(...) / am.getStreamMaxVolume(...);
```

---

### 第七章 图片音频和视频开发

第七章主要讲了 图片音频和视频开发

- Image：有下面这么几种类型 （分别是压缩类型，多少位的色深，特点...）

  - JPEG （Joint Photographic Experts Group）(lossy compression，8-bit color depth，高质量但小文件，照片和网页照片，高性能压缩) 总色彩 = 256×256×256 = 16,777,216


  - PNG （Portable Network Graphics）（lossless compression，same，增加对alpha通道的支持，所以非常适合透明图像，含文字的网页图像或要清晰边缘的图像） 总色彩 = 256×256×256 = 16,777,216

  - GIF（Graphics Interchange Format）（lossless compression，八位色彩256种颜色，色彩有限，支持动画和透明，简单动画和图标类网页图像）

  - TIFF（Tagged Image File Format）（可选lossless或lossy，8/16色深，多图层和透明通道，多种色彩空间，用于印刷级图像保留与专业摄影，no网页,体积较大）TIFF 更适合打印，PNG 更适合屏幕。

| 格式     | 压缩类型  | 色彩支持                | 透明支持 | 动画支持 | 文件大小 | 常见用途           |
| -------- | --------- | ----------------------- | -------- | -------- | -------- | ------------------ |
| **JPEG** | 有损      | 24位色（RGB 8位×3）     | 否       | 否       | 小       | 照片、网页图片     |
| **PNG**  | 无损      | 24位色 + 8位透明        | 是       | 否       | 中等     | 带透明背景图、图标 |
| **GIF**  | 无损      | 8位（256色）            | 是       | 是       | 小       | 简单动画、表情包   |
| **TIFF** | 有损/无损 | 8/16位（RGB/CMYK/灰度） | 是       | 否       | 大       | 专业摄影、印刷     |

- **Audio**
  - 两个概念，采样和量化（sampling and quantization）采样是在时间上对连续模拟信号进行离散化（例：每秒采样 44,100 次）。量化是每个采样值映射到离散的数值等级（如 8位、16位、24位等）。
  - WAV（Waveform Audio File Format）
  - MP3（MPEG Audio Layer 3）
  - AAC（Advanced Audio Coding）
  - FLAC（Free Lossless Audio Codec）
  - Ogg（Ogging）
  - Preparing Audio Effect（制作音效）

| 格式             | 压缩类型         | 是否保留原始音质 | 文件大小 | 常见用途                 | 特点             |
| ---------------- | ---------------- | ---------------- | -------- | ------------------------ | ---------------- |
| **WAV (PCM)**    | 无压缩           | ✅ 是             | 极大     | 音频编辑、原始录音       | 高保真           |
| **MP3**          | 有损             | ❌ 否             | 小       | 流媒体、下载音乐         | 支持 VBR，兼容广 |
| **AAC**          | 有损             | ❌ 否（较高质量） | 小       | Apple、YouTube、APP      | 比 MP3 更高效    |
| **FLAC**         | 无损压缩         | ✅ 是             | 中-大    | 音乐收藏、音响发烧       | 保留全部音质     |
| **Ogg (Vorbis)** | 有损（容器格式） | ❌ 否             | 小       | 游戏、复杂音乐、开源应用 | 比 MP3 表现更好  |

- **Video**

| 格式    | 类型 | 编解码支持              | 文件大小 | 兼容性         | 常见用途              | 特点                   |
| ------- | ---- | ----------------------- | -------- | -------------- | --------------------- | ---------------------- |
| **MP4** | 容器 | H.264 + AAC 等          | 小-中    | ✅ 高           | 视频播放、APP、流媒体 | 主流、推荐             |
| **AVI** | 容器 | 多种                    | 大       | ✅ 中           | 老系统、Windows       | 老格式，低压缩效率     |
| **MOV** | 容器 | Apple 编码              | 中等     | ⚠ 需支持播放器 | Mac/iOS 视频编辑      | 高质量，苹果专属       |
| **MKV** | 容器 | 多种（支持字幕/多音轨） | 中-大    | ⚠ 依赖播放器   | 高清电影、动漫        | 多轨、字幕、多平台支持 |

### 第八章 处理多线程和并发的问题（看起来比较重要）

介绍移动应用中如何处理多线程和并发的问题。

1. 第一个概念，进程是什么，线程是什么

   - 进程是应用程序的基本执行单位；彼此之间**不共享**状态或内存；上下文切换成本较高（开销大）。
   - 线程同一应用中可以有多个线程；线程之间可以**共享状态和内存**；适合进行并行计算。

2. UI线程（是主线程）Android应用的UI线程（主线程）只能有一个**。

   - 用于处理View（布局）和 ViewGroup（小部件），所有事件的处理队列（按钮什么的）
   - 如果有多个线程同时访问 UI，会出错（Android UI 线程不是线程安全的）
   - 长时间任务（例如下载）不应在 UI 线程中执行，否则会**卡顿甚至被系统杀掉**
   - 这解释了为什么你不能在 UI 线程中执行耗时任务，否则用户体验会很差。

3. 主线程

   - 两条重要规则：
     1. 不要阻塞 UI 线程
     2. 不要从 UI 线程以外的线程访问 UI 工具包
   - 举例：你要在 UI 上更新图片、文本，**只能在主线程中做**。如果你用后台线程更新 UI，就会抛出异常。

4. 线程（Thread）与任务（Runnable）

   - | 项目       | 描述                                           |
     | ---------- | ---------------------------------------------- |
     | `Thread`   | 控制执行流程的对象。通过 `.start()` 启动执行。 |
     | `Runnable` | 封装一个可执行任务，需实现 `.run()` 方法。     |

   - ```java
     new Thread(new Runnable() {
         public void run() {
             // 你的任务逻辑
         }
     }).start();
     ```

5. 常见错误示例与修复

   ❌ 错误示例（无线程，直接访问网络）：

   ```java
   Bitmap b = loadImageFromNetwork(url); // 在UI线程中执行
   mImageView.setImageBitmap(b);
   ```

   > 会造成**UI线程阻塞**，尤其网络慢时，导致崩溃。

   ❌ 错误线程示例（虽然用了线程，但更新了UI）：

   ```java
   new Thread(new Runnable() {
       public void run() {
           Bitmap b = loadImageFromNetwork(url);
           mImageView.setImageBitmap(b); // ❌ 非主线程中更新UI
       }
   }).start();
   ```

   > 会导致**崩溃或UI异常**。

   ✅ 正确修复方法一：`View.post(Runnable)`

   ```java
   mImageView.post(new Runnable() {
       public void run() {
           mImageView.setImageBitmap(bitmap); // ✅ 由主线程执行
       }
   });
   ```

   - `post()` 将 Runnable 加入 UI 主线程的队列中等待执行。

   ✅ 正确修复方法二：`Executor + Handler`

   ```java
   ExecutorService executor = Executors.newSingleThreadExecutor();
   Handler handler = new Handler(Looper.getMainLooper());
   
   executor.execute(new Runnable() {
       public void run() {
           Bitmap b = loadImageFromNetwork(url);
           handler.post(() -> mImageView.setImageBitmap(b)); // 主线程更新UI
       }
   });
   ```

   - `ExecutorService` 负责后台任务；
   - `Handler.post()` 把UI更新交给主线程执行。

6. 线程控制：如何停止一个线程

   由于 `.run()` 一旦开始不能中途强制终止，因此需要**自己控制循环逻辑**。

   ```java
   boolean threadOn = true;
   
   new Thread(() -> {
       while(threadOn && i < 100) {
           // 循环逻辑
       }
   }).start();
   ```

   - 只需设置 `threadOn = false` 即可终止线程行为。

7. 定时任务与Handler实现倒计时器（Timer）

   | 对象       | 作用说明                                 |
   | ---------- | ---------------------------------------- |
   | `Handler`  | 管理线程间通信，允许将任务放入主线程执行 |
   | `Runnable` | 每隔固定时间被Handler调度运行            |

   示例代码结构（每秒更新一次TextView）：

   ```java
   Handler handler = new Handler();
   Runnable updateTimer = new Runnable() {
       public void run() {
           time--;
           textView.setText(time + "s");
           if (timerEnabled && time > 0)
               handler.postDelayed(this, 1000); // 每秒递归调度
       }
   };
   handler.postDelayed(updateTimer, 1000);
   ```

8. iOS 的并发模型：Grand Central Dispatch（GCD）

   核心理念：

   - **不直接管理线程**；
   - 使用系统提供的**Dispatch Queue（任务队列）**自动安排任务。

   队列种类：

   | 队列类型                          | 特点                     |
   | --------------------------------- | ------------------------ |
   | 主队列 `DispatchQueue.main`       | 串行队列，专门用于UI更新 |
   | 全局队列 `DispatchQueue.global()` | 并发执行，适合后台任务   |
   | 自定义私有队列                    | 可以串行或并发，自由定义 |

   示例代码（异步任务）：

   ```swift
   DispatchQueue.global().async {
       // 后台执行任务
       let result = downloadSomething()
       DispatchQueue.main.async {
           // 回主线程更新UI
           self.label.text = result
       }
   }
   ```

9. 总结：Android 与 iOS 并发对比

   | 特性         | Android                     | iOS (GCD)                   |
   | ------------ | --------------------------- | --------------------------- |
   | 主线程更新UI | 仅主线程可更新              | 同上                        |
   | 后台任务     | Thread / Executor + Handler | Global DispatchQueue        |
   | 定时任务     | Handler + postDelayed       | Timer / DispatchSourceTimer |
   | 难点         | 多线程 UI 非线程安全        | FIFO队列控制任务顺序        |

### 第九章 iOS Apps Development Environment概论 （不是很重要）

#### 一、iOS 开发生态与基本模式

##### iOS生态概览

- iOS SDK 自 2009 推出
- App 发布渠道：**Apple App Store**
- 收益模式：
  - 标准抽成：**开发者 70% / Apple 30%**
  - 小型企业计划（年收入 <$1M）：**Apple 仅收 15%**
- 支持 In-App Purchase (IAP)、家庭共享（不支持 IAP）
- 成为开发者：注册 Apple Developer（年费 $99/$299）

------

#### 二、iOS 技术栈与系统架构

#####  四层技术架构（Slides 6–9）

| 层级   | 框架功能                                             |
| ------ | ---------------------------------------------------- |
| UI层   | 视图、控件、事件响应（UIKit）                        |
| 媒体层 | 音视频播放、图形渲染、动画（AVKit, CoreAnimation）   |
| 服务层 | 文件、网络、定位、iCloud（Foundation, CoreLocation） |
| 核心层 | 硬件访问、内存、底层网络（IOKit, CoreBluetooth）     |

![ios_layer](https://ulanqabbadguy.github.io/mypage/assets/images/ios_layer.png)

------

####  三、语言与开发环境介绍

#####  Objective-C（Slide 11–12）

- 面向对象扩展语言，源于 SmallTalk，Apple 自 NeXT Step 沿用
- 方法调用语法：`[object method]`
- 示例代码：

```objc
@property float centerX;
- (void) move: (float)dx: (float)dy;
[fireball move: 10: 10];
```

#####  Swift（Slide 13）

- Apple 自研现代语言，摒弃 C 的繁复语法
- 语法借鉴 Haskell、Python、C#，强调：**安全 + 简洁 + 强类型**

#####  面向对象复习（Slides 14–16）

- `Class`：类定义
- `Instance`：类的实例
- `Method`：对象的接口
- `Property` = Getter + Setter组合

#####  Xcode（Slides 17–21）

- macOS 专用 IDE
- 包含编译器、模拟器、UI 编辑器（Storyboard/SwiftUI）
- 云方案：MacInCloud, XCodeClub
- 模拟器可调缩放

------

####  四、iOS 应用架构与主要组件（Storyboard 项目）

#####  核心组成结构（Slides 23–28）

| 组件              | 功能                                    |
| ----------------- | --------------------------------------- |
| `main.m`          | 程序主入口，仅在 Objective-C 项目中存在 |
| `AppDelegate`     | 管理生命周期（启动、终止）              |
| `SceneDelegate`   | 多窗口支持（iOS 13+）                   |
| `Main.storyboard` | 拖拽式 UI 视图容器                      |
| `ViewController`  | 控制逻辑，如按钮响应等                  |

🧠 小贴士：iOS 13 起将部分 `AppDelegate` 职责移交给 `SceneDelegate`

------

####  五、Hello World 示例（Storyboard 项目）

#####  Objective-C 项目流程（Slides 30–47）

1. 创建新项目 → 选择语言为 Objective-C
2. 在 `Main.storyboard` 拖入 Label & Button
3. **Ctrl + 拖动**绑定组件：

```objc
@property (weak, nonatomic) IBOutlet UILabel *label1;
- (IBAction)button1:(id)sender;
```

1. 实现方法逻辑：

```objc
- (IBAction)button1:(id)sender {
    label1.text = @"Hello iOS!!!";
}
```

🧠 内存管理：

- `strong`：强引用，决定对象生命周期
- `weak`：弱引用，不影响生命周期，防止循环引用

------

#####  Swift 项目流程（Slides 48–57）

1. 创建项目，选择语言为 Swift
2. 拖入 UI 控件（Label & Button）
3. 使用 Ctrl + 拖动进行绑定：

```swift
@IBOutlet weak var label1: UILabel!
@IBAction func button1(sender: AnyObject) {
    label1.text = "Hello iOS!!!"
}
```

#####  Objective-C vs Swift 差异对比（Slide 58）

| 特性     | Objective-C               | Swift                |
| -------- | ------------------------- | -------------------- |
| 语法风格 | `[]` 语法                 | 点语法               |
| 引用管理 | `@property (weak/strong)` | `@IBOutlet weak var` |
| 文件结构 | `.h` + `.m`               | 单 `.swift` 文件     |
| 接口声明 | `IBAction/IBOutlet`       | 同上但更简洁         |

------

####  六、页面导航控制：Navigation Controller（Slides 60–70）

#####  实现步骤：

1. 选中初始 View → `Editor → Embed In → Navigation Controller`
2. 拖入多个 `ViewController` 作为“页面”
3. 使用“Bar Button Item”并 `Ctrl + 拖动` 添加转场（segue）→ 类型选择“Show”
4. 自动生成返回按钮
5. 创建各自的控制器类（继承自 `UIViewController`），绑定视图

------

####  七、SwiftUI 入门（Slides 72–81）

#####  SwiftUI 特点

- 2019年发布的新UI框架，**声明式编程**方式构建视图
- 支持 iOS 13+ 和 Xcode 11+
- UI 由代码描述，而非拖拽
- 跨平台（iOS、macOS、watchOS）统一

#####  示例代码：

```swift
struct ContentView: View {
    @State var message = "Hello World!"
    var body: some View {
        VStack {
            Text(message)
            Button("Click Me!") {
                message = "Hello iOS!!!"
            }
        }
        .padding()
    }
}
```

#####  优缺点分析：

| 优势               | 限制                       |
| ------------------ | -------------------------- |
| 结构简洁，实时预览 | 仅支持 iOS 13+             |
| 跨平台重用组件     | 与 Storyboard 迁移不兼容   |
| 支持模块化 UI      | 社区资源较少，学习曲线较陡 |

------

####  八、UI开发演化趋势（Slide 82）

| 工具                 | UI构建方式              |
| -------------------- | ----------------------- |
| Eclipse (旧 Android) | 手写 XML                |
| Android Studio       | ConstraintLayout + 拖拽 |
| Xcode + Storyboard   | 拖拽式可视化            |
| Xcode + SwiftUI      | 声明式代码 + 实时预览   |

------

####  九、复习建议与重点

| 类别     | 建议掌握内容                                      |
| -------- | ------------------------------------------------- |
| Swift    | 属性声明、函数书写、控件绑定                      |
| App架构  | AppDelegate、SceneDelegate职责与启动流程          |
| 开发工具 | Xcode 使用、模拟器操作                            |
| 导航跳转 | Navigation Controller 使用与多页面绑定            |
| SwiftUI  | 声明式 UI 编程方法，@State 使用，跨平台优势与限制 |

### 第十章 Swift Programming

八个核心概念：Constant & Variable，Flow Control，Class，Function，String & Array，Optionals（可选类型），Image，Touching Events

#### 第3–6页：常量与变量 Constant & Variable

变量定义方式：

Swift 中可以用 `var` 声明变量，其格式是：

```swift
var width: Int = 5
```

- `var`：表示变量
- `width`：变量名
- `Int`：类型
- `5`：初始值

也可以省略类型（类型推断）：

```swift
var width = 5
```

常量定义方式：

使用 `let` 表示**不可变**：

```swift
let A = 10
let message = "Hello World"
```

优势：

- 更安全（不能被修改）
- 编译器可以优化内存性能

#### 第4–5页：基本数据类型（Primitive Data Types）

| 类型        | 说明       | 示例                      |
| ----------- | ---------- | ------------------------- |
| `Int`       | 整型       | `var a: Int = 10`         |
| `Float`     | 单精度浮点 | `var b: Float = -0.333`   |
| `Double`    | 双精度浮点 | `var c = 0.333`           |
| `Character` | 单个字符   | `var ch: Character = "c"` |
| `String`    | 字符串     | `var str = "hi"`          |
| `Bool`      | 布尔       | `var flag = true`         |

#### 第6页：图像相关变量类型（Image-Specific Types）

在GUI界面中用于图像展示的变量类型有：

- `UIImageView`：用于展示一张图像
- `UILabel`：用于展示只读文字
- `UIButton`：用于触发交互事件的按钮

这些类型本质是 Swift 中的类（Class），实例化后可以放置在屏幕上。

#### 第7–10页：流程控制（Flow Control）

Swift 提供多种流程控制结构，包括条件判断、循环等。

**条件判断**

```swift
var a = 0
var b = 1

if (a < b) {
    // 如果 a 小于 b，执行这里
} else {
    // 否则执行这里
}
```

说明：

- `if...else` 与 C/Java 相似。
- 圆括号可以加也可以不加（Swift 不强制要求）。

**循环结构**

**1. For-in Loop**

```swift
for i in 0...b-1 {
    // i = 0, 1, 2, ..., b-1
}
```

- `0...b-1` 是闭区间操作符，等价于 `[0, b-1]`
- 若使用 `..<` 则为左闭右开区间。

**2. while Loop**

```swift
var count = 0
while count < 10 {
    print("count is \(count)")
    count += 1
}
```

**3. repeat-while Loop**

```swift
var count = 0
repeat {
    print("count is \(count)")
    count += 1
} while count < 10
```

- `repeat-while` 至少执行一次。

#### 第11–14页：类（Class）基本用法

面向对象范例（第12页）

以游戏中的“火球”Fireball 为例：

- 每个火球是一个对象（实例）
- 拥有属性（x, y 坐标，半径）
- 可以调用方法如 `move()` 进行移动

类的定义（第13页）

```swift
class Fireball {
    var centerX: Float
    var centerY: Float
    var radius: Float

    init(centerX: Float, centerY: Float, radius: Float) {
        self.centerX = centerX
        self.centerY = centerY
        self.radius = radius
    }

    func move(_ moveX: Float, _ moveY: Float) {
        self.centerX += moveX
        self.centerY += moveY
    }

    deinit {
        // 析构函数，释放资源
    }
}
```

关键说明：

- `init()` 是构造函数
- `self` 表示当前实例（等价于 Java 的 `this`）
- `deinit` 是析构函数（释放资源

类的使用与可选类型（第14页）

```swift
var fireball1 = Fireball?
fireball1 = Fireball(centerX: 7.0, centerY: 5.0, radius: 6.0)
fireball1!.move(1.0, 1.0)
```

- `Fireball?` 是**可选类型**（optional），表明变量可能为 nil。
- `!` 表示强制解包，告诉编译器“我确定这里不是 nil”。（nil约等于null）

⚠️ 若实际为 nil 而强制解包会崩溃。

#### 第15–17页：基本指针概念

在 Swift 中，**对象（如 Fireball）通常在运行时动态创建（dynamic allocation）**，变量本质上存储的是指向内存中该对象的指针（即引用）。

```swift
var fireball1 = Fireball?
fireball1 = Fireball(centerX: 10.0, centerY: 10.0, radius: 5.0)
```

说明：

- `Fireball?` 是一个可以为 nil 的 Fireball 实例引用。
- `fireball1` 实际上持有的是创建出来的对象的地址。
- 使用 `!` 访问对象属性或方法：`fireball1!.move(1.0, 1.0)`

#### 对象的创建和移除

![对象的创建和移除](https://ulanqabbadguy.github.io/mypage/assets/images/ios_pointer.png)

- 创建了两个 Fireball 实例，各自存放在内存中不同位置
- 每次调用 `move()` 会修改对应对象的 `centerX`, `centerY`
- 将 `fireball1`、`fireball2` 设为 `nil` 之后，原来的对象就失去引用，等待 ARC（自动引用计数）回收。

#### 内存泄漏

![内存泄漏](https://ulanqabbadguy.github.io/mypage/assets/images/mem_leaky.png)

这里的问题是：**原本 fireball1 指向一个对象 A**，后续 fireball2 也指向 A，当 fireball1 和 fireball2 都设为 nil 时，如果有“循环引用”或 ARC 无法判断对象已无引用，内存将不会被释放，造成“Memory Leak”。

#### “self” 关键字（类似 Java 的 this）

当我们在类的方法中引用当前对象自身的属性或方法时，用 `self`：

```swift
class Fireball {
    var centerX: Float
    var centerY: Float

    func move(_ dx: Float, _ dy: Float) {
        self.centerX += dx
        self.centerY += dy
    }
}
```

作用：

- `self.centerX` 明确指出访问当前对象的 `centerX` 属性，避免变量命名冲突。
- 图解展示：对象实例中包含一个隐式指针 `self` 指向自己。

![self](https://ulanqabbadguy.github.io/mypage/assets/images/self.png)

#### 函数的参数命名机制

Swift 函数的每个参数既有**内部名称**（parameter name）也可以有**外部名称**（argument label）。

```swift
func someFunction(firstParameterName: Int, secondParameterName: Int) {
    // 使用 firstParameterName 和 secondParameterName 进行计算
}
someFunction(firstParameterName: 1, secondParameterName: 2)
```

说明：

- `firstParameterName` 是内部变量名（在函数体内使用）
- 如果没有显式的 argument label，那么调用时也用内部名

#### 使用外部参数名（Argument Label）

```swift
func someFunction(argumentLabel parameterName: Int) {
    // 使用 parameterName
}

someFunction(argumentLabel: 7506)
```

- `argumentLabel` 是函数调用时用的名字
- `parameterName` 是函数内部用的变量名
- 两者通过冒号关联

作用：使函数调用**更像自然语言**，提升可读性。

#### 示例函数 greet

```swift
func greet(person: String, from hometown: String) -> String {
    return "Hello \(person)! Glad you could visit from \(hometown)."
}

print(greet(person: "Bill", from: "Cupertino"))
```

结果输出：

```csharp
Hello Bill! Glad you could visit from Cupertino.
```

说明：

- `from` 是外部参数名，`hometown` 是内部变量名

#### 多个参数的外部命名

```swift
func sayHello(to person: String, and anotherPerson: String) -> String {
    return "Hello \(person) and \(anotherPerson)!"
}

print(sayHello(to: "Bill", and: "Ted"))
```

说明：

- `to` 和 `and` 是外部参数名，调用时必须使用。
- 好处：使函数调用语义清晰

#### 省略外部参数名（使用 `_`）

```swift
func someFunction(_ first: Int, second: Int) {
    print(first, second)
}

someFunction(1, second: 2)
```

说明：

- `_` 表示调用时不需要外部参数名

#### 三种参数写法总结

1. 带外部参数名：

```swift
func ABC(e1 i1: Int, e2 i2: Int) { ... }
ABC(e1: 1, e2: 2)
```

1. 只有内部名（系统自动当作外部名）：

```swift
func ABC(i1: Int, i2: Int) { ... }
ABC(i1: 1, i2: 2)
```

1. 无外部名：

```swift
func ABC(_ i1: Int, _ i2: Int) { ... }
ABC(1, 2)
```

#### 默认参数值

```swift
func someFunction(parameterWithoutDefault: Int, parameterWithDefault: Int = 12) {
    print(parameterWithoutDefault + parameterWithDefault)
}

someFunction(parameterWithoutDefault: 3) // 输出 15
someFunction(parameterWithoutDefault: 3, parameterWithDefault: 6) // 输出 9
```

说明：

- 默认值允许你在调用时省略参数
- 默认参数必须放在**最后面**

#### 可变参数（Variadic Parameter）

```swift
func arithmeticMean(_ numbers: Double...) -> Double {
    var total: Double = 0
    for number in numbers {
        total += number
    }
    return total / Double(numbers.count)
}

arithmeticMean(1, 2, 3, 4, 5)  // 返回 3.0
```

说明：

- 使用 `...` 表示该参数可以接收多个输入（类似 C 的 `...args`）
- Swift 每个函数**最多只能有一个 variadic 参数**

#### inout 参数（可变引用）

```swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let temp = a
    a = b
    b = temp
}
```

调用方式：

```swift
var x = 5
var y = 10
swapTwoInts(&x, &y)
```

说明：

- 参数默认是常量，无法在函数体中修改
- `inout` 参数允许函数修改调用者变量的值
- 调用时需要加 `&` 表示传入的是**引用**

#### 类方法与实例方法

```swift
class AClass {
    class func aClassMethod() {
        print("I am a class method")
    }

    class func bClassMethod() {
        aClassMethod()
    }

    func anInstanceMethod() {
        print("anInstanceMethod. Calling bClassMethod().")
        AClass.bClassMethod()
    }
}
```

调用：

```swift
AClass.aClassMethod()

let aClass = AClass()
aClass.anInstanceMethod()
```

输出：

```css
I am a class method
anInstanceMethod. Calling bClassMethod().
I am a class method
```

说明：

- `class func` 表示类方法（可直接用类名调用）
- `func` 是实例方法，必须用对象来调用
- 实例方法中也能调用类方法

#### String

可变字符串（Mutable String）

```swift
var S = "hi"
var S: String = "hi"
var S = String("hi")
```

说明：

- 使用 `var` 声明字符串时，它是可变的。
- 三种写法效果相同，最后一种显式调用构造函数。

不可变字符串（Non-Mutable String）

```swift
let S = "hi"
let S: String = "hi"
let S = String("hi")
```

- 使用 `let` 声明后，该字符串不能再被修改。

字符串长度获取

- 使用 `count` 属性（Swift 5及以后）：

```swift
let length = S.count
```

 查找子字符串

```swift
var S = "hello Swift"
var range = S.range(of: "Swift")
```

说明：

- `range` 返回一个可选类型 `Range<String.Index>?`
- 若存在，`range` 表示子字符串的位置（起始和长度）
- 类似 Objective-C 中的 `NSRange`。

#### 基本数据类型数组（Array of Primitive Types）

可变数组（Mutable）

```swift
var myArray: [Int] = [555, 666]
var myArray = [555, 666]
```

常量数组（Constant）

```swift
let myArray: [Int] = [555, 666]
let myArray = [555, 666]
```

说明：

- `var` 可修改元素内容
- `let` 则表示整个数组及其元素都不可变

读取和写入元素

```swift
let val = myArray[0]         // 读取
myArray[1] = 777             // 写入（需是 var 声明）
```

------

对象数组（Array of Objects）

可变对象数组（两种写法）：

```swift
// 方式一：初始化时就填入对象
var myObjectArray: [Fireball] = [Fireball1, Fireball2]

// 方式二：先声明空数组，后续 append
var myObjectArray: [Fireball] = []
myObjectArray.append(Fireball1)
myObjectArray.append(Fireball2)
```

常量对象数组：

```swift
let myObjectArray: [Fireball] = [Fireball1, Fireball2]
```

遍历数组

```swift
for i in 0..<myObjectArray.count {
    print("myObjectArray[\(i)].radius = \(myObjectArray[i].radius)")
}
```

输出：

```swift
myObjectArray[0].radius = 6
myObjectArray[1].radius = 4
```

数组总结说明

- Swift 中数组类型定义为 `[Type]`。
- 可存储对象，也可存储基本类型。
- `.count` 可用于获取元素数量。
- 对于对象数组，必须确保数组中所有元素类型一致。

#### Optionals 的定义与用途

在 Swift 中，Optional 是一种**可以存值也可以是 nil 的类型**。定义方式如下：

```swift
var name: String?  // 可能是字符串，也可能是 nil
```

Optional 的目的：

- Swift 是 **强类型语言（Type-Safe）**，不能像 C/C++ 那样随便设置变量为 NULL。
- 为了解决“值不存在”或“操作失败”时的处理，Swift 引入了 `Optional`。

应用场景：

- 某个属性**可有可无**
- 某方法可能**找不到匹配项**
- 某操作可能**失败或出错**
- UI 组件（如 UILabel.text）**一开始就是 nil**
- 管理大内存资源（可能需要临时释放）

转换失败

```swift
let possibleNumber = "123a" //如果是“123”就转换成功了
var convertedNumber: Int? = Int(possibleNumber)

if convertedNumber != nil {
    print("convertedNumber contains value: \(convertedNumber).")
} else {
    print("'\(possibleNumber)' cannot be converted to integer.")
}
```

输出：

> '123a' cannot be converted to integer.

说明：

- 字符串中带有 `a`，转换失败
- `Int("123a")` 返回 nil
- 可选类型优雅地捕捉了这种失败情况

强解包

```swift
let possibleNumber = "1234"
var convertedNumber: Int? = Int(possibleNumber)

if convertedNumber != nil {
    print("convertedNumber contains value \(convertedNumber!).")
}
```

说明：

- `convertedNumber!` 表示**强制解包（Forced Unwrapping）**
- 编译器相信此时一定不是 nil（如果错了会程序崩溃）

| 表达式         | 含义                          |
| -------------- | ----------------------------- |
| `var x: Int?`  | 声明一个可能为 nil 的整型变量 |
| `x = 5`        | 赋值                          |
| `x == nil`     | 判断是否为空                  |
| `x!`           | 强制解包                      |
| `if let y = x` | 安全解包（可选绑定）          |

我们想在界面跳转（Segue）时，将一个文本框中的内容传递给下一个视图控制器进行使用。

示例代码解析：

```swift
override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
    print("enter prepare for segue …")

    if (segue.identifier == "loginToGameBoardSeg") {
        let nav = segue.destination as! UINavigationController
        let vc = nav.topViewController as! GameBoardViewController
        vc.setNavTitle(userNameTF.text!)
    }
}
```

逐句解释：

`override func prepare(...)`

- Swift 中，当你进行 segue（界面跳转）前，系统会自动调用这个方法。
- 你可以在这里提前准备要传递的数据。

`if (segue.identifier == "loginToGameBoardSeg")`

- 判断跳转是否是我们命名的 `"loginToGameBoardSeg"`。
- Segue 的标识符可以在 Storyboard 里设置。

`let nav = segue.destination as! UINavigationController`

- `segue.destination` 是跳转目的地的视图控制器。
- 强制类型转换为 `UINavigationController`（⚠️ 用了 `as!` 强制转型）。
- 如果转型失败，会导致运行时崩溃，开发中应谨慎使用（可用 `as?` 安全转型）。

 `let vc = nav.topViewController as! GameBoardViewController`

- 通过导航控制器获取其**顶部视图控制器**
- 强制转型为我们自定义的 `GameBoardViewController`

`vc.setNavTitle(userNameTF.text!)`

- 将当前界面中的文本框 `userNameTF` 的文字传给下一个控制器。
- `userNameTF.text!`：取出文本框内容（是 `String?` 类型，所以要解包）

⚠️：使用 `!` 强制解包时，**一定要确保不为 nil**，否则会 crash。

| 技术点                                     | 内容                     |
| ------------------------------------------ | ------------------------ |
| `prepare(for:sender:)`                     | 页面跳转前执行的数据准备 |
| `as!`                                      | 强制类型转换             |
| `text!`                                    | 可选类型强制解包         |
| `UINavigationController.topViewController` | 获取导航栈最上层控制器   |

#### UIImage & UIImageView (重要)

| 类型          | 说明                                         |
| ------------- | -------------------------------------------- |
| `UIImage`     | 图像数据的高层抽象类，可以从文件或数据中创建 |
| `UIImageView` | 显示图像的视图容器（可用于静态图或动画序列） |

功能说明：

- `UIImage` 处理图像数据（如从文件读取或网络下载）
- `UIImageView` 是 View（可以被添加到界面上）
- 动画功能：可设置图片序列、频率和动画控制（例如：帧动画）

```swift
// viewDidLoad() 方法回顾
override func viewDidLoad() {
    super.viewDidLoad()
}
// 在界面上显示第一张图片
override func viewDidLoad() {
    let myImage = UIImageView(image: UIImage(named: "puppy.jpeg"))
    view.addSubview(myImage)
    super.viewDidLoad()
}
// 添加第二张图片 与前面类似，只是加载第二张图片。此时，两张图片都显示在屏幕上（默认位置会重叠）。
let myImage2 = UIImageView(image: UIImage(named: "tiger.png"))
view.addSubview(myImage2)
// set the location of pictures
myImage2.center = CGPoint(x: 150, y: 200)
// set the size of picture
myImage2.frame = CGRect(x: 0, y: 0, width: 50, height: 25)
// 如果写成了
myImage2.center = CGPoint(x: 150, y: 200)
myImage2.frame = CGRect(x: 0, y: 0, width: 50, height: 25)
// 那么位置会被覆盖，正确顺序是
myImage2.frame = CGRect(x: 0, y: 0, width: 50, height: 25)
myImage2.center = CGPoint(x: 150, y: 200)
// 因为 frame 会影响视图的整体边界，可能会改变中心点坐标。
// 释放图像内存
myImage.deallocate()
myImage2.deallocate()
```

`viewDidLoad()` 是 UIViewController 的生命周期方法之一。

类似于 Android 中的 `onCreate()` 方法。

用于初始化界面、加载视图组件等操作。

`UIImage(named:)` 从资源中加载名为 `"puppy.jpeg"` 的图片。

`UIImageView(image:)` 创建一个图像视图组件。

`view.addSubview(...)` 将图像视图添加到当前界面中（默认左上角对齐）

CGPoint：

- 是一个结构体，表示二维坐标
- `x: 150, y: 200` 表示将图片中心定位到屏幕中的该点位置

Swift 中 **不要求开发者手动释放内存**（使用 ARC 自动管理）。

上面代码通常不需要写，写了也不会报错（只是示意）。

只有极端性能需求下才会考虑手动释放。

#### 触摸事件（Touching Events）

```swift
// 创建一个自定义视图 YourView，继承自 UIView
class YourView: UIView {

    // 用户手指刚触碰到屏幕时调用
    override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
        if let touch = touches.first {
            // 获取触点在当前视图中的坐标
            let currentPoint = touch.location(in: self)
            // 示例操作：将图像移动到触点位置
            image1.center = currentPoint
        }
    }

    // 用户手指在屏幕上滑动时调用
    override func touchesMoved(_ touches: Set<UITouch>, with event: UIEvent?) {
        if let touch = touches.first {
            let currentPoint = touch.location(in: self)
            image1.center = currentPoint
        }
    }

    // 用户手指离开屏幕时调用
    override func touchesEnded(_ touches: Set<UITouch>, with event: UIEvent?) {
        if let touch = touches.first {
            let currentPoint = touch.location(in: self)
            image1.center = currentPoint
        }
    }

    // 处理多点触控：每个触控点的位置都可以被处理
    override func touchesMoved(_ touches: Set<UITouch>, with event: UIEvent?) {
        for touch in touches {
            let newLocation = touch.location(in: self)
            // 示例：可用于绘制多指轨迹或多图像同步移动
        }
    }
}

```

#### 练习

```swift
// 此为练习题解决方案的结构：创建一个带输入、按钮和标签的简单阶乘计算应用
class ViewController: UIViewController {

    // 输入框：用于接受用户输入的整数
    @IBOutlet weak var inputTextField: UITextField!

    // 标签：用于显示计算结果
    @IBOutlet weak var resultLabel: UILabel!

    // 按钮事件：用户点击后触发计算操作
    @IBAction func calculateButtonPressed(_ sender: UIButton) {
        // 使用可选绑定安全提取文本框中的字符串并转换为整数
        if let inputText = inputTextField.text,
           let number = Int(inputText) {

            // 计算阶乘
            var result = 1
            for i in 1...number {
                result *= i
            }

            // 更新结果显示
            resultLabel.text = "Factorial: \(result)"

        } else {
            // 输入无效时的提示信息
            resultLabel.text = "Please enter a valid integer."
        }
    }
}

```

### 第十一章 Sensor & Location Service（传感器与定位服务）不是很重要

| 主题            | 简要说明                                                     | 详细补充说明                                                 |
| --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 传感器概览      | 移动设备与桌面设备区别：有传感器。需在真机上测试，不能用模拟器。 | 智能手机内建多种传感器使其能响应环境变化，如移动、光线、温度等。真机测试可验证功能是否真实有效。 |
| 传感器分类      | 分为运动（如加速度计）、位置（如磁力计）、环境（如光照传感器）。 | 按功能分为三类：运动传感器用于检测设备移动或旋转，位置传感器检测方向或靠近，环境传感器感知周围自然环境。 |
| 传感器实现      | 硬件传感器（真实器件）vs 软件传感器（计算生成，虚拟传感器）。 | 硬件传感器如陀螺仪是物理器件，数据较准确；软件传感器通过算法合成数据，计算量小但依赖基础传感器。 |
| 低通滤波器      | 提取重力信号，平滑数据变化。指数滤波器常用：out = α·out + (1-α)·in。 | 低通滤波器用于保留长期稳定信号如重力，加权前一时刻输出与当前输入，平滑突变值。 |
| 滤波代码示例    | 使用 onSensorChanged 事件分离重力与线性加速度。              | 通过事件回调函数onSensorChanged，使用指数加权方式提取重力，并从原始加速度中扣除它，得到线性加速度。 |
| 传感器特性      | 需关注可用性、量程、精度、功耗等，影响设备适配与耗电。       | 不同设备拥有不同数量与种类的传感器，应在运行前检测是否存在。高功耗传感器应按需启用。 |
| 误差来源        | 噪声：随机跳动；偏差：系统性误差，需校准或补偿。             | 噪声表现为数据随机波动，偏差为系统性误差。应使用滤波器减少噪声，用校准修正偏差。 |
| 坐标系统        | 本地坐标系（手机自身）vs 世界坐标系（地球方向），对方向识别关键。 | 设备坐标系随设备方向而变，世界坐标系固定（如地理方向）。方向识别算法需考虑二者转换。 |
| Manifest注册    | 声明传感器是否必须，建议非必需以增强兼容性。                 | 在AndroidManifest.xml中声明传感器是否为必须项，设置为false能增强程序兼容性。 |
| 电量优化        | 监听器应在 onResume 注册，onPause 注销，避免后台耗电。       | 传感器在后台运行将持续耗电，应在生命周期函数onResume/onPause中注册与注销监听器。 |
| 可用传感器      | 各设备和系统支持不同，常见如加速度计，稀有如温度计。         | 不同品牌设备搭载的传感器种类不同，部分如温度计并非所有型号都支持。应动态检查。 |
| Sensor编程结构  | SensorManager 用于获取与管理传感器，需注册监听器。           | SensorManager提供访问传感器的接口，开发者可注册SensorEventListener来接收传感器事件。 |
| 识别传感器      | getSensorList 获取全部；getDefaultSensor 获取指定类型。      | 调用getSensorList获取所有传感器列表；调用getDefaultSensor获取某种类型的默认传感器。 |
| 监听器结构      | SensorEventListener 有两个方法：onSensorChanged 和 onAccuracyChanged。 | onSensorChanged用于接收新数据，onAccuracyChanged用于通知传感器精度变化，适用于需要高精度应用。 |
| 监听器管理      | onResume/onPause 中注册注销监听器，避免持续耗电。            | 生命周期内注册监听器可减少功耗并避免内存泄漏，onResume中注册，onPause中注销。 |
| 开发建议        | 不要假设传感器一定存在，避免堵塞回调函数，尽量真机测试。     | 建议：避免在监听器中执行耗时操作，始终检查设备是否支持传感器，不使用废弃接口。 |
| 运动传感器      | 如加速度、陀螺仪等，识别移动、旋转等动作。                   | 加速度计用于检测沿xyz轴的线性加速度，陀螺仪用于测量旋转速率，是运动识别的基础。 |
| 位置传感器      | 如距离、磁场传感器，识别方向、靠近耳朵等动作。               | 磁力计检测磁场强度，用于电子罗盘。距离传感器可用于自动熄屏、体感游戏等应用。 |
| 环境传感器      | 检测温度、湿度、光照、气压等，用于自动调节或天气功能。       | 光照传感器自动调节亮度，温度/湿度/气压可用于气象、健康、模拟等应用。 |
| iOS传感器       | CoreMotion 提供加速度、陀螺仪、磁力计、融合后的运动数据。    | Core Motion是iOS的传感器接口框架，提供融合后的高层数据，减少开发难度。 |
| UIDevice API    | iOS中检测电量、朝向、接近等状态。                            | UIDevice类提供设备基本信息与传感器状态，如电量、方向、是否靠近用户等。 |
| 定位原理        | 传感器不能直接提供全球定位，需结合外部来源（GPS、WiFi等）。  | 传感器本身无法得出全球定位信息，只能感知局部变化。需GPS、WiFi等外部信号配合定位。 |
| GPS vs 网络定位 | GPS精度高但耗电，网络精度低但响应快，适用于不同场景。        | GPS精度高但耗电，网络定位快但误差大。可根据场景（导航/后台定位）动态切换。 |
| 定位用途        | 打卡、推荐商店、导航等场景，常需周期更新或地理围栏触发。     | 定位用于地图、社交、商业提醒等场景，常与内容打标签或地理围栏联动使用。 |
| Android定位API  | LocationManager 获取位置；LocationListener 接收更新。        | Android 中 LocationManager 负责位置服务，LocationListener 可接收位置信息更新。 |
| 权限声明        | ACCESS_FINE/COARSE_LOCATION 权限；模拟器需 MOCK_LOCATION。   | Android 需声明定位权限（精确或粗略），模拟器测试时需开启ACCESS_MOCK_LOCATION。 |
| iOS定位         | CoreLocation 框架使用 CLLocationManager 控制定位功能。       | iOS中使用CLLocationManager类处理标准定位、区域监听、信标扫描等功能。 |
| 定位挑战        | 信号噪声、不规则用户行为、多种来源如何融合。                 | 用户行为不确定，定位信号可能受遮挡或漂移，应融合多源信息以提高鲁棒性。 |
| 定位方法        | 通过与多个锚点（如GPS卫星）距离三角定位位置。                | 通过多个基站或卫星的信号距离交叉定位当前坐标，称为三角定位。 |
| 地理围栏        | 注册进入/离开某地的事件，触发指定行为。                      | 开发者可设置特定位置触发事件，适合用于广告推送、游戏机关等地理围栏应用。 |
| Google Map概述  | 可用于导航、交通、地图游戏等应用。                           | Google Maps SDK 支持路径规划、周边查询等服务，是基于位置的应用基础。 |
| 申请地图API     | 登录开发者控制台启用 Maps SDK，生成 API Key。                | 通过Google Cloud Console注册地图服务，启用SDK并获取API Key，用于验证身份。 |
| Android配置     | 需安装 Google Play Services SDK，使用模板或自行配置 XML/Java 文件。 | Android中需安装Google Play Services，模板工程可快速启用地图功能。 |
| Map类型         | 普通、卫星、混合、地形图四种。                               | Google Maps支持四种地图类型，分别为道路图、卫星图、混合图与地形图。 |
| Map功能设置     | 如启用交通图层、设置当前位置、添加标注等。                   | 可调用API设置交通图层、当前位置追踪、自定义标注（如HKU坐标与描述）。 |
| iOS地图使用     | 需参照官方文档设置 iOS 端地图 SDK。                          | iOS开发地图功能需使用对应iOS SDK，配置过程类似，需申请API Key。 |
| 穿戴设备数据    | 手机可接收来自智能手表的心率、步数等健康数据。               | 智能手表等穿戴设备能向手机发送健康数据，如步数、心率等，拓展数据源。 |
| 心率测量原理    | 通过PPG（光电体积描记法）测量血液流动变化。                  | 通过光电传感器监测血液流动变化，识别脉搏频率计算心率。       |
| 步数检测原理    | 加速度变化识别出“步频”与“峰值”节律。                         | 通过检测加速度变化中的规律峰值，识别连续步行动作，转换为步数。 |
| 血压、血氧等    | 通过光学/电阻等方式估算，通常需人工校准。                    | 大多数智能手表能估算血压、血氧等健康指标，但需依赖光学、电阻等非传统方法，并需校准。 |
| 总结            | 重点在如何将传感器/定位功能整合为创新应用，而非API调用本身。 | 如何利用传感器与定位数据创新是关键，应思考如何提升用户体验或产生新功能。 |

### 第十二章 Server Connection

#### 1. 移动App与服务器通信基础

| 知识点              | 说明                                               | 补充                                          |
| ------------------- | -------------------------------------------------- | --------------------------------------------- |
| 获取/更新服务器数据 | 如香港天文台app、微信等                            | 服务端可使用ASP、JSP、PHP、Python、Java等技术 |
| 通信模型            | App → HTTP请求 → Server处理 → HTTP响应 → App更新UI | 可带参数、读数据库或XML文件等                 |

#### 2. Android网络访问设置

##### Android权限声明

```xml
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
```

##### 网络状态检测代码

```java
ConnectivityManager connMgr = (ConnectivityManager) getSystemService(Context.CONNECTIVITY_SERVICE);
NetworkInfo networkInfo = connMgr.getActiveNetworkInfo();
if (networkInfo != null && networkInfo.isConnected()) {
    // 网络可用
}
```

##### 推荐网络库：Volley

- 简化HTTP请求流程，文档：https://google.github.io/volley/

#### 3. 获取网页内容的完整Android示例

##### AndroidManifest权限配置

```xml
<uses-permission android:name="android.permission.INTERNET" />
```

##### XML布局文件

```xml
<TextView android:id="@+id/myText" ... />
```

##### Java逻辑（核心流程）

```java
if (connMgr.getActiveNetworkInfo().isConnected()) {
    downloadWebpage("https://www.hku.hk");
}

Executors.newSingleThreadExecutor().execute(() -> {
    String result = downloadUrl(url);
    new Handler(Looper.getMainLooper()).post(() -> textView.setText(result));
});
```

##### 下载网页的函数实现

```java
private String downloadUrl(String myurl) throws IOException {
    HttpURLConnection conn = (HttpURLConnection) new URL(myurl).openConnection();
    conn.setRequestMethod("GET");
    InputStream is = conn.getInputStream();
    return readIt(is, 5000);
}
```

#### 4. GET 与 POST 方法对比

| 方法 | 特点                      | 示例                                    |
| ---- | ------------------------- | --------------------------------------- |
| GET  | 参数附加在URL后，长度有限 | `http://example.com/login.php?name=Tom` |
| POST | 参数放在请求体内，更安全  | 适合传输敏感或大数据                    |

#### 5. 使用PHP处理GET密码验证请求

##### 示例PHP代码（samplephp.php）

```php
$correct_password = "secret";
if (isset($_GET['password']) && $_GET['password'] === $correct_password) {
    header("Location: page2.php");
} else {
    echo "Incorrect or missing password.";
}
```

##### 页面跳转目标页（page2.php）

```php
<?php echo "Welcome to this protected page!"; ?>
```

#### 6. JSON数据解析（Java）

##### 示例JSON结构

```json
{
  "course_code": "COMP7506",
  "teacher_1": "Dr. T.W. Chim",
  "students": ["Anthony", "Ben"]
}
```

##### Java解析示例

```java
JSONObject root = new JSONObject(JSONString);
String teacher = root.getString("teacher_1");
JSONArray students = root.getJSONArray("students");
```

#### 7. 使用正则表达式解析HTML

##### Java代码解析Moodle源页面

```java
Pattern p = Pattern.compile("<h3 class=\"coursename\".*?>(.*?)</a>");
Matcher m = p.matcher(htmlContent);
while (m.find()) {
    String course = m.group(1);
}
```

#### 8. 嵌入网页：WebView组件（Android与iOS）

##### Android WebView设置

```xml
<WebView android:id="@+id/webview" ... />
WebView myWebView = findViewById(R.id.webview);
myWebView.loadUrl("https://www.cs.hku.hk");
```

##### iOS WKWebView 示例（Swift）

```swift
let webView = WKWebView()
let request = URLRequest(url: URL(string: "https://www.cs.hku.hk")!)
webView.load(request)
```

#### 9. 响应式网页设计基础

| 技术          | 说明                          | 示例                                                         |
| ------------- | ----------------------------- | ------------------------------------------------------------ |
| viewport      | 控制页面适配                  | `<meta name="viewport" content="width=device-width, initial-scale=1.0">` |
| 图片自适应    | `max-width:100%` 保持图像比例 | `<img style="max-width:100%; height:auto;">`                 |
| vw单位        | 文字随屏幕尺寸变化            | `font-size: 5vw;`                                            |
| Media Queries | 针对不同分辨率调整样式        | `@media screen and (max-width:800px) { ... }`                |

#### 10. JavaScript交互网页与WebView配合

##### 温度转换网页（demo8）

```html
<input type="number" oninput="temperatureConverter(this.value)">
<p id="outputCelcius"></p>
<script>
function temperatureConverter(val) {
    document.getElementById("outputCelcius").innerHTML = (val - 32)/1.8;
}
</script>
```

##### Android启用JavaScript

```java
WebSettings webSettings = webView.getSettings();
webSettings.setJavaScriptEnabled(true);
```

##### iOS启用（iOS 14前）

```swift
let preferences = WKPreferences()
preferences.javaScriptEnabled = true
```


#### 11. WebView上传文件的小技巧

- 原因：Android/iOS直接上传文件到CS服务器可能被拦截
- 方法：通过网页表单嵌入WebView实现上传

### 第十三章 Kotlin

#### Kotlin 简介与历史背景

| 内容                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| 官方支持            | 2017年Google宣布Kotlin成为Android官方开发语言                |
| 特性                | Kotlin 是面向 JVM、Android、浏览器的静态类型语言             |
| Android Studio 支持 | 从 3.0 起完全支持 Kotlin，支持 Java 转 Kotlin 自动转换（非100%准确） |

#### Java 转 Kotlin 示例对比：HelloWorld

```java
// Java
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
// Kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}
```

> Kotlin 无分号，函数定义方式更简洁

#### Kotlin 实战：最大公因数计算器（HCF Calculator）

**XML布局**

```xml
<EditText android:id="@+id/txtbox1" ... />
<EditText android:id="@+id/txtbox2" ... />
<Button android:id="@+id/button1" ... android:text="FIND HCF" />
<TextView android:id="@+id/lbl1" ... />
```

**Java 版主要逻辑：**

```java
button1.setOnClickListener(new OnClickListener() {
    public void onClick(View v) {
        int x = Integer.parseInt(txtbox1.getText().toString());
        int y = Integer.parseInt(txtbox2.getText().toString());
        int hcf = 1;
        for (int i = 1; i <= x || i <= y; i++) {
            if (x % i == 0 && y % i == 0) hcf = i;
        }
        tv.setText("HCF = " + hcf);
    }
});
```

**Kotlin 版等效代码：**

```kotlin
button1!!.setOnClickListener(clicker())

internal inner class clicker : View.OnClickListener {
    override fun onClick(v: View) {
        val x = txtbox1!!.text.toString().toInt()
        val y = txtbox2!!.text.toString().toInt()
        var hcf = 1
        var i = 1
        while (i <= x || i <= y) {
            if (x % i == 0 && y % i == 0) hcf = i
            i++
        }
        tv!!.text = "HCF = $hcf"
    }
}
```

> 使用 `!!` 强制解引用（可能抛NPE）

#### Java 与 Kotlin 示例对比

| 示例     | Java                                       | Kotlin                   |
| -------- | ------------------------------------------ | ------------------------ |
| WebView  | 使用 `findViewById` + 设置 JavaScript 启用 | 类似但语法更简洁         |
| 下载图片 | 用匿名内部类和 Handler                     | 使用 Lambda 与 `post {}` |

#### Kotlin 与 Java 特性对比总结

| 特性              | Java       | Kotlin                       |
| ----------------- | ---------- | ---------------------------- |
| Checked Exception | 有         | 无                           |
| 数据类            | 写大量代码 | `data class` 即可            |
| Null 安全         | 易出错     | 内建 null 检查与 `?.` 操作符 |
| 扩展函数          | 无         | 有                           |
| 协程              | 无         | 有                           |
| 类型推导          | 无         | 有                           |
| Smart Cast        | 无         | 有                           |
| 静态成员          | 有         | 用 `companion object` 实现   |

#### Kotlin 语言特性

**函数定义：**

```kotlin
fun sum(a: Int, b: Int): Int = a + b
fun calculate(num1: Int, num2: Int = 2, num3: Int = 4)
```

**可选命名参数调用：**

```kotlin
calculate(1, num3 = 5)
```

**变量定义：**

```kotlin
val a = 1  // 不可变
var b = 2  // 可变
```

**数组与遍历：**

```kotlin
val num = arrayOf(1, 2, 3, 4)
for (i in 0..num.size-1) println(num[i])
```

#### Null 安全机制

| 用法         | 示例                                  |
| ------------ | ------------------------------------- |
| 非空类型     | `var s: String = "abc"`（不能为null） |
| 可空类型     | `var s: String? = null`               |
| 安全调用     | `s?.length`                           |
| Elvis 操作符 | `val len = s?.length ?: 0`            |
| 强制调用     | `s!!.length`（若为 null 会抛异常）    |

#### 字符串插值

```kotlin
val name = "Kotlin"
println("Hello $name!")
```

#### 类与构造器

```kotlin
class Person(val name: String, val age: Int? = null) {
    init { println("Hello, I'm $name") }
}
```

**次构造器：**

```kotlin
class Car(val id: String, val type: String) {
    constructor(id: String): this(id, "unknown")
}
```

#### 类继承与访问控制

- 默认类是 final 的，需用 `open` 才能继承
- 使用 `override` 重写父类方法
- 静态成员通过 `companion object` 实现

#### 类继承综合示例（Person / Student / Lecturer / University）

**父类 Person：**

```kotlin
open class Person(val name: String, val age: Int, val gender: String) {
    companion object { var numOfPerson = 0 }
    init { numOfPerson++ }
    open fun getInfo(): String = "No information"
}
```

**子类 Student 与 Lecturer：**

```kotlin
class Student(...) : Person(...) {
    private val courseList = ArrayList<String>()
    override fun getInfo(): String { ... }
}

class Lecturer(...) : Person(...) {
    override fun getInfo(): String { ... }
}
```

**组合类 University：**

```kotlin
class University {
    private val people = ArrayList<Person>()
    fun addPerson(person: Person) { people.add(person) }
    fun getInfo(): String = people.joinToString("\n") { it.getInfo() }
}
```

### 第十四章 UI design

#### 用户的界面期望

- 用户希望App是**简单、快速响应、任务导向的**
- 希望能快速完成特定任务，尤其在移动场景下
- 用户界面应简洁直观，并能提供及时反馈
- 能尽量**自动化操作**

#### 用户不希望的体验

- 不希望等待
- 不希望猜测系统行为
- 不愿意花时间找按钮、菜单或信息
- 不希望频繁重新配置App以适应网络环境变化

#### 用户控制感

- 应用要让用户感觉**“掌控全局”**
- 提供多种方式完成任务（步骤越少越好）
- 允许个性化定制
- 支持撤销或恢复非关键错误

#### 什么是用户界面设计

- 是以用户体验为核心的界面与交互设计
- 包括硬件、软件、网页与移动端应用

#### 本章目标

- 提供UI设计的一般原则
- 探讨不同交互方式
- 图形/文本信息如何选用
- UI设计的流程
- 可用性评价的方法与指标

#### 用户界面设计基本原则

- **用户熟悉度**：使用用户熟悉的术语和概念
- **一致性**：命令、菜单、格式风格要统一
- **最小惊讶原则**：用户不应对系统行为感到意外
- **可恢复性**：如撤销、确认删除、错误提示等
- **用户引导**：提供明确反馈与上下文帮助
- **用户多样性**：如为视力差的用户提供大字体等功能

#### 移动设备界面设计要点

- 无鼠标键盘，手指输入
- 文字输入困难、精度低
- 不应使用过多表单和控件
- 设计应简洁、与Web版一致（颜色、风格等）

#### 移动UI通用设计建议

- 只显示必要数据与关键控件
- 控件应易于辨识、查找、使用
- 控件设计应具**一致性与可预测性**
- 控件间应有空隙防止误操作
- 避免复杂风格或过度美化
- 使用系统标准控件（如虚拟键盘）

#### 设计通用法则

- **KISS**（Keep It Simple, Stupid）
- **80/20 Rule**：80%功能使用集中于20%
- **Poka-Yoke原则**：防止误操作
- **Satisficing**：满意 + 足够 = 用户不需最优但需“够用”
- **渐进披露（Progressive Disclosure）**：按需展示更多内容

#### 人机交互设计定律

- **Fitt’s Law**：控件越大越近越容易点中
  - 界面角落和边缘是“无限大”的目标
- **Hick’s Law**：决策时间与选项数量成正比
  - 层级过深、菜单太多都降低效率

#### 用户认知定律

- **Magic Number 7 ± 2**：人类短时记忆容量为7个左右单位
- **Tesler’s Law（复杂度守恒）**：系统总复杂度不变，只是开发者或用户承担

#### 菜单设计建议

- 只展示必要内容
- 排序应按**使用频率**
- 避免多层嵌套菜单
- 常用功能直接放菜单栏
- 移动版菜单应模仿桌面网页顺序

#### 用户界面设计流程

1. 分析并理解用户活动
2. 纸上原型设计
3. 动态原型设计
4. 可执行原型
5. 与用户反复测试评估
6. 实现最终UI

#### Paper Prototype 原型设计

- 用手绘草图模拟界面交互
- 用于沟通设计思路（设计者、开发者、用户）
- 用于可用性测试（在开发前验证交互方式）

#### 用户-系统交互的两个核心问题

- 用户信息如何输入到系统中？
- 系统信息如何呈现给用户？

#### 可视化设计要素

- 色彩
- 图标/卡通图像
- 字体类型
- 元素大小（可视性与缩放性）
- 亮度与对比度

#### 色彩心理学（Color Psychology）

- 不同颜色给人不同的心理感受
- 可用来营造愉悦、紧张、安全、警告等氛围
- 建议阅读资料：
  - [Color Psychology in UI/UX Design](https://medium.com/@designbyshadow/color-psychology-in-ui-ux-design-understanding-the-emotional-impact-of-colors-b0f2d2ec8484)

### 第十五章 发布与测试

#### 本章结构

- App测试类型
- Android与iOS测试方法
- 安全测试与Monkey工具
- 数字签名与证书
- Android APK签名与上传流程
- iOS签名与发布流程

#### App测试指标分类

| 前端性能指标 | 后端性能指标          |
| ------------ | --------------------- |
| App加载时间  | Server负载            |
| 响应时间     | API延迟（如Cloud/AI） |
| 屏幕渲染效率 | 首字节时间（TTFB）    |
| 后台任务处理 | HTTP请求数            |
| 崩溃频率     | DNS查询数             |
| 电池消耗     | 吞吐量                |
| 内存占用     | –                     |
| 硬件兼容性   | –                     |

#### 功能性测试

- 验证App功能是否按照预期运作
- 包含输入-输出测试（IO测试）
- 包含用户验收测试（UAT）即Beta测试
- 常见方法：
  - 烟雾测试（Smoke Testing）
  - 回归测试（Regression Testing）

#### 非功能性测试

- 测试非业务逻辑相关的性能指标
- 包括：
  - 兼容性测试：多设备、OS、网络环境
  - 用户体验、资源使用等方面

#### 服务端测试类型

- 压力测试（Stress Testing）：极端条件下是否崩溃
- 容量测试（Capacity Testing）：系统最大承载用户数
- 体积/洪水测试（Volume/Flood Testing）：处理大数据是否稳定
- 峰值测试（Spike Testing）：突然增加负载是否稳定

#### 压力测试步骤

1. 规划目标与负载参数
2. 创建自动化脚本（如JMeter、LoadRunner）
3. 执行脚本，渐进/瞬时加载
4. 记录性能指标、错误、瓶颈
5. 优化后回归测试

#### 安全测试（渗透测试）

- 模拟攻击找出漏洞
- 典型问题：
  - 使用不安全组件
  - 权限过度
  - API或后端无防护
- 工具示例：MobSF（Mobile Security Framework）
  - 可分析Android/iOS安全问题

#### Android输入测试工具：Monkey

- Monkey模拟用户点击、滑动等行为
- 四类配置参数：
  - 基本参数（事件数量）
  - 运行限制（指定package）
  - 事件类型频率
  - Debug选项

#### Monkey运行与示例

执行命令（Mac/Linux加 `./`）：

```bash
adb -e shell monkey --ignore-crashes -p hk.hkucs.hcfcalculator 1000 > test_logs.txt
```

含义：

- `-e`: 模拟器
- `--ignore-crashes`: 出现崩溃也继续
- `-p`: 指定包名
- `1000`: 事件数量
- `> test_logs.txt`: 保存日志

#### Monkey输出与异常处理示例

```java
try {
  x = Integer.parseInt(a);
  y = Integer.parseInt(b);
} catch (NumberFormatException e) {
  // 处理异常
}
```

使用 `try-catch-finally` 捕捉风险操作（如用户乱输字符）

#### 真机测试（Android）

- 用USB连接设备
- 开启开发者模式（不同品牌略有差异）
- Android Studio中可选择设备进行APK安装与测试

#### 公钥加密机制

- 每用户一对密钥：公钥公开、私钥保密
- 加密用公钥，解密需私钥
- 防止第三方伪造或篡改消息

#### 加密摘要函数（Hash Function）

- 输入 → 固定长度输出（摘要）
- 不可逆：不可由摘要推回原始信息
- 校验完整性（相同输入 → 相同摘要）

#### 数字签名与证书

- 签名=摘要+私钥
- 接收者用发送者公钥验证
- App发布签名原理一致
- 证书由CA签发（如Google/Apple官方）

#### Android APK签名与发布

- 未签名APK在 `app/build/intermediates/apk/debug`
- 要发布必须签名：
  - Android Studio中：Build → Generate Signed Bundle/APK
  - 创建密钥库、设置 key alias 和密码

默认签名路径：

```plaintext
<project_root>/app/
```

#### build.gradle 中的配置示例

```gradle
defaultConfig {
    applicationId = "hk.hkucs.hcfcalculator"
    minSdk = 24
    targetSdk = 35
    versionCode 6
    versionName "1.5"
}
```

- `versionCode` 每次提交需 +1（整数）
- `versionName` 可如 1.0 → 1.1（小更新）/ 2.0（大更新）

#### 上传到 Google Play 流程

1. 注册开发者账号（$25 USD 终身）
2. 登录 Google Play Console
3. 点击 "Create app"
4. 提供基本信息、截图、Banner等
5. 可选择：
   - Internal Testing（100人内测）
   - Closed Testing（受控组测试）
   - Open Testing（公开Beta）
6. 最终发布后可查看稳定性、安装量等

#### iOS应用发布机制

- 每个可运行App必须“签名”
- 安装测试设备前必须：
  - 拥有开发者证书
  - 创建 Provisioning Profile（包含设备ID + App ID + 证书）

#### 证书类型回顾（常见）

| 类型             | 用途                     |
| ---------------- | ------------------------ |
| iOS Development  | 开发测试                 |
| iOS Distribution | 上架或Ad Hoc发布         |
| Mac Development  | macOS开发                |
| Developer ID     | 非App Store分发（仅Mac） |

#### iOS签名流程

1. 打开 Keychain Access，生成 `.csr` 文件
2. 上传到 Apple Developer，下载 `.cer` 证书
3. 创建 Provisioning Profile，包含设备列表与证书
4. 使用 Xcode 打包为 `.ipa` 并签名
5. 可用 Apple Configurator 或拖入 Xcode 安装测试

#### iOS App 发布流程

- 生成 Distribution 类型证书
- 创建分发专用的 Provisioning Profile
- 提交到 App Store 前，Xcode 会自动重新签名
- App Store 审核通过后，不再包含profile，所有设备可安装

#### iOS 审核标准

- 官方审核地址：https://developer.apple.com/app-store/review/guidelines/
- 内容审查较严格，需符合Apple准则
