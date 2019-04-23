---
title: Dokumentace rozhraní .NET framework
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
ms.openlocfilehash: b6e21d2514ad357c906885750d9320575bdb75b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976427"
---
# <a name="net-framework-guide"></a><span data-ttu-id="c0b42-102">Průvodce rozhraním .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c0b42-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="c0b42-103">Tato sada obsahu rozhraní .NET Framework obsahuje informace pro rozhraní .NET Framework verze 4.5 prostřednictvím 4.8.</span><span class="sxs-lookup"><span data-stu-id="c0b42-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="c0b42-104">Pokud chcete stáhnout rozhraní .NET Framework, naleznete v tématu [instalace rozhraní .NET Framework](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="c0b42-104">To download the .NET Framework, see [Installing the .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="c0b42-105">Seznam nových funkcí a změn v rozhraní .NET Framework najdete v tématu [co je nového v rozhraní .NET Framework](./whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="c0b42-105">For a list of new features and changes in the NET Framework, see [What's New in the .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="c0b42-106">Seznam podporovaných platforem najdete v tématu [rozhraní .NET Framework System Requirements](./get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0b42-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="c0b42-107">Dokumentaci ke službě starší verze rozhraní .NET Framework najdete v tématu [.NET dokumentace k předchozím verzím](https://docs.microsoft.com/previous-versions/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="c0b42-107">For documentation about older versions of the .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="c0b42-108">Rozhraní .NET Framework je Vývojová platforma pro vytváření aplikací pro web, Windows, Windows Phone, Windows Server a Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c0b42-108">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="c0b42-109">Zahrnuje common language runtime (CLR) a knihovny tříd rozhraní .NET Framework, která zahrnuje celou řadu funkcí a podporu pro mnoho oborových standardů.</span><span class="sxs-lookup"><span data-stu-id="c0b42-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="c0b42-110">Rozhraní .NET Framework poskytuje mnoho služeb, včetně správy paměti, bezpečnost typů a paměti, zabezpečení, sítě a nasazení aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0b42-110">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="c0b42-111">Poskytuje snadným ovládáním datových struktur a rozhraní API, která abstraktní operační systém Windows nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="c0b42-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="c0b42-112">Můžete použít různé programovací jazyky v rozhraní .NET Framework, včetně C#, F#a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c0b42-112">You can use different programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="c0b42-113">Obecný úvod k rozhraní .NET Framework pro uživatele a vývojáře naleznete v tématu [Začínáme](./get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="c0b42-113">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="c0b42-114">Úvod do architektury a klíčových funkcí rozhraní .NET Framework, najdete v článku [přehled](./get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="c0b42-114">For an introduction to the architecture and key features of the .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="c0b42-115">Rozhraní .NET Framework lze použít s Dockerem a s [kontejnery Windows](/virtualization/windowscontainers/about/).</span><span class="sxs-lookup"><span data-stu-id="c0b42-115">The .NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span> <span data-ttu-id="c0b42-116">Zobrazit [aplikace nasazení rozhraní .NET Framework pomocí Dockeru](./docker/index.md) se naučíte spouštět aplikace v kontejnerech Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c0b42-116">See [Deploying .NET Framework applications with Docker](./docker/index.md) to learn how to run your applications in Docker containers.</span></span>

## <a name="installation"></a><span data-ttu-id="c0b42-117">Instalace</span><span class="sxs-lookup"><span data-stu-id="c0b42-117">Installation</span></span>

<span data-ttu-id="c0b42-118">Rozhraní .NET Framework se dodává s Windows, takže umožňuje spouštět aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0b42-118">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="c0b42-119">Potřebujete novější verzi rozhraní .NET Framework než ten, který se dodává s vaší verzí Windows.</span><span class="sxs-lookup"><span data-stu-id="c0b42-119">You may need a later version of the .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="c0b42-120">Další informace najdete v tématu [nainstalovat rozhraní .NET Framework na Windows](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="c0b42-120">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="c0b42-121">Zobrazit [oprava rozhraní .NET Framework](./install/repair.md) se naučíte, opravte instalaci rozhraní .NET Framework, pokud dojde k chybám při instalaci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0b42-121">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you're experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="c0b42-122">Podrobné informace o stažení rozhraní .NET Framework, naleznete v tématu [nainstalovat rozhraní .NET Framework pro vývojáře](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="c0b42-122">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c0b42-123">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c0b42-123">In this section</span></span>

* [<span data-ttu-id="c0b42-124">Co je nového</span><span class="sxs-lookup"><span data-stu-id="c0b42-124">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="c0b42-125">Popisuje hlavní nové funkce a změny v nejnovějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0b42-125">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="c0b42-126">Obsahuje seznam zastaralých typů a členů a poskytuje návod pro migraci aplikací z předchozí verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0b42-126">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="c0b42-127">Začínáme</span><span class="sxs-lookup"><span data-stu-id="c0b42-127">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="c0b42-128">Poskytuje ucelený přehled o rozhraní .NET Framework a odkazy na další materiály.</span><span class="sxs-lookup"><span data-stu-id="c0b42-128">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="c0b42-129">Průvodce instalací</span><span class="sxs-lookup"><span data-stu-id="c0b42-129">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="c0b42-130">Poskytuje prostředky a pokyny k instalaci rozhraní .NET Framework a řešení potíží.</span><span class="sxs-lookup"><span data-stu-id="c0b42-130">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="c0b42-131">Průvodce migrací</span><span class="sxs-lookup"><span data-stu-id="c0b42-131">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="c0b42-132">Obsahuje seznam změn je potřeba zvážit, pokud migrujete na novou verzi rozhraní .NET Framework vaší aplikace a prostředky.</span><span class="sxs-lookup"><span data-stu-id="c0b42-132">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="c0b42-133">Průvodce rozhraním .NET Framework v Dockeru</span><span class="sxs-lookup"><span data-stu-id="c0b42-133">.NET Framework on Docker Guide</span></span>](./docker/index.md)  
<span data-ttu-id="c0b42-134">Poskytuje prostředky ke spouštění aplikací rozhraní .NET Framework pomocí Dockeru pomocí kontejnerů Windows.</span><span class="sxs-lookup"><span data-stu-id="c0b42-134">Provides resources to run .NET Framework applications with Docker, using Windows Containers.</span></span>

* [<span data-ttu-id="c0b42-135">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="c0b42-135">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="c0b42-136">Poskytuje postupy pro všechny klíčové oblasti technologie a úkoly pro vývoj aplikací včetně vytváření, konfigurace, ladění, zabezpečení a nasazení aplikace a informací o dynamickém programování, interoperabilitě, rozšiřitelnosti, správě paměti a podprocesech.</span><span class="sxs-lookup"><span data-stu-id="c0b42-136">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="c0b42-137">Nástroje</span><span class="sxs-lookup"><span data-stu-id="c0b42-137">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="c0b42-138">Popisuje nástroje, které pomáhají vyvíjet, konfigurovat a nasazovat aplikace s použitím technologií rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0b42-138">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="c0b42-139">Další knihovny tříd a rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c0b42-139">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="c0b42-140">Poskytuje dokumentaci pro privátní API rozhraní .NET Framework, používají nástroje pro Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c0b42-140">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0b42-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0b42-141">See also</span></span>

* [<span data-ttu-id="c0b42-142">Knihovna tříd rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="c0b42-142">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)