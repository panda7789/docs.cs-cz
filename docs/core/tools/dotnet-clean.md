---
title: příkaz - .NET Core rozhraní příkazového řádku vyčistit DotNet.
description: Příkaz clean dotnet vyčistí aktuální adresář.
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 92db35df770b1e1d2438127c4b529d4cb480c8df
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-clean"></a><span data-ttu-id="df357-103">Vyčištění DotNet.</span><span class="sxs-lookup"><span data-stu-id="df357-103">dotnet-clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="df357-104">Název</span><span class="sxs-lookup"><span data-stu-id="df357-104">Name</span></span>

<span data-ttu-id="df357-105">`dotnet clean` -Vyčistí výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="df357-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="df357-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="df357-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="df357-107">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="df357-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="df357-108">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="df357-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="df357-109">Popis</span><span class="sxs-lookup"><span data-stu-id="df357-109">Description</span></span>

<span data-ttu-id="df357-110">`dotnet clean` Příkaz vyčistí výstup předchozího sestavení.</span><span class="sxs-lookup"><span data-stu-id="df357-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="df357-111">Je implementovaný jako [MSBuild cíl](/visualstudio/msbuild/msbuild-targets), takže projektu vyhodnotí při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="df357-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="df357-112">Vyčištěním pouze výstupy vytvořené během sestavení.</span><span class="sxs-lookup"><span data-stu-id="df357-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="df357-113">Obě zprostředkující (*obj*) a závěrečný výstup (*bin*) vyčištěním složek.</span><span class="sxs-lookup"><span data-stu-id="df357-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="df357-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="df357-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="df357-115">Projektu nástroje MSBuild vyčistit.</span><span class="sxs-lookup"><span data-stu-id="df357-115">The MSBuild project to clean.</span></span> <span data-ttu-id="df357-116">Pokud projekt soubor není zadán, MSBuild vyhledá aktuální pracovní adresář pro soubor, který má příponu souboru, které *proj* a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="df357-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="df357-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="df357-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="df357-118">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="df357-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="df357-119">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="df357-119">Defines the build configuration.</span></span> <span data-ttu-id="df357-120">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="df357-120">The default value is `Debug`.</span></span> <span data-ttu-id="df357-121">Tato možnost je pouze při čištění, pokud jste zadali během okamžiku sestavení vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="df357-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="df357-122">[Framework](../../standard/frameworks.md) zadaný v čase vytvoření buildu.</span><span class="sxs-lookup"><span data-stu-id="df357-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="df357-123">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="df357-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="df357-124">Pokud jste zadali rozhraní v čase vytvoření buildu, musíte zadat rozhraní při čištění.</span><span class="sxs-lookup"><span data-stu-id="df357-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="df357-125">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="df357-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="df357-126">Adresář, ve kterém jsou umístěny výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="df357-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="df357-127">Zadejte `-f|--framework <FRAMEWORK>` přepínač s přepínačem výstupní adresář, pokud jste zadali rozhraní, pokud byl vytvořený projekt.</span><span class="sxs-lookup"><span data-stu-id="df357-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="df357-128">Vyčistí do výstupní složky zadané modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="df357-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="df357-129">Používá se při [samostatná nasazení](../deploying/index.md#self-contained-deployments-scd) byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="df357-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="df357-130">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="df357-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="df357-131">Povolené úrovně jsou q [uiet], [den] m, n [ormální], [podrobné] d a diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="df357-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="df357-132">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="df357-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="df357-133">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="df357-133">Defines the build configuration.</span></span> <span data-ttu-id="df357-134">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="df357-134">The default value is `Debug`.</span></span> <span data-ttu-id="df357-135">Tato možnost je pouze při čištění, pokud jste zadali během okamžiku sestavení vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="df357-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="df357-136">[Framework](../../standard/frameworks.md) zadaný v čase vytvoření buildu.</span><span class="sxs-lookup"><span data-stu-id="df357-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="df357-137">Rozhraní musí být definován v [soubor projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="df357-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="df357-138">Pokud jste zadali rozhraní v čase vytvoření buildu, musíte zadat rozhraní při čištění.</span><span class="sxs-lookup"><span data-stu-id="df357-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="df357-139">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="df357-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="df357-140">Adresář, ve kterém jsou umístěny výstupy sestavení.</span><span class="sxs-lookup"><span data-stu-id="df357-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="df357-141">Zadejte `-f|--framework <FRAMEWORK>` přepínač s přepínačem výstupní adresář, pokud jste zadali rozhraní, pokud byl vytvořený projekt.</span><span class="sxs-lookup"><span data-stu-id="df357-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="df357-142">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="df357-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="df357-143">Povolené úrovně jsou q [uiet], [den] m, n [ormální], [podrobné] d a diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="df357-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="df357-144">Příklady</span><span class="sxs-lookup"><span data-stu-id="df357-144">Examples</span></span>

<span data-ttu-id="df357-145">Vyčištění sestavení výchozí projektu:</span><span class="sxs-lookup"><span data-stu-id="df357-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="df357-146">Vyčistěte projekt sestaven pomocí konfigurace verze:</span><span class="sxs-lookup"><span data-stu-id="df357-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
