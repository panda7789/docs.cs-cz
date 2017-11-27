---
title: "příkaz úložiště DotNet."
description: "Příkaz 'dotnet úložiště, ukládá na zadaná sestavení v úložišti balíček modulu runtime."
author: bleroy
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: fcf1eeba0709e05cff124bc3ae7bb93f4ca57128
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-store"></a><span data-ttu-id="f9a96-103">úložiště DotNet.</span><span class="sxs-lookup"><span data-stu-id="f9a96-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="f9a96-104">Název</span><span class="sxs-lookup"><span data-stu-id="f9a96-104">Name</span></span>

<span data-ttu-id="f9a96-105">`dotnet store`-Ukládá na zadaná sestavení v [úložiště balíčku runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="f9a96-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="f9a96-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="f9a96-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="f9a96-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f9a96-107">Description</span></span>

<span data-ttu-id="f9a96-108">`dotnet store`ukládá na zadaná sestavení v [úložiště balíčku runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="f9a96-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="f9a96-109">Ve výchozím nastavení jsou sestavení optimalizované pro cílový modul runtime a framework.</span><span class="sxs-lookup"><span data-stu-id="f9a96-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="f9a96-110">Další informace najdete v tématu [úložiště balíčku runtime](../deploying/runtime-store.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="f9a96-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="f9a96-111">Požadované možnosti</span><span class="sxs-lookup"><span data-stu-id="f9a96-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="f9a96-112">Určuje, [cílové rozhraní](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f9a96-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="f9a96-113">*Souboru manifestu balíčku úložiště* je soubor XML, který obsahuje seznam balíčků pro uložení.</span><span class="sxs-lookup"><span data-stu-id="f9a96-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="f9a96-114">Je kompatibilní s formátem souboru manifestu *csproj* formátu.</span><span class="sxs-lookup"><span data-stu-id="f9a96-114">The format of the manifest file is compatible with the *csproj* format.</span></span> <span data-ttu-id="f9a96-115">Ano *csproj* soubor projektu, který odkazuje na požadované balíčky lze použít s `-m|--manifest` možnost ukládat sestavení v úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f9a96-115">So, a *csproj* project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="f9a96-116">Pokud chcete zadat více souborů manifestu, opakujte pro každý soubor možnost a cestu: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="f9a96-116">To specify multiple manifest files, repeat the option and path for each file: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="f9a96-117">Identifikátor runtime k cíli.</span><span class="sxs-lookup"><span data-stu-id="f9a96-117">The runtime identifier to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="f9a96-118">Volitelné možnosti</span><span class="sxs-lookup"><span data-stu-id="f9a96-118">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="f9a96-119">Určuje verzi rozhraní .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f9a96-119">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="f9a96-120">Tato možnost umožňuje vybrat konkrétní framework verze mimo rámec určeného `-f|--framework` možnost.</span><span class="sxs-lookup"><span data-stu-id="f9a96-120">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="f9a96-121">Zobrazí nápovědu informace.</span><span class="sxs-lookup"><span data-stu-id="f9a96-121">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f9a96-122">Určuje cestu k úložišti balíček modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f9a96-122">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="f9a96-123">Pokud není zadáno, výchozí hodnota *ukládání* podadresáři instalační adresář uživatelského profilu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9a96-123">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="f9a96-124">Přeskočí fázi optimalizace.</span><span class="sxs-lookup"><span data-stu-id="f9a96-124">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="f9a96-125">Přeskočí symbolů generace.</span><span class="sxs-lookup"><span data-stu-id="f9a96-125">Skips symbol generation.</span></span> <span data-ttu-id="f9a96-126">V současné době můžete vygenerovat pouze symboly v systému Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="f9a96-126">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f9a96-127">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f9a96-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f9a96-128">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f9a96-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="f9a96-129">Pracovní adresář využívá příkaz.</span><span class="sxs-lookup"><span data-stu-id="f9a96-129">The working directory used by the command.</span></span> <span data-ttu-id="f9a96-130">Pokud není zadaný, použije *obj* podadresáři aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="f9a96-130">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="f9a96-131">Příklady</span><span class="sxs-lookup"><span data-stu-id="f9a96-131">Examples</span></span>

<span data-ttu-id="f9a96-132">Ukládat balíčky v zadané *packages.csproj* soubor projektu pro .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="f9a96-132">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="f9a96-133">Ukládat balíčky v zadané *packages.csproj* bez optimalizace:</span><span class="sxs-lookup"><span data-stu-id="f9a96-133">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="f9a96-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9a96-134">See also</span></span>

[<span data-ttu-id="f9a96-135">Úložiště balíčku modulu runtime</span><span class="sxs-lookup"><span data-stu-id="f9a96-135">Runtime package store</span></span>](../deploying/runtime-store.md)   
