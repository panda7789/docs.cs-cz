---
title: Vývoj aplikací klienta se systémem Windows s využitím rozhraní .NET Framework
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
ms.openlocfilehash: 987f8e25014e8ce6413c998f6eb78d821558ecec
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400360"
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="b7270-102">Vývoj klientských aplikací s použitím rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b7270-102">Developing client applications with the .NET Framework</span></span>

<span data-ttu-id="b7270-103">Existuje několik způsobů, jak vyvíjet aplikace Windows využívající rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7270-103">There are several ways to develop Windows-based applications with the .NET Framework.</span></span> <span data-ttu-id="b7270-104">Můžete použít některý z těchto nástrojů a platforem:</span><span class="sxs-lookup"><span data-stu-id="b7270-104">You can use any of these tools and frameworks:</span></span> 

* [<span data-ttu-id="b7270-105">Univerzální platforma Windows (UPW)</span><span class="sxs-lookup"><span data-stu-id="b7270-105">Universal Windows Platform (UWP)</span></span>](https://developer.microsoft.com/windows/apps)
* [<span data-ttu-id="b7270-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b7270-106">Windows Presentation Foundation (WPF)</span></span>](../../docs/framework/wpf/index.md)
* [<span data-ttu-id="b7270-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b7270-107">Windows Forms</span></span>](../../docs/framework/winforms/index.md)

<span data-ttu-id="b7270-108">Tento oddíl obsahuje témata, která popisují, jak vytvářet aplikace pro systém Windows s použitím Windows Presentation Foundation nebo pomocí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b7270-108">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation or by using Windows Forms.</span></span> <span data-ttu-id="b7270-109">Můžete ale také vytvořit webové aplikace pomocí rozhraní .NET Framework a klientských aplikací pro počítače nebo zařízení, které dáte k dispozici přes Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="b7270-109">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Microsoft Store.</span></span>
 
## <a name="in-this-section"></a><span data-ttu-id="b7270-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b7270-110">In this section</span></span>

[<span data-ttu-id="b7270-111">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="b7270-111">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
<span data-ttu-id="b7270-112">Poskytuje informace o vývoji aplikací s použitím WPF.</span><span class="sxs-lookup"><span data-stu-id="b7270-112">Provides information about developing applications by using WPF.</span></span>

[<span data-ttu-id="b7270-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b7270-113">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
<span data-ttu-id="b7270-114">Poskytuje informace o vývoji aplikací s použitím Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b7270-114">Provides information about developing applications by using Windows Forms.</span></span>

[<span data-ttu-id="b7270-115">Technologie CCT (Common Client Technologies)</span><span class="sxs-lookup"><span data-stu-id="b7270-115">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
<span data-ttu-id="b7270-116">Poskytuje informace o dalších technologiích, které se dá použít při vývoji klientských aplikací.</span><span class="sxs-lookup"><span data-stu-id="b7270-116">Provides information about additional technologies that can be used when developing client applications.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b7270-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b7270-117">Related sections</span></span>

[<span data-ttu-id="b7270-118">Universal Windows Platform</span><span class="sxs-lookup"><span data-stu-id="b7270-118">Universal Windows Platform</span></span>](https://developer.microsoft.com/windows/apps)  
<span data-ttu-id="b7270-119">Popisuje, jak vytvářet aplikace pro Windows 10, která můžete zpřístupnit uživatelům prostřednictvím Windows Store.</span><span class="sxs-lookup"><span data-stu-id="b7270-119">Describes how to create applications for Windows 10 that you can make available to users through the Windows Store.</span></span>

[<span data-ttu-id="b7270-120">.NET pro aplikace pro UPW</span><span class="sxs-lookup"><span data-stu-id="b7270-120">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)  
<span data-ttu-id="b7270-121">Popisuje podporu rozhraní .NET Framework pro Store aplikace, které je možné nasadit do počítačů s Windows a zařízení.</span><span class="sxs-lookup"><span data-stu-id="b7270-121">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>

<span data-ttu-id="b7270-122">[Rozhraní .NET API pro Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="b7270-122">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>  
<span data-ttu-id="b7270-123">Zobrazí seznam API rozhraní .NET Framework můžete použít pro vytváření aplikací pro Windows Phone Silverlight.</span><span class="sxs-lookup"><span data-stu-id="b7270-123">Lists the .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>
  
[<span data-ttu-id="b7270-124">Vývoj pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="b7270-124">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
<span data-ttu-id="b7270-125">Popisuje různé metody rozhraní .NET Framework můžete cílit na více typy klientských aplikací.</span><span class="sxs-lookup"><span data-stu-id="b7270-125">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>

[<span data-ttu-id="b7270-126">Začínáme s weby ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b7270-126">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
<span data-ttu-id="b7270-127">Popisuje způsoby, kterými vám umožní vytvářet webové aplikace s využitím technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b7270-127">Describes the ways you can develop web apps using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7270-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7270-128">See also</span></span>

[<span data-ttu-id="b7270-129">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="b7270-129">.NET Standard</span></span>](../../docs/standard/net-standard.md)  
[<span data-ttu-id="b7270-130">Přehled</span><span class="sxs-lookup"><span data-stu-id="b7270-130">Overview</span></span>](../../docs/framework/get-started/overview.md)  
[<span data-ttu-id="b7270-131">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="b7270-131">Development Guide</span></span>](../../docs/framework/development-guide.md)  
[<span data-ttu-id="b7270-132">Aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="b7270-132">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
