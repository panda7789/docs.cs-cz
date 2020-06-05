---
title: Odinstalační nástroj
description: Přehled nástroje pro odinstalaci rozhraní .NET Core, což je průvodce nástrojem, který umožňuje řízené vyčištění sad .NET Core SDK a modulů runtime.
author: sfoslund
ms.date: 05/27/2020
ms.openlocfilehash: 4e70fd3438b582bd5a0d6a52d7e58ed5e07f8811
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446903"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="521a5-103">Nástroj pro odinstalaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="521a5-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="521a5-104">[Nástroj pro odinstalaci .NET Core](https://aka.ms/dotnet-core-uninstall-tool) ( `dotnet-core-uninstall` ) umožňuje odebrat sady SDK a moduly runtime .NET Core ze systému.</span><span class="sxs-lookup"><span data-stu-id="521a5-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="521a5-105">K dispozici je kolekce možností, které určují verze, které chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="521a5-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="521a5-106">Nástroj podporuje Windows a macOS.</span><span class="sxs-lookup"><span data-stu-id="521a5-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="521a5-107">Linux není aktuálně podporován.</span><span class="sxs-lookup"><span data-stu-id="521a5-107">Linux is currently not supported.</span></span>

<span data-ttu-id="521a5-108">V systému Windows může nástroj odinstalovat pouze sady SDK a moduly runtime, které byly nainstalovány pomocí jednoho z následujících instalačních programů:</span><span class="sxs-lookup"><span data-stu-id="521a5-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="521a5-109">Instalační program .NET Core SDK a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="521a5-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="521a5-110">Instalační program sady Visual Studio ve verzích starších než Visual Studio 2019 verze 16,3.</span><span class="sxs-lookup"><span data-stu-id="521a5-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="521a5-111">V macOS může nástroj odinstalovat jenom sady SDK a moduly runtime umístěné ve složce */usr/local/share/dotnet* .</span><span class="sxs-lookup"><span data-stu-id="521a5-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="521a5-112">Z důvodu těchto omezení nemusí nástroj na počítači odinstalovat všechny sady .NET Core SDK a moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="521a5-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="521a5-113">Pomocí `dotnet --info` příkazu můžete najít všechny nainstalované sady .NET Core SDK a moduly runtime, včetně těchto sad SDK a modulu runtime, které tento nástroj nemůže odebrat.</span><span class="sxs-lookup"><span data-stu-id="521a5-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="521a5-114">`dotnet-core-uninstall list`Příkaz zobrazí, které sady SDK je možné odinstalovat pomocí nástroje.</span><span class="sxs-lookup"><span data-stu-id="521a5-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="521a5-115">Instalace nástroje</span><span class="sxs-lookup"><span data-stu-id="521a5-115">Install the tool</span></span>

<span data-ttu-id="521a5-116">Nástroj pro odinstalaci rozhraní .NET Core si můžete stáhnout [odsud a najít](https://aka.ms/dotnet-core-uninstall-tool) zdrojový kód v úložišti GitHub [/CLI-Lab](https://github.com/dotnet/cli-lab) .</span><span class="sxs-lookup"><span data-stu-id="521a5-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="521a5-117">Tento nástroj vyžaduje zvýšení oprávnění k odinstalování sad SDK a modulů runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="521a5-118">Proto by měl být nainstalován v adresáři chráněném zápisem, například *C:\Program Files* ve Windows nebo */usr/local/bin* na MacOS.</span><span class="sxs-lookup"><span data-stu-id="521a5-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="521a5-119">Viz také [zvýšený přístup pro příkazy dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="521a5-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="521a5-120">Další informace najdete v [podrobných pokynech k instalaci](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="521a5-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="521a5-121">Spusťte nástroj.</span><span class="sxs-lookup"><span data-stu-id="521a5-121">Run the tool</span></span>

<span data-ttu-id="521a5-122">Následující kroky ukazují doporučený postup pro spuštění nástroje pro odinstalaci:</span><span class="sxs-lookup"><span data-stu-id="521a5-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="521a5-123">Krok 1 – zobrazení nainstalovaných sad SDK a modulů runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="521a5-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="521a5-124">Krok 2 – provedení suchého běhu</span><span class="sxs-lookup"><span data-stu-id="521a5-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="521a5-125">Krok 3 – odinstalace sad SDK a modulů runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="521a5-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="521a5-126">Krok 4 – odstranění záložní složky NuGet (volitelné)</span><span class="sxs-lookup"><span data-stu-id="521a5-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="521a5-127">Krok 1 – zobrazení nainstalovaných sad SDK a modulů runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="521a5-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="521a5-128">`dotnet-core-uninstall list`Příkaz vypíše nainstalované sady .NET Core SDK a moduly runtime, které lze pomocí tohoto nástroje odebrat.</span><span class="sxs-lookup"><span data-stu-id="521a5-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="521a5-129">Aplikace Visual Studio může vyžadovat některé sady SDK a moduly runtime, které se zobrazí s poznámkou, proč není doporučeno je odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="521a5-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="521a5-130">Výstup `dotnet-core-uninstall list` příkazu se neshoduje se seznamem nainstalovaných verzí ve `dotnet --info` většině případů ve výstupu.</span><span class="sxs-lookup"><span data-stu-id="521a5-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="521a5-131">Konkrétně tento nástroj nebude zobrazovat verze nainstalované soubory ZIP nebo spravované sadou Visual Studio (jakákoli verze nainstalovaná se sadou Visual Studio 2019 16,3 nebo novější).</span><span class="sxs-lookup"><span data-stu-id="521a5-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="521a5-132">Jedním ze způsobů, jak zjistit, jestli je verze spravovaná pomocí sady Visual Studio, je zobrazit v `Add or Remove Programs` , kde spravované verze Visual studia jsou označené jako v jejich zobrazovaných názvech.</span><span class="sxs-lookup"><span data-stu-id="521a5-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="521a5-133">**dotnet – základní – seznam odinstalování**</span><span class="sxs-lookup"><span data-stu-id="521a5-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="521a5-134">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="521a5-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="521a5-135">Možnosti</span><span class="sxs-lookup"><span data-stu-id="521a5-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="521a5-136">Windows</span><span class="sxs-lookup"><span data-stu-id="521a5-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="521a5-137">Zobrazí seznam všech ASP.NET Core Runtime, které lze pomocí tohoto nástroje odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="521a5-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="521a5-138">Zobrazí seznam všech hostitelských sad .NET Core, které mohou být pomocí tohoto nástroje odinstalovány.</span><span class="sxs-lookup"><span data-stu-id="521a5-138">Lists all the .NET Core hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="521a5-139">Zobrazí seznam všech modulů runtime .NET Core, které se dají odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="521a5-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="521a5-140">Zobrazí seznam všech sad SDK .NET Core, které se dají odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="521a5-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="521a5-141">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="521a5-141">Sets the verbosity level.</span></span> <span data-ttu-id="521a5-142">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="521a5-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="521a5-143">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="521a5-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="521a5-144">Obsahuje seznam všech sad SDK a modulů runtime x64 .NET Core, které je možné odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="521a5-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="521a5-145">Obsahuje seznam všech sad SDK a modulů runtime x86 .NET Core, které je možné odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="521a5-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="521a5-146">macOS</span><span class="sxs-lookup"><span data-stu-id="521a5-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="521a5-147">Zobrazí seznam všech modulů runtime .NET Core, které se dají odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="521a5-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="521a5-148">Zobrazí seznam všech sad SDK .NET Core, které se dají odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="521a5-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="521a5-149">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="521a5-149">Sets the verbosity level.</span></span> <span data-ttu-id="521a5-150">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="521a5-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="521a5-151">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="521a5-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="521a5-152">Příklady</span><span class="sxs-lookup"><span data-stu-id="521a5-152">Examples</span></span>

* <span data-ttu-id="521a5-153">Vypíše všechny sady SDK a moduly runtime .NET Core, které je možné odebrat pomocí tohoto nástroje:</span><span class="sxs-lookup"><span data-stu-id="521a5-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="521a5-154">Vypíše všechny sady SDK a moduly runtime x64 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="521a5-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="521a5-155">Vypíše všechny sady SDK x86 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="521a5-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="521a5-156">Krok 2 – provedení suchého běhu</span><span class="sxs-lookup"><span data-stu-id="521a5-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="521a5-157">`dotnet-core-uninstall dry-run`Příkazy a `dotnet-core-uninstall whatif` zobrazují sady .NET Core SDK a moduly runtime, které budou odebrány na základě možností, které jsou k dispozici bez provedení odinstalace.</span><span class="sxs-lookup"><span data-stu-id="521a5-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="521a5-158">Tyto příkazy jsou synonyma.</span><span class="sxs-lookup"><span data-stu-id="521a5-158">These commands are synonyms.</span></span>

<span data-ttu-id="521a5-159">**dotnet-Core – odinstalace suchého běhu a dotnet-Core-Uninstall whatIf**</span><span class="sxs-lookup"><span data-stu-id="521a5-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="521a5-160">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="521a5-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="521a5-161">Arguments</span><span class="sxs-lookup"><span data-stu-id="521a5-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="521a5-162">Zadaná verze, která se má odinstalovat</span><span class="sxs-lookup"><span data-stu-id="521a5-162">The specified version to uninstall.</span></span> <span data-ttu-id="521a5-163">Po druhém můžete zobrazit několik verzí, které jsou oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="521a5-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="521a5-164">Podporovány jsou také soubory odpovědí.</span><span class="sxs-lookup"><span data-stu-id="521a5-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="521a5-165">Soubory odpovědí jsou alternativou k umístění všech verzí do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="521a5-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="521a5-166">Jsou to textové soubory, obvykle s \* příponou. rsp a každá verze je uvedena na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="521a5-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="521a5-167">Chcete-li zadat soubor odpovědí pro `VERSION` argument, použijte \@ znak ihned následovaný názvem souboru odpovědi.</span><span class="sxs-lookup"><span data-stu-id="521a5-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="521a5-168">Možnosti</span><span class="sxs-lookup"><span data-stu-id="521a5-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="521a5-169">Windows</span><span class="sxs-lookup"><span data-stu-id="521a5-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="521a5-170">Odebere všechny sady SDK a moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="521a5-171">Odebere jenom sady SDK a modul runtime .NET Core s verzí nižší, než je zadaná verze.</span><span class="sxs-lookup"><span data-stu-id="521a5-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="521a5-172">Zadaná verze zůstane nainstalovaná.</span><span class="sxs-lookup"><span data-stu-id="521a5-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="521a5-173">Odebere všechny sady SDK a moduly runtime .NET Core s výjimkou uvedených verzí.</span><span class="sxs-lookup"><span data-stu-id="521a5-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="521a5-174">Odebere sady SDK a moduly runtime .NET Core s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="521a5-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="521a5-175">Odebere sady SDK a moduly runtime .NET Core nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="521a5-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="521a5-176">Tato možnost chrání Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="521a5-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="521a5-177">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="521a5-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="521a5-178">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy kromě nejvyšší verze Preview.</span><span class="sxs-lookup"><span data-stu-id="521a5-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="521a5-179">Odebere pouze moduly runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="521a5-180">Odebere jenom modul runtime .NET Core a hostitelské sady.</span><span class="sxs-lookup"><span data-stu-id="521a5-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="521a5-181">Odebere sady .NET Core SDK a moduly runtime, které odpovídají zadané `major.minor` verzi.</span><span class="sxs-lookup"><span data-stu-id="521a5-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="521a5-182">Odebere jenom modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="521a5-183">Odebere jenom sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="521a5-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="521a5-184">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="521a5-184">Sets the verbosity level.</span></span> <span data-ttu-id="521a5-185">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="521a5-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="521a5-186">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="521a5-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="521a5-187">Se musí použít s `--sdk` , `--runtime` a `--aspnet-runtime` pro odebrání sad nebo modulů runtime x64.</span><span class="sxs-lookup"><span data-stu-id="521a5-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="521a5-188">Se musí použít s `--sdk` , `--runtime` a `--aspnet-runtime` k odebrání sad SDK nebo modulů runtime x86.</span><span class="sxs-lookup"><span data-stu-id="521a5-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="521a5-189">**`--force`** Vynutí odebrání verzí, které mohou být použity v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="521a5-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="521a5-190">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="521a5-190">Notes:</span></span>

1. <span data-ttu-id="521a5-191">Je vyžadován právě jeden z `--sdk` , `--runtime` , a `--aspnet-runtime` `--hosting-bundle` .</span><span class="sxs-lookup"><span data-stu-id="521a5-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="521a5-192">`--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` a `[<VERSION>...]` jsou exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="521a5-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="521a5-193">Pokud `--x64` `--x86` nejsou zadány, budou odebrány obě platformy x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="521a5-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="521a5-194">macOS</span><span class="sxs-lookup"><span data-stu-id="521a5-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="521a5-195">Odebere všechny sady SDK a moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="521a5-196">Odebere sady SDK a moduly runtime .NET Core pod zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="521a5-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="521a5-197">Zadaná verze zůstane.</span><span class="sxs-lookup"><span data-stu-id="521a5-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="521a5-198">Odebere sady SDK a moduly runtime .NET Core s výjimkou uvedených verzí.</span><span class="sxs-lookup"><span data-stu-id="521a5-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="521a5-199">Odebere sady SDK a moduly runtime .NET Core s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="521a5-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="521a5-200">Odebere sady SDK a moduly runtime .NET Core nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="521a5-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="521a5-201">Tato možnost chrání Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="521a5-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="521a5-202">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="521a5-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="521a5-203">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy kromě nejvyšší verze Preview.</span><span class="sxs-lookup"><span data-stu-id="521a5-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="521a5-204">Odebere sady .NET Core SDK a moduly runtime, které odpovídají zadané `major.minor` verzi.</span><span class="sxs-lookup"><span data-stu-id="521a5-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="521a5-205">Odebere jenom modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="521a5-206">Odebere jenom sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="521a5-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="521a5-207">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="521a5-207">Sets the verbosity level.</span></span> <span data-ttu-id="521a5-208">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="521a5-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="521a5-209">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="521a5-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="521a5-210">**`--force`** Vynutí odebrání verzí, které mohou být použity v aplikaci Visual Studio nebo sadách SDK.</span><span class="sxs-lookup"><span data-stu-id="521a5-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="521a5-211">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="521a5-211">Notes:</span></span>

1. <span data-ttu-id="521a5-212">Je vyžadován právě jeden z `--sdk` a `--runtime` .</span><span class="sxs-lookup"><span data-stu-id="521a5-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="521a5-213">`--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` a `[<VERSION>...]` jsou exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="521a5-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="521a5-214">Příklady</span><span class="sxs-lookup"><span data-stu-id="521a5-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="521a5-215">Ve výchozím nastavení nejsou sady .NET Core SDK a moduly runtime, které mohou být vyžadovány aplikací Visual Studio nebo jinými sadami SDK, zahrnuty ve `dotnet-core-uninstall dry-run` výstupu.</span><span class="sxs-lookup"><span data-stu-id="521a5-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="521a5-216">V následujících příkladech nemusí být některé ze zadaných sad SDK a modulu runtime zahrnuty ve výstupu v závislosti na stavu počítače.</span><span class="sxs-lookup"><span data-stu-id="521a5-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="521a5-217">Pokud chcete zahrnout všechny sady SDK a moduly runtime, uveďte je explicitně jako argumenty nebo použijte `--force` možnost.</span><span class="sxs-lookup"><span data-stu-id="521a5-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="521a5-218">Suché spuštění odebrání všech modulů runtime .NET Core, které byly nahrazeny vyššími opravami:</span><span class="sxs-lookup"><span data-stu-id="521a5-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="521a5-219">Suché spuštění odebrání všech sad .NET Core SDK pod verzí `2.2.301` :</span><span class="sxs-lookup"><span data-stu-id="521a5-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="521a5-220">Krok 3 – odinstalace sad SDK a modulů runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="521a5-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="521a5-221">`dotnet-core-uninstall remove`odinstaluje sady SDK a moduly runtime .NET Core, které jsou určené kolekcí možností.</span><span class="sxs-lookup"><span data-stu-id="521a5-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="521a5-222">Tento nástroj se nedá použít k odinstalování sad SDK a běhových prostředí s verzí 5,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="521a5-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="521a5-223">Vzhledem k tomu, že tento nástroj má destruktivní chování, **důrazně** doporučujeme, abyste před spuštěním příkazu Remove nepoužívali suché spuštění.</span><span class="sxs-lookup"><span data-stu-id="521a5-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="521a5-224">V suchém běhu se zobrazí informace o tom, jaké sady .NET Core SDK a moduly runtime budou odebrány při použití `remove` příkazu.</span><span class="sxs-lookup"><span data-stu-id="521a5-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="521a5-225">Informace o tom, jak [mám odebrat verzi?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) informace o tom, které sady SDK a moduly runtime je bezpečné odebrat.</span><span class="sxs-lookup"><span data-stu-id="521a5-225">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="521a5-226">Pamatujte na následující upozornění:</span><span class="sxs-lookup"><span data-stu-id="521a5-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="521a5-227">Tento nástroj může odinstalovat verze .NET Core SDK, které jsou vyžadovány `global.json` soubory na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="521a5-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="521a5-228">Sady .NET Core SDK můžete přeinstalovat ze stránky [stáhnout jádro .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="521a5-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="521a5-229">Tento nástroj může odinstalovat verze modulu runtime .NET Core, které jsou vyžadovány závislými aplikacemi architektury na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="521a5-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="521a5-230">Moduly runtime .NET Core můžete přeinstalovat na stránce [stáhnout jádro .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="521a5-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="521a5-231">Tento nástroj může odinstalovat verze .NET Core SDK a modulu runtime, na kterém se aplikace Visual Studio spoléhá.</span><span class="sxs-lookup"><span data-stu-id="521a5-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="521a5-232">Pokud přerušíte instalaci sady Visual Studio, spusťte v instalačním programu sady Visual Studio "opravit" a vraťte se do funkčního stavu.</span><span class="sxs-lookup"><span data-stu-id="521a5-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="521a5-233">Ve výchozím nastavení všechny příkazy udržují sady SDK a moduly runtime .NET Core, které mohou být vyžadovány aplikací Visual Studio nebo jinými sadami SDK.</span><span class="sxs-lookup"><span data-stu-id="521a5-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="521a5-234">Tyto sady SDK a moduly runtime můžete odinstalovat tak, že je explicitně uvedete jako argumenty nebo pomocí `--force` Možnosti.</span><span class="sxs-lookup"><span data-stu-id="521a5-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="521a5-235">Tento nástroj vyžaduje zvýšení oprávnění k odinstalování sad SDK a modulů runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="521a5-236">Spusťte nástroj v příkazovém řádku správce ve Windows a v `sudo` MacOS.</span><span class="sxs-lookup"><span data-stu-id="521a5-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="521a5-237">`dry-run`Příkazy a `whatif` nevyžadují zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="521a5-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="521a5-238">**dotnet – jádro – odebrání odinstalace**</span><span class="sxs-lookup"><span data-stu-id="521a5-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="521a5-239">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="521a5-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="521a5-240">Arguments</span><span class="sxs-lookup"><span data-stu-id="521a5-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="521a5-241">Zadaná verze, která se má odinstalovat</span><span class="sxs-lookup"><span data-stu-id="521a5-241">The specified version to uninstall.</span></span> <span data-ttu-id="521a5-242">Po druhém můžete zobrazit několik verzí, které jsou oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="521a5-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="521a5-243">Podporovány jsou také soubory odpovědí.</span><span class="sxs-lookup"><span data-stu-id="521a5-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="521a5-244">Soubory odpovědí jsou alternativou k umístění všech verzí do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="521a5-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="521a5-245">Jsou to textové soubory, obvykle s \* příponou. rsp a každá verze je uvedena na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="521a5-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="521a5-246">Chcete-li zadat soubor odpovědí pro `VERSION` argument, použijte \@ znak ihned následovaný názvem souboru odpovědi.</span><span class="sxs-lookup"><span data-stu-id="521a5-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="521a5-247">Možnosti</span><span class="sxs-lookup"><span data-stu-id="521a5-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="521a5-248">Windows</span><span class="sxs-lookup"><span data-stu-id="521a5-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="521a5-249">Odebere všechny sady SDK a moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="521a5-250">Odebere jenom sady SDK a modul runtime .NET Core s verzí nižší, než je zadaná verze.</span><span class="sxs-lookup"><span data-stu-id="521a5-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="521a5-251">Zadaná verze zůstane nainstalovaná.</span><span class="sxs-lookup"><span data-stu-id="521a5-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="521a5-252">Odebere všechny sady SDK a moduly runtime .NET Core s výjimkou uvedených verzí.</span><span class="sxs-lookup"><span data-stu-id="521a5-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="521a5-253">Odebere sady SDK a moduly runtime .NET Core s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="521a5-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="521a5-254">Odebere sady SDK a moduly runtime .NET Core nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="521a5-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="521a5-255">Tato možnost chrání Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="521a5-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="521a5-256">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="521a5-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="521a5-257">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy kromě nejvyšší verze Preview.</span><span class="sxs-lookup"><span data-stu-id="521a5-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="521a5-258">Odebere pouze moduly runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="521a5-259">Odebere jenom hostitelské sady .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-259">Removes .NET Core hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="521a5-260">Odebere sady .NET Core SDK a moduly runtime, které odpovídají zadané `major.minor` verzi.</span><span class="sxs-lookup"><span data-stu-id="521a5-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="521a5-261">Odebere jenom modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="521a5-262">Odebere jenom sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="521a5-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="521a5-263">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="521a5-263">Sets the verbosity level.</span></span> <span data-ttu-id="521a5-264">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="521a5-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="521a5-265">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="521a5-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="521a5-266">Se musí použít s `--sdk` , `--runtime` a `--aspnet-runtime` pro odebrání sad nebo modulů runtime x64.</span><span class="sxs-lookup"><span data-stu-id="521a5-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="521a5-267">Se musí použít s `--sdk` , `--runtime` a `--aspnet-runtime` k odebrání sad SDK nebo modulů runtime x86.</span><span class="sxs-lookup"><span data-stu-id="521a5-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="521a5-268">**`-y, --yes`** Provede příkaz bez nutnosti potvrzení Ano nebo ne.</span><span class="sxs-lookup"><span data-stu-id="521a5-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="521a5-269">**`--force`** Vynutí odebrání verzí, které mohou být použity v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="521a5-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="521a5-270">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="521a5-270">Notes:</span></span>

1. <span data-ttu-id="521a5-271">Je vyžadován právě jeden z `--sdk` , `--runtime` , a `--aspnet-runtime` `--hosting-bundle` .</span><span class="sxs-lookup"><span data-stu-id="521a5-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="521a5-272">`--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` a `[<VERSION>...]` jsou exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="521a5-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="521a5-273">Pokud `--x64` `--x86` nejsou zadány, budou odebrány obě platformy x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="521a5-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="521a5-274">macOS</span><span class="sxs-lookup"><span data-stu-id="521a5-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="521a5-275">Odebere všechny sady SDK a moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="521a5-276">Odebere sady SDK a moduly runtime .NET Core pod zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="521a5-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="521a5-277">Zadaná verze zůstane.</span><span class="sxs-lookup"><span data-stu-id="521a5-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="521a5-278">Odebere sady SDK a moduly runtime .NET Core s výjimkou uvedených verzí.</span><span class="sxs-lookup"><span data-stu-id="521a5-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="521a5-279">Odebere sady SDK a moduly runtime .NET Core s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="521a5-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="521a5-280">Odebere sady SDK a moduly runtime .NET Core nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="521a5-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="521a5-281">Tato možnost chrání Global. JSON.</span><span class="sxs-lookup"><span data-stu-id="521a5-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="521a5-282">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="521a5-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="521a5-283">Odebere sady .NET Core SDK a moduly runtime označené jako náhledy kromě nejvyšší verze Preview.</span><span class="sxs-lookup"><span data-stu-id="521a5-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="521a5-284">Odebere sady .NET Core SDK a moduly runtime, které odpovídají zadané `major.minor` verzi.</span><span class="sxs-lookup"><span data-stu-id="521a5-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="521a5-285">Odebere jenom modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="521a5-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="521a5-286">Odebere jenom sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="521a5-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="521a5-287">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="521a5-287">Sets the verbosity level.</span></span> <span data-ttu-id="521a5-288">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="521a5-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="521a5-289">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="521a5-289">The default value is `normal`.</span></span>

* <span data-ttu-id="521a5-290">**`-y, --yes`** Provede příkaz bez potvrzení hodnoty Y/N.</span><span class="sxs-lookup"><span data-stu-id="521a5-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="521a5-291">**`--force`** Vynutí odebrání verzí, které mohou být použity v aplikaci Visual Studio nebo sadách SDK.</span><span class="sxs-lookup"><span data-stu-id="521a5-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="521a5-292">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="521a5-292">Notes:</span></span>

1. <span data-ttu-id="521a5-293">Je vyžadován právě jeden z `--sdk` a `--runtime` .</span><span class="sxs-lookup"><span data-stu-id="521a5-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="521a5-294">`--all`, `--all-below` , `--all-but` , `--all-but-latest` , `--all-lower-patches` , `--all-previews` , `--all-previews-but-latest` , `--major-minor` a `[<VERSION>...]` jsou exkluzivní.</span><span class="sxs-lookup"><span data-stu-id="521a5-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="521a5-295">Příklady</span><span class="sxs-lookup"><span data-stu-id="521a5-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="521a5-296">Ve výchozím nastavení jsou zachovány sady .NET Core SDK a moduly runtime, které mohou být vyžadovány aplikací Visual Studio nebo jinými sadami SDK.</span><span class="sxs-lookup"><span data-stu-id="521a5-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="521a5-297">V následujících příkladech mohou některé ze zadaných sad SDK a modulu runtime zůstat v závislosti na stavu počítače.</span><span class="sxs-lookup"><span data-stu-id="521a5-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="521a5-298">Pokud chcete odebrat všechny sady SDK a moduly runtime, uveďte je explicitně jako argumenty nebo použijte `--force` možnost.</span><span class="sxs-lookup"><span data-stu-id="521a5-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="521a5-299">Odeberte všechny moduly runtime .NET Core s výjimkou verze `3.0.0-preview6-27804-01` bez vyžadování a/N potvrzení:</span><span class="sxs-lookup"><span data-stu-id="521a5-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="521a5-300">Odeberte všechny sady SDK .NET Core 1,1, aniž by bylo nutné potvrzovat a/n:</span><span class="sxs-lookup"><span data-stu-id="521a5-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="521a5-301">Odebrání sady .NET Core 1.1.11 SDK bez výstupu konzoly:</span><span class="sxs-lookup"><span data-stu-id="521a5-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="521a5-302">Odeberte všechny sady SDK .NET Core, které je možné bezpečně odebrat tímto nástrojem:</span><span class="sxs-lookup"><span data-stu-id="521a5-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="521a5-303">Odebrat všechny sady .NET Core SDK, které mohou být tímto nástrojem odebrány, včetně sad SDK, které mohou být vyžadovány aplikací Visual Studio (nedoporučuje se):</span><span class="sxs-lookup"><span data-stu-id="521a5-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="521a5-304">Odebrat všechny sady .NET Core SDK, které jsou uvedené v souboru odpovědí`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="521a5-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="521a5-305">Obsah *verze. rsp* je následující:</span><span class="sxs-lookup"><span data-stu-id="521a5-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="521a5-306">Krok 4 – odstranění záložní složky NuGet (volitelné)</span><span class="sxs-lookup"><span data-stu-id="521a5-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="521a5-307">V některých případech už nepotřebujete a chcete, `NuGetFallbackFolder` aby ho bylo možné odstranit.</span><span class="sxs-lookup"><span data-stu-id="521a5-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="521a5-308">Další informace o odstranění této složky najdete v tématu [Odebrání NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="521a5-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="521a5-309">Odinstalace nástroje</span><span class="sxs-lookup"><span data-stu-id="521a5-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="521a5-310">Windows</span><span class="sxs-lookup"><span data-stu-id="521a5-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="521a5-311">Otevřete panel **Přidat nebo odebrat programy**.</span><span class="sxs-lookup"><span data-stu-id="521a5-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="521a5-312">Vyhledejte `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="521a5-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="521a5-313">Vyberte **odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="521a5-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="521a5-314">macOS</span><span class="sxs-lookup"><span data-stu-id="521a5-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="521a5-315">Odstraňte stažený soubor *dotnet-Core-Uninstall. tar. gz* z adresáře, kam byl nainstalován.</span><span class="sxs-lookup"><span data-stu-id="521a5-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="521a5-316">Pokud rozdělíte obsah tohoto souboru do jiného adresáře, nezapomeňte tento obsah také odstranit.</span><span class="sxs-lookup"><span data-stu-id="521a5-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
