---
title: dotnet nuget locals, příkaz
description: Dotnet nuget locals příkaz vymaže nebo uvádí místní nugetové prostředky, jako je například mezipaměť požadavků http, dočasná mezipaměť nebo globální složky globálních balíčků pro celý počítač.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 3fdd7d946b08b4c18cfaeb65013de259b927a7fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503692"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="e33d0-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="e33d0-103">dotnet nuget locals</span></span>

<span data-ttu-id="e33d0-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="e33d0-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e33d0-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="e33d0-105">Name</span></span>

<span data-ttu-id="e33d0-106">`dotnet nuget locals`- Vymaže nebo zobrazí seznam místních prostředků NuGet.</span><span class="sxs-lookup"><span data-stu-id="e33d0-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e33d0-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="e33d0-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="e33d0-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e33d0-108">Description</span></span>

<span data-ttu-id="e33d0-109">Příkaz `dotnet nuget locals` vymaže nebo zobrazí seznam místních prostředků NuGet ve složce http-request cache, temporary cache nebo global packages pro celý počítač.</span><span class="sxs-lookup"><span data-stu-id="e33d0-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="e33d0-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e33d0-110">Arguments</span></span>

- **`CACHE_LOCATION`**

  <span data-ttu-id="e33d0-111">Umístění mezipaměti do seznamu nebo vymazání.</span><span class="sxs-lookup"><span data-stu-id="e33d0-111">The cache location to list or clear.</span></span> <span data-ttu-id="e33d0-112">Přijímá jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="e33d0-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="e33d0-113">`all`- Označuje, že zadaná operace je použita pro všechny typy mezipaměti: http-request cache, globální balíčky mezipaměti a dočasné mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e33d0-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="e33d0-114">`http-cache`- Označuje, že zadaná operace je použita pouze pro mezipaměť požadavků http.</span><span class="sxs-lookup"><span data-stu-id="e33d0-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="e33d0-115">Ostatní umístění mezipaměti nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="e33d0-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="e33d0-116">`global-packages`- Označuje, že zadaná operace je použita pouze pro globální mezipaměti balíčků.</span><span class="sxs-lookup"><span data-stu-id="e33d0-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="e33d0-117">Ostatní umístění mezipaměti nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="e33d0-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="e33d0-118">`temp`- Označuje, že zadaná operace je použita pouze pro dočasnou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="e33d0-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="e33d0-119">Ostatní umístění mezipaměti nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="e33d0-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="e33d0-120">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e33d0-120">Options</span></span>

- **`--force-english-output`**

  <span data-ttu-id="e33d0-121">Vynutí spuštění aplikace pomocí invariantní jazykové verze založené na angličtině.</span><span class="sxs-lookup"><span data-stu-id="e33d0-121">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e33d0-122">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="e33d0-122">Prints out a short help for the command.</span></span>

- **`-c|--clear`**

  <span data-ttu-id="e33d0-123">Možnost vymazání provede jasnou operaci u zadaného typu mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e33d0-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="e33d0-124">Obsah adresářů mezipaměti jsou odstraněny rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="e33d0-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="e33d0-125">Vykonávající uživatel nebo skupina musí mít oprávnění k souborům v adresářích mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e33d0-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="e33d0-126">Pokud tomu tak není, zobrazí se chyba označující soubory nebo složky, které nebyly vymazány.</span><span class="sxs-lookup"><span data-stu-id="e33d0-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

- **`-l|--list`**

  <span data-ttu-id="e33d0-127">Možnost seznamu se používá k zobrazení umístění zadaného typu mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e33d0-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="e33d0-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="e33d0-128">Examples</span></span>

- <span data-ttu-id="e33d0-129">Zobrazí cesty všech adresářů místní mezipaměti (adresář http-cache, adresář mezipaměti globálních balíčků a dočasný adresář mezipaměti):</span><span class="sxs-lookup"><span data-stu-id="e33d0-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- <span data-ttu-id="e33d0-130">Zobrazí cestu k místnímu adresáři http-cache:</span><span class="sxs-lookup"><span data-stu-id="e33d0-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- <span data-ttu-id="e33d0-131">Vymaže všechny soubory ze všech adresářů místní mezipaměti (adresář http-cache, adresář mezipaměti globálních balíčků a dočasný adresář mezipaměti):</span><span class="sxs-lookup"><span data-stu-id="e33d0-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- <span data-ttu-id="e33d0-132">Vymaže všechny soubory v adresáři mezipaměti místních globálních balíčků:</span><span class="sxs-lookup"><span data-stu-id="e33d0-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- <span data-ttu-id="e33d0-133">Vymaže všechny soubory v místním adresáři dočasné mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="e33d0-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a><span data-ttu-id="e33d0-134">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="e33d0-134">Troubleshooting</span></span>

<span data-ttu-id="e33d0-135">Informace o běžných problémech `dotnet nuget locals` a chybách při použití příkazu naleznete v [tématu Správa mezipaměti NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="e33d0-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
