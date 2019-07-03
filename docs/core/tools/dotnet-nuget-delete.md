---
title: příkaz DotNet nuget delete
description: Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0b2ba64b70bae5e06f213457e30fedeca26a9819
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539256"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="c1fff-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="c1fff-103">dotnet nuget delete</span></span>

<span data-ttu-id="c1fff-104">**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="c1fff-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="c1fff-105">Name</span><span class="sxs-lookup"><span data-stu-id="c1fff-105">Name</span></span>

<span data-ttu-id="c1fff-106">`dotnet nuget delete` -Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="c1fff-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c1fff-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="c1fff-107">Synopsis</span></span>

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c1fff-108">Popis</span><span class="sxs-lookup"><span data-stu-id="c1fff-108">Description</span></span>

<span data-ttu-id="c1fff-109">`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="c1fff-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="c1fff-110">Pro [nuget.org](https://www.nuget.org/), "action" je k vyjmutí ze seznamu balíčku.</span><span class="sxs-lookup"><span data-stu-id="c1fff-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="c1fff-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="c1fff-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="c1fff-112">Název nebo ID balíčku, který se odstranit.</span><span class="sxs-lookup"><span data-stu-id="c1fff-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="c1fff-113">Verze balíčku, který se odstranit.</span><span class="sxs-lookup"><span data-stu-id="c1fff-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="c1fff-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c1fff-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="c1fff-115">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="c1fff-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="c1fff-116">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c1fff-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="c1fff-117">Umožňuje příkazu blokování a vyžaduje ruční akci pro operace, jako je například ověřování.</span><span class="sxs-lookup"><span data-stu-id="c1fff-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="c1fff-118">Možnost dostupné od verze sady SDK 2.2 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1fff-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="c1fff-119">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="c1fff-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="c1fff-120">"Api/v2/balíček" nemá připojení k zdrojová adresa URL.</span><span class="sxs-lookup"><span data-stu-id="c1fff-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="c1fff-121">Možnost dostupné od verze sady SDK .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="c1fff-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="c1fff-122">Není výzvu k zadání uživatele o vstup ani potvrzení.</span><span class="sxs-lookup"><span data-stu-id="c1fff-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="c1fff-123">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="c1fff-123">Specifies the server URL.</span></span> <span data-ttu-id="c1fff-124">Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="c1fff-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="c1fff-125">Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="c1fff-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="c1fff-126">Příklady</span><span class="sxs-lookup"><span data-stu-id="c1fff-126">Examples</span></span>

* <span data-ttu-id="c1fff-127">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="c1fff-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="c1fff-128">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, ne výzvou pro uživatele pro přihlašovací údaje nebo druhý vstup:</span><span class="sxs-lookup"><span data-stu-id="c1fff-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
