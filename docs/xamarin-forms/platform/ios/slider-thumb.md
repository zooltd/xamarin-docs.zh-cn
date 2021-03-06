---
标题： "滑块 Thumb 点击 iOS" 说明： "平台说明允许使用仅在特定平台上可用的功能，而无需实现自定义呈现器或效果。 本文介绍如何使用 iOS 平台特定的，该平台允许通过点击滑块上的 "值" 属性进行设置。
ms-chap： xamarin assetid： D0915D37-9A59-4728-BB6A-FE094A661275： xamarin 窗体作者： davidbritch： dabritch ms. 日期：10/24/2018 非 loc： [ Xamarin.Forms ， Xamarin.Essentials ]
---

# <a name="slider-thumb-tap-on-ios"></a>滚动条点击 iOS

[![下载示例](~/media/shared/download.png) 下载示例](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-platformspecifics)

此 iOS 平台特定用于 [`Slider.Value`](xref:Xamarin.Forms.Slider.Value) 通过点击栏上的位置 [`Slider`](xref:Xamarin.Forms.Slider) 而不是通过拖动滚动块来设置属性 `Slider` 。 它通过将 [`Slider.UpdateOnTap`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific.Slider.UpdateOnTapProperty) 可绑定的属性设置为来在 XAML 中使用 `true` ：

```xaml
<ContentPage ...
             xmlns:ios="clr-namespace:Xamarin.Forms.PlatformConfiguration.iOSSpecific;assembly=Xamarin.Forms.Core">
    <StackLayout ...>
        <Slider ... ios:Slider.UpdateOnTap="true" />
        ...
    </StackLayout>
</ContentPage>
```

此外，还可以使用 Fluent API 从 c # 使用该方法：

```csharp
using Xamarin.Forms.PlatformConfiguration;
using Xamarin.Forms.PlatformConfiguration.iOSSpecific;
...

var slider = new Xamarin.Forms.Slider();
slider.On<iOS>().SetUpdateOnTap(true);
```

`Slider.On<iOS>`方法指定此平台特定的仅在 iOS 上运行。 [ `Slider.SetUpdateOnTap` ] （X： Xamarin.Forms 。PlatformConfiguration. iOSSpecific SetUpdateOnTap （ Xamarin.Forms 。IPlatformElementConfiguration { Xamarin.Forms 。PlatformConfiguration、 Xamarin.Forms 。Slider}，System.object）方法， [`Xamarin.Forms.PlatformConfiguration.iOSSpecific`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific) 用于控制条形图上的点击是否 `Slider` 会设置 [`Slider.Value`](xref:Xamarin.Forms.Slider.Value) 属性。 此外，[ `Slider.GetUpdateOnTap` ] （x： Xamarin.Forms 。PlatformConfiguration. iOSSpecific GetUpdateOnTap （ Xamarin.Forms 。IPlatformElementConfiguration { Xamarin.Forms 。PlatformConfiguration、 Xamarin.Forms 。Slider}））方法可用于返回是否在 `Slider` 条形图上点击即可设置 `Slider.Value` 属性。

结果是，在栏上点击 [`Slider`](xref:Xamarin.Forms.Slider) 可以移动 `Slider` 滚动块并设置 [`Slider.Value`](xref:Xamarin.Forms.Slider.Value) 属性：

![](slider-thumb-images/slider-updateontap.png "Slider Update on Tap enabled")

## <a name="related-links"></a>相关链接

- [PlatformSpecifics （示例）](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-platformspecifics)
- [创建平台特定信息](~/xamarin-forms/platform/platform-specifics/index.md#creating-platform-specifics)
- [iOSSpecific API](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific)
