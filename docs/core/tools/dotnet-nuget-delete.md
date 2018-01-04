---
title: "příkaz - .NET Core rozhraní příkazového řádku odstranit nuget DotNet."
description: "Příkaz dotnet-nuget-delete Odstraní nebo unlists balíčku ze serveru."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 3c09556fe90a5c447b181bc1ac5b36f014399e4f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="51712-103">odstranění nuget DotNet.</span><span class="sxs-lookup"><span data-stu-id="51712-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="51712-104">Název</span><span class="sxs-lookup"><span data-stu-id="51712-104">Name</span></span>

<span data-ttu-id="51712-105">`dotnet nuget delete`-Odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="51712-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="51712-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="51712-106">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="51712-107">Popis</span><span class="sxs-lookup"><span data-stu-id="51712-107">Description</span></span>

<span data-ttu-id="51712-108">`dotnet nuget delete` Příkaz odstraní nebo unlists balíčku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="51712-108">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="51712-109">Pro [nuget.org](https://www.nuget.org/), akce se má unlist balíčku.</span><span class="sxs-lookup"><span data-stu-id="51712-109">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="51712-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="51712-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="51712-111">Balíček odstranit.</span><span class="sxs-lookup"><span data-stu-id="51712-111">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="51712-112">Verze balíčku, který má odstranit.</span><span class="sxs-lookup"><span data-stu-id="51712-112">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="51712-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="51712-113">Options</span></span>

`-h|--help`

<span data-ttu-id="51712-114">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="51712-114">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="51712-115">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="51712-115">Specifies the server URL.</span></span> <span data-ttu-id="51712-116">Podporované adresy URL pro zahrnují nuget.org `http://www.nuget.org`, `http://www.nuget.org/api/v3`, a `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="51712-116">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="51712-117">Pro privátní informační kanály, nahraďte název hostitele (například `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="51712-117">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="51712-118">Není výzvu pro vstup uživatele nebo potvrzení.</span><span class="sxs-lookup"><span data-stu-id="51712-118">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="51712-119">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="51712-119">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="51712-120">Vynutí příkazového řádku výstup v angličtině.</span><span class="sxs-lookup"><span data-stu-id="51712-120">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="51712-121">Příklady</span><span class="sxs-lookup"><span data-stu-id="51712-121">Examples</span></span>

<span data-ttu-id="51712-122">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="51712-122">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="51712-123">Odstraní verze 1.0 balíčku `Microsoft.AspNetCore.Mvc`, není výzvy uživatele pro přihlašovací údaje nebo jiné vstupní:</span><span class="sxs-lookup"><span data-stu-id="51712-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`