---
title: dotnet – příkaz odstranění NuGet
description: Příkaz dotnet-NuGet-delete odstraní nebo zruší výpis balíčku ze serveru.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 79634baa9d6d7ff1f388f6a794ffd816687be105
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117632"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="b5837-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="b5837-103">dotnet nuget delete</span></span>

<span data-ttu-id="b5837-104">**Toto téma se týká: ✓** .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="b5837-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="b5837-105">Name</span><span class="sxs-lookup"><span data-stu-id="b5837-105">Name</span></span>

<span data-ttu-id="b5837-106">`dotnet nuget delete`-Odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="b5837-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b5837-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="b5837-107">Synopsis</span></span>

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="b5837-108">Popis</span><span class="sxs-lookup"><span data-stu-id="b5837-108">Description</span></span>

<span data-ttu-id="b5837-109">`dotnet nuget delete` Příkaz odstraní nebo zruší výpis balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="b5837-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="b5837-110">V případě [NuGet.org](https://www.nuget.org/)je akce odpisovat balíček.</span><span class="sxs-lookup"><span data-stu-id="b5837-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="b5837-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="b5837-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="b5837-112">Název nebo ID balíčku, který se má odstranit</span><span class="sxs-lookup"><span data-stu-id="b5837-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="b5837-113">Verze balíčku, který se má odstranit</span><span class="sxs-lookup"><span data-stu-id="b5837-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="b5837-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b5837-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="b5837-115">Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.</span><span class="sxs-lookup"><span data-stu-id="b5837-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="b5837-116">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="b5837-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="b5837-117">Umožňuje příkazu blokovat a vyžadovat ruční akci pro operace, jako je ověřování.</span><span class="sxs-lookup"><span data-stu-id="b5837-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="b5837-118">Možnost je k dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="b5837-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="b5837-119">Klíč rozhraní API pro server</span><span class="sxs-lookup"><span data-stu-id="b5837-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="b5837-120">Nepřipojí k zdrojové adrese URL rozhraní API/v2/Package.</span><span class="sxs-lookup"><span data-stu-id="b5837-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="b5837-121">Možnost je k dispozici od verze .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="b5837-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="b5837-122">Nezobrazuje výzvu k zadání vstupu uživatele nebo potvrzení.</span><span class="sxs-lookup"><span data-stu-id="b5837-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="b5837-123">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="b5837-123">Specifies the server URL.</span></span> <span data-ttu-id="b5837-124">Podporované adresy URL pro NuGet.org `https://www.nuget.org`zahrnují `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="b5837-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="b5837-125">V případě privátních informačních kanálů nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="b5837-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="b5837-126">Příklady</span><span class="sxs-lookup"><span data-stu-id="b5837-126">Examples</span></span>

* <span data-ttu-id="b5837-127">Odstraní verzi 1,0 balíčku `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="b5837-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="b5837-128">Odstraní verzi 1,0 balíčku `Microsoft.AspNetCore.Mvc`, nezobrazuje výzvu k zadání přihlašovacích údajů uživatele nebo jiný vstup:</span><span class="sxs-lookup"><span data-stu-id="b5837-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
