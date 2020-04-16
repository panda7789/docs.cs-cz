---
title: dotnet clean, příkaz
description: Příkaz dotnet clean vyčistí aktuální adresář.
ms.date: 02/14/2020
ms.openlocfilehash: a59922feba75e940a5cee2dfeb500f4f86372870
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463704"
---
# <a name="dotnet-clean"></a><span data-ttu-id="4282c-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="4282c-103">dotnet clean</span></span>

<span data-ttu-id="4282c-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="4282c-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4282c-105">Název</span><span class="sxs-lookup"><span data-stu-id="4282c-105">Name</span></span>

<span data-ttu-id="4282c-106">`dotnet clean`- Čistí výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="4282c-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4282c-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="4282c-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--interactive]
    [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]

dotnet clean -h|--help
```

## <a name="description"></a><span data-ttu-id="4282c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4282c-108">Description</span></span>

<span data-ttu-id="4282c-109">Příkaz `dotnet clean` vyčistí výstup předchozísestavení.</span><span class="sxs-lookup"><span data-stu-id="4282c-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="4282c-110">Je implementován jako [cíl MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="4282c-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="4282c-111">Pouze výstupy vytvořené během sestavení jsou vyčištěny.</span><span class="sxs-lookup"><span data-stu-id="4282c-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="4282c-112">Obě střední (*obj*) a konečný výstup (*bin*) složky jsou vyčištěny.</span><span class="sxs-lookup"><span data-stu-id="4282c-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="4282c-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4282c-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="4282c-114">MSBuild projektu nebo řešení k čištění.</span><span class="sxs-lookup"><span data-stu-id="4282c-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="4282c-115">Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, která končí *na proj* nebo *sln*, a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="4282c-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="4282c-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="4282c-116">Options</span></span>

* **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="4282c-117">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="4282c-117">Defines the build configuration.</span></span> <span data-ttu-id="4282c-118">Výchozí hodnota pro `Debug`většinu projektů je , ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="4282c-118">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span> <span data-ttu-id="4282c-119">Tato možnost je vyžadována pouze při čištění, pokud jste ji zadali během doby sestavení.</span><span class="sxs-lookup"><span data-stu-id="4282c-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4282c-120">[Rámec,](../../standard/frameworks.md) který byl zadán v době sestavení.</span><span class="sxs-lookup"><span data-stu-id="4282c-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="4282c-121">Rámec musí být definován v [souboru projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="4282c-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="4282c-122">Pokud jste zadali rozhraní v době sestavení, je nutné zadat rámec při čištění.</span><span class="sxs-lookup"><span data-stu-id="4282c-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="4282c-123">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="4282c-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="4282c-124">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci.</span><span class="sxs-lookup"><span data-stu-id="4282c-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="4282c-125">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="4282c-125">For example, to complete authentication.</span></span> <span data-ttu-id="4282c-126">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="4282c-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="4282c-127">Nezobrazuje spouštěcí banner ani zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="4282c-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="4282c-128">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="4282c-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="4282c-129">Adresář, který obsahuje artefakty sestavení k čištění.</span><span class="sxs-lookup"><span data-stu-id="4282c-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="4282c-130">Zadejte `-f|--framework <FRAMEWORK>` přepínač s přepínačem výstupního adresáře, pokud jste zadali rámec při projektu byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="4282c-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="4282c-131">Vyčistí výstupní složku zadaného běhu.</span><span class="sxs-lookup"><span data-stu-id="4282c-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="4282c-132">Používá se při [vytvoření samostatného nasazení.](../deploying/index.md#publish-self-contained)</span><span class="sxs-lookup"><span data-stu-id="4282c-132">This is used when a [self-contained deployment](../deploying/index.md#publish-self-contained) was created.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="4282c-133">Nastaví úroveň podrobností MSBuild.</span><span class="sxs-lookup"><span data-stu-id="4282c-133">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="4282c-134">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="4282c-134">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4282c-135">Výchozí formát je `normal`.</span><span class="sxs-lookup"><span data-stu-id="4282c-135">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="4282c-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="4282c-136">Examples</span></span>

* <span data-ttu-id="4282c-137">Vyčistit výchozí sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="4282c-137">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="4282c-138">Vyčistěte projekt vytvořený pomocí konfigurace vydání:</span><span class="sxs-lookup"><span data-stu-id="4282c-138">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
