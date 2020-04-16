---
title: příkaz seznam nástrojů dotnet
description: Příkaz seznamu nástrojů dotnet obsahuje seznam nástrojů .NET Core nainstalovaných v počítači.
ms.date: 02/14/2020
ms.openlocfilehash: 28f9155407d1238f8b0960b69b34ea329ca0e8e6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463351"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="c0c2c-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="c0c2c-103">dotnet tool list</span></span>

<span data-ttu-id="c0c2c-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="c0c2c-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c0c2c-105">Název</span><span class="sxs-lookup"><span data-stu-id="c0c2c-105">Name</span></span>

<span data-ttu-id="c0c2c-106">`dotnet tool list`- Zobrazí seznam všech [nástrojů .NET Core](global-tools.md) zadaného typu aktuálně nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c0c2c-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="c0c2c-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="c0c2c-108">Popis</span><span class="sxs-lookup"><span data-stu-id="c0c2c-108">Description</span></span>

<span data-ttu-id="c0c2c-109">Příkaz `dotnet tool list` umožňuje zobrazit seznam všech globálních nástrojů .NET Core, cest nástrojů nebo místních nástrojů nainstalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="c0c2c-110">Příkaz obsahuje seznam názvu balíčku, nainstalované verze a příkazu nástroje.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="c0c2c-111">Chcete-li použít příkaz, zadejte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="c0c2c-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="c0c2c-112">Globální nástroj nainstalovaný ve výchozím umístění.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-112">A global tool installed in the default location.</span></span> <span data-ttu-id="c0c2c-113">Použít `--global` možnost</span><span class="sxs-lookup"><span data-stu-id="c0c2c-113">Use the `--global` option</span></span>
* <span data-ttu-id="c0c2c-114">Globální nástroj nainstalovaný ve vlastním umístění.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="c0c2c-115">Použijte `--tool-path` tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="c0c2c-116">Místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-116">A local tool.</span></span> <span data-ttu-id="c0c2c-117">`--global` Vynechte `--tool-path` možnosti a.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="c0c2c-118">**Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="c0c2c-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="c0c2c-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c0c2c-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="c0c2c-120">Uvádí globální nástroje pro celou uživatele.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-120">Lists user-wide global tools.</span></span> <span data-ttu-id="c0c2c-121">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="c0c2c-122">Vynechání obou `--global` `--tool-path` a uvádí místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c0c2c-123">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="c0c2c-124">Určuje vlastní umístění, kde lze najít globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="c0c2c-125">CESTA může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="c0c2c-126">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="c0c2c-127">Vynechání obou `--global` `--tool-path` a uvádí místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="c0c2c-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="c0c2c-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="c0c2c-129">Zobrazí seznam všech globálních nástrojů nainstalovaných v celém uživatelském počítači v počítači (aktuální profil uživatele).</span><span class="sxs-lookup"><span data-stu-id="c0c2c-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="c0c2c-130">Zobrazí seznam globálních nástrojů z určitého adresáře systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="c0c2c-131">Uvádí globální nástroje z konkrétního adresáře Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="c0c2c-132">Zobrazí seznam všech místních nástrojů dostupných v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="c0c2c-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0c2c-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0c2c-133">See also</span></span>

- [<span data-ttu-id="c0c2c-134">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="c0c2c-134">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="c0c2c-135">Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="c0c2c-135">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="c0c2c-136">Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="c0c2c-136">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
