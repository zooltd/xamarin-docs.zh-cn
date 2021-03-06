---
标题： "Windows 上的 MasterDetailPage 导航栏" 说明： "平台详细信息允许使用仅在特定平台上可用的功能，而无需实现自定义呈现器或效果。 本文介绍如何使用在 MasterDetailPage 上折叠导航栏的特定于 Windows 平台的。
ms-chap： xamarin assetid：0E7436C9-FA3E-40CD-801C-3F7ED95C412D： xamarin 窗体作者： davidbritch： dabritch ms. 日期：10/24/2018 非 loc： [ Xamarin.Forms ， Xamarin.Essentials ]
---

# <a name="masterdetailpage-navigation-bar-on-windows"></a>Windows 上的 MasterDetailPage 导航栏

[![下载示例](~/media/shared/download.png) 下载示例](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-platformspecifics)

此通用 Windows 平台平台特定用于在上折叠导航栏 [`MasterDetailPage`](xref:Xamarin.Forms.MasterDetailPage) ，并通过设置 [`MasterDetailPage.CollapseStyle`](xref:Xamarin.Forms.PlatformConfiguration.WindowsSpecific.MasterDetailPage.CollapseStyleProperty) 和附加属性在 XAML 中使用 [`MasterDetailPage.CollapsedPaneWidth`](xref:Xamarin.Forms.PlatformConfiguration.WindowsSpecific.MasterDetailPage.CollapsedPaneWidthProperty) ：

```xaml
<MasterDetailPage ...
                  xmlns:windows="clr-namespace:Xamarin.Forms.PlatformConfiguration.WindowsSpecific;assembly=Xamarin.Forms.Core"
                  windows:MasterDetailPage.CollapseStyle="Partial"
                  windows:MasterDetailPage.CollapsedPaneWidth="48">
  ...
</MasterDetailPage>

```

此外，还可以使用 Fluent API 从 c # 使用该方法：

```csharp
using Xamarin.Forms.PlatformConfiguration;
using Xamarin.Forms.PlatformConfiguration.WindowsSpecific;
...

page.On<Windows>().SetCollapseStyle(CollapseStyle.Partial).CollapsedPaneWidth(148);
```

`MasterDetailPage.On<Windows>`方法指定此平台特定的仅在 Windows 上运行。 [ `Page.SetCollapseStyle` ] （X： Xamarin.Forms 。PlatformConfiguration. WindowsSpecific. MasterDetailPage. SetCollapseStyle （ Xamarin.Forms 。IPlatformElementConfiguration { Xamarin.Forms 。PlatformConfiguration、 Xamarin.Forms 。MasterDetailPage}， Xamarin.Forms 。PlatformConfiguration. WindowsSpecific. CollapseStyle））方法， [`Xamarin.Forms.PlatformConfiguration.WindowsSpecific`](xref:Xamarin.Forms.PlatformConfiguration.WindowsSpecific) 用于指定折叠样式， [`CollapseStyle`](xref:Xamarin.Forms.PlatformConfiguration.WindowsSpecific.CollapseStyle) 枚举提供了两个值： [`Full`](xref:Xamarin.Forms.PlatformConfiguration.WindowsSpecific.CollapseStyle.Full) 和 [`Partial`](xref:Xamarin.Forms.PlatformConfiguration.WindowsSpecific.CollapseStyle.Partial) 。 [ `MasterDetailPage.CollapsedPaneWidth` ] （X： Xamarin.Forms 。PlatformConfiguration. WindowsSpecific. MasterDetailPage. CollapsedPaneWidth （ Xamarin.Forms 。IPlatformElementConfiguration { Xamarin.Forms 。PlatformConfiguration、 Xamarin.Forms 。MasterDetailPage}，System.object）方法用于指定部分折叠的导航栏的宽度。

结果是，指定的 [`CollapseStyle`](xref:Xamarin.Forms.PlatformConfiguration.WindowsSpecific.CollapseStyle) 将应用于 [`MasterDetailPage`](xref:Xamarin.Forms.MasterDetailPage) 实例，同时还指定了 width：

[![](masterdetailpage-navigation-bar-images/collapsed-navigation-bar.png "Collapsed Navigation Bar Platform-Specific")](masterdetailpage-navigation-bar-images/collapsed-navigation-bar-large.png#lightbox "Collapsed Navigation Bar Platform-Specific")

## <a name="related-links"></a>相关链接

- [PlatformSpecifics （示例）](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-platformspecifics)
- [创建平台特定信息](~/xamarin-forms/platform/platform-specifics/index.md#creating-platform-specifics)
- [WindowsSpecific API](xref:Xamarin.Forms.PlatformConfiguration.WindowsSpecific)
