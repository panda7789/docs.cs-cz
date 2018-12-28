---
title: Požadavky pro .NET Core v Linuxu
description: Podporované verze systému Linux a závislosti .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na počítačích s Linuxem.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 7a2b0b3af97500ab0988e5de7a44713a8c05ccb9
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656047"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="3b576-103">Požadavky pro .NET Core v Linuxu</span><span class="sxs-lookup"><span data-stu-id="3b576-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="3b576-104">Tento článek popisuje závislosti, které potřebujete pro vývoj aplikací .NET Core v Linuxu.</span><span class="sxs-lookup"><span data-stu-id="3b576-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="3b576-105">Podporované distribuce systému Linux/verze a závislosti, které následují platí na dva způsoby, jak vyvíjet aplikace .NET Core v Linuxu:</span><span class="sxs-lookup"><span data-stu-id="3b576-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="3b576-106">Pomocí oblíbeného editoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="3b576-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="3b576-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3b576-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="3b576-108">Balíček .NET Core SDK není potřeba pro produkční servery pro/prostředí.</span><span class="sxs-lookup"><span data-stu-id="3b576-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="3b576-109">Pro aplikace nasazené do produkčního prostředí se vyžaduje jenom balíček modulu runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b576-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="3b576-110">Modul runtime .NET Core je nasazený s aplikacemi jako součást samostatná nasazení, ale se musí nasadit pro závisí na architektuře nasazené aplikace samostatně.</span><span class="sxs-lookup"><span data-stu-id="3b576-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="3b576-111">Další informace o typech nasazení závisí na architektuře a samostatná najdete v tématu [nasazení aplikace .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b576-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="3b576-112">Viz také [Self-contained Linuxové aplikace](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) konkrétní pokyny.</span><span class="sxs-lookup"><span data-stu-id="3b576-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="3b576-113">Podporované verze Linuxu</span><span class="sxs-lookup"><span data-stu-id="3b576-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3b576-114">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="3b576-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="3b576-115">.NET core 2.x považuje Linux jako jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="3b576-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="3b576-116">Existuje jedno sestavení Linux (za architektura procesoru) podporované distribuce systému Linux.</span><span class="sxs-lookup"><span data-stu-id="3b576-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="3b576-117">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 2.2](https://www.microsoft.com/net/download/dotnet-core/2.2) nebo [soubory ke stažení rozhraní .NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="3b576-117">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="3b576-118">.NET core 2.x je podporovaný v následujících distribucích systému Linux/verzích:</span><span class="sxs-lookup"><span data-stu-id="3b576-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="3b576-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="3b576-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="3b576-120">CentOS 7 - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="3b576-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="3b576-121">Oracle Linux 7 - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="3b576-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="3b576-122">Fedora 28, 27 - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="3b576-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="3b576-123">Debian 9 (64-bit, `arm32`), 8.7 nebo novější verze - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="3b576-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="3b576-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="3b576-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="3b576-125">Linux Mint 18, 17 – 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="3b576-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="3b576-126">openSUSE 42.3 nebo novější verze - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="3b576-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="3b576-127">SUSE Enterprise Linux (SLES) 12 aktualizace Service Pack 2 nebo novější - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="3b576-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="3b576-128">Nástroj Alpine Linuxu 3.7 nebo novější verze - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="3b576-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="3b576-129">Zobrazit [podporované verze operačního systému .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) a [podporované verze operačního systému .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) úplný seznam .NET Core 2.1 a .NET Core 2.2 podporované operační systémy, distribuce a verze, z celkového počtu Podpora verze operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="3b576-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b576-130">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b576-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="3b576-131">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) nebo [.NET Core 1.0 stáhne](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="3b576-131">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="3b576-132">.NET core 1.x podporuje následující Linux 64-bit (`x86_64` nebo `amd64`) distribuce a verze:</span><span class="sxs-lookup"><span data-stu-id="3b576-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="3b576-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="3b576-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="3b576-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3b576-134">CentOS 7</span></span>
* <span data-ttu-id="3b576-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="3b576-135">Oracle Linux 7</span></span>
* <span data-ttu-id="3b576-136">Fedora 28 (.NET Core 1.1), z 27.</span><span class="sxs-lookup"><span data-stu-id="3b576-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="3b576-137">Debian 8.2 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="3b576-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="3b576-138">18.04 (.NET Core 1.1), Ubuntu 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="3b576-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="3b576-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="3b576-139">Linux Mint 17</span></span>
* <span data-ttu-id="3b576-140">openSUSE 42.3 nebo novější verze (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="3b576-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="3b576-141">Zobrazit [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, z verze podporu operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="3b576-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="3b576-142">.NET core 3.0 ve verzi Preview 1</span><span class="sxs-lookup"><span data-stu-id="3b576-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="3b576-143">.NET core 3.0 ve verzi Preview 1 považuje za jeden operační systém Linux.</span><span class="sxs-lookup"><span data-stu-id="3b576-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="3b576-144">Existuje jedno sestavení Linux (za architektura procesoru) podporované distribuce systému Linux.</span><span class="sxs-lookup"><span data-stu-id="3b576-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="3b576-145">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="3b576-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="3b576-146">.NET core 3.0 ve verzi Preview 1 se podporuje v následujících distribucích systému Linux/verzích.</span><span class="sxs-lookup"><span data-stu-id="3b576-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="3b576-147">Operační systém</span><span class="sxs-lookup"><span data-stu-id="3b576-147">OS</span></span>                            | <span data-ttu-id="3b576-148">Version</span><span class="sxs-lookup"><span data-stu-id="3b576-148">Version</span></span>               | <span data-ttu-id="3b576-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="3b576-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="3b576-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="3b576-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="3b576-151">6</span><span class="sxs-lookup"><span data-stu-id="3b576-151">6</span></span>                     | <span data-ttu-id="3b576-152">x64</span><span class="sxs-lookup"><span data-stu-id="3b576-152">x64</span></span>
<span data-ttu-id="3b576-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="3b576-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="3b576-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="3b576-154">CentOS</span></span><br><span data-ttu-id="3b576-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="3b576-155">Oracle Linux</span></span>  | <span data-ttu-id="3b576-156">7</span><span class="sxs-lookup"><span data-stu-id="3b576-156">7</span></span>                     | <span data-ttu-id="3b576-157">x64</span><span class="sxs-lookup"><span data-stu-id="3b576-157">x64</span></span>
<span data-ttu-id="3b576-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="3b576-158">Fedora</span></span>                        | <span data-ttu-id="3b576-159">28</span><span class="sxs-lookup"><span data-stu-id="3b576-159">28</span></span>                    | <span data-ttu-id="3b576-160">x64</span><span class="sxs-lookup"><span data-stu-id="3b576-160">x64</span></span>
<span data-ttu-id="3b576-161">Debian</span><span class="sxs-lookup"><span data-stu-id="3b576-161">Debian</span></span>                        | <span data-ttu-id="3b576-162">9</span><span class="sxs-lookup"><span data-stu-id="3b576-162">9</span></span>                     | <span data-ttu-id="3b576-163">x64 ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="3b576-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="3b576-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3b576-164">Ubuntu</span></span>                        | <span data-ttu-id="3b576-165">16.04 +, 18.04 +</span><span class="sxs-lookup"><span data-stu-id="3b576-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="3b576-166">x64 ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="3b576-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="3b576-167">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="3b576-167">Linux Mint</span></span>                    | <span data-ttu-id="3b576-168">18</span><span class="sxs-lookup"><span data-stu-id="3b576-168">18</span></span>                    | <span data-ttu-id="3b576-169">x64</span><span class="sxs-lookup"><span data-stu-id="3b576-169">x64</span></span>
<span data-ttu-id="3b576-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3b576-170">openSUSE</span></span>                      | <span data-ttu-id="3b576-171">42.3 +</span><span class="sxs-lookup"><span data-stu-id="3b576-171">42.3+</span></span>                 | <span data-ttu-id="3b576-172">x64</span><span class="sxs-lookup"><span data-stu-id="3b576-172">x64</span></span>
<span data-ttu-id="3b576-173">SUSE Linux Enterprise (SLES)</span><span class="sxs-lookup"><span data-stu-id="3b576-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="3b576-174">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="3b576-174">12 SP2+</span></span>               | <span data-ttu-id="3b576-175">x64</span><span class="sxs-lookup"><span data-stu-id="3b576-175">x64</span></span>
<span data-ttu-id="3b576-176">Nástroj Alpine Linuxu</span><span class="sxs-lookup"><span data-stu-id="3b576-176">Alpine Linux</span></span>                  | <span data-ttu-id="3b576-177">3.8 +</span><span class="sxs-lookup"><span data-stu-id="3b576-177">3.8+</span></span>                  | <span data-ttu-id="3b576-178">x64 ARM64</span><span class="sxs-lookup"><span data-stu-id="3b576-178">x64, ARM64</span></span>

<span data-ttu-id="3b576-179">\* Podpora ARM32 a ARM64 začíná Debian 9 a Ubuntu 16.04.</span><span class="sxs-lookup"><span data-stu-id="3b576-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="3b576-180">Starší verze těchto distribuce nejsou podporovány na čipech ARM.</span><span class="sxs-lookup"><span data-stu-id="3b576-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="3b576-181">Zobrazit [podporované verze operačního systému .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pro .NET Core 3.0 na úplný seznam podporovaných operačních systémů, distribuce a verze z verze podporu operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="3b576-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="3b576-182">Další informace o tom, jak nainstalovat .NET Core 3.0 na ARM64 najdete v tématu [instalace .NET Core 3.0 v systému Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="3b576-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>



---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="3b576-183">Závislosti distribuce Linuxu</span><span class="sxs-lookup"><span data-stu-id="3b576-183">Linux distribution dependencies</span></span>

<span data-ttu-id="3b576-184">Následující jsou určeny jako příklady.</span><span class="sxs-lookup"><span data-stu-id="3b576-184">The following are intended to be examples.</span></span> <span data-ttu-id="3b576-185">Přesné verze a názvy se mohou mírně lišit na vaší distribuci Linuxu podle výběru.</span><span class="sxs-lookup"><span data-stu-id="3b576-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="3b576-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3b576-186">Ubuntu</span></span>

<span data-ttu-id="3b576-187">Ubuntu distribuce vyžaduje nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="3b576-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="3b576-188">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="3b576-188">liblttng-ust0</span></span>
* <span data-ttu-id="3b576-189">libcurl3</span><span class="sxs-lookup"><span data-stu-id="3b576-189">libcurl3</span></span>
* <span data-ttu-id="3b576-190">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="3b576-190">libssl1.0.0</span></span>
* <span data-ttu-id="3b576-191">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="3b576-191">libkrb5-3</span></span>
* <span data-ttu-id="3b576-192">zlib1g</span><span class="sxs-lookup"><span data-stu-id="3b576-192">zlib1g</span></span>
* <span data-ttu-id="3b576-193">libicu52 (pro 14.x)</span><span class="sxs-lookup"><span data-stu-id="3b576-193">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="3b576-194">libicu55 (pro 16.x)</span><span class="sxs-lookup"><span data-stu-id="3b576-194">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="3b576-195">libicu57 (pro 17.x)</span><span class="sxs-lookup"><span data-stu-id="3b576-195">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="3b576-196">libicu60 (pro 18.x)</span><span class="sxs-lookup"><span data-stu-id="3b576-196">libicu60 (for 18.x)</span></span>

<span data-ttu-id="3b576-197">Pro verze starší než .NET Core 2.1 následující závislosti se rovněž vyžadují:</span><span class="sxs-lookup"><span data-stu-id="3b576-197">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="3b576-198">libunwind8</span><span class="sxs-lookup"><span data-stu-id="3b576-198">libunwind8</span></span>
* <span data-ttu-id="3b576-199">libuuid1</span><span class="sxs-lookup"><span data-stu-id="3b576-199">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="3b576-200">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="3b576-200">CentOS and Fedora</span></span>

<span data-ttu-id="3b576-201">CentOS distribuce vyžaduje nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="3b576-201">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="3b576-202">lttng tým ust</span><span class="sxs-lookup"><span data-stu-id="3b576-202">lttng-ust</span></span>
* <span data-ttu-id="3b576-203">libcurl</span><span class="sxs-lookup"><span data-stu-id="3b576-203">libcurl</span></span>
* <span data-ttu-id="3b576-204">knihovny OpenSSL</span><span class="sxs-lookup"><span data-stu-id="3b576-204">openssl-libs</span></span>
* <span data-ttu-id="3b576-205">krb5 knihovny</span><span class="sxs-lookup"><span data-stu-id="3b576-205">krb5-libs</span></span>
* <span data-ttu-id="3b576-206">libicu</span><span class="sxs-lookup"><span data-stu-id="3b576-206">libicu</span></span>
* <span data-ttu-id="3b576-207">zlib</span><span class="sxs-lookup"><span data-stu-id="3b576-207">zlib</span></span>

<span data-ttu-id="3b576-208">Uživatelé, fedora: Pokud vaše openssl verze > = 1.1, budete muset nainstalovat openssl10 kompatibility.</span><span class="sxs-lookup"><span data-stu-id="3b576-208">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="3b576-209">Pro verze starší než .NET Core 2.1 následující závislosti se rovněž vyžadují:</span><span class="sxs-lookup"><span data-stu-id="3b576-209">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="3b576-210">libunwind</span><span class="sxs-lookup"><span data-stu-id="3b576-210">libunwind</span></span>
* <span data-ttu-id="3b576-211">libuuid</span><span class="sxs-lookup"><span data-stu-id="3b576-211">libuuid</span></span>

<span data-ttu-id="3b576-212">Další informace o závislostech najdete v tématu [Self-contained Linuxové aplikace](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="3b576-212">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="3b576-213">Instalování závislostí pro .NET Core pomocí nativních instalačních programů</span><span class="sxs-lookup"><span data-stu-id="3b576-213">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="3b576-214">.NET core, které jsou k dispozici pro nativních instalačních programů podporované distribuce systému Linux/verze.</span><span class="sxs-lookup"><span data-stu-id="3b576-214">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="3b576-215">Nativních instalačních programů vyžadovat přístup správce (sudo) na server.</span><span class="sxs-lookup"><span data-stu-id="3b576-215">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="3b576-216">Výhodou použití nativní instalačního programu je, že jsou nainstalovány všechny závislosti nativní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b576-216">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="3b576-217">Nativních instalačních programů nainstalovat také systémová sada .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3b576-217">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="3b576-218">V Linuxu existují dvě možnosti balíček instalačního programu:</span><span class="sxs-lookup"><span data-stu-id="3b576-218">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="3b576-219">Pomocí Správce balíčků založená na informační kanál, třeba apt-get pro Ubuntu nebo yumu pro CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="3b576-219">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="3b576-220">Použití balíčků, sami, DEB nebo ot. / min.</span><span class="sxs-lookup"><span data-stu-id="3b576-220">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="3b576-221">Skriptování nainstaluje s skript instalačního programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="3b576-221">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="3b576-222">[Dotnet instalačních skriptů](./tools/dotnet-install-script.md) umožňují provést instalaci bez oprávnění správce. Sada nástrojů rozhraní příkazového řádku a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="3b576-222">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="3b576-223">Můžete stáhnout skript z [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).</span><span class="sxs-lookup"><span data-stu-id="3b576-223">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="3b576-224">Výchozí hodnoty skriptu k instalaci nejnovější verze "L", která je aktuálně .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="3b576-224">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="3b576-225">Pokud chcete nainstalovat rozhraní .NET Core 2.1, spusťte skript s přepínačem následující:</span><span class="sxs-lookup"><span data-stu-id="3b576-225">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="3b576-226">Skript bash instalačního programu se používá v scénáře automatizace a zařízení bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="3b576-226">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="3b576-227">Tento skript také přečte přepínače prostředí PowerShell, aby je bylo možné použít pomocí skriptu v systémech Linux nebo OS X.</span><span class="sxs-lookup"><span data-stu-id="3b576-227">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="3b576-228">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="3b576-228">Troubleshoot</span></span>

<span data-ttu-id="3b576-229">Pokud máte problémy s instalací rozhraní .NET Core na podporované distribuce systému Linux/version, najdete v následujících tématech nainstalovaných distribucí a verzí:</span><span class="sxs-lookup"><span data-stu-id="3b576-229">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="3b576-230">Známé problémy s .NET core 3.0</span><span class="sxs-lookup"><span data-stu-id="3b576-230">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="3b576-231">Známé problémy s .NET core 2.2</span><span class="sxs-lookup"><span data-stu-id="3b576-231">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="3b576-232">Známé problémy s .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="3b576-232">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="3b576-233">Známé problémy s .NET core 1.1</span><span class="sxs-lookup"><span data-stu-id="3b576-233">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="3b576-234">Známé problémy s .NET core 1.0</span><span class="sxs-lookup"><span data-stu-id="3b576-234">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
