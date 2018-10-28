---
title: příkaz – rozhraní příkazového řádku .NET Core DotNet nuget delete
description: Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: f4aa027a465c4adea1de13853063d03e8e295411
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180874"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="0d9f7-103">DotNet nuget delete</span><span class="sxs-lookup"><span data-stu-id="0d9f7-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0d9f7-104">Název</span><span class="sxs-lookup"><span data-stu-id="0d9f7-104">Name</span></span>

<span data-ttu-id="0d9f7-105">`dotnet nuget delete` -Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0d9f7-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="0d9f7-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0d9f7-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0d9f7-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0d9f7-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0d9f7-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0d9f7-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0d9f7-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="0d9f7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0d9f7-110">Description</span></span>

<span data-ttu-id="0d9f7-111">`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-111">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="0d9f7-112">Pro [nuget.org](https://www.nuget.org/), "action" je k vyjmutí ze seznamu balíčku.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-112">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="0d9f7-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="0d9f7-113">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="0d9f7-114">Název nebo ID balíčku, který se odstranit.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-114">Name/ID of the package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="0d9f7-115">Verze balíčku, který se odstranit.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-115">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="0d9f7-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0d9f7-116">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="0d9f7-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="0d9f7-117">.NET Core 2.1</span></span>](#tab/netcore21)

`--force-english-output`

 <span data-ttu-id="0d9f7-118">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-118">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="0d9f7-119">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-119">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0d9f7-120">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-120">The API key for the server.</span></span>

<span data-ttu-id="0d9f7-121">`--no-service-endpoint` "Api/v2/balíček" nemá připojení k zdrojová adresa URL.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-121">`--no-service-endpoint` Doesn't append "api/v2/package" to the source URL.</span></span>

`--non-interactive`

<span data-ttu-id="0d9f7-122">Není výzvu k zadání uživatele o vstup ani potvrzení.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-122">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0d9f7-123">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-123">Specifies the server URL.</span></span> <span data-ttu-id="0d9f7-124">Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0d9f7-125">Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0d9f7-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="0d9f7-126">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="0d9f7-126">.NET Core 2.0</span></span>](#tab/netcore20)

`--force-english-output`

 <span data-ttu-id="0d9f7-127">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-127">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="0d9f7-128">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-128">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0d9f7-129">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-129">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="0d9f7-130">Není výzvu k zadání uživatele o vstup ani potvrzení.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-130">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0d9f7-131">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-131">Specifies the server URL.</span></span> <span data-ttu-id="0d9f7-132">Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-132">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0d9f7-133">Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0d9f7-133">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0d9f7-134">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="0d9f7-134">.NET Core 1.x</span></span>](#tab/netcore1x)

`--force-english-output`

 <span data-ttu-id="0d9f7-135">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-135">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="0d9f7-136">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-136">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="0d9f7-137">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-137">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="0d9f7-138">Není výzvu k zadání uživatele o vstup ani potvrzení.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-138">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0d9f7-139">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-139">Specifies the server URL.</span></span> <span data-ttu-id="0d9f7-140">Nepodporuje adresy URL pro zahrnutí nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, a `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="0d9f7-140">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="0d9f7-141">Pro privátní kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="0d9f7-141">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="0d9f7-142">Příklady</span><span class="sxs-lookup"><span data-stu-id="0d9f7-142">Examples</span></span>

<span data-ttu-id="0d9f7-143">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="0d9f7-143">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

<span data-ttu-id="0d9f7-144">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, ne výzvou pro uživatele pro přihlašovací údaje nebo druhý vstup:</span><span class="sxs-lookup"><span data-stu-id="0d9f7-144">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
