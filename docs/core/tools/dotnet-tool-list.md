---
title: příkaz pro seznam nástrojů dotnet
description: Příkaz pro výpis seznamu nástrojů dotnet obsahuje seznam zadaného globálního nástroje .NET Core z počítače.
ms.date: 05/29/2018
ms.openlocfilehash: 6d35b1dce0c6d57edb0c6dd5f9711f093bc804aa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117561"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="b3f1c-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="b3f1c-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="b3f1c-104">Name</span><span class="sxs-lookup"><span data-stu-id="b3f1c-104">Name</span></span>

<span data-ttu-id="b3f1c-105">`dotnet tool list`– Zobrazí seznam všech [globálních nástrojů .NET Core](global-tools.md) , které jsou aktuálně nainstalované ve výchozím adresáři na vašem počítači nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b3f1c-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="b3f1c-106">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="b3f1c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b3f1c-107">Description</span></span>

<span data-ttu-id="b3f1c-108">`dotnet tool list` Příkaz umožňuje zobrazit seznam všech globálních nástrojů .NET Core nainstalovaných na vašem počítači (aktuální profil uživatele) nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="b3f1c-109">Příkaz vypíše název balíčku, nainstalovanou verzi a příkaz globálních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="b3f1c-110">Chcete-li použít příkaz list, je nutné určit, že chcete zobrazit všechny nástroje pro celý uživatel pomocí `--global` možnosti nebo zadat vlastní cestu `--tool-path` pomocí možnosti.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="b3f1c-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b3f1c-111">Options</span></span>

`-g|--global`

<span data-ttu-id="b3f1c-112">Obsahuje seznam globálních nástrojů pro všechny uživatele.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="b3f1c-113">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="b3f1c-114">Pokud tuto možnost nezadáte, musíte zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="b3f1c-115">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="b3f1c-116">Určuje vlastní umístění, kde se mají najít globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="b3f1c-117">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="b3f1c-118">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="b3f1c-119">Pokud tuto možnost nezadáte, musíte zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="b3f1c-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="b3f1c-120">Příklady</span><span class="sxs-lookup"><span data-stu-id="b3f1c-120">Examples</span></span>

<span data-ttu-id="b3f1c-121">Zobrazí seznam všech globálních nástrojů nainstalovaných v celém počítači (aktuální profil uživatele):</span><span class="sxs-lookup"><span data-stu-id="b3f1c-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="b3f1c-122">Zobrazí seznam globálních nástrojů z konkrétní složky systému Windows:</span><span class="sxs-lookup"><span data-stu-id="b3f1c-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="b3f1c-123">Zobrazí seznam globálních nástrojů z konkrétní složky Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="b3f1c-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="b3f1c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3f1c-124">See also</span></span>

- [<span data-ttu-id="b3f1c-125">Globální nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="b3f1c-125">.NET Core Global Tools</span></span>](global-tools.md)
