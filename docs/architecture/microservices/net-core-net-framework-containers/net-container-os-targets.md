---
title: Operační systém, na který mají cílit kontejnery .NET
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Jaký operační systém pro cílení na kontejnery .NET
ms.date: 01/07/2019
ms.openlocfilehash: 6f160aeba5257722490788271e6f89359342cc0d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296509"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="5e862-103">Operační systém, na který mají cílit kontejnery .NET</span><span class="sxs-lookup"><span data-stu-id="5e862-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="5e862-104">Vzhledem k rozmanitosti operačních systémů, které podporuje Docker, a rozdílů mezi .NET Framework a .NET Core, byste měli cílit na konkrétní operační systém a konkrétní verze v závislosti na používaném rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5e862-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="5e862-105">Pro Windows můžete použít jádro Windows serveru nebo Windows nano Server.</span><span class="sxs-lookup"><span data-stu-id="5e862-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="5e862-106">Tyto verze systému Windows poskytují různé charakteristiky (IIS v jádru Windows serveru a webový server v místním prostředí, jako je Kestrel na nano serveru), které může být potřeba .NET Framework nebo .NET Core v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="5e862-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="5e862-107">Pro Linux je k dispozici několik distribuce a podporují se v oficiálních bitových kopiích .NET Docker (jako Debian).</span><span class="sxs-lookup"><span data-stu-id="5e862-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="5e862-108">Na obrázku 3-1 můžete zobrazit možnou verzi operačního systému v závislosti na použitém rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e862-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![Při nasazování starších aplikací .NET Framework, které je třeba cílit na jádro Windows serveru, je kompatibilní se staršími aplikacemi a službou IIS má větší obrázek.](./media/image1.png)

<span data-ttu-id="5e862-113">**Obrázek 3-1.**</span><span class="sxs-lookup"><span data-stu-id="5e862-113">**Figure 3-1.**</span></span> <span data-ttu-id="5e862-114">Operační systémy určené pro cílení v závislosti na verzích rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5e862-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="5e862-115">Můžete také vytvořit vlastní image Docker v případech, kdy chcete použít jiný distribuce pro Linux nebo kde chcete image s verzemi, které Microsoft neposkytuje.</span><span class="sxs-lookup"><span data-stu-id="5e862-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="5e862-116">Můžete například vytvořit bitovou kopii s ASP.NET Core spuštěnou v tradičním .NET Framework a jádro Windows serveru, což je neobvyklý scénář pro Docker.</span><span class="sxs-lookup"><span data-stu-id="5e862-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="5e862-117">Když přidáte název Image do souboru souboru Dockerfile, můžete vybrat operační systém a verzi v závislosti na používané značce, jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="5e862-117">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="5e862-118">Image</span><span class="sxs-lookup"><span data-stu-id="5e862-118">Image</span></span></th>
<th><span data-ttu-id="5e862-119">Komentáře</span><span class="sxs-lookup"><span data-stu-id="5e862-119">Comments</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td><span data-ttu-id="5e862-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span><span class="sxs-lookup"><span data-stu-id="5e862-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span></span></td>
<td><span data-ttu-id="5e862-121">.NET Core 2,2 s více architekturami: Podporuje systémy Linux a Windows nano Server v závislosti na hostiteli Docker.</span><span class="sxs-lookup"><span data-stu-id="5e862-121">.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="5e862-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span><span class="sxs-lookup"><span data-stu-id="5e862-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span></span></td>
<td><p><span data-ttu-id="5e862-123">ASP.NET Core 2,2 s více architekturami: Podporuje systémy Linux a Windows nano Server v závislosti na hostiteli Docker.</span><span class="sxs-lookup"><span data-stu-id="5e862-123">ASP.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></p>
<p><span data-ttu-id="5e862-124">Obrázek aspnetcore má několik optimalizací pro ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e862-124">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="5e862-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span><span class="sxs-lookup"><span data-stu-id="5e862-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span></span></td>
<td><span data-ttu-id="5e862-126">.NET Core 2,2 runtime – jenom pro Linux Alpine distribuce</span><span class="sxs-lookup"><span data-stu-id="5e862-126">.NET Core 2.2 runtime-only on Linux Alpine distro</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="5e862-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="5e862-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span></span></td>
<td><span data-ttu-id="5e862-128">.NET Core 2,2 runtime – jenom na Windows nano serveru (Windows Server verze 1803)</span><span class="sxs-lookup"><span data-stu-id="5e862-128">.NET Core 2.2 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span></td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> <span data-ttu-id="5e862-129">[Předchozí](container-framework-choice-factors.md)Další
> [](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="5e862-129">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
