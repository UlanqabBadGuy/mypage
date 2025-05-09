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

#### 第27页：函数的参数命名机制

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

#### 第28页：使用外部参数名（Argument Label）

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

#### 第29页：示例函数 greet

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

#### 第30页：多个参数的外部命名

```swift
func sayHello(to person: String, and anotherPerson: String) -> String {
    return "Hello \(person) and \(anotherPerson)!"
}

print(sayHello(to: "Bill", and: "Ted"))
```

说明：

- `to` 和 `and` 是外部参数名，调用时必须使用。
- 好处：使函数调用语义清晰

#### 第31页：省略外部参数名（使用 `_`）

```swift
func someFunction(_ first: Int, second: Int) {
    print(first, second)
}

someFunction(1, second: 2)
```

说明：

- `_` 表示调用时不需要外部参数名

#### 第32页：三种参数写法总结

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

#### 第33页：默认参数值

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

#### 第34页：可变参数（Variadic Parameter）

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

#### 第35页：inout 参数（可变引用）

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

#### 第37页：类方法与实例方法

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

```
css复制编辑I am a class method
anInstanceMethod. Calling bClassMethod().
I am a class method
```

说明：

- `class func` 表示类方法（可直接用类名调用）
- `func` 是实例方法，必须用对象来调用
- 实例方法中也能调用类方法
