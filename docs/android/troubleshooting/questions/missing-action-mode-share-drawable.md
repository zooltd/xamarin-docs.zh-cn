---
title: Android.Support.v7.AppCompat - 未找到与给定名称匹配的资源：属性“android:actionModeShareDrawable”
ms.topic: troubleshooting
ms.prod: xamarin
ms.assetid: 5814069C-FC43-41DE-B5A5-024D05E59929
ms.technology: xamarin-android
author: davidortinau
ms.author: daortin
ms.date: 03/09/2018
ms.openlocfilehash: e688bd27d1116b2a77a12ccd6da29ea582053581
ms.sourcegitcommit: b0ea451e18504e6267b896732dd26df64ddfa843
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2020
ms.locfileid: "75728104"
---
# <a name="androidsupportv7appcompat---no-resource-found-that-matches-the-given-name-attr-androidactionmodesharedrawable"></a>Android.Support.v7.AppCompat - 未找到与给定名称匹配的资源：属性“android:actionModeShareDrawable”

1. 确保通过 Android SDK 管理器下载最新附加程序以及 Android 5.0 (API 21) SDK。

2. 确保在将 compileSdkVersion 设置为 21 的情况下编译应用程序。 也可以选择将 targetSdkVersion 设置为 21。

3. 如果需要以前的版本（如 API 19），请下载 NuGet 页面上的相应版本：

[https://www.nuget.org/packages/Xamarin.Android.Support.v7.AppCompat/](https://www.nuget.org/packages/Xamarin.Android.Support.v7.AppCompat/)

> [!NOTE]
> 如果通过程序包管理器控制台手动安装此版本，请确保同时安装相同版本的 Xamarin.Android.Support.v4

[https://www.nuget.org/packages/Xamarin.Android.Support.v4/](https://www.nuget.org/packages/Xamarin.Android.Support.v4/)

堆栈溢出参考：[https://stackoverflow.com/questions/26431676/appcompat-v721-0-0-no-resource-found-that-matches-the-given-name-attr-andro](https://stackoverflow.com/questions/26431676/appcompat-v721-0-0-no-resource-found-that-matches-the-given-name-attr-andro)

## <a name="see-also"></a>另请参阅

- [应安装哪些 Android SDK 包？](~/android/troubleshooting/questions/install-android-sdk-packages.md)
