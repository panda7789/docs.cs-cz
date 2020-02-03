---
title: dotnet – příkaz odstranění NuGet
description: Příkaz dotnet-NuGet-delete odstraní nebo zruší výpis balíčku ze serveru.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733119"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="f9fb7-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="f9fb7-103">dotnet nuget delete</span></span>

<span data-ttu-id="f9fb7-104">**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="f9fb7-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="f9fb7-105">Název</span><span class="sxs-lookup"><span data-stu-id="f9fb7-105">Name</span></span>

<span data-ttu-id="f9fb7-106">`dotnet nuget delete` – odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f9fb7-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="f9fb7-107">Synopsis</span></span>

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f9fb7-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f9fb7-108">Description</span></span>

<span data-ttu-id="f9fb7-109">Příkaz `dotnet nuget delete` odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="f9fb7-110">V případě [NuGet.org](https://www.nuget.org/)je akce odpisovat balíček.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="f9fb7-111">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f9fb7-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="f9fb7-112">Název nebo ID balíčku, který se má odstranit</span><span class="sxs-lookup"><span data-stu-id="f9fb7-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="f9fb7-113">Verze balíčku, který se má odstranit</span><span class="sxs-lookup"><span data-stu-id="f9fb7-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="f9fb7-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f9fb7-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="f9fb7-115">Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="f9fb7-116">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="f9fb7-117">Umožňuje příkazu blokovat a vyžadovat ruční akci pro operace, jako je ověřování.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="f9fb7-118">Možnost je k dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="f9fb7-119">Klíč rozhraní API pro server</span><span class="sxs-lookup"><span data-stu-id="f9fb7-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="f9fb7-120">Nepřipojí k zdrojové adrese URL rozhraní API/v2/Package.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="f9fb7-121">Možnost je k dispozici od verze .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="f9fb7-122">Nezobrazuje výzvu k zadání vstupu uživatele nebo potvrzení.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="f9fb7-123">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-123">Specifies the server URL.</span></span> <span data-ttu-id="f9fb7-124">Podporované adresy URL pro nuget.org zahrnují `https://www.nuget.org`, `https://www.nuget.org/api/v3`a `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="f9fb7-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="f9fb7-125">V případě privátních informačních kanálů nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="f9fb7-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="f9fb7-126">Příklady</span><span class="sxs-lookup"><span data-stu-id="f9fb7-126">Examples</span></span>

* <span data-ttu-id="f9fb7-127">Odstraní verzi 1,0 balíčku `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="f9fb7-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="f9fb7-128">Odstraní verzi 1,0 balíčku `Microsoft.AspNetCore.Mvc`, nezobrazuje výzvu k zadání přihlašovacích údajů nebo jiného vstupu:</span><span class="sxs-lookup"><span data-stu-id="f9fb7-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
