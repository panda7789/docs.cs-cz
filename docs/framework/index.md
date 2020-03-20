---
title: Dokumentace rozhraní .NET Framework
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
ms.openlocfilehash: d94d97cd1b519025ff360dc903558ea3656818d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181537"
---
# <a name="net-framework-guide"></a><span data-ttu-id="6f920-102">Průvodce rozhraním .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f920-102">.NET Framework guide</span></span>

> [!NOTE]
> <span data-ttu-id="6f920-103">Tato sada obsahu rozhraní .NET Framework obsahuje informace pro rozhraní .NET Framework verze 4.5 až 4.8.</span><span class="sxs-lookup"><span data-stu-id="6f920-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="6f920-104">Chcete-li stáhnout rozhraní .NET Framework, [přečtěte si informace o instalaci rozhraní .NET Framework](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="6f920-104">To download .NET Framework, see [Install .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="6f920-105">Seznam nových funkcí a změn v rozhraní .NET Framework naleznete [v tématu What's New in .NET Framework](./whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="6f920-105">For a list of new features and changes in .NET Framework, see [What's New in .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="6f920-106">Seznam podporovaných platforem naleznete v tématu [.NET Framework System Requirements](./get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f920-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="6f920-107">Dokumentaci o starších verzích rozhraní .NET Framework naleznete v [dokumentaci k předchozím verzím .NET](https://docs.microsoft.com/previous-versions/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="6f920-107">For documentation about older versions of .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="6f920-108">Rozhraní .NET Framework je vývojová platforma pro vytváření aplikací pro web, Windows, Windows Server a Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="6f920-108">.NET Framework is a development platform for building apps for web, Windows, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="6f920-109">Skládá se z clr (COMMON Language runtime) a knihovny tříd rozhraní .NET Framework, která zahrnuje širokou škálu funkcí a podpory pro mnoho oborových standardů.</span><span class="sxs-lookup"><span data-stu-id="6f920-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="6f920-110">Rozhraní .NET Framework poskytuje mnoho služeb, včetně správy paměti, zabezpečení typů a paměti, zabezpečení, sítí a nasazení aplikací.</span><span class="sxs-lookup"><span data-stu-id="6f920-110">.NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="6f920-111">Poskytuje snadno použitelné datové struktury a api, které abstrahují operační systém Windows nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="6f920-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="6f920-112">S rozhraním .NET Framework můžete používat různé programovací jazyky, včetně c#, f# a visual basicu.</span><span class="sxs-lookup"><span data-stu-id="6f920-112">You can use different programming languages with .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="6f920-113">Obecný úvod do rozhraní .NET Framework pro uživatele i vývojáře naleznete v [tématu Začínáme](./get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="6f920-113">For a general introduction to .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="6f920-114">Úvod do architektury a klíčové funkce rozhraní .NET Framework naleznete v [přehledu](./get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="6f920-114">For an introduction to the architecture and key features of .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="6f920-115">Rozhraní .NET Framework lze použít s Dockerem a s [kontejnery windows](/virtualization/windowscontainers/about/).</span><span class="sxs-lookup"><span data-stu-id="6f920-115">.NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="installation"></a><span data-ttu-id="6f920-116">Instalace</span><span class="sxs-lookup"><span data-stu-id="6f920-116">Installation</span></span>

<span data-ttu-id="6f920-117">Rozhraní .NET Framework je dodáváno se systémem Windows, které umožňuje spouštět aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f920-117">.NET Framework comes with Windows, which enables you to run .NET Framework applications.</span></span> <span data-ttu-id="6f920-118">Možná budete potřebovat novější verzi rozhraní .NET Framework, než je ta, která je dodávána s verzí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6f920-118">You may need a later version of .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="6f920-119">Další informace naleznete [v tématu Install .NET Framework on Windows](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="6f920-119">For more information, see [Install .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="6f920-120">Informace o tom, jak opravit instalaci rozhraní .NET Framework, pokud během instalace dochází k chybám, naleznete v [tématu Oprava rozhraní .NET Framework](./install/repair.md).</span><span class="sxs-lookup"><span data-stu-id="6f920-120">To learn how to repair your .NET Framework installation if you're experiencing errors during installation, see [Repair .NET Framework](./install/repair.md).</span></span>

<span data-ttu-id="6f920-121">Podrobnější informace o stahování rozhraní .NET Framework naleznete [v tématu Instalace rozhraní .NET Framework pro vývojáře](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="6f920-121">For more detailed information on downloading .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6f920-122">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6f920-122">In this section</span></span>

* [<span data-ttu-id="6f920-123">Co je nového</span><span class="sxs-lookup"><span data-stu-id="6f920-123">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="6f920-124">Popisuje hlavní nové funkce a změny v nejnovějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f920-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="6f920-125">Obsahuje seznam zastaralých typů a členů a poskytuje návod pro migraci aplikací z předchozí verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f920-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="6f920-126">Začínáme</span><span class="sxs-lookup"><span data-stu-id="6f920-126">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="6f920-127">Poskytuje ucelený přehled o rozhraní .NET Framework a odkazy na další materiály.</span><span class="sxs-lookup"><span data-stu-id="6f920-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="6f920-128">Instalační příručka</span><span class="sxs-lookup"><span data-stu-id="6f920-128">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="6f920-129">Obsahuje zdroje informací o instalaci rozhraní .NET Framework a řešení potíží.</span><span class="sxs-lookup"><span data-stu-id="6f920-129">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="6f920-130">Průvodce migrací</span><span class="sxs-lookup"><span data-stu-id="6f920-130">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="6f920-131">Obsahuje prostředky a seznam změn, které je třeba zvážit, pokud migrujete aplikaci na novou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f920-131">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="6f920-132">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="6f920-132">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="6f920-133">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="6f920-133">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="6f920-134">Nástroje</span><span class="sxs-lookup"><span data-stu-id="6f920-134">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="6f920-135">Popisuje nástroje, které pomáhají vyvíjet, konfigurovat a nasazovat aplikace s použitím technologií rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f920-135">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="6f920-136">Další knihovny tříd a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6f920-136">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="6f920-137">Obsahuje dokumentaci pro privátní rozhraní API rozhraní .NET Framework používaná nástroji společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6f920-137">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f920-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f920-138">See also</span></span>

* [<span data-ttu-id="6f920-139">Knihovna tříd rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f920-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)
