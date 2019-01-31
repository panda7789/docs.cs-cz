---
title: Jaký operační systém mají cílit kontejnery .NET
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Jaký operační systém mají cílit kontejnery .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: bef268a180584c47486a16960ca13fd63201fbe2
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479864"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="00e02-103">Jaký operační systém mají cílit kontejnery .NET</span><span class="sxs-lookup"><span data-stu-id="00e02-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="00e02-104">Zadaný spektrum operačních systémech podporovaných produktem rozdíly mezi rozhraní .NET Framework a .NET Core a Docker, by měl cíl konkrétní operační systém a konkrétní verze v závislosti na rozhraní, které používáte.</span><span class="sxs-lookup"><span data-stu-id="00e02-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="00e02-105">Pro Windows můžete použít Windows Server Core nebo Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="00e02-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="00e02-106">Tyto verze Windows poskytují různé vlastnosti (služba IIS v systému Windows Server Core a v místním prostředí webového serveru, jako Kestrel na Nano serveru), které může být potřeba pomocí rozhraní .NET Framework nebo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="00e02-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="00e02-107">Více distribuce pro Linux, jsou dostupné a podporované v oficiální Image .NET Dockeru (např. Debian).</span><span class="sxs-lookup"><span data-stu-id="00e02-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="00e02-108">Obrázek 3-1 se zobrazí možné verze operačního systému v závislosti na rozhraní .NET framework používá.</span><span class="sxs-lookup"><span data-stu-id="00e02-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![Při nasazování starších aplikací rozhraní .NET Framework, které máte na cílová jádra serveru systému Windows, kompatibilní s starší verze aplikace a služby IIS, má větší obrázek.](./media/image1.png)

<span data-ttu-id="00e02-113">**Obrázek 3-1.**</span><span class="sxs-lookup"><span data-stu-id="00e02-113">**Figure 3-1.**</span></span> <span data-ttu-id="00e02-114">Operační systémy pro cílení v závislosti na verzi rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="00e02-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="00e02-115">Můžete také vytvořit vlastní image Dockeru v případech, ve které chcete použít jiné distribuce Linuxu nebo místo bitovou kopii s verzemi, které neposkytuje Microsoft.</span><span class="sxs-lookup"><span data-stu-id="00e02-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="00e02-116">Například může vytvořit bitovou kopii s ASP.NET Core využívající tradiční rozhraní .NET Framework a Windows Server Core, který je not tak běžné scénáře pro Docker.</span><span class="sxs-lookup"><span data-stu-id="00e02-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="00e02-117">Když přidáte název bitové kopie do souboru Dockerfile, můžete vybrat operační systém a verze v závislosti na značku, kterou používáte, stejně jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="00e02-117">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="00e02-118">Image</span><span class="sxs-lookup"><span data-stu-id="00e02-118">Image</span></span></th>
<th><span data-ttu-id="00e02-119">Komentáře</span><span class="sxs-lookup"><span data-stu-id="00e02-119">Comments</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td><span data-ttu-id="00e02-120">Microsoft / dotnet:2.2 – modul runtime</span><span class="sxs-lookup"><span data-stu-id="00e02-120">microsoft/dotnet:2.2-runtime</span></span></td>
<td><span data-ttu-id="00e02-121">Více architektury .NET core 2.2: Podporuje Linux a Windows Nano serveru v závislosti na hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="00e02-121">.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="00e02-122">Microsoft / dotnet:2.2-aspnetcore-modulu runtime</span><span class="sxs-lookup"><span data-stu-id="00e02-122">microsoft/dotnet:2.2-aspnetcore-runtime</span></span></td>
<td><p><span data-ttu-id="00e02-123">Architektura ASP.NET Core 2.2 více: Podporuje Linux a Windows Nano serveru v závislosti na hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="00e02-123">ASP.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></p>
<p><span data-ttu-id="00e02-124">Aspnetcore image má několik optimalizací pro ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="00e02-124">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="00e02-125">Microsoft / dotnet:2.2-aspnetcore-runtime – alpine</span><span class="sxs-lookup"><span data-stu-id="00e02-125">microsoft/dotnet:2.2-aspnetcore-runtime-alpine</span></span></td>
<td><span data-ttu-id="00e02-126">.NET core 2.2 pouze modul runtime na Alpine distribuce Linuxu</span><span class="sxs-lookup"><span data-stu-id="00e02-126">.NET Core 2.2 runtime-only on Linux Alpine distro</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="00e02-127">microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="00e02-127">microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1803</span></span></td>
<td><span data-ttu-id="00e02-128">.NET core 2.2 pouze modul runtime Windows Nano Server (Windows Server verze 1803)</span><span class="sxs-lookup"><span data-stu-id="00e02-128">.NET Core 2.2 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
><span data-ttu-id="00e02-129">[Předchozí](container-framework-choice-factors.md)
>[další](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="00e02-129">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>