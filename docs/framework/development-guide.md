---
title: Průvodce vývojem s použitím rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
ms.openlocfilehash: abc392116aec8ffd8aa94f46ef97887c48516ca0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122471"
---
# <a name="net-framework-development-guide"></a><span data-ttu-id="ecca9-102">Průvodce vývojem s použitím rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ecca9-102">.NET Framework Development Guide</span></span>
<span data-ttu-id="ecca9-103">V této části se dozvíte, jak vytvářet, konfigurovat, ladit, zabezpečovat a nasazovat aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecca9-103">This section explains how to create, configure, debug, secure, and deploy your .NET Framework apps.</span></span> <span data-ttu-id="ecca9-104">V této části najdete taky informace o technologických oblastech, jako je dynamické programování, interoperabilita, rozšiřitelnost, Správa paměti a dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="ecca9-104">The section also provides information about technology areas such as dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ecca9-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ecca9-105">In This Section</span></span>  
 [<span data-ttu-id="ecca9-106">Základy vytváření aplikací</span><span class="sxs-lookup"><span data-stu-id="ecca9-106">Application Essentials</span></span>](../standard/application-essentials.md)  
 <span data-ttu-id="ecca9-107">Poskytuje informace o úlohách vývoje základních aplikací, jako je například programování s doménami aplikací a sestaveními, použití atributů, formátování a analýza základních typů, použití kolekcí, zpracování událostí a výjimek, používání souborů a datových proudů a používání Obecné typy.</span><span class="sxs-lookup"><span data-stu-id="ecca9-107">Provides information about basic app development tasks, such as programming with app domains and assemblies, using attributes, formatting and parsing base types, using collections, handling events and exceptions, using files and data streams, and using generics.</span></span>  
  
 [<span data-ttu-id="ecca9-108">Data a modelování</span><span class="sxs-lookup"><span data-stu-id="ecca9-108">Data and Modeling</span></span>](./data/index.md)  
 <span data-ttu-id="ecca9-109">Poskytuje informace o tom, jak získat přístup k datům pomocí ADO.NET, jazyka Integrated Query (LINQ), WCF Data Services a XML.</span><span class="sxs-lookup"><span data-stu-id="ecca9-109">Provides information about how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
 [<span data-ttu-id="ecca9-110">Klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="ecca9-110">Client Applications</span></span>](develop-client-apps.md)  
 <span data-ttu-id="ecca9-111">Vysvětluje, jak vytvořit aplikace založené na systému Windows pomocí Windows Presentation Foundation (WPF) nebo model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ecca9-111">Explains how to create Windows-based apps by using Windows Presentation Foundation (WPF) or Windows Forms.</span></span>  
  
 [<span data-ttu-id="ecca9-112">Webové aplikace s ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ecca9-112">Web Applications with ASP.NET</span></span>](develop-web-apps-with-aspnet.md)  
 <span data-ttu-id="ecca9-113">Obsahuje odkazy na informace o použití ASP.NET k vytváření webových aplikací podnikové třídy s minimálním kódováním.</span><span class="sxs-lookup"><span data-stu-id="ecca9-113">Provides links to information about using ASP.NET to build enterprise-class web apps with a minimum of coding.</span></span>  
  
 [<span data-ttu-id="ecca9-114">Aplikace orientované na služby s použitím technologie WCF</span><span class="sxs-lookup"><span data-stu-id="ecca9-114">Service-Oriented Applications with WCF</span></span>](./wcf/index.md)  
 <span data-ttu-id="ecca9-115">Popisuje, jak používat Windows Communication Foundation (WCF) k vytváření aplikací orientovaných na služby, které jsou bezpečné a spolehlivé.</span><span class="sxs-lookup"><span data-stu-id="ecca9-115">Describes how to use Windows Communication Foundation (WCF) to build service-oriented apps that are secure and reliable.</span></span>  
  
 <span data-ttu-id="ecca9-116">[Vytváření pracovních postupů pomocí programovací model Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span><span class="sxs-lookup"><span data-stu-id="ecca9-116">[Building workflows with Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span></span>  
 <span data-ttu-id="ecca9-117">Poskytuje informace o programovacím modelu, ukázkách a nástrojích pro použití programovací model Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="ecca9-117">Provides information about the programming model, samples, and tools for using Windows Workflow Foundation (WF).</span></span>  

 [<span data-ttu-id="ecca9-118">Aplikace služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="ecca9-118">Windows Service Applications</span></span>](./windows-services/index.md)  
 <span data-ttu-id="ecca9-119">Vysvětluje, jak můžete pomocí sady Visual Studio a .NET Framework vytvořit aplikaci, která je nainstalována jako služba, a spustit, zastavit a jinak řídit její chování.</span><span class="sxs-lookup"><span data-stu-id="ecca9-119">Explains how you can use Visual Studio and the .NET Framework to create an app that is installed as a service, and start, stop, and otherwise control its behavior.</span></span>  
  
 [<span data-ttu-id="ecca9-120">Paralelní zpracování, souběžnost a asynchronní programování v .NET</span><span class="sxs-lookup"><span data-stu-id="ecca9-120">Parallel Processing, Concurrency, and Async Programming in .NET</span></span>](../standard/parallel-processing-and-concurrency.md)  
 <span data-ttu-id="ecca9-121">Poskytuje informace o spravovaných vláknech, paralelním programování a vzorech návrhu asynchronního programování.</span><span class="sxs-lookup"><span data-stu-id="ecca9-121">Provides information about managed threading, parallel programming, and asynchronous programming design patterns.</span></span>  
  
 [<span data-ttu-id="ecca9-122">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ecca9-122">Network Programming in the .NET Framework</span></span>](./network-programming/index.md)  
 <span data-ttu-id="ecca9-123">Popisuje vrstvenou, rozšiřitelnou a spravovanou implementaci internetových služeb, které můžete snadno a snadno integrovat do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="ecca9-123">Describes the layered, extensible, and managed implementation of Internet services that you can quickly and easily integrate into your apps.</span></span>  
  
 <span data-ttu-id="ecca9-124">[Konfigurace aplikací .NET Framework](configure-apps/index.md)  </span><span class="sxs-lookup"><span data-stu-id="ecca9-124">[Configuring .NET Framework Apps](configure-apps/index.md)  </span></span>  
 <span data-ttu-id="ecca9-125">Vysvětluje, jak můžete pomocí konfiguračních souborů změnit nastavení bez nutnosti překompilovat aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecca9-125">Explains how you can use configuration files to change settings without having to recompile your .NET Framework apps.</span></span>  
  
 [<span data-ttu-id="ecca9-126">Kompilování aplikací pomocí .NET Native</span><span class="sxs-lookup"><span data-stu-id="ecca9-126">Compiling Apps with .NET Native</span></span>](./net-native/index.md)  
 <span data-ttu-id="ecca9-127">Vysvětluje, jak můžete použít technologii předkompilace .NET Native k sestavování a nasazování aplikací pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ecca9-127">Explains how you can use the .NET Native precompilation technology to build and deploy Windows Store apps.</span></span> <span data-ttu-id="ecca9-128">.NET Native zkompiluje aplikace, které jsou napsány ve spravovaném kódu (C#) a cílí na .NET Framework do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="ecca9-128">.NET Native compiles apps that are written in managed code (C#) and that target the .NET Framework to native code.</span></span>  
  
 [<span data-ttu-id="ecca9-129">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ecca9-129">Security</span></span>](../standard/security/index.md)  
 <span data-ttu-id="ecca9-130">Poskytuje informace o třídách a službách v .NET Framework, které usnadňují vývoj zabezpečených aplikací.</span><span class="sxs-lookup"><span data-stu-id="ecca9-130">Provides information about the classes and services in the .NET Framework that facilitate secure app development.</span></span>  
  
 [<span data-ttu-id="ecca9-131">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="ecca9-131">Debugging, Tracing, and Profiling</span></span>](./debug-trace-profile/index.md)  
 <span data-ttu-id="ecca9-132">Vysvětluje, jak testovat, optimalizovat a profilovat .NET Framework aplikace a prostředí aplikace.</span><span class="sxs-lookup"><span data-stu-id="ecca9-132">Explains how to test, optimize, and profile .NET Framework apps and the app environment.</span></span> <span data-ttu-id="ecca9-133">Tato část obsahuje informace o správcích i o vývojářích.</span><span class="sxs-lookup"><span data-stu-id="ecca9-133">This section includes information for administrators as well as developers.</span></span>  
  
 [<span data-ttu-id="ecca9-134">Vývoj pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="ecca9-134">Developing for Multiple Platforms</span></span>](../standard/cross-platform/index.md)  
 <span data-ttu-id="ecca9-135">Poskytuje informace o tom, jak můžete použít .NET Framework k sestavení sestavení, která lze sdílet napříč různými platformami a více zařízeními, jako jsou telefony, počítače a Web.</span><span class="sxs-lookup"><span data-stu-id="ecca9-135">Provides information about how you can use the .NET Framework to build assemblies that can be shared across multiple platforms and multiple devices such as phones, desktop, and web.</span></span>  
  
 [<span data-ttu-id="ecca9-136">Nasazení</span><span class="sxs-lookup"><span data-stu-id="ecca9-136">Deployment</span></span>](./deployment/index.md)  
 <span data-ttu-id="ecca9-137">Vysvětluje, jak zabalit a distribuovat aplikaci .NET Framework a obsahuje Průvodce nasazením pro vývojáře i správce.</span><span class="sxs-lookup"><span data-stu-id="ecca9-137">Explains how to package and distribute your .NET Framework app, and includes deployment guides for both developers and administrators.</span></span>  
  
 [<span data-ttu-id="ecca9-138">Výkon</span><span class="sxs-lookup"><span data-stu-id="ecca9-138">Performance</span></span>](./performance/index.md)  
 <span data-ttu-id="ecca9-139">Poskytuje informace o ukládání do mezipaměti, opožděné inicializaci, spolehlivosti a událostech ETW.</span><span class="sxs-lookup"><span data-stu-id="ecca9-139">Provides information about caching, lazy initialization, reliability, and ETW events.</span></span>  
 
## <a name="reference"></a><span data-ttu-id="ecca9-140">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ecca9-140">Reference</span></span>  
 [<span data-ttu-id="ecca9-141">Knihovna tříd .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ecca9-141">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.7)  
 <span data-ttu-id="ecca9-142">Poskytuje syntaxi, příklady kódu a informace o využití pro každou třídu, která je obsažena v .NET Framework obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ecca9-142">Supplies syntax, code examples, and usage information for each class that is contained in the .NET Framework namespaces.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ecca9-143">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ecca9-143">Related Sections</span></span>  
 [<span data-ttu-id="ecca9-144">Začínáme</span><span class="sxs-lookup"><span data-stu-id="ecca9-144">Getting Started</span></span>](./get-started/index.md)  
 <span data-ttu-id="ecca9-145">Poskytuje ucelený přehled o rozhraní .NET Framework a odkazy na další materiály.</span><span class="sxs-lookup"><span data-stu-id="ecca9-145">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
 [<span data-ttu-id="ecca9-146">Co je nového</span><span class="sxs-lookup"><span data-stu-id="ecca9-146">What's New</span></span>](./whats-new/index.md)  
 <span data-ttu-id="ecca9-147">Popisuje klíčové nové funkce a změny v nejnovější verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecca9-147">Describes key new features and changes in the latest version of the .NET Framework.</span></span> <span data-ttu-id="ecca9-148">Obsahuje seznam nových a zastaralých typů a členů a poskytuje návod pro migraci aplikací z předchozí verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecca9-148">Includes lists of new and obsolete types and members, and provides a guide for migrating your apps from the previous version of the .NET Framework.</span></span>  
  
 [<span data-ttu-id="ecca9-149">Nástroje</span><span class="sxs-lookup"><span data-stu-id="ecca9-149">Tools</span></span>](./tools/index.md)  
 <span data-ttu-id="ecca9-150">Popisuje nástroje, které vám pomůžou vyvíjet, konfigurovat a nasazovat aplikace pomocí technologií .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecca9-150">Describes the tools that help you develop, configure, and deploy apps by using .NET Framework technologies.</span></span>  
  
 [<span data-ttu-id="ecca9-151">Ukázky a kurzy .NET</span><span class="sxs-lookup"><span data-stu-id="ecca9-151">.NET samples and tutorials</span></span>](../samples-and-tutorials/index.md)  
 <span data-ttu-id="ecca9-152">Obsahuje odkazy na ukázky a kurzy, které vám pomůžou naučit se o .NET.</span><span class="sxs-lookup"><span data-stu-id="ecca9-152">Provides links to samples and tutorials that help you learn about .NET.</span></span>
