---
title: Závislosti .NET Core SDK a modulu runtime – .NET Core
description: Podrobně popisuje operační systém a požadavky na architekturu procesoru pro instalaci .NET Core SDK a modulu runtime v systémech Windows, Linux a macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 42765d4402dfa17d4e962b2ecaf7a83e91853c76
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140996"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="0a22d-103">Závislosti a požadavky .NET Core</span><span class="sxs-lookup"><span data-stu-id="0a22d-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="0a22d-104">Tento článek podrobně popisuje, které operační systémy a architektura procesoru jsou podporovány rozhraním .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0a22d-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="0a22d-105">Podporované operační systémy</span><span class="sxs-lookup"><span data-stu-id="0a22d-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="0a22d-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="0a22d-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="0a22d-107">Rozhraní .NET Core 3,1 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="0a22d-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="0a22d-108">`+` Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="0a22d-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0a22d-109">Operační systém</span><span class="sxs-lookup"><span data-stu-id="0a22d-109">OS</span></span>                            | <span data-ttu-id="0a22d-110">Version</span><span class="sxs-lookup"><span data-stu-id="0a22d-110">Version</span></span>                        | <span data-ttu-id="0a22d-111">Architektury</span><span class="sxs-lookup"><span data-stu-id="0a22d-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="0a22d-112">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="0a22d-112">Windows Client</span></span>                | <span data-ttu-id="0a22d-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="0a22d-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="0a22d-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-114">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-115">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="0a22d-115">Windows 10 Client</span></span>             | <span data-ttu-id="0a22d-116">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-116">Version 1607+</span></span>                  | <span data-ttu-id="0a22d-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-117">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="0a22d-118">Windows Server</span></span>                | <span data-ttu-id="0a22d-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-119">2012 R2+</span></span>                       | <span data-ttu-id="0a22d-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-120">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="0a22d-121">Nano Server</span></span>                   | <span data-ttu-id="0a22d-122">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-122">Version 1803+</span></span>                  | <span data-ttu-id="0a22d-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0a22d-123">x64, ARM32</span></span>      |

<span data-ttu-id="0a22d-124">Další informace o podporovaných operačních systémech .NET Core 3,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="0a22d-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0a22d-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="0a22d-126">*.NET Core 3,0 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="0a22d-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="0a22d-127">Rozhraní .NET Core 3,0 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="0a22d-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="0a22d-128">`+` Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="0a22d-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0a22d-129">Operační systém</span><span class="sxs-lookup"><span data-stu-id="0a22d-129">OS</span></span>                            | <span data-ttu-id="0a22d-130">Version</span><span class="sxs-lookup"><span data-stu-id="0a22d-130">Version</span></span>                        | <span data-ttu-id="0a22d-131">Architektury</span><span class="sxs-lookup"><span data-stu-id="0a22d-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="0a22d-132">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="0a22d-132">Windows Client</span></span>                | <span data-ttu-id="0a22d-133">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="0a22d-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="0a22d-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-134">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-135">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="0a22d-135">Windows 10 Client</span></span>             | <span data-ttu-id="0a22d-136">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-136">Version 1607+</span></span>                  | <span data-ttu-id="0a22d-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-137">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="0a22d-138">Windows Server</span></span>                | <span data-ttu-id="0a22d-139">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-139">2012 R2+</span></span>                       | <span data-ttu-id="0a22d-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-140">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="0a22d-141">Nano Server</span></span>                   | <span data-ttu-id="0a22d-142">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-142">Version 1803+</span></span>                  | <span data-ttu-id="0a22d-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0a22d-143">x64, ARM32</span></span>      |

<span data-ttu-id="0a22d-144">Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="0a22d-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="0a22d-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="0a22d-146">*.NET Core 2,2 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="0a22d-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="0a22d-147">Rozhraní .NET Core 2,2 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="0a22d-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="0a22d-148">`+` Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="0a22d-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0a22d-149">Operační systém</span><span class="sxs-lookup"><span data-stu-id="0a22d-149">OS</span></span>                            | <span data-ttu-id="0a22d-150">Version</span><span class="sxs-lookup"><span data-stu-id="0a22d-150">Version</span></span>                        | <span data-ttu-id="0a22d-151">Architektury</span><span class="sxs-lookup"><span data-stu-id="0a22d-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="0a22d-152">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="0a22d-152">Windows Client</span></span>                | <span data-ttu-id="0a22d-153">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="0a22d-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="0a22d-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-154">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-155">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="0a22d-155">Windows 10 Client</span></span>             | <span data-ttu-id="0a22d-156">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-156">Version 1607+</span></span>                  | <span data-ttu-id="0a22d-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-157">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="0a22d-158">Windows Server</span></span>                | <span data-ttu-id="0a22d-159">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="0a22d-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-160">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="0a22d-161">Nano Server</span></span>                   | <span data-ttu-id="0a22d-162">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-162">Version 1803+</span></span>                   | <span data-ttu-id="0a22d-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0a22d-163">x64, ARM32</span></span>      |

<span data-ttu-id="0a22d-164">Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="0a22d-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0a22d-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0a22d-166">Rozhraní .NET Core 2,1 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="0a22d-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="0a22d-167">`+` Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="0a22d-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0a22d-168">Operační systém</span><span class="sxs-lookup"><span data-stu-id="0a22d-168">OS</span></span>                            | <span data-ttu-id="0a22d-169">Version</span><span class="sxs-lookup"><span data-stu-id="0a22d-169">Version</span></span>                        | <span data-ttu-id="0a22d-170">Architektury</span><span class="sxs-lookup"><span data-stu-id="0a22d-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="0a22d-171">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="0a22d-171">Windows Client</span></span>                | <span data-ttu-id="0a22d-172">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="0a22d-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="0a22d-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-173">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-174">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="0a22d-174">Windows 10 Client</span></span>             | <span data-ttu-id="0a22d-175">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-175">Version 1607+</span></span>                  | <span data-ttu-id="0a22d-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-176">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="0a22d-177">Windows Server</span></span>                | <span data-ttu-id="0a22d-178">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="0a22d-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="0a22d-179">x64, x86</span></span>        |
| <span data-ttu-id="0a22d-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="0a22d-180">Nano Server</span></span>                   | <span data-ttu-id="0a22d-181">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-181">Version 1803+</span></span>                  | <span data-ttu-id="0a22d-182">platformě</span><span class="sxs-lookup"><span data-stu-id="0a22d-182">x64,</span></span>            |

<span data-ttu-id="0a22d-183">Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="0a22d-184">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="0a22d-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="0a22d-185">Pokud instalujete sadu .NET SDK nebo modul runtime v následujících verzích systému Windows, jsou vyžadovány další závislosti:</span><span class="sxs-lookup"><span data-stu-id="0a22d-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="0a22d-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="0a22d-186">Windows 7 SP1</span></span>
- <span data-ttu-id="0a22d-187">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="0a22d-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="0a22d-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="0a22d-188">Windows 8.1</span></span>
- <span data-ttu-id="0a22d-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="0a22d-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="0a22d-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="0a22d-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="0a22d-191">Nainstalujte následující:</span><span class="sxs-lookup"><span data-stu-id="0a22d-191">Install the following:</span></span>

- <span data-ttu-id="0a22d-192">[Microsoft Visual C++ 2015 Distribuovatelný Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="0a22d-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="0a22d-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="0a22d-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="0a22d-194">Výše uvedené požadavky se vyžadují také v případě, že dojde k jedné z následujících chyb:</span><span class="sxs-lookup"><span data-stu-id="0a22d-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="0a22d-195">Program nelze spustit, protože v počítači chybí *rozhraní API-MS-Win-CRT-runtime-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="0a22d-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="0a22d-196">Zkuste tento problém vyřešit tak, že znovu nainstalujete program.</span><span class="sxs-lookup"><span data-stu-id="0a22d-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="0a22d-197">\-ani</span><span class="sxs-lookup"><span data-stu-id="0a22d-197">\- or -</span></span>
>
> <span data-ttu-id="0a22d-198">Program nelze spustit, protože v počítači chybí *rozhraní API-MS-Win-cor-TimeZone-L1-1 -0. dll* .</span><span class="sxs-lookup"><span data-stu-id="0a22d-198">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="0a22d-199">Zkuste tento problém vyřešit tak, že znovu nainstalujete program.</span><span class="sxs-lookup"><span data-stu-id="0a22d-199">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="0a22d-200">\-ani</span><span class="sxs-lookup"><span data-stu-id="0a22d-200">\- or -</span></span>
>
> <span data-ttu-id="0a22d-201">Knihovna *hostfxr. dll* byla nalezena, ale byla načtena z *jazyka C\\\<: path_to_app \\>hostfxr. dll* se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="0a22d-201">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="0a22d-202">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="0a22d-202">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="0a22d-203">.NET Core 3,1 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="0a22d-203">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="0a22d-204">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="0a22d-204">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="0a22d-205">.NET Core 3,1 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="0a22d-205">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="0a22d-206">`+` Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="0a22d-206">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0a22d-207">Operační systém</span><span class="sxs-lookup"><span data-stu-id="0a22d-207">OS</span></span>                             | <span data-ttu-id="0a22d-208">Version</span><span class="sxs-lookup"><span data-stu-id="0a22d-208">Version</span></span>               | <span data-ttu-id="0a22d-209">Architektury</span><span class="sxs-lookup"><span data-stu-id="0a22d-209">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="0a22d-210">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-210">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="0a22d-211">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="0a22d-211">6, 7, 8</span></span>               | <span data-ttu-id="0a22d-212">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-212">x64</span></span> |
| <span data-ttu-id="0a22d-213">CentOS</span><span class="sxs-lookup"><span data-stu-id="0a22d-213">CentOS</span></span>                         | <span data-ttu-id="0a22d-214">7 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-214">7+</span></span>                    | <span data-ttu-id="0a22d-215">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-215">x64</span></span> |
| <span data-ttu-id="0a22d-216">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-216">Oracle Linux</span></span>                   | <span data-ttu-id="0a22d-217">7 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-217">7+</span></span>                    | <span data-ttu-id="0a22d-218">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-218">x64</span></span> |
| <span data-ttu-id="0a22d-219">Fedora</span><span class="sxs-lookup"><span data-stu-id="0a22d-219">Fedora</span></span>                         | <span data-ttu-id="0a22d-220">30 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-220">30+</span></span>                   | <span data-ttu-id="0a22d-221">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-221">x64</span></span> |
| <span data-ttu-id="0a22d-222">Debian</span><span class="sxs-lookup"><span data-stu-id="0a22d-222">Debian</span></span>                         | <span data-ttu-id="0a22d-223">9 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-223">9+</span></span>                    | <span data-ttu-id="0a22d-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="0a22d-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="0a22d-225">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0a22d-225">Ubuntu</span></span>                         | <span data-ttu-id="0a22d-226">16.04 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-226">16.04+</span></span>                | <span data-ttu-id="0a22d-227">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="0a22d-227">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="0a22d-228">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="0a22d-228">Linux Mint</span></span>                     | <span data-ttu-id="0a22d-229">18 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-229">18+</span></span>                   | <span data-ttu-id="0a22d-230">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-230">x64</span></span> |
| <span data-ttu-id="0a22d-231">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0a22d-231">openSUSE</span></span>                       | <span data-ttu-id="0a22d-232">15 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-232">15+</span></span>                   | <span data-ttu-id="0a22d-233">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-233">x64</span></span> |
| <span data-ttu-id="0a22d-234">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="0a22d-234">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="0a22d-235">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-235">12 SP2+</span></span>               | <span data-ttu-id="0a22d-236">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-236">x64</span></span> |
| <span data-ttu-id="0a22d-237">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-237">Alpine Linux</span></span>                   | <span data-ttu-id="0a22d-238">3.10 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-238">3.10+</span></span>                 | <span data-ttu-id="0a22d-239">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="0a22d-239">x64, ARM64</span></span> |

<span data-ttu-id="0a22d-240">Další informace o podporovaných operačních systémech .NET Core 3,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-240">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="0a22d-241">Další informace o tom, jak nainstalovat .NET Core 3,1 na ARM64 (kernel 4.14 +), najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="0a22d-241">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a22d-242">Podpora ARM64 vyžaduje Linux kernel 4,14 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="0a22d-242">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="0a22d-243">Některé distribuce systému Linux tento požadavek splňují, i když jiné ne.</span><span class="sxs-lookup"><span data-stu-id="0a22d-243">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="0a22d-244">Například Ubuntu 18,04 je podporován, ale Ubuntu 16,04 ne.</span><span class="sxs-lookup"><span data-stu-id="0a22d-244">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="0a22d-245">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0a22d-245">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="0a22d-246">*.NET Core 3,0 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="0a22d-246">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="0a22d-247">.NET Core 3,0 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="0a22d-247">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="0a22d-248">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="0a22d-248">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="0a22d-249">.NET Core 3,0 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="0a22d-249">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="0a22d-250">`+` Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="0a22d-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0a22d-251">Operační systém</span><span class="sxs-lookup"><span data-stu-id="0a22d-251">OS</span></span>                             | <span data-ttu-id="0a22d-252">Version</span><span class="sxs-lookup"><span data-stu-id="0a22d-252">Version</span></span>               | <span data-ttu-id="0a22d-253">Architektury</span><span class="sxs-lookup"><span data-stu-id="0a22d-253">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="0a22d-254">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-254">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="0a22d-255">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="0a22d-255">6, 7, 8</span></span>               | <span data-ttu-id="0a22d-256">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-256">x64</span></span> |
| <span data-ttu-id="0a22d-257">CentOS</span><span class="sxs-lookup"><span data-stu-id="0a22d-257">CentOS</span></span>                         | <span data-ttu-id="0a22d-258">7 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-258">7+</span></span>                    | <span data-ttu-id="0a22d-259">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-259">x64</span></span> |
| <span data-ttu-id="0a22d-260">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-260">Oracle Linux</span></span>                   | <span data-ttu-id="0a22d-261">7 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-261">7+</span></span>                    | <span data-ttu-id="0a22d-262">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-262">x64</span></span> |
| <span data-ttu-id="0a22d-263">Fedora</span><span class="sxs-lookup"><span data-stu-id="0a22d-263">Fedora</span></span>                         | <span data-ttu-id="0a22d-264">29 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-264">29+</span></span>                   | <span data-ttu-id="0a22d-265">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-265">x64</span></span> |
| <span data-ttu-id="0a22d-266">Debian</span><span class="sxs-lookup"><span data-stu-id="0a22d-266">Debian</span></span>                         | <span data-ttu-id="0a22d-267">9 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-267">9+</span></span>                    | <span data-ttu-id="0a22d-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="0a22d-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="0a22d-269">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0a22d-269">Ubuntu</span></span>                         | <span data-ttu-id="0a22d-270">16.04 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-270">16.04+</span></span>                | <span data-ttu-id="0a22d-271">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="0a22d-271">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="0a22d-272">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="0a22d-272">Linux Mint</span></span>                     | <span data-ttu-id="0a22d-273">18 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-273">18+</span></span>                   | <span data-ttu-id="0a22d-274">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-274">x64</span></span> |
| <span data-ttu-id="0a22d-275">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0a22d-275">openSUSE</span></span>                       | <span data-ttu-id="0a22d-276">15 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-276">15+</span></span>                   | <span data-ttu-id="0a22d-277">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-277">x64</span></span> |
| <span data-ttu-id="0a22d-278">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="0a22d-278">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="0a22d-279">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-279">12 SP2+</span></span>               | <span data-ttu-id="0a22d-280">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-280">x64</span></span> |
| <span data-ttu-id="0a22d-281">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-281">Alpine Linux</span></span>                   | <span data-ttu-id="0a22d-282">3.8 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-282">3.8+</span></span>                  | <span data-ttu-id="0a22d-283">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="0a22d-283">x64, ARM64</span></span> |

<span data-ttu-id="0a22d-284">Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-284">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="0a22d-285">Další informace o tom, jak nainstalovat .NET Core 3,0 na ARM64, najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="0a22d-285">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="0a22d-286">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="0a22d-286">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="0a22d-287">*.NET Core 2,2 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="0a22d-287">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="0a22d-288">.NET Core 2,2 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="0a22d-288">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="0a22d-289">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="0a22d-289">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="0a22d-290">.NET Core 2,2 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="0a22d-290">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="0a22d-291">`+` Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="0a22d-291">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0a22d-292">Operační systém</span><span class="sxs-lookup"><span data-stu-id="0a22d-292">OS</span></span>                             |  <span data-ttu-id="0a22d-293">Version</span><span class="sxs-lookup"><span data-stu-id="0a22d-293">Version</span></span>                |  <span data-ttu-id="0a22d-294">Architektury</span><span class="sxs-lookup"><span data-stu-id="0a22d-294">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="0a22d-295">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-295">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="0a22d-296">6, 7</span><span class="sxs-lookup"><span data-stu-id="0a22d-296">6, 7</span></span>                   | <span data-ttu-id="0a22d-297">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-297">x64</span></span> |
| <span data-ttu-id="0a22d-298">CentOS</span><span class="sxs-lookup"><span data-stu-id="0a22d-298">CentOS</span></span>                         |  <span data-ttu-id="0a22d-299">7</span><span class="sxs-lookup"><span data-stu-id="0a22d-299">7</span></span>                      | <span data-ttu-id="0a22d-300">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-300">x64</span></span> |
| <span data-ttu-id="0a22d-301">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-301">Oracle Linux</span></span>                   |  <span data-ttu-id="0a22d-302">7</span><span class="sxs-lookup"><span data-stu-id="0a22d-302">7</span></span>                      | <span data-ttu-id="0a22d-303">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-303">x64</span></span> |
| <span data-ttu-id="0a22d-304">Fedora</span><span class="sxs-lookup"><span data-stu-id="0a22d-304">Fedora</span></span>                         |  <span data-ttu-id="0a22d-305">29, 30</span><span class="sxs-lookup"><span data-stu-id="0a22d-305">29, 30</span></span>                 | <span data-ttu-id="0a22d-306">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-306">x64</span></span> |
| <span data-ttu-id="0a22d-307">Debian</span><span class="sxs-lookup"><span data-stu-id="0a22d-307">Debian</span></span>                         |  <span data-ttu-id="0a22d-308">9</span><span class="sxs-lookup"><span data-stu-id="0a22d-308">9</span></span>                      | <span data-ttu-id="0a22d-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0a22d-309">x64, ARM32</span></span> |
| <span data-ttu-id="0a22d-310">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0a22d-310">Ubuntu</span></span>                         |  <span data-ttu-id="0a22d-311">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="0a22d-311">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="0a22d-312">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0a22d-312">x64, ARM32</span></span> |
| <span data-ttu-id="0a22d-313">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="0a22d-313">Linux Mint</span></span>                     |  <span data-ttu-id="0a22d-314">17, 18</span><span class="sxs-lookup"><span data-stu-id="0a22d-314">17, 18</span></span>                 | <span data-ttu-id="0a22d-315">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-315">x64</span></span> |
| <span data-ttu-id="0a22d-316">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0a22d-316">openSUSE</span></span>                       |  <span data-ttu-id="0a22d-317">15 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-317">15+</span></span>                    | <span data-ttu-id="0a22d-318">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-318">x64</span></span> |
| <span data-ttu-id="0a22d-319">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="0a22d-319">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="0a22d-320">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-320">12 SP2+</span></span>                | <span data-ttu-id="0a22d-321">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-321">x64</span></span> |
| <span data-ttu-id="0a22d-322">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-322">Alpine Linux</span></span>                   |  <span data-ttu-id="0a22d-323">3.8 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-323">3.8+</span></span>                   | <span data-ttu-id="0a22d-324">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-324">x64</span></span> |

<span data-ttu-id="0a22d-325">Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-325">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="0a22d-326">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0a22d-326">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="0a22d-327">.NET Core 2,1 považuje Linux za jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="0a22d-327">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="0a22d-328">Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).</span><span class="sxs-lookup"><span data-stu-id="0a22d-328">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="0a22d-329">.NET Core 2,1 se podporuje v následujících distribucích a verzích systému Linux:</span><span class="sxs-lookup"><span data-stu-id="0a22d-329">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="0a22d-330">`+` Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="0a22d-330">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0a22d-331">Operační systém</span><span class="sxs-lookup"><span data-stu-id="0a22d-331">OS</span></span>                             |  <span data-ttu-id="0a22d-332">Version</span><span class="sxs-lookup"><span data-stu-id="0a22d-332">Version</span></span>                |  <span data-ttu-id="0a22d-333">Architektury</span><span class="sxs-lookup"><span data-stu-id="0a22d-333">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="0a22d-334">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-334">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="0a22d-335">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="0a22d-335">6, 7, 8</span></span>                | <span data-ttu-id="0a22d-336">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-336">x64</span></span> |
| <span data-ttu-id="0a22d-337">CentOS</span><span class="sxs-lookup"><span data-stu-id="0a22d-337">CentOS</span></span>                         |  <span data-ttu-id="0a22d-338">7 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-338">7+</span></span>                     | <span data-ttu-id="0a22d-339">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-339">x64</span></span> |
| <span data-ttu-id="0a22d-340">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-340">Oracle Linux</span></span>                   |  <span data-ttu-id="0a22d-341">7 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-341">7+</span></span>                     | <span data-ttu-id="0a22d-342">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-342">x64</span></span> |
| <span data-ttu-id="0a22d-343">Fedora</span><span class="sxs-lookup"><span data-stu-id="0a22d-343">Fedora</span></span>                         |  <span data-ttu-id="0a22d-344">30 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-344">30+</span></span>                    | <span data-ttu-id="0a22d-345">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-345">x64</span></span> |
| <span data-ttu-id="0a22d-346">Debian</span><span class="sxs-lookup"><span data-stu-id="0a22d-346">Debian</span></span>                         |  <span data-ttu-id="0a22d-347">9</span><span class="sxs-lookup"><span data-stu-id="0a22d-347">9</span></span>                      | <span data-ttu-id="0a22d-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0a22d-348">x64, ARM32</span></span> |
| <span data-ttu-id="0a22d-349">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0a22d-349">Ubuntu</span></span>                         |  <span data-ttu-id="0a22d-350">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="0a22d-350">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="0a22d-351">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="0a22d-351">x64, ARM32</span></span> |
| <span data-ttu-id="0a22d-352">Linux mentolová</span><span class="sxs-lookup"><span data-stu-id="0a22d-352">Linux Mint</span></span>                     |  <span data-ttu-id="0a22d-353">17 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-353">17+</span></span>                    | <span data-ttu-id="0a22d-354">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-354">x64</span></span> |
| <span data-ttu-id="0a22d-355">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0a22d-355">openSUSE</span></span>                       |  <span data-ttu-id="0a22d-356">15 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-356">15+</span></span>                    | <span data-ttu-id="0a22d-357">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-357">x64</span></span> |
| <span data-ttu-id="0a22d-358">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="0a22d-358">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="0a22d-359">12 SP2 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-359">12 SP2+</span></span>                | <span data-ttu-id="0a22d-360">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-360">x64</span></span> |
| <span data-ttu-id="0a22d-361">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-361">Alpine Linux</span></span>                   |  <span data-ttu-id="0a22d-362">3.8 +</span><span class="sxs-lookup"><span data-stu-id="0a22d-362">3.8+</span></span>                   | <span data-ttu-id="0a22d-363">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-363">x64</span></span> |

<span data-ttu-id="0a22d-364">Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-364">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="0a22d-365">Závislosti distribuce systému Linux</span><span class="sxs-lookup"><span data-stu-id="0a22d-365">Linux distribution dependencies</span></span>

<span data-ttu-id="0a22d-366">Na základě distribuce systému Linux bude pravděpodobně nutné nainstalovat další závislosti.</span><span class="sxs-lookup"><span data-stu-id="0a22d-366">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a22d-367">Přesné verze a názvy se mohou mírně lišit podle vaší možnosti rozšíření pro Linux.</span><span class="sxs-lookup"><span data-stu-id="0a22d-367">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="0a22d-368">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="0a22d-368">Ubuntu</span></span>

<span data-ttu-id="0a22d-369">Ubuntu distribuce vyžadují, aby byly nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="0a22d-369">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="0a22d-370">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="0a22d-370">liblttng-ust0</span></span>
- <span data-ttu-id="0a22d-371">libcurl3 (pro 14. x a 16. x)</span><span class="sxs-lookup"><span data-stu-id="0a22d-371">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="0a22d-372">libcurl4 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="0a22d-372">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="0a22d-373">libssl 1.0.0</span><span class="sxs-lookup"><span data-stu-id="0a22d-373">libssl1.0.0</span></span>
- <span data-ttu-id="0a22d-374">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="0a22d-374">libkrb5-3</span></span>
- <span data-ttu-id="0a22d-375">zlib1g</span><span class="sxs-lookup"><span data-stu-id="0a22d-375">zlib1g</span></span>
- <span data-ttu-id="0a22d-376">libicu52 (pro 14. x)</span><span class="sxs-lookup"><span data-stu-id="0a22d-376">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="0a22d-377">libicu55 (pro 16. x)</span><span class="sxs-lookup"><span data-stu-id="0a22d-377">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="0a22d-378">libicu57 (pro 17. x)</span><span class="sxs-lookup"><span data-stu-id="0a22d-378">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="0a22d-379">libicu60 (pro 18. x)</span><span class="sxs-lookup"><span data-stu-id="0a22d-379">libicu60 (for 18.x)</span></span>

<span data-ttu-id="0a22d-380">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:</span><span class="sxs-lookup"><span data-stu-id="0a22d-380">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="0a22d-381">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="0a22d-381">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="0a22d-382">Většina verzí Ubuntu zahrnuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="0a22d-382">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="0a22d-383">Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="0a22d-383">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="0a22d-384">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="0a22d-384">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="0a22d-385">CentOS a Fedora</span><span class="sxs-lookup"><span data-stu-id="0a22d-385">CentOS and Fedora</span></span>

<span data-ttu-id="0a22d-386">CentOS distribuce vyžadují následující nainstalované knihovny:</span><span class="sxs-lookup"><span data-stu-id="0a22d-386">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="0a22d-387">lttng – tým UST</span><span class="sxs-lookup"><span data-stu-id="0a22d-387">lttng-ust</span></span>
- <span data-ttu-id="0a22d-388">libcurl</span><span class="sxs-lookup"><span data-stu-id="0a22d-388">libcurl</span></span>
- <span data-ttu-id="0a22d-389">OpenSSL – knihovny</span><span class="sxs-lookup"><span data-stu-id="0a22d-389">openssl-libs</span></span>
- <span data-ttu-id="0a22d-390">krb5 – knihovny</span><span class="sxs-lookup"><span data-stu-id="0a22d-390">krb5-libs</span></span>
- <span data-ttu-id="0a22d-391">libicu</span><span class="sxs-lookup"><span data-stu-id="0a22d-391">libicu</span></span>
- <span data-ttu-id="0a22d-392">ZLIB</span><span class="sxs-lookup"><span data-stu-id="0a22d-392">zlib</span></span>

<span data-ttu-id="0a22d-393">Fedora uživatelé: Pokud verze vašeho OpenSSLu je >= 1,1, budete muset nainstalovat **kompatibilní s openssl10**.</span><span class="sxs-lookup"><span data-stu-id="0a22d-393">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="0a22d-394">Pro .NET Core 2,0 jsou potřeba taky následující závislosti:</span><span class="sxs-lookup"><span data-stu-id="0a22d-394">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="0a22d-395">libunwind</span><span class="sxs-lookup"><span data-stu-id="0a22d-395">libunwind</span></span>
- <span data-ttu-id="0a22d-396">libuuid</span><span class="sxs-lookup"><span data-stu-id="0a22d-396">libuuid</span></span>

<span data-ttu-id="0a22d-397">Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-397">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="0a22d-398">Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:</span><span class="sxs-lookup"><span data-stu-id="0a22d-398">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="0a22d-399">libgdiplus (verze 6.0.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="0a22d-399">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="0a22d-400">Většina verzí CentOS a Fedora zahrnuje starší verzi libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="0a22d-400">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="0a22d-401">Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému.</span><span class="sxs-lookup"><span data-stu-id="0a22d-401">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="0a22d-402">Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="0a22d-402">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="0a22d-403">Rozhraní .NET Core je podporované v následujících verzích macOS:</span><span class="sxs-lookup"><span data-stu-id="0a22d-403">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="0a22d-404">`+` Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="0a22d-404">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="0a22d-405">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="0a22d-405">.NET Core Version</span></span> | <span data-ttu-id="0a22d-406">macOS</span><span class="sxs-lookup"><span data-stu-id="0a22d-406">macOS</span></span>                 | <span data-ttu-id="0a22d-407">Architektury</span><span class="sxs-lookup"><span data-stu-id="0a22d-407">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="0a22d-408">3.1</span><span class="sxs-lookup"><span data-stu-id="0a22d-408">3.1</span></span>               | <span data-ttu-id="0a22d-409">Velký Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="0a22d-409">High Sierra (10.13+)</span></span>  | <span data-ttu-id="0a22d-410">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-410">x64</span></span> | [<span data-ttu-id="0a22d-411">Další informace</span><span class="sxs-lookup"><span data-stu-id="0a22d-411">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="0a22d-412">3.0</span><span class="sxs-lookup"><span data-stu-id="0a22d-412">3.0</span></span>               | <span data-ttu-id="0a22d-413">Velký Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="0a22d-413">High Sierra (10.13+)</span></span>  | <span data-ttu-id="0a22d-414">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-414">x64</span></span> | [<span data-ttu-id="0a22d-415">Další informace</span><span class="sxs-lookup"><span data-stu-id="0a22d-415">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="0a22d-416">2,2</span><span class="sxs-lookup"><span data-stu-id="0a22d-416">2.2</span></span>               | <span data-ttu-id="0a22d-417">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="0a22d-417">Sierra (10.12+)</span></span>       | <span data-ttu-id="0a22d-418">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-418">x64</span></span> | [<span data-ttu-id="0a22d-419">Další informace</span><span class="sxs-lookup"><span data-stu-id="0a22d-419">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="0a22d-420">2.1</span><span class="sxs-lookup"><span data-stu-id="0a22d-420">2.1</span></span>               | <span data-ttu-id="0a22d-421">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="0a22d-421">Sierra (10.12+)</span></span>       | <span data-ttu-id="0a22d-422">x64</span><span class="sxs-lookup"><span data-stu-id="0a22d-422">x64</span></span> | [<span data-ttu-id="0a22d-423">Další informace</span><span class="sxs-lookup"><span data-stu-id="0a22d-423">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="0a22d-424">Od macOS Catalina (verze 10,15) je nutné, aby byl veškerý software sestavený po 1. června 2019, který je distribuován s ID vývojáře, notarized.</span><span class="sxs-lookup"><span data-stu-id="0a22d-424">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="0a22d-425">Tento požadavek se vztahuje na modul runtime .NET Core, .NET Core SDK a software vytvořený pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0a22d-425">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="0a22d-426">Instalační programy pro .NET Core (běhové i sady SDK) verze 3,1, 3,0 a 2,1 byly notarized od 18. února 2020.</span><span class="sxs-lookup"><span data-stu-id="0a22d-426">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="0a22d-427">Předchozí vydané verze nejsou notarized.</span><span class="sxs-lookup"><span data-stu-id="0a22d-427">Prior released versions aren't notarized.</span></span> <span data-ttu-id="0a22d-428">Pokud spustíte aplikaci, která není notarized, zobrazí se chybová zpráva podobná následujícímu obrázku:</span><span class="sxs-lookup"><span data-stu-id="0a22d-428">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![Výstraha macOS Catalina notarization](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="0a22d-430">Další informace o tom, jak vynucované notarization má vliv na rozhraní .NET Core (a aplikace .NET Core), najdete v tématu [Working with MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-430">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="0a22d-431">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="0a22d-431">libgdiplus</span></span>

<span data-ttu-id="0a22d-432">Aplikace .NET Core, které používají *System. Drawing. Common* Assembly, vyžadují, aby bylo možné nainstalovat libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="0a22d-432">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="0a22d-433">Snadný způsob, jak získat libgdiplus, je použít Správce balíčků [homebrew ("Brew")](https://brew.sh/) pro MacOS.</span><span class="sxs-lookup"><span data-stu-id="0a22d-433">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="0a22d-434">Po instalaci *Brew*nainstalujte libgdiplus spuštěním následujících příkazů na příkazovém řádku terminálu (Command):</span><span class="sxs-lookup"><span data-stu-id="0a22d-434">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="0a22d-435">Další kroky</span><span class="sxs-lookup"><span data-stu-id="0a22d-435">Next steps</span></span>

- <span data-ttu-id="0a22d-436">Pro vývoj a spouštění aplikací nainstalujte [.NET Core SDK](sdk.md) (zahrnuje modul runtime).</span><span class="sxs-lookup"><span data-stu-id="0a22d-436">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="0a22d-437">Pokud chcete spouštět aplikace, které vytvořili jiní uživatelé, nainstalujte [modul runtime .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="0a22d-437">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
