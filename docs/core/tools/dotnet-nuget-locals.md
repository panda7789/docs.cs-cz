---
title: "příkaz místní hodnoty – DotNet nuget - .NET Core rozhraní příkazového řádku"
description: "Příkaz dotnet nuget místní hodnoty – vymaže nebo vypíše místní prostředky NuGet například mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 2b66198ac3e33c640abda0c96fb05944f5ea91df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="a9e0e-103">místní hodnoty nuget DotNet.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a9e0e-104">Název</span><span class="sxs-lookup"><span data-stu-id="a9e0e-104">Name</span></span>

<span data-ttu-id="a9e0e-105">`dotnet nuget locals`-Vymaže nebo vypíše místní prostředky NuGet.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a9e0e-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="a9e0e-106">Synopsis</span></span>

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="a9e0e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a9e0e-107">Description</span></span>

<span data-ttu-id="a9e0e-108">`dotnet nuget locals` Příkaz vymaže nebo vypíše místní prostředky NuGet v mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="a9e0e-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="a9e0e-109">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="a9e0e-110">Jedna z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="a9e0e-110">One of the following values:</span></span>

* <span data-ttu-id="a9e0e-111">`all`-Určuje, že zadaná operace platí pro všechny typy mezipaměti: mezipaměti požadavek http, globální balíčky mezipaměti a dočasnou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-111">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
* <span data-ttu-id="a9e0e-112">`http-cache`-Určuje, že zadaná operace platí pouze do mezipaměti v požadavku http.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-112">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="a9e0e-113">Ovlivněné nejsou jiných umístění mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-113">The other cache locations are not affected.</span></span>
* <span data-ttu-id="a9e0e-114">`global-packages`-Určuje, že zadaná operace se aplikuje jenom na globální balíčky mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-114">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="a9e0e-115">Ovlivněné nejsou jiných umístění mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-115">The other cache locations are not affected.</span></span>
* <span data-ttu-id="a9e0e-116">`temp`-Určuje, že zadaná operace se aplikuje jenom na dočasnou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-116">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="a9e0e-117">Ovlivněné nejsou jiných umístění mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-117">The other cache locations are not affected.</span></span>

## <a name="options"></a><span data-ttu-id="a9e0e-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a9e0e-118">Options</span></span>

`-h|--help`

<span data-ttu-id="a9e0e-119">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-119">Prints out a short help for the command.</span></span>

`-c|--clear`

<span data-ttu-id="a9e0e-120">Zrušte možnost provádí zrušte operaci na zadaný mezipaměti typu.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-120">The clear option performs a clear operation on the specified cache type.</span></span> <span data-ttu-id="a9e0e-121">Obsah mezipaměti adresáře jsou odstraněné rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-121">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="a9e0e-122">Provádění uživatel nebo skupina musí mít oprávnění k souborům v adresáři mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-122">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="a9e0e-123">Pokud ne, zobrazí se chybová zpráva, která udává, soubory a složky, které nejsou vymazána.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-123">If not, an error is displayed indicating the files/folders which were not cleared.</span></span>

`-l|--list`

<span data-ttu-id="a9e0e-124">V seznamu možnost se používá pro zobrazení umístění mezipaměti zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-124">The list option is used to display the location of the specified cache type.</span></span> 

`--force-english-output`

<span data-ttu-id="a9e0e-125">Vynutí příkazového řádku výstup v angličtině.</span><span class="sxs-lookup"><span data-stu-id="a9e0e-125">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="a9e0e-126">Příklady</span><span class="sxs-lookup"><span data-stu-id="a9e0e-126">Examples</span></span>

<span data-ttu-id="a9e0e-127">Zobrazí cesty všechny adresáře místní mezipaměti (adresář mezipaměti protokolu http, adresář mezipaměti globální balíčky a adresář mezipaměti pro dočasné):</span><span class="sxs-lookup"><span data-stu-id="a9e0e-127">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="a9e0e-128">Zobrazuje cestu k adresáři místní mezipaměti http:</span><span class="sxs-lookup"><span data-stu-id="a9e0e-128">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="a9e0e-129">Vymaže všechny soubory ze všech adresářů místní mezipaměti (adresář mezipaměti protokolu http, adresář mezipaměti globální balíčky a adresář mezipaměti pro dočasné):</span><span class="sxs-lookup"><span data-stu-id="a9e0e-129">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="a9e0e-130">Vymaže všechny soubory v adresáři mezipaměti místní globální balíčky:</span><span class="sxs-lookup"><span data-stu-id="a9e0e-130">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="a9e0e-131">Vymaže všechny soubory v adresáři místní dočasné mezipaměti:</span><span class="sxs-lookup"><span data-stu-id="a9e0e-131">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="a9e0e-132">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="a9e0e-132">Troubleshooting</span></span>

<span data-ttu-id="a9e0e-133">Informace o běžné problémy a chyby při použití `dotnet nuget locals` příkazů najdete v tématu [Správa mezipaměti NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="a9e0e-133">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>