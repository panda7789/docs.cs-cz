---
title: Vývoj klientských aplikací se systémem Windows pomocí .NET Framework
description: Vývoj aplikací založených na systému Windows pomocí .NET. Můžete použít Univerzální platforma Windows (UWP), Windows Presentation Foundation (WPF) nebo model Windows Forms.
ms.date: 01/09/2018
helpviewer_keywords:
- client application services
- applications [Windows Forms]
- Windows Presentation Foundation, in Visual Studio
- WPF, in Visual Studio
- Windows applications
- rich client applications
- .NET applications, Windows applications
- Visual Basic code, creating applications
- Visual C#, creating applications
- client/server applications, Windows applications
ms.assetid: 2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68
ms.openlocfilehash: 5920ecfae60274a8a504e4d300e531fd8b512901
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619387"
---
# <a name="develop-client-applications-with-net-framework"></a><span data-ttu-id="9f712-104">Vývoj klientských aplikací pomocí .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9f712-104">Develop client applications with .NET Framework</span></span>

<span data-ttu-id="9f712-105">Existuje několik způsobů, jak pomocí .NET Framework vyvíjet aplikace pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="9f712-105">There are several ways to develop Windows-based applications with .NET Framework.</span></span> <span data-ttu-id="9f712-106">Můžete použít kterýkoli z těchto nástrojů a platforem:</span><span class="sxs-lookup"><span data-stu-id="9f712-106">You can use any of these tools and frameworks:</span></span>

- [<span data-ttu-id="9f712-107">Univerzální platforma Windows (UPW)</span><span class="sxs-lookup"><span data-stu-id="9f712-107">Universal Windows Platform (UWP)</span></span>](/windows/uwp/)
- [<span data-ttu-id="9f712-108">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="9f712-108">Windows Presentation Foundation (WPF)</span></span>](./wpf/index.md)
- [<span data-ttu-id="9f712-109">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f712-109">Windows Forms</span></span>](./winforms/index.md)

<span data-ttu-id="9f712-110">Tato část obsahuje články, které popisují, jak vytvářet aplikace pro systém Windows pomocí Windows Presentation Foundation nebo model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9f712-110">This section contains articles that describe how to create Windows-based applications by using Windows Presentation Foundation or Windows Forms.</span></span> <span data-ttu-id="9f712-111">Můžete ale také vytvořit webové aplikace pomocí .NET Framework a klientských aplikací pro počítače nebo zařízení, které zpřístupníte prostřednictvím Microsoft Store (aplikace UWP).</span><span class="sxs-lookup"><span data-stu-id="9f712-111">However, you can also create web applications using .NET Framework and client applications for computers or devices that you make available through Microsoft Store (UWP apps).</span></span>

## <a name="related-sections"></a><span data-ttu-id="9f712-112">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9f712-112">Related sections</span></span>

<span data-ttu-id="9f712-113">[Univerzální platforma Windows](/windows/uwp/)</span><span class="sxs-lookup"><span data-stu-id="9f712-113">[Universal Windows Platform](/windows/uwp/)</span></span>\
<span data-ttu-id="9f712-114">Popisuje, jak vytvářet aplikace UWP, které můžete uživatelům zpřístupnit prostřednictvím Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="9f712-114">Describes how to create UWP applications that you can make available to users through Microsoft Store.</span></span>

<span data-ttu-id="9f712-115">[Rozhraní .NET API pro aplikace UWP](/dotnet/api/index?view=dotnet-uwp-10.0)</span><span class="sxs-lookup"><span data-stu-id="9f712-115">[.NET API for UWP apps](/dotnet/api/index?view=dotnet-uwp-10.0)</span></span>\
<span data-ttu-id="9f712-116">Referenční informace o typech .NET, které podporují aplikace pro UWP</span><span class="sxs-lookup"><span data-stu-id="9f712-116">Reference for .NET types that support UWP apps.</span></span>
  
<span data-ttu-id="9f712-117">[Vývoj pro různé platformy](../standard/cross-platform/index.md)</span><span class="sxs-lookup"><span data-stu-id="9f712-117">[Develop for Multiple Platforms](../standard/cross-platform/index.md)</span></span>\
<span data-ttu-id="9f712-118">V této části najdete popis různých metod, které můžete použít .NET Framework k zacílení na několik typů klientských aplikací.</span><span class="sxs-lookup"><span data-stu-id="9f712-118">Describes the different methods you can use .NET Framework to target multiple client app types.</span></span>

<span data-ttu-id="9f712-119">[Začínáme s ASP.NET weby](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span><span class="sxs-lookup"><span data-stu-id="9f712-119">[Get Started with ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span></span>\
<span data-ttu-id="9f712-120">Popisuje způsoby, jak můžete vyvíjet webové aplikace pomocí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9f712-120">Describes the ways you can develop web apps using ASP.NET.</span></span>

<span data-ttu-id="9f712-121">[Rozhraní .NET API pro Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="9f712-121">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>\
<span data-ttu-id="9f712-122">Seznam .NET Framework rozhraní API, která můžete použít k vytváření aplikací pomocí Windows Phone Silverlight.</span><span class="sxs-lookup"><span data-stu-id="9f712-122">Lists .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f712-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f712-123">See also</span></span>

- [<span data-ttu-id="9f712-124">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="9f712-124">.NET Standard</span></span>](../standard/net-standard.md)
- [<span data-ttu-id="9f712-125">Přehled</span><span class="sxs-lookup"><span data-stu-id="9f712-125">Overview</span></span>](./get-started/overview.md)
- [<span data-ttu-id="9f712-126">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="9f712-126">Development Guide</span></span>](./development-guide.md)
- [<span data-ttu-id="9f712-127">Aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="9f712-127">Windows Service Applications</span></span>](./windows-services/index.md)
