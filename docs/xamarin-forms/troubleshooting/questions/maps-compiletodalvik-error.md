---
title： "为什么要这样做 Xamarin.Forms 。地图 Android 项目失败，出现 COMPILETODALVIK 意外的顶级错误？ "
ms. 主题：故障排除： xamarin： xamarin assetid： C0251EB1-F509-47AD-98D6-846AF46425E5： xamarin 窗体作者： davidbritch： dabritch ms. 日期：04/25/2017 非 loc： [ Xamarin.Forms ， Xamarin.Essentials ]
---

# <a name="why-does-my-xamarinformsmaps-android-project-fail-with-compiletodalvik-unexpected-top-level-error"></a>为什么要这样做 Xamarin.Forms 。地图 Android 项目失败，出现 COMPILETODALVIK 意外顶级错误？

此错误可能出现在 Visual Studio for Mac 的错误板中，或在 Visual Studio 的 "生成输出" 窗口中。在 Android 项目中使用 Xamarin.Forms 。地图.

最常见的解决方法是增加你的 Xamarin Android 项目的 Java 堆大小。 请按照以下步骤提高堆大小：

## <a name="visual-studio"></a>Visual Studio

1. 右键单击 Android 项目 & 打开 "项目选项"。
2. 中转到**Android 选项-> 高级**
3. 在 "Java 堆大小" 文本框中，输入1G。
4. 重新生成项目。

![Visual Studio 项目选项的屏幕截图](maps-compiletodalvik-error-images/vsjavaheap.png "Visual Studio 中的 Android 生成选项")

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

1. 右键单击 Android 项目 & 打开 "项目选项"。
2. 中转到 **> Android build > Advanced**
3. 在 "Java 堆大小" 文本框中，输入1G。
4. 重新生成项目。  

![Visual Studio for Mac 项目选项的屏幕截图](maps-compiletodalvik-error-images/xsjavaheap.png "Visual Studio for Mac 中的 Android 生成选项")
