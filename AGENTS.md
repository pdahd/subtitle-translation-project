你是 Android 逆向工程和字节跳动安全体系分析专家。



## 背景

这是 CapCut 国际版 (com.lemon.lvoverseas) v16.9.0 官方 APK 的修改版 logcat 日志。



已完成的修改：

1. AndroidManifest: debuggable=true, allowBackup=true

2. CrackingInterceptor: intercept() 和 c(String)V 保持 native 不变

3. CrackingInterceptor.a(String)Z: 始终返回 true（跳过所有 URL 检查）

4. CrackingInterceptor.b(I)V: return-void（不写入 isCracking 标记）

5. showGlobalSecurityDialog: 直接 return Unit（不显示弹窗）

6. TransLynxActivity.onCreate(): 调用 super 后立即 finish()

7. APK 使用自签名重签名



当前状态：

- ✅ 安全弹窗已消除

- ✅ JNI 注册无错误

- ❌ 面板 API 仍返回 error_code=-5 "shark block reinstall"

- ❌ check_risk API 被 -555 TRAFFIC_CONTROL_DROP 丢弃



## 分析要求



### 1. MetaSec 签名检测路径

- 找到 libmetasec_ov.so 的所有 JNI 调用痕迹

- 特别关注是否有 PackageManager.getPackageInfo、Signature、MessageDigest 的调用

- 找到 SecModuleInit/SecModuleInitTask 的执行日志

- 寻找 MetaSec 从 Java 层获取签名信息的任何线索



### 2. shark block 的精确触发点

- error_code=-5 首次出现的精确时间和调用栈

- -5 是在 Java 层生成的还是从 native 层传递过来的？

- ResPool SDK 是通过什么网络客户端发请求的？（TTNet? OkHttp? HttpURLConnection?）

- 请求是否实际到达了服务器，还是在客户端本地被拦截？



### 3. 签名读取入口

- 搜索所有 PackageManager、getPackageInfo、GET_SIGNATURES、GET_SIGNING_CERTIFICATES 相关日志

- 搜索所有 MessageDigest（MD5/SHA1/SHA256）计算的痕迹

- 搜索所有读取 /data/app/base.apk 或 META-INF 的文件操作

- 这些操作发生在主进程还是子进程？



### 4. TTNet 初始化和配置

- TTNet/Cronet 的初始化参数

- tnc_config 是否被重新下载/更新

- 流量控制规则是从哪里加载的？



### 5. 寻找 Java 层的签名验证入口

- 是否有任何 Java 类在读取 APK 签名并传递给 native 层？

- com.bytedance.mobsec.metasec.ov.MSManagerUtils 的初始化过程

- 是否可以在 Java 层拦截签名传递？



## 输出格式



### A. MetaSec 签名检测的 Java 层入口点（如果找到）

### B. shark block -5 的完整产生路径

### C. 是否存在可以在 smali 层面拦截签名检测的入口

### D. 建议的下一步 Patch 目标（仅限 smali/Java 层可行的方案）



=========



👉将分析结果保存为md 文件。


