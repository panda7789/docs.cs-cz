---
title: dotnet – místní příkazy NuGet
description: Příkaz dotnet NuGet Locals vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 3fdd7d946b08b4c18cfaeb65013de259b927a7fa
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503692"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="37dfc-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="37dfc-103">dotnet nuget locals</span></span>

<span data-ttu-id="37dfc-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="37dfc-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="37dfc-105">Název</span><span class="sxs-lookup"><span data-stu-id="37dfc-105">Name</span></span>

<span data-ttu-id="37dfc-106">`dotnet nuget locals` – vymaže nebo vypíše místní prostředky NuGet.</span><span class="sxs-lookup"><span data-stu-id="37dfc-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="37dfc-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="37dfc-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="37dfc-108">Popis</span><span class="sxs-lookup"><span data-stu-id="37dfc-108">Description</span></span>

<span data-ttu-id="37dfc-109">Příkaz `dotnet nuget locals` vymaže nebo vypíše místní prostředky NuGet v mezipaměti požadavku HTTP, dočasné mezipaměti nebo v rámci globální složky balíčků v celém počítači.</span><span class="sxs-lookup"><span data-stu-id="37dfc-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="37dfc-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="37dfc-110">Arguments</span></span>

- **`CACHE_LOCATION`**

  <span data-ttu-id="37dfc-111">Umístění mezipaměti, které se má vypsat nebo vymazat</span><span class="sxs-lookup"><span data-stu-id="37dfc-111">The cache location to list or clear.</span></span> <span data-ttu-id="37dfc-112">Přijímá jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="37dfc-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="37dfc-113">`all` – určuje, že zadaná operace se použije pro všechny typy mezipaměti: mezipaměť požadavků HTTP, mezipaměť globálních balíčků a dočasná mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="37dfc-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="37dfc-114">`http-cache` – určuje, že zadaná operace se použije jenom pro mezipaměť http požadavku.</span><span class="sxs-lookup"><span data-stu-id="37dfc-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="37dfc-115">Ostatní umístění mezipaměti nejsou ovlivněna.</span><span class="sxs-lookup"><span data-stu-id="37dfc-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="37dfc-116">`global-packages` – určuje, že zadaná operace se použije jenom pro mezipaměť globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="37dfc-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="37dfc-117">Ostatní umístění mezipaměti nejsou ovlivněna.</span><span class="sxs-lookup"><span data-stu-id="37dfc-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="37dfc-118">`temp` – určuje, že zadaná operace se použije jenom pro dočasnou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="37dfc-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="37dfc-119">Ostatní umístění mezipaměti nejsou ovlivněna.</span><span class="sxs-lookup"><span data-stu-id="37dfc-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="37dfc-120">Možnosti</span><span class="sxs-lookup"><span data-stu-id="37dfc-120">Options</span></span>

- **`--force-english-output`**

  <span data-ttu-id="37dfc-121">Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.</span><span class="sxs-lookup"><span data-stu-id="37dfc-121">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="37dfc-122">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="37dfc-122">Prints out a short help for the command.</span></span>

- **`-c|--clear`**

  <span data-ttu-id="37dfc-123">Možnost Clear spustí u zadaného typu mezipaměti operaci Clear.</span><span class="sxs-lookup"><span data-stu-id="37dfc-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="37dfc-124">Obsah adresářů mezipaměti se odstraní rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="37dfc-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="37dfc-125">Spuštěný uživatel nebo skupina musí mít oprávnění k souborům v adresářích mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="37dfc-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="37dfc-126">V takovém případě se zobrazí chyba označující soubory nebo složky, které nebyly vymazány.</span><span class="sxs-lookup"><span data-stu-id="37dfc-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

- **`-l|--list`**

  <span data-ttu-id="37dfc-127">Možnost seznam slouží k zobrazení umístění zadaného typu mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="37dfc-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="37dfc-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="37dfc-128">Examples</span></span>

- <span data-ttu-id="37dfc-129">Zobrazuje cesty ke všem adresářům místní mezipaměti (adresář HTTP-cache, adresář mezipaměti globálních balíčků a dočasný adresář mezipaměti):</span><span class="sxs-lookup"><span data-stu-id="37dfc-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- <span data-ttu-id="37dfc-130">Zobrazuje cestu k místnímu adresáři protokolu HTTP-cache:</span><span class="sxs-lookup"><span data-stu-id="37dfc-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- <span data-ttu-id="37dfc-131">Vymaže všechny soubory ze všech adresářů místní mezipaměti (adresář mezipaměti protokolu HTTP, adresář mezipaměti globálních balíčků a dočasný adresář mezipaměti):</span><span class="sxs-lookup"><span data-stu-id="37dfc-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- <span data-ttu-id="37dfc-132">Vymaže všechny soubory v místní složce mezipaměti Global-Packages:</span><span class="sxs-lookup"><span data-stu-id="37dfc-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- <span data-ttu-id="37dfc-133">Vymaže všechny soubory v adresáři místní dočasné mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="37dfc-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a><span data-ttu-id="37dfc-134">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="37dfc-134">Troubleshooting</span></span>

<span data-ttu-id="37dfc-135">Informace o běžných problémech a chybách při použití příkazu `dotnet nuget locals` najdete v tématu [Správa mezipaměti NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="37dfc-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
