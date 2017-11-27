---
title: "Rozhraní .NET framework 4.7, 4.6 a 4.5"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
f1_keywords: f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 531da21d69f13a212eecb7b079fbf90bd7c8e681
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="net-framework-guide"></a><span data-ttu-id="bfed0-102">.NET framework – Průvodce</span><span class="sxs-lookup"><span data-stu-id="bfed0-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="bfed0-103">Tato sada obsahu rozhraní .NET Framework obsahuje informace o rozhraní .NET Framework verze 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 a 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="bfed0-103">This .NET Framework content set includes information for .NET Framework versions 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, and 4.7.1.</span></span> <span data-ttu-id="bfed0-104">Chcete-li stáhnout rozhraní .NET Framework, přečtěte si téma [instalace rozhraní .NET Framework](../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="bfed0-104">To download the .NET Framework, see [Installing the .NET Framework](../../docs/framework/install/guide-for-developers.md).</span></span> <span data-ttu-id="bfed0-105">Seznam nových funkcí a změn v rozhraní .NET Framework 4.5 [!INCLUDE[net_v46](../../includes/net-v46-md.md)], jejich verze bodu a 4.7 rozhraní .NET Framework a 4.7.1, najdete v části [co je nového v rozhraní .NET Framework](../../docs/framework/whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="bfed0-105">For a list of new features and changes in the NET Framework 4.5, the [!INCLUDE[net_v46](../../includes/net-v46-md.md)], their point releases, and the .NET Framework 4.7 and 4.7.1, see [What's New in the .NET Framework](../../docs/framework/whats-new/index.md).</span></span> <span data-ttu-id="bfed0-106">Seznam podporovaných platforem najdete v tématu [požadavky na systém rozhraní .NET Framework](../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfed0-106">For a list of supported platforms, see [.NET Framework System Requirements](../../docs/framework/get-started/system-requirements.md).</span></span> 

<span data-ttu-id="bfed0-107">Rozhraní .NET Framework je vývoj pro platformu pro sestavování aplikací pro web, Windows, Windows Phone, Windows Server a Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="bfed0-107">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="bfed0-108">Skládá se z common language runtime (CLR) a knihovně tříd rozhraní .NET Framework, která zahrnuje širokou škálu funkcí a podpora pro mnoho oborových standardů.</span><span class="sxs-lookup"><span data-stu-id="bfed0-108">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="bfed0-109">Rozhraní .NET Framework poskytuje mnoho služeb, včetně správy paměti, typ a paměť zabezpečení, zabezpečení, sítě a nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="bfed0-109">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="bfed0-110">Poskytuje snadno použitelnou datové struktury a rozhraní API, která abstraktní operační systém Windows nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="bfed0-110">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="bfed0-111">Můžete použít celou řadu programovacích jazyků s rozhraním .NET Framework, včetně C#, F # a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bfed0-111">You can use a variety of programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>  

<span data-ttu-id="bfed0-112">Obecný úvod do rozhraní .NET Framework pro uživatele a vývojáře, najdete v části [Začínáme](../../docs/framework/get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="bfed0-112">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](../../docs/framework/get-started/index.md).</span></span> <span data-ttu-id="bfed0-113">Úvod do architektury a klíčových funkcí rozhraní .NET Framework, najdete v článku [přehled](../../docs/framework/get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="bfed0-113">For an introduction to the architecture and key features of the .NET Framework, see the [overview](../../docs/framework/get-started/overview.md).</span></span>  

<span data-ttu-id="bfed0-114">Rozhraní .NET Framework lze použít s Docker a [Windows kontejnery](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).</span><span class="sxs-lookup"><span data-stu-id="bfed0-114">The .NET Framework can be used with Docker and with [Windows Containers](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).</span></span> <span data-ttu-id="bfed0-115">V tématu [nasazení .NET Framework – aplikace s Docker](./docker/index.md) se dozvíte, jak pro spuštění aplikací v nástroji Docker kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="bfed0-115">See [Deploying .NET Framework applications with Docker](./docker/index.md) to learn how to run your applications in Docker containers.</span></span>

## <a name="installation"></a><span data-ttu-id="bfed0-116">Instalace</span><span class="sxs-lookup"><span data-stu-id="bfed0-116">Installation</span></span>

<span data-ttu-id="bfed0-117">Rozhraní .NET Framework se dodává s Windows, které umožňují spouštět aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfed0-117">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="bfed0-118">Může být nutné novější verzi rozhraní .NET Framework, než se dodává s vaší verzí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bfed0-118">You may need a later version of the .NET Framework than comes with your Windows version.</span></span> <span data-ttu-id="bfed0-119">Další informace najdete v tématu [instalaci rozhraní .NET Framework v systému Windows](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="bfed0-119">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="bfed0-120">V tématu [opravit rozhraní .NET Framework](./install/repair.md) se dozvíte, jak k opravě instalace rozhraní .NET Framework, pokud při výskytu chyb při instalaci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfed0-120">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you are experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="bfed0-121">Podrobné informace o stažení rozhraní .NET Framework, najdete v části [instalaci rozhraní .NET Framework pro vývojáře](../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="bfed0-121">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](../../docs/framework/install/guide-for-developers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bfed0-122">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bfed0-122">In This Section</span></span>

[<span data-ttu-id="bfed0-123">Co je nového</span><span class="sxs-lookup"><span data-stu-id="bfed0-123">What's New</span></span>](../../docs/framework/whats-new/index.md)  
<span data-ttu-id="bfed0-124">Popisuje hlavní nové funkce a změny v nejnovějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfed0-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="bfed0-125">Obsahuje seznam zastaralých typů a členů a poskytuje návod pro migraci aplikací z předchozí verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfed0-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>  
  
[<span data-ttu-id="bfed0-126">Začínáme</span><span class="sxs-lookup"><span data-stu-id="bfed0-126">Getting Started</span></span>](../../docs/framework/get-started/index.md)  
<span data-ttu-id="bfed0-127">Poskytuje ucelený přehled o rozhraní .NET Framework a odkazy na další materiály.</span><span class="sxs-lookup"><span data-stu-id="bfed0-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
<span data-ttu-id="bfed0-128">[Příručka k migraci](../../docs/framework/migration-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bfed0-128">[Migration Guide](../../docs/framework/migration-guide/index.md) </span></span>  
<span data-ttu-id="bfed0-129">Poskytuje prostředky a seznam změn, které je potřeba zvážit, pokud se migrace vaší aplikace na novou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfed0-129">Provides resources and a list of changes you need to consider  if you're migrating your application to a new version of the .NET Framework.</span></span>  
  
[<span data-ttu-id="bfed0-130">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="bfed0-130">Development Guide</span></span>](../../docs/framework/development-guide.md)  
<span data-ttu-id="bfed0-131">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="bfed0-131">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
[<span data-ttu-id="bfed0-132">Nástroje</span><span class="sxs-lookup"><span data-stu-id="bfed0-132">Tools</span></span>](../../docs/framework/tools/index.md)  
<span data-ttu-id="bfed0-133">Popisuje nástroje, které pomáhají vyvíjet, konfigurovat a nasazovat aplikace s použitím technologií rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfed0-133">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>  
  
<span data-ttu-id="bfed0-134">[Knihovna tříd rozhraní .NET framework](/dotnet/api/?view=netframework-4.7.1) </span><span class="sxs-lookup"><span data-stu-id="bfed0-134">[.NET Framework Class Library](/dotnet/api/?view=netframework-4.7.1) </span></span>  
<span data-ttu-id="bfed0-135">Poskytuje syntaxi, ukázky kódu a související informace pro každou třídu obsaženou v oborech názvů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfed0-135">Supplies syntax, code examples, and related information for each class contained in the .NET Framework namespaces.</span></span>  
  
[<span data-ttu-id="bfed0-136">Rozhraní API a knihovny další – třída</span><span class="sxs-lookup"><span data-stu-id="bfed0-136">Additional Class Libraries and APIs</span></span>](../../docs/framework/additional-apis/index.md)  
<span data-ttu-id="bfed0-137">Poskytuje dokumentaci pro třídy, které jsou obsažené v out-of-band (OOB) verze, a také pro třídy, které cílí na specifické platformy nebo implementace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bfed0-137">Provides documentation for classes contained in out-of-band (OOB) releases, as well as for classes that target specific platforms or implementations of the .NET Framework.</span></span>
