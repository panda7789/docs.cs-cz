---
title: dotnet store, příkaz
description: Příkaz 'dotnet store' ukládá zadaná sestavení v runtime package store.
ms.date: 02/14/2020
ms.openlocfilehash: 2f28a9bc287a87f600bda385c579e8070cbaa5ab
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463387"
---
# <a name="dotnet-store"></a><span data-ttu-id="1319b-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="1319b-103">dotnet store</span></span>

<span data-ttu-id="1319b-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="1319b-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1319b-105">Název</span><span class="sxs-lookup"><span data-stu-id="1319b-105">Name</span></span>

<span data-ttu-id="1319b-106">`dotnet store`- Ukládá zadaná sestavení v [runtime package store](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="1319b-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="1319b-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="1319b-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest <PATH_TO_MANIFEST_FILE>
    -f|--framework <FRAMEWORK_VERSION> -r|--runtime <RUNTIME_IDENTIFIER>
    [--framework-version <FRAMEWORK_VERSION>] [--output <OUTPUT_DIRECTORY>]
    [--skip-optimization] [--skip-symbols] [-v|--verbosity <LEVEL>]
    [--working-dir <WORKING_DIRECTORY>]

dotnet store -h|--help
```

## <a name="description"></a><span data-ttu-id="1319b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="1319b-108">Description</span></span>

<span data-ttu-id="1319b-109">`dotnet store`ukládá zadaná sestavení do [runtime package store](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="1319b-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="1319b-110">Ve výchozím nastavení jsou sestavení optimalizována pro cílový běh za běhu a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1319b-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="1319b-111">Další informace naleznete v tématu [runtime package store.](../deploying/runtime-store.md)</span><span class="sxs-lookup"><span data-stu-id="1319b-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="1319b-112">Požadované možnosti</span><span class="sxs-lookup"><span data-stu-id="1319b-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="1319b-113">Určuje [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="1319b-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="1319b-114">Cílová architektura musí být zadána v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="1319b-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="1319b-115">*Soubor manifestu úložiště balíčků* je soubor XML, který obsahuje seznam balíčků k uložení.</span><span class="sxs-lookup"><span data-stu-id="1319b-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="1319b-116">Formát souboru manifestu je kompatibilní s formátem projektu ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="1319b-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="1319b-117">Takže soubor projektu, který odkazuje na požadované balíčky lze použít s `-m|--manifest` možností ukládat sestavení v úložišti balíčků runtime.</span><span class="sxs-lookup"><span data-stu-id="1319b-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="1319b-118">Chcete-li určit více souborů manifestu, opakujte volbu a cestu pro každý soubor.</span><span class="sxs-lookup"><span data-stu-id="1319b-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="1319b-119">Například: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="1319b-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="1319b-120">[Identifikátor za běhu](../rid-catalog.md) cíl.</span><span class="sxs-lookup"><span data-stu-id="1319b-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="1319b-121">Volitelné možnosti</span><span class="sxs-lookup"><span data-stu-id="1319b-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="1319b-122">Určuje verzi sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="1319b-122">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="1319b-123">Tato možnost umožňuje vybrat konkrétní verzi architektury nad `-f|--framework` rámec určený možností.</span><span class="sxs-lookup"><span data-stu-id="1319b-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1319b-124">Zobrazí informace nápovědy.</span><span class="sxs-lookup"><span data-stu-id="1319b-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="1319b-125">Určuje cestu k runtime package store.</span><span class="sxs-lookup"><span data-stu-id="1319b-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="1319b-126">Pokud není zadán, je výchozí podadresář *úložiště* instalačního adresáře .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1319b-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="1319b-127">Přeskočí fázi optimalizace.</span><span class="sxs-lookup"><span data-stu-id="1319b-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="1319b-128">Přeskočí generování symbolů.</span><span class="sxs-lookup"><span data-stu-id="1319b-128">Skips symbol generation.</span></span> <span data-ttu-id="1319b-129">V současné době můžete generovat pouze symboly v systému Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="1319b-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="1319b-130">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="1319b-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1319b-131">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="1319b-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="1319b-132">Pracovní adresář používaný příkazem.</span><span class="sxs-lookup"><span data-stu-id="1319b-132">The working directory used by the command.</span></span> <span data-ttu-id="1319b-133">Pokud není zadán, používá *podadresář obj* aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="1319b-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="1319b-134">Příklady</span><span class="sxs-lookup"><span data-stu-id="1319b-134">Examples</span></span>

- <span data-ttu-id="1319b-135">Uložte balíčky zadané v souboru projektu *packages.csproj* pro rozhraní .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="1319b-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="1319b-136">Uložte balíčky zadané v *packages.csproj* bez optimalizace:</span><span class="sxs-lookup"><span data-stu-id="1319b-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="1319b-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="1319b-137">See also</span></span>

- [<span data-ttu-id="1319b-138">Úložiště balíčků modulu runtime</span><span class="sxs-lookup"><span data-stu-id="1319b-138">Runtime package store</span></span>](../deploying/runtime-store.md)
