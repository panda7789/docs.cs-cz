---
title: příkaz - .NET Core rozhraní příkazového řádku odstranit nuget DotNet.
description: Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: a56ddaba72f8e1a76db810231e64993c657e908e
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697239"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="a7e3a-103">odstranění nuget DotNet.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a7e3a-104">Název</span><span class="sxs-lookup"><span data-stu-id="a7e3a-104">Name</span></span>

<span data-ttu-id="a7e3a-105">`dotnet nuget delete` -Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a7e3a-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="a7e3a-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a7e3a-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="a7e3a-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a7e3a-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="a7e3a-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a7e3a-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="a7e3a-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="a7e3a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a7e3a-110">Description</span></span>

<span data-ttu-id="a7e3a-111">`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-111">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="a7e3a-112">Pro [nuget.org](https://www.nuget.org/), akce se má unlist balíčku.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-112">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="a7e3a-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="a7e3a-113">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="a7e3a-114">Název nebo ID balíčku, který má odstranit.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-114">Name/ID of the package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="a7e3a-115">Verze balíčku, který má odstranit.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-115">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="a7e3a-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a7e3a-116">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="a7e3a-117">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="a7e3a-117">.NET Core 2.1</span></span>](#tab/netcore21)

`--force-english-output`

 <span data-ttu-id="a7e3a-118">Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-118">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="a7e3a-119">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-119">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="a7e3a-120">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-120">The API key for the server.</span></span>

<span data-ttu-id="a7e3a-121">` --no-service-endpoint` Není připojit "v2/api/packages" na adresu URL zdroje.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-121">` --no-service-endpoint` Doesn't append "api/v2/packages" to the source URL.</span></span>

`--non-interactive`

<span data-ttu-id="a7e3a-122">Není výzvu pro vstup uživatele nebo potvrzení.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-122">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="a7e3a-123">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-123">Specifies the server URL.</span></span> <span data-ttu-id="a7e3a-124">Podporované adresy URL pro zahrnují nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, a `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-124">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="a7e3a-125">Pro privátní informační kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="a7e3a-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="a7e3a-126">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="a7e3a-126">.NET Core 2.0</span></span>](#tab/netcore20)

`--force-english-output`

 <span data-ttu-id="a7e3a-127">Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-127">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="a7e3a-128">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-128">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="a7e3a-129">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-129">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="a7e3a-130">Není výzvu pro vstup uživatele nebo potvrzení.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-130">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="a7e3a-131">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-131">Specifies the server URL.</span></span> <span data-ttu-id="a7e3a-132">Podporované adresy URL pro zahrnují nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, a `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-132">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="a7e3a-133">Pro privátní informační kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="a7e3a-133">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a7e3a-134">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="a7e3a-134">.NET Core 1.x</span></span>](#tab/netcore1x)

`--force-english-output`

 <span data-ttu-id="a7e3a-135">Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-135">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="a7e3a-136">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-136">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="a7e3a-137">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-137">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="a7e3a-138">Není výzvu pro vstup uživatele nebo potvrzení.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-138">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="a7e3a-139">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-139">Specifies the server URL.</span></span> <span data-ttu-id="a7e3a-140">Podporované adresy URL pro zahrnují nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, a `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-140">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="a7e3a-141">Pro privátní informační kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="a7e3a-141">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="a7e3a-142">Příklady</span><span class="sxs-lookup"><span data-stu-id="a7e3a-142">Examples</span></span>

<span data-ttu-id="a7e3a-143">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="a7e3a-143">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

<span data-ttu-id="a7e3a-144">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, není výzvy uživatele pro přihlašovací údaje nebo jiné vstupní:</span><span class="sxs-lookup"><span data-stu-id="a7e3a-144">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`