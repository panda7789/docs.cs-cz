---
title: Nástroj odinstalace
description: Přehled nástroje .NET Core Uninstall Tool, což je nástroj s průvodcem, který umožňuje řízené vyčištění sad SDK jádra .NET a runčase.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 816aef6ab8bc0e51bb8befb14fde60513d4fadfc
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507318"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="9ef02-103">Nástroj pro odinstalaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="9ef02-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="9ef02-104">[Nástroj .NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) umožňuje odebrat sady .NET Core SDK a runtimes ze systému.</span><span class="sxs-lookup"><span data-stu-id="9ef02-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="9ef02-105">K dispozici je kolekce možností, které určují, které verze chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="9ef02-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="9ef02-106">Nástroj podporuje Windows a macOS.</span><span class="sxs-lookup"><span data-stu-id="9ef02-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="9ef02-107">Linux není v současné době podporován.</span><span class="sxs-lookup"><span data-stu-id="9ef02-107">Linux is currently not supported.</span></span>

<span data-ttu-id="9ef02-108">V systému Windows může nástroj odinstalovat pouze sady SDK a runtimes, které byly nainstalovány pomocí jednoho z následujících instalačních programů:</span><span class="sxs-lookup"><span data-stu-id="9ef02-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="9ef02-109">Instalační program .NET Core SDK a runtime.</span><span class="sxs-lookup"><span data-stu-id="9ef02-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="9ef02-110">Instalační program sady Visual Studio ve verzích starších než Visual Studio 2019 verze 16.3.</span><span class="sxs-lookup"><span data-stu-id="9ef02-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="9ef02-111">V systému macOS může nástroj odinstalovat pouze sady SDK a runtimes umístěné ve složce */usr/local/share/dotnet.*</span><span class="sxs-lookup"><span data-stu-id="9ef02-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="9ef02-112">Z důvodu těchto omezení nemusí být nástroj schopen odinstalovat všechny sady .NET Core SDK a runtimes v počítači.</span><span class="sxs-lookup"><span data-stu-id="9ef02-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="9ef02-113">Pomocí příkazu `dotnet --info` můžete najít všechny nainstalované sady .NET Core SDK a runtimes, včetně těchto sad SDK a runtimes, které tento nástroj nelze odebrat.</span><span class="sxs-lookup"><span data-stu-id="9ef02-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="9ef02-114">Příkaz `dotnet-core-uninstall list` zobrazí sady SDK, které lze pomocí nástroje odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="9ef02-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="9ef02-115">Instalace nástroje</span><span class="sxs-lookup"><span data-stu-id="9ef02-115">Install the tool</span></span>

<span data-ttu-id="9ef02-116">Zde si můžete stáhnout nástroj .NET Core Uninstall Tool [a](https://aka.ms/dotnet-core-uninstall-tool) zdrojový kód najdete v úložišti GitHub [dotnet/cli-lab.](https://github.com/dotnet/cli-lab)</span><span class="sxs-lookup"><span data-stu-id="9ef02-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="9ef02-117">Nástroj vyžaduje zvýšení odinstalace sad SDK jádra .NET a runčase.</span><span class="sxs-lookup"><span data-stu-id="9ef02-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="9ef02-118">Proto by měl být nainstalován v adresáři chráněném pro zápis, například *C:\Program Files* v systému Windows nebo */usr/local/bin* v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="9ef02-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="9ef02-119">Viz také [zvýšený přístup pro příkazy dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="9ef02-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="9ef02-120">Další informace naleznete v [podrobných pokynech k instalaci](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="9ef02-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="9ef02-121">Spuštění nástroje</span><span class="sxs-lookup"><span data-stu-id="9ef02-121">Run the tool</span></span>

<span data-ttu-id="9ef02-122">Následující kroky ukazují doporučený postup pro spuštění nástroje pro odinstalaci:</span><span class="sxs-lookup"><span data-stu-id="9ef02-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="9ef02-123">Krok 1 – Zobrazení nainstalovaných sad SDK .NET Core A RunTimes</span><span class="sxs-lookup"><span data-stu-id="9ef02-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="9ef02-124">Krok 2 - Proveďte suchý běh</span><span class="sxs-lookup"><span data-stu-id="9ef02-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="9ef02-125">Krok 3 – Odinstalace sad SDK jádra .NET a runčase</span><span class="sxs-lookup"><span data-stu-id="9ef02-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="9ef02-126">Krok 4 – Odstranění záložní složky NuGet (volitelné)</span><span class="sxs-lookup"><span data-stu-id="9ef02-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="9ef02-127">Krok 1 – Zobrazení nainstalovaných sad SDK .NET Core A RunTimes</span><span class="sxs-lookup"><span data-stu-id="9ef02-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="9ef02-128">Příkaz `dotnet-core-uninstall list` obsahuje seznam nainstalovaných sad SDK jádra .NET a dob běhu, které lze pomocí tohoto nástroje odebrat.</span><span class="sxs-lookup"><span data-stu-id="9ef02-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="9ef02-129">Některé sady SDK a runtimes mohou být vyžadovány sadou Visual Studio a zobrazí se s poznámkou, proč se nedoporučuje je odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="9ef02-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="9ef02-130">Výstup příkazu `dotnet-core-uninstall list` nebude odpovídat seznamu nainstalovaných verzí ve `dotnet --info` výstupu ve většině případů.</span><span class="sxs-lookup"><span data-stu-id="9ef02-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="9ef02-131">Konkrétně tento nástroj nebude zobrazovat verze nainstalované soubory ZIP nebo spravované aplikací Visual Studio (libovolná verze nainstalovaná v sadě Visual Studio 2019 16.3 nebo novější).</span><span class="sxs-lookup"><span data-stu-id="9ef02-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="9ef02-132">Jedním ze způsobů, jak zkontrolovat, zda je verze `Add or Remove Programs`spravována visual studio je zobrazit v aplikaci , kde Visual Studio spravované verze jsou označeny jako takové v jejich zobrazované názvy.</span><span class="sxs-lookup"><span data-stu-id="9ef02-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="9ef02-133">**seznam odinstalace dotnet-core-uninstall**</span><span class="sxs-lookup"><span data-stu-id="9ef02-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9ef02-134">Synopse</span><span class="sxs-lookup"><span data-stu-id="9ef02-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="9ef02-135">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9ef02-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="9ef02-136">Windows</span><span class="sxs-lookup"><span data-stu-id="9ef02-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="9ef02-137">Zobrazí seznam všech ASP.NET za běhu jádra, které lze odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="9ef02-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="9ef02-138">Zobrazí seznam všech runtime rozhraní .NET Core a hostingových balíčků, které lze odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="9ef02-138">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="9ef02-139">Zobrazí seznam všech runčasů jádra .NET, které lze tímto nástrojem odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="9ef02-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="9ef02-140">Zobrazí seznam všech sad SDK jádra .NET, které lze tímto nástrojem odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="9ef02-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9ef02-141">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="9ef02-141">Sets the verbosity level.</span></span> <span data-ttu-id="9ef02-142">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="9ef02-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9ef02-143">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="9ef02-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="9ef02-144">Zobrazí seznam všech sad X64 .NET Core SDK a runtimes, které lze odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="9ef02-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="9ef02-145">Zobrazí seznam všech sad X86 .NET Core SDK a runtimes, které lze odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="9ef02-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="9ef02-146">Macos</span><span class="sxs-lookup"><span data-stu-id="9ef02-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="9ef02-147">Zobrazí seznam všech runčasů jádra .NET, které lze tímto nástrojem odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="9ef02-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="9ef02-148">Zobrazí seznam všech sad SDK jádra .NET, které lze tímto nástrojem odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="9ef02-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9ef02-149">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="9ef02-149">Sets the verbosity level.</span></span> <span data-ttu-id="9ef02-150">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="9ef02-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9ef02-151">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="9ef02-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="9ef02-152">Příklady</span><span class="sxs-lookup"><span data-stu-id="9ef02-152">Examples</span></span>

* <span data-ttu-id="9ef02-153">Seznam všech sad SDK jádra .NET a runtimes, které lze odebrat pomocí tohoto nástroje:</span><span class="sxs-lookup"><span data-stu-id="9ef02-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="9ef02-154">Seznam všech sad sdsad a runčase jádra x64 .NET:</span><span class="sxs-lookup"><span data-stu-id="9ef02-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="9ef02-155">Seznam všech sad sdsad x86 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="9ef02-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="9ef02-156">Krok 2 - Proveďte suchý běh</span><span class="sxs-lookup"><span data-stu-id="9ef02-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="9ef02-157">`dotnet-core-uninstall dry-run` Příkazy `dotnet-core-uninstall whatif` a zobrazují sady .NET Core SDK a runtimes, které budou odebrány na základě možností, které jsou k dispozici bez provedení odinstalace.</span><span class="sxs-lookup"><span data-stu-id="9ef02-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="9ef02-158">Tyto příkazy jsou synonyma.</span><span class="sxs-lookup"><span data-stu-id="9ef02-158">These commands are synonyms.</span></span>

<span data-ttu-id="9ef02-159">**dotnet-core-uninstall dry-run a dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="9ef02-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9ef02-160">Synopse</span><span class="sxs-lookup"><span data-stu-id="9ef02-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="9ef02-161">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9ef02-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="9ef02-162">Zadaná verze k odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="9ef02-162">The specified version to uninstall.</span></span> <span data-ttu-id="9ef02-163">Můžete uvést několik verzí jeden po druhém, oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="9ef02-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="9ef02-164">Soubory odpovědí jsou také podporovány.</span><span class="sxs-lookup"><span data-stu-id="9ef02-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="9ef02-165">Soubory odpovědí jsou alternativou k umístění všech verzí na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="9ef02-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="9ef02-166">Jedná se o textové soubory, \*obvykle s příponou RSP, a každá verze je uvedena na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="9ef02-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="9ef02-167">Chcete-li zadat soubor `VERSION` odpovědí pro \@ argument, použijte znak bezprostředně následovaný názvem souboru odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9ef02-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="9ef02-168">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9ef02-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="9ef02-169">Windows</span><span class="sxs-lookup"><span data-stu-id="9ef02-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="9ef02-170">Odebere všechny sady .NET Core SDK a runtimes.</span><span class="sxs-lookup"><span data-stu-id="9ef02-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="9ef02-171">Odebere pouze sady .NET Core SDK a runtimes s verzí menší než zadaná verze.</span><span class="sxs-lookup"><span data-stu-id="9ef02-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="9ef02-172">Zadaná verze zůstane nainstalována.</span><span class="sxs-lookup"><span data-stu-id="9ef02-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="9ef02-173">Odebere všechny sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.</span><span class="sxs-lookup"><span data-stu-id="9ef02-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="9ef02-174">Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="9ef02-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="9ef02-175">Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="9ef02-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="9ef02-176">Tato možnost chrání global.json.</span><span class="sxs-lookup"><span data-stu-id="9ef02-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="9ef02-177">Odebere sady .NET Core SDK a runtimes označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="9ef02-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="9ef02-178">Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.</span><span class="sxs-lookup"><span data-stu-id="9ef02-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="9ef02-179">Odebere pouze ASP.NET za běhu jádra.</span><span class="sxs-lookup"><span data-stu-id="9ef02-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="9ef02-180">Odebere pouze runtime .NET Core a hostování balíčků.</span><span class="sxs-lookup"><span data-stu-id="9ef02-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="9ef02-181">Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.</span><span class="sxs-lookup"><span data-stu-id="9ef02-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="9ef02-182">Odebere pouze runtimes jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="9ef02-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="9ef02-183">Odebere pouze sady SDK jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="9ef02-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9ef02-184">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="9ef02-184">Sets the verbosity level.</span></span> <span data-ttu-id="9ef02-185">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="9ef02-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9ef02-186">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="9ef02-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="9ef02-187">Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x64 SDK nebo runtimes.</span><span class="sxs-lookup"><span data-stu-id="9ef02-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="9ef02-188">Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x86 SDK nebo runtimes.</span><span class="sxs-lookup"><span data-stu-id="9ef02-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="9ef02-189">**`--force`** Vynutí odebrání verzí, které mohou být použity visual studio.</span><span class="sxs-lookup"><span data-stu-id="9ef02-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="9ef02-190">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="9ef02-190">Notes:</span></span>

1. <span data-ttu-id="9ef02-191">Přesně jeden `--sdk` `--runtime`z `--aspnet-runtime`, `--hosting-bundle` , , a je požadováno.</span><span class="sxs-lookup"><span data-stu-id="9ef02-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="9ef02-192">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.</span><span class="sxs-lookup"><span data-stu-id="9ef02-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="9ef02-193">Pokud `--x64` `--x86` nebo nejsou zadány, budou odebrány x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="9ef02-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="9ef02-194">Macos</span><span class="sxs-lookup"><span data-stu-id="9ef02-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="9ef02-195">Odebere všechny sady .NET Core SDK a runtimes.</span><span class="sxs-lookup"><span data-stu-id="9ef02-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="9ef02-196">Odebere sady .NET Core SDK a runtimes pod zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="9ef02-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="9ef02-197">Zadaná verze zůstane zachována.</span><span class="sxs-lookup"><span data-stu-id="9ef02-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="9ef02-198">Odebere sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.</span><span class="sxs-lookup"><span data-stu-id="9ef02-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="9ef02-199">Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="9ef02-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="9ef02-200">Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="9ef02-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="9ef02-201">Tato možnost chrání global.json.</span><span class="sxs-lookup"><span data-stu-id="9ef02-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="9ef02-202">Odebere sady .NET Core SDK a runtimes označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="9ef02-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="9ef02-203">Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.</span><span class="sxs-lookup"><span data-stu-id="9ef02-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="9ef02-204">Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.</span><span class="sxs-lookup"><span data-stu-id="9ef02-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="9ef02-205">Odebere pouze runtimes jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="9ef02-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="9ef02-206">Odebere pouze sady SDK jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="9ef02-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9ef02-207">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="9ef02-207">Sets the verbosity level.</span></span> <span data-ttu-id="9ef02-208">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="9ef02-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9ef02-209">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="9ef02-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="9ef02-210">**`--force`** Vynutí odebrání verzí, které mohou být používány sady Visual Studio nebo sady SDK.</span><span class="sxs-lookup"><span data-stu-id="9ef02-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="9ef02-211">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="9ef02-211">Notes:</span></span>

1. <span data-ttu-id="9ef02-212">Přesně jeden `--sdk` `--runtime` z a je nutné.</span><span class="sxs-lookup"><span data-stu-id="9ef02-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="9ef02-213">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.</span><span class="sxs-lookup"><span data-stu-id="9ef02-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="9ef02-214">Příklady</span><span class="sxs-lookup"><span data-stu-id="9ef02-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="9ef02-215">Ve výchozím nastavení nejsou ve `dotnet-core-uninstall dry-run` výstupu zahrnuty sady .NET Core SDK a runtimes, které mohou být vyžadovány sadou Visual Studio nebo jinými sadami SDK.</span><span class="sxs-lookup"><span data-stu-id="9ef02-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="9ef02-216">V následujících příkladech některé zadané sady SDK a doba běhu nemusí být zahrnuty do výstupu, v závislosti na stavu počítače.</span><span class="sxs-lookup"><span data-stu-id="9ef02-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="9ef02-217">Chcete-li zahrnout všechny sady SDK a dobu běhu, `--force` uveďte je explicitně jako argumenty nebo použijte možnost.</span><span class="sxs-lookup"><span data-stu-id="9ef02-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="9ef02-218">Běh nasucho odebrání všech runčasů .NET Core, které byly nahrazeny vyššími opravami:</span><span class="sxs-lookup"><span data-stu-id="9ef02-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="9ef02-219">Nasucho odstranit všechny sady .NET Core `2.2.301`SDK pod verzí :</span><span class="sxs-lookup"><span data-stu-id="9ef02-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="9ef02-220">Krok 3 – Odinstalace sad SDK jádra .NET a runčase</span><span class="sxs-lookup"><span data-stu-id="9ef02-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="9ef02-221">`dotnet-core-uninstall remove`odinstaluje sady .NET Core SDK a runtimes, které jsou určeny kolekcí možností.</span><span class="sxs-lookup"><span data-stu-id="9ef02-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="9ef02-222">Nástroj nelze použít k odinstalaci sad SDK a runtimes s verzí 5.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9ef02-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="9ef02-223">Vzhledem k tomu, že tento nástroj má destruktivní chování, **důrazně** doporučujeme provést spuštění nasucho před spuštěním příkazu remove.</span><span class="sxs-lookup"><span data-stu-id="9ef02-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="9ef02-224">Běh na sucho vám ukáže, jaké sady .NET Core SDK `remove` a runtimes budou odebrány při použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="9ef02-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="9ef02-225">Odkazovat na [Mám odebrat verzi?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) chcete-li zjistit, které sady SDK a runtimes jsou bezpečné odebrat.</span><span class="sxs-lookup"><span data-stu-id="9ef02-225">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="9ef02-226">Mějte na paměti následující upozornění:</span><span class="sxs-lookup"><span data-stu-id="9ef02-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="9ef02-227">Tento nástroj může odinstalovat verze sady .NET Core SDK, které jsou vyžadovány `global.json` soubory v počítači.</span><span class="sxs-lookup"><span data-stu-id="9ef02-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="9ef02-228">Sady SDK jádra .NET můžete přeinstalovat na stránce [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="9ef02-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="9ef02-229">Tento nástroj může odinstalovat verze runtime .NET Core, které jsou vyžadovány aplikacemi závislými na rámci počítače.</span><span class="sxs-lookup"><span data-stu-id="9ef02-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="9ef02-230">Runtime jádra .NET můžete přeinstalovat na stránce [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="9ef02-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="9ef02-231">Tento nástroj může odinstalovat verze sady .NET Core SDK a runtime, na které aplikace Visual Studio spoléhá.</span><span class="sxs-lookup"><span data-stu-id="9ef02-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="9ef02-232">Pokud přerušíte instalaci sady Visual Studio, spusťte "Oprava" v instalačním programu sady Visual Studio a vraťte se do pracovního stavu.</span><span class="sxs-lookup"><span data-stu-id="9ef02-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="9ef02-233">Ve výchozím nastavení všechny příkazy zachovat .NET Core SDK a runtimes, které mohou být vyžadovány Visual Studio nebo jiné sady SDK.</span><span class="sxs-lookup"><span data-stu-id="9ef02-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="9ef02-234">Tyto sady SDK a runtimes lze odinstalovat jejich výpisem `--force` explicitně jako argumenty nebo pomocí možnosti.</span><span class="sxs-lookup"><span data-stu-id="9ef02-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="9ef02-235">Nástroj vyžaduje zvýšení odinstalace sad SDK jádra .NET a runčase.</span><span class="sxs-lookup"><span data-stu-id="9ef02-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="9ef02-236">Spusťte nástroj v příkazovém `sudo` řádku Správce v systému Windows a v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="9ef02-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="9ef02-237">`dry-run` Příkazy `whatif` a nevyžadují zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9ef02-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="9ef02-238">**dotnet-core-uninstall odebrat**</span><span class="sxs-lookup"><span data-stu-id="9ef02-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="9ef02-239">Synopse</span><span class="sxs-lookup"><span data-stu-id="9ef02-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="9ef02-240">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9ef02-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="9ef02-241">Zadaná verze k odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="9ef02-241">The specified version to uninstall.</span></span> <span data-ttu-id="9ef02-242">Můžete uvést několik verzí jeden po druhém, oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="9ef02-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="9ef02-243">Soubory odpovědí jsou také podporovány.</span><span class="sxs-lookup"><span data-stu-id="9ef02-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="9ef02-244">Soubory odpovědí jsou alternativou k umístění všech verzí na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="9ef02-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="9ef02-245">Jedná se o textové soubory, \*obvykle s příponou RSP, a každá verze je uvedena na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="9ef02-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="9ef02-246">Chcete-li zadat soubor `VERSION` odpovědí pro \@ argument, použijte znak bezprostředně následovaný názvem souboru odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9ef02-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="9ef02-247">Možnosti</span><span class="sxs-lookup"><span data-stu-id="9ef02-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="9ef02-248">Windows</span><span class="sxs-lookup"><span data-stu-id="9ef02-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="9ef02-249">Odebere všechny sady .NET Core SDK a runtimes.</span><span class="sxs-lookup"><span data-stu-id="9ef02-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="9ef02-250">Odebere pouze sady .NET Core SDK a runtimes s verzí menší než zadaná verze.</span><span class="sxs-lookup"><span data-stu-id="9ef02-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="9ef02-251">Zadaná verze zůstane nainstalována.</span><span class="sxs-lookup"><span data-stu-id="9ef02-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="9ef02-252">Odebere všechny sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.</span><span class="sxs-lookup"><span data-stu-id="9ef02-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="9ef02-253">Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="9ef02-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="9ef02-254">Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="9ef02-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="9ef02-255">Tato možnost chrání global.json.</span><span class="sxs-lookup"><span data-stu-id="9ef02-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="9ef02-256">Odebere sady .NET Core SDK a runtimes označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="9ef02-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="9ef02-257">Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.</span><span class="sxs-lookup"><span data-stu-id="9ef02-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="9ef02-258">Odebere pouze ASP.NET za běhu jádra.</span><span class="sxs-lookup"><span data-stu-id="9ef02-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="9ef02-259">Odebere pouze runtime .NET Core a hostování balíčků.</span><span class="sxs-lookup"><span data-stu-id="9ef02-259">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="9ef02-260">Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.</span><span class="sxs-lookup"><span data-stu-id="9ef02-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="9ef02-261">Odebere pouze runtimes jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="9ef02-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="9ef02-262">Odebere pouze sady SDK jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="9ef02-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9ef02-263">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="9ef02-263">Sets the verbosity level.</span></span> <span data-ttu-id="9ef02-264">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="9ef02-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9ef02-265">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="9ef02-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="9ef02-266">Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x64 SDK nebo runtimes.</span><span class="sxs-lookup"><span data-stu-id="9ef02-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="9ef02-267">Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x86 SDK nebo runtimes.</span><span class="sxs-lookup"><span data-stu-id="9ef02-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="9ef02-268">**`-y, --yes`** Provede příkaz bez nutnosti potvrzení ano nebo ne.</span><span class="sxs-lookup"><span data-stu-id="9ef02-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="9ef02-269">**`--force`** Vynutí odebrání verzí, které mohou být použity visual studio.</span><span class="sxs-lookup"><span data-stu-id="9ef02-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="9ef02-270">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="9ef02-270">Notes:</span></span>

1. <span data-ttu-id="9ef02-271">Přesně jeden `--sdk` `--runtime`z `--aspnet-runtime`, `--hosting-bundle` , , a je požadováno.</span><span class="sxs-lookup"><span data-stu-id="9ef02-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="9ef02-272">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.</span><span class="sxs-lookup"><span data-stu-id="9ef02-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="9ef02-273">Pokud `--x64` `--x86` nebo nejsou zadány, budou odebrány x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="9ef02-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="9ef02-274">Macos</span><span class="sxs-lookup"><span data-stu-id="9ef02-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="9ef02-275">Odebere všechny sady .NET Core SDK a runtimes.</span><span class="sxs-lookup"><span data-stu-id="9ef02-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="9ef02-276">Odebere sady .NET Core SDK a runtimes pod zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="9ef02-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="9ef02-277">Zadaná verze zůstane zachována.</span><span class="sxs-lookup"><span data-stu-id="9ef02-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="9ef02-278">Odebere sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.</span><span class="sxs-lookup"><span data-stu-id="9ef02-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="9ef02-279">Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="9ef02-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="9ef02-280">Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="9ef02-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="9ef02-281">Tato možnost chrání global.json.</span><span class="sxs-lookup"><span data-stu-id="9ef02-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="9ef02-282">Odebere sady .NET Core SDK a runtimes označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="9ef02-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="9ef02-283">Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.</span><span class="sxs-lookup"><span data-stu-id="9ef02-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="9ef02-284">Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.</span><span class="sxs-lookup"><span data-stu-id="9ef02-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="9ef02-285">Odebere pouze runtimes jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="9ef02-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="9ef02-286">Odebere pouze sady SDK jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="9ef02-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="9ef02-287">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="9ef02-287">Sets the verbosity level.</span></span> <span data-ttu-id="9ef02-288">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="9ef02-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9ef02-289">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="9ef02-289">The default value is `normal`.</span></span>

* <span data-ttu-id="9ef02-290">**`-y, --yes`** Provede příkaz bez nutnosti potvrzení Y/N.</span><span class="sxs-lookup"><span data-stu-id="9ef02-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="9ef02-291">**`--force`** Vynutí odebrání verzí, které mohou být používány sady Visual Studio nebo sady SDK.</span><span class="sxs-lookup"><span data-stu-id="9ef02-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="9ef02-292">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="9ef02-292">Notes:</span></span>

1. <span data-ttu-id="9ef02-293">Přesně jeden `--sdk` `--runtime` z a je nutné.</span><span class="sxs-lookup"><span data-stu-id="9ef02-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="9ef02-294">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.</span><span class="sxs-lookup"><span data-stu-id="9ef02-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="9ef02-295">Příklady</span><span class="sxs-lookup"><span data-stu-id="9ef02-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="9ef02-296">Ve výchozím nastavení jsou uloženy sady .NET Core SDK a runtimes, které mohou být vyžadovány sadou Visual Studio nebo jinými sadami SDK.</span><span class="sxs-lookup"><span data-stu-id="9ef02-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="9ef02-297">V následujících příkladech mohou některé zadané sady SDK a doba běhu zůstat v závislosti na stavu počítače.</span><span class="sxs-lookup"><span data-stu-id="9ef02-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="9ef02-298">Chcete-li odebrat všechny sady SDK a dobu běhu, uveďte je explicitně jako argumenty nebo použijte `--force` možnost.</span><span class="sxs-lookup"><span data-stu-id="9ef02-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="9ef02-299">Odeberte všechny runtimes jádra .NET kromě verze `3.0.0-preview6-27804-01` bez nutnosti potvrzení y/n:</span><span class="sxs-lookup"><span data-stu-id="9ef02-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="9ef02-300">Odeberte všechny sady .NET Core 1.1 SDK bez nutnosti potvrzení Y/n:</span><span class="sxs-lookup"><span data-stu-id="9ef02-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="9ef02-301">Odeberte sdk .NET Core 1.1.11 bez výstupu konzoly:</span><span class="sxs-lookup"><span data-stu-id="9ef02-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="9ef02-302">Odeberte všechny sady .NET Core SDK, které lze bezpečně odebrat tímto nástrojem:</span><span class="sxs-lookup"><span data-stu-id="9ef02-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="9ef02-303">Odeberte všechny sady .NET Core SDK, které lze odebrat tímto nástrojem, včetně sad SDK, které mohou být vyžadovány sadou Visual Studio (nedoporučuje se):</span><span class="sxs-lookup"><span data-stu-id="9ef02-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="9ef02-304">Odebrání všech sad SDK jádra ROZHRANÍ .NET, které jsou zadány v souboru odpovědí`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="9ef02-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="9ef02-305">Obsah *versions.rsp* je následující:</span><span class="sxs-lookup"><span data-stu-id="9ef02-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="9ef02-306">Krok 4 – Odstranění záložní složky NuGet (volitelné)</span><span class="sxs-lookup"><span data-stu-id="9ef02-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="9ef02-307">V některých případech již `NuGetFallbackFolder` nepotřebujete a možná budete chtít odstranit.</span><span class="sxs-lookup"><span data-stu-id="9ef02-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="9ef02-308">Další informace o odstranění této složky naleznete [v tématu Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="9ef02-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="9ef02-309">Odinstalace nástroje</span><span class="sxs-lookup"><span data-stu-id="9ef02-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="9ef02-310">Windows</span><span class="sxs-lookup"><span data-stu-id="9ef02-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="9ef02-311">Sem **Přidat nebo odebrat programy**.</span><span class="sxs-lookup"><span data-stu-id="9ef02-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="9ef02-312">Vyhledejte `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="9ef02-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="9ef02-313">Vyberte **možnost Odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="9ef02-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="9ef02-314">Macos</span><span class="sxs-lookup"><span data-stu-id="9ef02-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="9ef02-315">Odstraňte stažený soubor *dotnet-core-uninstall.tar.gz* z adresáře, ve kterém byl nainstalován.</span><span class="sxs-lookup"><span data-stu-id="9ef02-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="9ef02-316">Pokud jste rozbalili obsah tohoto souboru do jiného adresáře, nezapomeňte tento obsah také odstranit.</span><span class="sxs-lookup"><span data-stu-id="9ef02-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
