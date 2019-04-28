---
title: příkaz DotNet nuget delete
description: Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: a657fa273ca6b5229a1713fbcaf003217a59fd7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648671"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="0e809-103">DotNet nuget delete</span><span class="sxs-lookup"><span data-stu-id="0e809-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0e809-104">Název</span><span class="sxs-lookup"><span data-stu-id="0e809-104">Name</span></span>

<span data-ttu-id="0e809-105">`dotnet nuget delete` -Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="0e809-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0e809-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="0e809-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0e809-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0e809-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0e809-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0e809-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="0e809-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0e809-109">Description</span></span>

<span data-ttu-id="0e809-110">`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="0e809-110">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="0e809-111">Pro [nuget.org](https://www.nuget.org/), "action" je k vyjmutí ze seznamu balíčku.</span><span class="sxs-lookup"><span data-stu-id="0e809-111">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="0e809-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="0e809-112">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="0e809-113">Název nebo ID balíčku, který se odstranit.</span><span class="sxs-lookup"><span data-stu-id="0e809-113">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="0e809-114">Verze balíčku, který se odstranit.</span><span class="sxs-lookup"><span data-stu-id="0e809-114">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="0e809-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0e809-115">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0e809-116">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0e809-116">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`--force-english-output`**

  <span data-ttu-id="0e809-117">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="0e809-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="0e809-118">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0e809-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="0e809-119">Umožňuje příkazu blokování a vyžaduje ruční akci pro operace, jako je například ověřování.</span><span class="sxs-lookup"><span data-stu-id="0e809-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="0e809-120">Možnost dostupné od verze sady SDK 2.2 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0e809-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="0e809-121">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="0e809-121">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="0e809-122">"Api/v2/balíček" nemá připojení k zdrojová adresa URL.</span><span class="sxs-lookup"><span data-stu-id="0e809-122">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="0e809-123">Možnost dostupné od verze sady SDK .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="0e809-123">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="0e809-124">Není výzvu k zadání uživatele o vstup ani potvrzení.</span><span class="sxs-lookup"><span data-stu-id="0e809-124">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="0e809-125">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="0e809-125">Specifies the server URL.</span></span> <span data-ttu-id="0e809-126">Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0e809-126">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0e809-127">Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0e809-127">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0e809-128">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0e809-128">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`--force-english-output`**

  <span data-ttu-id="0e809-129">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="0e809-129">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="0e809-130">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0e809-130">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="0e809-131">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="0e809-131">The API key for the server.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="0e809-132">Není výzvu k zadání uživatele o vstup ani potvrzení.</span><span class="sxs-lookup"><span data-stu-id="0e809-132">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="0e809-133">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="0e809-133">Specifies the server URL.</span></span> <span data-ttu-id="0e809-134">Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0e809-134">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0e809-135">Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0e809-135">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="0e809-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="0e809-136">Examples</span></span>

* <span data-ttu-id="0e809-137">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="0e809-137">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="0e809-138">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, ne výzvou pro uživatele pro přihlašovací údaje nebo druhý vstup:</span><span class="sxs-lookup"><span data-stu-id="0e809-138">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```