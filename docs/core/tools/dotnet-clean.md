---
title: dotnet – příkaz Vyčištění
description: Příkaz dotnet Cleanup vyčistí aktuální adresář.
ms.date: 02/14/2020
ms.openlocfilehash: 186f1ea07718a8e178f88c3d079cf6e2f1f8660b
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503751"
---
# <a name="dotnet-clean"></a><span data-ttu-id="0407a-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="0407a-103">dotnet clean</span></span>

<span data-ttu-id="0407a-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="0407a-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0407a-105">Název</span><span class="sxs-lookup"><span data-stu-id="0407a-105">Name</span></span>

<span data-ttu-id="0407a-106">`dotnet clean` – vyčistí výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="0407a-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0407a-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="0407a-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="0407a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="0407a-108">Description</span></span>

<span data-ttu-id="0407a-109">Příkaz `dotnet clean` vyčistí výstup předchozího buildu.</span><span class="sxs-lookup"><span data-stu-id="0407a-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="0407a-110">Je implementována jako [cíl nástroje MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="0407a-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="0407a-111">Vyčištěny jsou pouze výstupy vytvořené během sestavení.</span><span class="sxs-lookup"><span data-stu-id="0407a-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="0407a-112">Jsou vyčištěny mezilehlé složky (*obj*) i finální výstupní složky (*bin*).</span><span class="sxs-lookup"><span data-stu-id="0407a-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="0407a-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0407a-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="0407a-114">Projekt nebo řešení MSBuild, které se má vyčistit</span><span class="sxs-lookup"><span data-stu-id="0407a-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="0407a-115">Pokud není zadán soubor projektu nebo řešení, nástroj MSBuild vyhledá aktuální pracovní adresář pro soubor s příponou souboru, který končí v *proj* nebo *sln*, a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="0407a-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="0407a-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0407a-116">Options</span></span>

* **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="0407a-117">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="0407a-117">Defines the build configuration.</span></span> <span data-ttu-id="0407a-118">Výchozí hodnota pro většinu projektů je `Debug`, ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="0407a-118">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span> <span data-ttu-id="0407a-119">Tato možnost je vyžadována pouze při čištění, pokud jste ji zadali během sestavování.</span><span class="sxs-lookup"><span data-stu-id="0407a-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0407a-120">[Rozhraní](../../standard/frameworks.md) , které bylo zadáno v čase sestavení.</span><span class="sxs-lookup"><span data-stu-id="0407a-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="0407a-121">Rozhraní musí být definováno v [souboru projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="0407a-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="0407a-122">Pokud jste v době sestavení zadali rozhraní, je nutné při čištění zadat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0407a-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="0407a-123">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="0407a-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="0407a-124">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="0407a-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="0407a-125">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="0407a-125">For example, to complete authentication.</span></span> <span data-ttu-id="0407a-126">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="0407a-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="0407a-127">Nezobrazuje úvodní nápis nebo zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="0407a-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="0407a-128">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="0407a-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="0407a-129">Adresář obsahující artefakty sestavení, které mají být vyčištěny.</span><span class="sxs-lookup"><span data-stu-id="0407a-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="0407a-130">Zadejte `-f|--framework <FRAMEWORK>` přepínač s přepínačem výstupní adresář, pokud jste zadali rozhraní při sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="0407a-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="0407a-131">Vyčistí výstupní složku zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0407a-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="0407a-132">Tato funkce se používá, když se vytvořilo [samostatné nasazení](../deploying/index.md#publish-self-contained) .</span><span class="sxs-lookup"><span data-stu-id="0407a-132">This is used when a [self-contained deployment](../deploying/index.md#publish-self-contained) was created.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0407a-133">Nastaví úroveň podrobností MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0407a-133">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="0407a-134">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0407a-134">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0407a-135">Výchozí formát je `normal`.</span><span class="sxs-lookup"><span data-stu-id="0407a-135">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="0407a-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="0407a-136">Examples</span></span>

* <span data-ttu-id="0407a-137">Vyčistit výchozí sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="0407a-137">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="0407a-138">Vyčištění projektu vytvořeného pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="0407a-138">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
