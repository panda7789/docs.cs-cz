---
title: příkaz DotNet nuget delete
description: Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: a657fa273ca6b5229a1713fbcaf003217a59fd7f
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612625"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="8c3ca-103">DotNet nuget delete</span><span class="sxs-lookup"><span data-stu-id="8c3ca-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8c3ca-104">Name</span><span class="sxs-lookup"><span data-stu-id="8c3ca-104">Name</span></span>

<span data-ttu-id="8c3ca-105">`dotnet nuget delete` -Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8c3ca-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="8c3ca-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8c3ca-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8c3ca-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8c3ca-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8c3ca-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="8c3ca-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8c3ca-109">Description</span></span>

<span data-ttu-id="8c3ca-110">`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-110">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="8c3ca-111">Pro [nuget.org](https://www.nuget.org/), "action" je k vyjmutí ze seznamu balíčku.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-111">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="8c3ca-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="8c3ca-112">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="8c3ca-113">Název nebo ID balíčku, který se odstranit.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-113">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="8c3ca-114">Verze balíčku, který se odstranit.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-114">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="8c3ca-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8c3ca-115">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8c3ca-116">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8c3ca-116">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`--force-english-output`**

  <span data-ttu-id="8c3ca-117">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="8c3ca-118">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="8c3ca-119">Umožňuje příkazu blokování a vyžaduje ruční akci pro operace, jako je například ověřování.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="8c3ca-120">Možnost dostupné od verze sady SDK 2.2 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="8c3ca-121">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-121">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="8c3ca-122">"Api/v2/balíček" nemá připojení k zdrojová adresa URL.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-122">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="8c3ca-123">Možnost dostupné od verze sady SDK .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-123">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="8c3ca-124">Není výzvu k zadání uživatele o vstup ani potvrzení.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-124">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="8c3ca-125">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-125">Specifies the server URL.</span></span> <span data-ttu-id="8c3ca-126">Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-126">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="8c3ca-127">Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="8c3ca-127">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8c3ca-128">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8c3ca-128">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`--force-english-output`**

  <span data-ttu-id="8c3ca-129">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-129">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="8c3ca-130">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-130">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="8c3ca-131">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-131">The API key for the server.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="8c3ca-132">Není výzvu k zadání uživatele o vstup ani potvrzení.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-132">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="8c3ca-133">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-133">Specifies the server URL.</span></span> <span data-ttu-id="8c3ca-134">Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="8c3ca-134">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="8c3ca-135">Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="8c3ca-135">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="8c3ca-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="8c3ca-136">Examples</span></span>

* <span data-ttu-id="8c3ca-137">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="8c3ca-137">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="8c3ca-138">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, ne výzvou pro uživatele pro přihlašovací údaje nebo druhý vstup:</span><span class="sxs-lookup"><span data-stu-id="8c3ca-138">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```