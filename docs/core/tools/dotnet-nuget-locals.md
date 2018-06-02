---
title: příkaz místní hodnoty – DotNet nuget - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet nuget místní hodnoty – vymaže nebo vypíše místní prostředky NuGet například mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 799acb92d6ab7439e15c23c9f0b7b572c966adda
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696868"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="b5a12-103">místní hodnoty nuget DotNet.</span><span class="sxs-lookup"><span data-stu-id="b5a12-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b5a12-104">Název</span><span class="sxs-lookup"><span data-stu-id="b5a12-104">Name</span></span>

<span data-ttu-id="b5a12-105">`dotnet nuget locals` -Vymaže nebo vypíše místní prostředky NuGet.</span><span class="sxs-lookup"><span data-stu-id="b5a12-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b5a12-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="b5a12-106">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="b5a12-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b5a12-107">Description</span></span>

<span data-ttu-id="b5a12-108">`dotnet nuget locals` Příkaz vymaže nebo vypíše místní prostředky NuGet v mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.</span><span class="sxs-lookup"><span data-stu-id="b5a12-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="b5a12-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="b5a12-109">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="b5a12-110">Umístění mezipaměti k zobrazení seznamu nebo vymazat.</span><span class="sxs-lookup"><span data-stu-id="b5a12-110">The cache location to list or clear.</span></span> <span data-ttu-id="b5a12-111">Přijme jeden z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="b5a12-111">It accepts one of the following values:</span></span>

* <span data-ttu-id="b5a12-112">`all` -Určuje, že zadaná operace platí pro všechny typy mezipaměti: mezipaměti požadavek http, globální balíčky mezipaměti a dočasnou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="b5a12-112">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
* <span data-ttu-id="b5a12-113">`http-cache` -Určuje, že zadaná operace platí pouze do mezipaměti v požadavku http.</span><span class="sxs-lookup"><span data-stu-id="b5a12-113">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="b5a12-114">Ovlivněné nejsou jiných umístění mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b5a12-114">The other cache locations aren't affected.</span></span>
* <span data-ttu-id="b5a12-115">`global-packages` -Určuje, že zadaná operace se aplikuje jenom na globální balíčky mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b5a12-115">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="b5a12-116">Ovlivněné nejsou jiných umístění mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b5a12-116">The other cache locations aren't affected.</span></span>
* <span data-ttu-id="b5a12-117">`temp` -Určuje, že zadaná operace se aplikuje jenom na dočasnou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="b5a12-117">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="b5a12-118">Ovlivněné nejsou jiných umístění mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b5a12-118">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="b5a12-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b5a12-119">Options</span></span>

`--force-english-output`

<span data-ttu-id="b5a12-120">Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5a12-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="b5a12-121">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="b5a12-121">Prints out a short help for the command.</span></span>

`-c|--clear`

<span data-ttu-id="b5a12-122">Zrušte možnost provede zrušte operaci na zadaný mezipaměti typu.</span><span class="sxs-lookup"><span data-stu-id="b5a12-122">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="b5a12-123">Obsah mezipaměti adresáře jsou odstraněné rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="b5a12-123">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="b5a12-124">Provádění uživatel nebo skupina musí mít oprávnění k souborům v adresáři mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b5a12-124">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="b5a12-125">Pokud ne, zobrazí se chybová zpráva označující, soubory a složky, které nejsou vymazána.</span><span class="sxs-lookup"><span data-stu-id="b5a12-125">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

`-l|--list`

<span data-ttu-id="b5a12-126">V seznamu možnost se používá pro zobrazení umístění mezipaměti zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="b5a12-126">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="b5a12-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="b5a12-127">Examples</span></span>

<span data-ttu-id="b5a12-128">Zobrazí cesty všechny adresáře místní mezipaměti (adresář mezipaměti protokolu http, adresář mezipaměti globální balíčky a adresář mezipaměti pro dočasné):</span><span class="sxs-lookup"><span data-stu-id="b5a12-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="b5a12-129">Zobrazuje cestu k adresáři místní mezipaměti http:</span><span class="sxs-lookup"><span data-stu-id="b5a12-129">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="b5a12-130">Vymaže všechny soubory ze všech adresářů místní mezipaměti (adresář mezipaměti protokolu http, adresář mezipaměti globální balíčky a adresář mezipaměti pro dočasné):</span><span class="sxs-lookup"><span data-stu-id="b5a12-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="b5a12-131">Vymaže všechny soubory v adresáři mezipaměti místní globální balíčky:</span><span class="sxs-lookup"><span data-stu-id="b5a12-131">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="b5a12-132">Vymaže všechny soubory v adresáři místní dočasné mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="b5a12-132">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="b5a12-133">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="b5a12-133">Troubleshooting</span></span>

<span data-ttu-id="b5a12-134">Informace o běžné problémy a chyby při použití `dotnet nuget locals` příkazů najdete v tématu [Správa mezipaměti NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="b5a12-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>