---
title: Xamarin.Forms Shell 布局
description: 浮出控件后，Shell 应用程序中的下一级别导航为底部选项卡栏。 当一个选项卡包含多个页面时，页面将可通过顶部选项卡导航。
ms.prod: xamarin
ms.assetid: 318D81DB-E456-4E44-B083-36A27DBD9523
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 05/06/2019
ms.openlocfilehash: bc1ca01f4bf5cb8f7ef51c705319fb2cc1a0bd99
ms.sourcegitcommit: 9d90a26cbe13ebd106f55ba4a5445f28d9c18a1a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2019
ms.locfileid: "65054307"
---
# <a name="xamarinforms-shell-tabs"></a>Xamarin.Forms Shell 选项卡

![](~/media/shared/preview.png "此 API 当前为预发布版本")

[![下载示例](~/media/shared/download.png) 下载示例](https://github.com/xamarin/xamarin-forms-samples/tree/forms40/UserInterface/Xaminals/)

浮出控件后，Shell 应用程序中的下一级别导航为底部选项卡栏。 或者，浮出控件关闭时，系统将底部选项卡栏视作顶级导航。

每个 `FlyoutItem` 对象可以包含一个或多个 `Tab` 对象，每个 `Tab` 对象表示底部选项卡栏上的一个选项卡。 每个 `Tab` 对象可以包含一个或多个 `ShellContent` 对象，每个 `ShellContent` 对象将显示单个 [`ContentPage`](xref:Xamarin.Forms.ContentPage) 对象。 当一个 `Tab` 对象中存在多个 `ShellContent` 对象时，`ContentPage` 对象将可通过顶部选项卡导航。

在每个 `ContentPage` 对象中，可以导航到其他 `ContentPage` 对象。 有关导航的详细信息，请参阅 [Xamarin.Forms Shell 导航](navigation.md)。

## <a name="single-page-application"></a>单页应用程序

最简单的 Shell 应用程序为单页应用程序，可以通过向 `FlyoutItem` 对象添加单个 `Tab` 对象来创建该应用程序。 在 `Tab` 对象中，应将 `ShellContent` 对象设置为 [`ContentPage`](xref:Xamarin.Forms.ContentPage) 对象：

```xaml
<Shell xmlns="http://xamarin.com/schemas/2014/forms"
       xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
       xmlns:views="clr-namespace:Xaminals.Views"
       x:Class="Xaminals.AppShell"
       FlyoutBehavior="Disabled">
    <FlyoutItem>
        <Tab>
            <ShellContent>
                <views:CatsPage />
            </ShellContent>
        </Tab>
    </FlyoutItem>
</Shell>
```

此代码示例生成了以下单页应用程序：

[![iOS 和 Android 上 Shell 单页应用程序的屏幕截图](tabs-images/single-page-app.png "Shell 单页应用程序")](tabs-images/single-page-app-large.png#lightbox "Shell 单页应用程序")

单页应用程序中不需要浮出控件，因此将 `Shell.FlyoutBehavior` 属性设置为 `Disabled`。

> [!NOTE]
> 如果需要，可以通过在 [`ContentPage`](xref:Xamarin.Forms.ContentPage) 对象上将 `Shell.NavBarIsVisible` 附加属性设置为 `false` 来隐藏导航栏。

Shell 具有隐式转换运算符，可以简化 Shell 的视觉层次结构，而无需在可视化树中引入额外的视图。 这是可能的，因为子类 `Shell` 对象只能包含 `FlyoutItem` 对象，`FlyoutItem` 对象只能包含 `Tab` 对象，`Tab` 对象只能包含 `ShellContent` 对象。 这些隐式转换运算符可用于从前面的示例中删除 `FlyoutItem`、`Tab` 和 `ShellContent` 对象：

```xaml
<Shell xmlns="http://xamarin.com/schemas/2014/forms"
       xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
       xmlns:views="clr-namespace:Xaminals.Views"
       x:Class="Xaminals.AppShell"
       FlyoutBehavior="Disabled">
    <views:CatsPage />
</Shell>
```

此隐式转换自动将 [`ContentPage`](xref:Xamarin.Forms.ContentPage) 对象包装在 `ShellContent` 对象中，`ShellContent` 对象包装在 `Tab` 对象中，`Tab` 对象包装在 `FlyoutItem` 对象中。

> [!IMPORTANT]
> 在 Shell 应用程序中，作为 `ShellContent` 对象子对象的每个 [`ContentPage`](xref:Xamarin.Forms.ContentPage) 都是在应用程序启动期间创建的。 使用该方法添加其他 `ShellContent` 对象将导致在应用程序启动期间创建额外页面，这可能导致糟糕的启动体验。 不过，Shell 还能够根据需要创建页面，以响应导航。 有关详细信息，请参阅[高效页面加载](tabs.md#efficient-page-loading)。

## <a name="bottom-tabs"></a>底部选项卡

倘若一个 `FlyoutItem` 对象中有多个 `Tab` 对象，则 `Tab` 对象呈现为底部选项卡：

```xaml
<Shell xmlns="http://xamarin.com/schemas/2014/forms"
       xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
       xmlns:views="clr-namespace:Xaminals.Views"
       x:Class="Xaminals.AppShell"
       FlyoutBehavior="Disabled">
    <FlyoutItem>
        <Tab Title="Cats"
             Icon="cat.png">
            <ShellContent>
                <views:CatsPage />
            </ShellContent>
        </Tab>
        <Tab Title="Dogs"
             Icon="dog.png">
            <ShellContent>
                <views:DogsPage />
            </ShellContent>
        </Tab>
    </FlyoutItem>
</Shell>
```

选项卡标题和图标在每个 `Tab` 对象上设置，并在底部选项卡上显示：

[![iOS 和 Android 上带底部选项卡的 Shell 两页应用程序屏幕截图](tabs-images/two-page-app-bottom-tabs.png "带底部选项卡的 Shell 两页应用程序")](tabs-images/two-page-app-bottom-tabs-large.png#lightbox "带底部选项卡的 Shell 两页应用程序")

或者，可以使用 Shell 的隐式转换运算符删除前面示例中的 `ShellContent` 和 `Tab` 对象：

```xaml
<Shell xmlns="http://xamarin.com/schemas/2014/forms"
       xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
       xmlns:views="clr-namespace:Xaminals.Views"
       x:Class="Xaminals.AppShell"
       FlyoutBehavior="Disabled">
    <FlyoutItem>
        <views:CatsPage Icon="cat.png" />
        <views:DogsPage Icon="dog.png" />
    </FlyoutItem>
</Shell>
```

此隐式转换自动将每个 [`ContentPage`](xref:Xamarin.Forms.ContentPage) 对象包装在 `ShellContent` 对象中，然后将两者均包装在 `Tab` 对象中。

> [!IMPORTANT]
> 在 Shell 应用程序中，作为 `ShellContent` 对象子对象的每个 [`ContentPage`](xref:Xamarin.Forms.ContentPage) 都是在应用程序启动期间创建的。 使用该方法添加其他 `ShellContent` 对象将导致在应用程序启动期间创建额外页面，这可能导致糟糕的启动体验。 不过，Shell 还能够根据需要创建页面，以响应导航。 有关详细信息，请参阅[高效页面加载](tabs.md#efficient-page-loading)。

### <a name="tab-class"></a>Tab 类

`Tab` 类包含以下控制选项卡外观和行为的属性：

- `CurrentItem`，属于 `ShellContent` 类型，表示所选项。
- `FlyoutDisplayOptions`，属于 `FlyoutDisplayOptions` 类型，定义项及其子项在浮出控件中的显示方式。 默认值为 `AsSingleItem`。
- `FlyoutIcon`，属于 `ImageSource` 类型，定义将在浮出控件中显示的图标。
- `Icon`，属于 `ImageSource` 类型，定义要在 chrome 的非浮出控件部分显示的图标。
- `IsChecked`，属于 `boolean` 类型，定义项当前是否在浮出控件中突出显示。
- `IsEnabled`，属于 `boolean` 类型，定义项是否可在 chrome 中选择。
- `Items`，属于 `ShellContentCollection` 类型，定义 `Tab` 中的所有内容。
- `Title`，属于 `string` 类型，表示在 UI 中的选项卡上显示的标题。

## <a name="shell-content"></a>Shell 内容

每个 `Tab` 对象的子对象都是 `ShellContent` 对象，其 `Content` 属性设置为 [`ContentPage`](xref:Xamarin.Forms.ContentPage)：

```xaml
<Shell xmlns="http://xamarin.com/schemas/2014/forms"
       xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
       xmlns:views="clr-namespace:Xaminals.Views"
       x:Class="Xaminals.AppShell"
       FlyoutBehavior="Disabled">
    <FlyoutItem>
        <Tab Title="Cats"
             Icon="cat.png">
            <ShellContent>
                <views:CatsPage />
            </ShellContent>
        </Tab>
        <Tab Title="Dogs"
             Icon="dog.png">
            <ShellContent>
                <views:DogsPage />
            </ShellContent>
        </Tab>
    </FlyoutItem>
</Shell>
```

在每个 `ContentPage` 对象中，可以导航到其他 `ContentPage` 对象。 有关导航的详细信息，请参阅 [Xamarin.Forms Shell 导航](navigation.md)。

### <a name="shellcontent-class"></a>ShellContent 类

`ShellContent` 类包含以下控制选项卡内容外观和行为的属性：

- `Content`属于 `object` 类型，表示 `ShellContent` 的内容。
- `ContentTemplate`，属于 `DataTemplate` 类型，是用于动态放大 `ShellContent` 内容的模板。
- `FlyoutIcon`，属于 `ImageSource` 类型，定义将在浮出控件中显示的图标。
- `Icon`，属于 `ImageSource` 类型，定义要在 chrome 的非浮出控件部分显示的图标。
- `IsChecked`，属于 `boolean` 类型，定义项当前是否在浮出控件中突出显示。
- `IsEnabled`，属于 `boolean` 类型，定义项是否可在 chrome 中选择。
- `MenuItems`，属于 `MenuItemCollection` 类型，表示当此 `ShellContent` 为呈现页面时，要在浮出控件中显示的菜单项。
- `Title`，属于 `string` 类型，表示在 UI 中显示的标题。

所有这些属性都由 [`BindableProperty`](xref:Xamarin.Forms.BindableProperty) 对象提供支持，这意味着这些属性可以作为数据绑定的目标。

## <a name="bottom-and-top-tabs"></a>底部和顶部选项卡

当一个 `Tab` 对象中存在多个 `ShellContent` 对象时，将在底部选项卡中添加一个顶部选项卡栏，通过该选项卡栏可以导航 `ContentPage` 对象：

```xaml
<Shell xmlns="http://xamarin.com/schemas/2014/forms"
       xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
       xmlns:views="clr-namespace:Xaminals.Views"
       x:Class="Xaminals.AppShell"
       FlyoutBehavior="Disabled">
    <FlyoutItem>
        <Tab Title="Domestic"
             Icon="domestic.png">
            <ShellContent>
                <views:CatsPage />
            </ShellContent>
            <ShellContent>
                <views:DogsPage />
            </ShellContent>
        </Tab>
        <Tab Title="Monkeys"
             Icon="monkey.png">
            <ShellContent>
                <views:MonkeysPage />
            </ShellContent>
        </Tab>
    </FlyoutItem>
</Shell>
```

这会导致如以下屏幕截图中所示的布局：

[![iOS 和 Android 上带顶部和底部选项卡的 Shell 两页应用程序屏幕截图](tabs-images/two-page-app-top-tabs.png "带顶部和底部选项卡的 Shell 两页应用程序")](tabs-images/two-page-app-top-tabs-large.png#lightbox "带顶部和底部选项卡的 Shell 两页应用程序")

或者，可以使用 Shell 的隐式转换运算符删除前面示例中的 `ShellContent` 对象和第二个 `Tab` 对象：

```xaml
<Shell xmlns="http://xamarin.com/schemas/2014/forms"
       xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
       xmlns:views="clr-namespace:Xaminals.Views"
       x:Class="Xaminals.AppShell"
       FlyoutBehavior="Disabled">
    <FlyoutItem>
        <Tab Title="Domestic"
             Icon="domestic.png">
            <views:CatsPage />
            <views:DogsPage />
        </Tab>
        <views:MonkeysPage Icon="monkey.png" />
    </FlyoutItem>
</Shell>
```

此隐式转换自动将 `MonkeysPage` 包装在 `ShellContent` 对象中，然后将其包装在 `Tab` 对象中。 此外，`CatsPage` 和 `DogsPage` 隐式包装在 `ShellContent` 对象中。

## <a name="efficient-page-loading"></a>高效页面加载

在 Shell 应用程序中，`ShellContent` 对象中的每个 [`ContentPage`](xref:Xamarin.Forms.ContentPage) 对象都是在应用程序启动期间创建的，这可能会导致糟糕的启动体验。 不过，Shell 还允许根据需要创建页面，以响应导航。 这可以通过使用 `DataTemplate` 标记扩展来实现，将每个 `ContentPage` 转换为 [`DataTemplate`](xref:Xamarin.Forms.DataTemplate)，然后将结果设置为 `ShellContent.ContentTemplate` 属性值：

```xaml
<Shell xmlns="http://xamarin.com/schemas/2014/forms"
       xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
       xmlns:views="clr-namespace:Xaminals.Views"
       x:Class="Xaminals.AppShell">    
    <FlyoutItem Title="Animals"
                FlyoutDisplayOptions="AsMultipleItems">
        <Tab Title="Domestic"
             Icon="paw.png">
            <ShellContent Title="Cats"
                          Icon="cat.png"
                          ContentTemplate="{DataTemplate views:CatsPage}" />
            <ShellContent Title="Dogs"
                          Icon="dog.png"
                          ContentTemplate="{DataTemplate views:DogsPage}" />
        </Tab>
        <ShellContent Title="Monkeys"
                      Icon="monkey.png"
                      ContentTemplate="{DataTemplate views:MonkeysPage}" />
    </FlyoutItem>    
</Shell>
```

此 XAML 创建和显示 `CatsPage`，因为它是子类 `Shell` 对象中声明的第一个内容项。 可以通过底部选项卡导航到 `CatsPage` 和 `MonkeysPage`，只有在用户导航到它们时才会创建这些页面。 此方法的优点是避免了糟糕的启动体验，因为页面是根据响应导航需要创建的，而不是在应用程序启动时创建的。

## <a name="tab-appearance"></a>选项卡外观

`Shell` 类定义以下控制选项卡外观的属性：

- `ShellTabBarBackgroundColor` 是 `Color` 类型的附加属性，用于定义选项卡栏的背景色。 如果未设置属性，则使用 `ShellBackgroundColor` 属性值。
- `ShellTabBarDisabledColor` 是 `Color` 类型的附加属性，用于定义选项卡栏的禁用颜色。 如果未设置属性，则使用 `ShellDisabledColor` 属性值。
- `ShellTabBarForegroundColor` 是 `Color` 类型的附加属性，用于定义选项卡栏的前景色。 如果未设置属性，则使用 `ShellForegroundColor` 属性值。
- `ShellTabBarTitleColor` 是 `Color` 类型的附加属性，用于定义选项卡栏的标题颜色。 如果未设置属性，将使用 `ShellTitleColor` 属性值。
- `ShellTabBarUnselectedColor` 是 `Color` 类型的附加属性，用于定义选项卡栏的未选定颜色。 如果未设置属性，则使用 `ShellUnselectedColor` 属性值。

所有这些属性都由 [`BindableProperty`](xref:Xamarin.Forms.BindableProperty) 对象提供支持，这意味着这些属性可以作为数据绑定的目标。

因此，可以使用 XAML 样式设置选项卡样式。 下面的示例演示设置不同选项卡颜色属性的 XAML 样式：

```xaml
<Style x:Key="BaseStyle"
       TargetType="Element">
    <Setter Property="Shell.ShellTabBarBackgroundColor"
            Value="#3498DB" />
    <Setter Property="Shell.ShellTabBarTitleColor"
            Value="White" />
    <Setter Property="Shell.ShellTabBarUnselectedColor"
            Value="#B4FFFFFF" />
</Style>
```

此外，还可以使用级联样式表 (CSS) 来设置选项卡的样式。 有关详细信息，请参阅 [Xamarin.Forms Shell 特定属性](~/xamarin-forms/user-interface/styles/css/index.md#xamarinforms-shell-specific-properties)。

## <a name="related-links"></a>相关链接

- [Xaminals（示例）](https://github.com/xamarin/xamarin-forms-samples/tree/forms40/UserInterface/Xaminals/)
- [Xamarin.Forms Shell 导航](navigation.md)
- [Xamarin.Forms Shell 特定属性](~/xamarin-forms/user-interface/styles/css/index.md#xamarinforms-shell-specific-properties)