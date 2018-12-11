---
title: příkaz DotNet nuget místních hodnot
description: Příkaz dotnet nuget locals vymaže nebo vypíše místní prostředky NuGet, třeba mezipaměť požadavku http, dočasná mezipaměť nebo celý počítač globální složku balíčků.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: d0f1c7c2e0b233c214cc48d026c19755fc047bfa
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170753"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="becfc-103">DotNet nuget locals</span><span class="sxs-lookup"><span data-stu-id="becfc-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="becfc-104">Název</span><span class="sxs-lookup"><span data-stu-id="becfc-104">Name</span></span>

<span data-ttu-id="becfc-105">`dotnet nuget locals` -Vymaže nebo vypíše místní prostředky NuGet.</span><span class="sxs-lookup"><span data-stu-id="becfc-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="becfc-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="becfc-106">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="becfc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="becfc-107">Description</span></span>

<span data-ttu-id="becfc-108">`dotnet nuget locals` Příkaz vymaže nebo vypíše místní prostředky NuGet v mezipaměti požadavku http, dočasná mezipaměť nebo celý počítač globální složku balíčků.</span><span class="sxs-lookup"><span data-stu-id="becfc-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="becfc-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="becfc-109">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="becfc-110">Umístění mezipaměti seznamu nebo zrušte zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="becfc-110">The cache location to list or clear.</span></span> <span data-ttu-id="becfc-111">Přijímá jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="becfc-111">It accepts one of the following values:</span></span>

  * <span data-ttu-id="becfc-112">`all` – Označuje, že zadaná operace platí pro všechny typy mezipaměti: mezipaměť požadavku http, mezipaměť globálních balíčků a dočasná mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="becfc-112">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="becfc-113">`http-cache` -Označuje, že zadaná operace je použit pouze pro mezipaměť požadavku http.</span><span class="sxs-lookup"><span data-stu-id="becfc-113">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="becfc-114">Jiné umístění mezipaměti nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="becfc-114">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="becfc-115">`global-packages` -Označuje, že zadaná operace platí pouze pro mezipaměť globálních balíčků.</span><span class="sxs-lookup"><span data-stu-id="becfc-115">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="becfc-116">Jiné umístění mezipaměti nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="becfc-116">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="becfc-117">`temp` -Označuje, že zadaná operace platí jenom pro dočasná mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="becfc-117">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="becfc-118">Jiné umístění mezipaměti nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="becfc-118">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="becfc-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="becfc-119">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="becfc-120">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="becfc-120">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="becfc-121">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="becfc-121">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="becfc-122">Zrušte zaškrtnutí možnost provede operaci zrušte na typ zadaný mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="becfc-122">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="becfc-123">Obsah adresáře mezipaměti jsou odstraněné rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="becfc-123">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="becfc-124">Provádění uživatele nebo skupiny musí mít oprávnění k souborům v adresářích mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="becfc-124">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="becfc-125">Pokud tomu tak není, zobrazí se chyba, která souborů a složek, které nebyly vymazány.</span><span class="sxs-lookup"><span data-stu-id="becfc-125">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="becfc-126">Možnost seznamu se používá k zobrazení umístění mezipaměti zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="becfc-126">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="becfc-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="becfc-127">Examples</span></span>

* <span data-ttu-id="becfc-128">Zobrazuje cesty ke všem adresářům místní mezipaměti (http-cache adresáře, cesta k adresáři mezipaměti global-packages a cesta k adresáři mezipaměti pro dočasné):</span><span class="sxs-lookup"><span data-stu-id="becfc-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="becfc-129">Zobrazuje cestu k adresáři místní mezipaměť http:</span><span class="sxs-lookup"><span data-stu-id="becfc-129">Displays the path for the local http-cache directory:</span></span>

  ```console
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="becfc-130">Vymaže všechny soubory z adresáře všechny místní mezipaměti (http-cache adresáře, cesta k adresáři mezipaměti global-packages a cesta k adresáři mezipaměti pro dočasné):</span><span class="sxs-lookup"><span data-stu-id="becfc-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="becfc-131">Vymaže všechny soubory v adresáři místního global-packages mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="becfc-131">Clears all files in local global-packages cache directory:</span></span>

  ```console
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="becfc-132">Vymaže všechny soubory v adresáři místní dočasné mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="becfc-132">Clears all files in local temporary cache directory:</span></span>

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="becfc-133">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="becfc-133">Troubleshooting</span></span>

<span data-ttu-id="becfc-134">Informace o běžných problémech a chyb při použití `dotnet nuget locals` naleznete [Správa mezipaměti Nugetu](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="becfc-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>