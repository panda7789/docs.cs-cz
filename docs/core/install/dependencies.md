---
title: Základní sada SDK a závislosti za běhu .NET – jádro .NET
description: Podrobnosti o předpokladech architektury operačního systému a procesoru pro instalaci sady .NET Core SDK a runtime ve Windows, Linux u macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157804"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="27106-103">.NET Základní závislosti a požadavky</span><span class="sxs-lookup"><span data-stu-id="27106-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="27106-104">Tento článek podrobně popisuje, které operační systémy a architektura procesoru jsou podporovány rozhraním .NET Core.</span><span class="sxs-lookup"><span data-stu-id="27106-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="27106-105">Podporované operační systémy</span><span class="sxs-lookup"><span data-stu-id="27106-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="27106-106">.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="27106-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="27106-107">Pomocí rozhraní .NET Core 3.1 jsou podporovány následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="27106-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="27106-108">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="27106-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="27106-109">Operační systém</span><span class="sxs-lookup"><span data-stu-id="27106-109">OS</span></span>                            | <span data-ttu-id="27106-110">Version</span><span class="sxs-lookup"><span data-stu-id="27106-110">Version</span></span>                        | <span data-ttu-id="27106-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="27106-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="27106-112">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="27106-112">Windows Client</span></span>                | <span data-ttu-id="27106-113">7 SP1+, 8,1</span><span class="sxs-lookup"><span data-stu-id="27106-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="27106-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-114">x64, x86</span></span>        |
| <span data-ttu-id="27106-115">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="27106-115">Windows 10 Client</span></span>             | <span data-ttu-id="27106-116">Verze 1607+</span><span class="sxs-lookup"><span data-stu-id="27106-116">Version 1607+</span></span>                  | <span data-ttu-id="27106-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-117">x64, x86</span></span>        |
| <span data-ttu-id="27106-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="27106-118">Windows Server</span></span>                | <span data-ttu-id="27106-119">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="27106-119">2012 R2+</span></span>                       | <span data-ttu-id="27106-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-120">x64, x86</span></span>        |
| <span data-ttu-id="27106-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="27106-121">Nano Server</span></span>                   | <span data-ttu-id="27106-122">Verze 1803+</span><span class="sxs-lookup"><span data-stu-id="27106-122">Version 1803+</span></span>                  | <span data-ttu-id="27106-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="27106-123">x64, ARM32</span></span>      |

<span data-ttu-id="27106-124">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.1 naleznete v tématu .NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="27106-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="27106-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="27106-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="27106-126">Pomocí rozhraní .NET Core 3.0 jsou podporovány následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="27106-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="27106-127">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="27106-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="27106-128">Operační systém</span><span class="sxs-lookup"><span data-stu-id="27106-128">OS</span></span>                            | <span data-ttu-id="27106-129">Version</span><span class="sxs-lookup"><span data-stu-id="27106-129">Version</span></span>                        | <span data-ttu-id="27106-130">Architektury</span><span class="sxs-lookup"><span data-stu-id="27106-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="27106-131">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="27106-131">Windows Client</span></span>                | <span data-ttu-id="27106-132">7 SP1+, 8,1</span><span class="sxs-lookup"><span data-stu-id="27106-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="27106-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-133">x64, x86</span></span>        |
| <span data-ttu-id="27106-134">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="27106-134">Windows 10 Client</span></span>             | <span data-ttu-id="27106-135">Verze 1607+</span><span class="sxs-lookup"><span data-stu-id="27106-135">Version 1607+</span></span>                  | <span data-ttu-id="27106-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-136">x64, x86</span></span>        |
| <span data-ttu-id="27106-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="27106-137">Windows Server</span></span>                | <span data-ttu-id="27106-138">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="27106-138">2012 R2+</span></span>                       | <span data-ttu-id="27106-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-139">x64, x86</span></span>        |
| <span data-ttu-id="27106-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="27106-140">Nano Server</span></span>                   | <span data-ttu-id="27106-141">Verze 1803+</span><span class="sxs-lookup"><span data-stu-id="27106-141">Version 1803+</span></span>                  | <span data-ttu-id="27106-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="27106-142">x64, ARM32</span></span>      |

<span data-ttu-id="27106-143">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.0 naleznete v tématu .NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="27106-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="27106-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="27106-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="27106-145">Pomocí rozhraní .NET Core 2.2 jsou podporovány následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="27106-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="27106-146">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="27106-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="27106-147">Operační systém</span><span class="sxs-lookup"><span data-stu-id="27106-147">OS</span></span>                            | <span data-ttu-id="27106-148">Version</span><span class="sxs-lookup"><span data-stu-id="27106-148">Version</span></span>                        | <span data-ttu-id="27106-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="27106-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="27106-150">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="27106-150">Windows Client</span></span>                | <span data-ttu-id="27106-151">7 SP1+, 8,1</span><span class="sxs-lookup"><span data-stu-id="27106-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="27106-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-152">x64, x86</span></span>        |
| <span data-ttu-id="27106-153">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="27106-153">Windows 10 Client</span></span>             | <span data-ttu-id="27106-154">Verze 1607+</span><span class="sxs-lookup"><span data-stu-id="27106-154">Version 1607+</span></span>                  | <span data-ttu-id="27106-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-155">x64, x86</span></span>        |
| <span data-ttu-id="27106-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="27106-156">Windows Server</span></span>                | <span data-ttu-id="27106-157">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="27106-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="27106-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-158">x64, x86</span></span>        |
| <span data-ttu-id="27106-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="27106-159">Nano Server</span></span>                   | <span data-ttu-id="27106-160">Verze 1803+</span><span class="sxs-lookup"><span data-stu-id="27106-160">Version 1803+</span></span>                   | <span data-ttu-id="27106-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="27106-161">x64, ARM32</span></span>      |

<span data-ttu-id="27106-162">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.2 naleznete v tématu .NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="27106-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="27106-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="27106-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="27106-164">Následující verze systému Windows jsou podporovány pomocí rozhraní .NET Core 2.1:</span><span class="sxs-lookup"><span data-stu-id="27106-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="27106-165">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="27106-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="27106-166">Operační systém</span><span class="sxs-lookup"><span data-stu-id="27106-166">OS</span></span>                            | <span data-ttu-id="27106-167">Version</span><span class="sxs-lookup"><span data-stu-id="27106-167">Version</span></span>                        | <span data-ttu-id="27106-168">Architektury</span><span class="sxs-lookup"><span data-stu-id="27106-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="27106-169">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="27106-169">Windows Client</span></span>                | <span data-ttu-id="27106-170">7 SP1+, 8,1</span><span class="sxs-lookup"><span data-stu-id="27106-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="27106-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-171">x64, x86</span></span>        |
| <span data-ttu-id="27106-172">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="27106-172">Windows 10 Client</span></span>             | <span data-ttu-id="27106-173">Verze 1607+</span><span class="sxs-lookup"><span data-stu-id="27106-173">Version 1607+</span></span>                  | <span data-ttu-id="27106-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-174">x64, x86</span></span>        |
| <span data-ttu-id="27106-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="27106-175">Windows Server</span></span>                | <span data-ttu-id="27106-176">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="27106-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="27106-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="27106-177">x64, x86</span></span>        |
| <span data-ttu-id="27106-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="27106-178">Nano Server</span></span>                   | <span data-ttu-id="27106-179">Verze 1803+</span><span class="sxs-lookup"><span data-stu-id="27106-179">Version 1803+</span></span>                  | <span data-ttu-id="27106-180">x64,</span><span class="sxs-lookup"><span data-stu-id="27106-180">x64,</span></span>            |

<span data-ttu-id="27106-181">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.1 naleznete v tématu .NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="27106-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="27106-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="27106-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="27106-183">Další závislosti jsou vyžadovány, pokud instalujete sdsad .NET nebo runtime v následujících verzích systému Windows:</span><span class="sxs-lookup"><span data-stu-id="27106-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="27106-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="27106-184">Windows 7 SP1</span></span>
- <span data-ttu-id="27106-185">Systém Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="27106-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="27106-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="27106-186">Windows 8.1</span></span>
- <span data-ttu-id="27106-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="27106-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="27106-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="27106-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="27106-189">Nainstalujte následující:</span><span class="sxs-lookup"><span data-stu-id="27106-189">Install the following:</span></span>

- <span data-ttu-id="27106-190">[Redistribuovatelná aktualizace 3 aplikace Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="27106-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="27106-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="27106-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="27106-192">Výše uvedené požadavky jsou také vyžadovány, pokud narazíte na jednu z následujících chyb:</span><span class="sxs-lookup"><span data-stu-id="27106-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="27106-193">Program nelze spustit, protože *api-ms-win-crt-runtime-l1-1-0.dll* chybí v počítači.</span><span class="sxs-lookup"><span data-stu-id="27106-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="27106-194">Zkuste tento problém vyřešit přeinstalací programu.</span><span class="sxs-lookup"><span data-stu-id="27106-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="27106-195">\-nebo -</span><span class="sxs-lookup"><span data-stu-id="27106-195">\- or -</span></span>
>
> <span data-ttu-id="27106-196">Knihovna *hostfxr.dll* byla nalezena, ale načítání z *C:\\\<path_to_app>\\hostfxr.dll* se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="27106-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="27106-197">.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="27106-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="27106-198">.NET Core 3.1 zachází s Linuxem jako s jediným operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="27106-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="27106-199">Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.</span><span class="sxs-lookup"><span data-stu-id="27106-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="27106-200">.NET Core 3.1 je podporován na následujících linuxových distribucích/verzích:</span><span class="sxs-lookup"><span data-stu-id="27106-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="27106-201">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="27106-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="27106-202">Operační systém</span><span class="sxs-lookup"><span data-stu-id="27106-202">OS</span></span>                             | <span data-ttu-id="27106-203">Version</span><span class="sxs-lookup"><span data-stu-id="27106-203">Version</span></span>               | <span data-ttu-id="27106-204">Architektury</span><span class="sxs-lookup"><span data-stu-id="27106-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="27106-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="27106-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="27106-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="27106-206">6, 7, 8</span></span>               | <span data-ttu-id="27106-207">x64</span><span class="sxs-lookup"><span data-stu-id="27106-207">x64</span></span> |
| <span data-ttu-id="27106-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="27106-208">CentOS</span></span>                         | <span data-ttu-id="27106-209">7+</span><span class="sxs-lookup"><span data-stu-id="27106-209">7+</span></span>                    | <span data-ttu-id="27106-210">x64</span><span class="sxs-lookup"><span data-stu-id="27106-210">x64</span></span> |
| <span data-ttu-id="27106-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="27106-211">Oracle Linux</span></span>                   | <span data-ttu-id="27106-212">7+</span><span class="sxs-lookup"><span data-stu-id="27106-212">7+</span></span>                    | <span data-ttu-id="27106-213">x64</span><span class="sxs-lookup"><span data-stu-id="27106-213">x64</span></span> |
| <span data-ttu-id="27106-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="27106-214">Fedora</span></span>                         | <span data-ttu-id="27106-215">29+</span><span class="sxs-lookup"><span data-stu-id="27106-215">29+</span></span>                   | <span data-ttu-id="27106-216">x64</span><span class="sxs-lookup"><span data-stu-id="27106-216">x64</span></span> |
| <span data-ttu-id="27106-217">Debian</span><span class="sxs-lookup"><span data-stu-id="27106-217">Debian</span></span>                         | <span data-ttu-id="27106-218">9+</span><span class="sxs-lookup"><span data-stu-id="27106-218">9+</span></span>                    | <span data-ttu-id="27106-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="27106-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="27106-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="27106-220">Ubuntu</span></span>                         | <span data-ttu-id="27106-221">16.04+</span><span class="sxs-lookup"><span data-stu-id="27106-221">16.04+</span></span>                | <span data-ttu-id="27106-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="27106-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="27106-223">Linux mincovna</span><span class="sxs-lookup"><span data-stu-id="27106-223">Linux Mint</span></span>                     | <span data-ttu-id="27106-224">18+</span><span class="sxs-lookup"><span data-stu-id="27106-224">18+</span></span>                   | <span data-ttu-id="27106-225">x64</span><span class="sxs-lookup"><span data-stu-id="27106-225">x64</span></span> |
| <span data-ttu-id="27106-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="27106-226">openSUSE</span></span>                       | <span data-ttu-id="27106-227">15+</span><span class="sxs-lookup"><span data-stu-id="27106-227">15+</span></span>                   | <span data-ttu-id="27106-228">x64</span><span class="sxs-lookup"><span data-stu-id="27106-228">x64</span></span> |
| <span data-ttu-id="27106-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="27106-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="27106-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="27106-230">12 SP2+</span></span>               | <span data-ttu-id="27106-231">x64</span><span class="sxs-lookup"><span data-stu-id="27106-231">x64</span></span> |
| <span data-ttu-id="27106-232">Alpský Linux</span><span class="sxs-lookup"><span data-stu-id="27106-232">Alpine Linux</span></span>                   | <span data-ttu-id="27106-233">3.10+</span><span class="sxs-lookup"><span data-stu-id="27106-233">3.10+</span></span>                 | <span data-ttu-id="27106-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="27106-234">x64, ARM64</span></span> |

<span data-ttu-id="27106-235">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.1 naleznete v tématu .NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="27106-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="27106-236">Další informace o instalaci rozhraní .NET Core 3.1 na ARM64 (jádro 4.14+) najdete [v tématu Instalace rozhraní .NET Core 3.0 na Linuxarm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="27106-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27106-237">Podpora ARM64 vyžaduje linuxové jádro 4.14 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="27106-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="27106-238">Některé linuxové distribuce splňují tento požadavek, zatímco jiné ne.</span><span class="sxs-lookup"><span data-stu-id="27106-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="27106-239">Například Ubuntu 18.04 je podporováno, ale Ubuntu 16.04 není.</span><span class="sxs-lookup"><span data-stu-id="27106-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="27106-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="27106-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="27106-241">.NET Core 3.0 zachází s Linuxem jako s jediným operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="27106-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="27106-242">Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.</span><span class="sxs-lookup"><span data-stu-id="27106-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="27106-243">Rozhraní .NET Core 3.0 je podporováno v následujících linuxových distribucích/verzích:</span><span class="sxs-lookup"><span data-stu-id="27106-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="27106-244">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="27106-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="27106-245">Operační systém</span><span class="sxs-lookup"><span data-stu-id="27106-245">OS</span></span>                             | <span data-ttu-id="27106-246">Version</span><span class="sxs-lookup"><span data-stu-id="27106-246">Version</span></span>               | <span data-ttu-id="27106-247">Architektury</span><span class="sxs-lookup"><span data-stu-id="27106-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="27106-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="27106-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="27106-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="27106-249">6, 7, 8</span></span>               | <span data-ttu-id="27106-250">x64</span><span class="sxs-lookup"><span data-stu-id="27106-250">x64</span></span> |
| <span data-ttu-id="27106-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="27106-251">CentOS</span></span>                         | <span data-ttu-id="27106-252">7+</span><span class="sxs-lookup"><span data-stu-id="27106-252">7+</span></span>                    | <span data-ttu-id="27106-253">x64</span><span class="sxs-lookup"><span data-stu-id="27106-253">x64</span></span> |
| <span data-ttu-id="27106-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="27106-254">Oracle Linux</span></span>                   | <span data-ttu-id="27106-255">7+</span><span class="sxs-lookup"><span data-stu-id="27106-255">7+</span></span>                    | <span data-ttu-id="27106-256">x64</span><span class="sxs-lookup"><span data-stu-id="27106-256">x64</span></span> |
| <span data-ttu-id="27106-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="27106-257">Fedora</span></span>                         | <span data-ttu-id="27106-258">29+</span><span class="sxs-lookup"><span data-stu-id="27106-258">29+</span></span>                   | <span data-ttu-id="27106-259">x64</span><span class="sxs-lookup"><span data-stu-id="27106-259">x64</span></span> |
| <span data-ttu-id="27106-260">Debian</span><span class="sxs-lookup"><span data-stu-id="27106-260">Debian</span></span>                         | <span data-ttu-id="27106-261">9+</span><span class="sxs-lookup"><span data-stu-id="27106-261">9+</span></span>                    | <span data-ttu-id="27106-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="27106-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="27106-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="27106-263">Ubuntu</span></span>                         | <span data-ttu-id="27106-264">16.04+</span><span class="sxs-lookup"><span data-stu-id="27106-264">16.04+</span></span>                | <span data-ttu-id="27106-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="27106-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="27106-266">Linux mincovna</span><span class="sxs-lookup"><span data-stu-id="27106-266">Linux Mint</span></span>                     | <span data-ttu-id="27106-267">18+</span><span class="sxs-lookup"><span data-stu-id="27106-267">18+</span></span>                   | <span data-ttu-id="27106-268">x64</span><span class="sxs-lookup"><span data-stu-id="27106-268">x64</span></span> |
| <span data-ttu-id="27106-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="27106-269">openSUSE</span></span>                       | <span data-ttu-id="27106-270">15+</span><span class="sxs-lookup"><span data-stu-id="27106-270">15+</span></span>                   | <span data-ttu-id="27106-271">x64</span><span class="sxs-lookup"><span data-stu-id="27106-271">x64</span></span> |
| <span data-ttu-id="27106-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="27106-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="27106-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="27106-273">12 SP2+</span></span>               | <span data-ttu-id="27106-274">x64</span><span class="sxs-lookup"><span data-stu-id="27106-274">x64</span></span> |
| <span data-ttu-id="27106-275">Alpský Linux</span><span class="sxs-lookup"><span data-stu-id="27106-275">Alpine Linux</span></span>                   | <span data-ttu-id="27106-276">3.8+</span><span class="sxs-lookup"><span data-stu-id="27106-276">3.8+</span></span>                  | <span data-ttu-id="27106-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="27106-277">x64, ARM64</span></span> |

<span data-ttu-id="27106-278">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.0 naleznete v tématu .NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="27106-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="27106-279">Další informace o instalaci rozhraní .NET Core 3.0 na ARM64 naleznete [v tématu Instalace rozhraní .NET Core 3.0 na Linuxarm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="27106-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="27106-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="27106-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="27106-281">.NET Core 2.2 zachází s Linuxem jako s jediným operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="27106-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="27106-282">Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.</span><span class="sxs-lookup"><span data-stu-id="27106-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="27106-283">Rozhraní .NET Core 2.2 je podporováno v následujících linuxových distribucích/verzích:</span><span class="sxs-lookup"><span data-stu-id="27106-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="27106-284">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="27106-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="27106-285">Operační systém</span><span class="sxs-lookup"><span data-stu-id="27106-285">OS</span></span>                             |  <span data-ttu-id="27106-286">Version</span><span class="sxs-lookup"><span data-stu-id="27106-286">Version</span></span>                |  <span data-ttu-id="27106-287">Architektury</span><span class="sxs-lookup"><span data-stu-id="27106-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="27106-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="27106-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="27106-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="27106-289">6, 7</span></span>                   | <span data-ttu-id="27106-290">x64</span><span class="sxs-lookup"><span data-stu-id="27106-290">x64</span></span> |
| <span data-ttu-id="27106-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="27106-291">CentOS</span></span>                         |  <span data-ttu-id="27106-292">7</span><span class="sxs-lookup"><span data-stu-id="27106-292">7</span></span>                      | <span data-ttu-id="27106-293">x64</span><span class="sxs-lookup"><span data-stu-id="27106-293">x64</span></span> |
| <span data-ttu-id="27106-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="27106-294">Oracle Linux</span></span>                   |  <span data-ttu-id="27106-295">7</span><span class="sxs-lookup"><span data-stu-id="27106-295">7</span></span>                      | <span data-ttu-id="27106-296">x64</span><span class="sxs-lookup"><span data-stu-id="27106-296">x64</span></span> |
| <span data-ttu-id="27106-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="27106-297">Fedora</span></span>                         |  <span data-ttu-id="27106-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="27106-298">29, 30</span></span>                 | <span data-ttu-id="27106-299">x64</span><span class="sxs-lookup"><span data-stu-id="27106-299">x64</span></span> |
| <span data-ttu-id="27106-300">Debian</span><span class="sxs-lookup"><span data-stu-id="27106-300">Debian</span></span>                         |  <span data-ttu-id="27106-301">9</span><span class="sxs-lookup"><span data-stu-id="27106-301">9</span></span>                      | <span data-ttu-id="27106-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="27106-302">x64, ARM32</span></span> |
| <span data-ttu-id="27106-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="27106-303">Ubuntu</span></span>                         |  <span data-ttu-id="27106-304">16.04, 18.04, 18.10</span><span class="sxs-lookup"><span data-stu-id="27106-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="27106-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="27106-305">x64, ARM32</span></span> |
| <span data-ttu-id="27106-306">Linux mincovna</span><span class="sxs-lookup"><span data-stu-id="27106-306">Linux Mint</span></span>                     |  <span data-ttu-id="27106-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="27106-307">17, 18</span></span>                 | <span data-ttu-id="27106-308">x64</span><span class="sxs-lookup"><span data-stu-id="27106-308">x64</span></span> |
| <span data-ttu-id="27106-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="27106-309">openSUSE</span></span>                       |  <span data-ttu-id="27106-310">15+</span><span class="sxs-lookup"><span data-stu-id="27106-310">15+</span></span>                    | <span data-ttu-id="27106-311">x64</span><span class="sxs-lookup"><span data-stu-id="27106-311">x64</span></span> |
| <span data-ttu-id="27106-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="27106-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="27106-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="27106-313">12 SP2+</span></span>                | <span data-ttu-id="27106-314">x64</span><span class="sxs-lookup"><span data-stu-id="27106-314">x64</span></span> |
| <span data-ttu-id="27106-315">Alpský Linux</span><span class="sxs-lookup"><span data-stu-id="27106-315">Alpine Linux</span></span>                   |  <span data-ttu-id="27106-316">3.8+</span><span class="sxs-lookup"><span data-stu-id="27106-316">3.8+</span></span>                   | <span data-ttu-id="27106-317">x64</span><span class="sxs-lookup"><span data-stu-id="27106-317">x64</span></span> |

<span data-ttu-id="27106-318">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.2 naleznete v tématu .NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="27106-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="27106-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="27106-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="27106-320">.NET Core 2.1 zachází s Linuxem jako s jediným operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="27106-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="27106-321">Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.</span><span class="sxs-lookup"><span data-stu-id="27106-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="27106-322">.NET Core 2.1 je podporován na následujících linuxových distribucích/verzích:</span><span class="sxs-lookup"><span data-stu-id="27106-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="27106-323">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="27106-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="27106-324">Operační systém</span><span class="sxs-lookup"><span data-stu-id="27106-324">OS</span></span>                             |  <span data-ttu-id="27106-325">Version</span><span class="sxs-lookup"><span data-stu-id="27106-325">Version</span></span>                |  <span data-ttu-id="27106-326">Architektury</span><span class="sxs-lookup"><span data-stu-id="27106-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="27106-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="27106-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="27106-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="27106-328">6, 7, 8</span></span>                | <span data-ttu-id="27106-329">x64</span><span class="sxs-lookup"><span data-stu-id="27106-329">x64</span></span> |
| <span data-ttu-id="27106-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="27106-330">CentOS</span></span>                         |  <span data-ttu-id="27106-331">7+</span><span class="sxs-lookup"><span data-stu-id="27106-331">7+</span></span>                     | <span data-ttu-id="27106-332">x64</span><span class="sxs-lookup"><span data-stu-id="27106-332">x64</span></span> |
| <span data-ttu-id="27106-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="27106-333">Oracle Linux</span></span>                   |  <span data-ttu-id="27106-334">7+</span><span class="sxs-lookup"><span data-stu-id="27106-334">7+</span></span>                     | <span data-ttu-id="27106-335">x64</span><span class="sxs-lookup"><span data-stu-id="27106-335">x64</span></span> |
| <span data-ttu-id="27106-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="27106-336">Fedora</span></span>                         |  <span data-ttu-id="27106-337">29+</span><span class="sxs-lookup"><span data-stu-id="27106-337">29+</span></span>                    | <span data-ttu-id="27106-338">x64</span><span class="sxs-lookup"><span data-stu-id="27106-338">x64</span></span> |
| <span data-ttu-id="27106-339">Debian</span><span class="sxs-lookup"><span data-stu-id="27106-339">Debian</span></span>                         |  <span data-ttu-id="27106-340">9</span><span class="sxs-lookup"><span data-stu-id="27106-340">9</span></span>                      | <span data-ttu-id="27106-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="27106-341">x64, ARM32</span></span> |
| <span data-ttu-id="27106-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="27106-342">Ubuntu</span></span>                         |  <span data-ttu-id="27106-343">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="27106-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="27106-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="27106-344">x64, ARM32</span></span> |
| <span data-ttu-id="27106-345">Linux mincovna</span><span class="sxs-lookup"><span data-stu-id="27106-345">Linux Mint</span></span>                     |  <span data-ttu-id="27106-346">17+</span><span class="sxs-lookup"><span data-stu-id="27106-346">17+</span></span>                    | <span data-ttu-id="27106-347">x64</span><span class="sxs-lookup"><span data-stu-id="27106-347">x64</span></span> |
| <span data-ttu-id="27106-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="27106-348">openSUSE</span></span>                       |  <span data-ttu-id="27106-349">15+</span><span class="sxs-lookup"><span data-stu-id="27106-349">15+</span></span>                    | <span data-ttu-id="27106-350">x64</span><span class="sxs-lookup"><span data-stu-id="27106-350">x64</span></span> |
| <span data-ttu-id="27106-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="27106-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="27106-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="27106-352">12 SP2+</span></span>                | <span data-ttu-id="27106-353">x64</span><span class="sxs-lookup"><span data-stu-id="27106-353">x64</span></span> |
| <span data-ttu-id="27106-354">Alpský Linux</span><span class="sxs-lookup"><span data-stu-id="27106-354">Alpine Linux</span></span>                   |  <span data-ttu-id="27106-355">3.8+</span><span class="sxs-lookup"><span data-stu-id="27106-355">3.8+</span></span>                   | <span data-ttu-id="27106-356">x64</span><span class="sxs-lookup"><span data-stu-id="27106-356">x64</span></span> |

<span data-ttu-id="27106-357">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.1 naleznete v tématu .NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="27106-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="27106-358">Závislosti distribuce Linuxu</span><span class="sxs-lookup"><span data-stu-id="27106-358">Linux distribution dependencies</span></span>

<span data-ttu-id="27106-359">Na základě distribuce linuxu může být nutné nainstalovat další závislosti.</span><span class="sxs-lookup"><span data-stu-id="27106-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27106-360">Přesné verze a názvy se mohou mírně lišit v distribuci Linuxu.</span><span class="sxs-lookup"><span data-stu-id="27106-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="27106-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="27106-361">Ubuntu</span></span>

<span data-ttu-id="27106-362">Distribuce Ubuntu vyžadují instalaci následujících knihoven:</span><span class="sxs-lookup"><span data-stu-id="27106-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="27106-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="27106-363">liblttng-ust0</span></span>
- <span data-ttu-id="27106-364">libcurl3 (pro 14.x a 16.x)</span><span class="sxs-lookup"><span data-stu-id="27106-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="27106-365">libcurl4 (pro 18.x)</span><span class="sxs-lookup"><span data-stu-id="27106-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="27106-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="27106-366">libssl1.0.0</span></span>
- <span data-ttu-id="27106-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="27106-367">libkrb5-3</span></span>
- <span data-ttu-id="27106-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="27106-368">zlib1g</span></span>
- <span data-ttu-id="27106-369">libicu52 (pro 14.x)</span><span class="sxs-lookup"><span data-stu-id="27106-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="27106-370">libicu55 (pro 16.x)</span><span class="sxs-lookup"><span data-stu-id="27106-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="27106-371">libicu57 (pro 17.x)</span><span class="sxs-lookup"><span data-stu-id="27106-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="27106-372">libicu60 (pro 18.x)</span><span class="sxs-lookup"><span data-stu-id="27106-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="27106-373">Pro aplikace .NET Core, které používají sestavení *System.Drawing.Common,* potřebujete také následující závislost:</span><span class="sxs-lookup"><span data-stu-id="27106-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="27106-374">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="27106-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="27106-375">Většina verzí Ubuntu obsahuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="27106-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="27106-376">Můžete nainstalovat nejnovější verzi libgdiplus přidáním mono úložiště do vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="27106-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="27106-377">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="27106-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="27106-378">CentOS a Fedora</span><span class="sxs-lookup"><span data-stu-id="27106-378">CentOS and Fedora</span></span>

<span data-ttu-id="27106-379">Distribuce CentOS vyžadují nainstalovány následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="27106-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="27106-380">Lttng-ust</span><span class="sxs-lookup"><span data-stu-id="27106-380">lttng-ust</span></span>
- <span data-ttu-id="27106-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="27106-381">libcurl</span></span>
- <span data-ttu-id="27106-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="27106-382">openssl-libs</span></span>
- <span data-ttu-id="27106-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="27106-383">krb5-libs</span></span>
- <span data-ttu-id="27106-384">libicu</span><span class="sxs-lookup"><span data-stu-id="27106-384">libicu</span></span>
- <span data-ttu-id="27106-385">Zlib</span><span class="sxs-lookup"><span data-stu-id="27106-385">zlib</span></span>

<span data-ttu-id="27106-386">Uživatelé Fedory: Pokud verze vašeho OpenSSL >= 1.1, budete muset nainstalovat **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="27106-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="27106-387">Pro rozhraní .NET Core 2.0 jsou také vyžadovány následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="27106-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="27106-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="27106-388">libunwind</span></span>
- <span data-ttu-id="27106-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="27106-389">libuuid</span></span>

<span data-ttu-id="27106-390">Další informace o závislostech naleznete v [tématu Samostatné linuxové aplikace](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="27106-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="27106-391">Pro aplikace .NET Core, které používají sestavení *System.Drawing.Common,* budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="27106-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="27106-392">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="27106-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="27106-393">Většina verzí CentOS a Fedory obsahuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="27106-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="27106-394">Můžete nainstalovat nejnovější verzi libgdiplus přidáním mono úložiště do vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="27106-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="27106-395">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="27106-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="27106-396">Jádro .NET je podporováno v následujících verzích macOS:</span><span class="sxs-lookup"><span data-stu-id="27106-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="27106-397">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="27106-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="27106-398">Základní verze rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="27106-398">.NET Core Version</span></span> | <span data-ttu-id="27106-399">macOS</span><span class="sxs-lookup"><span data-stu-id="27106-399">macOS</span></span>                 | <span data-ttu-id="27106-400">Architektury</span><span class="sxs-lookup"><span data-stu-id="27106-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="27106-401">3.1</span><span class="sxs-lookup"><span data-stu-id="27106-401">3.1</span></span>               | <span data-ttu-id="27106-402">Vysoká Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="27106-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="27106-403">x64</span><span class="sxs-lookup"><span data-stu-id="27106-403">x64</span></span> | [<span data-ttu-id="27106-404">Více informací</span><span class="sxs-lookup"><span data-stu-id="27106-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="27106-405">3.0</span><span class="sxs-lookup"><span data-stu-id="27106-405">3.0</span></span>               | <span data-ttu-id="27106-406">Vysoká Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="27106-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="27106-407">x64</span><span class="sxs-lookup"><span data-stu-id="27106-407">x64</span></span> | [<span data-ttu-id="27106-408">Více informací</span><span class="sxs-lookup"><span data-stu-id="27106-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="27106-409">2,2</span><span class="sxs-lookup"><span data-stu-id="27106-409">2.2</span></span>               | <span data-ttu-id="27106-410">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="27106-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="27106-411">x64</span><span class="sxs-lookup"><span data-stu-id="27106-411">x64</span></span> | [<span data-ttu-id="27106-412">Více informací</span><span class="sxs-lookup"><span data-stu-id="27106-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="27106-413">2.1</span><span class="sxs-lookup"><span data-stu-id="27106-413">2.1</span></span>               | <span data-ttu-id="27106-414">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="27106-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="27106-415">x64</span><span class="sxs-lookup"><span data-stu-id="27106-415">x64</span></span> | [<span data-ttu-id="27106-416">Více informací</span><span class="sxs-lookup"><span data-stu-id="27106-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="27106-417">Počínaje macOS Catalina (verze 10.15), veškerý software postavený po červnu 1, 2019, který je distribuován s ID vývojáře, musí být notářsky.Rzavený až k MacS Catalina (verze 10.15), všechen software postavený po 1.</span><span class="sxs-lookup"><span data-stu-id="27106-417">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="27106-418">Tento požadavek se vztahuje na modul runtime .NET Core, sadku .NET Core SDK a software vytvořený pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="27106-418">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="27106-419">Instalační programy pro .NET Core (runtime a SDK) verze 3.1, 3.0 a 2.1 byly notářsky oznamovány od 18.</span><span class="sxs-lookup"><span data-stu-id="27106-419">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="27106-420">Předchozí vydané verze nejsou notářsky oslněny.</span><span class="sxs-lookup"><span data-stu-id="27106-420">Prior released versions aren't notarized.</span></span> <span data-ttu-id="27106-421">Pokud spustíte aplikaci, která není notářsky vedena, zobrazí se chyba podobná následujícímu obrázku:</span><span class="sxs-lookup"><span data-stu-id="27106-421">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina notářská výstraha](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="27106-423">Další informace o tom, jak vynucená notářská činnost ovlivňuje .NET Core (a vaše aplikace .NET Core), najdete v [tématu Práce s macOS Catalina Notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="27106-423">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="27106-424">libgdiplus řekl:</span><span class="sxs-lookup"><span data-stu-id="27106-424">libgdiplus</span></span>

<span data-ttu-id="27106-425">Základní aplikace .NET, které používají sestavení *System.Drawing.Common,* vyžadují instalaci libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="27106-425">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="27106-426">Snadný způsob, jak získat libgdiplus, je pomocí Správce balíčků [Homebrew ("brew")](https://brew.sh/) pro macOS.</span><span class="sxs-lookup"><span data-stu-id="27106-426">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="27106-427">Po instalaci *vařit*, nainstalujte libgdiplus provedením následujících příkazů na terminálu (příkaz) prompt:</span><span class="sxs-lookup"><span data-stu-id="27106-427">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="27106-428">Další kroky</span><span class="sxs-lookup"><span data-stu-id="27106-428">Next steps</span></span>

- <span data-ttu-id="27106-429">Chcete-li vyvíjet a spouštět aplikace, nainstalujte sadu [.NET Core SDK](sdk.md) (včetně runtime).</span><span class="sxs-lookup"><span data-stu-id="27106-429">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="27106-430">Chcete-li spustit aplikace, které vytvořili jiní uživatelé, nainstalujte [za běhu .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="27106-430">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
