---
标题： "在 iOS 上 ListView 分隔符样式" 说明： "平台说明允许使用仅在特定平台上可用的功能，而无需实现自定义呈现器或效果。 本文介绍如何使用特定于 iOS 平台的来控制 ListView 中的单元格之间的分隔符是否使用 ListView 的完整宽度。
ms-chap： xamarin assetid： A4CB45CE-9FB7-47ED-8C3D-93E39BF282E4： xamarin 窗体作者： davidbritch： dabritch ms. 日期：10/24/2018 非 loc： [ Xamarin.Forms ， Xamarin.Essentials ]
---

# <a name="listview-separator-style-on-ios"></a>IOS 上的 ListView 分隔符样式

[![下载示例](~/media/shared/download.png) 下载示例](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-platformspecifics)

此 iOS 平台特定控制中的单元格之间的分隔符是否 [`ListView`](xref:Xamarin.Forms.ListView) 使用的完整宽度 `ListView` 。 它通过将 [`ListView.SeparatorStyle`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.ListView.SeparatorStyleProperty) 附加属性设置为枚举的值，在 XAML 中使用 [`SeparatorStyle`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.SeparatorStyle) ：

```xaml
<ContentPage ...
             xmlns:ios="clr-namespace:Xamarin.Forms.PlatformConfiguration.iOSSpecific;assembly=Xamarin.Forms.Core">
    <StackLayout Margin="20">
        <ListView ... ios:ListView.SeparatorStyle="FullWidth">
            ...
        </ListView>
    </StackLayout>
</ContentPage>
```

此外，还可以使用 Fluent API 从 c # 使用该方法：

```csharp
using Xamarin.Forms.PlatformConfiguration;
using Xamarin.Forms.PlatformConfiguration.iOSSpecific;
...

listView.On<iOS>().SetSeparatorStyle(SeparatorStyle.FullWidth);
```

`ListView.On<iOS>`方法指定此平台特定的仅在 iOS 上运行。 [ `ListView.SetSeparatorStyle` ] （X： Xamarin.Forms 。PlatformConfiguration. iOSSpecific. SetSeparatorStyle （ Xamarin.Forms 。IPlatformElementConfiguration { Xamarin.Forms 。PlatformConfiguration、 Xamarin.Forms 。ListView}， Xamarin.Forms 。PlatformConfiguration. iOSSpecific. SeparatorStyle））方法， [`Xamarin.Forms.PlatformConfiguration.iOSSpecific`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific) 用于控制在中的单元格之间的分隔符是否 [`ListView`](xref:Xamarin.Forms.ListView) 使用的全半角 `ListView` ，同时 [`SeparatorStyle`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.SeparatorStyle) 枚举提供两个可能的值：

- [`Default`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.SeparatorStyle.Default)–指示默认的 iOS 分隔符行为。 这是中的默认行为 Xamarin.Forms 。
- [`FullWidth`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.SeparatorStyle.FullWidth)-指示将从的一个边缘向另一个边缘绘制分隔符 `ListView` 。

结果就是，将指定的 [`SeparatorStyle`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.SeparatorStyle) 值应用于 [`ListView`](xref:Xamarin.Forms.ListView) ，后者控制单元格之间的分隔符的宽度：

![](listview-separator-style-images/listview-separatorstyle.png "ListView SeparatorStyle Platform-Specific")

> [!NOTE]
> 分隔符样式设置为后 `FullWidth` ，不能 `Default` 在运行时更改回。

## <a name="related-links"></a>相关链接

- [PlatformSpecifics （示例）](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-platformspecifics)
- [创建平台特定信息](~/xamarin-forms/platform/platform-specifics/index.md#creating-platform-specifics)
- [iOSSpecific API](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific)
