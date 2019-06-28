---
title: čištění příkaz DotNet
description: Příkaz dotnet clean odstraní aktuální adresář.
ms.date: 06/26/2019
ms.openlocfilehash: 36630c046ff8f1ad8d513b4e64cfb74a8625776b
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422022"
---
# <a name="dotnet-clean"></a><span data-ttu-id="32de5-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="32de5-103">dotnet clean</span></span>

<span data-ttu-id="32de5-104">**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="32de5-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="32de5-105">Name</span><span class="sxs-lookup"><span data-stu-id="32de5-105">Name</span></span>

<span data-ttu-id="32de5-106">`dotnet clean` -Vyčistí výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="32de5-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="32de5-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="32de5-107">Synopsis</span></span>

```
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] 
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="32de5-108">Popis</span><span class="sxs-lookup"><span data-stu-id="32de5-108">Description</span></span>

<span data-ttu-id="32de5-109">`dotnet clean` Příkaz vyčistí výstupního předchozím sestavením.</span><span class="sxs-lookup"><span data-stu-id="32de5-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="32de5-110">Je implementován jako [cíl nástroje MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="32de5-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="32de5-111">Pouze výstupů během sestavení se vytvořila vymazána.</span><span class="sxs-lookup"><span data-stu-id="32de5-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="32de5-112">Obě zprostředkující (*obj*) a závěrečný výstup (*bin*) se čištění složky.</span><span class="sxs-lookup"><span data-stu-id="32de5-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="32de5-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="32de5-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="32de5-114">Nástroj MSBuild projekt nebo řešení pro čištění.</span><span class="sxs-lookup"><span data-stu-id="32de5-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="32de5-115">Pokud není zadán soubor projektu nebo řešení, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí na *proj* nebo *sln*a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="32de5-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="32de5-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="32de5-116">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="32de5-117">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="32de5-117">Defines the build configuration.</span></span> <span data-ttu-id="32de5-118">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="32de5-118">The default value is `Debug`.</span></span> <span data-ttu-id="32de5-119">Tato možnost je pouze při čištění, pokud jste zadali během doby sestavení vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="32de5-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="32de5-120">[Framework](../../standard/frameworks.md) , který byl zadán v okamžiku sestavení.</span><span class="sxs-lookup"><span data-stu-id="32de5-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="32de5-121">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="32de5-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="32de5-122">Pokud jste zadali rozhraní v okamžiku sestavení, je nutné zadat rozhraní framework při čištění souboru.</span><span class="sxs-lookup"><span data-stu-id="32de5-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="32de5-123">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="32de5-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="32de5-124">Povoluje příkazu zastavit a počkat na vstup uživatele nebo akce.</span><span class="sxs-lookup"><span data-stu-id="32de5-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="32de5-125">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="32de5-125">For example, to complete authentication.</span></span> <span data-ttu-id="32de5-126">Tato možnost je k dispozici, protože .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="32de5-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="32de5-127">Nezobrazí úvodní nápis a zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="32de5-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="32de5-128">Tato možnost je k dispozici, protože .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="32de5-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="32de5-129">Adresář, který obsahuje artefakty sestavení k odstranění.</span><span class="sxs-lookup"><span data-stu-id="32de5-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="32de5-130">Zadejte `-f|--framework <FRAMEWORK>` přepnout s přepínačem výstupní adresář, pokud jste zadali rozhraní, když byl projekt sestaven.</span><span class="sxs-lookup"><span data-stu-id="32de5-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="32de5-131">Vyčištění výstupní složky zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="32de5-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="32de5-132">Používá se při [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="32de5-132">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="32de5-133">Možnost dostupné od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="32de5-133">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="32de5-134">Nastaví úroveň podrobností MSBuild.</span><span class="sxs-lookup"><span data-stu-id="32de5-134">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="32de5-135">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="32de5-135">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="32de5-136">Výchozí hodnota je `normal`.</span><span class="sxs-lookup"><span data-stu-id="32de5-136">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="32de5-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="32de5-137">Examples</span></span>

* <span data-ttu-id="32de5-138">Vyčištění výchozí sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="32de5-138">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="32de5-139">Vyčistěte projekt vyvíjené v konfiguraci vydané verze:</span><span class="sxs-lookup"><span data-stu-id="32de5-139">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```
