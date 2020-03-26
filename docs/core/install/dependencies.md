---
title: Základní sada SDK a závislosti za běhu .NET – jádro .NET
description: Podrobnosti o předpokladech architektury operačního systému a procesoru pro instalaci sady .NET Core SDK a runtime ve Windows, Linux u macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 023b8fdf029dd6b17fe2186296d87dd7507c60b5
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546559"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="5ea4d-103">.NET Základní závislosti a požadavky</span><span class="sxs-lookup"><span data-stu-id="5ea4d-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="5ea4d-104">Tento článek podrobně popisuje, které operační systémy a architektura procesoru jsou podporovány rozhraním .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="5ea4d-105">Podporované operační systémy</span><span class="sxs-lookup"><span data-stu-id="5ea4d-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="5ea4d-106">.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="5ea4d-107">Pomocí rozhraní .NET Core 3.1 jsou podporovány následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="5ea4d-108">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5ea4d-109">Operační systém</span><span class="sxs-lookup"><span data-stu-id="5ea4d-109">OS</span></span>                            | <span data-ttu-id="5ea4d-110">Version</span><span class="sxs-lookup"><span data-stu-id="5ea4d-110">Version</span></span>                        | <span data-ttu-id="5ea4d-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="5ea4d-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5ea4d-112">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="5ea4d-112">Windows Client</span></span>                | <span data-ttu-id="5ea4d-113">7 SP1+, 8,1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5ea4d-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-114">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-115">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="5ea4d-115">Windows 10 Client</span></span>             | <span data-ttu-id="5ea4d-116">Verze 1607+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-116">Version 1607+</span></span>                  | <span data-ttu-id="5ea4d-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-117">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5ea4d-118">Windows Server</span></span>                | <span data-ttu-id="5ea4d-119">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-119">2012 R2+</span></span>                       | <span data-ttu-id="5ea4d-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-120">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5ea4d-121">Nano Server</span></span>                   | <span data-ttu-id="5ea4d-122">Verze 1803+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-122">Version 1803+</span></span>                  | <span data-ttu-id="5ea4d-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5ea4d-123">x64, ARM32</span></span>      |

<span data-ttu-id="5ea4d-124">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.1 naleznete v tématu .NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="5ea4d-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5ea4d-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="5ea4d-126">*Rozhraní .NET Core 3.0 je momentálně mimo podporu. Další informace naleznete v [zásadách základní podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="5ea4d-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="5ea4d-127">Pomocí rozhraní .NET Core 3.0 jsou podporovány následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="5ea4d-128">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5ea4d-129">Operační systém</span><span class="sxs-lookup"><span data-stu-id="5ea4d-129">OS</span></span>                            | <span data-ttu-id="5ea4d-130">Version</span><span class="sxs-lookup"><span data-stu-id="5ea4d-130">Version</span></span>                        | <span data-ttu-id="5ea4d-131">Architektury</span><span class="sxs-lookup"><span data-stu-id="5ea4d-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5ea4d-132">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="5ea4d-132">Windows Client</span></span>                | <span data-ttu-id="5ea4d-133">7 SP1+, 8,1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5ea4d-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-134">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-135">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="5ea4d-135">Windows 10 Client</span></span>             | <span data-ttu-id="5ea4d-136">Verze 1607+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-136">Version 1607+</span></span>                  | <span data-ttu-id="5ea4d-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-137">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5ea4d-138">Windows Server</span></span>                | <span data-ttu-id="5ea4d-139">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-139">2012 R2+</span></span>                       | <span data-ttu-id="5ea4d-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-140">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5ea4d-141">Nano Server</span></span>                   | <span data-ttu-id="5ea4d-142">Verze 1803+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-142">Version 1803+</span></span>                  | <span data-ttu-id="5ea4d-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5ea4d-143">x64, ARM32</span></span>      |

<span data-ttu-id="5ea4d-144">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.0 naleznete v tématu .NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="5ea4d-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5ea4d-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5ea4d-146">*Rozhraní .NET Core 2.2 je momentálně mimo podporu. Další informace naleznete v [zásadách základní podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="5ea4d-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="5ea4d-147">Pomocí rozhraní .NET Core 2.2 jsou podporovány následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="5ea4d-148">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5ea4d-149">Operační systém</span><span class="sxs-lookup"><span data-stu-id="5ea4d-149">OS</span></span>                            | <span data-ttu-id="5ea4d-150">Version</span><span class="sxs-lookup"><span data-stu-id="5ea4d-150">Version</span></span>                        | <span data-ttu-id="5ea4d-151">Architektury</span><span class="sxs-lookup"><span data-stu-id="5ea4d-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5ea4d-152">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="5ea4d-152">Windows Client</span></span>                | <span data-ttu-id="5ea4d-153">7 SP1+, 8,1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5ea4d-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-154">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-155">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="5ea4d-155">Windows 10 Client</span></span>             | <span data-ttu-id="5ea4d-156">Verze 1607+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-156">Version 1607+</span></span>                  | <span data-ttu-id="5ea4d-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-157">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5ea4d-158">Windows Server</span></span>                | <span data-ttu-id="5ea4d-159">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="5ea4d-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-160">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5ea4d-161">Nano Server</span></span>                   | <span data-ttu-id="5ea4d-162">Verze 1803+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-162">Version 1803+</span></span>                   | <span data-ttu-id="5ea4d-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5ea4d-163">x64, ARM32</span></span>      |

<span data-ttu-id="5ea4d-164">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.2 naleznete v tématu .NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="5ea4d-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5ea4d-166">Následující verze systému Windows jsou podporovány pomocí rozhraní .NET Core 2.1:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="5ea4d-167">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5ea4d-168">Operační systém</span><span class="sxs-lookup"><span data-stu-id="5ea4d-168">OS</span></span>                            | <span data-ttu-id="5ea4d-169">Version</span><span class="sxs-lookup"><span data-stu-id="5ea4d-169">Version</span></span>                        | <span data-ttu-id="5ea4d-170">Architektury</span><span class="sxs-lookup"><span data-stu-id="5ea4d-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="5ea4d-171">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="5ea4d-171">Windows Client</span></span>                | <span data-ttu-id="5ea4d-172">7 SP1+, 8,1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="5ea4d-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-173">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-174">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="5ea4d-174">Windows 10 Client</span></span>             | <span data-ttu-id="5ea4d-175">Verze 1607+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-175">Version 1607+</span></span>                  | <span data-ttu-id="5ea4d-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-176">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="5ea4d-177">Windows Server</span></span>                | <span data-ttu-id="5ea4d-178">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="5ea4d-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="5ea4d-179">x64, x86</span></span>        |
| <span data-ttu-id="5ea4d-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="5ea4d-180">Nano Server</span></span>                   | <span data-ttu-id="5ea4d-181">Verze 1803+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-181">Version 1803+</span></span>                  | <span data-ttu-id="5ea4d-182">x64,</span><span class="sxs-lookup"><span data-stu-id="5ea4d-182">x64,</span></span>            |

<span data-ttu-id="5ea4d-183">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.1 naleznete v tématu .NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="5ea4d-184">Windows 7 / Vista / 8.1 / Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="5ea4d-184">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="5ea4d-185">Další závislosti jsou vyžadovány, pokud instalujete sdsad .NET nebo runtime v následujících verzích systému Windows:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="5ea4d-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-186">Windows 7 SP1</span></span>
- <span data-ttu-id="5ea4d-187">Systém Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="5ea4d-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="5ea4d-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-188">Windows 8.1</span></span>
- <span data-ttu-id="5ea4d-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="5ea4d-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="5ea4d-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="5ea4d-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="5ea4d-191">Nainstalujte následující:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-191">Install the following:</span></span>

- <span data-ttu-id="5ea4d-192">[Redistribuovatelná aktualizace 3 aplikace Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="5ea4d-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="5ea4d-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="5ea4d-194">Výše uvedené požadavky jsou také vyžadovány, pokud narazíte na jednu z následujících chyb:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="5ea4d-195">Program nelze spustit, protože *api-ms-win-crt-runtime-l1-1-0.dll* chybí v počítači.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="5ea4d-196">Zkuste tento problém vyřešit přeinstalací programu.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="5ea4d-197">\-nebo -</span><span class="sxs-lookup"><span data-stu-id="5ea4d-197">\- or -</span></span>
>
> <span data-ttu-id="5ea4d-198">Knihovna *hostfxr.dll* byla nalezena, ale načítání z *C:\\\<path_to_app>\\hostfxr.dll* se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-198">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="5ea4d-199">.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-199">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="5ea4d-200">.NET Core 3.1 zachází s Linuxem jako s jediným operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-200">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="5ea4d-201">Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-201">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5ea4d-202">.NET Core 3.1 je podporován na následujících linuxových distribucích/verzích:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-202">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5ea4d-203">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-203">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5ea4d-204">Operační systém</span><span class="sxs-lookup"><span data-stu-id="5ea4d-204">OS</span></span>                             | <span data-ttu-id="5ea4d-205">Version</span><span class="sxs-lookup"><span data-stu-id="5ea4d-205">Version</span></span>               | <span data-ttu-id="5ea4d-206">Architektury</span><span class="sxs-lookup"><span data-stu-id="5ea4d-206">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="5ea4d-207">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-207">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="5ea4d-208">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="5ea4d-208">6, 7, 8</span></span>               | <span data-ttu-id="5ea4d-209">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-209">x64</span></span> |
| <span data-ttu-id="5ea4d-210">CentOS</span><span class="sxs-lookup"><span data-stu-id="5ea4d-210">CentOS</span></span>                         | <span data-ttu-id="5ea4d-211">7+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-211">7+</span></span>                    | <span data-ttu-id="5ea4d-212">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-212">x64</span></span> |
| <span data-ttu-id="5ea4d-213">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-213">Oracle Linux</span></span>                   | <span data-ttu-id="5ea4d-214">7+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-214">7+</span></span>                    | <span data-ttu-id="5ea4d-215">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-215">x64</span></span> |
| <span data-ttu-id="5ea4d-216">Fedora</span><span class="sxs-lookup"><span data-stu-id="5ea4d-216">Fedora</span></span>                         | <span data-ttu-id="5ea4d-217">30+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-217">30+</span></span>                   | <span data-ttu-id="5ea4d-218">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-218">x64</span></span> |
| <span data-ttu-id="5ea4d-219">Debian</span><span class="sxs-lookup"><span data-stu-id="5ea4d-219">Debian</span></span>                         | <span data-ttu-id="5ea4d-220">9+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-220">9+</span></span>                    | <span data-ttu-id="5ea4d-221">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-221">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="5ea4d-222">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5ea4d-222">Ubuntu</span></span>                         | <span data-ttu-id="5ea4d-223">16.04+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-223">16.04+</span></span>                | <span data-ttu-id="5ea4d-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="5ea4d-225">Linux mincovna</span><span class="sxs-lookup"><span data-stu-id="5ea4d-225">Linux Mint</span></span>                     | <span data-ttu-id="5ea4d-226">18+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-226">18+</span></span>                   | <span data-ttu-id="5ea4d-227">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-227">x64</span></span> |
| <span data-ttu-id="5ea4d-228">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5ea4d-228">openSUSE</span></span>                       | <span data-ttu-id="5ea4d-229">15+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-229">15+</span></span>                   | <span data-ttu-id="5ea4d-230">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-230">x64</span></span> |
| <span data-ttu-id="5ea4d-231">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-231">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="5ea4d-232">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-232">12 SP2+</span></span>               | <span data-ttu-id="5ea4d-233">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-233">x64</span></span> |
| <span data-ttu-id="5ea4d-234">Alpský Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-234">Alpine Linux</span></span>                   | <span data-ttu-id="5ea4d-235">3.10+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-235">3.10+</span></span>                 | <span data-ttu-id="5ea4d-236">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-236">x64, ARM64</span></span> |

<span data-ttu-id="5ea4d-237">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.1 naleznete v tématu .NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-237">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="5ea4d-238">Další informace o instalaci rozhraní .NET Core 3.1 na ARM64 (jádro 4.14+) najdete [v tématu Instalace rozhraní .NET Core 3.0 na Linuxarm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-238">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ea4d-239">Podpora ARM64 vyžaduje linuxové jádro 4.14 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-239">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="5ea4d-240">Některé linuxové distribuce splňují tento požadavek, zatímco jiné ne.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-240">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="5ea4d-241">Například Ubuntu 18.04 je podporováno, ale Ubuntu 16.04 není.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-241">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="5ea4d-242">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5ea4d-242">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="5ea4d-243">*Rozhraní .NET Core 3.0 je momentálně mimo podporu. Další informace naleznete v [zásadách základní podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="5ea4d-243">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="5ea4d-244">.NET Core 3.0 zachází s Linuxem jako s jediným operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-244">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="5ea4d-245">Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-245">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5ea4d-246">Rozhraní .NET Core 3.0 je podporováno v následujících linuxových distribucích/verzích:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-246">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5ea4d-247">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-247">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5ea4d-248">Operační systém</span><span class="sxs-lookup"><span data-stu-id="5ea4d-248">OS</span></span>                             | <span data-ttu-id="5ea4d-249">Version</span><span class="sxs-lookup"><span data-stu-id="5ea4d-249">Version</span></span>               | <span data-ttu-id="5ea4d-250">Architektury</span><span class="sxs-lookup"><span data-stu-id="5ea4d-250">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="5ea4d-251">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-251">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="5ea4d-252">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="5ea4d-252">6, 7, 8</span></span>               | <span data-ttu-id="5ea4d-253">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-253">x64</span></span> |
| <span data-ttu-id="5ea4d-254">CentOS</span><span class="sxs-lookup"><span data-stu-id="5ea4d-254">CentOS</span></span>                         | <span data-ttu-id="5ea4d-255">7+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-255">7+</span></span>                    | <span data-ttu-id="5ea4d-256">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-256">x64</span></span> |
| <span data-ttu-id="5ea4d-257">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-257">Oracle Linux</span></span>                   | <span data-ttu-id="5ea4d-258">7+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-258">7+</span></span>                    | <span data-ttu-id="5ea4d-259">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-259">x64</span></span> |
| <span data-ttu-id="5ea4d-260">Fedora</span><span class="sxs-lookup"><span data-stu-id="5ea4d-260">Fedora</span></span>                         | <span data-ttu-id="5ea4d-261">29+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-261">29+</span></span>                   | <span data-ttu-id="5ea4d-262">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-262">x64</span></span> |
| <span data-ttu-id="5ea4d-263">Debian</span><span class="sxs-lookup"><span data-stu-id="5ea4d-263">Debian</span></span>                         | <span data-ttu-id="5ea4d-264">9+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-264">9+</span></span>                    | <span data-ttu-id="5ea4d-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="5ea4d-266">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5ea4d-266">Ubuntu</span></span>                         | <span data-ttu-id="5ea4d-267">16.04+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-267">16.04+</span></span>                | <span data-ttu-id="5ea4d-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="5ea4d-269">Linux mincovna</span><span class="sxs-lookup"><span data-stu-id="5ea4d-269">Linux Mint</span></span>                     | <span data-ttu-id="5ea4d-270">18+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-270">18+</span></span>                   | <span data-ttu-id="5ea4d-271">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-271">x64</span></span> |
| <span data-ttu-id="5ea4d-272">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5ea4d-272">openSUSE</span></span>                       | <span data-ttu-id="5ea4d-273">15+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-273">15+</span></span>                   | <span data-ttu-id="5ea4d-274">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-274">x64</span></span> |
| <span data-ttu-id="5ea4d-275">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-275">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="5ea4d-276">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-276">12 SP2+</span></span>               | <span data-ttu-id="5ea4d-277">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-277">x64</span></span> |
| <span data-ttu-id="5ea4d-278">Alpský Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-278">Alpine Linux</span></span>                   | <span data-ttu-id="5ea4d-279">3.8+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-279">3.8+</span></span>                  | <span data-ttu-id="5ea4d-280">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-280">x64, ARM64</span></span> |

<span data-ttu-id="5ea4d-281">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.0 naleznete v tématu .NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-281">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="5ea4d-282">Další informace o instalaci rozhraní .NET Core 3.0 na ARM64 naleznete [v tématu Instalace rozhraní .NET Core 3.0 na Linuxarm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-282">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="5ea4d-283">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="5ea4d-283">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="5ea4d-284">*Rozhraní .NET Core 2.2 je momentálně mimo podporu. Další informace naleznete v [zásadách základní podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="5ea4d-284">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="5ea4d-285">.NET Core 2.2 zachází s Linuxem jako s jediným operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-285">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="5ea4d-286">Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-286">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5ea4d-287">Rozhraní .NET Core 2.2 je podporováno v následujících linuxových distribucích/verzích:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-287">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5ea4d-288">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-288">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5ea4d-289">Operační systém</span><span class="sxs-lookup"><span data-stu-id="5ea4d-289">OS</span></span>                             |  <span data-ttu-id="5ea4d-290">Version</span><span class="sxs-lookup"><span data-stu-id="5ea4d-290">Version</span></span>                |  <span data-ttu-id="5ea4d-291">Architektury</span><span class="sxs-lookup"><span data-stu-id="5ea4d-291">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="5ea4d-292">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-292">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="5ea4d-293">6, 7</span><span class="sxs-lookup"><span data-stu-id="5ea4d-293">6, 7</span></span>                   | <span data-ttu-id="5ea4d-294">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-294">x64</span></span> |
| <span data-ttu-id="5ea4d-295">CentOS</span><span class="sxs-lookup"><span data-stu-id="5ea4d-295">CentOS</span></span>                         |  <span data-ttu-id="5ea4d-296">7</span><span class="sxs-lookup"><span data-stu-id="5ea4d-296">7</span></span>                      | <span data-ttu-id="5ea4d-297">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-297">x64</span></span> |
| <span data-ttu-id="5ea4d-298">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-298">Oracle Linux</span></span>                   |  <span data-ttu-id="5ea4d-299">7</span><span class="sxs-lookup"><span data-stu-id="5ea4d-299">7</span></span>                      | <span data-ttu-id="5ea4d-300">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-300">x64</span></span> |
| <span data-ttu-id="5ea4d-301">Fedora</span><span class="sxs-lookup"><span data-stu-id="5ea4d-301">Fedora</span></span>                         |  <span data-ttu-id="5ea4d-302">29, 30</span><span class="sxs-lookup"><span data-stu-id="5ea4d-302">29, 30</span></span>                 | <span data-ttu-id="5ea4d-303">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-303">x64</span></span> |
| <span data-ttu-id="5ea4d-304">Debian</span><span class="sxs-lookup"><span data-stu-id="5ea4d-304">Debian</span></span>                         |  <span data-ttu-id="5ea4d-305">9</span><span class="sxs-lookup"><span data-stu-id="5ea4d-305">9</span></span>                      | <span data-ttu-id="5ea4d-306">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5ea4d-306">x64, ARM32</span></span> |
| <span data-ttu-id="5ea4d-307">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5ea4d-307">Ubuntu</span></span>                         |  <span data-ttu-id="5ea4d-308">16.04, 18.04, 18.10</span><span class="sxs-lookup"><span data-stu-id="5ea4d-308">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="5ea4d-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5ea4d-309">x64, ARM32</span></span> |
| <span data-ttu-id="5ea4d-310">Linux mincovna</span><span class="sxs-lookup"><span data-stu-id="5ea4d-310">Linux Mint</span></span>                     |  <span data-ttu-id="5ea4d-311">17, 18</span><span class="sxs-lookup"><span data-stu-id="5ea4d-311">17, 18</span></span>                 | <span data-ttu-id="5ea4d-312">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-312">x64</span></span> |
| <span data-ttu-id="5ea4d-313">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5ea4d-313">openSUSE</span></span>                       |  <span data-ttu-id="5ea4d-314">15+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-314">15+</span></span>                    | <span data-ttu-id="5ea4d-315">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-315">x64</span></span> |
| <span data-ttu-id="5ea4d-316">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-316">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="5ea4d-317">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-317">12 SP2+</span></span>                | <span data-ttu-id="5ea4d-318">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-318">x64</span></span> |
| <span data-ttu-id="5ea4d-319">Alpský Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-319">Alpine Linux</span></span>                   |  <span data-ttu-id="5ea4d-320">3.8+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-320">3.8+</span></span>                   | <span data-ttu-id="5ea4d-321">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-321">x64</span></span> |

<span data-ttu-id="5ea4d-322">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.2 naleznete v tématu .NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-322">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="5ea4d-323">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-323">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="5ea4d-324">.NET Core 2.1 zachází s Linuxem jako s jediným operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-324">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="5ea4d-325">Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-325">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="5ea4d-326">.NET Core 2.1 je podporován na následujících linuxových distribucích/verzích:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-326">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="5ea4d-327">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-327">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5ea4d-328">Operační systém</span><span class="sxs-lookup"><span data-stu-id="5ea4d-328">OS</span></span>                             |  <span data-ttu-id="5ea4d-329">Version</span><span class="sxs-lookup"><span data-stu-id="5ea4d-329">Version</span></span>                |  <span data-ttu-id="5ea4d-330">Architektury</span><span class="sxs-lookup"><span data-stu-id="5ea4d-330">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="5ea4d-331">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-331">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="5ea4d-332">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="5ea4d-332">6, 7, 8</span></span>                | <span data-ttu-id="5ea4d-333">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-333">x64</span></span> |
| <span data-ttu-id="5ea4d-334">CentOS</span><span class="sxs-lookup"><span data-stu-id="5ea4d-334">CentOS</span></span>                         |  <span data-ttu-id="5ea4d-335">7+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-335">7+</span></span>                     | <span data-ttu-id="5ea4d-336">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-336">x64</span></span> |
| <span data-ttu-id="5ea4d-337">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-337">Oracle Linux</span></span>                   |  <span data-ttu-id="5ea4d-338">7+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-338">7+</span></span>                     | <span data-ttu-id="5ea4d-339">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-339">x64</span></span> |
| <span data-ttu-id="5ea4d-340">Fedora</span><span class="sxs-lookup"><span data-stu-id="5ea4d-340">Fedora</span></span>                         |  <span data-ttu-id="5ea4d-341">30+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-341">30+</span></span>                    | <span data-ttu-id="5ea4d-342">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-342">x64</span></span> |
| <span data-ttu-id="5ea4d-343">Debian</span><span class="sxs-lookup"><span data-stu-id="5ea4d-343">Debian</span></span>                         |  <span data-ttu-id="5ea4d-344">9</span><span class="sxs-lookup"><span data-stu-id="5ea4d-344">9</span></span>                      | <span data-ttu-id="5ea4d-345">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5ea4d-345">x64, ARM32</span></span> |
| <span data-ttu-id="5ea4d-346">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5ea4d-346">Ubuntu</span></span>                         |  <span data-ttu-id="5ea4d-347">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="5ea4d-347">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="5ea4d-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="5ea4d-348">x64, ARM32</span></span> |
| <span data-ttu-id="5ea4d-349">Linux mincovna</span><span class="sxs-lookup"><span data-stu-id="5ea4d-349">Linux Mint</span></span>                     |  <span data-ttu-id="5ea4d-350">17+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-350">17+</span></span>                    | <span data-ttu-id="5ea4d-351">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-351">x64</span></span> |
| <span data-ttu-id="5ea4d-352">openSUSE</span><span class="sxs-lookup"><span data-stu-id="5ea4d-352">openSUSE</span></span>                       |  <span data-ttu-id="5ea4d-353">15+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-353">15+</span></span>                    | <span data-ttu-id="5ea4d-354">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-354">x64</span></span> |
| <span data-ttu-id="5ea4d-355">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-355">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="5ea4d-356">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-356">12 SP2+</span></span>                | <span data-ttu-id="5ea4d-357">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-357">x64</span></span> |
| <span data-ttu-id="5ea4d-358">Alpský Linux</span><span class="sxs-lookup"><span data-stu-id="5ea4d-358">Alpine Linux</span></span>                   |  <span data-ttu-id="5ea4d-359">3.8+</span><span class="sxs-lookup"><span data-stu-id="5ea4d-359">3.8+</span></span>                   | <span data-ttu-id="5ea4d-360">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-360">x64</span></span> |

<span data-ttu-id="5ea4d-361">Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.1 naleznete v tématu .NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-361">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="5ea4d-362">Závislosti distribuce Linuxu</span><span class="sxs-lookup"><span data-stu-id="5ea4d-362">Linux distribution dependencies</span></span>

<span data-ttu-id="5ea4d-363">Na základě distribuce linuxu může být nutné nainstalovat další závislosti.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-363">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ea4d-364">Přesné verze a názvy se mohou mírně lišit v distribuci Linuxu.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-364">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="5ea4d-365">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="5ea4d-365">Ubuntu</span></span>

<span data-ttu-id="5ea4d-366">Distribuce Ubuntu vyžadují instalaci následujících knihoven:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-366">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="5ea4d-367">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="5ea4d-367">liblttng-ust0</span></span>
- <span data-ttu-id="5ea4d-368">libcurl3 (pro 14.x a 16.x)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-368">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="5ea4d-369">libcurl4 (pro 18.x)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-369">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="5ea4d-370">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="5ea4d-370">libssl1.0.0</span></span>
- <span data-ttu-id="5ea4d-371">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="5ea4d-371">libkrb5-3</span></span>
- <span data-ttu-id="5ea4d-372">zlib1g</span><span class="sxs-lookup"><span data-stu-id="5ea4d-372">zlib1g</span></span>
- <span data-ttu-id="5ea4d-373">libicu52 (pro 14.x)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-373">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="5ea4d-374">libicu55 (pro 16.x)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-374">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="5ea4d-375">libicu57 (pro 17.x)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-375">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="5ea4d-376">libicu60 (pro 18.x)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-376">libicu60 (for 18.x)</span></span>

<span data-ttu-id="5ea4d-377">Pro aplikace .NET Core, které používají sestavení *System.Drawing.Common,* potřebujete také následující závislost:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-377">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="5ea4d-378">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-378">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="5ea4d-379">Většina verzí Ubuntu obsahuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-379">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="5ea4d-380">Můžete nainstalovat nejnovější verzi libgdiplus přidáním mono úložiště do vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-380">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="5ea4d-381">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-381">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="5ea4d-382">CentOS a Fedora</span><span class="sxs-lookup"><span data-stu-id="5ea4d-382">CentOS and Fedora</span></span>

<span data-ttu-id="5ea4d-383">Distribuce CentOS vyžadují nainstalovány následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-383">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="5ea4d-384">Lttng-ust</span><span class="sxs-lookup"><span data-stu-id="5ea4d-384">lttng-ust</span></span>
- <span data-ttu-id="5ea4d-385">libcurl</span><span class="sxs-lookup"><span data-stu-id="5ea4d-385">libcurl</span></span>
- <span data-ttu-id="5ea4d-386">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="5ea4d-386">openssl-libs</span></span>
- <span data-ttu-id="5ea4d-387">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="5ea4d-387">krb5-libs</span></span>
- <span data-ttu-id="5ea4d-388">libicu</span><span class="sxs-lookup"><span data-stu-id="5ea4d-388">libicu</span></span>
- <span data-ttu-id="5ea4d-389">Zlib</span><span class="sxs-lookup"><span data-stu-id="5ea4d-389">zlib</span></span>

<span data-ttu-id="5ea4d-390">Uživatelé Fedory: Pokud verze vašeho OpenSSL >= 1.1, budete muset nainstalovat **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-390">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="5ea4d-391">Pro rozhraní .NET Core 2.0 jsou také vyžadovány následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-391">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="5ea4d-392">libunwind</span><span class="sxs-lookup"><span data-stu-id="5ea4d-392">libunwind</span></span>
- <span data-ttu-id="5ea4d-393">libuuid</span><span class="sxs-lookup"><span data-stu-id="5ea4d-393">libuuid</span></span>

<span data-ttu-id="5ea4d-394">Další informace o závislostech naleznete v [tématu Samostatné linuxové aplikace](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-394">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="5ea4d-395">Pro aplikace .NET Core, které používají sestavení *System.Drawing.Common,* budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-395">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="5ea4d-396">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-396">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="5ea4d-397">Většina verzí CentOS a Fedory obsahuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-397">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="5ea4d-398">Můžete nainstalovat nejnovější verzi libgdiplus přidáním mono úložiště do vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-398">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="5ea4d-399">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-399">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="5ea4d-400">Jádro .NET je podporováno v následujících verzích macOS:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-400">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="5ea4d-401">Symbol `+` představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-401">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="5ea4d-402">Základní verze rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="5ea4d-402">.NET Core Version</span></span> | <span data-ttu-id="5ea4d-403">macOS</span><span class="sxs-lookup"><span data-stu-id="5ea4d-403">macOS</span></span>                 | <span data-ttu-id="5ea4d-404">Architektury</span><span class="sxs-lookup"><span data-stu-id="5ea4d-404">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="5ea4d-405">3.1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-405">3.1</span></span>               | <span data-ttu-id="5ea4d-406">Vysoká Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="5ea4d-407">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-407">x64</span></span> | [<span data-ttu-id="5ea4d-408">Více informací</span><span class="sxs-lookup"><span data-stu-id="5ea4d-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="5ea4d-409">3.0</span><span class="sxs-lookup"><span data-stu-id="5ea4d-409">3.0</span></span>               | <span data-ttu-id="5ea4d-410">Vysoká Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-410">High Sierra (10.13+)</span></span>  | <span data-ttu-id="5ea4d-411">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-411">x64</span></span> | [<span data-ttu-id="5ea4d-412">Více informací</span><span class="sxs-lookup"><span data-stu-id="5ea4d-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="5ea4d-413">2,2</span><span class="sxs-lookup"><span data-stu-id="5ea4d-413">2.2</span></span>               | <span data-ttu-id="5ea4d-414">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="5ea4d-415">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-415">x64</span></span> | [<span data-ttu-id="5ea4d-416">Více informací</span><span class="sxs-lookup"><span data-stu-id="5ea4d-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="5ea4d-417">2.1</span><span class="sxs-lookup"><span data-stu-id="5ea4d-417">2.1</span></span>               | <span data-ttu-id="5ea4d-418">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="5ea4d-418">Sierra (10.12+)</span></span>       | <span data-ttu-id="5ea4d-419">x64</span><span class="sxs-lookup"><span data-stu-id="5ea4d-419">x64</span></span> | [<span data-ttu-id="5ea4d-420">Více informací</span><span class="sxs-lookup"><span data-stu-id="5ea4d-420">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="5ea4d-421">Počínaje macOS Catalina (verze 10.15), veškerý software postavený po červnu 1, 2019, který je distribuován s ID vývojáře, musí být notářsky.Rzavený až k MacS Catalina (verze 10.15), všechen software postavený po 1.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-421">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="5ea4d-422">Tento požadavek se vztahuje na modul runtime .NET Core, sadku .NET Core SDK a software vytvořený pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-422">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="5ea4d-423">Instalační programy pro .NET Core (runtime a SDK) verze 3.1, 3.0 a 2.1 byly notářsky oznamovány od 18.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-423">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="5ea4d-424">Předchozí vydané verze nejsou notářsky oslněny.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-424">Prior released versions aren't notarized.</span></span> <span data-ttu-id="5ea4d-425">Pokud spustíte aplikaci, která není notářsky vedena, zobrazí se chyba podobná následujícímu obrázku:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-425">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina notářská výstraha](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="5ea4d-427">Další informace o tom, jak vynucená notářská činnost ovlivňuje .NET Core (a vaše aplikace .NET Core), najdete v [tématu Práce s macOS Catalina Notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-427">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="5ea4d-428">libgdiplus řekl:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-428">libgdiplus</span></span>

<span data-ttu-id="5ea4d-429">Základní aplikace .NET, které používají sestavení *System.Drawing.Common,* vyžadují instalaci libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-429">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="5ea4d-430">Snadný způsob, jak získat libgdiplus, je pomocí Správce balíčků [Homebrew ("brew")](https://brew.sh/) pro macOS.</span><span class="sxs-lookup"><span data-stu-id="5ea4d-430">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="5ea4d-431">Po instalaci *vařit*, nainstalujte libgdiplus provedením následujících příkazů na terminálu (příkaz) prompt:</span><span class="sxs-lookup"><span data-stu-id="5ea4d-431">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="5ea4d-432">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5ea4d-432">Next steps</span></span>

- <span data-ttu-id="5ea4d-433">Chcete-li vyvíjet a spouštět aplikace, nainstalujte sadu [.NET Core SDK](sdk.md) (včetně runtime).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-433">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="5ea4d-434">Chcete-li spustit aplikace, které vytvořili jiní uživatelé, nainstalujte [za běhu .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="5ea4d-434">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
