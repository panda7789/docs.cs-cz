---
title: "Vývoj klientských aplikací s použitím rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f90cbac0e7f78d8965a75df281c0db6b213d9e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="020e0-102">Vývoj klientských aplikací s použitím rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="020e0-102">Developing Client Applications with the .NET Framework</span></span>
<span data-ttu-id="020e0-103">K vývoji aplikací systému Windows, s rozhraním .NET framework, které běží místně na počítače uživatelů nebo zařízení několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="020e0-103">There are multiple ways to develop Windows-based applications with the .NET framework that run locally on users' computers or devices.</span></span> <span data-ttu-id="020e0-104">Tento oddíl obsahuje témata, které popisují, jak vytvářet aplikace pro systém Windows pomocí Windows Presentation Foundation (WPF) nebo pomocí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="020e0-104">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation (WPF) or by using Windows Forms.</span></span> <span data-ttu-id="020e0-105">Můžete však také vytvořit webových aplikací pomocí rozhraní .NET Framework a klientské aplikace pro počítače nebo zařízení, které dáte k dispozici prostřednictvím Windows Store nebo Windows Phone Store.</span><span class="sxs-lookup"><span data-stu-id="020e0-105">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Windows Store or Windows Phone Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="020e0-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="020e0-106">In This Section</span></span>  
 [<span data-ttu-id="020e0-107">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="020e0-107">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
 <span data-ttu-id="020e0-108">Poskytuje informace o vývoji aplikací pomocí grafického subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="020e0-108">Provides information about developing applications by using WPF.</span></span>  
  
 [<span data-ttu-id="020e0-109">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="020e0-109">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
 <span data-ttu-id="020e0-110">Poskytuje informace o vývoji aplikací s použitím Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="020e0-110">Provides information about developing applications by using Windows Forms.</span></span>  
  
 [<span data-ttu-id="020e0-111">Technologie CCT (Common Client Technologies)</span><span class="sxs-lookup"><span data-stu-id="020e0-111">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
 <span data-ttu-id="020e0-112">Poskytuje informace o další technologie, které lze použít při vývoji klientských aplikací.</span><span class="sxs-lookup"><span data-stu-id="020e0-112">Provides information about additional technologies that can be used when developing client applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="020e0-113">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="020e0-113">Related Sections</span></span>  
 [<span data-ttu-id="020e0-114">Aplikace pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="020e0-114">Windows Store apps</span></span>](http://msdn.microsoft.com/windows/apps/)  
 <span data-ttu-id="020e0-115">Popisuje, jak vytvářet aplikace, které můžete zpřístupnit uživatelům přes Windows Store</span><span class="sxs-lookup"><span data-stu-id="020e0-115">Describes how to create apps that you can make available to users through the Windows Store</span></span>  
  
 [<span data-ttu-id="020e0-116">Aplikace .NET pro Store</span><span class="sxs-lookup"><span data-stu-id="020e0-116">.NET for Store apps</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 <span data-ttu-id="020e0-117">Popisuje podporu rozhraní .NET Framework pro aplikace pro Store, které se dá nasadit na počítače se systémem Windows a zařízení.</span><span class="sxs-lookup"><span data-stu-id="020e0-117">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>  
  
 <span data-ttu-id="020e0-118">[Rozhraní API .NET pro Windows Phone Silverlight](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="020e0-118">[.NET API for Windows Phone Silverlight](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span></span>  
 <span data-ttu-id="020e0-119">Seznam API technologie .NET Framework, můžete použít pro vytváření aplikací s Windows Phone Silverlight</span><span class="sxs-lookup"><span data-stu-id="020e0-119">List the .NET Framework APIs you can use for building apps with Windows Phone Silverlight</span></span>  
  
 [<span data-ttu-id="020e0-120">Vývoj pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="020e0-120">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="020e0-121">Popisuje různé metody, které můžete použít rozhraní .NET Framework pro více typů aplikace klienta.</span><span class="sxs-lookup"><span data-stu-id="020e0-121">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>  
  
 [<span data-ttu-id="020e0-122">Začínáme s ASP.NET – webové servery</span><span class="sxs-lookup"><span data-stu-id="020e0-122">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
 <span data-ttu-id="020e0-123">Popisuje způsoby, jak můžete vyvíjet webové aplikace pomocí technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="020e0-123">Describes the ways you can develop web apps using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="020e0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="020e0-124">See Also</span></span>  
 [<span data-ttu-id="020e0-125">Přenosná knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="020e0-125">Portable Class Library</span></span>](../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)  
 [<span data-ttu-id="020e0-126">Přehled</span><span class="sxs-lookup"><span data-stu-id="020e0-126">Overview</span></span>](../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="020e0-127">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="020e0-127">Development Guide</span></span>](../../docs/framework/development-guide.md)  
 [<span data-ttu-id="020e0-128">Postupy: vytvoření aplikace Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="020e0-128">How to: Create a Windows Desktop Application</span></span>](http://msdn.microsoft.com/library/47021403-eaca-4c34-946a-a26c42a64148)  
 [<span data-ttu-id="020e0-129">Aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="020e0-129">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)
