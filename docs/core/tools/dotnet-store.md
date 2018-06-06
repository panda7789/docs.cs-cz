---
title: příkaz úložiště DotNet.
description: Příkaz 'dotnet úložiště, ukládá na zadaná sestavení v úložišti balíček modulu runtime.
author: bleroy
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 54654522207157f7d49bb86223b7986acccf51ee
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696322"
---
# <a name="dotnet-store"></a><span data-ttu-id="7f649-103">úložiště DotNet.</span><span class="sxs-lookup"><span data-stu-id="7f649-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="7f649-104">Název</span><span class="sxs-lookup"><span data-stu-id="7f649-104">Name</span></span>

<span data-ttu-id="7f649-105">`dotnet store` -Ukládá na zadaná sestavení v [úložiště balíčku runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="7f649-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="7f649-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="7f649-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="7f649-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7f649-107">Description</span></span>

<span data-ttu-id="7f649-108">`dotnet store` ukládá na zadaná sestavení v [úložiště balíčku runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="7f649-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="7f649-109">Ve výchozím nastavení jsou sestavení optimalizované pro cílový modul runtime a framework.</span><span class="sxs-lookup"><span data-stu-id="7f649-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="7f649-110">Další informace najdete v tématu [úložiště balíčku runtime](../deploying/runtime-store.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="7f649-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="7f649-111">Požadované možnosti</span><span class="sxs-lookup"><span data-stu-id="7f649-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="7f649-112">Určuje, [cílové rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="7f649-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="7f649-113">*Souboru manifestu balíčku úložiště* je soubor XML, který obsahuje seznam balíčků pro uložení.</span><span class="sxs-lookup"><span data-stu-id="7f649-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="7f649-114">Formát souboru manifestu není kompatibilní s formátem stylu SDK projektu.</span><span class="sxs-lookup"><span data-stu-id="7f649-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="7f649-115">Ano, dá použít soubor projektu, který odkazuje na požadované balíčky s `-m|--manifest` možnost ukládat sestavení v úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7f649-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="7f649-116">Pokud chcete zadat více souborů manifestu, opakujte pro každý soubor možnost a cestu.</span><span class="sxs-lookup"><span data-stu-id="7f649-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="7f649-117">Příklad: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="7f649-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="7f649-118">[Runtime identifikátor](../rid-catalog.md) k cíli.</span><span class="sxs-lookup"><span data-stu-id="7f649-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="7f649-119">Volitelné možnosti</span><span class="sxs-lookup"><span data-stu-id="7f649-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="7f649-120">Určuje verzi rozhraní .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="7f649-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="7f649-121">Tato možnost umožňuje vybrat konkrétní framework verze mimo rámec určeného `-f|--framework` možnost.</span><span class="sxs-lookup"><span data-stu-id="7f649-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="7f649-122">Zobrazí nápovědu informace.</span><span class="sxs-lookup"><span data-stu-id="7f649-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7f649-123">Určuje cestu k úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7f649-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="7f649-124">Pokud není zadáno, výchozí hodnota *ukládání* podadresáři instalační adresář uživatelského profilu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7f649-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="7f649-125">Přeskočí fázi optimalizace.</span><span class="sxs-lookup"><span data-stu-id="7f649-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="7f649-126">Přeskočí symbolů generace.</span><span class="sxs-lookup"><span data-stu-id="7f649-126">Skips symbol generation.</span></span> <span data-ttu-id="7f649-127">V současné době můžete vygenerovat pouze symboly v systému Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="7f649-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7f649-128">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="7f649-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7f649-129">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7f649-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="7f649-130">Pracovní adresář využívá příkaz.</span><span class="sxs-lookup"><span data-stu-id="7f649-130">The working directory used by the command.</span></span> <span data-ttu-id="7f649-131">Pokud není zadaný, použije *obj* podadresáři aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="7f649-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="7f649-132">Příklady</span><span class="sxs-lookup"><span data-stu-id="7f649-132">Examples</span></span>

<span data-ttu-id="7f649-133">Ukládat balíčky v zadané *packages.csproj* soubor projektu pro .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="7f649-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="7f649-134">Ukládat balíčky v zadané *packages.csproj* bez optimalizace:</span><span class="sxs-lookup"><span data-stu-id="7f649-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="7f649-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f649-135">See also</span></span>

[<span data-ttu-id="7f649-136">Úložiště balíčků modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7f649-136">Runtime package store</span></span>](../deploying/runtime-store.md)