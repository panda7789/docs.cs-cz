---
title: Vývoj klientských aplikací systému Windows pomocí rozhraní .NET Framework
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
ms.openlocfilehash: b6b5f47980e7c0c87128b9efb782e637ed7144f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79181634"
---
# <a name="develop-client-applications-with-net-framework"></a><span data-ttu-id="1ed24-102">Vývoj klientských aplikací pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1ed24-102">Develop client applications with .NET Framework</span></span>

<span data-ttu-id="1ed24-103">Existuje několik způsobů, jak vyvíjet aplikace založené na systému Windows pomocí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ed24-103">There are several ways to develop Windows-based applications with .NET Framework.</span></span> <span data-ttu-id="1ed24-104">Můžete použít některý z těchto nástrojů a rámců:</span><span class="sxs-lookup"><span data-stu-id="1ed24-104">You can use any of these tools and frameworks:</span></span>

- [<span data-ttu-id="1ed24-105">Univerzální platforma Windows (UPW)</span><span class="sxs-lookup"><span data-stu-id="1ed24-105">Universal Windows Platform (UWP)</span></span>](/windows/uwp/)
- [<span data-ttu-id="1ed24-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="1ed24-106">Windows Presentation Foundation (WPF)</span></span>](./wpf/index.md)
- [<span data-ttu-id="1ed24-107">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1ed24-107">Windows Forms</span></span>](./winforms/index.md)

<span data-ttu-id="1ed24-108">Tato část obsahuje články, které popisují, jak vytvářet aplikace založené na systému Windows pomocí služby Windows Presentation Foundation nebo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1ed24-108">This section contains articles that describe how to create Windows-based applications by using Windows Presentation Foundation or Windows Forms.</span></span> <span data-ttu-id="1ed24-109">Můžete však také vytvářet webové aplikace pomocí rozhraní .NET Framework a klientských aplikací pro počítače nebo zařízení, které zpřístupníte prostřednictvím obchodu Microsoft Store (aplikace UPW).</span><span class="sxs-lookup"><span data-stu-id="1ed24-109">However, you can also create web applications using .NET Framework and client applications for computers or devices that you make available through Microsoft Store (UWP apps).</span></span>

## <a name="related-sections"></a><span data-ttu-id="1ed24-110">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1ed24-110">Related sections</span></span>

<span data-ttu-id="1ed24-111">[Univerzální platforma Windows](/windows/uwp/)</span><span class="sxs-lookup"><span data-stu-id="1ed24-111">[Universal Windows Platform](/windows/uwp/)</span></span>\
<span data-ttu-id="1ed24-112">Popisuje, jak vytvořit aplikace UPW, které můžete zpřístupnit uživatelům prostřednictvím obchodu Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="1ed24-112">Describes how to create UWP applications that you can make available to users through Microsoft Store.</span></span>

<span data-ttu-id="1ed24-113">[Rozhraní .NET API pro aplikace UPW](/dotnet/api/index?view=dotnet-uwp-10.0)</span><span class="sxs-lookup"><span data-stu-id="1ed24-113">[.NET API for UWP apps](/dotnet/api/index?view=dotnet-uwp-10.0)</span></span>\
<span data-ttu-id="1ed24-114">Odkaz na typy rozhraní .NET, které podporují aplikace UPW.</span><span class="sxs-lookup"><span data-stu-id="1ed24-114">Reference for .NET types that support UWP apps.</span></span>
  
<span data-ttu-id="1ed24-115">[Vývoj pro více platforem](../standard/cross-platform/index.md)</span><span class="sxs-lookup"><span data-stu-id="1ed24-115">[Develop for Multiple Platforms](../standard/cross-platform/index.md)</span></span>\
<span data-ttu-id="1ed24-116">Popisuje různé metody, které můžete použít rozhraní .NET Framework k cílení na více typů klientských aplikací.</span><span class="sxs-lookup"><span data-stu-id="1ed24-116">Describes the different methods you can use .NET Framework to target multiple client app types.</span></span>

<span data-ttu-id="1ed24-117">[Začínáme s ASP.NET weby](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span><span class="sxs-lookup"><span data-stu-id="1ed24-117">[Get Started with ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span></span>\
<span data-ttu-id="1ed24-118">Popisuje způsoby vývoje webových aplikací pomocí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1ed24-118">Describes the ways you can develop web apps using ASP.NET.</span></span>

<span data-ttu-id="1ed24-119">[Rozhraní API .NET pro Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="1ed24-119">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>\
<span data-ttu-id="1ed24-120">Seznamy rozhraní API rozhraní .NET Framework, které můžete použít pro vytváření aplikací pomocí programu Windows Phone Silverlight.</span><span class="sxs-lookup"><span data-stu-id="1ed24-120">Lists .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ed24-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ed24-121">See also</span></span>

- [<span data-ttu-id="1ed24-122">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="1ed24-122">.NET Standard</span></span>](../standard/net-standard.md)
- [<span data-ttu-id="1ed24-123">Přehled</span><span class="sxs-lookup"><span data-stu-id="1ed24-123">Overview</span></span>](./get-started/overview.md)
- [<span data-ttu-id="1ed24-124">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="1ed24-124">Development Guide</span></span>](./development-guide.md)
- [<span data-ttu-id="1ed24-125">Aplikace spouštěné jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="1ed24-125">Windows Service Applications</span></span>](./windows-services/index.md)
