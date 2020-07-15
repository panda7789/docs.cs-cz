---
title: Nainstalovat .NET Core v systému Windows
description: Seznamte se s verzemi Windows, na kterých můžete nainstalovat .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 06/22/2020
ms.openlocfilehash: 97f67d00b3eb4dafc55256aea51f4295bb0ef06a
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308946"
---
# <a name="install-net-core-on-windows"></a><span data-ttu-id="c2a05-103">Nainstalovat .NET Core v systému Windows</span><span class="sxs-lookup"><span data-stu-id="c2a05-103">Install .NET Core on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Instalace v systému Windows](windows.md)
> - [Instalace v systému macOS](macos.md)
> - [Instalace v systému Linux](linux.md)

<span data-ttu-id="c2a05-107">V tomto článku se dozvíte, jak nainstalovat .NET Core v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c2a05-107">In this article, you'll learn how to install .NET Core on Windows.</span></span> <span data-ttu-id="c2a05-108">.NET Core se skládá z modulu runtime a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="c2a05-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="c2a05-109">Modul runtime se používá ke spuštění aplikace .NET Core a může nebo nemusí být součástí aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2a05-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="c2a05-110">Sada SDK se používá k vytváření aplikací a knihoven .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2a05-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="c2a05-111">Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="c2a05-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="c2a05-112">Nejnovější verze .NET Core je 3,1.</span><span class="sxs-lookup"><span data-stu-id="c2a05-112">The latest version of .NET Core is 3.1.</span></span>

> [!div class="button"]
> [<span data-ttu-id="c2a05-113">Stáhnout .NET Core</span><span class="sxs-lookup"><span data-stu-id="c2a05-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="c2a05-114">Podporované verze</span><span class="sxs-lookup"><span data-stu-id="c2a05-114">Supported releases</span></span>

<span data-ttu-id="c2a05-115">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze Windows, na kterých jsou podporované.</span><span class="sxs-lookup"><span data-stu-id="c2a05-115">The following table is a list of currently supported .NET Core releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="c2a05-116">Tato verze zůstane podporovaná, dokud žádná verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [Windows dosáhne konce životnosti](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span><span class="sxs-lookup"><span data-stu-id="c2a05-116">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="c2a05-117">Verze Windows 10 pro data ukončení služby jsou rozdělené podle edice.</span><span class="sxs-lookup"><span data-stu-id="c2a05-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="c2a05-118">V následující tabulce jsou zváženy pouze edice **Home**, **pro**, **pro vzdělávání**a **sady pro for for Workstation** .</span><span class="sxs-lookup"><span data-stu-id="c2a05-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="c2a05-119">Konkrétní podrobnosti najdete v [tabulce faktů pro životní cyklus systému Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) .</span><span class="sxs-lookup"><span data-stu-id="c2a05-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

- <span data-ttu-id="c2a05-120">✔️ označuje, že verze Windows nebo .NET Core je stále podporovaná.</span><span class="sxs-lookup"><span data-stu-id="c2a05-120">A ✔️ indicates that the version of Windows or .NET Core is still supported.</span></span>
- <span data-ttu-id="c2a05-121">❌Indikuje, že verze Windows nebo .NET Core není v této verzi Windows podporována.</span><span class="sxs-lookup"><span data-stu-id="c2a05-121">A ❌ indicates that the version of Windows or .NET Core isn't supported on that Windows release.</span></span>
- <span data-ttu-id="c2a05-122">Pokud se ✔️á verze Windows i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.</span><span class="sxs-lookup"><span data-stu-id="c2a05-122">When both a version of Windows and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="c2a05-123">Operační systém</span><span class="sxs-lookup"><span data-stu-id="c2a05-123">Operating System</span></span>                      | <span data-ttu-id="c2a05-124">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c2a05-124">.NET Core 2.1</span></span> | <span data-ttu-id="c2a05-125">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-125">.NET Core 3.1</span></span> | <span data-ttu-id="c2a05-126">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-126">.NET 5 Preview</span></span> |
|-----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="c2a05-127">✔️ Windows 10 verze 2004</span><span class="sxs-lookup"><span data-stu-id="c2a05-127">✔️ Windows 10, Version 2004</span></span> | <span data-ttu-id="c2a05-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-128">✔️ 2.1</span></span>        | <span data-ttu-id="c2a05-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-129">✔️ 3.1</span></span>        | <span data-ttu-id="c2a05-130">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c2a05-131">✔️ Windows 10 verze 1909</span><span class="sxs-lookup"><span data-stu-id="c2a05-131">✔️ Windows 10, Version 1909</span></span> | <span data-ttu-id="c2a05-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-132">✔️ 2.1</span></span>        | <span data-ttu-id="c2a05-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-133">✔️ 3.1</span></span>        | <span data-ttu-id="c2a05-134">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c2a05-135">✔️ Windows 10 verze 1903</span><span class="sxs-lookup"><span data-stu-id="c2a05-135">✔️ Windows 10, Version 1903</span></span> | <span data-ttu-id="c2a05-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-136">✔️ 2.1</span></span>        | <span data-ttu-id="c2a05-137">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-137">✔️ 3.1</span></span>        | <span data-ttu-id="c2a05-138">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-138">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c2a05-139">✔️ Windows 10 verze 1809</span><span class="sxs-lookup"><span data-stu-id="c2a05-139">✔️ Windows 10, Version 1809</span></span> | <span data-ttu-id="c2a05-140">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-140">✔️ 2.1</span></span>        | <span data-ttu-id="c2a05-141">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-141">✔️ 3.1</span></span>        | <span data-ttu-id="c2a05-142">✔️ 5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-142">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c2a05-143">❌Windows 10 verze 1803</span><span class="sxs-lookup"><span data-stu-id="c2a05-143">❌ Windows 10, Version 1803</span></span> | <span data-ttu-id="c2a05-144">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-144">✔️ 2.1</span></span>        | <span data-ttu-id="c2a05-145">❌3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-145">❌ 3.1</span></span>        | <span data-ttu-id="c2a05-146">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-146">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="c2a05-147">❌Windows 10 verze 1709</span><span class="sxs-lookup"><span data-stu-id="c2a05-147">❌ Windows 10, Version 1709</span></span> | <span data-ttu-id="c2a05-148">❌2,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-148">❌ 2.1</span></span>        | <span data-ttu-id="c2a05-149">❌3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-149">❌ 3.1</span></span>        | <span data-ttu-id="c2a05-150">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-150">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="c2a05-151">❌Windows 10 verze 1703</span><span class="sxs-lookup"><span data-stu-id="c2a05-151">❌ Windows 10, Version 1703</span></span> | <span data-ttu-id="c2a05-152">❌2,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-152">❌ 2.1</span></span>        | <span data-ttu-id="c2a05-153">❌3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-153">❌ 3.1</span></span>        | <span data-ttu-id="c2a05-154">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-154">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="c2a05-155">❌Windows 10 verze 1607</span><span class="sxs-lookup"><span data-stu-id="c2a05-155">❌ Windows 10, Version 1607</span></span> | <span data-ttu-id="c2a05-156">❌2,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-156">❌ 2.1</span></span>        | <span data-ttu-id="c2a05-157">❌3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-157">❌ 3.1</span></span>        | <span data-ttu-id="c2a05-158">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-158">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="c2a05-159">❌Windows 10 verze 1511</span><span class="sxs-lookup"><span data-stu-id="c2a05-159">❌ Windows 10, Version 1511</span></span> | <span data-ttu-id="c2a05-160">❌2,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-160">❌ 2.1</span></span>        | <span data-ttu-id="c2a05-161">❌3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-161">❌ 3.1</span></span>        | <span data-ttu-id="c2a05-162">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-162">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="c2a05-163">❌Windows 10 verze 1507</span><span class="sxs-lookup"><span data-stu-id="c2a05-163">❌ Windows 10, Version 1507</span></span> | <span data-ttu-id="c2a05-164">❌2,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-164">❌ 2.1</span></span>        | <span data-ttu-id="c2a05-165">❌3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-165">❌ 3.1</span></span>        | <span data-ttu-id="c2a05-166">❌5,0 Preview</span><span class="sxs-lookup"><span data-stu-id="c2a05-166">❌ 5.0 Preview</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="c2a05-167">Nepodporované verze</span><span class="sxs-lookup"><span data-stu-id="c2a05-167">Unsupported releases</span></span>

<span data-ttu-id="c2a05-168">Následující verze rozhraní .NET Core již nejsou ❌ podporovány.</span><span class="sxs-lookup"><span data-stu-id="c2a05-168">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="c2a05-169">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="c2a05-169">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c2a05-170">3.0</span><span class="sxs-lookup"><span data-stu-id="c2a05-170">3.0</span></span>
- <span data-ttu-id="c2a05-171">2,2</span><span class="sxs-lookup"><span data-stu-id="c2a05-171">2.2</span></span>
- <span data-ttu-id="c2a05-172">2.0</span><span class="sxs-lookup"><span data-stu-id="c2a05-172">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="c2a05-173">Běhové informace</span><span class="sxs-lookup"><span data-stu-id="c2a05-173">Runtime information</span></span>

<span data-ttu-id="c2a05-174">Modul runtime se používá ke spouštění aplikací vytvořených pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2a05-174">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="c2a05-175">Když autor aplikace publikuje aplikaci, může do své aplikace zahrnout modul runtime.</span><span class="sxs-lookup"><span data-stu-id="c2a05-175">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="c2a05-176">Pokud neobsahují modul runtime, je uživatel k instalaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c2a05-176">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="c2a05-177">V systému Windows můžete nainstalovat tři různé moduly runtime:</span><span class="sxs-lookup"><span data-stu-id="c2a05-177">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="c2a05-178">*Modul runtime ASP.NET Core*</span><span class="sxs-lookup"><span data-stu-id="c2a05-178">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="c2a05-179">Spustí aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2a05-179">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="c2a05-180">Zahrnuje modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2a05-180">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="c2a05-181">*Běhové prostředí plochy*</span><span class="sxs-lookup"><span data-stu-id="c2a05-181">*Desktop runtime*</span></span>\
<span data-ttu-id="c2a05-182">Spustí aplikace .NET Core WPF a .NET Core model Windows Forms desktopové aplikace pro Windows.</span><span class="sxs-lookup"><span data-stu-id="c2a05-182">Runs .NET Core WPF and .NET Core Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="c2a05-183">Zahrnuje modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2a05-183">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="c2a05-184">*Modul runtime .NET Core*</span><span class="sxs-lookup"><span data-stu-id="c2a05-184">*.NET Core runtime*</span></span>\
<span data-ttu-id="c2a05-185">Tento modul runtime je nejjednodušším modulem runtime a neobsahuje žádné další moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="c2a05-185">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="c2a05-186">Pro zajištění nejlepší kompatibility s aplikacemi .NET Core doporučujeme nainstalovat modul runtime *ASP.NET Core* a *modul runtime pro stolní počítače* .</span><span class="sxs-lookup"><span data-stu-id="c2a05-186">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET Core apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="c2a05-187">Stáhnout .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="c2a05-187">Download .NET Core Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="c2a05-188">Informace o sadě SDK</span><span class="sxs-lookup"><span data-stu-id="c2a05-188">SDK information</span></span>

<span data-ttu-id="c2a05-189">Sada SDK se používá k sestavování a publikování aplikací a knihoven .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2a05-189">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="c2a05-190">Instalace sady SDK zahrnuje všechny tři [moduly runtime](#runtime-information): ASP.NET Core, Desktop a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2a05-190">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET Core.</span></span>

> [!div class="button"]
> [<span data-ttu-id="c2a05-191">Stáhnout .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c2a05-191">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="c2a05-192">Závislosti</span><span class="sxs-lookup"><span data-stu-id="c2a05-192">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="c2a05-193">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-193">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="c2a05-194">Rozhraní .NET Core 3,1 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="c2a05-194">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="c2a05-195">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-195">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c2a05-196">Operační systém</span><span class="sxs-lookup"><span data-stu-id="c2a05-196">OS</span></span>                            | <span data-ttu-id="c2a05-197">Verze</span><span class="sxs-lookup"><span data-stu-id="c2a05-197">Version</span></span>                        | <span data-ttu-id="c2a05-198">Architektury</span><span class="sxs-lookup"><span data-stu-id="c2a05-198">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="c2a05-199">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="c2a05-199">Windows Client</span></span>                | <span data-ttu-id="c2a05-200">8.1</span><span class="sxs-lookup"><span data-stu-id="c2a05-200">8.1</span></span>                            | <span data-ttu-id="c2a05-201">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-201">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-202">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="c2a05-202">Windows 10 Client</span></span>             | <span data-ttu-id="c2a05-203">Verze 1609 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-203">Version 1609+</span></span>                  | <span data-ttu-id="c2a05-204">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-204">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-205">Windows Server</span><span class="sxs-lookup"><span data-stu-id="c2a05-205">Windows Server</span></span>                | <span data-ttu-id="c2a05-206">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-206">2012 R2+</span></span>                       | <span data-ttu-id="c2a05-207">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-207">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-208">Nano Server</span><span class="sxs-lookup"><span data-stu-id="c2a05-208">Nano Server</span></span>                   | <span data-ttu-id="c2a05-209">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-209">Version 1803+</span></span>                  | <span data-ttu-id="c2a05-210">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="c2a05-210">x64, ARM32</span></span>      |

<span data-ttu-id="c2a05-211">Další informace o podporovaných operačních systémech .NET Core 3,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-211">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="c2a05-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c2a05-212">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="c2a05-213">*.NET Core 3,0 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="c2a05-213">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="c2a05-214">Rozhraní .NET Core 3,0 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="c2a05-214">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="c2a05-215">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c2a05-216">Operační systém</span><span class="sxs-lookup"><span data-stu-id="c2a05-216">OS</span></span>                            | <span data-ttu-id="c2a05-217">Verze</span><span class="sxs-lookup"><span data-stu-id="c2a05-217">Version</span></span>                        | <span data-ttu-id="c2a05-218">Architektury</span><span class="sxs-lookup"><span data-stu-id="c2a05-218">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="c2a05-219">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="c2a05-219">Windows Client</span></span>                | <span data-ttu-id="c2a05-220">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-220">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="c2a05-221">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-221">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-222">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="c2a05-222">Windows 10 Client</span></span>             | <span data-ttu-id="c2a05-223">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-223">Version 1607+</span></span>                  | <span data-ttu-id="c2a05-224">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-224">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="c2a05-225">Windows Server</span></span>                | <span data-ttu-id="c2a05-226">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-226">2012 R2+</span></span>                       | <span data-ttu-id="c2a05-227">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-227">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-228">Nano Server</span><span class="sxs-lookup"><span data-stu-id="c2a05-228">Nano Server</span></span>                   | <span data-ttu-id="c2a05-229">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-229">Version 1803+</span></span>                  | <span data-ttu-id="c2a05-230">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="c2a05-230">x64, ARM32</span></span>      |

<span data-ttu-id="c2a05-231">Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-231">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="c2a05-232">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="c2a05-232">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="c2a05-233">*.NET Core 2,2 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="c2a05-233">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="c2a05-234">Rozhraní .NET Core 2,2 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="c2a05-234">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="c2a05-235">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-235">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c2a05-236">Operační systém</span><span class="sxs-lookup"><span data-stu-id="c2a05-236">OS</span></span>                            | <span data-ttu-id="c2a05-237">Verze</span><span class="sxs-lookup"><span data-stu-id="c2a05-237">Version</span></span>                        | <span data-ttu-id="c2a05-238">Architektury</span><span class="sxs-lookup"><span data-stu-id="c2a05-238">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="c2a05-239">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="c2a05-239">Windows Client</span></span>                | <span data-ttu-id="c2a05-240">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-240">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="c2a05-241">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-241">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-242">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="c2a05-242">Windows 10 Client</span></span>             | <span data-ttu-id="c2a05-243">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-243">Version 1607+</span></span>                  | <span data-ttu-id="c2a05-244">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-244">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-245">Windows Server</span><span class="sxs-lookup"><span data-stu-id="c2a05-245">Windows Server</span></span>                | <span data-ttu-id="c2a05-246">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-246">2008 R2 SP1+</span></span>                   | <span data-ttu-id="c2a05-247">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-247">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-248">Nano Server</span><span class="sxs-lookup"><span data-stu-id="c2a05-248">Nano Server</span></span>                   | <span data-ttu-id="c2a05-249">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-249">Version 1803+</span></span>                   | <span data-ttu-id="c2a05-250">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="c2a05-250">x64, ARM32</span></span>      |

<span data-ttu-id="c2a05-251">Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-251">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="c2a05-252">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c2a05-252">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="c2a05-253">Rozhraní .NET Core 2,1 podporuje následující verze systému Windows:</span><span class="sxs-lookup"><span data-stu-id="c2a05-253">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="c2a05-254">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-254">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="c2a05-255">Operační systém</span><span class="sxs-lookup"><span data-stu-id="c2a05-255">OS</span></span>                            | <span data-ttu-id="c2a05-256">Verze</span><span class="sxs-lookup"><span data-stu-id="c2a05-256">Version</span></span>                        | <span data-ttu-id="c2a05-257">Architektury</span><span class="sxs-lookup"><span data-stu-id="c2a05-257">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="c2a05-258">Klient Windows</span><span class="sxs-lookup"><span data-stu-id="c2a05-258">Windows Client</span></span>                | <span data-ttu-id="c2a05-259">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="c2a05-259">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="c2a05-260">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-260">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-261">Klient Windows 10</span><span class="sxs-lookup"><span data-stu-id="c2a05-261">Windows 10 Client</span></span>             | <span data-ttu-id="c2a05-262">Verze 1607 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-262">Version 1607+</span></span>                  | <span data-ttu-id="c2a05-263">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-263">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-264">Windows Server</span><span class="sxs-lookup"><span data-stu-id="c2a05-264">Windows Server</span></span>                | <span data-ttu-id="c2a05-265">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-265">2008 R2 SP1+</span></span>                   | <span data-ttu-id="c2a05-266">x64, x86</span><span class="sxs-lookup"><span data-stu-id="c2a05-266">x64, x86</span></span>        |
| <span data-ttu-id="c2a05-267">Nano Server</span><span class="sxs-lookup"><span data-stu-id="c2a05-267">Nano Server</span></span>                   | <span data-ttu-id="c2a05-268">Verze 1803 +</span><span class="sxs-lookup"><span data-stu-id="c2a05-268">Version 1803+</span></span>                  | <span data-ttu-id="c2a05-269">platformě</span><span class="sxs-lookup"><span data-stu-id="c2a05-269">x64,</span></span>            |

<span data-ttu-id="c2a05-270">Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-270">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="c2a05-271">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c2a05-271">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="c2a05-272">Pokud instalujete sadu .NET SDK nebo modul runtime v následujících verzích systému Windows, jsou vyžadovány další závislosti:</span><span class="sxs-lookup"><span data-stu-id="c2a05-272">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="c2a05-273">❌Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="c2a05-273">❌ Windows 7 SP1</span></span>
- <span data-ttu-id="c2a05-274">❌Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="c2a05-274">❌ Windows Vista SP 2</span></span>
- <span data-ttu-id="c2a05-275">✔️ Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="c2a05-275">✔️ Windows 8.1</span></span>
- <span data-ttu-id="c2a05-276">✔️ Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c2a05-276">✔️ Windows Server 2008 R2</span></span>
- <span data-ttu-id="c2a05-277">✔️ Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c2a05-277">✔️ Windows Server 2012 R2</span></span>

<span data-ttu-id="c2a05-278">Nainstalujte následující:</span><span class="sxs-lookup"><span data-stu-id="c2a05-278">Install the following:</span></span>

- <span data-ttu-id="c2a05-279">[Microsoft Visual C++ 2015 Distribuovatelný Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="c2a05-279">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="c2a05-280">KB2533623</span><span class="sxs-lookup"><span data-stu-id="c2a05-280">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="c2a05-281">Výše uvedené požadavky se vyžadují také v případě, že dojde k jedné z následujících chyb:</span><span class="sxs-lookup"><span data-stu-id="c2a05-281">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="c2a05-282">Program nelze spustit, protože ve vašem počítači chybí *api-ms-win-crt-runtime-l1-1-0.dll* .</span><span class="sxs-lookup"><span data-stu-id="c2a05-282">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="c2a05-283">Zkuste tento problém vyřešit tak, že znovu nainstalujete program.</span><span class="sxs-lookup"><span data-stu-id="c2a05-283">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="c2a05-284">\-ani</span><span class="sxs-lookup"><span data-stu-id="c2a05-284">\- or -</span></span>
>
> <span data-ttu-id="c2a05-285">Program nelze spustit, protože ve vašem počítači chybí *api-ms-win-cor-timezone-l1-1-0.dll* .</span><span class="sxs-lookup"><span data-stu-id="c2a05-285">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="c2a05-286">Zkuste tento problém vyřešit tak, že znovu nainstalujete program.</span><span class="sxs-lookup"><span data-stu-id="c2a05-286">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="c2a05-287">\-ani</span><span class="sxs-lookup"><span data-stu-id="c2a05-287">\- or -</span></span>
>
> <span data-ttu-id="c2a05-288">*hostfxr.dll* knihovny bylo nalezeno, ale bylo načteno z *C: \\ \<path_to_app> \\hostfxr.dll* se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="c2a05-288">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="c2a05-289">Instalace pomocí automatizace PowerShellu</span><span class="sxs-lookup"><span data-stu-id="c2a05-289">Install with PowerShell automation</span></span>

<span data-ttu-id="c2a05-290">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci ci a nesprávce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c2a05-290">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="c2a05-291">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-291">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="c2a05-292">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c2a05-292">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="c2a05-293">Konkrétní vydání můžete zvolit zadáním `Channel` přepínače.</span><span class="sxs-lookup"><span data-stu-id="c2a05-293">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="c2a05-294">Zahrňte `Runtime` přepínač pro instalaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c2a05-294">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="c2a05-295">V opačném případě skript nainstaluje [sadu SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-295">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

<span data-ttu-id="c2a05-296">Nainstalujte sadu SDK tak, že tento přepínač vynecháte `-Runtime` .</span><span class="sxs-lookup"><span data-stu-id="c2a05-296">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="c2a05-297">`-Channel`V tomto příkladu je nastaven přepínač na `Current` , který nainstaluje nejnovější podporovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-297">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="c2a05-298">Instalace se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c2a05-298">Install with Visual Studio</span></span>

<span data-ttu-id="c2a05-299">Pokud používáte Visual Studio pro vývoj aplikací .NET Core, v následující tabulce je popsána minimální požadovaná verze sady Visual Studio na základě cílové verze .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c2a05-299">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="c2a05-300">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c2a05-300">.NET Core SDK version</span></span> | <span data-ttu-id="c2a05-301">Verze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c2a05-301">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="c2a05-302">3.1</span><span class="sxs-lookup"><span data-stu-id="c2a05-302">3.1</span></span>                   | <span data-ttu-id="c2a05-303">Visual Studio 2019 verze 16,4 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c2a05-303">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="c2a05-304">3.0</span><span class="sxs-lookup"><span data-stu-id="c2a05-304">3.0</span></span>                   | <span data-ttu-id="c2a05-305">Visual Studio 2019 verze 16,3 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c2a05-305">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="c2a05-306">2,2</span><span class="sxs-lookup"><span data-stu-id="c2a05-306">2.2</span></span>                   | <span data-ttu-id="c2a05-307">Visual Studio 2017 verze 15,9 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c2a05-307">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="c2a05-308">2.1</span><span class="sxs-lookup"><span data-stu-id="c2a05-308">2.1</span></span>                   | <span data-ttu-id="c2a05-309">Visual Studio 2017 verze 15,7 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="c2a05-309">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="c2a05-310">Pokud již máte nainstalováno Visual Studio, můžete si ověřit verzi pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="c2a05-310">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="c2a05-311">Otevřete sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c2a05-311">Open Visual Studio.</span></span>
01. <span data-ttu-id="c2a05-312">Vyberte **nápovědu**  >  **o Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c2a05-312">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="c2a05-313">Přečtěte si číslo verze v dialogovém okně **o produktu** .</span><span class="sxs-lookup"><span data-stu-id="c2a05-313">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="c2a05-314">Visual Studio může nainstalovat nejnovější .NET Core SDK a modul runtime.</span><span class="sxs-lookup"><span data-stu-id="c2a05-314">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="c2a05-315">[Stáhněte si Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="c2a05-315">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="c2a05-316">Vyberte úlohu.</span><span class="sxs-lookup"><span data-stu-id="c2a05-316">Select a workload</span></span>

<span data-ttu-id="c2a05-317">Při instalaci nebo úpravách sady Visual Studio vyberte jednu nebo více následujících úloh v závislosti na typu aplikace, kterou vytváříte:</span><span class="sxs-lookup"><span data-stu-id="c2a05-317">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="c2a05-318">Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="c2a05-318">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="c2a05-319">Úlohy **vývoje ASP.NET a webu** v části **Web & Cloud** .</span><span class="sxs-lookup"><span data-stu-id="c2a05-319">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="c2a05-320">Úlohy **vývoje Azure** v části **Web & cloudu** .</span><span class="sxs-lookup"><span data-stu-id="c2a05-320">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="c2a05-321">Úloha **vývoj desktopových aplikací .NET** v části **Desktop & Mobile** .</span><span class="sxs-lookup"><span data-stu-id="c2a05-321">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="c2a05-322">[![Windows Visual Studio 2019 s úlohou .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="c2a05-322">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="c2a05-323">Nainstalovat společně Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c2a05-323">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="c2a05-324">Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="c2a05-324">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="c2a05-325">Visual Studio Code je k dispozici pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="c2a05-325">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="c2a05-326">I když Visual Studio Code nepřichází s automatizovaným instalačním programem .NET Core, jako je Visual Studio, přidání podpory .NET Core je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="c2a05-326">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="c2a05-327">[Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="c2a05-327">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="c2a05-328">[Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="c2a05-328">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="c2a05-329">[Nainstalujte rozšíření C# z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="c2a05-329">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="c2a05-330">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="c2a05-330">Download and manually install</span></span>

<span data-ttu-id="c2a05-331">Jako alternativu k instalačním programům Windows pro .NET Core si můžete stáhnout a ručně nainstalovat sadu SDK nebo modul runtime.</span><span class="sxs-lookup"><span data-stu-id="c2a05-331">As an alternative to the Windows installers for .NET Core, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="c2a05-332">Ruční instalace se obvykle provádí jako součást testování průběžné integrace.</span><span class="sxs-lookup"><span data-stu-id="c2a05-332">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="c2a05-333">Pro vývojáře nebo uživatele je obecně lepší použít [instalační program](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="c2a05-333">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="c2a05-334">.NET Core SDK i modul runtime .NET Core lze po stažení ručně nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="c2a05-334">Both .NET Core SDK and .NET Core Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="c2a05-335">Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime.</span><span class="sxs-lookup"><span data-stu-id="c2a05-335">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="c2a05-336">Nejprve Stáhněte binární verzi pro sadu SDK nebo modul runtime z jednoho z následujících lokalit:</span><span class="sxs-lookup"><span data-stu-id="c2a05-336">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="c2a05-337">[soubory ke stažení ✔️ .net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="c2a05-337">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="c2a05-338">[soubory ke stažení ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="c2a05-338">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="c2a05-339">[soubory ke stažení ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="c2a05-339">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="c2a05-340">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="c2a05-340">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="c2a05-341">Vytvořte adresář pro extrakci rozhraní .NET, například `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="c2a05-341">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="c2a05-342">Pak Extrahujte stažený soubor zip do tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="c2a05-342">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="c2a05-343">Ve výchozím nastavení nepoužívají .NET Core CLI příkazy a aplikace tímto způsobem nainstalované rozhraní .NET Core a musíte ho explicitně použít.</span><span class="sxs-lookup"><span data-stu-id="c2a05-343">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="c2a05-344">Provedete to tak, že změníte proměnné prostředí, se kterými je aplikace spuštěná:</span><span class="sxs-lookup"><span data-stu-id="c2a05-344">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="c2a05-345">Tento přístup umožňuje nainstalovat více verzí do samostatných umístění a pak explicitně zvolit umístění instalace, které by měla aplikace používat, a to spuštěním aplikace s proměnnými prostředí, které ukazují na toto umístění.</span><span class="sxs-lookup"><span data-stu-id="c2a05-345">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="c2a05-346">Když `DOTNET_MULTILEVEL_LOOKUP` je nastavená na `0` , rozhraní .NET Core ignoruje všechny globálně nainstalované verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2a05-346">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET Core ignores any globally installed .NET Core version.</span></span> <span data-ttu-id="c2a05-347">Odeberte toto nastavení prostředí, aby rozhraní .NET Core při výběru nejlepšího rozhraní pro spuštění aplikace bralo v úvahu výchozí globální umístění instalace.</span><span class="sxs-lookup"><span data-stu-id="c2a05-347">Remove that environment setting to let .NET Core consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="c2a05-348">Výchozí hodnota je obvykle `C:\Program Files\dotnet` , což znamená, že instalační programy instalují .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2a05-348">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET Core.</span></span>

## <a name="docker"></a><span data-ttu-id="c2a05-349">Docker</span><span class="sxs-lookup"><span data-stu-id="c2a05-349">Docker</span></span>

<span data-ttu-id="c2a05-350">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="c2a05-350">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="c2a05-351">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="c2a05-351">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="c2a05-352">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="c2a05-352">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="c2a05-353">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="c2a05-353">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="c2a05-354">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="c2a05-354">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="c2a05-355">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="c2a05-355">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="c2a05-356">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="c2a05-356">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="c2a05-357">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-357">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c2a05-358">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c2a05-358">Next steps</span></span>

- <span data-ttu-id="c2a05-359">[Jak zjistit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c2a05-359">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="c2a05-360">[Kurz: kurz Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-360">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="c2a05-361">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-361">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="c2a05-362">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="c2a05-362">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>
