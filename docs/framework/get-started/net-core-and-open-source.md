---
title: .NET Core a open source
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc41a51a9c85b84f2f5365eb1650ebec37888652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="net-core-and-open-source"></a><span data-ttu-id="79939-102">.NET Core a open source</span><span class="sxs-lookup"><span data-stu-id="79939-102">.NET Core and Open-Source</span></span>
<span data-ttu-id="79939-103">Toto téma obsahuje stručný přehled co .NET Core a ukazuje, jak můžete najít další informace.</span><span class="sxs-lookup"><span data-stu-id="79939-103">This topic provides a brief overview  of what .NET Core is and shows how you can find more information.</span></span> <span data-ttu-id="79939-104">Úplný seznam témat pro .NET Core naleznete [.NET Core průvodce](../../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="79939-104">To find the complete list of topics for .NET Core, visit the [.NET Core Guide](../../core/index.md).</span></span>
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a><span data-ttu-id="79939-105">Co je .NET Core?</span><span class="sxs-lookup"><span data-stu-id="79939-105">What is .NET Core?</span></span>  
 <span data-ttu-id="79939-106">.NET core je obecné účely, modulární, napříč platformami a open source implementace .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="79939-106">.NET Core is a general purpose, modular, cross-platform and open source implementation of the .NET Standard.</span></span> <span data-ttu-id="79939-107">Obsahuje řadu stejná rozhraní API jako rozhraní .NET Framework (ale .NET Core je menší sadu) a zahrnuje modul runtime, framework, kompilátoru a nástroje pro součásti, které podporují celou řadu operačních systémů a čip cíle.</span><span class="sxs-lookup"><span data-stu-id="79939-107">It contains many of the same APIs as the .NET Framework (but .NET Core is a smaller set) and includes runtime, framework, compiler and tools components that support a variety of operating systems and chip targets.</span></span> <span data-ttu-id="79939-108">Implementace .NET Core se primárně vycházejí úlohami ASP.NET Core, ale také potřeba a chcete mít více moderní implementace.</span><span class="sxs-lookup"><span data-stu-id="79939-108">The .NET Core implementation was primarily driven by the ASP.NET Core workloads but also by the need and desire to have a more modern implementation.</span></span> <span data-ttu-id="79939-109">Je můžete použít v zařízení, cloudu a scénáře vložených/IoT.</span><span class="sxs-lookup"><span data-stu-id="79939-109">It can be used in device, cloud and embedded/IoT scenarios.</span></span>  
  
 <span data-ttu-id="79939-110">Chcete-li začít pracovat s .NET Core, navštivte [domovské stránky .NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="79939-110">To get started with .NET Core, please visit the [.NET Core homepage](https://www.microsoft.com/net/core).</span></span>  
  
 <span data-ttu-id="79939-111">Zde jsou hlavní vlastnosti .NET Core:</span><span class="sxs-lookup"><span data-stu-id="79939-111">Here are the main characteristics of .NET Core:</span></span>  
  
-   <span data-ttu-id="79939-112">**Napříč platformami:** .NET Core poskytuje klíčové funkce pro implementaci funkce aplikací, které potřebujete a znovu použít tento kód bez ohledu na vaše cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="79939-112">**Cross-platform:** .NET Core provides key functionality to implement the app features you need and reuse this code regardless of your platform target.</span></span> <span data-ttu-id="79939-113">Aktuálně podporuje tři hlavní operační systémy (OS): Windows, Linux a systému macOS.</span><span class="sxs-lookup"><span data-stu-id="79939-113">It currently supports three main operating systems (OS): Windows, Linux and macOS.</span></span> <span data-ttu-id="79939-114">Můžete napsat aplikace a knihovny, které běží ve podporované operační systémy beze změny.</span><span class="sxs-lookup"><span data-stu-id="79939-114">You can write apps and libraries that run unmodified across supported operating systems.</span></span> <span data-ttu-id="79939-115">Chcete-li zobrazit seznam podporovaných operačních systémů, navštivte [.NET Core plán](https://github.com/dotnet/core/blob/master/roadmap.md).</span><span class="sxs-lookup"><span data-stu-id="79939-115">To see the list of supported operating systems, visit [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).</span></span>
  
-   <span data-ttu-id="79939-116">**S otevřeným zdrojem:** .NET Core je jednou z mnoha projektů v části péči o [.NET Foundation](http://www.dotnetfoundation.org/) a je k dispozici na [Githubu](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="79939-116">**Open source:** .NET Core is one of the many projects under the stewardship of the [.NET Foundation](http://www.dotnetfoundation.org/) and is available on [GitHub](https://github.com/).</span></span>  <span data-ttu-id="79939-117">S .NET Core jako opensourcový projekt podporuje více transparentní procesu vývoje a zvýší úroveň aktivní a aktivnější komunity.</span><span class="sxs-lookup"><span data-stu-id="79939-117">Having .NET Core as an open source project promotes a more transparent development process and promotes an active and engaged community.</span></span>  
  
-   <span data-ttu-id="79939-118">**Flexibilní nasazení:** existují dva hlavní způsoby k nasazení své aplikace: samostatná nasazení nebo nasazení framework závislé.</span><span class="sxs-lookup"><span data-stu-id="79939-118">**Flexible deployment:** there are two main ways to deploy your app: framework-dependent deployment or self-contained deployment.</span></span> <span data-ttu-id="79939-119">Nasazení závislé na framework jsou nainstalované jenom svoje závislosti aplikace a třetích stran a aplikace závisí na systémové verzi .NET Core nacházet.</span><span class="sxs-lookup"><span data-stu-id="79939-119">With framework-dependent deployment, only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.</span></span>  <span data-ttu-id="79939-120">Samostatná nasazení verze .NET Core sloužící k vytvoření aplikace je nasazená taky společně s vaší aplikace a třetích stran závislosti a lze spustit souběžně sdílená s jinými verzemi.</span><span class="sxs-lookup"><span data-stu-id="79939-120">With self-contained deployment, the .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side-by-side with other versions.</span></span>    <span data-ttu-id="79939-121">Další informace najdete v tématu [nasazení aplikace .NET Core](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="79939-121">For more information, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>

-   <span data-ttu-id="79939-122">**Modulární:** .NET Core je modulární, protože bylo vydáno prostřednictvím balíčku NuGet v rámci menší balíčky sestavení.</span><span class="sxs-lookup"><span data-stu-id="79939-122">**Modular:** .NET Core is modular because it's released through NuGet in smaller assembly packages.</span></span> <span data-ttu-id="79939-123">Místo jeden velký sestavení, které obsahuje většinu základní funkce je k dispozici jako menší balíčky zaměřené na funkce .NET Core.</span><span class="sxs-lookup"><span data-stu-id="79939-123">Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller feature-centric packages.</span></span> <span data-ttu-id="79939-124">To umožňuje více agilní model vývoje pro nás a umožňuje optimalizovat aplikaci, kterou chcete zahrnout jenom balíčky NuGet, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="79939-124">This enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.</span></span> <span data-ttu-id="79939-125">Příklady výhod menší aplikace útoku spolehlivější zabezpečení snížit údržby, zvýšení výkonu a snížení nákladů ve model platím pro what--používání.</span><span class="sxs-lookup"><span data-stu-id="79939-125">The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.</span></span>  
  
## <a name="the-net-core-platform"></a><span data-ttu-id="79939-126">Možnosti základní platformy .NET</span><span class="sxs-lookup"><span data-stu-id="79939-126">The .NET Core Platform</span></span>  
 <span data-ttu-id="79939-127">Platformy .NET Core přišla několik komponent, která zahrnuje spravované kompilátory, modulu runtime, knihovny základní třídy a množství modely aplikace, jako je ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="79939-127">The .NET Core platform is made of several components, which includes the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.</span></span> <span data-ttu-id="79939-128">Další informace o různých komponent a získat zapojení, navštivte následující [Githubu](https://github.com/) úložiště:</span><span class="sxs-lookup"><span data-stu-id="79939-128">You can learn more about the different components and get engaged, by visiting the following [GitHub](https://github.com/) repos:</span></span>  
  
-   [<span data-ttu-id="79939-129">.NET Core</span><span class="sxs-lookup"><span data-stu-id="79939-129">.NET Core</span></span>](https://github.com/dotnet/core)  
  
-   [<span data-ttu-id="79939-130">CoreFX – základní knihovny .NET Core</span><span class="sxs-lookup"><span data-stu-id="79939-130">CoreFX - .NET Core foundational libraries</span></span>](https://github.com/dotnet/corefx)  
  
-   [<span data-ttu-id="79939-131">CoreCLR - .NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="79939-131">CoreCLR - .NET Core runtime</span></span>](https://github.com/dotnet/coreclr)  
  
-   [<span data-ttu-id="79939-132">Rozhraní příkazového řádku - nástroje příkazového řádku .NET Core</span><span class="sxs-lookup"><span data-stu-id="79939-132">CLI - .NET Core command-line tools</span></span>](https://github.com/dotnet/cli)  
  
-   [<span data-ttu-id="79939-133">Roslyn - kompilátoru platformy .NET</span><span class="sxs-lookup"><span data-stu-id="79939-133">Roslyn - .NET Compiler Platform</span></span>](https://github.com/dotnet/roslyn)  
  
-   [<span data-ttu-id="79939-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="79939-134">ASP.NET Core</span></span>](https://github.com/aspnet/home)  
  
## <a name="see-also"></a><span data-ttu-id="79939-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="79939-135">See Also</span></span>  
 [<span data-ttu-id="79939-136">.NET core domovské stránky</span><span class="sxs-lookup"><span data-stu-id="79939-136">.NET Core homepage</span></span>](https://www.microsoft.com/net/core)  
 [<span data-ttu-id="79939-137">Průvodce platformou .NET Core</span><span class="sxs-lookup"><span data-stu-id="79939-137">.NET Core Guide</span></span>](../../core/index.md)  
 [<span data-ttu-id="79939-138">Dokumentace k technologii ASP.NET</span><span class="sxs-lookup"><span data-stu-id="79939-138">ASP.NET Core Documentation</span></span>](/aspnet/core/)
