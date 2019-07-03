---
title: příkaz DotNet nuget místních hodnot
description: Příkaz dotnet nuget locals vymaže nebo vypíše místní prostředky NuGet, třeba mezipaměť požadavku http, dočasná mezipaměť nebo celý počítač globální složku balíčků.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 6436bbaee7ae50f4b225c32b2245c737b0d359c3
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539260"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="561c7-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="561c7-103">dotnet nuget locals</span></span>

<span data-ttu-id="561c7-104">**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="561c7-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="561c7-105">Name</span><span class="sxs-lookup"><span data-stu-id="561c7-105">Name</span></span>

<span data-ttu-id="561c7-106">`dotnet nuget locals` -Vymaže nebo vypíše místní prostředky NuGet.</span><span class="sxs-lookup"><span data-stu-id="561c7-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="561c7-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="561c7-107">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="561c7-108">Popis</span><span class="sxs-lookup"><span data-stu-id="561c7-108">Description</span></span>

<span data-ttu-id="561c7-109">`dotnet nuget locals` Příkaz vymaže nebo vypíše místní prostředky NuGet v mezipaměti požadavku http, dočasná mezipaměť nebo celý počítač globální složku balíčků.</span><span class="sxs-lookup"><span data-stu-id="561c7-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="561c7-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="561c7-110">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="561c7-111">Umístění mezipaměti seznamu nebo zrušte zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="561c7-111">The cache location to list or clear.</span></span> <span data-ttu-id="561c7-112">Přijímá jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="561c7-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="561c7-113">`all` – Označuje, že zadaná operace platí pro všechny typy mezipaměti: mezipaměť požadavku http, mezipaměť globálních balíčků a dočasná mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="561c7-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="561c7-114">`http-cache` -Označuje, že zadaná operace je použit pouze pro mezipaměť požadavku http.</span><span class="sxs-lookup"><span data-stu-id="561c7-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="561c7-115">Jiné umístění mezipaměti nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="561c7-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="561c7-116">`global-packages` -Označuje, že zadaná operace platí pouze pro mezipaměť globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="561c7-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="561c7-117">Jiné umístění mezipaměti nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="561c7-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="561c7-118">`temp` -Označuje, že zadaná operace platí jenom pro dočasná mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="561c7-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="561c7-119">Jiné umístění mezipaměti nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="561c7-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="561c7-120">Možnosti</span><span class="sxs-lookup"><span data-stu-id="561c7-120">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="561c7-121">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="561c7-121">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="561c7-122">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="561c7-122">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="561c7-123">Zrušte zaškrtnutí možnost provede operaci zrušte na typ zadaný mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="561c7-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="561c7-124">Obsah adresáře mezipaměti jsou odstraněné rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="561c7-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="561c7-125">Provádění uživatele nebo skupiny musí mít oprávnění k souborům v adresářích mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="561c7-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="561c7-126">Pokud tomu tak není, zobrazí se chyba, která souborů a složek, které nebyly vymazány.</span><span class="sxs-lookup"><span data-stu-id="561c7-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="561c7-127">Možnost seznamu se používá k zobrazení umístění mezipaměti zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="561c7-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="561c7-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="561c7-128">Examples</span></span>

* <span data-ttu-id="561c7-129">Zobrazuje cesty ke všem adresářům místní mezipaměti (http-cache adresáře, cesta k adresáři mezipaměti global-packages a cesta k adresáři mezipaměti pro dočasné):</span><span class="sxs-lookup"><span data-stu-id="561c7-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="561c7-130">Zobrazuje cestu k adresáři místní mezipaměť http:</span><span class="sxs-lookup"><span data-stu-id="561c7-130">Displays the path for the local http-cache directory:</span></span>

  ```console
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="561c7-131">Vymaže všechny soubory z adresáře všechny místní mezipaměti (http-cache adresáře, cesta k adresáři mezipaměti global-packages a cesta k adresáři mezipaměti pro dočasné):</span><span class="sxs-lookup"><span data-stu-id="561c7-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="561c7-132">Vymaže všechny soubory v adresáři místního global-packages mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="561c7-132">Clears all files in local global-packages cache directory:</span></span>

  ```console
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="561c7-133">Vymaže všechny soubory v adresáři místní dočasné mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="561c7-133">Clears all files in local temporary cache directory:</span></span>

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="561c7-134">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="561c7-134">Troubleshooting</span></span>

<span data-ttu-id="561c7-135">Informace o běžných problémech a chyb při použití `dotnet nuget locals` naleznete [Správa mezipaměti Nugetu](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="561c7-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
