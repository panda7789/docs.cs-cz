---
title: "Jaké operačního systému k cíli s kontejnery rozhraní .NET"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Jaké operačního systému k cíli s kontejnery rozhraní .NET"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="372f5-104">Jaké operačního systému k cíli s kontejnery rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="372f5-104">What OS to target with .NET containers</span></span>

<span data-ttu-id="372f5-105">Zadané různorodost operační systémy podporované nástrojem Docker a rozdíly mezi rozhraní .NET Framework a .NET Core, by měl cílové konkrétní operační systém a konkrétní verze v závislosti na rozhraní framework, který používáte.</span><span class="sxs-lookup"><span data-stu-id="372f5-105">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="372f5-106">Pro systém Windows můžete použít Windows Server Core nebo Nano Server systému Windows.</span><span class="sxs-lookup"><span data-stu-id="372f5-106">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="372f5-107">Tyto verze systému Windows zadejte různými charakteristikami (služba IIS v systému Windows Server Core a vlastním hostováním webového serveru jako Kestrel v Nano Server), které mohou být potřebné rozhraní .NET Framework nebo .NET Core, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="372f5-107">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="372f5-108">Pro systémy Linux více distribucích jsou dostupné a podporované v oficiální imagí Dockeru .NET (například Debian).</span><span class="sxs-lookup"><span data-stu-id="372f5-108">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="372f5-109">Obrázek 3-1 se zobrazí možné verze operačního systému v závislosti na rozhraní .NET framework, který používá.</span><span class="sxs-lookup"><span data-stu-id="372f5-109">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="372f5-110">**Obrázek 3-1.**</span><span class="sxs-lookup"><span data-stu-id="372f5-110">**Figure 3-1.**</span></span> <span data-ttu-id="372f5-111">Operační systémy do cíle v závislosti na verze rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="372f5-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="372f5-112">Můžete také vytvořit vlastní image Docker v případech, kde chcete použít jiný distro Linux nebo místo bitovou kopii s verzemi není poskytovaný společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="372f5-112">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="372f5-113">Například může vytvořit bitovou kopii pomocí ASP.NET Core systémem tradiční rozhraní .NET Framework a Windows Server Core, což není tak běžné scénáře pro Docker.</span><span class="sxs-lookup"><span data-stu-id="372f5-113">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="372f5-114">Když přidáte název bitové kopie do souboru soubor Docker, můžete vybrat operační systém a verze v závislosti na značku, kterou používáte, jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="372f5-114">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="372f5-115">Microsoft /**dotnet:2.0.0-runtime-Klára**</span><span class="sxs-lookup"><span data-stu-id="372f5-115">microsoft/**dotnet:2.0.0-runtime-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

-   <span data-ttu-id="372f5-116">Microsoft /**dotnet:2.0.0-runtime-nanoserver-. 1709**</span><span class="sxs-lookup"><span data-stu-id="372f5-116">microsoft/**dotnet:2.0.0-runtime-nanoserver-1709**</span></span> 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   <span data-ttu-id="372f5-117">Microsoft /**aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="372f5-117">microsoft/**aspnetcore:2.0**</span></span>
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
<span data-ttu-id="372f5-118">[Předchozí] (kontejner framework – volba factors.md) [Další] (oficiální net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="372f5-118">[Previous] (container-framework-choice-factors.md) [Next] (official-net-docker-images.md)</span></span>
