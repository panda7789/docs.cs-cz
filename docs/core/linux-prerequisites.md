---
title: Předpoklady pro .NET Core v systému Linux
description: Podporované verze systému Linux a závislosti rozhraní .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na počítačích se systémem Linux.
author: leecow
ms.author: leecow
ms.date: 10/11/2019
ms.openlocfilehash: 0e798e86fcf88a1b7a67f50c2301e10ad725fad8
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521484"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="8c751-103">Předpoklady pro .NET Core v systému Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="8c751-104">Tento článek ukazuje závislosti potřebné pro vývoj aplikací .NET Core v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="8c751-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="8c751-105">Podporované distribuce a verze systému Linux a závislosti, které následují, se vztahují na dva způsoby vývoje aplikací .NET Core v systému Linux:</span><span class="sxs-lookup"><span data-stu-id="8c751-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

- [<span data-ttu-id="8c751-106">Příkazový řádek s oblíbeným editorem</span><span class="sxs-lookup"><span data-stu-id="8c751-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
- [<span data-ttu-id="8c751-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8c751-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="8c751-108">Pro produkční servery a prostředí se .NET Core SDK balíček nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="8c751-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="8c751-109">Pro aplikace nasazené do produkčního prostředí je potřeba jenom balíček runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c751-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="8c751-110">Modul runtime .NET Core je nasazen s aplikacemi jako součást samostatného nasazení, ale musí být nasazen pro samostatně nasazené aplikace závislé na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c751-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="8c751-111">Další informace o typech nasazení závislých na rozhraní a samostatně obsažených typů naleznete v tématu [nasazení aplikace .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="8c751-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="8c751-112">Konkrétní pokyny najdete také v části [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="8c751-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="8c751-113">Podporované verze systému Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-113">Supported Linux versions</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="8c751-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8c751-114">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="8c751-115">.NET Core 3,0 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="8c751-115">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="8c751-116">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="8c751-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="8c751-117">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="8c751-117">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="8c751-118">.NET Core 3,0 se podporuje na následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="8c751-118">.NET Core 3.0 is supported on the following Linux distributions/versions):</span></span>

> [!NOTE]
> <span data-ttu-id="8c751-119">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="8c751-119">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="8c751-120">JINÉHO</span><span class="sxs-lookup"><span data-stu-id="8c751-120">OS</span></span>                             | <span data-ttu-id="8c751-121">Version</span><span class="sxs-lookup"><span data-stu-id="8c751-121">Version</span></span>               | <span data-ttu-id="8c751-122">Architektury</span><span class="sxs-lookup"><span data-stu-id="8c751-122">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="8c751-123">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-123">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="8c751-124">6 +, 7</span><span class="sxs-lookup"><span data-stu-id="8c751-124">6+, 7</span></span>                 | <span data-ttu-id="8c751-125">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-125">x64</span></span> |
| <span data-ttu-id="8c751-126">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-126">Oracle Linux</span></span>                   | <span data-ttu-id="8c751-127">čl</span><span class="sxs-lookup"><span data-stu-id="8c751-127">7</span></span>                     | <span data-ttu-id="8c751-128">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-128">x64</span></span> |
| <span data-ttu-id="8c751-129">CentOS</span><span class="sxs-lookup"><span data-stu-id="8c751-129">CentOS</span></span>                         | <span data-ttu-id="8c751-130">čl</span><span class="sxs-lookup"><span data-stu-id="8c751-130">7</span></span>                     | <span data-ttu-id="8c751-131">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-131">x64</span></span> |
| <span data-ttu-id="8c751-132">Fedora</span><span class="sxs-lookup"><span data-stu-id="8c751-132">Fedora</span></span>                         | <span data-ttu-id="8c751-133">29 +</span><span class="sxs-lookup"><span data-stu-id="8c751-133">29+</span></span>                   | <span data-ttu-id="8c751-134">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-134">x64</span></span> |
| <span data-ttu-id="8c751-135">Debian</span><span class="sxs-lookup"><span data-stu-id="8c751-135">Debian</span></span>                         | <span data-ttu-id="8c751-136">9 +</span><span class="sxs-lookup"><span data-stu-id="8c751-136">9+</span></span>                    | <span data-ttu-id="8c751-137">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="8c751-137">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="8c751-138">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8c751-138">Ubuntu</span></span>                         | <span data-ttu-id="8c751-139">16.04 +</span><span class="sxs-lookup"><span data-stu-id="8c751-139">16.04+</span></span>                | <span data-ttu-id="8c751-140">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="8c751-140">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="8c751-141">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="8c751-141">Linux Mint</span></span>                     | <span data-ttu-id="8c751-142">18 +</span><span class="sxs-lookup"><span data-stu-id="8c751-142">18+</span></span>                   | <span data-ttu-id="8c751-143">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-143">x64</span></span> |
| <span data-ttu-id="8c751-144">openSUSE</span><span class="sxs-lookup"><span data-stu-id="8c751-144">openSUSE</span></span>                       | <span data-ttu-id="8c751-145">15 +</span><span class="sxs-lookup"><span data-stu-id="8c751-145">15+</span></span>                   | <span data-ttu-id="8c751-146">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-146">x64</span></span> |
| <span data-ttu-id="8c751-147">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="8c751-147">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="8c751-148">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="8c751-148">12 SP2+</span></span>               | <span data-ttu-id="8c751-149">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-149">x64</span></span> |
| <span data-ttu-id="8c751-150">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-150">Alpine Linux</span></span>                   | <span data-ttu-id="8c751-151">3.8 +</span><span class="sxs-lookup"><span data-stu-id="8c751-151">3.8+</span></span>                  | <span data-ttu-id="8c751-152">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="8c751-152">x64, ARM64</span></span> |

<span data-ttu-id="8c751-153">Úplný 3,0 seznam podporovaných operačních systémů, distribucí a verzí operačního systému a odkazů na zásady životního cyklu najdete v tématu podporované verze operačního systému .NET [core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="8c751-153">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="8c751-154">Další informace o tom, jak nainstalovat .NET Core 3,0 na ARM64, najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="8c751-154">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="8c751-155">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="8c751-155">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="8c751-156">.NET Core 2,2 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="8c751-156">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="8c751-157">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="8c751-157">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="8c751-158">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení pro .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2).</span><span class="sxs-lookup"><span data-stu-id="8c751-158">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2).</span></span>

<span data-ttu-id="8c751-159">.NET Core 2,2 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="8c751-159">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="8c751-160">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="8c751-160">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="8c751-161">JINÉHO</span><span class="sxs-lookup"><span data-stu-id="8c751-161">OS</span></span>                             |  <span data-ttu-id="8c751-162">Version</span><span class="sxs-lookup"><span data-stu-id="8c751-162">Version</span></span>                |  <span data-ttu-id="8c751-163">Architektury</span><span class="sxs-lookup"><span data-stu-id="8c751-163">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="8c751-164">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-164">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="8c751-165">6, 7</span><span class="sxs-lookup"><span data-stu-id="8c751-165">6, 7</span></span>                   | <span data-ttu-id="8c751-166">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-166">x64</span></span> |
| <span data-ttu-id="8c751-167">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-167">Oracle Linux</span></span>                   |  <span data-ttu-id="8c751-168">čl</span><span class="sxs-lookup"><span data-stu-id="8c751-168">7</span></span>                      | <span data-ttu-id="8c751-169">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-169">x64</span></span> |
| <span data-ttu-id="8c751-170">CentOS</span><span class="sxs-lookup"><span data-stu-id="8c751-170">CentOS</span></span>                         |  <span data-ttu-id="8c751-171">čl</span><span class="sxs-lookup"><span data-stu-id="8c751-171">7</span></span>                      | <span data-ttu-id="8c751-172">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-172">x64</span></span> |
| <span data-ttu-id="8c751-173">Fedora</span><span class="sxs-lookup"><span data-stu-id="8c751-173">Fedora</span></span>                         |  <span data-ttu-id="8c751-174">29, 30</span><span class="sxs-lookup"><span data-stu-id="8c751-174">29, 30</span></span>                 | <span data-ttu-id="8c751-175">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-175">x64</span></span> |
| <span data-ttu-id="8c751-176">Debian</span><span class="sxs-lookup"><span data-stu-id="8c751-176">Debian</span></span>                         |  <span data-ttu-id="8c751-177">9</span><span class="sxs-lookup"><span data-stu-id="8c751-177">9</span></span>                      | <span data-ttu-id="8c751-178">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="8c751-178">x64, ARM32</span></span> |
| <span data-ttu-id="8c751-179">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8c751-179">Ubuntu</span></span>                         |  <span data-ttu-id="8c751-180">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="8c751-180">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="8c751-181">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="8c751-181">x64, ARM32</span></span> |
| <span data-ttu-id="8c751-182">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="8c751-182">Linux Mint</span></span>                     |  <span data-ttu-id="8c751-183">17, 18</span><span class="sxs-lookup"><span data-stu-id="8c751-183">17, 18</span></span>                 | <span data-ttu-id="8c751-184">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-184">x64</span></span> |
| <span data-ttu-id="8c751-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="8c751-185">openSUSE</span></span>                       |  <span data-ttu-id="8c751-186">15 +</span><span class="sxs-lookup"><span data-stu-id="8c751-186">15+</span></span>                    | <span data-ttu-id="8c751-187">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-187">x64</span></span> |
| <span data-ttu-id="8c751-188">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="8c751-188">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="8c751-189">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="8c751-189">12 SP2+</span></span>                | <span data-ttu-id="8c751-190">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-190">x64</span></span> |
| <span data-ttu-id="8c751-191">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-191">Alpine Linux</span></span>                   |  <span data-ttu-id="8c751-192">3.7 +</span><span class="sxs-lookup"><span data-stu-id="8c751-192">3.7+</span></span>                   | <span data-ttu-id="8c751-193">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-193">x64</span></span> |

<span data-ttu-id="8c751-194">Úplný 2,2 seznam podporovaných operačních systémů, distribucí a verzí operačního systému a odkazů na zásady životního cyklu najdete v tématu podporované verze operačního systému .NET [core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="8c751-194">See [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="8c751-195">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="8c751-195">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="8c751-196">.NET Core 2,1 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="8c751-196">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="8c751-197">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="8c751-197">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="8c751-198">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení pro .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="8c751-198">For download links and more information, see [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="8c751-199">.NET Core 2,1 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="8c751-199">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

| <span data-ttu-id="8c751-200">JINÉHO</span><span class="sxs-lookup"><span data-stu-id="8c751-200">OS</span></span>                             |  <span data-ttu-id="8c751-201">Version</span><span class="sxs-lookup"><span data-stu-id="8c751-201">Version</span></span>                |  <span data-ttu-id="8c751-202">Architektury</span><span class="sxs-lookup"><span data-stu-id="8c751-202">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="8c751-203">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-203">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="8c751-204">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="8c751-204">6, 7, 8</span></span>                | <span data-ttu-id="8c751-205">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-205">x64</span></span> |
| <span data-ttu-id="8c751-206">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-206">Oracle Linux</span></span>                   |  <span data-ttu-id="8c751-207">čl</span><span class="sxs-lookup"><span data-stu-id="8c751-207">7</span></span>                      | <span data-ttu-id="8c751-208">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-208">x64</span></span> |
| <span data-ttu-id="8c751-209">CentOS</span><span class="sxs-lookup"><span data-stu-id="8c751-209">CentOS</span></span>                         |  <span data-ttu-id="8c751-210">čl</span><span class="sxs-lookup"><span data-stu-id="8c751-210">7</span></span>                      | <span data-ttu-id="8c751-211">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-211">x64</span></span> |
| <span data-ttu-id="8c751-212">Fedora</span><span class="sxs-lookup"><span data-stu-id="8c751-212">Fedora</span></span>                         |  <span data-ttu-id="8c751-213">29, 30</span><span class="sxs-lookup"><span data-stu-id="8c751-213">29, 30</span></span>                 | <span data-ttu-id="8c751-214">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-214">x64</span></span> |
| <span data-ttu-id="8c751-215">Debian</span><span class="sxs-lookup"><span data-stu-id="8c751-215">Debian</span></span>                         |  <span data-ttu-id="8c751-216">9</span><span class="sxs-lookup"><span data-stu-id="8c751-216">9</span></span>                      | <span data-ttu-id="8c751-217">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="8c751-217">x64, ARM32</span></span> |
| <span data-ttu-id="8c751-218">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8c751-218">Ubuntu</span></span>                         |  <span data-ttu-id="8c751-219">16,04, 18,04, 19,04</span><span class="sxs-lookup"><span data-stu-id="8c751-219">16.04, 18.04, 19.04</span></span>    | <span data-ttu-id="8c751-220">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="8c751-220">x64, ARM32</span></span> |
| <span data-ttu-id="8c751-221">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="8c751-221">Linux Mint</span></span>                     |  <span data-ttu-id="8c751-222">17, 18</span><span class="sxs-lookup"><span data-stu-id="8c751-222">17, 18</span></span>                 | <span data-ttu-id="8c751-223">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-223">x64</span></span> |
| <span data-ttu-id="8c751-224">openSUSE</span><span class="sxs-lookup"><span data-stu-id="8c751-224">openSUSE</span></span>                       |  <span data-ttu-id="8c751-225">42.3 +</span><span class="sxs-lookup"><span data-stu-id="8c751-225">42.3+</span></span>                  | <span data-ttu-id="8c751-226">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-226">x64</span></span> |
| <span data-ttu-id="8c751-227">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="8c751-227">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="8c751-228">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="8c751-228">12 SP2+</span></span>                | <span data-ttu-id="8c751-229">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-229">x64</span></span> |
| <span data-ttu-id="8c751-230">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-230">Alpine Linux</span></span>                   |  <span data-ttu-id="8c751-231">3.7 +</span><span class="sxs-lookup"><span data-stu-id="8c751-231">3.7+</span></span>                   | <span data-ttu-id="8c751-232">x64</span><span class="sxs-lookup"><span data-stu-id="8c751-232">x64</span></span> |

<span data-ttu-id="8c751-233">Úplný 2,1 seznam podporovaných operačních systémů, distribucí a verzí operačního systému a odkazů na zásady životního cyklu najdete v tématu podporované verze operačního systému .NET [core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="8c751-233">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="8c751-234">Závislosti distribuce systému Linux</span><span class="sxs-lookup"><span data-stu-id="8c751-234">Linux distribution dependencies</span></span>

<span data-ttu-id="8c751-235">Níže jsou uvedené příklady.</span><span class="sxs-lookup"><span data-stu-id="8c751-235">The following are intended to be examples.</span></span> <span data-ttu-id="8c751-236">Přesné verze a názvy se mohou mírně lišit podle vaší možnosti rozšíření pro Linux.</span><span class="sxs-lookup"><span data-stu-id="8c751-236">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="8c751-237">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8c751-237">Ubuntu</span></span>

<span data-ttu-id="8c751-238">Ubuntu distribuce vyžadují následující nainstalované knihovny:</span><span class="sxs-lookup"><span data-stu-id="8c751-238">Ubuntu distributions require the following libraries installed:</span></span>

- <span data-ttu-id="8c751-239">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="8c751-239">liblttng-ust0</span></span>
- <span data-ttu-id="8c751-240">libcurl3 (pro 14. x a 16. x)</span><span class="sxs-lookup"><span data-stu-id="8c751-240">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="8c751-241">libcurl4 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="8c751-241">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="8c751-242">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="8c751-242">libssl1.0.0</span></span>
- <span data-ttu-id="8c751-243">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="8c751-243">libkrb5-3</span></span>
- <span data-ttu-id="8c751-244">zlib1g</span><span class="sxs-lookup"><span data-stu-id="8c751-244">zlib1g</span></span>
- <span data-ttu-id="8c751-245">libicu52 (pro 14. x)</span><span class="sxs-lookup"><span data-stu-id="8c751-245">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="8c751-246">libicu55 (pro 16. x)</span><span class="sxs-lookup"><span data-stu-id="8c751-246">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="8c751-247">libicu57 (pro 17. x)</span><span class="sxs-lookup"><span data-stu-id="8c751-247">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="8c751-248">libicu60 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="8c751-248">libicu60 (for 18.x)</span></span>

<span data-ttu-id="8c751-249">Pro verze starší než .NET Core 2,1 jsou vyžadovány i následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="8c751-249">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

- <span data-ttu-id="8c751-250">libunwind8</span><span class="sxs-lookup"><span data-stu-id="8c751-250">libunwind8</span></span>
- <span data-ttu-id="8c751-251">libuuid1</span><span class="sxs-lookup"><span data-stu-id="8c751-251">libuuid1</span></span>

<span data-ttu-id="8c751-252">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:</span><span class="sxs-lookup"><span data-stu-id="8c751-252">For .NET Core applications that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

* <span data-ttu-id="8c751-253">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="8c751-253">libgdiplus (version 6.0.1 or later)</span></span>

> [!NOTE]
> <span data-ttu-id="8c751-254">Většina verzí Ubuntu zahrnuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="8c751-254">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="8c751-255">Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="8c751-255">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="8c751-256">Další informace najdete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="8c751-256">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="8c751-257">CentOS a Fedora</span><span class="sxs-lookup"><span data-stu-id="8c751-257">CentOS and Fedora</span></span>

<span data-ttu-id="8c751-258">CentOS distribuce vyžadují následující nainstalované knihovny:</span><span class="sxs-lookup"><span data-stu-id="8c751-258">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="8c751-259">lttng – tým UST</span><span class="sxs-lookup"><span data-stu-id="8c751-259">lttng-ust</span></span>
- <span data-ttu-id="8c751-260">libcurl</span><span class="sxs-lookup"><span data-stu-id="8c751-260">libcurl</span></span>
- <span data-ttu-id="8c751-261">OpenSSL – knihovny</span><span class="sxs-lookup"><span data-stu-id="8c751-261">openssl-libs</span></span>
- <span data-ttu-id="8c751-262">krb5 – knihovny</span><span class="sxs-lookup"><span data-stu-id="8c751-262">krb5-libs</span></span>
- <span data-ttu-id="8c751-263">libicu</span><span class="sxs-lookup"><span data-stu-id="8c751-263">libicu</span></span>
- <span data-ttu-id="8c751-264">ZLIB</span><span class="sxs-lookup"><span data-stu-id="8c751-264">zlib</span></span>

<span data-ttu-id="8c751-265">Fedora uživatelé: Pokud verze vašeho opensslu je > = 1,1, budete muset nainstalovat kompatibilní s openssl10.</span><span class="sxs-lookup"><span data-stu-id="8c751-265">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="8c751-266">Pro verze starší než .NET Core 2,1 jsou vyžadovány i následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="8c751-266">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

- <span data-ttu-id="8c751-267">libunwind</span><span class="sxs-lookup"><span data-stu-id="8c751-267">libunwind</span></span>
- <span data-ttu-id="8c751-268">libuuid</span><span class="sxs-lookup"><span data-stu-id="8c751-268">libuuid</span></span>

<span data-ttu-id="8c751-269">Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="8c751-269">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="8c751-270">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="8c751-270">For .NET Core applications that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

* <span data-ttu-id="8c751-271">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="8c751-271">libgdiplus (version 6.0.1 or later)</span></span>

> [!NOTE]
> <span data-ttu-id="8c751-272">Většina verzí CentOS a Fedora zahrnuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="8c751-272">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="8c751-273">Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="8c751-273">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="8c751-274">Další informace najdete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="8c751-274">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="8c751-275">Instalace závislostí .NET Core s nativními instalačními programy</span><span class="sxs-lookup"><span data-stu-id="8c751-275">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="8c751-276">Nativní instalační programy .NET Core jsou k dispozici pro podporované distribuce a verze systému Linux.</span><span class="sxs-lookup"><span data-stu-id="8c751-276">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="8c751-277">Nativní instalační programy vyžadují přístup správce (sudo) k serveru.</span><span class="sxs-lookup"><span data-stu-id="8c751-277">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="8c751-278">Výhodou použití nativního instalačního programu je, že jsou nainstalované všechny nativní závislosti .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c751-278">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="8c751-279">Nativní instalační programy také instalují .NET Core SDK systém.</span><span class="sxs-lookup"><span data-stu-id="8c751-279">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="8c751-280">V systému Linux jsou k dispozici dvě možnosti balíčku instalačního programu:</span><span class="sxs-lookup"><span data-stu-id="8c751-280">On Linux, there are two installer package choices:</span></span>

- <span data-ttu-id="8c751-281">Pomocí Správce balíčků na základě informačního kanálu, jako je apt-get pro Ubuntu, nebo Yumu pro CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="8c751-281">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
- <span data-ttu-id="8c751-282">Použití samotných balíčků, DEB nebo ot./min.</span><span class="sxs-lookup"><span data-stu-id="8c751-282">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="8c751-283">Skripty se instalují pomocí skriptu Instalační služby .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c751-283">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="8c751-284">[Příkaz dotnet – instalace skriptů](./tools/dotnet-install-script.md) slouží k provedení instalace rozhraní příkazového řádku CLI sada nástrojů a sdíleného modulu runtime bez správy.</span><span class="sxs-lookup"><span data-stu-id="8c751-284">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="8c751-285">Skript si můžete stáhnout z <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="8c751-285">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="8c751-286">Skript ve výchozím nastavení instaluje nejnovější verzi "LTS", která je aktuálně .NET Core 1,1.</span><span class="sxs-lookup"><span data-stu-id="8c751-286">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="8c751-287">Pokud chcete nainstalovat .NET Core 2,1, spusťte skript s následujícím přepínačem:</span><span class="sxs-lookup"><span data-stu-id="8c751-287">To install .NET Core 2.1, run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="8c751-288">Skript bash instalačního programu se používá ve scénářích automatizace a v instalacích bez správy.</span><span class="sxs-lookup"><span data-stu-id="8c751-288">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="8c751-289">Tento skript také přečte přepínače prostředí PowerShell, takže je možné ho použít se skriptem v systémech Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="8c751-289">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="8c751-290">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="8c751-290">Troubleshoot</span></span>

<span data-ttu-id="8c751-291">Pokud máte problémy s instalací .NET Core v podporované distribuci/verzi systému Linux, přečtěte si následující témata o nainstalovaných distribucích a verzích:</span><span class="sxs-lookup"><span data-stu-id="8c751-291">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

- [<span data-ttu-id="8c751-292">Známé problémy s .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="8c751-292">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
- [<span data-ttu-id="8c751-293">Známé problémy s .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="8c751-293">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
- [<span data-ttu-id="8c751-294">Známé problémy s .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="8c751-294">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
- [<span data-ttu-id="8c751-295">Známé problémy s .NET Core 1,1</span><span class="sxs-lookup"><span data-stu-id="8c751-295">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
- [<span data-ttu-id="8c751-296">Známé problémy s .NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="8c751-296">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
