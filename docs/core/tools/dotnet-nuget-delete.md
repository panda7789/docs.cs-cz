---
title: dotnet nuget odstranit příkaz
description: Příkaz dotnet-nuget-delete odstraní nebo vyřadí balíček ze serveru.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733119"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="97359-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="97359-103">dotnet nuget delete</span></span>

<span data-ttu-id="97359-104">**Tento článek se týká:** ✔️ .NET Core 1.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="97359-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="97359-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="97359-105">Name</span></span>

<span data-ttu-id="97359-106">`dotnet nuget delete`- Odstraní nebo unlists balíček ze serveru.</span><span class="sxs-lookup"><span data-stu-id="97359-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="97359-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="97359-107">Synopsis</span></span>

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="97359-108">Popis</span><span class="sxs-lookup"><span data-stu-id="97359-108">Description</span></span>

<span data-ttu-id="97359-109">Příkaz `dotnet nuget delete` odstraní nebo odseznamuje balíček ze serveru.</span><span class="sxs-lookup"><span data-stu-id="97359-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="97359-110">Pro [nuget.org](https://www.nuget.org/)je akce zrušit seznam balíčku.</span><span class="sxs-lookup"><span data-stu-id="97359-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="97359-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="97359-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="97359-112">Název/ID balíčku, který má být odstraněn.</span><span class="sxs-lookup"><span data-stu-id="97359-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="97359-113">Verze balíčku odstranit.</span><span class="sxs-lookup"><span data-stu-id="97359-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="97359-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="97359-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="97359-115">Vynutí spuštění aplikace pomocí invariantní jazykové verze založené na angličtině.</span><span class="sxs-lookup"><span data-stu-id="97359-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="97359-116">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="97359-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="97359-117">Umožňuje příkaz blokovat a vyžaduje ruční akci pro operace, jako je ověřování.</span><span class="sxs-lookup"><span data-stu-id="97359-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="97359-118">Možnost je k dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="97359-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="97359-119">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="97359-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="97359-120">Nepřipojí "api/v2/package" ke zdrojové adrese URL.</span><span class="sxs-lookup"><span data-stu-id="97359-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="97359-121">Možnost je k dispozici od .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="97359-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="97359-122">Nezobrazí výzvu k zadání uživatele nebo potvrzení.</span><span class="sxs-lookup"><span data-stu-id="97359-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="97359-123">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="97359-123">Specifies the server URL.</span></span> <span data-ttu-id="97359-124">Mezi podporované adresy URL `https://www.nuget.org` `https://www.nuget.org/api/v3`pro `https://www.nuget.org/api/v2/package`nuget.org patří , a .</span><span class="sxs-lookup"><span data-stu-id="97359-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="97359-125">U soukromých informačních kanálů nahraďte `%hostname%/api/v3`název hostitele (například).</span><span class="sxs-lookup"><span data-stu-id="97359-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="97359-126">Příklady</span><span class="sxs-lookup"><span data-stu-id="97359-126">Examples</span></span>

* <span data-ttu-id="97359-127">Odstraní verzi 1.0 `Microsoft.AspNetCore.Mvc`balíčku :</span><span class="sxs-lookup"><span data-stu-id="97359-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="97359-128">Odstraní verzi 1.0 `Microsoft.AspNetCore.Mvc`balíčku , nevyzve uživatele k zadání pověření nebo jiného vstupu:</span><span class="sxs-lookup"><span data-stu-id="97359-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
