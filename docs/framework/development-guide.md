---
title: "Průvodce vývojem s použitím rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7aaac046a6f5022e4b903faacd609748092d2809
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="net-framework-development-guide"></a><span data-ttu-id="7b86b-102">Průvodce vývojem s použitím rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7b86b-102">.NET Framework Development Guide</span></span>
<span data-ttu-id="7b86b-103">Tato část vysvětluje, jak vytvářet, konfigurovat, ladění, zabezpečení a nasazení aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b86b-103">This section explains how to create, configure, debug, secure, and deploy your .NET Framework apps.</span></span> <span data-ttu-id="7b86b-104">Tato část taky poskytuje informace o technologii oblasti jako dynamické programování, vzájemná funkční spolupráce, rozšiřitelnosti, správa paměti a dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="7b86b-104">The section also provides information about technology areas such as dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b86b-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7b86b-105">In This Section</span></span>  
 [<span data-ttu-id="7b86b-106">Základy vytváření aplikací</span><span class="sxs-lookup"><span data-stu-id="7b86b-106">Application Essentials</span></span>](../../docs/standard/application-essentials.md)  
 <span data-ttu-id="7b86b-107">Poskytuje informace o základní aplikaci vývoj úloh, například programování s doménami aplikací a sestavení, pomocí atributů, formátování a analýza základních typů, pomocí kolekcí, zpracování události a výjimkami, použití souborů a datových proudů a pomocí Obecné typy.</span><span class="sxs-lookup"><span data-stu-id="7b86b-107">Provides information about basic app development tasks, such as programming with app domains and assemblies, using attributes, formatting and parsing base types, using collections, handling events and exceptions, using files and data streams, and using generics.</span></span>  
  
 [<span data-ttu-id="7b86b-108">Data a modelování</span><span class="sxs-lookup"><span data-stu-id="7b86b-108">Data and Modeling</span></span>](../../docs/framework/data/index.md)  
 <span data-ttu-id="7b86b-109">Poskytuje informace o tom, jak získat přístup k datům pomocí ADO.NET, jazyk integrovaného dotazu (LINQ), služby WCF Data Services a XML.</span><span class="sxs-lookup"><span data-stu-id="7b86b-109">Provides information about how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
 [<span data-ttu-id="7b86b-110">Klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="7b86b-110">Client Applications</span></span>](../../docs/framework/develop-client-apps.md)  
 <span data-ttu-id="7b86b-111">Vysvětluje, jak vytvářet aplikace pro systém Windows pomocí služby Windows Presentation Foundation (WPF) nebo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7b86b-111">Explains how to create Windows-based apps by using Windows Presentation Foundation (WPF) or Windows Forms.</span></span>  
  
 [<span data-ttu-id="7b86b-112">Webové aplikace s ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7b86b-112">Web Applications with ASP.NET</span></span>](../../docs/framework/develop-web-apps-with-aspnet.md)  
 <span data-ttu-id="7b86b-113">Obsahuje odkazy na informace o použití technologie ASP.NET můžete vytvářet podnikové webové aplikace s minimální kódování.</span><span class="sxs-lookup"><span data-stu-id="7b86b-113">Provides links to information about using ASP.NET to build enterprise-class web apps with a minimum of coding.</span></span>  
  
 [<span data-ttu-id="7b86b-114">Aplikace orientované na služby s použitím technologie WCF</span><span class="sxs-lookup"><span data-stu-id="7b86b-114">Service-Oriented Applications with WCF</span></span>](../../docs/framework/wcf/index.md)  
 <span data-ttu-id="7b86b-115">Popisuje, jak pomocí Windows Communication Foundation (WCF) můžete vytvářet aplikace orientované na služby, které jsou zabezpečený a spolehlivý.</span><span class="sxs-lookup"><span data-stu-id="7b86b-115">Describes how to use Windows Communication Foundation (WCF) to build service-oriented apps that are secure and reliable.</span></span>  
  
 <span data-ttu-id="7b86b-116">[Vytváření pracovních postupů s Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span><span class="sxs-lookup"><span data-stu-id="7b86b-116">[Building workflows with Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span></span>  
 <span data-ttu-id="7b86b-117">Poskytuje informace o modelu programování, ukázky a nástroje pro používání Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="7b86b-117">Provides information about the programming model, samples, and tools for using Windows Workflow Foundation (WF).</span></span>  

 [<span data-ttu-id="7b86b-118">Aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="7b86b-118">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
 <span data-ttu-id="7b86b-119">Vysvětluje, jak vytvořit aplikaci, která je nainstalována jako službu a spustit, zastavit a jinak kontrolovat své chování můžete Visual Studio a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b86b-119">Explains how you can use Visual Studio and the .NET Framework to create an app that is installed as a service, and start, stop, and otherwise control its behavior.</span></span>  
  
 [<span data-ttu-id="7b86b-120">Paralelní zpracování a souběžnost</span><span class="sxs-lookup"><span data-stu-id="7b86b-120">Parallel Processing and Concurrency</span></span>](../../docs/standard/parallel-processing-and-concurrency.md)  
 <span data-ttu-id="7b86b-121">Poskytuje informace o spravovaného dělení na vlákna, paralelní programování a vzory asynchronního programování návrhu.</span><span class="sxs-lookup"><span data-stu-id="7b86b-121">Provides information about managed threading, parallel programming, and asynchronous programming design patterns.</span></span>  
  
 [<span data-ttu-id="7b86b-122">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7b86b-122">Network Programming in the .NET Framework</span></span>](../../docs/framework/network-programming/index.md)  
 <span data-ttu-id="7b86b-123">Popisuje implementace vrstev, rozšiřitelný a spravovaných služeb Internetu, které můžete rychle a snadno integrovat do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="7b86b-123">Describes the layered, extensible, and managed implementation of Internet services that you can quickly and easily integrate into your apps.</span></span>  
  
 <span data-ttu-id="7b86b-124">[Konfigurace aplikací rozhraní .NET Framework](configure-apps/index.md)  </span><span class="sxs-lookup"><span data-stu-id="7b86b-124">[Configuring .NET Framework Apps](configure-apps/index.md)  </span></span>  
 <span data-ttu-id="7b86b-125">Vysvětluje, jak můžete použít konfigurační soubory, chcete-li změnit nastavení bez nutnosti její kompilace aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b86b-125">Explains how you can use configuration files to change settings without having to recompile your .NET Framework apps.</span></span>  
  
 [<span data-ttu-id="7b86b-126">Kompilování aplikací pomocí .NET Native</span><span class="sxs-lookup"><span data-stu-id="7b86b-126">Compiling Apps with .NET Native</span></span>](../../docs/framework/net-native/index.md)  
 <span data-ttu-id="7b86b-127">Vysvětluje, jak můžete pomocí [!INCLUDE[net_native](../../includes/net-native-md.md)] předkompilace technologie pro vytváření a nasazení aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="7b86b-127">Explains how you can use the [!INCLUDE[net_native](../../includes/net-native-md.md)] precompilation technology to build and deploy Windows Store apps.</span></span> [!INCLUDE[net_native](../../includes/net-native-md.md)]<span data-ttu-id="7b86b-128">zkompiluje aplikace, které jsou zapsané ve spravovaném kódu (C#) a která cílí na rozhraní .NET Framework do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7b86b-128"> compiles apps that are written in managed code (C#) and that target the .NET Framework to native code.</span></span>  
  
 [<span data-ttu-id="7b86b-129">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7b86b-129">Security</span></span>](../../docs/standard/security/index.md)  
 <span data-ttu-id="7b86b-130">Poskytuje informace o třídy a službách v rozhraní .NET Framework, které usnadňují vývoj zabezpečení aplikací.</span><span class="sxs-lookup"><span data-stu-id="7b86b-130">Provides information about the classes and services in the .NET Framework that facilitate secure app development.</span></span>  
  
 [<span data-ttu-id="7b86b-131">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="7b86b-131">Debugging, Tracing, and Profiling</span></span>](../../docs/framework/debug-trace-profile/index.md)  
 <span data-ttu-id="7b86b-132">Vysvětluje, jak otestovat, optimalizace a profil aplikace rozhraní .NET Framework a prostředí aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b86b-132">Explains how to test, optimize, and profile .NET Framework apps and the app environment.</span></span> <span data-ttu-id="7b86b-133">Tato část obsahuje informace pro správce i pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="7b86b-133">This section includes information for administrators as well as developers.</span></span>  
  
 [<span data-ttu-id="7b86b-134">Vývoj pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="7b86b-134">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="7b86b-135">Poskytuje informace o tom, jak můžete použít rozhraní .NET Framework k vytváření sestavení, které můžete sdílet mezi více platforem a více zařízení, jako jsou telefony, plochy a webový.</span><span class="sxs-lookup"><span data-stu-id="7b86b-135">Provides information about how you can use the .NET Framework to build assemblies that can be shared across multiple platforms and multiple devices such as phones, desktop, and web.</span></span>  
  
 [<span data-ttu-id="7b86b-136">Nasazení</span><span class="sxs-lookup"><span data-stu-id="7b86b-136">Deployment</span></span>](../../docs/framework/deployment/index.md)  
 <span data-ttu-id="7b86b-137">Vysvětluje, jak balíčků a distribuovat aplikace rozhraní .NET Framework a zahrnuje průvodcích nasazením pro vývojáře a správce.</span><span class="sxs-lookup"><span data-stu-id="7b86b-137">Explains how to package and distribute your .NET Framework app, and includes deployment guides for both developers and administrators.</span></span>  
  
 [<span data-ttu-id="7b86b-138">Výkon</span><span class="sxs-lookup"><span data-stu-id="7b86b-138">Performance</span></span>](../../docs/framework/performance/index.md)  
 <span data-ttu-id="7b86b-139">Poskytuje informace o ukládání do mezipaměti, opožděné inicializace, spolehlivosti a události trasování událostí.</span><span class="sxs-lookup"><span data-stu-id="7b86b-139">Provides information about caching, lazy initialization, reliability, and ETW events.</span></span>  
  
 <!--zz [Advanced Reading for the .NET Framework](http://msdn.microsoft.com/en-us/faae8083-fecb-4514-b133-b0a5a32a7c3c)  
 Provides information about advanced development tasks and techniques in the .NET Framework, including extensibility, interoperability, and reflection. Also includes the reference topics for unmanaged APIs that can be used by managed apps, such as runtime hosts, compilers, disassemblers, debuggers, and profilers.  --> 
  
## <a name="reference"></a><span data-ttu-id="7b86b-140">Odkaz</span><span class="sxs-lookup"><span data-stu-id="7b86b-140">Reference</span></span>  
 [<span data-ttu-id="7b86b-141">Knihovna tříd rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="7b86b-141">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.7)  
 <span data-ttu-id="7b86b-142">Poskytuje informace o využití pro každou třídu, která je součástí, syntaxe a příklady kódu [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] obory názvů.</span><span class="sxs-lookup"><span data-stu-id="7b86b-142">Supplies syntax, code examples, and usage information for each class that is contained in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7b86b-143">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7b86b-143">Related Sections</span></span>  
 [<span data-ttu-id="7b86b-144">Začínáme</span><span class="sxs-lookup"><span data-stu-id="7b86b-144">Getting Started</span></span>](../../docs/framework/get-started/index.md)  
 <span data-ttu-id="7b86b-145">Poskytuje ucelený přehled o rozhraní .NET Framework a odkazy na další materiály.</span><span class="sxs-lookup"><span data-stu-id="7b86b-145">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
 [<span data-ttu-id="7b86b-146">Co je nového</span><span class="sxs-lookup"><span data-stu-id="7b86b-146">What's New</span></span>](../../docs/framework/whats-new/index.md)  
 <span data-ttu-id="7b86b-147">Popisuje hlavní nové funkce a změny v nejnovější verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b86b-147">Describes key new features and changes in the latest version of the .NET Framework.</span></span> <span data-ttu-id="7b86b-148">Obsahuje seznam nových a zastaralé typy a členy a poskytuje vodítko k migraci aplikace z předchozí verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b86b-148">Includes lists of new and obsolete types and members, and provides a guide for migrating your apps from the previous version of the .NET Framework.</span></span>  
  
 [<span data-ttu-id="7b86b-149">Nástroje</span><span class="sxs-lookup"><span data-stu-id="7b86b-149">Tools</span></span>](../../docs/framework/tools/index.md)  
 <span data-ttu-id="7b86b-150">Popisuje nástroje, které vám pomohou vyvíjet, konfigurovat a nasazovat aplikace pomocí technologie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b86b-150">Describes the tools that help you develop, configure, and deploy apps by using .NET Framework technologies.</span></span>  
  
 [<span data-ttu-id="7b86b-151">.NET framework – ukázky</span><span class="sxs-lookup"><span data-stu-id="7b86b-151">.NET Framework Samples</span></span>](http://msdn.microsoft.com/en-us/177055f8-4a1f-43e7-aee6-995c196079b1)  
 <span data-ttu-id="7b86b-152">Obsahuje odkazy na ukázky galerie kódů MSDN ukázkových aplikací, které ukazují technologie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b86b-152">Provides links to the MSDN Code Samples Gallery for sample apps that demonstrate .NET Framework technologies.</span></span>
