---
title: dotnet – příkaz pro úložiště
description: Příkaz dotnet Store ukládá zadaná sestavení do úložiště balíčků modulu runtime.
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503577"
---
# <a name="dotnet-store"></a><span data-ttu-id="7818f-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="7818f-103">dotnet store</span></span>

<span data-ttu-id="7818f-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="7818f-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7818f-105">Název</span><span class="sxs-lookup"><span data-stu-id="7818f-105">Name</span></span>

<span data-ttu-id="7818f-106">`dotnet store` – uloží zadaná sestavení do [úložiště balíčků modulu runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="7818f-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="7818f-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="7818f-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a><span data-ttu-id="7818f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7818f-108">Description</span></span>

<span data-ttu-id="7818f-109">`dotnet store` ukládá zadaná sestavení do [úložiště balíčků modulu runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="7818f-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="7818f-110">Ve výchozím nastavení jsou sestavení optimalizována pro cílový modul runtime a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7818f-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="7818f-111">Další informace najdete v tématu [úložiště balíčků za běhu](../deploying/runtime-store.md) .</span><span class="sxs-lookup"><span data-stu-id="7818f-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="7818f-112">Požadované možnosti</span><span class="sxs-lookup"><span data-stu-id="7818f-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="7818f-113">Určuje [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="7818f-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="7818f-114">Cílová architektura musí být zadána v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="7818f-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="7818f-115">*Soubor manifestu úložiště balíčku* je soubor XML, který obsahuje seznam balíčků, které mají být uloženy.</span><span class="sxs-lookup"><span data-stu-id="7818f-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="7818f-116">Formát souboru manifestu je kompatibilní s formátem projektu ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="7818f-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="7818f-117">Soubor projektu, který odkazuje na požadované balíčky, lze proto použít s možností `-m|--manifest` pro uložení sestavení v úložišti balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7818f-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="7818f-118">Chcete-li zadat více souborů manifestu, opakujte možnost a cestu pro každý soubor.</span><span class="sxs-lookup"><span data-stu-id="7818f-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="7818f-119">Například: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="7818f-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="7818f-120">[Identifikátor modulu runtime](../rid-catalog.md) , který má být cílen.</span><span class="sxs-lookup"><span data-stu-id="7818f-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="7818f-121">Volitelné možnosti</span><span class="sxs-lookup"><span data-stu-id="7818f-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="7818f-122">Určuje .NET Core SDK verzi.</span><span class="sxs-lookup"><span data-stu-id="7818f-122">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="7818f-123">Tato možnost umožňuje vybrat konkrétní verzi rozhraní nad rámec určenou možností `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="7818f-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="7818f-124">Zobrazí informace o nápovědě.</span><span class="sxs-lookup"><span data-stu-id="7818f-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="7818f-125">Určuje cestu k úložišti balíčků modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7818f-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="7818f-126">Pokud není zadaný, použije se výchozí podadresář *úložiště* instalačního adresáře .NET Core uživatelského profilu.</span><span class="sxs-lookup"><span data-stu-id="7818f-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="7818f-127">Přeskočí fázi optimalizace.</span><span class="sxs-lookup"><span data-stu-id="7818f-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="7818f-128">Přeskočí generování symbolů.</span><span class="sxs-lookup"><span data-stu-id="7818f-128">Skips symbol generation.</span></span> <span data-ttu-id="7818f-129">V současné době můžete generovat symboly jenom v systémech Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="7818f-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7818f-130">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="7818f-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7818f-131">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7818f-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="7818f-132">Pracovní adresář použitý příkazem.</span><span class="sxs-lookup"><span data-stu-id="7818f-132">The working directory used by the command.</span></span> <span data-ttu-id="7818f-133">Pokud není zadaný, použije se podadresář *obj* aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="7818f-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="7818f-134">Příklady</span><span class="sxs-lookup"><span data-stu-id="7818f-134">Examples</span></span>

- <span data-ttu-id="7818f-135">Uložte balíčky zadané v souboru projektu *Packages. csproj* pro .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="7818f-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="7818f-136">Uložit balíčky zadané v *balíčku. csproj* bez optimalizace:</span><span class="sxs-lookup"><span data-stu-id="7818f-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="7818f-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="7818f-137">See also</span></span>

- [<span data-ttu-id="7818f-138">Úložiště balíčků modulu runtime</span><span class="sxs-lookup"><span data-stu-id="7818f-138">Runtime package store</span></span>](../deploying/runtime-store.md)
