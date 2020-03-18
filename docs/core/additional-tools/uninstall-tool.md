---
title: Nástroj odinstalace
description: Přehled nástroje .NET Core Uninstall Tool, což je nástroj s průvodcem, který umožňuje řízené vyčištění sad SDK jádra .NET a runčase.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: bd20cba133cbb754dcca48e48b76a391a9efacba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847022"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="b2168-103">Nástroj pro odinstalaci .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2168-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="b2168-104">[Nástroj .NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) umožňuje odebrat sady .NET Core SDK a runtimes ze systému.</span><span class="sxs-lookup"><span data-stu-id="b2168-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="b2168-105">K dispozici je kolekce možností, které určují, které verze chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="b2168-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="b2168-106">Nástroj podporuje Windows a macOS.</span><span class="sxs-lookup"><span data-stu-id="b2168-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="b2168-107">Linux není v současné době podporován.</span><span class="sxs-lookup"><span data-stu-id="b2168-107">Linux is currently not supported.</span></span>

<span data-ttu-id="b2168-108">V systému Windows může nástroj odinstalovat pouze sady SDK a runtimes, které byly nainstalovány pomocí jednoho z následujících instalačních programů:</span><span class="sxs-lookup"><span data-stu-id="b2168-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="b2168-109">Instalační program .NET Core SDK a runtime.</span><span class="sxs-lookup"><span data-stu-id="b2168-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="b2168-110">Instalační program sady Visual Studio ve verzích starších než Visual Studio 2019 verze 16.3.</span><span class="sxs-lookup"><span data-stu-id="b2168-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="b2168-111">V systému macOS může nástroj odinstalovat pouze sady SDK a runtimes umístěné ve složce */usr/local/share/dotnet.*</span><span class="sxs-lookup"><span data-stu-id="b2168-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="b2168-112">Z důvodu těchto omezení nemusí být nástroj schopen odinstalovat všechny sady .NET Core SDK a runtimes v počítači.</span><span class="sxs-lookup"><span data-stu-id="b2168-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="b2168-113">Pomocí příkazu `dotnet --info` můžete najít všechny nainstalované sady .NET Core SDK a runtimes, včetně těchto sad SDK a runtimes, které tento nástroj nelze odebrat.</span><span class="sxs-lookup"><span data-stu-id="b2168-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="b2168-114">Příkaz `dotnet-core-uninstall list` zobrazí sady SDK, které lze pomocí nástroje odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="b2168-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="b2168-115">Instalace nástroje</span><span class="sxs-lookup"><span data-stu-id="b2168-115">Install the tool</span></span>

<span data-ttu-id="b2168-116">Zde si můžete stáhnout nástroj .NET Core Uninstall Tool [a](https://aka.ms/dotnet-core-uninstall-tool) zdrojový kód najdete v úložišti GitHub [dotnet/cli-lab.](https://github.com/dotnet/cli-lab)</span><span class="sxs-lookup"><span data-stu-id="b2168-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="b2168-117">Nástroj vyžaduje zvýšení odinstalace sad SDK jádra .NET a runčase.</span><span class="sxs-lookup"><span data-stu-id="b2168-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="b2168-118">Proto by měl být nainstalován v adresáři chráněném pro zápis, například *C:\Program Files* v systému Windows nebo */usr/local/bin* v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="b2168-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="b2168-119">Viz také [zvýšený přístup pro příkazy dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="b2168-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="b2168-120">Další informace naleznete v [podrobných pokynech k instalaci](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="b2168-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="b2168-121">Spuštění nástroje</span><span class="sxs-lookup"><span data-stu-id="b2168-121">Run the tool</span></span>

<span data-ttu-id="b2168-122">Následující kroky ukazují doporučený postup pro spuštění nástroje pro odinstalaci:</span><span class="sxs-lookup"><span data-stu-id="b2168-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="b2168-123">Krok 1 – Zobrazení nainstalovaných sad SDK .NET Core A RunTimes</span><span class="sxs-lookup"><span data-stu-id="b2168-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="b2168-124">Krok 2 - Proveďte suchý běh</span><span class="sxs-lookup"><span data-stu-id="b2168-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="b2168-125">Krok 3 – Odinstalace sad SDK jádra .NET a runčase</span><span class="sxs-lookup"><span data-stu-id="b2168-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="b2168-126">Krok 4 – Odstranění záložní složky NuGet (volitelné)</span><span class="sxs-lookup"><span data-stu-id="b2168-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="b2168-127">Krok 1 – Zobrazení nainstalovaných sad SDK .NET Core A RunTimes</span><span class="sxs-lookup"><span data-stu-id="b2168-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="b2168-128">Příkaz `dotnet-core-uninstall list` obsahuje seznam nainstalovaných sad SDK jádra .NET a dob běhu, které lze pomocí tohoto nástroje odebrat.</span><span class="sxs-lookup"><span data-stu-id="b2168-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="b2168-129">Některé sady SDK a runtimes mohou být vyžadovány sadou Visual Studio a zobrazí se s poznámkou, proč se nedoporučuje je odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="b2168-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="b2168-130">**seznam odinstalace dotnet-core-uninstall**</span><span class="sxs-lookup"><span data-stu-id="b2168-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="b2168-131">Synopse</span><span class="sxs-lookup"><span data-stu-id="b2168-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="b2168-132">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b2168-132">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="b2168-133">Windows</span><span class="sxs-lookup"><span data-stu-id="b2168-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="b2168-134">Zobrazí seznam všech ASP.NET za běhu jádra, které lze odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="b2168-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="b2168-135">Zobrazí seznam všech runtime rozhraní .NET Core a hostingových balíčků, které lze odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="b2168-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="b2168-136">Zobrazí seznam všech runčasů jádra .NET, které lze tímto nástrojem odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="b2168-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2168-137">Zobrazí seznam všech sad SDK jádra .NET, které lze tímto nástrojem odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="b2168-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2168-138">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="b2168-138">Sets the verbosity level.</span></span> <span data-ttu-id="b2168-139">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="b2168-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2168-140">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2168-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="b2168-141">Zobrazí seznam všech sad X64 .NET Core SDK a runtimes, které lze odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="b2168-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="b2168-142">Zobrazí seznam všech sad X86 .NET Core SDK a runtimes, které lze odinstalovat pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="b2168-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b2168-143">Macos</span><span class="sxs-lookup"><span data-stu-id="b2168-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="b2168-144">Zobrazí seznam všech runčasů jádra .NET, které lze tímto nástrojem odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="b2168-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2168-145">Zobrazí seznam všech sad SDK jádra .NET, které lze tímto nástrojem odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="b2168-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2168-146">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="b2168-146">Sets the verbosity level.</span></span> <span data-ttu-id="b2168-147">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="b2168-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2168-148">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2168-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="b2168-149">Příklady</span><span class="sxs-lookup"><span data-stu-id="b2168-149">Examples</span></span>

* <span data-ttu-id="b2168-150">Seznam všech sad SDK jádra .NET a runtimes, které lze odebrat pomocí tohoto nástroje:</span><span class="sxs-lookup"><span data-stu-id="b2168-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="b2168-151">Seznam všech sad sdsad a runčase jádra x64 .NET:</span><span class="sxs-lookup"><span data-stu-id="b2168-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="b2168-152">Seznam všech sad sdsad x86 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="b2168-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="b2168-153">Krok 2 - Proveďte suchý běh</span><span class="sxs-lookup"><span data-stu-id="b2168-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="b2168-154">`dotnet-core-uninstall dry-run` Příkazy `dotnet-core-uninstall whatif` a zobrazují sady .NET Core SDK a runtimes, které budou odebrány na základě možností, které jsou k dispozici bez provedení odinstalace.</span><span class="sxs-lookup"><span data-stu-id="b2168-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="b2168-155">Tyto příkazy jsou synonyma.</span><span class="sxs-lookup"><span data-stu-id="b2168-155">These commands are synonyms.</span></span>

<span data-ttu-id="b2168-156">**dotnet-core-uninstall dry-run a dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="b2168-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="b2168-157">Synopse</span><span class="sxs-lookup"><span data-stu-id="b2168-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="b2168-158">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b2168-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="b2168-159">Zadaná verze k odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="b2168-159">The specified version to uninstall.</span></span> <span data-ttu-id="b2168-160">Můžete uvést několik verzí jeden po druhém, oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="b2168-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="b2168-161">Soubory odpovědí jsou také podporovány.</span><span class="sxs-lookup"><span data-stu-id="b2168-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="b2168-162">Soubory odpovědí jsou alternativou k umístění všech verzí na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b2168-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="b2168-163">Jedná se o textové soubory, \*obvykle s příponou RSP, a každá verze je uvedena na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="b2168-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="b2168-164">Chcete-li zadat soubor `VERSION` odpovědí pro \@ argument, použijte znak bezprostředně následovaný názvem souboru odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b2168-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="b2168-165">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b2168-165">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="b2168-166">Windows</span><span class="sxs-lookup"><span data-stu-id="b2168-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="b2168-167">Odebere všechny sady .NET Core SDK a runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2168-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="b2168-168">Odebere pouze sady .NET Core SDK a runtimes s verzí menší než zadaná verze.</span><span class="sxs-lookup"><span data-stu-id="b2168-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="b2168-169">Zadaná verze zůstane nainstalována.</span><span class="sxs-lookup"><span data-stu-id="b2168-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="b2168-170">Odebere všechny sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.</span><span class="sxs-lookup"><span data-stu-id="b2168-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b2168-171">Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="b2168-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b2168-172">Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="b2168-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b2168-173">Tato možnost chrání global.json.</span><span class="sxs-lookup"><span data-stu-id="b2168-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b2168-174">Odebere sady .NET Core SDK a runtimes označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="b2168-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b2168-175">Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.</span><span class="sxs-lookup"><span data-stu-id="b2168-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="b2168-176">Odebere pouze ASP.NET za běhu jádra.</span><span class="sxs-lookup"><span data-stu-id="b2168-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="b2168-177">Odebere pouze runtime .NET Core a hostování balíčků.</span><span class="sxs-lookup"><span data-stu-id="b2168-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b2168-178">Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.</span><span class="sxs-lookup"><span data-stu-id="b2168-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b2168-179">Odebere pouze runtimes jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="b2168-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2168-180">Odebere pouze sady SDK jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="b2168-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2168-181">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="b2168-181">Sets the verbosity level.</span></span> <span data-ttu-id="b2168-182">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="b2168-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2168-183">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2168-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="b2168-184">Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x64 SDK nebo runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2168-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="b2168-185">Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x86 SDK nebo runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2168-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="b2168-186">**`--force`** Vynutí odebrání verzí, které mohou být použity visual studio.</span><span class="sxs-lookup"><span data-stu-id="b2168-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="b2168-187">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="b2168-187">Notes:</span></span>

1. <span data-ttu-id="b2168-188">Přesně jeden `--sdk` `--runtime`z `--aspnet-runtime`, `--hosting-bundle` , , a je požadováno.</span><span class="sxs-lookup"><span data-stu-id="b2168-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="b2168-189">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.</span><span class="sxs-lookup"><span data-stu-id="b2168-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="b2168-190">Pokud `--x64` `--x86` nebo nejsou zadány, budou odebrány x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="b2168-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b2168-191">Macos</span><span class="sxs-lookup"><span data-stu-id="b2168-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="b2168-192">Odebere všechny sady .NET Core SDK a runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2168-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="b2168-193">Odebere sady .NET Core SDK a runtimes pod zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="b2168-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="b2168-194">Zadaná verze zůstane zachována.</span><span class="sxs-lookup"><span data-stu-id="b2168-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="b2168-195">Odebere sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.</span><span class="sxs-lookup"><span data-stu-id="b2168-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b2168-196">Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="b2168-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b2168-197">Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="b2168-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b2168-198">Tato možnost chrání global.json.</span><span class="sxs-lookup"><span data-stu-id="b2168-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b2168-199">Odebere sady .NET Core SDK a runtimes označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="b2168-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b2168-200">Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.</span><span class="sxs-lookup"><span data-stu-id="b2168-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b2168-201">Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.</span><span class="sxs-lookup"><span data-stu-id="b2168-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b2168-202">Odebere pouze runtimes jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="b2168-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2168-203">Odebere pouze sady SDK jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="b2168-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2168-204">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="b2168-204">Sets the verbosity level.</span></span> <span data-ttu-id="b2168-205">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="b2168-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2168-206">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2168-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="b2168-207">**`--force`** Vynutí odebrání verzí, které mohou být používány sady Visual Studio nebo sady SDK.</span><span class="sxs-lookup"><span data-stu-id="b2168-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="b2168-208">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="b2168-208">Notes:</span></span>

1. <span data-ttu-id="b2168-209">Přesně jeden `--sdk` `--runtime` z a je nutné.</span><span class="sxs-lookup"><span data-stu-id="b2168-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="b2168-210">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.</span><span class="sxs-lookup"><span data-stu-id="b2168-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="b2168-211">Příklady</span><span class="sxs-lookup"><span data-stu-id="b2168-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="b2168-212">Ve výchozím nastavení nejsou ve `dotnet-core-uninstall dry-run` výstupu zahrnuty sady .NET Core SDK a runtimes, které mohou být vyžadovány sadou Visual Studio nebo jinými sadami SDK.</span><span class="sxs-lookup"><span data-stu-id="b2168-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="b2168-213">V následujících příkladech některé zadané sady SDK a doba běhu nemusí být zahrnuty do výstupu, v závislosti na stavu počítače.</span><span class="sxs-lookup"><span data-stu-id="b2168-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="b2168-214">Chcete-li zahrnout všechny sady SDK a dobu běhu, `--force` uveďte je explicitně jako argumenty nebo použijte možnost.</span><span class="sxs-lookup"><span data-stu-id="b2168-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="b2168-215">Běh nasucho odebrání všech runčasů .NET Core, které byly nahrazeny vyššími opravami:</span><span class="sxs-lookup"><span data-stu-id="b2168-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="b2168-216">Nasucho odstranit všechny sady .NET Core `2.2.301`SDK pod verzí :</span><span class="sxs-lookup"><span data-stu-id="b2168-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="b2168-217">Krok 3 – Odinstalace sad SDK jádra .NET a runčase</span><span class="sxs-lookup"><span data-stu-id="b2168-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="b2168-218">`dotnet-core-uninstall remove`odinstaluje sady .NET Core SDK a runtimes, které jsou určeny kolekcí možností.</span><span class="sxs-lookup"><span data-stu-id="b2168-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="b2168-219">Nástroj nelze použít k odinstalaci sad SDK a runtimes s verzí 5.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="b2168-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="b2168-220">Vzhledem k tomu, že tento nástroj má destruktivní chování, **důrazně** doporučujeme provést spuštění nasucho před spuštěním příkazu remove.</span><span class="sxs-lookup"><span data-stu-id="b2168-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="b2168-221">Běh na sucho vám ukáže, jaké sady .NET Core SDK `remove` a runtimes budou odebrány při použití příkazu.</span><span class="sxs-lookup"><span data-stu-id="b2168-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="b2168-222">Odkazovat na [Mám odebrat verzi?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) chcete-li zjistit, které sady SDK a runtimes jsou bezpečné odebrat.</span><span class="sxs-lookup"><span data-stu-id="b2168-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="b2168-223">Mějte na paměti následující upozornění:</span><span class="sxs-lookup"><span data-stu-id="b2168-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="b2168-224">Tento nástroj může odinstalovat verze sady .NET Core SDK, které jsou vyžadovány `global.json` soubory v počítači.</span><span class="sxs-lookup"><span data-stu-id="b2168-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="b2168-225">Sady SDK jádra .NET můžete přeinstalovat na stránce [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="b2168-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="b2168-226">Tento nástroj může odinstalovat verze runtime .NET Core, které jsou vyžadovány aplikacemi závislými na rámci počítače.</span><span class="sxs-lookup"><span data-stu-id="b2168-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="b2168-227">Runtime jádra .NET můžete přeinstalovat na stránce [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="b2168-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="b2168-228">Tento nástroj může odinstalovat verze sady .NET Core SDK a runtime, na které aplikace Visual Studio spoléhá.</span><span class="sxs-lookup"><span data-stu-id="b2168-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="b2168-229">Pokud přerušíte instalaci sady Visual Studio, spusťte "Oprava" v instalačním programu sady Visual Studio a vraťte se do pracovního stavu.</span><span class="sxs-lookup"><span data-stu-id="b2168-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="b2168-230">Ve výchozím nastavení všechny příkazy zachovat .NET Core SDK a runtimes, které mohou být vyžadovány Visual Studio nebo jiné sady SDK.</span><span class="sxs-lookup"><span data-stu-id="b2168-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="b2168-231">Tyto sady SDK a runtimes lze odinstalovat jejich výpisem `--force` explicitně jako argumenty nebo pomocí možnosti.</span><span class="sxs-lookup"><span data-stu-id="b2168-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="b2168-232">Nástroj vyžaduje zvýšení odinstalace sad SDK jádra .NET a runčase.</span><span class="sxs-lookup"><span data-stu-id="b2168-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="b2168-233">Spusťte nástroj v příkazovém `sudo` řádku Správce v systému Windows a v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="b2168-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="b2168-234">`dry-run` Příkazy `whatif` a nevyžadují zvýšení oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b2168-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="b2168-235">**dotnet-core-uninstall odebrat**</span><span class="sxs-lookup"><span data-stu-id="b2168-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="b2168-236">Synopse</span><span class="sxs-lookup"><span data-stu-id="b2168-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="b2168-237">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b2168-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="b2168-238">Zadaná verze k odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="b2168-238">The specified version to uninstall.</span></span> <span data-ttu-id="b2168-239">Můžete uvést několik verzí jeden po druhém, oddělené mezerami.</span><span class="sxs-lookup"><span data-stu-id="b2168-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="b2168-240">Soubory odpovědí jsou také podporovány.</span><span class="sxs-lookup"><span data-stu-id="b2168-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="b2168-241">Soubory odpovědí jsou alternativou k umístění všech verzí na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b2168-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="b2168-242">Jedná se o textové soubory, \*obvykle s příponou RSP, a každá verze je uvedena na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="b2168-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="b2168-243">Chcete-li zadat soubor `VERSION` odpovědí pro \@ argument, použijte znak bezprostředně následovaný názvem souboru odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b2168-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="b2168-244">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b2168-244">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="b2168-245">Windows</span><span class="sxs-lookup"><span data-stu-id="b2168-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="b2168-246">Odebere všechny sady .NET Core SDK a runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2168-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="b2168-247">Odebere pouze sady .NET Core SDK a runtimes s verzí menší než zadaná verze.</span><span class="sxs-lookup"><span data-stu-id="b2168-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="b2168-248">Zadaná verze zůstane nainstalována.</span><span class="sxs-lookup"><span data-stu-id="b2168-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="b2168-249">Odebere všechny sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.</span><span class="sxs-lookup"><span data-stu-id="b2168-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b2168-250">Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="b2168-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b2168-251">Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="b2168-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b2168-252">Tato možnost chrání global.json.</span><span class="sxs-lookup"><span data-stu-id="b2168-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b2168-253">Odebere sady .NET Core SDK a runtimes označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="b2168-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b2168-254">Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.</span><span class="sxs-lookup"><span data-stu-id="b2168-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="b2168-255">Odebere pouze ASP.NET za běhu jádra.</span><span class="sxs-lookup"><span data-stu-id="b2168-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="b2168-256">Odebere pouze runtime .NET Core a hostování balíčků.</span><span class="sxs-lookup"><span data-stu-id="b2168-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b2168-257">Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.</span><span class="sxs-lookup"><span data-stu-id="b2168-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b2168-258">Odebere pouze runtimes jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="b2168-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2168-259">Odebere pouze sady SDK jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="b2168-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2168-260">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="b2168-260">Sets the verbosity level.</span></span> <span data-ttu-id="b2168-261">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="b2168-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2168-262">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2168-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="b2168-263">Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x64 SDK nebo runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2168-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="b2168-264">Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x86 SDK nebo runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2168-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="b2168-265">**`-y, --yes`** Provede příkaz bez nutnosti potvrzení ano nebo ne.</span><span class="sxs-lookup"><span data-stu-id="b2168-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="b2168-266">**`--force`** Vynutí odebrání verzí, které mohou být použity visual studio.</span><span class="sxs-lookup"><span data-stu-id="b2168-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="b2168-267">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="b2168-267">Notes:</span></span>

1. <span data-ttu-id="b2168-268">Přesně jeden `--sdk` `--runtime`z `--aspnet-runtime`, `--hosting-bundle` , , a je požadováno.</span><span class="sxs-lookup"><span data-stu-id="b2168-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="b2168-269">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.</span><span class="sxs-lookup"><span data-stu-id="b2168-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="b2168-270">Pokud `--x64` `--x86` nebo nejsou zadány, budou odebrány x64 i x86.</span><span class="sxs-lookup"><span data-stu-id="b2168-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b2168-271">Macos</span><span class="sxs-lookup"><span data-stu-id="b2168-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="b2168-272">Odebere všechny sady .NET Core SDK a runtimes.</span><span class="sxs-lookup"><span data-stu-id="b2168-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="b2168-273">Odebere sady .NET Core SDK a runtimes pod zadanou verzí.</span><span class="sxs-lookup"><span data-stu-id="b2168-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="b2168-274">Zadaná verze zůstane zachována.</span><span class="sxs-lookup"><span data-stu-id="b2168-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="b2168-275">Odebere sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.</span><span class="sxs-lookup"><span data-stu-id="b2168-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="b2168-276">Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.</span><span class="sxs-lookup"><span data-stu-id="b2168-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="b2168-277">Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami.</span><span class="sxs-lookup"><span data-stu-id="b2168-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="b2168-278">Tato možnost chrání global.json.</span><span class="sxs-lookup"><span data-stu-id="b2168-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="b2168-279">Odebere sady .NET Core SDK a runtimes označené jako náhledy.</span><span class="sxs-lookup"><span data-stu-id="b2168-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="b2168-280">Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.</span><span class="sxs-lookup"><span data-stu-id="b2168-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="b2168-281">Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.</span><span class="sxs-lookup"><span data-stu-id="b2168-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="b2168-282">Odebere pouze runtimes jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="b2168-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="b2168-283">Odebere pouze sady SDK jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="b2168-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="b2168-284">Nastaví úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="b2168-284">Sets the verbosity level.</span></span> <span data-ttu-id="b2168-285">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="b2168-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b2168-286">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="b2168-286">The default value is `normal`.</span></span>

* <span data-ttu-id="b2168-287">**`-y, --yes`** Provede příkaz bez nutnosti potvrzení Y/N.</span><span class="sxs-lookup"><span data-stu-id="b2168-287">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="b2168-288">**`--force`** Vynutí odebrání verzí, které mohou být používány sady Visual Studio nebo sady SDK.</span><span class="sxs-lookup"><span data-stu-id="b2168-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="b2168-289">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="b2168-289">Notes:</span></span>

1. <span data-ttu-id="b2168-290">Přesně jeden `--sdk` `--runtime` z a je nutné.</span><span class="sxs-lookup"><span data-stu-id="b2168-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="b2168-291">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.</span><span class="sxs-lookup"><span data-stu-id="b2168-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="b2168-292">Příklady</span><span class="sxs-lookup"><span data-stu-id="b2168-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="b2168-293">Ve výchozím nastavení jsou uloženy sady .NET Core SDK a runtimes, které mohou být vyžadovány sadou Visual Studio nebo jinými sadami SDK.</span><span class="sxs-lookup"><span data-stu-id="b2168-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="b2168-294">V následujících příkladech mohou některé zadané sady SDK a doba běhu zůstat v závislosti na stavu počítače.</span><span class="sxs-lookup"><span data-stu-id="b2168-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="b2168-295">Chcete-li odebrat všechny sady SDK a dobu běhu, uveďte je explicitně jako argumenty nebo použijte `--force` možnost.</span><span class="sxs-lookup"><span data-stu-id="b2168-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="b2168-296">Odeberte všechny runtimes jádra .NET kromě verze `3.0.0-preview6-27804-01` bez nutnosti potvrzení y/n:</span><span class="sxs-lookup"><span data-stu-id="b2168-296">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="b2168-297">Odeberte všechny sady .NET Core 1.1 SDK bez nutnosti potvrzení Y/n:</span><span class="sxs-lookup"><span data-stu-id="b2168-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="b2168-298">Odeberte sdk .NET Core 1.1.11 bez výstupu konzoly:</span><span class="sxs-lookup"><span data-stu-id="b2168-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="b2168-299">Odeberte všechny sady .NET Core SDK, které lze bezpečně odebrat tímto nástrojem:</span><span class="sxs-lookup"><span data-stu-id="b2168-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="b2168-300">Odeberte všechny sady .NET Core SDK, které lze odebrat tímto nástrojem, včetně sad SDK, které mohou být vyžadovány sadou Visual Studio (nedoporučuje se):</span><span class="sxs-lookup"><span data-stu-id="b2168-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="b2168-301">Odebrání všech sad SDK jádra ROZHRANÍ .NET, které jsou zadány v souboru odpovědí`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="b2168-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="b2168-302">Obsah *versions.rsp* je následující:</span><span class="sxs-lookup"><span data-stu-id="b2168-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="b2168-303">Krok 4 – Odstranění záložní složky NuGet (volitelné)</span><span class="sxs-lookup"><span data-stu-id="b2168-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="b2168-304">V některých případech již `NuGetFallbackFolder` nepotřebujete a možná budete chtít odstranit.</span><span class="sxs-lookup"><span data-stu-id="b2168-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="b2168-305">Další informace o odstranění této složky naleznete [v tématu Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="b2168-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="b2168-306">Odinstalace nástroje</span><span class="sxs-lookup"><span data-stu-id="b2168-306">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="b2168-307">Windows</span><span class="sxs-lookup"><span data-stu-id="b2168-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="b2168-308">Sem **Přidat nebo odebrat programy**.</span><span class="sxs-lookup"><span data-stu-id="b2168-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="b2168-309">Vyhledejte `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="b2168-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="b2168-310">Vyberte **možnost Odinstalovat**.</span><span class="sxs-lookup"><span data-stu-id="b2168-310">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="b2168-311">Macos</span><span class="sxs-lookup"><span data-stu-id="b2168-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="b2168-312">Odstraňte stažený soubor *dotnet-core-uninstall.tar.gz* z adresáře, ve kterém byl nainstalován.</span><span class="sxs-lookup"><span data-stu-id="b2168-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="b2168-313">Pokud jste rozbalili obsah tohoto souboru do jiného adresáře, nezapomeňte tento obsah také odstranit.</span><span class="sxs-lookup"><span data-stu-id="b2168-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
