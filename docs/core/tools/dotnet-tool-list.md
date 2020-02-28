---
title: příkaz pro seznam nástrojů dotnet
description: Příkaz pro výpis seznamu nástrojů dotnet obsahuje seznam nástrojů .NET Core, které jsou nainstalovány na vašem počítači.
ms.date: 02/14/2020
ms.openlocfilehash: f231dcfe64a925f75f948d508e7a2d83befd9a00
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156982"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="dd5e9-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="dd5e9-103">dotnet tool list</span></span>

<span data-ttu-id="dd5e9-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="dd5e9-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="dd5e9-105">Název</span><span class="sxs-lookup"><span data-stu-id="dd5e9-105">Name</span></span>

<span data-ttu-id="dd5e9-106">`dotnet tool list` – zobrazí seznam všech [nástrojů .NET Core](global-tools.md) zadaného typu, které jsou aktuálně nainstalované na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dd5e9-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="dd5e9-107">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="dd5e9-108">Popis</span><span class="sxs-lookup"><span data-stu-id="dd5e9-108">Description</span></span>

<span data-ttu-id="dd5e9-109">Příkaz `dotnet tool list` slouží jako způsob zobrazení seznamu všech nástrojů .NET Core Global, nástroje-Path nebo místních nástrojů, které jsou nainstalovány na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="dd5e9-110">Příkaz vypíše název balíčku, nainstalovanou verzi a příkaz nástroje.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="dd5e9-111">Chcete-li použít příkaz, zadejte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="dd5e9-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="dd5e9-112">Globální nástroj nainstalovaný ve výchozím umístění.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-112">A global tool installed in the default location.</span></span> <span data-ttu-id="dd5e9-113">Použití možnosti `--global`</span><span class="sxs-lookup"><span data-stu-id="dd5e9-113">Use the `--global` option</span></span>
* <span data-ttu-id="dd5e9-114">Globální nástroj nainstalovaný ve vlastním umístění.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="dd5e9-115">Použijte možnost `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="dd5e9-116">Místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-116">A local tool.</span></span> <span data-ttu-id="dd5e9-117">Vynechejte možnosti `--global` a `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="dd5e9-118">**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="dd5e9-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="dd5e9-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="dd5e9-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="dd5e9-120">Obsahuje seznam globálních nástrojů pro všechny uživatele.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-120">Lists user-wide global tools.</span></span> <span data-ttu-id="dd5e9-121">Nelze kombinovat s možností `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="dd5e9-122">Vynechání `--global` a `--tool-path` seznam místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="dd5e9-123">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="dd5e9-124">Určuje vlastní umístění, kde se mají najít globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="dd5e9-125">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="dd5e9-126">Nelze kombinovat s možností `--global`.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="dd5e9-127">Vynechání `--global` a `--tool-path` seznam místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="dd5e9-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="dd5e9-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="dd5e9-129">Zobrazí seznam všech globálních nástrojů nainstalovaných v celém počítači (aktuální profil uživatele).</span><span class="sxs-lookup"><span data-stu-id="dd5e9-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="dd5e9-130">Zobrazí seznam globálních nástrojů z konkrétního adresáře Windows.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="dd5e9-131">Zobrazí seznam globálních nástrojů z konkrétního adresáře Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="dd5e9-132">Zobrazí seznam všech místních nástrojů dostupných v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="dd5e9-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd5e9-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd5e9-133">See also</span></span>

- [<span data-ttu-id="dd5e9-134">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="dd5e9-134">.NET Core tools</span></span>](global-tools.md)
