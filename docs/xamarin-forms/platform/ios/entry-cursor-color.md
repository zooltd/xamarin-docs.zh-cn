---
title： "在 iOS 上输入光标颜色" 说明： "平台细节使你可以使用仅在特定平台上可用的功能，而无需实现自定义呈现器或效果。 本文介绍如何使用 iOS 平台特定的来设置项的光标颜色。 "
ms-chap： xamarin assetid：867D70BA-53F9-4434-8094-85D71DCECC2D： xamarin 窗体作者： davidbritch： dabritch ms. 日期：10/24/2018 非 loc： [ Xamarin.Forms ， Xamarin.Essentials ]
---

# <a name="entry-cursor-color-on-ios"></a>IOS 上的入口光标颜色

[![下载示例](~/media/shared/download.png) 下载示例](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-platformspecifics)

此 iOS 平台特定于将的光标颜色设置 [`Entry`](xref:Xamarin.Forms.Entry) 为指定的颜色。 它通过将 [`Entry.CursorColor`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.Entry.CursorColorProperty) 可绑定的属性设置为来在 XAML 中使用 [`Color`](xref:Xamarin.Forms.Color) ：

```xaml
<ContentPage ...
             xmlns:ios="clr-namespace:Xamarin.Forms.PlatformConfiguration.iOSSpecific;assembly=Xamarin.Forms.Core">
    <StackLayout>
        <Entry ... ios:Entry.CursorColor="LimeGreen" />
    </StackLayout>
</ContentPage>
```

此外，还可以使用 Fluent API 从 c # 使用该方法：

```csharp
using Xamarin.Forms.PlatformConfiguration;
using Xamarin.Forms.PlatformConfiguration.iOSSpecific;
...

var entry = new Xamarin.Forms.Entry();
entry.On<iOS>().SetCursorColor(Color.LimeGreen);
```

`Entry.On<iOS>`方法指定此平台特定的仅在 iOS 上运行。 [ `Entry.SetCursorColor` ] （X： Xamarin.Forms 。PlatformConfiguration. iOSSpecific. SetCursorColor （ Xamarin.Forms 。IPlatformElementConfiguration { Xamarin.Forms 。PlatformConfiguration、 Xamarin.Forms 。Entry}， Xamarin.Forms 。Color））方法，在 [`Xamarin.Forms.PlatformConfiguration.iOSSpecific`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific) 命名空间中，将光标颜色设置为指定的 [`Color`](xref:Xamarin.Forms.Color) 。 此外，[ `Entry.GetCursorColor` ] （x： Xamarin.Forms 。PlatformConfiguration. iOSSpecific. GetCursorColor （ Xamarin.Forms 。IPlatformElementConfiguration { Xamarin.Forms 。PlatformConfiguration、 Xamarin.Forms 。Entry}））方法可用于检索当前游标的颜色。

因此，中的光标颜色 [`Entry`](xref:Xamarin.Forms.Entry) 可以设置为特定 [`Color`](xref:Xamarin.Forms.Color) ：

![](entry-cursor-color-images/entry-cursorcolor.png "Entry Cursor Color")

## <a name="related-links"></a>相关链接

- [PlatformSpecifics （示例）](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-platformspecifics)
- [创建平台特定信息](~/xamarin-forms/platform/platform-specifics/index.md#creating-platform-specifics)
- [iOSSpecific API](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific)
