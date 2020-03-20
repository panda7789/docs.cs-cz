---
title: Průvodce vývojem s použitím rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
ms.openlocfilehash: 0500e11d2897cfa7392cc8280a0b69c5e2fc515f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79181623"
---
# <a name="net-framework-development-guide"></a><span data-ttu-id="b17b4-102">Průvodce vývojem s použitím rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b17b4-102">.NET Framework Development Guide</span></span>
<span data-ttu-id="b17b4-103">Tato část vysvětluje, jak vytvořit, nakonfigurovat, ladit, zabezpečit a nasadit aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b17b4-103">This section explains how to create, configure, debug, secure, and deploy your .NET Framework apps.</span></span> <span data-ttu-id="b17b4-104">Část také poskytuje informace o technologických oblastech, jako je dynamické programování, interoperabilita, rozšiřitelnost, správa paměti a threading.</span><span class="sxs-lookup"><span data-stu-id="b17b4-104">The section also provides information about technology areas such as dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b17b4-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b17b4-105">In This Section</span></span>  
 [<span data-ttu-id="b17b4-106">Základy vytváření aplikací</span><span class="sxs-lookup"><span data-stu-id="b17b4-106">Application Essentials</span></span>](../standard/application-essentials.md)  
 <span data-ttu-id="b17b4-107">Obsahuje informace o základních úlohách vývoje aplikací, jako je programování s doménami a sestaveními aplikací, použití atributů, formátování a analýzy základních typů, použití kolekcí, zpracování událostí a výjimek, používání souborů a datových proudů a používání datových proudů a používání Generik.</span><span class="sxs-lookup"><span data-stu-id="b17b4-107">Provides information about basic app development tasks, such as programming with app domains and assemblies, using attributes, formatting and parsing base types, using collections, handling events and exceptions, using files and data streams, and using generics.</span></span>  
  
 [<span data-ttu-id="b17b4-108">Data a modelování</span><span class="sxs-lookup"><span data-stu-id="b17b4-108">Data and Modeling</span></span>](./data/index.md)  
 <span data-ttu-id="b17b4-109">Obsahuje informace o tom, jak přistupovat k datům pomocí ADO.NET, jazykově integrovaný dotaz (LINQ), WCF Data Services a XML.</span><span class="sxs-lookup"><span data-stu-id="b17b4-109">Provides information about how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
 [<span data-ttu-id="b17b4-110">Klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="b17b4-110">Client Applications</span></span>](develop-client-apps.md)  
 <span data-ttu-id="b17b4-111">Vysvětluje, jak vytvářet aplikace založené na Windows pomocí Windows Presentation Foundation (WPF) nebo Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b17b4-111">Explains how to create Windows-based apps by using Windows Presentation Foundation (WPF) or Windows Forms.</span></span>  
  
 [<span data-ttu-id="b17b4-112">Webové aplikace s ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b17b4-112">Web Applications with ASP.NET</span></span>](develop-web-apps-with-aspnet.md)  
 <span data-ttu-id="b17b4-113">Obsahuje odkazy na informace o používání ASP.NET k vytváření webových aplikací podnikové třídy s minimem kódování.</span><span class="sxs-lookup"><span data-stu-id="b17b4-113">Provides links to information about using ASP.NET to build enterprise-class web apps with a minimum of coding.</span></span>  
  
 [<span data-ttu-id="b17b4-114">Aplikace orientované na služby s použitím technologie WCF</span><span class="sxs-lookup"><span data-stu-id="b17b4-114">Service-Oriented Applications with WCF</span></span>](./wcf/index.md)  
 <span data-ttu-id="b17b4-115">Popisuje, jak používat Windows Communication Foundation (WCF) k vytváření aplikací orientovaných na služby, které jsou zabezpečené a spolehlivé.</span><span class="sxs-lookup"><span data-stu-id="b17b4-115">Describes how to use Windows Communication Foundation (WCF) to build service-oriented apps that are secure and reliable.</span></span>  
  
 <span data-ttu-id="b17b4-116">[Vytváření pracovních postupů pomocí nadace Windows Workflow Foundation](windows-workflow-foundation/index.md) Obsahuje informace o programovacím modelu, ukázkách a nástrojích pro použití služby Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="b17b4-116">[Building workflows with Windows Workflow Foundation](windows-workflow-foundation/index.md) Provides information about the programming model, samples, and tools for using Windows Workflow Foundation (WF).</span></span>  

 [<span data-ttu-id="b17b4-117">Aplikace spouštěné jako služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="b17b4-117">Windows Service Applications</span></span>](./windows-services/index.md)  
 <span data-ttu-id="b17b4-118">Vysvětluje, jak můžete pomocí sady Visual Studio a rozhraní .NET Framework vytvořit aplikaci, která je nainstalována jako služba, a spustit, zastavit a jinak řídit její chování.</span><span class="sxs-lookup"><span data-stu-id="b17b4-118">Explains how you can use Visual Studio and the .NET Framework to create an app that is installed as a service, and start, stop, and otherwise control its behavior.</span></span>  
  
 [<span data-ttu-id="b17b4-119">Paralelní zpracování, souběžnost a asynchronní programování v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="b17b4-119">Parallel Processing, Concurrency, and Async Programming in .NET</span></span>](../standard/parallel-processing-and-concurrency.md)  
 <span data-ttu-id="b17b4-120">Obsahuje informace o spravovaném podprocesu, paralelním programování a vzorcích návrhu asynchronního programování.</span><span class="sxs-lookup"><span data-stu-id="b17b4-120">Provides information about managed threading, parallel programming, and asynchronous programming design patterns.</span></span>  
  
 [<span data-ttu-id="b17b4-121">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b17b4-121">Network Programming in the .NET Framework</span></span>](./network-programming/index.md)  
 <span data-ttu-id="b17b4-122">Popisuje vrstvenou, rozšiřitelnou a spravovanou implementaci internetových služeb, kterou můžete rychle a snadno integrovat do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="b17b4-122">Describes the layered, extensible, and managed implementation of Internet services that you can quickly and easily integrate into your apps.</span></span>  
  
 <span data-ttu-id="b17b4-123">[Konfigurace aplikací rozhraní .NET Framework](configure-apps/index.md) Vysvětluje, jak můžete pomocí konfiguračních souborů změnit nastavení, aniž byste museli znovu kompilovat aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b17b4-123">[Configuring .NET Framework Apps](configure-apps/index.md) Explains how you can use configuration files to change settings without having to recompile your .NET Framework apps.</span></span>  
  
 [<span data-ttu-id="b17b4-124">Kompilování aplikací pomocí .NET Native</span><span class="sxs-lookup"><span data-stu-id="b17b4-124">Compiling Apps with .NET Native</span></span>](./net-native/index.md)  
 <span data-ttu-id="b17b4-125">Vysvětluje, jak můžete použít nativní předkompilaci .NET k vytváření a nasazování aplikací pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="b17b4-125">Explains how you can use the .NET Native precompilation technology to build and deploy Windows Store apps.</span></span> <span data-ttu-id="b17b4-126">.NET Native zkompiluje aplikace, které jsou zapsány ve spravovaném kódu (C#) a které cílí na rozhraní .NET Framework na nativní kód.</span><span class="sxs-lookup"><span data-stu-id="b17b4-126">.NET Native compiles apps that are written in managed code (C#) and that target the .NET Framework to native code.</span></span>  
  
 [<span data-ttu-id="b17b4-127">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b17b4-127">Security</span></span>](../standard/security/index.md)  
 <span data-ttu-id="b17b4-128">Obsahuje informace o třídách a službách v rozhraní .NET Framework, které usnadňují bezpečný vývoj aplikací.</span><span class="sxs-lookup"><span data-stu-id="b17b4-128">Provides information about the classes and services in the .NET Framework that facilitate secure app development.</span></span>  
  
 [<span data-ttu-id="b17b4-129">Ladění, trasování a profilace</span><span class="sxs-lookup"><span data-stu-id="b17b4-129">Debugging, Tracing, and Profiling</span></span>](./debug-trace-profile/index.md)  
 <span data-ttu-id="b17b4-130">Vysvětluje, jak testovat, optimalizovat a profilovat aplikace rozhraní .NET Framework a prostředí aplikace.</span><span class="sxs-lookup"><span data-stu-id="b17b4-130">Explains how to test, optimize, and profile .NET Framework apps and the app environment.</span></span> <span data-ttu-id="b17b4-131">Tato část obsahuje informace pro správce i vývojáře.</span><span class="sxs-lookup"><span data-stu-id="b17b4-131">This section includes information for administrators as well as developers.</span></span>  
  
 [<span data-ttu-id="b17b4-132">Vývoj pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="b17b4-132">Developing for Multiple Platforms</span></span>](../standard/cross-platform/index.md)  
 <span data-ttu-id="b17b4-133">Obsahuje informace o tom, jak můžete pomocí rozhraní .NET Framework vytvářet sestavení, která lze sdílet na více platformách a na více zařízeních, jako jsou telefony, stolní počítače a web.</span><span class="sxs-lookup"><span data-stu-id="b17b4-133">Provides information about how you can use the .NET Framework to build assemblies that can be shared across multiple platforms and multiple devices such as phones, desktop, and web.</span></span>  
  
 [<span data-ttu-id="b17b4-134">Nasazení</span><span class="sxs-lookup"><span data-stu-id="b17b4-134">Deployment</span></span>](./deployment/index.md)  
 <span data-ttu-id="b17b4-135">Vysvětluje, jak zabalit a distribuovat aplikaci rozhraní .NET Framework a obsahuje průvodce nasazením pro vývojáře i správce.</span><span class="sxs-lookup"><span data-stu-id="b17b4-135">Explains how to package and distribute your .NET Framework app, and includes deployment guides for both developers and administrators.</span></span>  
  
 [<span data-ttu-id="b17b4-136">Výkon</span><span class="sxs-lookup"><span data-stu-id="b17b4-136">Performance</span></span>](./performance/index.md)  
 <span data-ttu-id="b17b4-137">Obsahuje informace o ukládání do mezipaměti, opožděné inicializaci, spolehlivosti a událostech ETW.</span><span class="sxs-lookup"><span data-stu-id="b17b4-137">Provides information about caching, lazy initialization, reliability, and ETW events.</span></span>  

## <a name="reference"></a><span data-ttu-id="b17b4-138">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="b17b4-138">Reference</span></span>  
 [<span data-ttu-id="b17b4-139">Knihovna tříd rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b17b4-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.7)  
 <span data-ttu-id="b17b4-140">Poskytuje syntaxi, příklady kódu a informace o použití pro každou třídu, která je obsažena v oborech názvů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b17b4-140">Supplies syntax, code examples, and usage information for each class that is contained in the .NET Framework namespaces.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b17b4-141">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b17b4-141">Related Sections</span></span>  
 [<span data-ttu-id="b17b4-142">Začínáme</span><span class="sxs-lookup"><span data-stu-id="b17b4-142">Getting Started</span></span>](./get-started/index.md)  
 <span data-ttu-id="b17b4-143">Poskytuje ucelený přehled o rozhraní .NET Framework a odkazy na další materiály.</span><span class="sxs-lookup"><span data-stu-id="b17b4-143">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
 [<span data-ttu-id="b17b4-144">Co je nového</span><span class="sxs-lookup"><span data-stu-id="b17b4-144">What's New</span></span>](./whats-new/index.md)  
 <span data-ttu-id="b17b4-145">Popisuje klíčové nové funkce a změny v nejnovější verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b17b4-145">Describes key new features and changes in the latest version of the .NET Framework.</span></span> <span data-ttu-id="b17b4-146">Obsahuje seznamy nových a zastaralých typů a členů a poskytuje průvodce pro migraci aplikací z předchozí verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b17b4-146">Includes lists of new and obsolete types and members, and provides a guide for migrating your apps from the previous version of the .NET Framework.</span></span>  
  
 [<span data-ttu-id="b17b4-147">Nástroje</span><span class="sxs-lookup"><span data-stu-id="b17b4-147">Tools</span></span>](./tools/index.md)  
 <span data-ttu-id="b17b4-148">Popisuje nástroje, které vám pomohou vyvíjet, konfigurovat a nasazovat aplikace pomocí technologií rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b17b4-148">Describes the tools that help you develop, configure, and deploy apps by using .NET Framework technologies.</span></span>  
  
 [<span data-ttu-id="b17b4-149">Ukázky a výukové programy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="b17b4-149">.NET samples and tutorials</span></span>](../samples-and-tutorials/index.md)  
 <span data-ttu-id="b17b4-150">Obsahuje odkazy na ukázky a kurzy, které vám pomohou získat informace o rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="b17b4-150">Provides links to samples and tutorials that help you learn about .NET.</span></span>
