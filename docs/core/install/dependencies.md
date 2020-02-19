---
title: Závislosti .NET Core SDK a modulu runtime – .NET Core
description: Podrobně popisuje operační systém a požadavky na architekturu procesoru pro instalaci .NET Core SDK a modulu runtime v systémech Windows, Linux a macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 4164ea5a04d80ab20109168a225b793b02ee616a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448890"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="721f1-103">Závislosti a požadavky .NET Core</span><span class="sxs-lookup"><span data-stu-id="721f1-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="721f1-104">Tento článek podrobně popisuje, které operační systémy a architektura procesoru jsou podporovány rozhraním .NET Core.</span><span class="sxs-lookup"><span data-stu-id="721f1-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="721f1-105">Podporované operační systémy</span><span class="sxs-lookup"><span data-stu-id="721f1-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="721f1-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="721f1-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="721f1-107">Rozhraní .NET Core 3,1 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="721f1-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="721f1-108">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="721f1-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="721f1-109">Operační systém</span><span class="sxs-lookup"><span data-stu-id="721f1-109">OS</span></span>                            | <span data-ttu-id="721f1-110">Verze</span><span class="sxs-lookup"><span data-stu-id="721f1-110">Version</span></span>                        | <span data-ttu-id="721f1-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="721f1-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="721f1-112">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="721f1-112">Windows Client</span></span>                | <span data-ttu-id="721f1-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="721f1-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="721f1-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-114">x64, x86</span></span>        |
| <span data-ttu-id="721f1-115">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="721f1-115">Windows 10 Client</span></span>             | <span data-ttu-id="721f1-116">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="721f1-116">Version 1607+</span></span>                  | <span data-ttu-id="721f1-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-117">x64, x86</span></span>        |
| <span data-ttu-id="721f1-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="721f1-118">Windows Server</span></span>                | <span data-ttu-id="721f1-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="721f1-119">2012 R2+</span></span>                       | <span data-ttu-id="721f1-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-120">x64, x86</span></span>        |
| <span data-ttu-id="721f1-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="721f1-121">Nano Server</span></span>                   | <span data-ttu-id="721f1-122">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="721f1-122">Version 1803+</span></span>                  | <span data-ttu-id="721f1-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="721f1-123">x64, ARM32</span></span>      |

<span data-ttu-id="721f1-124">Další informace o podporovaných operačních systémech .NET Core 3,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="721f1-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="721f1-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="721f1-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="721f1-126">Rozhraní .NET Core 3,0 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="721f1-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="721f1-127">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="721f1-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="721f1-128">Operační systém</span><span class="sxs-lookup"><span data-stu-id="721f1-128">OS</span></span>                            | <span data-ttu-id="721f1-129">Verze</span><span class="sxs-lookup"><span data-stu-id="721f1-129">Version</span></span>                        | <span data-ttu-id="721f1-130">Architektury</span><span class="sxs-lookup"><span data-stu-id="721f1-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="721f1-131">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="721f1-131">Windows Client</span></span>                | <span data-ttu-id="721f1-132">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="721f1-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="721f1-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-133">x64, x86</span></span>        |
| <span data-ttu-id="721f1-134">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="721f1-134">Windows 10 Client</span></span>             | <span data-ttu-id="721f1-135">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="721f1-135">Version 1607+</span></span>                  | <span data-ttu-id="721f1-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-136">x64, x86</span></span>        |
| <span data-ttu-id="721f1-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="721f1-137">Windows Server</span></span>                | <span data-ttu-id="721f1-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="721f1-138">2012 R2+</span></span>                       | <span data-ttu-id="721f1-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-139">x64, x86</span></span>        |
| <span data-ttu-id="721f1-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="721f1-140">Nano Server</span></span>                   | <span data-ttu-id="721f1-141">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="721f1-141">Version 1803+</span></span>                  | <span data-ttu-id="721f1-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="721f1-142">x64, ARM32</span></span>      |

<span data-ttu-id="721f1-143">Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="721f1-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="721f1-144">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="721f1-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="721f1-145">Rozhraní .NET Core 2,2 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="721f1-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="721f1-146">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="721f1-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="721f1-147">Operační systém</span><span class="sxs-lookup"><span data-stu-id="721f1-147">OS</span></span>                            | <span data-ttu-id="721f1-148">Verze</span><span class="sxs-lookup"><span data-stu-id="721f1-148">Version</span></span>                        | <span data-ttu-id="721f1-149">Architektury</span><span class="sxs-lookup"><span data-stu-id="721f1-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="721f1-150">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="721f1-150">Windows Client</span></span>                | <span data-ttu-id="721f1-151">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="721f1-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="721f1-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-152">x64, x86</span></span>        |
| <span data-ttu-id="721f1-153">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="721f1-153">Windows 10 Client</span></span>             | <span data-ttu-id="721f1-154">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="721f1-154">Version 1607+</span></span>                  | <span data-ttu-id="721f1-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-155">x64, x86</span></span>        |
| <span data-ttu-id="721f1-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="721f1-156">Windows Server</span></span>                | <span data-ttu-id="721f1-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="721f1-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="721f1-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-158">x64, x86</span></span>        |
| <span data-ttu-id="721f1-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="721f1-159">Nano Server</span></span>                   | <span data-ttu-id="721f1-160">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="721f1-160">Version 1803+</span></span>                   | <span data-ttu-id="721f1-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="721f1-161">x64, ARM32</span></span>      |

<span data-ttu-id="721f1-162">Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="721f1-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="721f1-163">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="721f1-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="721f1-164">Rozhraní .NET Core 2,1 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="721f1-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="721f1-165">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="721f1-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="721f1-166">Operační systém</span><span class="sxs-lookup"><span data-stu-id="721f1-166">OS</span></span>                            | <span data-ttu-id="721f1-167">Verze</span><span class="sxs-lookup"><span data-stu-id="721f1-167">Version</span></span>                        | <span data-ttu-id="721f1-168">Architektury</span><span class="sxs-lookup"><span data-stu-id="721f1-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="721f1-169">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="721f1-169">Windows Client</span></span>                | <span data-ttu-id="721f1-170">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="721f1-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="721f1-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-171">x64, x86</span></span>        |
| <span data-ttu-id="721f1-172">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="721f1-172">Windows 10 Client</span></span>             | <span data-ttu-id="721f1-173">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="721f1-173">Version 1607+</span></span>                  | <span data-ttu-id="721f1-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-174">x64, x86</span></span>        |
| <span data-ttu-id="721f1-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="721f1-175">Windows Server</span></span>                | <span data-ttu-id="721f1-176">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="721f1-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="721f1-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="721f1-177">x64, x86</span></span>        |
| <span data-ttu-id="721f1-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="721f1-178">Nano Server</span></span>                   | <span data-ttu-id="721f1-179">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="721f1-179">Version 1803+</span></span>                  | <span data-ttu-id="721f1-180">platformě</span><span class="sxs-lookup"><span data-stu-id="721f1-180">x64,</span></span>            |

<span data-ttu-id="721f1-181">Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="721f1-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="721f1-182">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="721f1-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="721f1-183">Pokud instalujete sadu .NET SDK nebo modul runtime v následujících verzích systému Windows, jsou vyžadovány další závislosti:</span><span class="sxs-lookup"><span data-stu-id="721f1-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="721f1-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="721f1-184">Windows 7 SP1</span></span>
- <span data-ttu-id="721f1-185">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="721f1-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="721f1-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="721f1-186">Windows 8.1</span></span>
- <span data-ttu-id="721f1-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="721f1-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="721f1-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="721f1-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="721f1-189">Nainstalujte následující:</span><span class="sxs-lookup"><span data-stu-id="721f1-189">Install the following:</span></span>

- <span data-ttu-id="721f1-190">[Distribuovatelné C++ součásti Microsoft Visual 2015 Update 3](https://www.microsoft.com/download/details.aspx?id=52685)</span><span class="sxs-lookup"><span data-stu-id="721f1-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="721f1-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="721f1-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="721f1-192">Výše uvedené požadavky se vyžadují také v případě, že dojde k jedné z následujících chyb:</span><span class="sxs-lookup"><span data-stu-id="721f1-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="721f1-193">Program nelze spustit, protože v počítači chybí *rozhraní API-MS-Win-CRT-runtime-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="721f1-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="721f1-194">Zkuste tento problém vyřešit tak, že znovu nainstalujete program.</span><span class="sxs-lookup"><span data-stu-id="721f1-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="721f1-195">\- nebo-</span><span class="sxs-lookup"><span data-stu-id="721f1-195">\- or -</span></span>
>
> <span data-ttu-id="721f1-196">Knihovna *hostfxr. dll* byla nalezena, ale byla načtena z *C:\\\<path_to_app >\\hostfxr. dll* se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="721f1-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="721f1-197">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="721f1-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="721f1-198">.NET Core 3,1 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="721f1-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="721f1-199">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="721f1-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="721f1-200">.NET Core 3,1 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="721f1-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="721f1-201">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="721f1-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="721f1-202">Operační systém</span><span class="sxs-lookup"><span data-stu-id="721f1-202">OS</span></span>                             | <span data-ttu-id="721f1-203">Verze</span><span class="sxs-lookup"><span data-stu-id="721f1-203">Version</span></span>               | <span data-ttu-id="721f1-204">Architektury</span><span class="sxs-lookup"><span data-stu-id="721f1-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="721f1-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="721f1-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="721f1-206">6, 7, 8</span></span>               | <span data-ttu-id="721f1-207">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-207">x64</span></span> |
| <span data-ttu-id="721f1-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="721f1-208">CentOS</span></span>                         | <span data-ttu-id="721f1-209">7 +</span><span class="sxs-lookup"><span data-stu-id="721f1-209">7+</span></span>                    | <span data-ttu-id="721f1-210">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-210">x64</span></span> |
| <span data-ttu-id="721f1-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-211">Oracle Linux</span></span>                   | <span data-ttu-id="721f1-212">7 +</span><span class="sxs-lookup"><span data-stu-id="721f1-212">7+</span></span>                    | <span data-ttu-id="721f1-213">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-213">x64</span></span> |
| <span data-ttu-id="721f1-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="721f1-214">Fedora</span></span>                         | <span data-ttu-id="721f1-215">29 +</span><span class="sxs-lookup"><span data-stu-id="721f1-215">29+</span></span>                   | <span data-ttu-id="721f1-216">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-216">x64</span></span> |
| <span data-ttu-id="721f1-217">Debian</span><span class="sxs-lookup"><span data-stu-id="721f1-217">Debian</span></span>                         | <span data-ttu-id="721f1-218">9 +</span><span class="sxs-lookup"><span data-stu-id="721f1-218">9+</span></span>                    | <span data-ttu-id="721f1-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="721f1-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="721f1-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="721f1-220">Ubuntu</span></span>                         | <span data-ttu-id="721f1-221">16.04 +</span><span class="sxs-lookup"><span data-stu-id="721f1-221">16.04+</span></span>                | <span data-ttu-id="721f1-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="721f1-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="721f1-223">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="721f1-223">Linux Mint</span></span>                     | <span data-ttu-id="721f1-224">18 +</span><span class="sxs-lookup"><span data-stu-id="721f1-224">18+</span></span>                   | <span data-ttu-id="721f1-225">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-225">x64</span></span> |
| <span data-ttu-id="721f1-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="721f1-226">openSUSE</span></span>                       | <span data-ttu-id="721f1-227">15 +</span><span class="sxs-lookup"><span data-stu-id="721f1-227">15+</span></span>                   | <span data-ttu-id="721f1-228">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-228">x64</span></span> |
| <span data-ttu-id="721f1-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="721f1-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="721f1-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="721f1-230">12 SP2+</span></span>               | <span data-ttu-id="721f1-231">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-231">x64</span></span> |
| <span data-ttu-id="721f1-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-232">Alpine Linux</span></span>                   | <span data-ttu-id="721f1-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="721f1-233">3.10+</span></span>                 | <span data-ttu-id="721f1-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="721f1-234">x64, ARM64</span></span> |

<span data-ttu-id="721f1-235">Další informace o podporovaných operačních systémech .NET Core 3,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="721f1-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="721f1-236">Další informace o tom, jak nainstalovat .NET Core 3,1 na ARM64 (kernel 4.14 +), najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="721f1-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="721f1-237">Podpora ARM64 vyžaduje Linux kernel 4,14 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="721f1-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="721f1-238">Některé distribuce systému Linux tento požadavek splňují, i když jiné ne.</span><span class="sxs-lookup"><span data-stu-id="721f1-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="721f1-239">Například Ubuntu 18,04 je podporován, ale Ubuntu 16,04 ne.</span><span class="sxs-lookup"><span data-stu-id="721f1-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="721f1-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="721f1-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="721f1-241">.NET Core 3,0 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="721f1-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="721f1-242">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="721f1-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="721f1-243">.NET Core 3,0 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="721f1-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="721f1-244">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="721f1-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="721f1-245">Operační systém</span><span class="sxs-lookup"><span data-stu-id="721f1-245">OS</span></span>                             | <span data-ttu-id="721f1-246">Verze</span><span class="sxs-lookup"><span data-stu-id="721f1-246">Version</span></span>               | <span data-ttu-id="721f1-247">Architektury</span><span class="sxs-lookup"><span data-stu-id="721f1-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="721f1-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="721f1-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="721f1-249">6, 7, 8</span></span>               | <span data-ttu-id="721f1-250">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-250">x64</span></span> |
| <span data-ttu-id="721f1-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="721f1-251">CentOS</span></span>                         | <span data-ttu-id="721f1-252">7 +</span><span class="sxs-lookup"><span data-stu-id="721f1-252">7+</span></span>                    | <span data-ttu-id="721f1-253">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-253">x64</span></span> |
| <span data-ttu-id="721f1-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-254">Oracle Linux</span></span>                   | <span data-ttu-id="721f1-255">7 +</span><span class="sxs-lookup"><span data-stu-id="721f1-255">7+</span></span>                    | <span data-ttu-id="721f1-256">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-256">x64</span></span> |
| <span data-ttu-id="721f1-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="721f1-257">Fedora</span></span>                         | <span data-ttu-id="721f1-258">29 +</span><span class="sxs-lookup"><span data-stu-id="721f1-258">29+</span></span>                   | <span data-ttu-id="721f1-259">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-259">x64</span></span> |
| <span data-ttu-id="721f1-260">Debian</span><span class="sxs-lookup"><span data-stu-id="721f1-260">Debian</span></span>                         | <span data-ttu-id="721f1-261">9 +</span><span class="sxs-lookup"><span data-stu-id="721f1-261">9+</span></span>                    | <span data-ttu-id="721f1-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="721f1-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="721f1-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="721f1-263">Ubuntu</span></span>                         | <span data-ttu-id="721f1-264">16.04 +</span><span class="sxs-lookup"><span data-stu-id="721f1-264">16.04+</span></span>                | <span data-ttu-id="721f1-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="721f1-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="721f1-266">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="721f1-266">Linux Mint</span></span>                     | <span data-ttu-id="721f1-267">18 +</span><span class="sxs-lookup"><span data-stu-id="721f1-267">18+</span></span>                   | <span data-ttu-id="721f1-268">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-268">x64</span></span> |
| <span data-ttu-id="721f1-269">openSUSE</span><span class="sxs-lookup"><span data-stu-id="721f1-269">openSUSE</span></span>                       | <span data-ttu-id="721f1-270">15 +</span><span class="sxs-lookup"><span data-stu-id="721f1-270">15+</span></span>                   | <span data-ttu-id="721f1-271">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-271">x64</span></span> |
| <span data-ttu-id="721f1-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="721f1-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="721f1-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="721f1-273">12 SP2+</span></span>               | <span data-ttu-id="721f1-274">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-274">x64</span></span> |
| <span data-ttu-id="721f1-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-275">Alpine Linux</span></span>                   | <span data-ttu-id="721f1-276">3.8 +</span><span class="sxs-lookup"><span data-stu-id="721f1-276">3.8+</span></span>                  | <span data-ttu-id="721f1-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="721f1-277">x64, ARM64</span></span> |

<span data-ttu-id="721f1-278">Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="721f1-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="721f1-279">Další informace o tom, jak nainstalovat .NET Core 3,0 na ARM64, najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="721f1-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="721f1-280">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="721f1-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="721f1-281">.NET Core 2,2 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="721f1-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="721f1-282">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="721f1-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="721f1-283">.NET Core 2,2 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="721f1-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="721f1-284">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="721f1-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="721f1-285">Operační systém</span><span class="sxs-lookup"><span data-stu-id="721f1-285">OS</span></span>                             |  <span data-ttu-id="721f1-286">Verze</span><span class="sxs-lookup"><span data-stu-id="721f1-286">Version</span></span>                |  <span data-ttu-id="721f1-287">Architektury</span><span class="sxs-lookup"><span data-stu-id="721f1-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="721f1-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="721f1-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="721f1-289">6, 7</span></span>                   | <span data-ttu-id="721f1-290">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-290">x64</span></span> |
| <span data-ttu-id="721f1-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="721f1-291">CentOS</span></span>                         |  <span data-ttu-id="721f1-292">7</span><span class="sxs-lookup"><span data-stu-id="721f1-292">7</span></span>                      | <span data-ttu-id="721f1-293">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-293">x64</span></span> |
| <span data-ttu-id="721f1-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-294">Oracle Linux</span></span>                   |  <span data-ttu-id="721f1-295">7</span><span class="sxs-lookup"><span data-stu-id="721f1-295">7</span></span>                      | <span data-ttu-id="721f1-296">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-296">x64</span></span> |
| <span data-ttu-id="721f1-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="721f1-297">Fedora</span></span>                         |  <span data-ttu-id="721f1-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="721f1-298">29, 30</span></span>                 | <span data-ttu-id="721f1-299">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-299">x64</span></span> |
| <span data-ttu-id="721f1-300">Debian</span><span class="sxs-lookup"><span data-stu-id="721f1-300">Debian</span></span>                         |  <span data-ttu-id="721f1-301">9</span><span class="sxs-lookup"><span data-stu-id="721f1-301">9</span></span>                      | <span data-ttu-id="721f1-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="721f1-302">x64, ARM32</span></span> |
| <span data-ttu-id="721f1-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="721f1-303">Ubuntu</span></span>                         |  <span data-ttu-id="721f1-304">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="721f1-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="721f1-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="721f1-305">x64, ARM32</span></span> |
| <span data-ttu-id="721f1-306">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="721f1-306">Linux Mint</span></span>                     |  <span data-ttu-id="721f1-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="721f1-307">17, 18</span></span>                 | <span data-ttu-id="721f1-308">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-308">x64</span></span> |
| <span data-ttu-id="721f1-309">openSUSE</span><span class="sxs-lookup"><span data-stu-id="721f1-309">openSUSE</span></span>                       |  <span data-ttu-id="721f1-310">15 +</span><span class="sxs-lookup"><span data-stu-id="721f1-310">15+</span></span>                    | <span data-ttu-id="721f1-311">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-311">x64</span></span> |
| <span data-ttu-id="721f1-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="721f1-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="721f1-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="721f1-313">12 SP2+</span></span>                | <span data-ttu-id="721f1-314">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-314">x64</span></span> |
| <span data-ttu-id="721f1-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-315">Alpine Linux</span></span>                   |  <span data-ttu-id="721f1-316">3.8 +</span><span class="sxs-lookup"><span data-stu-id="721f1-316">3.8+</span></span>                   | <span data-ttu-id="721f1-317">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-317">x64</span></span> |

<span data-ttu-id="721f1-318">Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="721f1-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="721f1-319">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="721f1-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="721f1-320">.NET Core 2,1 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="721f1-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="721f1-321">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="721f1-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="721f1-322">.NET Core 2,1 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="721f1-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="721f1-323">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="721f1-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="721f1-324">Operační systém</span><span class="sxs-lookup"><span data-stu-id="721f1-324">OS</span></span>                             |  <span data-ttu-id="721f1-325">Verze</span><span class="sxs-lookup"><span data-stu-id="721f1-325">Version</span></span>                |  <span data-ttu-id="721f1-326">Architektury</span><span class="sxs-lookup"><span data-stu-id="721f1-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="721f1-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="721f1-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="721f1-328">6, 7, 8</span></span>                | <span data-ttu-id="721f1-329">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-329">x64</span></span> |
| <span data-ttu-id="721f1-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="721f1-330">CentOS</span></span>                         |  <span data-ttu-id="721f1-331">7 +</span><span class="sxs-lookup"><span data-stu-id="721f1-331">7+</span></span>                     | <span data-ttu-id="721f1-332">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-332">x64</span></span> |
| <span data-ttu-id="721f1-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-333">Oracle Linux</span></span>                   |  <span data-ttu-id="721f1-334">7 +</span><span class="sxs-lookup"><span data-stu-id="721f1-334">7+</span></span>                     | <span data-ttu-id="721f1-335">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-335">x64</span></span> |
| <span data-ttu-id="721f1-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="721f1-336">Fedora</span></span>                         |  <span data-ttu-id="721f1-337">29 +</span><span class="sxs-lookup"><span data-stu-id="721f1-337">29+</span></span>                    | <span data-ttu-id="721f1-338">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-338">x64</span></span> |
| <span data-ttu-id="721f1-339">Debian</span><span class="sxs-lookup"><span data-stu-id="721f1-339">Debian</span></span>                         |  <span data-ttu-id="721f1-340">9</span><span class="sxs-lookup"><span data-stu-id="721f1-340">9</span></span>                      | <span data-ttu-id="721f1-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="721f1-341">x64, ARM32</span></span> |
| <span data-ttu-id="721f1-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="721f1-342">Ubuntu</span></span>                         |  <span data-ttu-id="721f1-343">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="721f1-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="721f1-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="721f1-344">x64, ARM32</span></span> |
| <span data-ttu-id="721f1-345">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="721f1-345">Linux Mint</span></span>                     |  <span data-ttu-id="721f1-346">17 +</span><span class="sxs-lookup"><span data-stu-id="721f1-346">17+</span></span>                    | <span data-ttu-id="721f1-347">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-347">x64</span></span> |
| <span data-ttu-id="721f1-348">openSUSE</span><span class="sxs-lookup"><span data-stu-id="721f1-348">openSUSE</span></span>                       |  <span data-ttu-id="721f1-349">15 +</span><span class="sxs-lookup"><span data-stu-id="721f1-349">15+</span></span>                    | <span data-ttu-id="721f1-350">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-350">x64</span></span> |
| <span data-ttu-id="721f1-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="721f1-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="721f1-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="721f1-352">12 SP2+</span></span>                | <span data-ttu-id="721f1-353">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-353">x64</span></span> |
| <span data-ttu-id="721f1-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-354">Alpine Linux</span></span>                   |  <span data-ttu-id="721f1-355">3.8 +</span><span class="sxs-lookup"><span data-stu-id="721f1-355">3.8+</span></span>                   | <span data-ttu-id="721f1-356">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-356">x64</span></span> |

<span data-ttu-id="721f1-357">Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="721f1-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="721f1-358">Závislosti distribuce systému Linux</span><span class="sxs-lookup"><span data-stu-id="721f1-358">Linux distribution dependencies</span></span>

<span data-ttu-id="721f1-359">Na základě distribuce systému Linux bude pravděpodobně nutné nainstalovat další závislosti.</span><span class="sxs-lookup"><span data-stu-id="721f1-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="721f1-360">Přesné verze a názvy se mohou mírně lišit podle vaší možnosti rozšíření pro Linux.</span><span class="sxs-lookup"><span data-stu-id="721f1-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="721f1-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="721f1-361">Ubuntu</span></span>

<span data-ttu-id="721f1-362">Ubuntu distribuce vyžadují, aby byly nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="721f1-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="721f1-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="721f1-363">liblttng-ust0</span></span>
- <span data-ttu-id="721f1-364">libcurl3 (pro 14. x a 16. x)</span><span class="sxs-lookup"><span data-stu-id="721f1-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="721f1-365">libcurl4 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="721f1-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="721f1-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="721f1-366">libssl1.0.0</span></span>
- <span data-ttu-id="721f1-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="721f1-367">libkrb5-3</span></span>
- <span data-ttu-id="721f1-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="721f1-368">zlib1g</span></span>
- <span data-ttu-id="721f1-369">libicu52 (pro 14. x)</span><span class="sxs-lookup"><span data-stu-id="721f1-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="721f1-370">libicu55 (pro 16. x)</span><span class="sxs-lookup"><span data-stu-id="721f1-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="721f1-371">libicu57 (pro 17. x)</span><span class="sxs-lookup"><span data-stu-id="721f1-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="721f1-372">libicu60 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="721f1-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="721f1-373">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:</span><span class="sxs-lookup"><span data-stu-id="721f1-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="721f1-374">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="721f1-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="721f1-375">Většina verzí Ubuntu zahrnuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="721f1-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="721f1-376">Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="721f1-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="721f1-377">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="721f1-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="721f1-378">CentOS a Fedora</span><span class="sxs-lookup"><span data-stu-id="721f1-378">CentOS and Fedora</span></span>

<span data-ttu-id="721f1-379">CentOS distribuce vyžadují následující nainstalované knihovny:</span><span class="sxs-lookup"><span data-stu-id="721f1-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="721f1-380">lttng – tým UST</span><span class="sxs-lookup"><span data-stu-id="721f1-380">lttng-ust</span></span>
- <span data-ttu-id="721f1-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="721f1-381">libcurl</span></span>
- <span data-ttu-id="721f1-382">OpenSSL – knihovny</span><span class="sxs-lookup"><span data-stu-id="721f1-382">openssl-libs</span></span>
- <span data-ttu-id="721f1-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="721f1-383">krb5-libs</span></span>
- <span data-ttu-id="721f1-384">libicu</span><span class="sxs-lookup"><span data-stu-id="721f1-384">libicu</span></span>
- <span data-ttu-id="721f1-385">ZLIB</span><span class="sxs-lookup"><span data-stu-id="721f1-385">zlib</span></span>

<span data-ttu-id="721f1-386">Fedora uživatelé: Pokud verze vašeho OpenSSLu je > = 1,1, budete muset nainstalovat **kompatibilní s openssl10**.</span><span class="sxs-lookup"><span data-stu-id="721f1-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="721f1-387">Pro .NET Core 2,0 jsou potřeba taky následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="721f1-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="721f1-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="721f1-388">libunwind</span></span>
- <span data-ttu-id="721f1-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="721f1-389">libuuid</span></span>

<span data-ttu-id="721f1-390">Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="721f1-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="721f1-391">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="721f1-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="721f1-392">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="721f1-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="721f1-393">Většina verzí CentOS a Fedora zahrnuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="721f1-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="721f1-394">Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="721f1-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="721f1-395">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="721f1-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="721f1-396">Rozhraní .NET Core je podporované v následujících verzích macOS:</span><span class="sxs-lookup"><span data-stu-id="721f1-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="721f1-397">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="721f1-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="721f1-398">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="721f1-398">.NET Core Version</span></span> | <span data-ttu-id="721f1-399">macOS</span><span class="sxs-lookup"><span data-stu-id="721f1-399">macOS</span></span>                 | <span data-ttu-id="721f1-400">Architektury</span><span class="sxs-lookup"><span data-stu-id="721f1-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="721f1-401">3.1</span><span class="sxs-lookup"><span data-stu-id="721f1-401">3.1</span></span>               | <span data-ttu-id="721f1-402">Velký Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="721f1-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="721f1-403">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-403">x64</span></span> | [<span data-ttu-id="721f1-404">Další informace</span><span class="sxs-lookup"><span data-stu-id="721f1-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="721f1-405">3.0</span><span class="sxs-lookup"><span data-stu-id="721f1-405">3.0</span></span>               | <span data-ttu-id="721f1-406">Velký Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="721f1-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="721f1-407">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-407">x64</span></span> | [<span data-ttu-id="721f1-408">Další informace</span><span class="sxs-lookup"><span data-stu-id="721f1-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="721f1-409">2.2</span><span class="sxs-lookup"><span data-stu-id="721f1-409">2.2</span></span>               | <span data-ttu-id="721f1-410">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="721f1-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="721f1-411">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-411">x64</span></span> | [<span data-ttu-id="721f1-412">Další informace</span><span class="sxs-lookup"><span data-stu-id="721f1-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="721f1-413">2.1</span><span class="sxs-lookup"><span data-stu-id="721f1-413">2.1</span></span>               | <span data-ttu-id="721f1-414">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="721f1-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="721f1-415">x64</span><span class="sxs-lookup"><span data-stu-id="721f1-415">x64</span></span> | [<span data-ttu-id="721f1-416">Další informace</span><span class="sxs-lookup"><span data-stu-id="721f1-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="721f1-417">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="721f1-417">libgdiplus</span></span>

<span data-ttu-id="721f1-418">Aplikace .NET Core, které používají *System. Drawing. Common* Assembly, vyžadují, aby bylo možné nainstalovat libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="721f1-418">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="721f1-419">Snadný způsob, jak získat libgdiplus, je použít Správce balíčků [homebrew ("Brew")](https://brew.sh/) pro MacOS.</span><span class="sxs-lookup"><span data-stu-id="721f1-419">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="721f1-420">Po instalaci *Brew*nainstalujte libgdiplus spuštěním následujících příkazů na příkazovém řádku terminálu (Command):</span><span class="sxs-lookup"><span data-stu-id="721f1-420">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="721f1-421">Další kroky</span><span class="sxs-lookup"><span data-stu-id="721f1-421">Next steps</span></span>

- <span data-ttu-id="721f1-422">Pro vývoj a spouštění aplikací nainstalujte [.NET Core SDK](sdk.md) (zahrnuje modul runtime).</span><span class="sxs-lookup"><span data-stu-id="721f1-422">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="721f1-423">Pokud chcete spouštět aplikace, které vytvořili jiní uživatelé, nainstalujte [modul runtime .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="721f1-423">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
