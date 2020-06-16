---
title: příkaz pro seznam nástrojů dotnet
description: Příkaz pro výpis seznamu nástrojů dotnet obsahuje seznam nástrojů .NET Core, které jsou nainstalovány na vašem počítači.
ms.date: 02/14/2020
ms.openlocfilehash: 7ca894ab0f5daf0118ff92fb39e0118b952b3d83
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768271"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="a7dee-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="a7dee-103">dotnet tool list</span></span>

<span data-ttu-id="a7dee-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="a7dee-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a7dee-105">Name</span><span class="sxs-lookup"><span data-stu-id="a7dee-105">Name</span></span>

<span data-ttu-id="a7dee-106">`dotnet tool list`– Zobrazí seznam všech [nástrojů .NET Core](global-tools.md) zadaného typu, které jsou aktuálně nainstalované na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="a7dee-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a7dee-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="a7dee-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="a7dee-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a7dee-108">Description</span></span>

<span data-ttu-id="a7dee-109">`dotnet tool list`Příkaz umožňuje zobrazit seznam všech nástrojů .NET Core Global, Tool-Path nebo místních nástrojů, které jsou nainstalovány na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="a7dee-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="a7dee-110">Příkaz vypíše název balíčku, nainstalovanou verzi a příkaz nástroje.</span><span class="sxs-lookup"><span data-stu-id="a7dee-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="a7dee-111">Chcete-li použít příkaz, zadejte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="a7dee-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="a7dee-112">Pokud chcete zobrazit seznam globálních nástrojů nainstalovaných ve výchozím umístění, použijte `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="a7dee-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="a7dee-113">Pokud chcete zobrazit seznam globálních nástrojů nainstalovaných ve vlastním umístění, použijte `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="a7dee-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="a7dee-114">Chcete-li zobrazit seznam místních nástrojů, místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="a7dee-114">To list local tools, A local tool.</span></span> <span data-ttu-id="a7dee-115">použijte `--local` možnost nebo vynechejte `--global` Možnosti, `--tool-path` a `--local` .</span><span class="sxs-lookup"><span data-stu-id="a7dee-115">use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="a7dee-116">**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="a7dee-116">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="a7dee-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a7dee-117">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="a7dee-118">Obsahuje seznam globálních nástrojů pro všechny uživatele.</span><span class="sxs-lookup"><span data-stu-id="a7dee-118">Lists user-wide global tools.</span></span> <span data-ttu-id="a7dee-119">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="a7dee-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="a7dee-120">Vynechání obou `--global` a `--tool-path` seznam místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="a7dee-120">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a7dee-121">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="a7dee-121">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="a7dee-122">Zobrazí seznam místních nástrojů pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="a7dee-122">Lists local tools for the current directory.</span></span> <span data-ttu-id="a7dee-123">Nelze kombinovat s `--global` `--tool-path` možnostmi nebo.</span><span class="sxs-lookup"><span data-stu-id="a7dee-123">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="a7dee-124">Vynechání obou `--global` a `--tool-path` seznam místních nástrojů, i když není `--local` zadaný.</span><span class="sxs-lookup"><span data-stu-id="a7dee-124">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="a7dee-125">Určuje vlastní umístění, kde se mají najít globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="a7dee-125">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="a7dee-126">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="a7dee-126">PATH can be absolute or relative.</span></span> <span data-ttu-id="a7dee-127">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="a7dee-127">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="a7dee-128">Vynechání obou `--global` a `--tool-path` seznam místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="a7dee-128">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="a7dee-129">Příklady</span><span class="sxs-lookup"><span data-stu-id="a7dee-129">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="a7dee-130">Zobrazí seznam všech globálních nástrojů nainstalovaných v celém počítači (aktuální profil uživatele).</span><span class="sxs-lookup"><span data-stu-id="a7dee-130">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="a7dee-131">Zobrazí seznam globálních nástrojů z konkrétního adresáře Windows.</span><span class="sxs-lookup"><span data-stu-id="a7dee-131">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="a7dee-132">Zobrazí seznam globálních nástrojů z konkrétního adresáře Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="a7dee-132">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="a7dee-133">**`dotnet tool list`** ani**`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="a7dee-133">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="a7dee-134">Zobrazí seznam všech místních nástrojů dostupných v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="a7dee-134">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7dee-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7dee-135">See also</span></span>

- [<span data-ttu-id="a7dee-136">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="a7dee-136">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="a7dee-137">Kurz: instalace a použití globálního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a7dee-137">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="a7dee-138">Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a7dee-138">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
