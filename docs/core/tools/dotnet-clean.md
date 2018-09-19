---
title: DotNet vyčistit příkaz – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet clean odstraní aktuální adresář.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 5553e4b4423a2d824c05caf7114c47b5f1c20477
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45988332"
---
# <a name="dotnet-clean"></a><span data-ttu-id="a2502-103">DotNet čisté</span><span class="sxs-lookup"><span data-stu-id="a2502-103">dotnet clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a2502-104">Název</span><span class="sxs-lookup"><span data-stu-id="a2502-104">Name</span></span>

<span data-ttu-id="a2502-105">`dotnet clean` -Vyčistí výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="a2502-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a2502-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="a2502-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a2502-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="a2502-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a2502-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="a2502-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="a2502-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a2502-109">Description</span></span>

<span data-ttu-id="a2502-110">`dotnet clean` Příkaz vyčistí výstupního předchozím sestavením.</span><span class="sxs-lookup"><span data-stu-id="a2502-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="a2502-111">Je implementován jako [cíl nástroje MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="a2502-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="a2502-112">Pouze výstupů během sestavení se vytvořila vymazána.</span><span class="sxs-lookup"><span data-stu-id="a2502-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="a2502-113">Obě zprostředkující (*obj*) a závěrečný výstup (*bin*) se čištění složky.</span><span class="sxs-lookup"><span data-stu-id="a2502-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="a2502-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="a2502-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a2502-115">Projekt MSBuild pro čištění.</span><span class="sxs-lookup"><span data-stu-id="a2502-115">The MSBuild project to clean.</span></span> <span data-ttu-id="a2502-116">Pokud není zadán soubor projektu, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, který končí na *proj* a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="a2502-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="a2502-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a2502-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a2502-118">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="a2502-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a2502-119">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2502-119">Defines the build configuration.</span></span> <span data-ttu-id="a2502-120">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="a2502-120">The default value is `Debug`.</span></span> <span data-ttu-id="a2502-121">Tato možnost je pouze při čištění, pokud jste zadali během doby sestavení vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="a2502-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a2502-122">[Framework](../../standard/frameworks.md) , který byl zadán v okamžiku sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2502-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="a2502-123">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="a2502-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="a2502-124">Pokud jste zadali rozhraní v okamžiku sestavení, je nutné zadat rozhraní framework při čištění souboru.</span><span class="sxs-lookup"><span data-stu-id="a2502-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="a2502-125">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a2502-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a2502-126">Adresář, ve kterém je umístí výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2502-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="a2502-127">Zadejte `-f|--framework <FRAMEWORK>` přepnout s přepínačem výstupní adresář, pokud jste zadali rozhraní, když byl projekt sestaven.</span><span class="sxs-lookup"><span data-stu-id="a2502-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a2502-128">Vyčištění výstupní složky zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a2502-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="a2502-129">Používá se při [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="a2502-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a2502-130">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="a2502-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a2502-131">Povolené úrovně jsou q [uiet], m [inimal], n [ormal], d [etailed] a diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="a2502-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a2502-132">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="a2502-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a2502-133">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2502-133">Defines the build configuration.</span></span> <span data-ttu-id="a2502-134">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="a2502-134">The default value is `Debug`.</span></span> <span data-ttu-id="a2502-135">Tato možnost je pouze při čištění, pokud jste zadali během doby sestavení vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="a2502-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a2502-136">[Framework](../../standard/frameworks.md) , který byl zadán v okamžiku sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2502-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="a2502-137">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="a2502-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="a2502-138">Pokud jste zadali rozhraní v okamžiku sestavení, je nutné zadat rozhraní framework při čištění souboru.</span><span class="sxs-lookup"><span data-stu-id="a2502-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="a2502-139">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a2502-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a2502-140">Adresář, ve kterém je umístí výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2502-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="a2502-141">Zadejte `-f|--framework <FRAMEWORK>` přepnout s přepínačem výstupní adresář, pokud jste zadali rozhraní, když byl projekt sestaven.</span><span class="sxs-lookup"><span data-stu-id="a2502-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a2502-142">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="a2502-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a2502-143">Povolené úrovně jsou q [uiet], m [inimal], n [ormal], d [etailed] a diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="a2502-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="a2502-144">Příklady</span><span class="sxs-lookup"><span data-stu-id="a2502-144">Examples</span></span>

<span data-ttu-id="a2502-145">Vyčištění výchozí sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="a2502-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="a2502-146">Vyčistěte projekt vyvíjené v konfiguraci vydané verze:</span><span class="sxs-lookup"><span data-stu-id="a2502-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
