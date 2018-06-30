---
title: Jaké operačního systému k cíli s kontejnery rozhraní .NET
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Jaké operačního systému k cíli s kontejnery rozhraní .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: fca5cf280d5abb85da78413a6eed463a2ffe6a88
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104876"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="42f57-103">Jaké operačního systému k cíli s kontejnery rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="42f57-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="42f57-104">Zadané různorodost operační systémy podporované nástrojem Docker a rozdíly mezi rozhraní .NET Framework a .NET Core, by měl cílové konkrétní operační systém a konkrétní verze v závislosti na rozhraní framework, který používáte.</span><span class="sxs-lookup"><span data-stu-id="42f57-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="42f57-105">Pro systém Windows můžete použít Windows Server Core nebo Nano Server systému Windows.</span><span class="sxs-lookup"><span data-stu-id="42f57-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="42f57-106">Tyto verze systému Windows zadejte různými charakteristikami (služba IIS v systému Windows Server Core a vlastním hostováním webového serveru jako Kestrel v Nano Server), které mohou být potřebné rozhraní .NET Framework nebo .NET Core, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="42f57-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="42f57-107">Pro systémy Linux více distribucích jsou dostupné a podporované v oficiální imagí Dockeru .NET (například Debian).</span><span class="sxs-lookup"><span data-stu-id="42f57-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="42f57-108">Obrázek 3-1 se zobrazí možné verze operačního systému v závislosti na rozhraní .NET framework, který používá.</span><span class="sxs-lookup"><span data-stu-id="42f57-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="42f57-109">**Obrázek 3-1.**</span><span class="sxs-lookup"><span data-stu-id="42f57-109">**Figure 3-1.**</span></span> <span data-ttu-id="42f57-110">Operační systémy do cíle v závislosti na verze rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="42f57-110">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="42f57-111">Můžete také vytvořit vlastní image Docker v případech, kde chcete použít jiný distro Linux nebo místo bitovou kopii s verzemi není poskytovaný společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="42f57-111">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="42f57-112">Například může vytvořit bitovou kopii pomocí ASP.NET Core systémem tradiční rozhraní .NET Framework a Windows Server Core, což není tak běžné scénáře pro Docker.</span><span class="sxs-lookup"><span data-stu-id="42f57-112">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="42f57-113">Když přidáte název bitové kopie do souboru soubor Docker, můžete vybrat operační systém a verze v závislosti na značku, kterou používáte, jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="42f57-113">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="42f57-114">Microsoft /**dotnet:2.1 – modul runtime**</span><span class="sxs-lookup"><span data-stu-id="42f57-114">microsoft/**dotnet:2.1-runtime**</span></span>

        .NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.

-   <span data-ttu-id="42f57-115">Microsoft /**dotnet:2.1-aspnetcore – modul runtime**</span><span class="sxs-lookup"><span data-stu-id="42f57-115">microsoft/**dotnet:2.1-aspnetcore-runtime**</span></span>
    
        ASP.NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 

-   <span data-ttu-id="42f57-116">Microsoft /**dotnet:2.1-aspnetcore-runtime-alpine**</span><span class="sxs-lookup"><span data-stu-id="42f57-116">microsoft/**dotnet:2.1-aspnetcore-runtime-alpine**</span></span> 

        .NET Core 2.1 runtime-only on Linux Alpine distro

-   <span data-ttu-id="42f57-117">Microsoft /**dotnet:2.1-aspnetcore-runtime-nanoserver-1803**</span><span class="sxs-lookup"><span data-stu-id="42f57-117">microsoft/**dotnet:2.1-aspnetcore-runtime-nanoserver-1803**</span></span> 

        .NET Core 2.1 runtime-only on Windows Nano Server (Windows Server version 1803)




>[!div class="step-by-step"]
<span data-ttu-id="42f57-118">[Předchozí](container-framework-choice-factors.md)
[další](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="42f57-118">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
