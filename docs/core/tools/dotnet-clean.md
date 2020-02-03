---
title: dotnet – příkaz Vyčištění
description: Příkaz dotnet Cleanup vyčistí aktuální adresář.
ms.date: 06/26/2019
ms.openlocfilehash: 736c0bba5d156e919534f1ad811641e815b3ffac
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734250"
---
# <a name="dotnet-clean"></a><span data-ttu-id="7d902-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="7d902-103">dotnet clean</span></span>

<span data-ttu-id="7d902-104">**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="7d902-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="7d902-105">Název</span><span class="sxs-lookup"><span data-stu-id="7d902-105">Name</span></span>

<span data-ttu-id="7d902-106">`dotnet clean` – vyčistí výstup projektu.</span><span class="sxs-lookup"><span data-stu-id="7d902-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7d902-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="7d902-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="7d902-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7d902-108">Description</span></span>

<span data-ttu-id="7d902-109">Příkaz `dotnet clean` vyčistí výstup předchozího buildu.</span><span class="sxs-lookup"><span data-stu-id="7d902-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="7d902-110">Je implementována jako [cíl nástroje MSBuild](/visualstudio/msbuild/msbuild-targets), takže projekt je vyhodnocen při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="7d902-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="7d902-111">Vyčištěny jsou pouze výstupy vytvořené během sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d902-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="7d902-112">Jsou vyčištěny mezilehlé složky (*obj*) i finální výstupní složky (*bin*).</span><span class="sxs-lookup"><span data-stu-id="7d902-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="7d902-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7d902-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="7d902-114">Projekt nebo řešení MSBuild, které se má vyčistit</span><span class="sxs-lookup"><span data-stu-id="7d902-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="7d902-115">Pokud není zadán soubor projektu nebo řešení, nástroj MSBuild vyhledá aktuální pracovní adresář pro soubor s příponou souboru, který končí v *proj* nebo *sln*, a použije tento soubor.</span><span class="sxs-lookup"><span data-stu-id="7d902-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="7d902-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="7d902-116">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="7d902-117">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d902-117">Defines the build configuration.</span></span> <span data-ttu-id="7d902-118">Výchozí hodnota je `Debug`.</span><span class="sxs-lookup"><span data-stu-id="7d902-118">The default value is `Debug`.</span></span> <span data-ttu-id="7d902-119">Tato možnost je vyžadována pouze při čištění, pokud jste ji zadali během sestavování.</span><span class="sxs-lookup"><span data-stu-id="7d902-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="7d902-120">[Rozhraní](../../standard/frameworks.md) , které bylo zadáno v čase sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d902-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="7d902-121">Rozhraní musí být definováno v [souboru projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="7d902-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="7d902-122">Pokud jste v době sestavení zadali rozhraní, je nutné při čištění zadat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7d902-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="7d902-123">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="7d902-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="7d902-124">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="7d902-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="7d902-125">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="7d902-125">For example, to complete authentication.</span></span> <span data-ttu-id="7d902-126">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="7d902-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="7d902-127">Nezobrazuje úvodní nápis nebo zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="7d902-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="7d902-128">K dispozici od verze .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="7d902-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="7d902-129">Adresář obsahující artefakty sestavení, které mají být vyčištěny.</span><span class="sxs-lookup"><span data-stu-id="7d902-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="7d902-130">Zadejte `-f|--framework <FRAMEWORK>` přepínač s přepínačem výstupní adresář, pokud jste zadali rozhraní při sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="7d902-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="7d902-131">Vyčistí výstupní složku zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7d902-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="7d902-132">Tato funkce se používá, když se vytvořilo [samostatné nasazení](../deploying/index.md#self-contained-deployments-scd) .</span><span class="sxs-lookup"><span data-stu-id="7d902-132">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="7d902-133">Možnost je k dispozici od verze .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="7d902-133">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7d902-134">Nastaví úroveň podrobností MSBuild.</span><span class="sxs-lookup"><span data-stu-id="7d902-134">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="7d902-135">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7d902-135">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="7d902-136">Výchozí formát je `normal`.</span><span class="sxs-lookup"><span data-stu-id="7d902-136">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="7d902-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="7d902-137">Examples</span></span>

* <span data-ttu-id="7d902-138">Vyčistit výchozí sestavení projektu:</span><span class="sxs-lookup"><span data-stu-id="7d902-138">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="7d902-139">Vyčištění projektu vytvořeného pomocí konfigurace vydané verze:</span><span class="sxs-lookup"><span data-stu-id="7d902-139">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
