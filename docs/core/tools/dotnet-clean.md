---
title: čištění příkaz DotNet
description: Příkaz dotnet clean odstraní aktuální adresář.
ms.date: 04/14/2019
ms.openlocfilehash: 3e735c02c9be9b6f51a8cdf048c18eff34f838cb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754120"
---
# <a name="dotnet-clean"></a><span data-ttu-id="5b7a9-103">DotNet čisté</span><span class="sxs-lookup"><span data-stu-id="5b7a9-103">dotnet clean</span></span>

<span data-ttu-id="5b7a9-104">**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="5b7a9-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="5b7a9-105">Name</span><span class="sxs-lookup"><span data-stu-id="5b7a9-105">Name</span></span>

<span data-ttu-id="5b7a9-106">`dotnet clean` -Vyčistí výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5b7a9-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="5b7a9-107">Synopsis</span></span>

```
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5b7a9-108">Popis</span><span class="sxs-lookup"><span data-stu-id="5b7a9-108">Description</span></span>

<span data-ttu-id="5b7a9-109">`dotnet clean` Příkaz vyčistí výstupního předchozím sestavením.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="5b7a9-110">Je implementován jako [cíl nástroje MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="5b7a9-111">Pouze výstupů během sestavení se vytvořila vymazána.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="5b7a9-112">Obě zprostředkující (*obj*) a závěrečný výstup (*bin*) se čištění složky.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="5b7a9-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="5b7a9-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="5b7a9-114">Nástroj MSBuild projekt nebo řešení pro čištění.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="5b7a9-115">Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí na *proj* nebo *sln*a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="5b7a9-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5b7a9-116">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="5b7a9-117">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-117">Defines the build configuration.</span></span> <span data-ttu-id="5b7a9-118">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-118">The default value is `Debug`.</span></span> <span data-ttu-id="5b7a9-119">Tato možnost je pouze při čištění, pokud jste zadali během doby sestavení vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5b7a9-120">[Framework](../../standard/frameworks.md) , který byl zadán v okamžiku sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="5b7a9-121">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="5b7a9-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="5b7a9-122">Pokud jste zadali rozhraní v okamžiku sestavení, je nutné zadat rozhraní framework při čištění souboru.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="5b7a9-123">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="5b7a9-124">Povoluje příkazu zastavit a počkat na vstup uživatele nebo akce.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="5b7a9-125">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-125">For example, to complete authentication.</span></span> <span data-ttu-id="5b7a9-126">Tato možnost je k dispozici, protože .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-126">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5b7a9-127">Adresář, který obsahuje artefakty sestavení k odstranění.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-127">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="5b7a9-128">Zadejte `-f|--framework <FRAMEWORK>` přepnout s přepínačem výstupní adresář, pokud jste zadali rozhraní, když byl projekt sestaven.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-128">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5b7a9-129">Vyčištění výstupní složky zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-129">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="5b7a9-130">Používá se při [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-130">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="5b7a9-131">Možnost dostupné od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-131">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5b7a9-132">Nastaví úroveň podrobností MSBuild.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-132">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="5b7a9-133">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-133">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5b7a9-134">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="5b7a9-134">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="5b7a9-135">Příklady</span><span class="sxs-lookup"><span data-stu-id="5b7a9-135">Examples</span></span>

* <span data-ttu-id="5b7a9-136">Vyčištění výchozí sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="5b7a9-136">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="5b7a9-137">Vyčistěte projekt vyvíjené v konfiguraci vydané verze:</span><span class="sxs-lookup"><span data-stu-id="5b7a9-137">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```