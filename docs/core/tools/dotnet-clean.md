---
title: "příkaz - .NET Core rozhraní příkazového řádku vyčistit DotNet."
description: "Příkaz clean dotnet vyčistí aktuální adresář."
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: f56ccc485884114262cd1364cf9398e302f2c48a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-clean"></a><span data-ttu-id="922d2-103">Vyčištění DotNet.</span><span class="sxs-lookup"><span data-stu-id="922d2-103">dotnet-clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="922d2-104">Název</span><span class="sxs-lookup"><span data-stu-id="922d2-104">Name</span></span>

<span data-ttu-id="922d2-105">`dotnet clean`-Vyčistí výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="922d2-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="922d2-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="922d2-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="922d2-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="922d2-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="922d2-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="922d2-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="922d2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="922d2-109">Description</span></span>

<span data-ttu-id="922d2-110">`dotnet clean` Příkaz vyčistí výstup předchozího sestavení.</span><span class="sxs-lookup"><span data-stu-id="922d2-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="922d2-111">Je implementovaný jako [MSBuild cíl](/visualstudio/msbuild/msbuild-targets), takže projektu vyhodnotí při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="922d2-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="922d2-112">Vyčištěním pouze výstupy vytvořené během sestavení.</span><span class="sxs-lookup"><span data-stu-id="922d2-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="922d2-113">Obě zprostředkující (*obj*) a závěrečný výstup (*bin*) vyčištěním složek.</span><span class="sxs-lookup"><span data-stu-id="922d2-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="922d2-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="922d2-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="922d2-115">Projektu nástroje MSBuild vyčistit.</span><span class="sxs-lookup"><span data-stu-id="922d2-115">The MSBuild project to clean.</span></span> <span data-ttu-id="922d2-116">Pokud projekt soubor není zadán, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, které *proj* a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="922d2-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="922d2-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="922d2-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="922d2-118">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="922d2-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="922d2-119">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="922d2-119">Defines the build configuration.</span></span> <span data-ttu-id="922d2-120">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="922d2-120">The default value is `Debug`.</span></span> <span data-ttu-id="922d2-121">Tato možnost je pouze při čištění, pokud jste zadali během okamžiku sestavení vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="922d2-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="922d2-122">[Framework](../../standard/frameworks.md) zadaný v čase vytvoření buildu.</span><span class="sxs-lookup"><span data-stu-id="922d2-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="922d2-123">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="922d2-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="922d2-124">Pokud jste zadali rozhraní v čase vytvoření buildu, musíte zadat rozhraní při čištění.</span><span class="sxs-lookup"><span data-stu-id="922d2-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="922d2-125">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="922d2-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="922d2-126">Adresář, ve kterém jsou umístěny výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="922d2-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="922d2-127">Zadejte `-f|--framework <FRAMEWORK>` přepínač s přepínačem výstupní adresář, pokud jste zadali rozhraní, pokud byl vytvořený projekt.</span><span class="sxs-lookup"><span data-stu-id="922d2-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="922d2-128">Vyčistí do výstupní složky zadané modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="922d2-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="922d2-129">Používá se při [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="922d2-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="922d2-130">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="922d2-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="922d2-131">Povolené úrovně jsou q [uiet], [den] m, n [ormální], [podrobné] d a diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="922d2-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="922d2-132">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="922d2-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="922d2-133">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="922d2-133">Defines the build configuration.</span></span> <span data-ttu-id="922d2-134">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="922d2-134">The default value is `Debug`.</span></span> <span data-ttu-id="922d2-135">Tato možnost je pouze při čištění, pokud jste zadali během okamžiku sestavení vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="922d2-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="922d2-136">[Framework](../../standard/frameworks.md) zadaný v čase vytvoření buildu.</span><span class="sxs-lookup"><span data-stu-id="922d2-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="922d2-137">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="922d2-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="922d2-138">Pokud jste zadali rozhraní v čase vytvoření buildu, musíte zadat rozhraní při čištění.</span><span class="sxs-lookup"><span data-stu-id="922d2-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="922d2-139">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="922d2-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="922d2-140">Adresář, ve kterém jsou umístěny výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="922d2-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="922d2-141">Zadejte `-f|--framework <FRAMEWORK>` přepínač s přepínačem výstupní adresář, pokud jste zadali rozhraní, pokud byl vytvořený projekt.</span><span class="sxs-lookup"><span data-stu-id="922d2-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="922d2-142">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="922d2-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="922d2-143">Povolené úrovně jsou q [uiet], [den] m, n [ormální], [podrobné] d a diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="922d2-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="922d2-144">Příklady</span><span class="sxs-lookup"><span data-stu-id="922d2-144">Examples</span></span>

<span data-ttu-id="922d2-145">Vyčištění sestavení výchozí projektu:</span><span class="sxs-lookup"><span data-stu-id="922d2-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="922d2-146">Vyčistěte projekt sestaven pomocí konfigurace verze:</span><span class="sxs-lookup"><span data-stu-id="922d2-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
