---
title: čištění příkaz DotNet
description: Příkaz dotnet clean odstraní aktuální adresář.
ms.date: 12/04/2018
ms.openlocfilehash: a25b7930794795e3dff5051a8ca1dd1b9c261dfd
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169856"
---
# <a name="dotnet-clean"></a><span data-ttu-id="64bdc-103">DotNet čisté</span><span class="sxs-lookup"><span data-stu-id="64bdc-103">dotnet clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="64bdc-104">Název</span><span class="sxs-lookup"><span data-stu-id="64bdc-104">Name</span></span>

<span data-ttu-id="64bdc-105">`dotnet clean` -Vyčistí výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="64bdc-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="64bdc-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="64bdc-106">Synopsis</span></span>

```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="64bdc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="64bdc-107">Description</span></span>

<span data-ttu-id="64bdc-108">`dotnet clean` Příkaz vyčistí výstupního předchozím sestavením.</span><span class="sxs-lookup"><span data-stu-id="64bdc-108">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="64bdc-109">Je implementován jako [cíl nástroje MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="64bdc-109">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="64bdc-110">Pouze výstupů během sestavení se vytvořila vymazána.</span><span class="sxs-lookup"><span data-stu-id="64bdc-110">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="64bdc-111">Obě zprostředkující (*obj*) a závěrečný výstup (*bin*) se čištění složky.</span><span class="sxs-lookup"><span data-stu-id="64bdc-111">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="64bdc-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="64bdc-112">Arguments</span></span>

`PROJECT`

<span data-ttu-id="64bdc-113">Projekt MSBuild pro čištění.</span><span class="sxs-lookup"><span data-stu-id="64bdc-113">The MSBuild project to clean.</span></span> <span data-ttu-id="64bdc-114">Pokud není zadán soubor projektu, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí na *proj* a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="64bdc-114">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="64bdc-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="64bdc-115">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="64bdc-116">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="64bdc-116">Defines the build configuration.</span></span> <span data-ttu-id="64bdc-117">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="64bdc-117">The default value is `Debug`.</span></span> <span data-ttu-id="64bdc-118">Tato možnost je pouze při čištění, pokud jste zadali během doby sestavení vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="64bdc-118">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="64bdc-119">[Framework](../../standard/frameworks.md) , který byl zadán v okamžiku sestavení.</span><span class="sxs-lookup"><span data-stu-id="64bdc-119">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="64bdc-120">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="64bdc-120">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="64bdc-121">Pokud jste zadali rozhraní v okamžiku sestavení, je nutné zadat rozhraní framework při čištění souboru.</span><span class="sxs-lookup"><span data-stu-id="64bdc-121">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="64bdc-122">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="64bdc-122">Prints out a short help for the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="64bdc-123">Adresář, ve kterém je umístí výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="64bdc-123">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="64bdc-124">Zadejte `-f|--framework <FRAMEWORK>` přepnout s přepínačem výstupní adresář, pokud jste zadali rozhraní, když byl projekt sestaven.</span><span class="sxs-lookup"><span data-stu-id="64bdc-124">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="64bdc-125">Vyčištění výstupní složky zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="64bdc-125">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="64bdc-126">Používá se při [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="64bdc-126">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="64bdc-127">Možnost dostupné od verze rozhraní .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="64bdc-127">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="64bdc-128">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="64bdc-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="64bdc-129">Povolené úrovně jsou q [uiet], m [inimal], n [ormal], d [etailed] a diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="64bdc-129">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

## <a name="examples"></a><span data-ttu-id="64bdc-130">Příklady</span><span class="sxs-lookup"><span data-stu-id="64bdc-130">Examples</span></span>

* <span data-ttu-id="64bdc-131">Vyčištění výchozí sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="64bdc-131">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="64bdc-132">Vyčistěte projekt vyvíjené v konfiguraci vydané verze:</span><span class="sxs-lookup"><span data-stu-id="64bdc-132">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```