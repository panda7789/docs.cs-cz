---
title: Odinstalační nástroj
description: Přehled nástroje pro odinstalaci rozhraní .NET Core, což je průvodce nástrojem, který umožňuje řízené vyčištění sad .NET Core SDK a modulů runtime.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 4944c983cbd02b456c3a09a1b03bc28ba6e458cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714542"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="67bdd-103">Nástroj pro odinstalaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="67bdd-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="67bdd-104">[Nástroj pro odinstalaci .NET Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) umožňuje odebrat sady .NET Core SDK a moduly runtime ze systému.</span><span class="sxs-lookup"><span data-stu-id="67bdd-104">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="67bdd-105">K dispozici je kolekce možností, které určují verze, které chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="67bdd-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="67bdd-106">Nástroj podporuje Windows a macOS.</span><span class="sxs-lookup"><span data-stu-id="67bdd-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="67bdd-107">Linux není aktuálně podporován.</span><span class="sxs-lookup"><span data-stu-id="67bdd-107">Linux is currently not supported.</span></span>

<span data-ttu-id="67bdd-108">V systému Windows může nástroj odinstalovat pouze sady SDK a moduly runtime, které byly nainstalovány pomocí jednoho z následujících instalačních programů:</span><span class="sxs-lookup"><span data-stu-id="67bdd-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="67bdd-109">Instalační program .NET Core SDK a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="67bdd-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="67bdd-110">Instalační program sady Visual Studio ve verzích starších než Visual Studio 2019 verze 16,3.</span><span class="sxs-lookup"><span data-stu-id="67bdd-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="67bdd-111">V macOS může nástroj odinstalovat jenom sady SDK a moduly runtime umístěné ve složce */usr/local/share/dotnet* .</span><span class="sxs-lookup"><span data-stu-id="67bdd-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="67bdd-112">Z důvodu těchto omezení nemusí nástroj na počítači odinstalovat všechny sady .NET Core SDK a moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="67bdd-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="67bdd-113">Pomocí příkazu `dotnet --info` můžete vyhledat všechny nainstalované sady SDK a moduly runtime .NET Core, včetně sad SDK a modulů runtime, které tento nástroj nemůže odebrat.</span><span class="sxs-lookup"><span data-stu-id="67bdd-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="67bdd-114">Příkaz `dotnet-core-uninstall list` zobrazuje, které sady SDK je možné odinstalovat pomocí nástroje.</span><span class="sxs-lookup"><span data-stu-id="67bdd-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="67bdd-115">Instalace nástroje</span><span class="sxs-lookup"><span data-stu-id="67bdd-115">Install the tool</span></span>

<span data-ttu-id="67bdd-116">Nástroj pro odinstalaci .NET Core si můžete stáhnout z úložiště GitHubu [dotnet/CLI-Lab](https://github.com/dotnet/cli-lab/releases) .</span><span class="sxs-lookup"><span data-stu-id="67bdd-116">You can download the .NET Core Uninstall Tool from the [dotnet/cli-lab](https://github.com/dotnet/cli-lab/releases) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="67bdd-117">Tento nástroj vyžaduje zvýšení oprávnění k odinstalování sad SDK a modulů runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="67bdd-118">Proto by měl být nainstalován v adresáři chráněném zápisem, například *C:\Program Files* ve Windows nebo */usr/local/bin* na MacOS.</span><span class="sxs-lookup"><span data-stu-id="67bdd-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="67bdd-119">Viz také [zvýšený přístup pro příkazy dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="67bdd-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="67bdd-120">Podrobné pokyny k instalaci jsou k dispozici na [stránce verze GitHubu](https://github.com/dotnet/cli-lab/releases).</span><span class="sxs-lookup"><span data-stu-id="67bdd-120">Detailed installation instructions are available on the [GitHub Releases page](https://github.com/dotnet/cli-lab/releases).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="67bdd-121">Spusťte nástroj</span><span class="sxs-lookup"><span data-stu-id="67bdd-121">Run the tool</span></span>

<span data-ttu-id="67bdd-122">Následující kroky ukazují doporučený postup pro spuštění nástroje pro odinstalaci:</span><span class="sxs-lookup"><span data-stu-id="67bdd-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="67bdd-123">Krok 1 – zobrazení nainstalovaných sad SDK a modulů runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="67bdd-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="67bdd-124">Krok 2 – provedení suchého běhu</span><span class="sxs-lookup"><span data-stu-id="67bdd-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="67bdd-125">Krok 3 – odinstalace sad SDK a modulů runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="67bdd-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="67bdd-126">Krok 4 – odstranění záložní složky NuGet (volitelné)</span><span class="sxs-lookup"><span data-stu-id="67bdd-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="67bdd-127">Krok 1 – zobrazení nainstalovaných sad SDK a modulů runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="67bdd-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="67bdd-128">Příkaz `dotnet-core-uninstall list` vypíše nainstalované sady .NET Core SDK a moduly runtime, které lze pomocí tohoto nástroje odebrat.</span><span class="sxs-lookup"><span data-stu-id="67bdd-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="67bdd-129">Aplikace Visual Studio může vyžadovat některé sady SDK a moduly runtime, které se zobrazí s poznámkou, proč není doporučeno je odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="67bdd-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="67bdd-130">**dotnet – základní – seznam odinstalování**</span><span class="sxs-lookup"><span data-stu-id="67bdd-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="67bdd-131">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="67bdd-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="67bdd-132">Možnosti</span><span class="sxs-lookup"><span data-stu-id="67bdd-132">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="67bdd-133">Windows</span><span class="sxs-lookup"><span data-stu-id="67bdd-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="67bdd-134">Zobrazí seznam všech ASP.NET Core Runtime, které lze pomocí tohoto nástroje odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="67bdd-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="67bdd-135">Zobrazí seznam všech modulů runtime .NET Core a hostitelských sad, které se dají odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="67bdd-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="67bdd-136">Zobrazí seznam všech modulů runtime .NET Core, které se dají odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="67bdd-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="67bdd-137">Zobrazí seznam všech sad SDK .NET Core, které se dají odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="67bdd-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="67bdd-138">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="67bdd-138">Sets the verbosity level.</span></span> <span data-ttu-id="67bdd-139">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="67bdd-140">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="67bdd-141">Obsahuje seznam všech sad SDK a modulů runtime x64 .NET Core, které je možné odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="67bdd-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="67bdd-142">Obsahuje seznam všech sad SDK a modulů runtime x86 .NET Core, které je možné odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="67bdd-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="67bdd-143">macOS</span><span class="sxs-lookup"><span data-stu-id="67bdd-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="67bdd-144">Zobrazí seznam všech modulů runtime .NET Core, které se dají odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="67bdd-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="67bdd-145">Zobrazí seznam všech sad SDK .NET Core, které se dají odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="67bdd-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="67bdd-146">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="67bdd-146">Sets the verbosity level.</span></span> <span data-ttu-id="67bdd-147">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="67bdd-148">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="67bdd-149">Příklady</span><span class="sxs-lookup"><span data-stu-id="67bdd-149">Examples</span></span>

* <span data-ttu-id="67bdd-150">Vypíše všechny sady SDK a moduly runtime .NET Core, které je možné odebrat pomocí tohoto nástroje:</span><span class="sxs-lookup"><span data-stu-id="67bdd-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="67bdd-151">Vypíše všechny sady SDK a moduly runtime x64 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="67bdd-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="67bdd-152">Vypíše všechny sady SDK x86 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="67bdd-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="67bdd-153">Krok 2 – provedení suchého běhu</span><span class="sxs-lookup"><span data-stu-id="67bdd-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="67bdd-154">Příkazy `dotnet-core-uninstall dry-run` a `dotnet-core-uninstall whatif` zobrazují sady SDK a moduly runtime .NET Core, které se odeberou na základě možností, které jsou k dispozici bez provedení odinstalace.</span><span class="sxs-lookup"><span data-stu-id="67bdd-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="67bdd-155">Tyto příkazy jsou synonyma.</span><span class="sxs-lookup"><span data-stu-id="67bdd-155">These commands are synonyms.</span></span>

<span data-ttu-id="67bdd-156">**dotnet-Core – odinstalace suchého běhu a dotnet-Core-Uninstall whatIf**</span><span class="sxs-lookup"><span data-stu-id="67bdd-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="67bdd-157">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="67bdd-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="67bdd-158">Arguments</span><span class="sxs-lookup"><span data-stu-id="67bdd-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="67bdd-159">Zadaná verze, která se má odinstalovat</span><span class="sxs-lookup"><span data-stu-id="67bdd-159">The specified version to uninstall.</span></span> <span data-ttu-id="67bdd-160">Po druhém můžete zobrazit několik verzí, které jsou oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="67bdd-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="67bdd-161">Podporovány jsou také soubory odpovědí.</span><span class="sxs-lookup"><span data-stu-id="67bdd-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="67bdd-162">Soubory odpovědí jsou alternativou k umístění všech verzí do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="67bdd-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="67bdd-163">Jedná se o textové soubory, obvykle s příponou \*. rsp a každá verze je uvedena na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="67bdd-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="67bdd-164">Chcete-li zadat soubor odpovědí pro argument `VERSION`, použijte znak \@ ihned následovaný názvem souboru odpovědi.</span><span class="sxs-lookup"><span data-stu-id="67bdd-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="67bdd-165">Možnosti</span><span class="sxs-lookup"><span data-stu-id="67bdd-165">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="67bdd-166">Windows</span><span class="sxs-lookup"><span data-stu-id="67bdd-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="67bdd-167">Odebere všechny sady SDK a moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="67bdd-168">Odebere jenom sady SDK a modul runtime .NET Core s verzí nižší, než je zadaná verze.</span><span class="sxs-lookup"><span data-stu-id="67bdd-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="67bdd-169">Zadaná verze zůstane nainstalovaná.</span><span class="sxs-lookup"><span data-stu-id="67bdd-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="67bdd-170">Odebere všechny sady SDK a moduly runtime .NET Core s výjimkou uvedených verzí.</span><span class="sxs-lookup"><span data-stu-id="67bdd-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="67bdd-171">Odebere sady SDK a moduly runtime .NET Core s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="67bdd-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="67bdd-172">Odebere sady SDK a moduly runtime .NET Core nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="67bdd-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="67bdd-173">Tato možnost chrání Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="67bdd-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="67bdd-174">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="67bdd-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="67bdd-175">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy kromě nejvyšší verze Preview.</span><span class="sxs-lookup"><span data-stu-id="67bdd-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="67bdd-176">Odebere pouze moduly runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="67bdd-177">Odebere jenom modul runtime .NET Core a hostitelské sady.</span><span class="sxs-lookup"><span data-stu-id="67bdd-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="67bdd-178">Odebere sady SDK a moduly runtime .NET Core, které odpovídají zadané verzi `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="67bdd-179">Odebere jenom modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="67bdd-180">Odebere jenom sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="67bdd-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="67bdd-181">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="67bdd-181">Sets the verbosity level.</span></span> <span data-ttu-id="67bdd-182">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="67bdd-183">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="67bdd-184">Se musí použít s `--sdk`, `--runtime`a `--aspnet-runtime` k odebrání sad nebo runtime sady x64.</span><span class="sxs-lookup"><span data-stu-id="67bdd-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="67bdd-185">Se musí použít s `--sdk`, `--runtime`a `--aspnet-runtime` k odebrání sad SDK nebo modulů runtime x86.</span><span class="sxs-lookup"><span data-stu-id="67bdd-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="67bdd-186">**`--force`** Vynutí odebrání verzí, které mohou být použity v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67bdd-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="67bdd-187">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="67bdd-187">Notes:</span></span>

1. <span data-ttu-id="67bdd-188">Je vyžadován právě jeden z `--sdk`, `--runtime`, `--aspnet-runtime`a `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="67bdd-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`a `[<VERSION>...]` jsou exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="67bdd-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="67bdd-190">Pokud nejsou zadány `--x64` nebo `--x86`, budou odebrány obě platformy x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="67bdd-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="67bdd-191">macOS</span><span class="sxs-lookup"><span data-stu-id="67bdd-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="67bdd-192">Odebere všechny sady SDK a moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="67bdd-193">Odebere sady SDK a moduly runtime .NET Core pod zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="67bdd-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="67bdd-194">Zadaná verze zůstane.</span><span class="sxs-lookup"><span data-stu-id="67bdd-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="67bdd-195">Odebere sady SDK a moduly runtime .NET Core s výjimkou uvedených verzí.</span><span class="sxs-lookup"><span data-stu-id="67bdd-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="67bdd-196">Odebere sady SDK a moduly runtime .NET Core s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="67bdd-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="67bdd-197">Odebere sady SDK a moduly runtime .NET Core nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="67bdd-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="67bdd-198">Tato možnost chrání Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="67bdd-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="67bdd-199">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="67bdd-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="67bdd-200">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy kromě nejvyšší verze Preview.</span><span class="sxs-lookup"><span data-stu-id="67bdd-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="67bdd-201">Odebere sady SDK a moduly runtime .NET Core, které odpovídají zadané verzi `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="67bdd-202">Odebere jenom modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="67bdd-203">Odebere jenom sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="67bdd-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="67bdd-204">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="67bdd-204">Sets the verbosity level.</span></span> <span data-ttu-id="67bdd-205">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="67bdd-206">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="67bdd-207">**`--force`** Vynutí odebrání verzí, které mohou být použity v aplikaci Visual Studio nebo sadách SDK.</span><span class="sxs-lookup"><span data-stu-id="67bdd-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="67bdd-208">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="67bdd-208">Notes:</span></span>

1. <span data-ttu-id="67bdd-209">Je vyžadován právě jeden z `--sdk` a `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="67bdd-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`a `[<VERSION>...]` jsou exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="67bdd-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="67bdd-211">Příklady</span><span class="sxs-lookup"><span data-stu-id="67bdd-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="67bdd-212">Ve výchozím nastavení nejsou sady .NET Core SDK a moduly runtime, které mohou být vyžadovány aplikací Visual Studio nebo jinými sadami SDK, obsaženy v `dotnet-core-uninstall dry-run`m výstupu.</span><span class="sxs-lookup"><span data-stu-id="67bdd-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="67bdd-213">V následujících příkladech nemusí být některé ze zadaných sad SDK a modulu runtime zahrnuty ve výstupu v závislosti na stavu počítače.</span><span class="sxs-lookup"><span data-stu-id="67bdd-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="67bdd-214">Pokud chcete zahrnout všechny sady SDK a moduly runtime, uveďte je explicitně jako argumenty nebo použijte možnost `--force`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="67bdd-215">Suché spuštění odebrání všech modulů runtime .NET Core, které byly nahrazeny vyššími opravami:</span><span class="sxs-lookup"><span data-stu-id="67bdd-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="67bdd-216">Suché spuštění odebrání všech sad .NET Core SDK pod verzí `2.2.301`:</span><span class="sxs-lookup"><span data-stu-id="67bdd-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="67bdd-217">Krok 3 – odinstalace sad SDK a modulů runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="67bdd-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="67bdd-218">`dotnet-core-uninstall remove` odinstaluje sady SDK a moduly runtime .NET Core, které jsou určené kolekcí možností.</span><span class="sxs-lookup"><span data-stu-id="67bdd-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="67bdd-219">Tento nástroj se nedá použít k odinstalování sad SDK a běhových prostředí s verzí 5,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="67bdd-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="67bdd-220">Vzhledem k tomu, že tento nástroj má destruktivní chování, **důrazně** doporučujeme, abyste před spuštěním příkazu Remove nepoužívali suché spuštění.</span><span class="sxs-lookup"><span data-stu-id="67bdd-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="67bdd-221">V suchém běhu se zobrazí informace o tom, jaké sady .NET Core SDK a moduly runtime budou odebrány při použití příkazu `remove`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="67bdd-222">Informace o tom, jak [mám odebrat verzi?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) informace o tom, které sady SDK a moduly runtime je bezpečné odebrat.</span><span class="sxs-lookup"><span data-stu-id="67bdd-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="67bdd-223">Pamatujte na následující upozornění:</span><span class="sxs-lookup"><span data-stu-id="67bdd-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="67bdd-224">Tento nástroj může odinstalovat verze .NET Core SDK, které jsou vyžadovány soubory `global.json` na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="67bdd-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="67bdd-225">Sady .NET Core SDK můžete přeinstalovat ze stránky [stáhnout jádro .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="67bdd-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="67bdd-226">Tento nástroj může odinstalovat verze modulu runtime .NET Core, které jsou vyžadovány závislými aplikacemi architektury na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="67bdd-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="67bdd-227">Moduly runtime .NET Core můžete přeinstalovat na stránce [stáhnout jádro .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="67bdd-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="67bdd-228">Tento nástroj může odinstalovat verze .NET Core SDK a modulu runtime, na kterém se aplikace Visual Studio spoléhá.</span><span class="sxs-lookup"><span data-stu-id="67bdd-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="67bdd-229">Pokud přerušíte instalaci sady Visual Studio, spusťte v instalačním programu sady Visual Studio "opravit" a vraťte se do funkčního stavu.</span><span class="sxs-lookup"><span data-stu-id="67bdd-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="67bdd-230">Ve výchozím nastavení všechny příkazy udržují sady SDK a moduly runtime .NET Core, které mohou být vyžadovány aplikací Visual Studio nebo jinými sadami SDK.</span><span class="sxs-lookup"><span data-stu-id="67bdd-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="67bdd-231">Tyto sady SDK a moduly runtime můžete odinstalovat tak, že je explicitně uvedete jako argumenty nebo pomocí možnosti `--force`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="67bdd-232">Tento nástroj vyžaduje zvýšení oprávnění k odinstalování sad SDK a modulů runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="67bdd-233">Spusťte nástroj z příkazového řádku správce ve Windows a pomocí `sudo` v macOS.</span><span class="sxs-lookup"><span data-stu-id="67bdd-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="67bdd-234">Příkazy `dry-run` a `whatif` nevyžadují zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="67bdd-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="67bdd-235">**dotnet – jádro – odebrání odinstalace**</span><span class="sxs-lookup"><span data-stu-id="67bdd-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="67bdd-236">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="67bdd-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="67bdd-237">Arguments</span><span class="sxs-lookup"><span data-stu-id="67bdd-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="67bdd-238">Zadaná verze, která se má odinstalovat</span><span class="sxs-lookup"><span data-stu-id="67bdd-238">The specified version to uninstall.</span></span> <span data-ttu-id="67bdd-239">Po druhém můžete zobrazit několik verzí, které jsou oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="67bdd-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="67bdd-240">Podporovány jsou také soubory odpovědí.</span><span class="sxs-lookup"><span data-stu-id="67bdd-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="67bdd-241">Soubory odpovědí jsou alternativou k umístění všech verzí do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="67bdd-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="67bdd-242">Jedná se o textové soubory, obvykle s příponou \*. rsp a každá verze je uvedena na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="67bdd-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="67bdd-243">Chcete-li zadat soubor odpovědí pro argument `VERSION`, použijte znak \@ ihned následovaný názvem souboru odpovědi.</span><span class="sxs-lookup"><span data-stu-id="67bdd-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="67bdd-244">Možnosti</span><span class="sxs-lookup"><span data-stu-id="67bdd-244">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="67bdd-245">Windows</span><span class="sxs-lookup"><span data-stu-id="67bdd-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="67bdd-246">Odebere všechny sady SDK a moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="67bdd-247">Odebere jenom sady SDK a modul runtime .NET Core s verzí nižší, než je zadaná verze.</span><span class="sxs-lookup"><span data-stu-id="67bdd-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="67bdd-248">Zadaná verze zůstane nainstalovaná.</span><span class="sxs-lookup"><span data-stu-id="67bdd-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="67bdd-249">Odebere všechny sady SDK a moduly runtime .NET Core s výjimkou uvedených verzí.</span><span class="sxs-lookup"><span data-stu-id="67bdd-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="67bdd-250">Odebere sady SDK a moduly runtime .NET Core s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="67bdd-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="67bdd-251">Odebere sady SDK a moduly runtime .NET Core nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="67bdd-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="67bdd-252">Tato možnost chrání Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="67bdd-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="67bdd-253">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="67bdd-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="67bdd-254">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy kromě nejvyšší verze Preview.</span><span class="sxs-lookup"><span data-stu-id="67bdd-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="67bdd-255">Odebere pouze moduly runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="67bdd-256">Odebere jenom modul runtime .NET Core a hostitelské sady.</span><span class="sxs-lookup"><span data-stu-id="67bdd-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="67bdd-257">Odebere sady SDK a moduly runtime .NET Core, které odpovídají zadané verzi `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="67bdd-258">Odebere jenom modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="67bdd-259">Odebere jenom sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="67bdd-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="67bdd-260">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="67bdd-260">Sets the verbosity level.</span></span> <span data-ttu-id="67bdd-261">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="67bdd-262">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="67bdd-263">Se musí použít s `--sdk`, `--runtime`a `--aspnet-runtime` k odebrání sad nebo runtime sady x64.</span><span class="sxs-lookup"><span data-stu-id="67bdd-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="67bdd-264">Se musí použít s `--sdk`, `--runtime`a `--aspnet-runtime` k odebrání sad SDK nebo modulů runtime x86.</span><span class="sxs-lookup"><span data-stu-id="67bdd-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="67bdd-265">**`-y, --yes`** Provede příkaz bez nutnosti potvrzení Ano nebo ne.</span><span class="sxs-lookup"><span data-stu-id="67bdd-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="67bdd-266">**`--force`** Vynutí odebrání verzí, které mohou být použity v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67bdd-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="67bdd-267">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="67bdd-267">Notes:</span></span>

1. <span data-ttu-id="67bdd-268">Je vyžadován právě jeden z `--sdk`, `--runtime`, `--aspnet-runtime`a `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="67bdd-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`a `[<VERSION>...]` jsou exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="67bdd-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="67bdd-270">Pokud nejsou zadány `--x64` nebo `--x86`, budou odebrány obě platformy x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="67bdd-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="67bdd-271">macOS</span><span class="sxs-lookup"><span data-stu-id="67bdd-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="67bdd-272">Odebere všechny sady SDK a moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="67bdd-273">Odebere sady SDK a moduly runtime .NET Core pod zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="67bdd-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="67bdd-274">Zadaná verze zůstane.</span><span class="sxs-lookup"><span data-stu-id="67bdd-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="67bdd-275">Odebere sady SDK a moduly runtime .NET Core s výjimkou uvedených verzí.</span><span class="sxs-lookup"><span data-stu-id="67bdd-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="67bdd-276">Odebere sady SDK a moduly runtime .NET Core s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="67bdd-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="67bdd-277">Odebere sady SDK a moduly runtime .NET Core nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="67bdd-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="67bdd-278">Tato možnost chrání Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="67bdd-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="67bdd-279">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="67bdd-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="67bdd-280">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy kromě nejvyšší verze Preview.</span><span class="sxs-lookup"><span data-stu-id="67bdd-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="67bdd-281">Odebere sady SDK a moduly runtime .NET Core, které odpovídají zadané verzi `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="67bdd-282">Odebere jenom modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="67bdd-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="67bdd-283">Odebere jenom sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="67bdd-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="67bdd-284">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="67bdd-284">Sets the verbosity level.</span></span> <span data-ttu-id="67bdd-285">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="67bdd-286">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-286">The default value is `normal`.</span></span>

* <span data-ttu-id="67bdd-287">**`-y, --yes`** Provede příkaz bez potvrzení hodnoty Y/N.</span><span class="sxs-lookup"><span data-stu-id="67bdd-287">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="67bdd-288">**`--force`** Vynutí odebrání verzí, které mohou být použity v aplikaci Visual Studio nebo sadách SDK.</span><span class="sxs-lookup"><span data-stu-id="67bdd-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="67bdd-289">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="67bdd-289">Notes:</span></span>

1. <span data-ttu-id="67bdd-290">Je vyžadován právě jeden z `--sdk` a `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="67bdd-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`a `[<VERSION>...]` jsou exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="67bdd-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="67bdd-292">Příklady</span><span class="sxs-lookup"><span data-stu-id="67bdd-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="67bdd-293">Ve výchozím nastavení jsou zachovány sady .NET Core SDK a moduly runtime, které mohou být vyžadovány aplikací Visual Studio nebo jinými sadami SDK.</span><span class="sxs-lookup"><span data-stu-id="67bdd-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="67bdd-294">V následujících příkladech mohou některé ze zadaných sad SDK a modulu runtime zůstat v závislosti na stavu počítače.</span><span class="sxs-lookup"><span data-stu-id="67bdd-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="67bdd-295">Pokud chcete odebrat všechny sady SDK a moduly runtime, uveďte je explicitně jako argumenty nebo použijte možnost `--force`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="67bdd-296">Odeberte všechny moduly runtime .NET Core s výjimkou verze `3.0.0-preview6-27804-01` bez Vyžadování potvrzení a/N:</span><span class="sxs-lookup"><span data-stu-id="67bdd-296">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="67bdd-297">Odeberte všechny sady SDK .NET Core 1,1, aniž by bylo nutné potvrzovat a/n:</span><span class="sxs-lookup"><span data-stu-id="67bdd-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="67bdd-298">Odebrání sady .NET Core 1.1.11 SDK bez výstupu konzoly:</span><span class="sxs-lookup"><span data-stu-id="67bdd-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="67bdd-299">Odeberte všechny sady SDK .NET Core, které je možné bezpečně odebrat tímto nástrojem:</span><span class="sxs-lookup"><span data-stu-id="67bdd-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="67bdd-300">Odebrat všechny sady .NET Core SDK, které mohou být tímto nástrojem odebrány, včetně sad SDK, které mohou být vyžadovány aplikací Visual Studio (nedoporučuje se):</span><span class="sxs-lookup"><span data-stu-id="67bdd-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="67bdd-301">Odeberte všechny sady .NET Core SDK, které jsou zadané v souboru odpovědí `versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="67bdd-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="67bdd-302">Obsah *verze. rsp* je následující:</span><span class="sxs-lookup"><span data-stu-id="67bdd-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="67bdd-303">Krok 4 – odstranění záložní složky NuGet (volitelné)</span><span class="sxs-lookup"><span data-stu-id="67bdd-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="67bdd-304">V některých případech už `NuGetFallbackFolder` nepotřebujete a budete ho chtít odstranit.</span><span class="sxs-lookup"><span data-stu-id="67bdd-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="67bdd-305">Další informace o odstranění této složky najdete v tématu [Odebrání NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="67bdd-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="67bdd-306">Odinstalace nástroje</span><span class="sxs-lookup"><span data-stu-id="67bdd-306">Uninstall the tool</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="67bdd-307">Windows</span><span class="sxs-lookup"><span data-stu-id="67bdd-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="67bdd-308">Otevřete panel **Přidat nebo odebrat programy**.</span><span class="sxs-lookup"><span data-stu-id="67bdd-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="67bdd-309">Vyhledejte `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="67bdd-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="67bdd-310">Vyberte **Odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="67bdd-310">Select **Uninstall**.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="67bdd-311">macOS</span><span class="sxs-lookup"><span data-stu-id="67bdd-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="67bdd-312">Odstraňte stažený soubor *dotnet-Core-Uninstall. tar. gz* z adresáře, kam byl nainstalován.</span><span class="sxs-lookup"><span data-stu-id="67bdd-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="67bdd-313">Pokud rozdělíte obsah tohoto souboru do jiného adresáře, nezapomeňte tento obsah také odstranit.</span><span class="sxs-lookup"><span data-stu-id="67bdd-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
