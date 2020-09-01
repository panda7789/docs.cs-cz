---
title: Nainstalovat .NET Core na macOS
description: Přečtěte si, na jaké verze macOS můžete .NET Core nainstalovat.
author: adegeo
ms.author: adegeo
ms.date: 06/25/2020
ms.openlocfilehash: 19d5ca77b0308533c8f228be70c61daf1b7f82d9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132752"
---
# <a name="install-net-core-on-macos"></a><span data-ttu-id="8075c-103">Nainstalovat .NET Core na macOS</span><span class="sxs-lookup"><span data-stu-id="8075c-103">Install .NET Core on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [Instalace v systému Windows](windows.md)
> - [Instalace v systému macOS](macos.md)
> - [Instalace v systému Linux](linux.md)

<span data-ttu-id="8075c-107">V tomto článku se dozvíte, jak nainstalovat .NET Core na macOS.</span><span class="sxs-lookup"><span data-stu-id="8075c-107">In this article, you'll learn how to install .NET Core on macOS.</span></span> <span data-ttu-id="8075c-108">.NET Core se skládá z modulu runtime a sady SDK.</span><span class="sxs-lookup"><span data-stu-id="8075c-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="8075c-109">Modul runtime se používá ke spuštění aplikace .NET Core a může nebo nemusí být součástí aplikace.</span><span class="sxs-lookup"><span data-stu-id="8075c-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="8075c-110">Sada SDK se používá k vytváření aplikací a knihoven .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8075c-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="8075c-111">Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="8075c-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="8075c-112">Nejnovější verze .NET Core je 3,1.</span><span class="sxs-lookup"><span data-stu-id="8075c-112">The latest version of .NET Core is 3.1.</span></span>

> [!div class="button"]
> [<span data-ttu-id="8075c-113">Stáhnout .NET Core</span><span class="sxs-lookup"><span data-stu-id="8075c-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="8075c-114">Podporované verze</span><span class="sxs-lookup"><span data-stu-id="8075c-114">Supported releases</span></span>

<span data-ttu-id="8075c-115">Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze macOS, na kterých jsou podporované.</span><span class="sxs-lookup"><span data-stu-id="8075c-115">The following table is a list of currently supported .NET Core releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="8075c-116">Tato verze zůstane podporovaná, protože verze [.NET Core dosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="8075c-116">These versions remain supported either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="8075c-117">✔️ označuje, že verze rozhraní .NET Core je stále podporovaná.</span><span class="sxs-lookup"><span data-stu-id="8075c-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="8075c-118">A ❌ označuje, že verze rozhraní .NET Core není podporována.</span><span class="sxs-lookup"><span data-stu-id="8075c-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="8075c-119">Operační systém</span><span class="sxs-lookup"><span data-stu-id="8075c-119">Operating System</span></span>          | <span data-ttu-id="8075c-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8075c-120">.NET Core 2.1</span></span> | <span data-ttu-id="8075c-121">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="8075c-121">.NET Core 3.1</span></span> | <span data-ttu-id="8075c-122">.NET 5 Preview</span><span class="sxs-lookup"><span data-stu-id="8075c-122">.NET 5 Preview</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="8075c-123">macOS 10,15 "Catalina"</span><span class="sxs-lookup"><span data-stu-id="8075c-123">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="8075c-124">✔️ 2,1 ([poznámky k verzi][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="8075c-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="8075c-125">✔️ 3,1 ([poznámky k verzi][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="8075c-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="8075c-126">✔️ 5,0 Preview ([poznámky k verzi][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="8075c-126">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="8075c-127">macOS 10,14 "Mojave"</span><span class="sxs-lookup"><span data-stu-id="8075c-127">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="8075c-128">✔️ 2,1 ([poznámky k verzi][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="8075c-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="8075c-129">✔️ 3,1 ([poznámky k verzi][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="8075c-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="8075c-130">✔️ 5,0 Preview ([poznámky k verzi][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="8075c-130">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="8075c-131">macOS 10,13 "High Sierra"</span><span class="sxs-lookup"><span data-stu-id="8075c-131">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="8075c-132">✔️ 2,1 ([poznámky k verzi][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="8075c-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="8075c-133">✔️ 3,1 ([poznámky k verzi][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="8075c-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="8075c-134">✔️ 5,0 Preview ([poznámky k verzi][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="8075c-134">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="8075c-135">macOS 10,12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="8075c-135">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="8075c-136">✔️ 2,1 ([poznámky k verzi][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="8075c-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="8075c-137">❌ 3,1 ([poznámky k verzi][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="8075c-137">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="8075c-138">❌ 5,0 Preview ([poznámky k verzi][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="8075c-138">❌ 5.0 Preview ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="8075c-139">Nepodporované verze</span><span class="sxs-lookup"><span data-stu-id="8075c-139">Unsupported releases</span></span>

<span data-ttu-id="8075c-140">Následující verze rozhraní .NET Core již nejsou ❌ podporovány.</span><span class="sxs-lookup"><span data-stu-id="8075c-140">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="8075c-141">Soubory ke stažení pro tyto soubory zůstanou publikované:</span><span class="sxs-lookup"><span data-stu-id="8075c-141">The downloads for these still remain published:</span></span>

- <span data-ttu-id="8075c-142">3,0 ([poznámky k verzi][release-notes-30])</span><span class="sxs-lookup"><span data-stu-id="8075c-142">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="8075c-143">2,2 ([poznámky k verzi][release-notes-22])</span><span class="sxs-lookup"><span data-stu-id="8075c-143">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="8075c-144">2,0 ([poznámky k verzi][release-notes-20])</span><span class="sxs-lookup"><span data-stu-id="8075c-144">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="8075c-145">Běhové informace</span><span class="sxs-lookup"><span data-stu-id="8075c-145">Runtime information</span></span>

<span data-ttu-id="8075c-146">Modul runtime se používá ke spouštění aplikací vytvořených pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8075c-146">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="8075c-147">Když autor aplikace publikuje aplikaci, může do své aplikace zahrnout modul runtime.</span><span class="sxs-lookup"><span data-stu-id="8075c-147">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="8075c-148">Pokud neobsahují modul runtime, je uživatel k instalaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8075c-148">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="8075c-149">V macOS můžete nainstalovat tři různé moduly runtime:</span><span class="sxs-lookup"><span data-stu-id="8075c-149">There are three different runtimes you can install on macOS:</span></span>

<span data-ttu-id="8075c-150">*Modul runtime ASP.NET Core*</span><span class="sxs-lookup"><span data-stu-id="8075c-150">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="8075c-151">Spustí aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8075c-151">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="8075c-152">Zahrnuje modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8075c-152">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="8075c-153">*Modul runtime .NET Core*</span><span class="sxs-lookup"><span data-stu-id="8075c-153">*.NET Core runtime*</span></span>\
<span data-ttu-id="8075c-154">Tento modul runtime je nejjednodušším modulem runtime a neobsahuje žádné další moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="8075c-154">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="8075c-155">Pro zajištění nejlepší kompatibility s aplikacemi .NET Core důrazně doporučujeme nainstalovat *ASP.NET Core Runtime* .</span><span class="sxs-lookup"><span data-stu-id="8075c-155">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET Core apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="8075c-156">Stáhnout .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="8075c-156">Download .NET Core Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="8075c-157">Informace o sadě SDK</span><span class="sxs-lookup"><span data-stu-id="8075c-157">SDK information</span></span>

<span data-ttu-id="8075c-158">Sada SDK se používá k sestavování a publikování aplikací a knihoven .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8075c-158">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="8075c-159">Instalace sady SDK zahrnuje jak [běhové prostředí](#runtime-information): ASP.NET Core, tak .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8075c-159">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET Core.</span></span>

> [!div class="button"]
> [<span data-ttu-id="8075c-160">Stáhnout .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="8075c-160">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="8075c-161">Závislosti</span><span class="sxs-lookup"><span data-stu-id="8075c-161">Dependencies</span></span>

<span data-ttu-id="8075c-162">Rozhraní .NET Core je podporované v následujících verzích macOS:</span><span class="sxs-lookup"><span data-stu-id="8075c-162">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="8075c-163">`+`Symbol představuje minimální verzi.</span><span class="sxs-lookup"><span data-stu-id="8075c-163">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="8075c-164">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="8075c-164">.NET Core Version</span></span> | <span data-ttu-id="8075c-165">macOS</span><span class="sxs-lookup"><span data-stu-id="8075c-165">macOS</span></span>                 | <span data-ttu-id="8075c-166">Architektury</span><span class="sxs-lookup"><span data-stu-id="8075c-166">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="8075c-167">3.1</span><span class="sxs-lookup"><span data-stu-id="8075c-167">3.1</span></span>               | <span data-ttu-id="8075c-168">Velký Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="8075c-168">High Sierra (10.13+)</span></span>  | <span data-ttu-id="8075c-169">x64</span><span class="sxs-lookup"><span data-stu-id="8075c-169">x64</span></span> | [<span data-ttu-id="8075c-170">Další informace</span><span class="sxs-lookup"><span data-stu-id="8075c-170">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="8075c-171">3,0</span><span class="sxs-lookup"><span data-stu-id="8075c-171">3.0</span></span>               | <span data-ttu-id="8075c-172">Velký Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="8075c-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="8075c-173">x64</span><span class="sxs-lookup"><span data-stu-id="8075c-173">x64</span></span> | [<span data-ttu-id="8075c-174">Další informace</span><span class="sxs-lookup"><span data-stu-id="8075c-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="8075c-175">2,2</span><span class="sxs-lookup"><span data-stu-id="8075c-175">2.2</span></span>               | <span data-ttu-id="8075c-176">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="8075c-176">Sierra (10.12+)</span></span>       | <span data-ttu-id="8075c-177">x64</span><span class="sxs-lookup"><span data-stu-id="8075c-177">x64</span></span> | [<span data-ttu-id="8075c-178">Další informace</span><span class="sxs-lookup"><span data-stu-id="8075c-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="8075c-179">2.1</span><span class="sxs-lookup"><span data-stu-id="8075c-179">2.1</span></span>               | <span data-ttu-id="8075c-180">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="8075c-180">Sierra (10.12+)</span></span>       | <span data-ttu-id="8075c-181">x64</span><span class="sxs-lookup"><span data-stu-id="8075c-181">x64</span></span> | [<span data-ttu-id="8075c-182">Další informace</span><span class="sxs-lookup"><span data-stu-id="8075c-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="8075c-183">Od macOS Catalina (verze 10,15) je nutné, aby byl veškerý software sestavený po 1. června 2019, který je distribuován s ID vývojáře, notarized.</span><span class="sxs-lookup"><span data-stu-id="8075c-183">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="8075c-184">Tento požadavek se vztahuje na modul runtime .NET Core, .NET Core SDK a software vytvořený pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8075c-184">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="8075c-185">Instalační programy pro .NET Core (běhové i sady SDK) verze 3,1, 3,0 a 2,1 byly notarized od 18. února 2020.</span><span class="sxs-lookup"><span data-stu-id="8075c-185">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="8075c-186">Předchozí vydané verze nejsou notarized.</span><span class="sxs-lookup"><span data-stu-id="8075c-186">Prior released versions aren't notarized.</span></span> <span data-ttu-id="8075c-187">Pokud spustíte aplikaci, která není notarized, zobrazí se chybová zpráva podobná následujícímu obrázku:</span><span class="sxs-lookup"><span data-stu-id="8075c-187">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![Výstraha macOS Catalina notarization](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="8075c-189">Další informace o tom, jak vynucované notarization má vliv na rozhraní .NET Core (a aplikace .NET Core), najdete v tématu [Working with MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="8075c-189">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="8075c-190">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="8075c-190">libgdiplus</span></span>

<span data-ttu-id="8075c-191">Aplikace .NET Core, které používají *System. Drawing. Common* Assembly, vyžadují, aby bylo možné nainstalovat libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="8075c-191">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="8075c-192">Snadný způsob, jak získat libgdiplus, je použít Správce balíčků [homebrew ("Brew")](https://brew.sh/) pro MacOS.</span><span class="sxs-lookup"><span data-stu-id="8075c-192">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="8075c-193">Po instalaci *Brew*nainstalujte libgdiplus spuštěním následujících příkazů na příkazovém řádku terminálu (Command):</span><span class="sxs-lookup"><span data-stu-id="8075c-193">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="8075c-194">Instalace pomocí instalačního programu</span><span class="sxs-lookup"><span data-stu-id="8075c-194">Install with an installer</span></span>

<span data-ttu-id="8075c-195">macOS má samostatné instalační programy, které se dají použít k instalaci sady .NET Core 3,1 SDK:</span><span class="sxs-lookup"><span data-stu-id="8075c-195">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="8075c-196">Procesory x64 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="8075c-196">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="8075c-197">Stažení a ruční instalace</span><span class="sxs-lookup"><span data-stu-id="8075c-197">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="8075c-198">Jako alternativu k instalačním modulům macOS pro .NET Core si můžete stáhnout a ručně nainstalovat sadu SDK a modul runtime.</span><span class="sxs-lookup"><span data-stu-id="8075c-198">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="8075c-199">Ruční instalace se obvykle provádí jako součást testování průběžné integrace.</span><span class="sxs-lookup"><span data-stu-id="8075c-199">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="8075c-200">Pro vývojáře nebo uživatele je obecně lepší použít [instalační program](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="8075c-200">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="8075c-201">Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime.</span><span class="sxs-lookup"><span data-stu-id="8075c-201">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="8075c-202">Nejprve stáhněte **binární** verzi pro sadu SDK nebo modul runtime z jednoho z následujících lokalit:</span><span class="sxs-lookup"><span data-stu-id="8075c-202">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="8075c-203">[soubory ke stažení ✔️ .net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="8075c-203">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="8075c-204">[soubory ke stažení ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="8075c-204">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="8075c-205">[soubory ke stažení ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="8075c-205">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="8075c-206">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="8075c-206">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="8075c-207">Dále Extrahujte stažený soubor a pomocí `export` příkazu nastavte proměnné používané .NET Core a pak zajistěte, aby byl .NET Core v cestě.</span><span class="sxs-lookup"><span data-stu-id="8075c-207">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="8075c-208">Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve Stáhněte binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8075c-208">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="8075c-209">Pak otevřete terminál a spusťte následující příkazy z adresáře, kam byl soubor uložen.</span><span class="sxs-lookup"><span data-stu-id="8075c-209">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="8075c-210">Název souboru archivu se může lišit v závislosti na tom, co jste stáhli.</span><span class="sxs-lookup"><span data-stu-id="8075c-210">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="8075c-211">**K extrakci modulu runtime použijte následující příkaz**:</span><span class="sxs-lookup"><span data-stu-id="8075c-211">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.5-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="8075c-212">**K extrakci sady SDK použijte následující příkaz**:</span><span class="sxs-lookup"><span data-stu-id="8075c-212">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="8075c-213">Předchozí `export` příkazy zpřístupní pouze příkazy .NET Core CLI pro relaci terminálu, ve které byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="8075c-213">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="8075c-214">Úpravou profilu prostředí můžete tyto příkazy trvale přidat.</span><span class="sxs-lookup"><span data-stu-id="8075c-214">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="8075c-215">K dispozici je řada různých prostředí pro Linux a každá má jiný profil.</span><span class="sxs-lookup"><span data-stu-id="8075c-215">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="8075c-216">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8075c-216">For example:</span></span>
>
> - <span data-ttu-id="8075c-217">**Prostředí bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="8075c-217">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="8075c-218">**Korn shell**: *~/.KSHRC* nebo *. Profile*</span><span class="sxs-lookup"><span data-stu-id="8075c-218">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="8075c-219">**Prostředí Z**: *~/.zshrc* nebo *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="8075c-219">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="8075c-220">Upravte příslušný zdrojový soubor pro prostředí a přidejte `:$HOME/dotnet` na konec existujícího `PATH` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8075c-220">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="8075c-221">Pokud `PATH` není žádný příkaz zahrnutý, přidejte nový řádek s `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="8075c-221">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="8075c-222">Přidejte také `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="8075c-222">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="8075c-223">Tento přístup umožňuje nainstalovat různé verze do samostatných umístění a zvolit, která z nich se má použít pro kterou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8075c-223">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="8075c-224">Instalace pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="8075c-224">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="8075c-225">Visual Studio pro Mac nainstaluje .NET Core SDK při výběru úlohy **.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="8075c-225">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="8075c-226">Chcete-li začít s vývojem .NET Core v macOS, přečtěte si téma [instalace sady Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="8075c-226">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="8075c-227">Pro nejnovější vydání .NET Core 3,1 je nutné použít Visual Studio pro Mac 8,4.</span><span class="sxs-lookup"><span data-stu-id="8075c-227">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="8075c-228">[![macOS Visual Studio 2019 for Mac s funkcí úlohy .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="8075c-228">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="8075c-229">Nainstalovat společně Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8075c-229">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="8075c-230">Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="8075c-230">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="8075c-231">Visual Studio Code je k dispozici pro Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="8075c-231">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="8075c-232">I když Visual Studio Code nepřichází s automatizovaným instalačním programem .NET Core, jako je Visual Studio, přidání podpory .NET Core je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="8075c-232">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="8075c-233">[Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="8075c-233">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="8075c-234">[Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="8075c-234">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="8075c-235">[Nainstalujte rozšíření C# z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="8075c-235">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="8075c-236">Instalace pomocí služby bash Automation</span><span class="sxs-lookup"><span data-stu-id="8075c-236">Install with bash automation</span></span>

<span data-ttu-id="8075c-237">[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8075c-237">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="8075c-238">Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="8075c-238">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="8075c-239">Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="8075c-239">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="8075c-240">Konkrétní vydání můžete zvolit zadáním `current` přepínače.</span><span class="sxs-lookup"><span data-stu-id="8075c-240">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="8075c-241">Zahrňte `runtime` přepínač pro instalaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8075c-241">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="8075c-242">V opačném případě skript nainstaluje [sadu SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="8075c-242">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="8075c-243">Výše uvedený příkaz nainstaluje modul runtime ASP.NET Core, aby se maximální kompatibilita mohla.</span><span class="sxs-lookup"><span data-stu-id="8075c-243">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="8075c-244">Modul runtime ASP.NET Core zahrnuje také standardní modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8075c-244">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="8075c-245">Docker</span><span class="sxs-lookup"><span data-stu-id="8075c-245">Docker</span></span>

<span data-ttu-id="8075c-246">Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="8075c-246">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="8075c-247">Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.</span><span class="sxs-lookup"><span data-stu-id="8075c-247">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="8075c-248">.NET Core může běžet v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="8075c-248">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="8075c-249">Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="8075c-249">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="8075c-250">Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.</span><span class="sxs-lookup"><span data-stu-id="8075c-250">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="8075c-251">Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="8075c-251">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="8075c-252">Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="8075c-252">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="8075c-253">Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="8075c-253">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8075c-254">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8075c-254">Next steps</span></span>

- <span data-ttu-id="8075c-255">[Jak zjistit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="8075c-255">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="8075c-256">[Práce s MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="8075c-256">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="8075c-257">[Kurz: Začínáme s MacOS](../tutorials/with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="8075c-257">[Tutorial: Get started on macOS](../tutorials/with-visual-studio-mac.md).</span></span>
- <span data-ttu-id="8075c-258">[Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="8075c-258">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="8075c-259">[Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)</span><span class="sxs-lookup"><span data-stu-id="8075c-259">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
