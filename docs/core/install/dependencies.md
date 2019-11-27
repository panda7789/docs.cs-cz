---
title: Závislosti .NET Core SDK a modulu runtime – .NET Core
description: Podrobně popisuje operační systém a požadavky na architekturu procesoru pro instalaci .NET Core SDK a modulu runtime v systémech Windows, Linux a macOS.
author: leecow
ms.author: leecow
ms.date: 11/06/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: b79ec6a9723cbd44717d5f187213278556c0b6ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451099"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="5f8b5-103">Závislosti a požadavky .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f8b5-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="5f8b5-104">Tento článek podrobně popisuje, které operační systémy a architektura procesoru jsou podporovány rozhraním .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="5f8b5-105">Podporované operační systémy</span><span class="sxs-lookup"><span data-stu-id="5f8b5-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="5f8b5-106">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f8b5-106">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="5f8b5-107">Rozhraní .NET Core 3,0 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-107">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="5f8b5-108">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5f8b5-109">OS</span><span class="sxs-lookup"><span data-stu-id="5f8b5-109">OS</span></span>                            | <span data-ttu-id="5f8b5-110">Version</span><span class="sxs-lookup"><span data-stu-id="5f8b5-110">Version</span></span>                        | <span data-ttu-id="5f8b5-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="5f8b5-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5f8b5-112">Počítač s klientským operačním systémem Windows</span><span class="sxs-lookup"><span data-stu-id="5f8b5-112">Windows Client</span></span>                | <span data-ttu-id="5f8b5-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="5f8b5-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5f8b5-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5f8b5-114">x64, x86</span></span>        |
| <span data-ttu-id="5f8b5-115">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="5f8b5-115">Windows 10 Client</span></span>             | <span data-ttu-id="5f8b5-116">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-116">Version 1607+</span></span>                  | <span data-ttu-id="5f8b5-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5f8b5-117">x64, x86</span></span>        |
| <span data-ttu-id="5f8b5-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5f8b5-118">Windows Server</span></span>                | <span data-ttu-id="5f8b5-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-119">2012 R2+</span></span>                       | <span data-ttu-id="5f8b5-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5f8b5-120">x64, x86</span></span>        |
| <span data-ttu-id="5f8b5-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5f8b5-121">Nano Server</span></span>                   | <span data-ttu-id="5f8b5-122">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-122">Version 1803+</span></span>                  | <span data-ttu-id="5f8b5-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5f8b5-123">x64, ARM32</span></span>      |

<span data-ttu-id="5f8b5-124">Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-124">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="5f8b5-125">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="5f8b5-125">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5f8b5-126">Rozhraní .NET Core 2,2 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-126">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="5f8b5-127">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5f8b5-128">OS</span><span class="sxs-lookup"><span data-stu-id="5f8b5-128">OS</span></span>                            | <span data-ttu-id="5f8b5-129">Version</span><span class="sxs-lookup"><span data-stu-id="5f8b5-129">Version</span></span>                        | <span data-ttu-id="5f8b5-130">Architektury</span><span class="sxs-lookup"><span data-stu-id="5f8b5-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5f8b5-131">Počítač s klientským operačním systémem Windows</span><span class="sxs-lookup"><span data-stu-id="5f8b5-131">Windows Client</span></span>                | <span data-ttu-id="5f8b5-132">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="5f8b5-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5f8b5-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5f8b5-133">x64, x86</span></span>        |
| <span data-ttu-id="5f8b5-134">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="5f8b5-134">Windows 10 Client</span></span>             | <span data-ttu-id="5f8b5-135">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-135">Version 1607+</span></span>                  | <span data-ttu-id="5f8b5-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5f8b5-136">x64, x86</span></span>        |
| <span data-ttu-id="5f8b5-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5f8b5-137">Windows Server</span></span>                | <span data-ttu-id="5f8b5-138">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-138">2008 R2 SP1+</span></span>                   | <span data-ttu-id="5f8b5-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5f8b5-139">x64, x86</span></span>        |
| <span data-ttu-id="5f8b5-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5f8b5-140">Nano Server</span></span>                   | <span data-ttu-id="5f8b5-141">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-141">Version 1803+</span></span>                   | <span data-ttu-id="5f8b5-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5f8b5-142">x64, ARM32</span></span>      |

<span data-ttu-id="5f8b5-143">Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-143">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5f8b5-144">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="5f8b5-144">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5f8b5-145">Rozhraní .NET Core 2,1 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-145">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="5f8b5-146">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5f8b5-147">OS</span><span class="sxs-lookup"><span data-stu-id="5f8b5-147">OS</span></span>                            | <span data-ttu-id="5f8b5-148">Version</span><span class="sxs-lookup"><span data-stu-id="5f8b5-148">Version</span></span>                        | <span data-ttu-id="5f8b5-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="5f8b5-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5f8b5-150">Počítač s klientským operačním systémem Windows</span><span class="sxs-lookup"><span data-stu-id="5f8b5-150">Windows Client</span></span>                | <span data-ttu-id="5f8b5-151">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="5f8b5-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5f8b5-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5f8b5-152">x64, x86</span></span>        |
| <span data-ttu-id="5f8b5-153">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="5f8b5-153">Windows 10 Client</span></span>             | <span data-ttu-id="5f8b5-154">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-154">Version 1607+</span></span>                  | <span data-ttu-id="5f8b5-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5f8b5-155">x64, x86</span></span>        |
| <span data-ttu-id="5f8b5-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5f8b5-156">Windows Server</span></span>                | <span data-ttu-id="5f8b5-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="5f8b5-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5f8b5-158">x64, x86</span></span>        |
| <span data-ttu-id="5f8b5-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5f8b5-159">Nano Server</span></span>                   | <span data-ttu-id="5f8b5-160">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-160">Version 1803+</span></span>                  | <span data-ttu-id="5f8b5-161">platformě</span><span class="sxs-lookup"><span data-stu-id="5f8b5-161">x64,</span></span>            |

<span data-ttu-id="5f8b5-162">Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-162">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="5f8b5-163">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="5f8b5-163">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="5f8b5-164">Pokud instalujete sadu .NET SDK nebo modul runtime v následujících verzích systému Windows, jsou vyžadovány další závislosti:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-164">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="5f8b5-165">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="5f8b5-165">Windows 7 SP1</span></span>
- <span data-ttu-id="5f8b5-166">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="5f8b5-166">Windows Vista SP 2</span></span>
- <span data-ttu-id="5f8b5-167">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="5f8b5-167">Windows 8.1</span></span>
- <span data-ttu-id="5f8b5-168">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="5f8b5-168">Windows Server 2008 R2</span></span>
- <span data-ttu-id="5f8b5-169">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5f8b5-169">Windows Server 2012 R2</span></span>

<span data-ttu-id="5f8b5-170">Nainstalujte následující:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-170">Install the following:</span></span>

- <span data-ttu-id="5f8b5-171">[Distribuovatelné C++ součásti Microsoft Visual 2015 Update 3](https://www.microsoft.com/download/details.aspx?id=52685)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-171">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="5f8b5-172">KB2533623</span><span class="sxs-lookup"><span data-stu-id="5f8b5-172">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="5f8b5-173">Výše uvedené požadavky se vyžadují také v případě, že dojde k jedné z následujících chyb:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-173">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="5f8b5-174">Program nelze spustit, protože v počítači chybí *rozhraní API-MS-Win-CRT-runtime-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="5f8b5-174">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="5f8b5-175">Zkuste tento problém vyřešit tak, že znovu nainstalujete program.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-175">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="5f8b5-176">\- nebo-</span><span class="sxs-lookup"><span data-stu-id="5f8b5-176">\- or -</span></span>
>
> <span data-ttu-id="5f8b5-177">Knihovna *hostfxr. dll* byla nalezena, ale byla načtena z *C:\\\<path_to_app >\\hostfxr. dll* se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-177">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="5f8b5-178">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f8b5-178">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="5f8b5-179">.NET Core 3,0 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-179">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="5f8b5-180">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-180">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5f8b5-181">.NET Core 3,0 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-181">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5f8b5-182">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-182">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5f8b5-183">OS</span><span class="sxs-lookup"><span data-stu-id="5f8b5-183">OS</span></span>                             | <span data-ttu-id="5f8b5-184">Version</span><span class="sxs-lookup"><span data-stu-id="5f8b5-184">Version</span></span>               | <span data-ttu-id="5f8b5-185">Architektury</span><span class="sxs-lookup"><span data-stu-id="5f8b5-185">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="5f8b5-186">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5f8b5-186">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="5f8b5-187">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="5f8b5-187">6, 7, 8</span></span>               | <span data-ttu-id="5f8b5-188">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-188">x64</span></span> |
| <span data-ttu-id="5f8b5-189">CentOS</span><span class="sxs-lookup"><span data-stu-id="5f8b5-189">CentOS</span></span>                         | <span data-ttu-id="5f8b5-190">7 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-190">7+</span></span>                    | <span data-ttu-id="5f8b5-191">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-191">x64</span></span> |
| <span data-ttu-id="5f8b5-192">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5f8b5-192">Oracle Linux</span></span>                   | <span data-ttu-id="5f8b5-193">7 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-193">7+</span></span>                    | <span data-ttu-id="5f8b5-194">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-194">x64</span></span> |
| <span data-ttu-id="5f8b5-195">Fedora</span><span class="sxs-lookup"><span data-stu-id="5f8b5-195">Fedora</span></span>                         | <span data-ttu-id="5f8b5-196">29 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-196">29+</span></span>                   | <span data-ttu-id="5f8b5-197">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-197">x64</span></span> |
| <span data-ttu-id="5f8b5-198">Debian</span><span class="sxs-lookup"><span data-stu-id="5f8b5-198">Debian</span></span>                         | <span data-ttu-id="5f8b5-199">9 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-199">9+</span></span>                    | <span data-ttu-id="5f8b5-200">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-200">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="5f8b5-201">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5f8b5-201">Ubuntu</span></span>                         | <span data-ttu-id="5f8b5-202">16.04 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-202">16.04+</span></span>                | <span data-ttu-id="5f8b5-203">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-203">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="5f8b5-204">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="5f8b5-204">Linux Mint</span></span>                     | <span data-ttu-id="5f8b5-205">18 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-205">18+</span></span>                   | <span data-ttu-id="5f8b5-206">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-206">x64</span></span> |
| <span data-ttu-id="5f8b5-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5f8b5-207">openSUSE</span></span>                       | <span data-ttu-id="5f8b5-208">15 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-208">15+</span></span>                   | <span data-ttu-id="5f8b5-209">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-209">x64</span></span> |
| <span data-ttu-id="5f8b5-210">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-210">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="5f8b5-211">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="5f8b5-211">12 SP2+</span></span>               | <span data-ttu-id="5f8b5-212">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-212">x64</span></span> |
| <span data-ttu-id="5f8b5-213">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="5f8b5-213">Alpine Linux</span></span>                   | <span data-ttu-id="5f8b5-214">3.8 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-214">3.8+</span></span>                  | <span data-ttu-id="5f8b5-215">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-215">x64, ARM64</span></span> |

<span data-ttu-id="5f8b5-216">Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-216">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="5f8b5-217">Další informace o tom, jak nainstalovat .NET Core 3,0 na ARM64, najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-217">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="5f8b5-218">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="5f8b5-218">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5f8b5-219">.NET Core 2,2 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-219">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="5f8b5-220">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-220">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5f8b5-221">.NET Core 2,2 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-221">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5f8b5-222">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-222">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5f8b5-223">OS</span><span class="sxs-lookup"><span data-stu-id="5f8b5-223">OS</span></span>                             |  <span data-ttu-id="5f8b5-224">Version</span><span class="sxs-lookup"><span data-stu-id="5f8b5-224">Version</span></span>                |  <span data-ttu-id="5f8b5-225">Architektury</span><span class="sxs-lookup"><span data-stu-id="5f8b5-225">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="5f8b5-226">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5f8b5-226">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="5f8b5-227">6, 7</span><span class="sxs-lookup"><span data-stu-id="5f8b5-227">6, 7</span></span>                   | <span data-ttu-id="5f8b5-228">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-228">x64</span></span> |
| <span data-ttu-id="5f8b5-229">CentOS</span><span class="sxs-lookup"><span data-stu-id="5f8b5-229">CentOS</span></span>                         |  <span data-ttu-id="5f8b5-230">7</span><span class="sxs-lookup"><span data-stu-id="5f8b5-230">7</span></span>                      | <span data-ttu-id="5f8b5-231">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-231">x64</span></span> |
| <span data-ttu-id="5f8b5-232">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5f8b5-232">Oracle Linux</span></span>                   |  <span data-ttu-id="5f8b5-233">7</span><span class="sxs-lookup"><span data-stu-id="5f8b5-233">7</span></span>                      | <span data-ttu-id="5f8b5-234">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-234">x64</span></span> |
| <span data-ttu-id="5f8b5-235">Fedora</span><span class="sxs-lookup"><span data-stu-id="5f8b5-235">Fedora</span></span>                         |  <span data-ttu-id="5f8b5-236">29, 30</span><span class="sxs-lookup"><span data-stu-id="5f8b5-236">29, 30</span></span>                 | <span data-ttu-id="5f8b5-237">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-237">x64</span></span> |
| <span data-ttu-id="5f8b5-238">Debian</span><span class="sxs-lookup"><span data-stu-id="5f8b5-238">Debian</span></span>                         |  <span data-ttu-id="5f8b5-239">9</span><span class="sxs-lookup"><span data-stu-id="5f8b5-239">9</span></span>                      | <span data-ttu-id="5f8b5-240">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5f8b5-240">x64, ARM32</span></span> |
| <span data-ttu-id="5f8b5-241">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5f8b5-241">Ubuntu</span></span>                         |  <span data-ttu-id="5f8b5-242">16,04, 18,04, 18,10, 19,04</span><span class="sxs-lookup"><span data-stu-id="5f8b5-242">16.04, 18.04, 18.10, 19.04</span></span>    | <span data-ttu-id="5f8b5-243">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5f8b5-243">x64, ARM32</span></span> |
| <span data-ttu-id="5f8b5-244">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="5f8b5-244">Linux Mint</span></span>                     |  <span data-ttu-id="5f8b5-245">17, 18</span><span class="sxs-lookup"><span data-stu-id="5f8b5-245">17, 18</span></span>                 | <span data-ttu-id="5f8b5-246">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-246">x64</span></span> |
| <span data-ttu-id="5f8b5-247">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5f8b5-247">openSUSE</span></span>                       |  <span data-ttu-id="5f8b5-248">15 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-248">15+</span></span>                    | <span data-ttu-id="5f8b5-249">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-249">x64</span></span> |
| <span data-ttu-id="5f8b5-250">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-250">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="5f8b5-251">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="5f8b5-251">12 SP2+</span></span>                | <span data-ttu-id="5f8b5-252">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-252">x64</span></span> |
| <span data-ttu-id="5f8b5-253">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="5f8b5-253">Alpine Linux</span></span>                   |  <span data-ttu-id="5f8b5-254">3.8 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-254">3.8+</span></span>                   | <span data-ttu-id="5f8b5-255">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-255">x64</span></span> |

<span data-ttu-id="5f8b5-256">Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-256">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5f8b5-257">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="5f8b5-257">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5f8b5-258">.NET Core 2,1 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-258">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="5f8b5-259">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-259">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5f8b5-260">.NET Core 2,1 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-260">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5f8b5-261">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-261">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5f8b5-262">OS</span><span class="sxs-lookup"><span data-stu-id="5f8b5-262">OS</span></span>                             |  <span data-ttu-id="5f8b5-263">Version</span><span class="sxs-lookup"><span data-stu-id="5f8b5-263">Version</span></span>                |  <span data-ttu-id="5f8b5-264">Architektury</span><span class="sxs-lookup"><span data-stu-id="5f8b5-264">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="5f8b5-265">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5f8b5-265">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="5f8b5-266">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="5f8b5-266">6, 7, 8</span></span>                | <span data-ttu-id="5f8b5-267">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-267">x64</span></span> |
| <span data-ttu-id="5f8b5-268">CentOS</span><span class="sxs-lookup"><span data-stu-id="5f8b5-268">CentOS</span></span>                         |  <span data-ttu-id="5f8b5-269">7 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-269">7+</span></span>                     | <span data-ttu-id="5f8b5-270">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-270">x64</span></span> |
| <span data-ttu-id="5f8b5-271">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5f8b5-271">Oracle Linux</span></span>                   |  <span data-ttu-id="5f8b5-272">7 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-272">7+</span></span>                     | <span data-ttu-id="5f8b5-273">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-273">x64</span></span> |
| <span data-ttu-id="5f8b5-274">Fedora</span><span class="sxs-lookup"><span data-stu-id="5f8b5-274">Fedora</span></span>                         |  <span data-ttu-id="5f8b5-275">29 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-275">29+</span></span>                    | <span data-ttu-id="5f8b5-276">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-276">x64</span></span> |
| <span data-ttu-id="5f8b5-277">Debian</span><span class="sxs-lookup"><span data-stu-id="5f8b5-277">Debian</span></span>                         |  <span data-ttu-id="5f8b5-278">9</span><span class="sxs-lookup"><span data-stu-id="5f8b5-278">9</span></span>                      | <span data-ttu-id="5f8b5-279">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5f8b5-279">x64, ARM32</span></span> |
| <span data-ttu-id="5f8b5-280">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5f8b5-280">Ubuntu</span></span>                         |  <span data-ttu-id="5f8b5-281">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="5f8b5-281">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="5f8b5-282">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5f8b5-282">x64, ARM32</span></span> |
| <span data-ttu-id="5f8b5-283">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="5f8b5-283">Linux Mint</span></span>                     |  <span data-ttu-id="5f8b5-284">17 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-284">17+</span></span>                    | <span data-ttu-id="5f8b5-285">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-285">x64</span></span> |
| <span data-ttu-id="5f8b5-286">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5f8b5-286">openSUSE</span></span>                       |  <span data-ttu-id="5f8b5-287">15 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-287">15+</span></span>                    | <span data-ttu-id="5f8b5-288">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-288">x64</span></span> |
| <span data-ttu-id="5f8b5-289">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-289">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="5f8b5-290">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="5f8b5-290">12 SP2+</span></span>                | <span data-ttu-id="5f8b5-291">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-291">x64</span></span> |
| <span data-ttu-id="5f8b5-292">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="5f8b5-292">Alpine Linux</span></span>                   |  <span data-ttu-id="5f8b5-293">3.8 +</span><span class="sxs-lookup"><span data-stu-id="5f8b5-293">3.8+</span></span>                   | <span data-ttu-id="5f8b5-294">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-294">x64</span></span> |

<span data-ttu-id="5f8b5-295">Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-295">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="5f8b5-296">Závislosti distribuce systému Linux</span><span class="sxs-lookup"><span data-stu-id="5f8b5-296">Linux distribution dependencies</span></span>

<span data-ttu-id="5f8b5-297">Na základě distribuce systému Linux bude pravděpodobně nutné nainstalovat další závislosti.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-297">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f8b5-298">Přesné verze a názvy se mohou mírně lišit podle vaší možnosti rozšíření pro Linux.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-298">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="5f8b5-299">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5f8b5-299">Ubuntu</span></span>

<span data-ttu-id="5f8b5-300">Ubuntu distribuce vyžadují, aby byly nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-300">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="5f8b5-301">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="5f8b5-301">liblttng-ust0</span></span>
- <span data-ttu-id="5f8b5-302">libcurl3 (pro 14. x a 16. x)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-302">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="5f8b5-303">libcurl4 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-303">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="5f8b5-304">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="5f8b5-304">libssl1.0.0</span></span>
- <span data-ttu-id="5f8b5-305">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="5f8b5-305">libkrb5-3</span></span>
- <span data-ttu-id="5f8b5-306">zlib1g</span><span class="sxs-lookup"><span data-stu-id="5f8b5-306">zlib1g</span></span>
- <span data-ttu-id="5f8b5-307">libicu52 (pro 14. x)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-307">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="5f8b5-308">libicu55 (pro 16. x)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-308">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="5f8b5-309">libicu57 (pro 17. x)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-309">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="5f8b5-310">libicu60 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-310">libicu60 (for 18.x)</span></span>

<span data-ttu-id="5f8b5-311">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-311">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="5f8b5-312">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-312">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="5f8b5-313">Většina verzí Ubuntu zahrnuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-313">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="5f8b5-314">Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-314">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="5f8b5-315">Další informace najdete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-315">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="5f8b5-316">CentOS a Fedora</span><span class="sxs-lookup"><span data-stu-id="5f8b5-316">CentOS and Fedora</span></span>

<span data-ttu-id="5f8b5-317">CentOS distribuce vyžadují následující nainstalované knihovny:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-317">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="5f8b5-318">lttng – tým UST</span><span class="sxs-lookup"><span data-stu-id="5f8b5-318">lttng-ust</span></span>
- <span data-ttu-id="5f8b5-319">libcurl</span><span class="sxs-lookup"><span data-stu-id="5f8b5-319">libcurl</span></span>
- <span data-ttu-id="5f8b5-320">OpenSSL – knihovny</span><span class="sxs-lookup"><span data-stu-id="5f8b5-320">openssl-libs</span></span>
- <span data-ttu-id="5f8b5-321">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="5f8b5-321">krb5-libs</span></span>
- <span data-ttu-id="5f8b5-322">libicu</span><span class="sxs-lookup"><span data-stu-id="5f8b5-322">libicu</span></span>
- <span data-ttu-id="5f8b5-323">ZLIB</span><span class="sxs-lookup"><span data-stu-id="5f8b5-323">zlib</span></span>

<span data-ttu-id="5f8b5-324">Fedora uživatelé: Pokud verze vašeho OpenSSLu je > = 1,1, budete muset nainstalovat **kompatibilní s openssl10**.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-324">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="5f8b5-325">Pro .NET Core 2,0 jsou potřeba taky následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-325">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="5f8b5-326">libunwind</span><span class="sxs-lookup"><span data-stu-id="5f8b5-326">libunwind</span></span>
- <span data-ttu-id="5f8b5-327">libuuid</span><span class="sxs-lookup"><span data-stu-id="5f8b5-327">libuuid</span></span>

<span data-ttu-id="5f8b5-328">Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-328">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="5f8b5-329">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-329">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="5f8b5-330">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-330">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="5f8b5-331">Většina verzí CentOS a Fedora zahrnuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-331">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="5f8b5-332">Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-332">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="5f8b5-333">Další informace najdete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-333">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="5f8b5-334">Rozhraní .NET Core je podporované v následujících verzích macOS:</span><span class="sxs-lookup"><span data-stu-id="5f8b5-334">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="5f8b5-335">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-335">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5f8b5-336">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f8b5-336">.NET Core Version</span></span> | <span data-ttu-id="5f8b5-337">macOS</span><span class="sxs-lookup"><span data-stu-id="5f8b5-337">macOS</span></span>                 | <span data-ttu-id="5f8b5-338">Architektury</span><span class="sxs-lookup"><span data-stu-id="5f8b5-338">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="5f8b5-339">3,0</span><span class="sxs-lookup"><span data-stu-id="5f8b5-339">3.0</span></span>               | <span data-ttu-id="5f8b5-340">Velký Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-340">High Sierra (10.13+)</span></span>  | <span data-ttu-id="5f8b5-341">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-341">x64</span></span> | [<span data-ttu-id="5f8b5-342">Další informace</span><span class="sxs-lookup"><span data-stu-id="5f8b5-342">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="5f8b5-343">2.2</span><span class="sxs-lookup"><span data-stu-id="5f8b5-343">2.2</span></span>               | <span data-ttu-id="5f8b5-344">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-344">Sierra (10.12+)</span></span>       | <span data-ttu-id="5f8b5-345">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-345">x64</span></span> | [<span data-ttu-id="5f8b5-346">Další informace</span><span class="sxs-lookup"><span data-stu-id="5f8b5-346">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="5f8b5-347">2.1</span><span class="sxs-lookup"><span data-stu-id="5f8b5-347">2.1</span></span>               | <span data-ttu-id="5f8b5-348">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="5f8b5-348">Sierra (10.12+)</span></span>       | <span data-ttu-id="5f8b5-349">x64</span><span class="sxs-lookup"><span data-stu-id="5f8b5-349">x64</span></span> | [<span data-ttu-id="5f8b5-350">Další informace</span><span class="sxs-lookup"><span data-stu-id="5f8b5-350">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="5f8b5-351">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="5f8b5-351">libgdiplus</span></span>

<span data-ttu-id="5f8b5-352">Aplikace .NET Core, které používají *System. Drawing. Common* Assembly, vyžadují, aby bylo možné nainstalovat libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-352">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="5f8b5-353">Snadný způsob, jak získat libgdiplus, je použít Správce balíčků [homebrew ("Brew")](https://brew.sh/) pro MacOS.</span><span class="sxs-lookup"><span data-stu-id="5f8b5-353">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="5f8b5-354">Po instalaci *Brew*nainstalujte libgdiplus spuštěním následujících příkazů na příkazovém řádku terminálu (Command):</span><span class="sxs-lookup"><span data-stu-id="5f8b5-354">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="5f8b5-355">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5f8b5-355">Next steps</span></span>

- <span data-ttu-id="5f8b5-356">Pro vývoj a spouštění aplikací nainstalujte [.NET Core SDK](sdk.md) (zahrnuje modul runtime).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-356">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="5f8b5-357">Pokud chcete spouštět aplikace, které vytvořili jiní uživatelé, nainstalujte [modul runtime .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="5f8b5-357">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
