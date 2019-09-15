---
title: Předpoklady pro .NET Core v systému Linux
description: Podporované verze systému Linux a závislosti rozhraní .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na počítačích se systémem Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 5fcf931572f3c7e9b9857d2e91e9d620c7aad0bd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969871"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="535b9-103">Předpoklady pro .NET Core v systému Linux</span><span class="sxs-lookup"><span data-stu-id="535b9-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="535b9-104">Tento článek ukazuje závislosti potřebné pro vývoj aplikací .NET Core v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="535b9-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="535b9-105">Podporované distribuce a verze systému Linux a závislosti, které následují, se vztahují na dva způsoby vývoje aplikací .NET Core v systému Linux:</span><span class="sxs-lookup"><span data-stu-id="535b9-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="535b9-106">Příkazový řádek s oblíbeným editorem</span><span class="sxs-lookup"><span data-stu-id="535b9-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="535b9-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="535b9-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="535b9-108">Pro produkční servery a prostředí se .NET Core SDK balíček nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="535b9-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="535b9-109">Pro aplikace nasazené do produkčního prostředí je potřeba jenom balíček runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="535b9-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="535b9-110">Modul runtime .NET Core je nasazen s aplikacemi jako součást samostatného nasazení, ale musí být nasazen pro samostatně nasazené aplikace závislé na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="535b9-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="535b9-111">Další informace o typech nasazení závislých na rozhraní a samostatně obsažených typů naleznete v tématu [nasazení aplikace .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="535b9-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="535b9-112">Konkrétní pokyny najdete také v části [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="535b9-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="535b9-113">Podporované verze systému Linux</span><span class="sxs-lookup"><span data-stu-id="535b9-113">Supported Linux versions</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="535b9-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="535b9-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="535b9-115">.NET Core 2. x považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="535b9-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="535b9-116">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="535b9-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="535b9-117">Odkazy ke stažení a další informace najdete v tématu soubory ke stažení pro [.NET core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) nebo soubory ke stažení pro [.NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="535b9-117">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="535b9-118">Rozhraní .NET Core 2. x je podporováno v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="535b9-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="535b9-119">Red Hat Enterprise Linux 7, 6-64 – bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="535b9-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="535b9-120">CentOS 7-64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="535b9-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="535b9-121">Oracle Linux 7-64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="535b9-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="535b9-122">Fedora 28, 27-64 – bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="535b9-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="535b9-123">Debian 9 (64-bit, `arm32`), 8,7 nebo novější verze-64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="535b9-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="535b9-124">Ubuntu 18,04 (64-bit, `arm32`), 16,04, 14,04-64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="535b9-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="535b9-125">Linux mentolová 18, 17-64 – bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="535b9-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="535b9-126">openSUSE 42,3 nebo novější verze – 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="535b9-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="535b9-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 nebo novější-64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="535b9-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="535b9-128">Alpine Linux 3,7 nebo novější verze – 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="535b9-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="535b9-129">Úplný seznam operačních systémů .NET Core 2,1 2,2 a .NET Core 2,2 s podporovanými operačními systémy, distribuce a verze, nepodporované verze operačního systému a zásady životního cyklu najdete v článku podporované verze operačního systému .NET [core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) a .net Core [](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) . odkazy.</span><span class="sxs-lookup"><span data-stu-id="535b9-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="535b9-130">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="535b9-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="535b9-131">Odkazy ke stažení a další informace najdete v tématu soubory ke stažení pro [.NET core 1,1](https://dotnet.microsoft.com/download/dotnet-core/1.1) nebo soubory ke stažení pro [.NET Core 1,0](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="535b9-131">For download links and more information, see [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="535b9-132">Rozhraní .NET Core 1. x je podporováno v následujících distribucích a verzích systému`x86_64` Linux `amd64`64-bit:</span><span class="sxs-lookup"><span data-stu-id="535b9-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="535b9-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="535b9-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="535b9-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="535b9-134">CentOS 7</span></span>
* <span data-ttu-id="535b9-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="535b9-135">Oracle Linux 7</span></span>
* <span data-ttu-id="535b9-136">Fedora 28 (.NET Core 1,1), 27</span><span class="sxs-lookup"><span data-stu-id="535b9-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="535b9-137">Debian 8,2 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="535b9-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="535b9-138">Ubuntu 18,04 (.NET Core 1,1), 16,04, 14,04</span><span class="sxs-lookup"><span data-stu-id="535b9-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="535b9-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="535b9-139">Linux Mint 17</span></span>
* <span data-ttu-id="535b9-140">openSUSE 42,3 nebo novější verze (.NET Core 1,1)</span><span class="sxs-lookup"><span data-stu-id="535b9-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="535b9-141">Úplný seznam podporovaných operačních systémů pro .NET Core 1. x najdete v článku podporované verze operačního systému s podporou rozhraní .NET [Core](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) 1. x, verze operačních systémů a odkazy na zásady životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="535b9-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="535b9-142">.NET Core 3,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="535b9-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="535b9-143">.NET Core 3,0 Preview 1 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="535b9-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="535b9-144">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="535b9-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="535b9-145">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="535b9-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="535b9-146">Verze .NET Core 3,0 Preview 1 je podporována v následujících distribucích a verzích systému Linux.</span><span class="sxs-lookup"><span data-stu-id="535b9-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="535b9-147">OS</span><span class="sxs-lookup"><span data-stu-id="535b9-147">OS</span></span>                            | <span data-ttu-id="535b9-148">Version</span><span class="sxs-lookup"><span data-stu-id="535b9-148">Version</span></span>               | <span data-ttu-id="535b9-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="535b9-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="535b9-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="535b9-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="535b9-151">6</span><span class="sxs-lookup"><span data-stu-id="535b9-151">6</span></span>                     | <span data-ttu-id="535b9-152">x64</span><span class="sxs-lookup"><span data-stu-id="535b9-152">x64</span></span>
<span data-ttu-id="535b9-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="535b9-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="535b9-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="535b9-154">CentOS</span></span><br><span data-ttu-id="535b9-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="535b9-155">Oracle Linux</span></span>  | <span data-ttu-id="535b9-156">7</span><span class="sxs-lookup"><span data-stu-id="535b9-156">7</span></span>                     | <span data-ttu-id="535b9-157">x64</span><span class="sxs-lookup"><span data-stu-id="535b9-157">x64</span></span>
<span data-ttu-id="535b9-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="535b9-158">Fedora</span></span>                        | <span data-ttu-id="535b9-159">28</span><span class="sxs-lookup"><span data-stu-id="535b9-159">28</span></span>                    | <span data-ttu-id="535b9-160">x64</span><span class="sxs-lookup"><span data-stu-id="535b9-160">x64</span></span>
<span data-ttu-id="535b9-161">Debian</span><span class="sxs-lookup"><span data-stu-id="535b9-161">Debian</span></span>                        | <span data-ttu-id="535b9-162">9</span><span class="sxs-lookup"><span data-stu-id="535b9-162">9</span></span>                     | <span data-ttu-id="535b9-163">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="535b9-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="535b9-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="535b9-164">Ubuntu</span></span>                        | <span data-ttu-id="535b9-165">16.04+, 18.04+</span><span class="sxs-lookup"><span data-stu-id="535b9-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="535b9-166">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="535b9-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="535b9-167">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="535b9-167">Linux Mint</span></span>                    | <span data-ttu-id="535b9-168">18</span><span class="sxs-lookup"><span data-stu-id="535b9-168">18</span></span>                    | <span data-ttu-id="535b9-169">x64</span><span class="sxs-lookup"><span data-stu-id="535b9-169">x64</span></span>
<span data-ttu-id="535b9-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="535b9-170">openSUSE</span></span>                      | <span data-ttu-id="535b9-171">42.3 +</span><span class="sxs-lookup"><span data-stu-id="535b9-171">42.3+</span></span>                 | <span data-ttu-id="535b9-172">x64</span><span class="sxs-lookup"><span data-stu-id="535b9-172">x64</span></span>
<span data-ttu-id="535b9-173">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="535b9-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="535b9-174">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="535b9-174">12 SP2+</span></span>               | <span data-ttu-id="535b9-175">x64</span><span class="sxs-lookup"><span data-stu-id="535b9-175">x64</span></span>
<span data-ttu-id="535b9-176">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="535b9-176">Alpine Linux</span></span>                  | <span data-ttu-id="535b9-177">3.8 +</span><span class="sxs-lookup"><span data-stu-id="535b9-177">3.8+</span></span>                  | <span data-ttu-id="535b9-178">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="535b9-178">x64, ARM64</span></span>

<span data-ttu-id="535b9-179">\*Podpora ARM32 a ARM64 začíná na Debian 9 a Ubuntu 16,04.</span><span class="sxs-lookup"><span data-stu-id="535b9-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="535b9-180">V čipy ARM nejsou starší verze těchto distribuce podporovány.</span><span class="sxs-lookup"><span data-stu-id="535b9-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="535b9-181">Úplný 3,0 seznam podporovaných operačních systémů, distribucí a verzí operačního systému a odkazů na zásady životního cyklu najdete v tématu podporované verze operačního systému .NET [core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="535b9-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="535b9-182">Další informace o tom, jak nainstalovat .NET Core 3,0 na ARM64, najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="535b9-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="535b9-183">Závislosti distribuce systému Linux</span><span class="sxs-lookup"><span data-stu-id="535b9-183">Linux distribution dependencies</span></span>

<span data-ttu-id="535b9-184">Níže jsou uvedené příklady.</span><span class="sxs-lookup"><span data-stu-id="535b9-184">The following are intended to be examples.</span></span> <span data-ttu-id="535b9-185">Přesné verze a názvy se mohou mírně lišit podle vaší možnosti rozšíření pro Linux.</span><span class="sxs-lookup"><span data-stu-id="535b9-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="535b9-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="535b9-186">Ubuntu</span></span>

<span data-ttu-id="535b9-187">Ubuntu distribuce vyžadují následující nainstalované knihovny:</span><span class="sxs-lookup"><span data-stu-id="535b9-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="535b9-188">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="535b9-188">liblttng-ust0</span></span>
* <span data-ttu-id="535b9-189">libcurl3 (pro 14. x a 16. x)</span><span class="sxs-lookup"><span data-stu-id="535b9-189">libcurl3 (for 14.x and 16.x)</span></span>
* <span data-ttu-id="535b9-190">libcurl4 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="535b9-190">libcurl4 (for 18.x)</span></span>
* <span data-ttu-id="535b9-191">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="535b9-191">libssl1.0.0</span></span>
* <span data-ttu-id="535b9-192">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="535b9-192">libkrb5-3</span></span>
* <span data-ttu-id="535b9-193">zlib1g</span><span class="sxs-lookup"><span data-stu-id="535b9-193">zlib1g</span></span>
* <span data-ttu-id="535b9-194">libicu52 (pro 14. x)</span><span class="sxs-lookup"><span data-stu-id="535b9-194">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="535b9-195">libicu55 (pro 16. x)</span><span class="sxs-lookup"><span data-stu-id="535b9-195">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="535b9-196">libicu57 (pro 17. x)</span><span class="sxs-lookup"><span data-stu-id="535b9-196">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="535b9-197">libicu60 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="535b9-197">libicu60 (for 18.x)</span></span>

<span data-ttu-id="535b9-198">Pro verze starší než .NET Core 2,1 jsou vyžadovány i následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="535b9-198">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="535b9-199">libunwind8</span><span class="sxs-lookup"><span data-stu-id="535b9-199">libunwind8</span></span>
* <span data-ttu-id="535b9-200">libuuid1</span><span class="sxs-lookup"><span data-stu-id="535b9-200">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="535b9-201">CentOS a Fedora</span><span class="sxs-lookup"><span data-stu-id="535b9-201">CentOS and Fedora</span></span>

<span data-ttu-id="535b9-202">CentOS distribuce vyžadují následující nainstalované knihovny:</span><span class="sxs-lookup"><span data-stu-id="535b9-202">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="535b9-203">lttng – tým UST</span><span class="sxs-lookup"><span data-stu-id="535b9-203">lttng-ust</span></span>
* <span data-ttu-id="535b9-204">libcurl</span><span class="sxs-lookup"><span data-stu-id="535b9-204">libcurl</span></span>
* <span data-ttu-id="535b9-205">OpenSSL – knihovny</span><span class="sxs-lookup"><span data-stu-id="535b9-205">openssl-libs</span></span>
* <span data-ttu-id="535b9-206">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="535b9-206">krb5-libs</span></span>
* <span data-ttu-id="535b9-207">libicu</span><span class="sxs-lookup"><span data-stu-id="535b9-207">libicu</span></span>
* <span data-ttu-id="535b9-208">ZLIB</span><span class="sxs-lookup"><span data-stu-id="535b9-208">zlib</span></span>

<span data-ttu-id="535b9-209">Fedora uživatelé: Pokud vaše verze OpenSSL > = 1,1, budete muset nainstalovat openssl10.</span><span class="sxs-lookup"><span data-stu-id="535b9-209">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="535b9-210">Pro verze starší než .NET Core 2,1 jsou vyžadovány i následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="535b9-210">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="535b9-211">libunwind</span><span class="sxs-lookup"><span data-stu-id="535b9-211">libunwind</span></span>
* <span data-ttu-id="535b9-212">libuuid</span><span class="sxs-lookup"><span data-stu-id="535b9-212">libuuid</span></span>

<span data-ttu-id="535b9-213">Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="535b9-213">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="535b9-214">Instalace závislostí .NET Core s nativními instalačními programy</span><span class="sxs-lookup"><span data-stu-id="535b9-214">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="535b9-215">Nativní instalační programy .NET Core jsou k dispozici pro podporované distribuce a verze systému Linux.</span><span class="sxs-lookup"><span data-stu-id="535b9-215">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="535b9-216">Nativní instalační programy vyžadují přístup správce (sudo) k serveru.</span><span class="sxs-lookup"><span data-stu-id="535b9-216">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="535b9-217">Výhodou použití nativního instalačního programu je, že jsou nainstalované všechny nativní závislosti .NET Core.</span><span class="sxs-lookup"><span data-stu-id="535b9-217">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="535b9-218">Nativní instalační programy také instalují .NET Core SDK systém.</span><span class="sxs-lookup"><span data-stu-id="535b9-218">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="535b9-219">V systému Linux jsou k dispozici dvě možnosti balíčku instalačního programu:</span><span class="sxs-lookup"><span data-stu-id="535b9-219">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="535b9-220">Pomocí Správce balíčků na základě informačního kanálu, jako je apt-get pro Ubuntu, nebo Yumu pro CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="535b9-220">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="535b9-221">Použití samotných balíčků, DEB nebo ot./min.</span><span class="sxs-lookup"><span data-stu-id="535b9-221">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="535b9-222">Skripty se instalují pomocí skriptu Instalační služby .NET Core.</span><span class="sxs-lookup"><span data-stu-id="535b9-222">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="535b9-223">[Příkaz dotnet – instalace skriptů](./tools/dotnet-install-script.md) slouží k provedení instalace rozhraní příkazového řádku CLI sada nástrojů a sdíleného modulu runtime bez správy.</span><span class="sxs-lookup"><span data-stu-id="535b9-223">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="535b9-224">Skript si můžete stáhnout z <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="535b9-224">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="535b9-225">Skript ve výchozím nastavení instaluje nejnovější verzi "LTS", která je aktuálně .NET Core 1,1.</span><span class="sxs-lookup"><span data-stu-id="535b9-225">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="535b9-226">Pokud chcete nainstalovat .NET Core 2,1, spusťte skript s následujícím přepínačem:</span><span class="sxs-lookup"><span data-stu-id="535b9-226">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="535b9-227">Skript bash instalačního programu se používá ve scénářích automatizace a v instalacích bez správy.</span><span class="sxs-lookup"><span data-stu-id="535b9-227">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="535b9-228">Tento skript také přečte přepínače prostředí PowerShell, takže je možné ho použít se skriptem v systémech Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="535b9-228">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="535b9-229">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="535b9-229">Troubleshoot</span></span>

<span data-ttu-id="535b9-230">Pokud máte problémy s instalací .NET Core v podporované distribuci/verzi systému Linux, přečtěte si následující témata o nainstalovaných distribucích a verzích:</span><span class="sxs-lookup"><span data-stu-id="535b9-230">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="535b9-231">Známé problémy s .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="535b9-231">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="535b9-232">Známé problémy s .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="535b9-232">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="535b9-233">Známé problémy s .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="535b9-233">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="535b9-234">Známé problémy s .NET Core 1,1</span><span class="sxs-lookup"><span data-stu-id="535b9-234">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="535b9-235">Známé problémy s .NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="535b9-235">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
