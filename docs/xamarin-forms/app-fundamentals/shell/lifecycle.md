---
title: Xamarin.Forms Shell 生命周期
description: Shell 应用程序遵循 Xamarin.Forms 生命周期，当页面将出现在屏幕上时，将引发 Appearing 事件，当页面将从屏幕上消失时，将引发 Disappearing 事件。
ms.prod: ''
ms.assetid: ''
ms.technology: ''
author: ''
ms.author: ''
ms.date: ''
no-loc:
- Xamarin.Forms
- Xamarin.Essentials
ms.openlocfilehash: 3a7a46187d861098b61f638a3fb460d890b081dd
ms.sourcegitcommit: 57bc714633364aeb34aba9803e88802bebf321ba
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84138718"
---
# <a name="xamarinforms-shell-lifecycle"></a>Xamarin.Forms Shell 生命周期

[![下载示例](~/media/shared/download.png) 下载示例](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-xaminals/)

Shell 应用程序遵循 Xamarin.Forms 生命周期，当页面将出现在屏幕上时，将引发 `Appearing` 事件，当页面将从屏幕上消失时，将引发 `Disappearing` 事件。 这些事件会传播到页面，可以通过重写页面上的 [`OnAppearing`](xref:Xamarin.Forms.Page.OnAppearing) 或 [`OnDisappearing`](xref:Xamarin.Forms.Page.OnDisappearing) 方法进行处理。

> [!NOTE]
> 在 Shell 应用程序中，在平台代码使页面可见或从屏幕上删除页面之前，跨平台代码中将引发 `Appearing` 和 `Disappearing` 事件。

有关 Xamarin.Forms 应用生命周期的详细信息，请参阅 [Xamarin.Forms 应用生命周期](~/xamarin-forms/app-fundamentals/app-lifecycle.md)。

## <a name="hierarchical-navigation"></a>分层导航

在 Shell 应用程序中，将页面推送到导航堆栈将导致当前可见的 `ShellContent` 对象及其页面内容引发 `Disappearing` 事件。 同样，从导航堆栈中弹出最后一个页面将导致最新可见的 `ShellContent` 对象及其页面内容引发 `Appearing` 事件。

有关分层导航的详细信息，请参阅 [Xamarin.Forms 分层导航](~/xamarin-forms/app-fundamentals/navigation/hierarchical.md)。

## <a name="modal-navigation"></a>模式导航

在 Shell 应用程序中，将模式页面推送到模式导航堆栈将导致所有可见 Shell 对象引发 `Disappearing` 事件。 同样，从模式导航堆栈中弹出最后一个模式页面将导致所有可见 Shell 对象引发 `Appearing` 事件。

有关模式导航的详细信息，请参阅 [Xamarin.Forms 模式页面](~/xamarin-forms/app-fundamentals/navigation/modal.md)。

## <a name="related-links"></a>相关链接

- [Xaminals（示例）](https://docs.microsoft.com/samples/xamarin/xamarin-forms-samples/userinterface-xaminals/)
- [Xamarin.Forms 应用生命周期](~/xamarin-forms/app-fundamentals/app-lifecycle.md)
- [Xamarin.Forms 模式页面](~/xamarin-forms/app-fundamentals/navigation/modal.md)
