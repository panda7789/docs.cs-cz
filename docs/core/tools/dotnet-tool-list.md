---
title: příkaz pro seznam nástrojů dotnet
description: Příkaz pro výpis seznamu nástrojů dotnet obsahuje seznam nástrojů .NET Core, které jsou nainstalovány na vašem počítači.
ms.date: 02/14/2020
ms.openlocfilehash: 4035c5be233232e53c6d7150485f737108c1e18d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925459"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="3488b-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="3488b-103">dotnet tool list</span></span>

<span data-ttu-id="3488b-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="3488b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3488b-105">Název</span><span class="sxs-lookup"><span data-stu-id="3488b-105">Name</span></span>

<span data-ttu-id="3488b-106">`dotnet tool list`– Zobrazí seznam všech [nástrojů .NET Core](global-tools.md) zadaného typu, které jsou aktuálně nainstalované na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="3488b-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3488b-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="3488b-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="3488b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3488b-108">Description</span></span>

<span data-ttu-id="3488b-109">`dotnet tool list`Příkaz umožňuje zobrazit seznam všech nástrojů .NET Core Global, Tool-Path nebo místních nástrojů, které jsou nainstalovány na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="3488b-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="3488b-110">Příkaz vypíše název balíčku, nainstalovanou verzi a příkaz nástroje.</span><span class="sxs-lookup"><span data-stu-id="3488b-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="3488b-111">Chcete-li použít příkaz, zadejte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="3488b-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="3488b-112">Pokud chcete zobrazit seznam globálních nástrojů nainstalovaných ve výchozím umístění, použijte `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="3488b-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="3488b-113">Pokud chcete zobrazit seznam globálních nástrojů nainstalovaných ve vlastním umístění, použijte `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="3488b-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="3488b-114">Chcete-li zobrazit seznam místních nástrojů, použijte `--local` možnost nebo vynechejte `--global` `--tool-path` Možnosti, a `--local` .</span><span class="sxs-lookup"><span data-stu-id="3488b-114">To list local tools, use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="3488b-115">**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="3488b-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="3488b-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="3488b-116">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="3488b-117">Obsahuje seznam globálních nástrojů pro všechny uživatele.</span><span class="sxs-lookup"><span data-stu-id="3488b-117">Lists user-wide global tools.</span></span> <span data-ttu-id="3488b-118">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="3488b-118">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="3488b-119">Vynechání obou `--global` a `--tool-path` seznam místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="3488b-119">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="3488b-120">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="3488b-120">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="3488b-121">Zobrazí seznam místních nástrojů pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="3488b-121">Lists local tools for the current directory.</span></span> <span data-ttu-id="3488b-122">Nelze kombinovat s `--global` `--tool-path` možnostmi nebo.</span><span class="sxs-lookup"><span data-stu-id="3488b-122">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="3488b-123">Vynechání obou `--global` a `--tool-path` seznam místních nástrojů, i když není `--local` zadaný.</span><span class="sxs-lookup"><span data-stu-id="3488b-123">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="3488b-124">Určuje vlastní umístění, kde se mají najít globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="3488b-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="3488b-125">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="3488b-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="3488b-126">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="3488b-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="3488b-127">Vynechání obou `--global` a `--tool-path` seznam místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="3488b-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="3488b-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="3488b-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="3488b-129">Zobrazí seznam všech globálních nástrojů nainstalovaných v celém počítači (aktuální profil uživatele).</span><span class="sxs-lookup"><span data-stu-id="3488b-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="3488b-130">Zobrazí seznam globálních nástrojů z konkrétního adresáře Windows.</span><span class="sxs-lookup"><span data-stu-id="3488b-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="3488b-131">Zobrazí seznam globálních nástrojů z konkrétního adresáře Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="3488b-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="3488b-132">**`dotnet tool list`** ani**`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="3488b-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="3488b-133">Zobrazí seznam všech místních nástrojů dostupných v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="3488b-133">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="3488b-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="3488b-134">See also</span></span>

- [<span data-ttu-id="3488b-135">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="3488b-135">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="3488b-136">Kurz: instalace a použití globálního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="3488b-136">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="3488b-137">Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="3488b-137">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
