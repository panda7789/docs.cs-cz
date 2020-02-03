---
title: dotnet – příkaz pro úložiště
description: Příkaz dotnet Store ukládá zadaná sestavení do úložiště balíčků modulu runtime.
ms.date: 05/29/2018
ms.openlocfilehash: cc5b4b6160ba296e1529f006c15e238746d9e08a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733048"
---
# <a name="dotnet-store"></a><span data-ttu-id="77ecf-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="77ecf-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="77ecf-104">Název</span><span class="sxs-lookup"><span data-stu-id="77ecf-104">Name</span></span>

<span data-ttu-id="77ecf-105">`dotnet store` – uloží zadaná sestavení do [úložiště balíčků modulu runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="77ecf-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="77ecf-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="77ecf-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="77ecf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="77ecf-107">Description</span></span>

<span data-ttu-id="77ecf-108">`dotnet store` ukládá zadaná sestavení do [úložiště balíčků modulu runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="77ecf-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="77ecf-109">Ve výchozím nastavení jsou sestavení optimalizována pro cílový modul runtime a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="77ecf-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="77ecf-110">Další informace najdete v tématu [úložiště balíčků za běhu](../deploying/runtime-store.md) .</span><span class="sxs-lookup"><span data-stu-id="77ecf-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="77ecf-111">Požadované možnosti</span><span class="sxs-lookup"><span data-stu-id="77ecf-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="77ecf-112">Určuje [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="77ecf-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="77ecf-113">*Soubor manifestu úložiště balíčku* je soubor XML, který obsahuje seznam balíčků, které mají být uloženy.</span><span class="sxs-lookup"><span data-stu-id="77ecf-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="77ecf-114">Formát souboru manifestu je kompatibilní s formátem projektu ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="77ecf-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="77ecf-115">Soubor projektu, který odkazuje na požadované balíčky, lze proto použít s možností `-m|--manifest` pro uložení sestavení v úložišti balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="77ecf-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="77ecf-116">Chcete-li zadat více souborů manifestu, opakujte možnost a cestu pro každý soubor.</span><span class="sxs-lookup"><span data-stu-id="77ecf-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="77ecf-117">Například: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="77ecf-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="77ecf-118">[Identifikátor modulu runtime](../rid-catalog.md) , který má být cílen.</span><span class="sxs-lookup"><span data-stu-id="77ecf-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="77ecf-119">Volitelné možnosti</span><span class="sxs-lookup"><span data-stu-id="77ecf-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="77ecf-120">Určuje .NET Core SDK verzi.</span><span class="sxs-lookup"><span data-stu-id="77ecf-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="77ecf-121">Tato možnost umožňuje vybrat konkrétní verzi rozhraní nad rámec určenou možností `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="77ecf-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="77ecf-122">Zobrazí informace o nápovědě.</span><span class="sxs-lookup"><span data-stu-id="77ecf-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="77ecf-123">Určuje cestu k úložišti balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="77ecf-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="77ecf-124">Pokud není zadaný, použije se výchozí podadresář *úložiště* instalačního adresáře .NET Core uživatelského profilu.</span><span class="sxs-lookup"><span data-stu-id="77ecf-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="77ecf-125">Přeskočí fázi optimalizace.</span><span class="sxs-lookup"><span data-stu-id="77ecf-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="77ecf-126">Přeskočí generování symbolů.</span><span class="sxs-lookup"><span data-stu-id="77ecf-126">Skips symbol generation.</span></span> <span data-ttu-id="77ecf-127">V současné době můžete generovat symboly jenom v systémech Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="77ecf-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="77ecf-128">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="77ecf-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="77ecf-129">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="77ecf-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="77ecf-130">Pracovní adresář použitý příkazem.</span><span class="sxs-lookup"><span data-stu-id="77ecf-130">The working directory used by the command.</span></span> <span data-ttu-id="77ecf-131">Pokud není zadaný, použije se podadresář *obj* aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="77ecf-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="77ecf-132">Příklady</span><span class="sxs-lookup"><span data-stu-id="77ecf-132">Examples</span></span>

<span data-ttu-id="77ecf-133">Uložte balíčky zadané v souboru projektu *Packages. csproj* pro .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="77ecf-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="77ecf-134">Uložit balíčky zadané v *balíčku. csproj* bez optimalizace:</span><span class="sxs-lookup"><span data-stu-id="77ecf-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="77ecf-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="77ecf-135">See also</span></span>

- [<span data-ttu-id="77ecf-136">Úložiště balíčků modulu runtime</span><span class="sxs-lookup"><span data-stu-id="77ecf-136">Runtime package store</span></span>](../deploying/runtime-store.md)
