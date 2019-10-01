---
title: Dokumentace k .NET Framework
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5a86b3abf821a37944a0e478d0bc8f1bea31ccb
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699057"
---
# <a name="net-framework-guide"></a><span data-ttu-id="0f550-102">Průvodce rozhraním .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0f550-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="0f550-103">Tato .NET Framework sada obsahu obsahuje informace pro .NET Framework verze 4,5 až 4,8.</span><span class="sxs-lookup"><span data-stu-id="0f550-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="0f550-104">Pokud si chcete stáhnout .NET Framework, přečtěte si téma [instalace .NET Framework](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="0f550-104">To download the .NET Framework, see [Installing the .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="0f550-105">Seznam nových funkcí a změn v rozhraní .NET Framework najdete v tématu [co je nového v .NET Framework](./whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="0f550-105">For a list of new features and changes in the NET Framework, see [What's New in the .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="0f550-106">Seznam podporovaných platforem najdete v tématu [.NET Framework požadavky na systém](./get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f550-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="0f550-107">Dokumentaci k starším verzím .NET Framework najdete v [dokumentaci k předchozím verzím rozhraní .NET](https://docs.microsoft.com/previous-versions/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="0f550-107">For documentation about older versions of the .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="0f550-108">.NET Framework je vývojová platforma pro vytváření aplikací pro web, Windows, Windows Phone, Windows Server a Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="0f550-108">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="0f550-109">Skládá se z modulu CLR (Common Language Runtime) a knihovny tříd .NET Framework, která zahrnuje širokou škálu funkcí a podpory pro mnoho oborových standardů.</span><span class="sxs-lookup"><span data-stu-id="0f550-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="0f550-110">.NET Framework poskytuje mnoho služeb, včetně správy paměti, zabezpečení typu a paměti, zabezpečení, sítě a nasazení aplikací.</span><span class="sxs-lookup"><span data-stu-id="0f550-110">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="0f550-111">Nabízí snadno použitelné datové struktury a rozhraní API, které obsahují abstraktní operační systém Windows na nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="0f550-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="0f550-112">Můžete použít různé programovací jazyky s .NET Framework, včetně C#, F#a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0f550-112">You can use different programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="0f550-113">Obecný úvod k .NET Framework pro uživatele a vývojáře naleznete v tématu [Začínáme](./get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="0f550-113">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="0f550-114">Úvod k architektuře a klíčovým funkcím .NET Framework najdete v [přehledu](./get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="0f550-114">For an introduction to the architecture and key features of the .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="0f550-115">.NET Framework lze použít s Docker a [kontejnery Windows](/virtualization/windowscontainers/about/).</span><span class="sxs-lookup"><span data-stu-id="0f550-115">The .NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="installation"></a><span data-ttu-id="0f550-116">Instalace</span><span class="sxs-lookup"><span data-stu-id="0f550-116">Installation</span></span>

<span data-ttu-id="0f550-117">.NET Framework se dodává se systémem Windows, což vám umožní spouštět aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f550-117">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="0f550-118">Možná budete potřebovat novější verzi .NET Framework než ta, která se dodává s vaší verzí Windows.</span><span class="sxs-lookup"><span data-stu-id="0f550-118">You may need a later version of the .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="0f550-119">Další informace najdete v tématu [instalace .NET Framework ve Windows](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="0f550-119">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="0f550-120">Pokud při instalaci .NET Framework dochází k chybám, přečtěte si téma věnované [opravě .NET Framework](./install/repair.md) , kde se dozvíte, jak opravit .NET Framework instalaci.</span><span class="sxs-lookup"><span data-stu-id="0f550-120">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you're experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="0f550-121">Podrobnější informace o stažení .NET Framework najdete v tématu [instalace .NET Framework pro vývojáře](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="0f550-121">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0f550-122">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0f550-122">In this section</span></span>

* [<span data-ttu-id="0f550-123">Co je nového</span><span class="sxs-lookup"><span data-stu-id="0f550-123">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="0f550-124">Popisuje hlavní nové funkce a změny v nejnovějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f550-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="0f550-125">Obsahuje seznam zastaralých typů a členů a poskytuje návod pro migraci aplikací z předchozí verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f550-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="0f550-126">Začínáme</span><span class="sxs-lookup"><span data-stu-id="0f550-126">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="0f550-127">Poskytuje ucelený přehled o rozhraní .NET Framework a odkazy na další materiály.</span><span class="sxs-lookup"><span data-stu-id="0f550-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="0f550-128">Průvodce instalací</span><span class="sxs-lookup"><span data-stu-id="0f550-128">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="0f550-129">Poskytuje prostředky a pokyny týkající se .NET Framework instalace a řešení potíží.</span><span class="sxs-lookup"><span data-stu-id="0f550-129">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="0f550-130">Průvodce migrací</span><span class="sxs-lookup"><span data-stu-id="0f550-130">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="0f550-131">Poskytuje prostředky a seznam změn, které je třeba vzít v úvahu, pokud migrujete aplikaci na novou verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f550-131">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="0f550-132">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="0f550-132">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="0f550-133">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="0f550-133">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="0f550-134">Nástroje</span><span class="sxs-lookup"><span data-stu-id="0f550-134">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="0f550-135">Popisuje nástroje, které pomáhají vyvíjet, konfigurovat a nasazovat aplikace s použitím technologií rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f550-135">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="0f550-136">Další knihovny tříd a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0f550-136">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="0f550-137">Poskytuje dokumentaci pro soukromá .NET Framework rozhraní API používaná nástroji Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="0f550-137">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f550-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f550-138">See also</span></span>

- [<span data-ttu-id="0f550-139">Knihovna tříd .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0f550-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)
