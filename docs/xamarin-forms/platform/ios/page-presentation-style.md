---
标题： "iOS 上的模式页呈现样式" 说明： "平台细节使你可以使用仅在特定平台上可用的功能，而无需实现自定义呈现器或效果。 本文介绍如何使用 iOS 平台特定的来设置模式页面的表示形式。
ms-chap： xamarin assetid： C791F7CF-330A-44BA-987A-4CFCCBB9278B： xamarin 窗体作者： davidbritch： dabritch ms. 日期：04/02/2020 非 loc： [ Xamarin.Forms ， Xamarin.Essentials ]
---

# <a name="modal-page-presentation-style-on-ios"></a>IOS 上的模式页呈现样式

[![下载示例](~/media/shared/download.png) 下载示例](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-platformspecifics)

此 iOS 平台特定用于设置模式页面的表示形式，此外还可用于显示具有透明背景的模式页面。 它通过将 `Page.ModalPresentationStyle` 可绑定的属性设置为一个枚举值在 XAML 中使用 `UIModalPresentationStyle` ：

```xaml
<ContentPage ...
             xmlns:ios="clr-namespace:Xamarin.Forms.PlatformConfiguration.iOSSpecific;assembly=Xamarin.Forms.Core"
             ios:Page.ModalPresentationStyle="OverFullScreen">
    ...
</ContentPage>
```

此外，还可以使用 Fluent API 从 c # 使用该方法：

```csharp
using Xamarin.Forms.PlatformConfiguration;
using Xamarin.Forms.PlatformConfiguration.iOSSpecific;
...

public class iOSModalFormSheetPageCS : ContentPage
{
    public iOSModalFormSheetPageCS()
    {
        On<iOS>().SetModalPresentationStyle(UIModalPresentationStyle.OverFullScreen);
        ...
    }
}
```

`Page.On<iOS>`方法指定此平台特定的仅在 iOS 上运行。 `Page.SetModalPresentationStyle`命名空间中的方法 [`Xamarin.Forms.PlatformConfiguration.iOSSpecific`](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific) 用于 [`Page`](xref:Xamarin.Forms.Page) 通过指定以下枚举值之一，在上设置模式呈现样式 `UIModalPresentationStyle` ：

- `FullScreen`，它将模式呈现样式设置为包含整个屏幕。 默认情况下，使用此演示样式显示模式页面。
- `FormSheet`，它将模式呈现样式设置为居中并小于屏幕。
- `Automatic`，它将模式呈现样式设置为系统所选的默认样式。 对于大多数视图控制器， `UIKit` 将其映射到 `UIModalPresentationStyle.PageSheet` ，但某些系统视图控制器可以将其映射到不同的样式。
- `OverFullScreen`，它将模式呈现样式设置为涵盖屏幕。
- `PageSheet`，它将模式呈现样式设置为涵盖基础内容。

此外， `GetModalPresentationStyle` 方法可用于检索 `UIModalPresentationStyle` 应用于的枚举的当前值 [`Page`](xref:Xamarin.Forms.Page) 。

结果就是可以设置上的模式呈现样式 [`Page`](xref:Xamarin.Forms.Page) ：

[![](page-presentation-style-images/modal-presentation-style-small.png "Modal Presentation Styles")](page-presentation-style-images/modal-presentation-style-large.png#lightbox "Modal Presentation Styles")

> [!NOTE]
> 使用此特定于平台的的页面设置模式呈现样式必须使用模式导航。 有关详细信息，请参阅[ Xamarin.Forms 模式页面](~/xamarin-forms/app-fundamentals/navigation/modal.md)。

## <a name="related-links"></a>相关链接

- [PlatformSpecifics （示例）](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-platformspecifics)
- [创建平台特定信息](~/xamarin-forms/platform/platform-specifics/index.md#creating-platform-specifics)
- [iOSSpecific API](xref:Xamarin.Forms.PlatformConfiguration.iOSSpecific)
