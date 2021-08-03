## 启动优化

### 启动模式
1. 冷启动
App进程不存在，需要重新创建进程和首页。
2. 温启动
  - App进程存在但首页不存在，启动需要重新创建首页，如首页主动调用finish()或者按下返回键(不会保存实例状态)。
  - App进程不存在但保存了首页实例状态，如APP在后台时被系统回收（调用onSaveInstanceState保存实例状态），已保存实例状态（传递给onCreate()）对于重新创建应用有一定帮助。
3. 热启动
App进程与首页均存活，启动时直接带回前台即可。


### 冷启动流程
1. 加载与启动APP
2. 展示空白启动窗口
3. 创建进程

进程负责如下步骤：
1. 创建app对象
2. 启动主线程
3. 创建首页Activity
4. 从布局资源扩展View
5. 布局屏幕
6. 进行初始回执

```
adb [-d|-e|-s <serialNumber>] shell am start -S -W
    com.example.app/.MainActivity
    -c android.intent.category.LAUNCHER
    -a android.intent.action.MAIN

Starting: Intent
    Activity: com.example.app/.MainActivity
    ThisTime: 2044
    TotalTime: 2044
    WaitTime: 2054
    Complete
```
















- [StartupMode](https://developer.android.com/reference/kotlin/androidx/benchmark/macro/StartupMode)
- [应用启动时间](https://developer.android.com/topic/performance/vitals/launch-time#cold)
- [生命周期-实例状态](https://developer.android.com/guide/components/activities/activity-lifecycle#instance-state)
- [Android 中如何计算 App 的启动时间？](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2016/0105/3830.html)
