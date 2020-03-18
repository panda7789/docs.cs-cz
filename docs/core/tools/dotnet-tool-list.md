---
title: příkaz seznam nástrojů dotnet
description: Příkaz seznamu nástrojů dotnet obsahuje seznam nástrojů .NET Core nainstalovaných v počítači.
ms.date: 02/14/2020
ms.openlocfilehash: def3c345a775e5a65ec3d37718d207c80ca7ceee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847869"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="afa5a-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="afa5a-103">dotnet tool list</span></span>

<span data-ttu-id="afa5a-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="afa5a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="afa5a-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="afa5a-105">Name</span></span>

<span data-ttu-id="afa5a-106">`dotnet tool list`- Zobrazí seznam všech [nástrojů .NET Core](global-tools.md) zadaného typu aktuálně nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="afa5a-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="afa5a-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="afa5a-107">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>

dotnet tool list <--tool-path>

dotnet tool list

dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="afa5a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="afa5a-108">Description</span></span>

<span data-ttu-id="afa5a-109">Příkaz `dotnet tool list` umožňuje zobrazit seznam všech globálních nástrojů .NET Core, cest nástrojů nebo místních nástrojů nainstalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="afa5a-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="afa5a-110">Příkaz obsahuje seznam názvu balíčku, nainstalované verze a příkazu nástroje.</span><span class="sxs-lookup"><span data-stu-id="afa5a-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="afa5a-111">Chcete-li použít příkaz, zadejte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="afa5a-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="afa5a-112">Globální nástroj nainstalovaný ve výchozím umístění.</span><span class="sxs-lookup"><span data-stu-id="afa5a-112">A global tool installed in the default location.</span></span> <span data-ttu-id="afa5a-113">Použít `--global` možnost</span><span class="sxs-lookup"><span data-stu-id="afa5a-113">Use the `--global` option</span></span>
* <span data-ttu-id="afa5a-114">Globální nástroj nainstalovaný ve vlastním umístění.</span><span class="sxs-lookup"><span data-stu-id="afa5a-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="afa5a-115">Použijte `--tool-path` tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="afa5a-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="afa5a-116">Místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="afa5a-116">A local tool.</span></span> <span data-ttu-id="afa5a-117">`--global` Vynechte `--tool-path` možnosti a.</span><span class="sxs-lookup"><span data-stu-id="afa5a-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="afa5a-118">**Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="afa5a-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="afa5a-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="afa5a-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="afa5a-120">Uvádí globální nástroje pro celou uživatele.</span><span class="sxs-lookup"><span data-stu-id="afa5a-120">Lists user-wide global tools.</span></span> <span data-ttu-id="afa5a-121">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="afa5a-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="afa5a-122">Vynechání obou `--global` `--tool-path` a uvádí místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="afa5a-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="afa5a-123">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="afa5a-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="afa5a-124">Určuje vlastní umístění, kde lze najít globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="afa5a-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="afa5a-125">CESTA může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="afa5a-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="afa5a-126">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="afa5a-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="afa5a-127">Vynechání obou `--global` `--tool-path` a uvádí místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="afa5a-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="afa5a-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="afa5a-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="afa5a-129">Zobrazí seznam všech globálních nástrojů nainstalovaných v celém uživatelském počítači v počítači (aktuální profil uživatele).</span><span class="sxs-lookup"><span data-stu-id="afa5a-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="afa5a-130">Zobrazí seznam globálních nástrojů z určitého adresáře systému Windows.</span><span class="sxs-lookup"><span data-stu-id="afa5a-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="afa5a-131">Uvádí globální nástroje z konkrétního adresáře Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="afa5a-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="afa5a-132">Zobrazí seznam všech místních nástrojů dostupných v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="afa5a-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="afa5a-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="afa5a-133">See also</span></span>

- [<span data-ttu-id="afa5a-134">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="afa5a-134">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="afa5a-135">Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="afa5a-135">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="afa5a-136">Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="afa5a-136">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
