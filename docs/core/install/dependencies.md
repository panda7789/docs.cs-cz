---
title: Závislosti .NET Core SDK a modulu runtime – .NET Core
description: Podrobně popisuje operační systém a požadavky na architekturu procesoru pro instalaci .NET Core SDK a modulu runtime v systémech Windows, Linux a macOS.
author: leecow
ms.author: leecow
ms.date: 06/01/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 81f6ab436428d71f71d9fd0f560bd2b0512a519b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590757"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="453a6-103">Závislosti a požadavky .NET Core</span><span class="sxs-lookup"><span data-stu-id="453a6-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="453a6-104">Tento článek podrobně popisuje, které operační systémy a architektura procesoru jsou podporovány rozhraním .NET Core.</span><span class="sxs-lookup"><span data-stu-id="453a6-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="453a6-105">Podporované operační systémy</span><span class="sxs-lookup"><span data-stu-id="453a6-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="453a6-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="453a6-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="453a6-107">Rozhraní .NET Core 3,1 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="453a6-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="453a6-108">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="453a6-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="453a6-109">Operační systém</span><span class="sxs-lookup"><span data-stu-id="453a6-109">OS</span></span>                            | <span data-ttu-id="453a6-110">Verze</span><span class="sxs-lookup"><span data-stu-id="453a6-110">Version</span></span>                        | <span data-ttu-id="453a6-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="453a6-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="453a6-112">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="453a6-112">Windows Client</span></span>                | <span data-ttu-id="453a6-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="453a6-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="453a6-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-114">x64, x86</span></span>        |
| <span data-ttu-id="453a6-115">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="453a6-115">Windows 10 Client</span></span>             | <span data-ttu-id="453a6-116">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="453a6-116">Version 1607+</span></span>                  | <span data-ttu-id="453a6-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-117">x64, x86</span></span>        |
| <span data-ttu-id="453a6-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="453a6-118">Windows Server</span></span>                | <span data-ttu-id="453a6-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="453a6-119">2012 R2+</span></span>                       | <span data-ttu-id="453a6-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-120">x64, x86</span></span>        |
| <span data-ttu-id="453a6-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="453a6-121">Nano Server</span></span>                   | <span data-ttu-id="453a6-122">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="453a6-122">Version 1803+</span></span>                  | <span data-ttu-id="453a6-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="453a6-123">x64, ARM32</span></span>      |

<span data-ttu-id="453a6-124">Další informace o podporovaných operačních systémech .NET Core 3,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="453a6-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="453a6-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="453a6-126">*.NET Core 3,0 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="453a6-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="453a6-127">Rozhraní .NET Core 3,0 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="453a6-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="453a6-128">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="453a6-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="453a6-129">Operační systém</span><span class="sxs-lookup"><span data-stu-id="453a6-129">OS</span></span>                            | <span data-ttu-id="453a6-130">Verze</span><span class="sxs-lookup"><span data-stu-id="453a6-130">Version</span></span>                        | <span data-ttu-id="453a6-131">Architektury</span><span class="sxs-lookup"><span data-stu-id="453a6-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="453a6-132">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="453a6-132">Windows Client</span></span>                | <span data-ttu-id="453a6-133">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="453a6-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="453a6-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-134">x64, x86</span></span>        |
| <span data-ttu-id="453a6-135">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="453a6-135">Windows 10 Client</span></span>             | <span data-ttu-id="453a6-136">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="453a6-136">Version 1607+</span></span>                  | <span data-ttu-id="453a6-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-137">x64, x86</span></span>        |
| <span data-ttu-id="453a6-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="453a6-138">Windows Server</span></span>                | <span data-ttu-id="453a6-139">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="453a6-139">2012 R2+</span></span>                       | <span data-ttu-id="453a6-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-140">x64, x86</span></span>        |
| <span data-ttu-id="453a6-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="453a6-141">Nano Server</span></span>                   | <span data-ttu-id="453a6-142">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="453a6-142">Version 1803+</span></span>                  | <span data-ttu-id="453a6-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="453a6-143">x64, ARM32</span></span>      |

<span data-ttu-id="453a6-144">Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="453a6-145">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="453a6-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="453a6-146">*.NET Core 2,2 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="453a6-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="453a6-147">Rozhraní .NET Core 2,2 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="453a6-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="453a6-148">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="453a6-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="453a6-149">Operační systém</span><span class="sxs-lookup"><span data-stu-id="453a6-149">OS</span></span>                            | <span data-ttu-id="453a6-150">Verze</span><span class="sxs-lookup"><span data-stu-id="453a6-150">Version</span></span>                        | <span data-ttu-id="453a6-151">Architektury</span><span class="sxs-lookup"><span data-stu-id="453a6-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="453a6-152">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="453a6-152">Windows Client</span></span>                | <span data-ttu-id="453a6-153">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="453a6-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="453a6-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-154">x64, x86</span></span>        |
| <span data-ttu-id="453a6-155">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="453a6-155">Windows 10 Client</span></span>             | <span data-ttu-id="453a6-156">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="453a6-156">Version 1607+</span></span>                  | <span data-ttu-id="453a6-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-157">x64, x86</span></span>        |
| <span data-ttu-id="453a6-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="453a6-158">Windows Server</span></span>                | <span data-ttu-id="453a6-159">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="453a6-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="453a6-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-160">x64, x86</span></span>        |
| <span data-ttu-id="453a6-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="453a6-161">Nano Server</span></span>                   | <span data-ttu-id="453a6-162">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="453a6-162">Version 1803+</span></span>                   | <span data-ttu-id="453a6-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="453a6-163">x64, ARM32</span></span>      |

<span data-ttu-id="453a6-164">Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="453a6-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="453a6-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="453a6-166">Rozhraní .NET Core 2,1 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="453a6-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="453a6-167">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="453a6-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="453a6-168">Operační systém</span><span class="sxs-lookup"><span data-stu-id="453a6-168">OS</span></span>                            | <span data-ttu-id="453a6-169">Verze</span><span class="sxs-lookup"><span data-stu-id="453a6-169">Version</span></span>                        | <span data-ttu-id="453a6-170">Architektury</span><span class="sxs-lookup"><span data-stu-id="453a6-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="453a6-171">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="453a6-171">Windows Client</span></span>                | <span data-ttu-id="453a6-172">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="453a6-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="453a6-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-173">x64, x86</span></span>        |
| <span data-ttu-id="453a6-174">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="453a6-174">Windows 10 Client</span></span>             | <span data-ttu-id="453a6-175">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="453a6-175">Version 1607+</span></span>                  | <span data-ttu-id="453a6-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-176">x64, x86</span></span>        |
| <span data-ttu-id="453a6-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="453a6-177">Windows Server</span></span>                | <span data-ttu-id="453a6-178">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="453a6-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="453a6-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="453a6-179">x64, x86</span></span>        |
| <span data-ttu-id="453a6-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="453a6-180">Nano Server</span></span>                   | <span data-ttu-id="453a6-181">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="453a6-181">Version 1803+</span></span>                  | <span data-ttu-id="453a6-182">platformě</span><span class="sxs-lookup"><span data-stu-id="453a6-182">x64,</span></span>            |

<span data-ttu-id="453a6-183">Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="453a6-184">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="453a6-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="453a6-185">Pokud instalujete sadu .NET SDK nebo modul runtime v následujících verzích systému Windows, jsou vyžadovány další závislosti:</span><span class="sxs-lookup"><span data-stu-id="453a6-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="453a6-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="453a6-186">Windows 7 SP1</span></span>
- <span data-ttu-id="453a6-187">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="453a6-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="453a6-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="453a6-188">Windows 8.1</span></span>
- <span data-ttu-id="453a6-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="453a6-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="453a6-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="453a6-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="453a6-191">Nainstalujte následující:</span><span class="sxs-lookup"><span data-stu-id="453a6-191">Install the following:</span></span>

- <span data-ttu-id="453a6-192">[Microsoft Visual C++ 2015 Distribuovatelný Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="453a6-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="453a6-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="453a6-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="453a6-194">Výše uvedené požadavky se vyžadují také v případě, že dojde k jedné z následujících chyb:</span><span class="sxs-lookup"><span data-stu-id="453a6-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="453a6-195">Program nelze spustit, protože v počítači chybí *rozhraní API-MS-Win-CRT-runtime-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="453a6-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="453a6-196">Zkuste tento problém vyřešit tak, že znovu nainstalujete program.</span><span class="sxs-lookup"><span data-stu-id="453a6-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="453a6-197">\-ani</span><span class="sxs-lookup"><span data-stu-id="453a6-197">\- or -</span></span>
>
> <span data-ttu-id="453a6-198">Program nelze spustit, protože v počítači chybí *rozhraní API-MS-Win-cor-TimeZone-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="453a6-198">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="453a6-199">Zkuste tento problém vyřešit tak, že znovu nainstalujete program.</span><span class="sxs-lookup"><span data-stu-id="453a6-199">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="453a6-200">\-ani</span><span class="sxs-lookup"><span data-stu-id="453a6-200">\- or -</span></span>
>
> <span data-ttu-id="453a6-201">Knihovna *hostfxr. dll* byla nalezena, ale načtení z *jazyka C: \\ \<path_to_app> \\ hostfxr. dll* se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="453a6-201">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="453a6-202">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="453a6-202">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="453a6-203">.NET Core 3,1 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="453a6-203">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="453a6-204">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="453a6-204">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="453a6-205">.NET Core 3,1 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="453a6-205">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="453a6-206">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="453a6-206">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="453a6-207">Operační systém</span><span class="sxs-lookup"><span data-stu-id="453a6-207">OS</span></span>                             | <span data-ttu-id="453a6-208">Verze</span><span class="sxs-lookup"><span data-stu-id="453a6-208">Version</span></span>               | <span data-ttu-id="453a6-209">Architektury</span><span class="sxs-lookup"><span data-stu-id="453a6-209">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="453a6-210">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-210">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="453a6-211">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="453a6-211">6, 7, 8</span></span>               | <span data-ttu-id="453a6-212">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-212">x64</span></span> |
| <span data-ttu-id="453a6-213">CentOS</span><span class="sxs-lookup"><span data-stu-id="453a6-213">CentOS</span></span>                         | <span data-ttu-id="453a6-214">7 +</span><span class="sxs-lookup"><span data-stu-id="453a6-214">7+</span></span>                    | <span data-ttu-id="453a6-215">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-215">x64</span></span> |
| <span data-ttu-id="453a6-216">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-216">Oracle Linux</span></span>                   | <span data-ttu-id="453a6-217">7 +</span><span class="sxs-lookup"><span data-stu-id="453a6-217">7+</span></span>                    | <span data-ttu-id="453a6-218">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-218">x64</span></span> |
| <span data-ttu-id="453a6-219">Fedora</span><span class="sxs-lookup"><span data-stu-id="453a6-219">Fedora</span></span>                         | <span data-ttu-id="453a6-220">30 +</span><span class="sxs-lookup"><span data-stu-id="453a6-220">30+</span></span>                   | <span data-ttu-id="453a6-221">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-221">x64</span></span> |
| <span data-ttu-id="453a6-222">Debian</span><span class="sxs-lookup"><span data-stu-id="453a6-222">Debian</span></span>                         | <span data-ttu-id="453a6-223">9 +</span><span class="sxs-lookup"><span data-stu-id="453a6-223">9+</span></span>                    | <span data-ttu-id="453a6-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="453a6-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="453a6-225">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="453a6-225">Ubuntu</span></span>                         | <span data-ttu-id="453a6-226">16.04 +</span><span class="sxs-lookup"><span data-stu-id="453a6-226">16.04+</span></span>                | <span data-ttu-id="453a6-227">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="453a6-227">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="453a6-228">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="453a6-228">Linux Mint</span></span>                     | <span data-ttu-id="453a6-229">18 +</span><span class="sxs-lookup"><span data-stu-id="453a6-229">18+</span></span>                   | <span data-ttu-id="453a6-230">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-230">x64</span></span> |
| <span data-ttu-id="453a6-231">openSUSE</span><span class="sxs-lookup"><span data-stu-id="453a6-231">openSUSE</span></span>                       | <span data-ttu-id="453a6-232">15 +</span><span class="sxs-lookup"><span data-stu-id="453a6-232">15+</span></span>                   | <span data-ttu-id="453a6-233">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-233">x64</span></span> |
| <span data-ttu-id="453a6-234">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="453a6-234">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="453a6-235">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="453a6-235">12 SP2+</span></span>               | <span data-ttu-id="453a6-236">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-236">x64</span></span> |
| <span data-ttu-id="453a6-237">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-237">Alpine Linux</span></span>                   | <span data-ttu-id="453a6-238">3.10 +</span><span class="sxs-lookup"><span data-stu-id="453a6-238">3.10+</span></span>                 | <span data-ttu-id="453a6-239">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="453a6-239">x64, ARM64</span></span> |

<span data-ttu-id="453a6-240">Další informace o podporovaných operačních systémech .NET Core 3,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-240">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="453a6-241">Další informace o tom, jak nainstalovat .NET Core 3,1 na ARM64 (kernel 4.14 +), najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="453a6-241">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="453a6-242">Podpora ARM64 vyžaduje Linux kernel 4,14 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="453a6-242">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="453a6-243">Některé distribuce systému Linux tento požadavek splňují, i když jiné ne.</span><span class="sxs-lookup"><span data-stu-id="453a6-243">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="453a6-244">Například Ubuntu 18,04 je podporován, ale Ubuntu 16,04 ne.</span><span class="sxs-lookup"><span data-stu-id="453a6-244">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="453a6-245">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="453a6-245">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="453a6-246">*.NET Core 3,0 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="453a6-246">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="453a6-247">.NET Core 3,0 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="453a6-247">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="453a6-248">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="453a6-248">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="453a6-249">.NET Core 3,0 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="453a6-249">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="453a6-250">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="453a6-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="453a6-251">Operační systém</span><span class="sxs-lookup"><span data-stu-id="453a6-251">OS</span></span>                             | <span data-ttu-id="453a6-252">Verze</span><span class="sxs-lookup"><span data-stu-id="453a6-252">Version</span></span>               | <span data-ttu-id="453a6-253">Architektury</span><span class="sxs-lookup"><span data-stu-id="453a6-253">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="453a6-254">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-254">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="453a6-255">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="453a6-255">6, 7, 8</span></span>               | <span data-ttu-id="453a6-256">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-256">x64</span></span> |
| <span data-ttu-id="453a6-257">CentOS</span><span class="sxs-lookup"><span data-stu-id="453a6-257">CentOS</span></span>                         | <span data-ttu-id="453a6-258">7 +</span><span class="sxs-lookup"><span data-stu-id="453a6-258">7+</span></span>                    | <span data-ttu-id="453a6-259">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-259">x64</span></span> |
| <span data-ttu-id="453a6-260">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-260">Oracle Linux</span></span>                   | <span data-ttu-id="453a6-261">7 +</span><span class="sxs-lookup"><span data-stu-id="453a6-261">7+</span></span>                    | <span data-ttu-id="453a6-262">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-262">x64</span></span> |
| <span data-ttu-id="453a6-263">Fedora</span><span class="sxs-lookup"><span data-stu-id="453a6-263">Fedora</span></span>                         | <span data-ttu-id="453a6-264">29 +</span><span class="sxs-lookup"><span data-stu-id="453a6-264">29+</span></span>                   | <span data-ttu-id="453a6-265">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-265">x64</span></span> |
| <span data-ttu-id="453a6-266">Debian</span><span class="sxs-lookup"><span data-stu-id="453a6-266">Debian</span></span>                         | <span data-ttu-id="453a6-267">9 +</span><span class="sxs-lookup"><span data-stu-id="453a6-267">9+</span></span>                    | <span data-ttu-id="453a6-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="453a6-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="453a6-269">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="453a6-269">Ubuntu</span></span>                         | <span data-ttu-id="453a6-270">16.04 +</span><span class="sxs-lookup"><span data-stu-id="453a6-270">16.04+</span></span>                | <span data-ttu-id="453a6-271">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="453a6-271">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="453a6-272">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="453a6-272">Linux Mint</span></span>                     | <span data-ttu-id="453a6-273">18 +</span><span class="sxs-lookup"><span data-stu-id="453a6-273">18+</span></span>                   | <span data-ttu-id="453a6-274">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-274">x64</span></span> |
| <span data-ttu-id="453a6-275">openSUSE</span><span class="sxs-lookup"><span data-stu-id="453a6-275">openSUSE</span></span>                       | <span data-ttu-id="453a6-276">15 +</span><span class="sxs-lookup"><span data-stu-id="453a6-276">15+</span></span>                   | <span data-ttu-id="453a6-277">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-277">x64</span></span> |
| <span data-ttu-id="453a6-278">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="453a6-278">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="453a6-279">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="453a6-279">12 SP2+</span></span>               | <span data-ttu-id="453a6-280">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-280">x64</span></span> |
| <span data-ttu-id="453a6-281">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-281">Alpine Linux</span></span>                   | <span data-ttu-id="453a6-282">3.8 +</span><span class="sxs-lookup"><span data-stu-id="453a6-282">3.8+</span></span>                  | <span data-ttu-id="453a6-283">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="453a6-283">x64, ARM64</span></span> |

<span data-ttu-id="453a6-284">Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-284">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="453a6-285">Další informace o tom, jak nainstalovat .NET Core 3,0 na ARM64, najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="453a6-285">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="453a6-286">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="453a6-286">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="453a6-287">*.NET Core 2,2 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="453a6-287">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="453a6-288">.NET Core 2,2 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="453a6-288">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="453a6-289">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="453a6-289">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="453a6-290">.NET Core 2,2 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="453a6-290">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="453a6-291">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="453a6-291">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="453a6-292">Operační systém</span><span class="sxs-lookup"><span data-stu-id="453a6-292">OS</span></span>                             |  <span data-ttu-id="453a6-293">Verze</span><span class="sxs-lookup"><span data-stu-id="453a6-293">Version</span></span>                |  <span data-ttu-id="453a6-294">Architektury</span><span class="sxs-lookup"><span data-stu-id="453a6-294">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="453a6-295">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-295">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="453a6-296">6, 7</span><span class="sxs-lookup"><span data-stu-id="453a6-296">6, 7</span></span>                   | <span data-ttu-id="453a6-297">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-297">x64</span></span> |
| <span data-ttu-id="453a6-298">CentOS</span><span class="sxs-lookup"><span data-stu-id="453a6-298">CentOS</span></span>                         |  <span data-ttu-id="453a6-299">7</span><span class="sxs-lookup"><span data-stu-id="453a6-299">7</span></span>                      | <span data-ttu-id="453a6-300">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-300">x64</span></span> |
| <span data-ttu-id="453a6-301">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-301">Oracle Linux</span></span>                   |  <span data-ttu-id="453a6-302">7</span><span class="sxs-lookup"><span data-stu-id="453a6-302">7</span></span>                      | <span data-ttu-id="453a6-303">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-303">x64</span></span> |
| <span data-ttu-id="453a6-304">Fedora</span><span class="sxs-lookup"><span data-stu-id="453a6-304">Fedora</span></span>                         |  <span data-ttu-id="453a6-305">29, 30</span><span class="sxs-lookup"><span data-stu-id="453a6-305">29, 30</span></span>                 | <span data-ttu-id="453a6-306">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-306">x64</span></span> |
| <span data-ttu-id="453a6-307">Debian</span><span class="sxs-lookup"><span data-stu-id="453a6-307">Debian</span></span>                         |  <span data-ttu-id="453a6-308">9</span><span class="sxs-lookup"><span data-stu-id="453a6-308">9</span></span>                      | <span data-ttu-id="453a6-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="453a6-309">x64, ARM32</span></span> |
| <span data-ttu-id="453a6-310">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="453a6-310">Ubuntu</span></span>                         |  <span data-ttu-id="453a6-311">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="453a6-311">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="453a6-312">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="453a6-312">x64, ARM32</span></span> |
| <span data-ttu-id="453a6-313">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="453a6-313">Linux Mint</span></span>                     |  <span data-ttu-id="453a6-314">17, 18</span><span class="sxs-lookup"><span data-stu-id="453a6-314">17, 18</span></span>                 | <span data-ttu-id="453a6-315">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-315">x64</span></span> |
| <span data-ttu-id="453a6-316">openSUSE</span><span class="sxs-lookup"><span data-stu-id="453a6-316">openSUSE</span></span>                       |  <span data-ttu-id="453a6-317">15 +</span><span class="sxs-lookup"><span data-stu-id="453a6-317">15+</span></span>                    | <span data-ttu-id="453a6-318">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-318">x64</span></span> |
| <span data-ttu-id="453a6-319">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="453a6-319">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="453a6-320">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="453a6-320">12 SP2+</span></span>                | <span data-ttu-id="453a6-321">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-321">x64</span></span> |
| <span data-ttu-id="453a6-322">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-322">Alpine Linux</span></span>                   |  <span data-ttu-id="453a6-323">3.8 +</span><span class="sxs-lookup"><span data-stu-id="453a6-323">3.8+</span></span>                   | <span data-ttu-id="453a6-324">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-324">x64</span></span> |

<span data-ttu-id="453a6-325">Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-325">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="453a6-326">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="453a6-326">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="453a6-327">.NET Core 2,1 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="453a6-327">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="453a6-328">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="453a6-328">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="453a6-329">.NET Core 2,1 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="453a6-329">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="453a6-330">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="453a6-330">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="453a6-331">Operační systém</span><span class="sxs-lookup"><span data-stu-id="453a6-331">OS</span></span>                             |  <span data-ttu-id="453a6-332">Verze</span><span class="sxs-lookup"><span data-stu-id="453a6-332">Version</span></span>                |  <span data-ttu-id="453a6-333">Architektury</span><span class="sxs-lookup"><span data-stu-id="453a6-333">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="453a6-334">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-334">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="453a6-335">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="453a6-335">6, 7, 8</span></span>                | <span data-ttu-id="453a6-336">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-336">x64</span></span> |
| <span data-ttu-id="453a6-337">CentOS</span><span class="sxs-lookup"><span data-stu-id="453a6-337">CentOS</span></span>                         |  <span data-ttu-id="453a6-338">7 +</span><span class="sxs-lookup"><span data-stu-id="453a6-338">7+</span></span>                     | <span data-ttu-id="453a6-339">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-339">x64</span></span> |
| <span data-ttu-id="453a6-340">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-340">Oracle Linux</span></span>                   |  <span data-ttu-id="453a6-341">7 +</span><span class="sxs-lookup"><span data-stu-id="453a6-341">7+</span></span>                     | <span data-ttu-id="453a6-342">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-342">x64</span></span> |
| <span data-ttu-id="453a6-343">Fedora</span><span class="sxs-lookup"><span data-stu-id="453a6-343">Fedora</span></span>                         |  <span data-ttu-id="453a6-344">30 +</span><span class="sxs-lookup"><span data-stu-id="453a6-344">30+</span></span>                    | <span data-ttu-id="453a6-345">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-345">x64</span></span> |
| <span data-ttu-id="453a6-346">Debian</span><span class="sxs-lookup"><span data-stu-id="453a6-346">Debian</span></span>                         |  <span data-ttu-id="453a6-347">9</span><span class="sxs-lookup"><span data-stu-id="453a6-347">9</span></span>                      | <span data-ttu-id="453a6-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="453a6-348">x64, ARM32</span></span> |
| <span data-ttu-id="453a6-349">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="453a6-349">Ubuntu</span></span>                         |  <span data-ttu-id="453a6-350">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="453a6-350">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="453a6-351">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="453a6-351">x64, ARM32</span></span> |
| <span data-ttu-id="453a6-352">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="453a6-352">Linux Mint</span></span>                     |  <span data-ttu-id="453a6-353">17 +</span><span class="sxs-lookup"><span data-stu-id="453a6-353">17+</span></span>                    | <span data-ttu-id="453a6-354">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-354">x64</span></span> |
| <span data-ttu-id="453a6-355">openSUSE</span><span class="sxs-lookup"><span data-stu-id="453a6-355">openSUSE</span></span>                       |  <span data-ttu-id="453a6-356">15 +</span><span class="sxs-lookup"><span data-stu-id="453a6-356">15+</span></span>                    | <span data-ttu-id="453a6-357">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-357">x64</span></span> |
| <span data-ttu-id="453a6-358">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="453a6-358">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="453a6-359">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="453a6-359">12 SP2+</span></span>                | <span data-ttu-id="453a6-360">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-360">x64</span></span> |
| <span data-ttu-id="453a6-361">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-361">Alpine Linux</span></span>                   |  <span data-ttu-id="453a6-362">3.8 +</span><span class="sxs-lookup"><span data-stu-id="453a6-362">3.8+</span></span>                   | <span data-ttu-id="453a6-363">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-363">x64</span></span> |

<span data-ttu-id="453a6-364">Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-364">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="453a6-365">Závislosti distribuce systému Linux</span><span class="sxs-lookup"><span data-stu-id="453a6-365">Linux distribution dependencies</span></span>

<span data-ttu-id="453a6-366">Na základě distribuce systému Linux bude pravděpodobně nutné nainstalovat další závislosti.</span><span class="sxs-lookup"><span data-stu-id="453a6-366">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="453a6-367">Přesné verze a názvy se mohou mírně lišit podle vaší možnosti rozšíření pro Linux.</span><span class="sxs-lookup"><span data-stu-id="453a6-367">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="453a6-368">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="453a6-368">Ubuntu</span></span>

<span data-ttu-id="453a6-369">Ubuntu distribuce vyžadují, aby byly nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="453a6-369">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="453a6-370">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="453a6-370">liblttng-ust0</span></span>
- <span data-ttu-id="453a6-371">libcurl3 (pro 14. x a 16. x)</span><span class="sxs-lookup"><span data-stu-id="453a6-371">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="453a6-372">libcurl4 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="453a6-372">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="453a6-373">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="453a6-373">libssl1.0.0</span></span>
- <span data-ttu-id="453a6-374">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="453a6-374">libkrb5-3</span></span>
- <span data-ttu-id="453a6-375">zlib1g</span><span class="sxs-lookup"><span data-stu-id="453a6-375">zlib1g</span></span>
- <span data-ttu-id="453a6-376">libicu52 (pro 14. x)</span><span class="sxs-lookup"><span data-stu-id="453a6-376">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="453a6-377">libicu55 (pro 16. x)</span><span class="sxs-lookup"><span data-stu-id="453a6-377">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="453a6-378">libicu57 (pro 17. x)</span><span class="sxs-lookup"><span data-stu-id="453a6-378">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="453a6-379">libicu60 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="453a6-379">libicu60 (for 18.x)</span></span>

<span data-ttu-id="453a6-380">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:</span><span class="sxs-lookup"><span data-stu-id="453a6-380">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="453a6-381">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="453a6-381">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="453a6-382">Většina verzí Ubuntu zahrnuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="453a6-382">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="453a6-383">Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="453a6-383">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="453a6-384">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="453a6-384">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="453a6-385">CentOS a Fedora</span><span class="sxs-lookup"><span data-stu-id="453a6-385">CentOS and Fedora</span></span>

<span data-ttu-id="453a6-386">CentOS distribuce vyžadují následující nainstalované knihovny:</span><span class="sxs-lookup"><span data-stu-id="453a6-386">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="453a6-387">lttng – tým UST</span><span class="sxs-lookup"><span data-stu-id="453a6-387">lttng-ust</span></span>
- <span data-ttu-id="453a6-388">libcurl</span><span class="sxs-lookup"><span data-stu-id="453a6-388">libcurl</span></span>
- <span data-ttu-id="453a6-389">OpenSSL – knihovny</span><span class="sxs-lookup"><span data-stu-id="453a6-389">openssl-libs</span></span>
- <span data-ttu-id="453a6-390">krb5 – knihovny</span><span class="sxs-lookup"><span data-stu-id="453a6-390">krb5-libs</span></span>
- <span data-ttu-id="453a6-391">libicu</span><span class="sxs-lookup"><span data-stu-id="453a6-391">libicu</span></span>
- <span data-ttu-id="453a6-392">ZLIB</span><span class="sxs-lookup"><span data-stu-id="453a6-392">zlib</span></span>

<span data-ttu-id="453a6-393">Fedora uživatelé: Pokud verze vašeho OpenSSLu je >= 1,1, budete muset nainstalovat **kompatibilní s openssl10**.</span><span class="sxs-lookup"><span data-stu-id="453a6-393">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="453a6-394">Pro .NET Core 2,0 jsou potřeba taky následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="453a6-394">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="453a6-395">libunwind</span><span class="sxs-lookup"><span data-stu-id="453a6-395">libunwind</span></span>
- <span data-ttu-id="453a6-396">libuuid</span><span class="sxs-lookup"><span data-stu-id="453a6-396">libuuid</span></span>

<span data-ttu-id="453a6-397">Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-397">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="453a6-398">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="453a6-398">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="453a6-399">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="453a6-399">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="453a6-400">Většina verzí CentOS a Fedora zahrnuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="453a6-400">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="453a6-401">Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="453a6-401">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="453a6-402">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="453a6-402">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="alpine"></a><span data-ttu-id="453a6-403">Alpine</span><span class="sxs-lookup"><span data-stu-id="453a6-403">Alpine</span></span>

<span data-ttu-id="453a6-404">Alpské distribuce vyžadují instalaci následujících knihoven:</span><span class="sxs-lookup"><span data-stu-id="453a6-404">Alpine distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="453a6-405">ICU-knihovny (není nutné v případě, že je globalizace zakázána)</span><span class="sxs-lookup"><span data-stu-id="453a6-405">icu-libs (this is not needed if globalization is disabled)</span></span>
- <span data-ttu-id="453a6-406">krb5 – knihovny</span><span class="sxs-lookup"><span data-stu-id="453a6-406">krb5-libs</span></span>
- <span data-ttu-id="453a6-407">libcurl</span><span class="sxs-lookup"><span data-stu-id="453a6-407">libcurl</span></span>
- <span data-ttu-id="453a6-408">libintl</span><span class="sxs-lookup"><span data-stu-id="453a6-408">libintl</span></span>
- <span data-ttu-id="453a6-409">libssl 1.1 (pro Alpine 3,9 nebo novější) nebo libssl 1.0 (pro starší verze)</span><span class="sxs-lookup"><span data-stu-id="453a6-409">libssl1.1 (for Alpine 3.9 or later) or libssl1.0 (for older ones)</span></span>
- <span data-ttu-id="453a6-410">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="453a6-410">libstdc++</span></span>
- <span data-ttu-id="453a6-411">lttng – tým UST</span><span class="sxs-lookup"><span data-stu-id="453a6-411">lttng-ust</span></span>
- <span data-ttu-id="453a6-412">numactl (volitelné, užitečné jenom pro zařízení s podporou NUMA)</span><span class="sxs-lookup"><span data-stu-id="453a6-412">numactl (optional, useful only for devices with NUMA enabled)</span></span>
- <span data-ttu-id="453a6-413">ZLIB</span><span class="sxs-lookup"><span data-stu-id="453a6-413">zlib</span></span>

<span data-ttu-id="453a6-414">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:</span><span class="sxs-lookup"><span data-stu-id="453a6-414">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="453a6-415">libgdiplus (je k dispozici pouze v úložišti Edge/testování)</span><span class="sxs-lookup"><span data-stu-id="453a6-415">libgdiplus (it is available only in the edge/testing repository)</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="453a6-416">Rozhraní .NET Core je podporované v následujících verzích macOS:</span><span class="sxs-lookup"><span data-stu-id="453a6-416">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="453a6-417">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="453a6-417">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="453a6-418">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="453a6-418">.NET Core Version</span></span> | <span data-ttu-id="453a6-419">macOS</span><span class="sxs-lookup"><span data-stu-id="453a6-419">macOS</span></span>                 | <span data-ttu-id="453a6-420">Architektury</span><span class="sxs-lookup"><span data-stu-id="453a6-420">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="453a6-421">3.1</span><span class="sxs-lookup"><span data-stu-id="453a6-421">3.1</span></span>               | <span data-ttu-id="453a6-422">Velký Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="453a6-422">High Sierra (10.13+)</span></span>  | <span data-ttu-id="453a6-423">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-423">x64</span></span> | [<span data-ttu-id="453a6-424">Další informace</span><span class="sxs-lookup"><span data-stu-id="453a6-424">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="453a6-425">3.0</span><span class="sxs-lookup"><span data-stu-id="453a6-425">3.0</span></span>               | <span data-ttu-id="453a6-426">Velký Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="453a6-426">High Sierra (10.13+)</span></span>  | <span data-ttu-id="453a6-427">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-427">x64</span></span> | [<span data-ttu-id="453a6-428">Další informace</span><span class="sxs-lookup"><span data-stu-id="453a6-428">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="453a6-429">2,2</span><span class="sxs-lookup"><span data-stu-id="453a6-429">2.2</span></span>               | <span data-ttu-id="453a6-430">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="453a6-430">Sierra (10.12+)</span></span>       | <span data-ttu-id="453a6-431">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-431">x64</span></span> | [<span data-ttu-id="453a6-432">Další informace</span><span class="sxs-lookup"><span data-stu-id="453a6-432">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="453a6-433">2.1</span><span class="sxs-lookup"><span data-stu-id="453a6-433">2.1</span></span>               | <span data-ttu-id="453a6-434">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="453a6-434">Sierra (10.12+)</span></span>       | <span data-ttu-id="453a6-435">x64</span><span class="sxs-lookup"><span data-stu-id="453a6-435">x64</span></span> | [<span data-ttu-id="453a6-436">Další informace</span><span class="sxs-lookup"><span data-stu-id="453a6-436">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="453a6-437">Od macOS Catalina (verze 10,15) je nutné, aby byl veškerý software sestavený po 1. června 2019, který je distribuován s ID vývojáře, notarized.</span><span class="sxs-lookup"><span data-stu-id="453a6-437">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="453a6-438">Tento požadavek se vztahuje na modul runtime .NET Core, .NET Core SDK a software vytvořený pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="453a6-438">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="453a6-439">Instalační programy pro .NET Core (běhové i sady SDK) verze 3,1, 3,0 a 2,1 byly notarized od 18. února 2020.</span><span class="sxs-lookup"><span data-stu-id="453a6-439">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="453a6-440">Předchozí vydané verze nejsou notarized.</span><span class="sxs-lookup"><span data-stu-id="453a6-440">Prior released versions aren't notarized.</span></span> <span data-ttu-id="453a6-441">Pokud spustíte aplikaci, která není notarized, zobrazí se chybová zpráva podobná následujícímu obrázku:</span><span class="sxs-lookup"><span data-stu-id="453a6-441">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![Výstraha macOS Catalina notarization](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="453a6-443">Další informace o tom, jak vynucované notarization má vliv na rozhraní .NET Core (a aplikace .NET Core), najdete v tématu [Working with MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-443">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="453a6-444">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="453a6-444">libgdiplus</span></span>

<span data-ttu-id="453a6-445">Aplikace .NET Core, které používají *System. Drawing. Common* Assembly, vyžadují, aby bylo možné nainstalovat libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="453a6-445">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="453a6-446">Snadný způsob, jak získat libgdiplus, je použít Správce balíčků [homebrew ("Brew")](https://brew.sh/) pro MacOS.</span><span class="sxs-lookup"><span data-stu-id="453a6-446">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="453a6-447">Po instalaci *Brew*nainstalujte libgdiplus spuštěním následujících příkazů na příkazovém řádku terminálu (Command):</span><span class="sxs-lookup"><span data-stu-id="453a6-447">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="453a6-448">Další kroky</span><span class="sxs-lookup"><span data-stu-id="453a6-448">Next steps</span></span>

- <span data-ttu-id="453a6-449">Pro vývoj a spouštění aplikací nainstalujte [.NET Core SDK](sdk.md) (zahrnuje modul runtime).</span><span class="sxs-lookup"><span data-stu-id="453a6-449">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="453a6-450">Pokud chcete spouštět aplikace, které vytvořili jiní uživatelé, nainstalujte [modul runtime .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="453a6-450">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
