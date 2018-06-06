---
title: příkaz seznamu DotNet nástroj - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet nástroj seznam uvádí zadaný .NET Core globální nástroj z vašeho počítače.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5f4793cd37c3a8df06eb6930ad9f381ac70d4e67
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696722"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="48d31-103">seznam nástrojů DotNet.</span><span class="sxs-lookup"><span data-stu-id="48d31-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="48d31-104">Název</span><span class="sxs-lookup"><span data-stu-id="48d31-104">Name</span></span>

<span data-ttu-id="48d31-105">`dotnet tool list` -Obsahuje seznam všech [.NET Core globální nástroje](global-tools.md) nainstalovány v výchozí adresář na počítači nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="48d31-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="48d31-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="48d31-106">Synopsis</span></span>

```
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="48d31-107">Popis</span><span class="sxs-lookup"><span data-stu-id="48d31-107">Description</span></span>

<span data-ttu-id="48d31-108">`dotnet tool list` Příkaz nabízí způsob, jak lze uvést všechny .NET Core globální nástroje nainstalovat celou uživatele na váš počítač (aktuální profil uživatele) nebo v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="48d31-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="48d31-109">Příkaz uvádí název balíčku, verzi a příkaz globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="48d31-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="48d31-110">Použití příkazu seznamu, můžete mít buď k určení, zda chcete zobrazit všechny nástroje celou uživatele pomocí `--global` možnost nebo zadejte vlastní cesta pomocí `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="48d31-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="48d31-111">Možnosti</span><span class="sxs-lookup"><span data-stu-id="48d31-111">Options</span></span>

`-g|--global`

<span data-ttu-id="48d31-112">Obsahuje seznam nástrojů globální úrovni uživatele.</span><span class="sxs-lookup"><span data-stu-id="48d31-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="48d31-113">Nelze kombinovat s `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="48d31-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="48d31-114">Pokud nezadáte tuto možnost, musíte zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="48d31-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="48d31-115">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="48d31-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="48d31-116">Určuje do vlastního umístění, kde najít nástroje na globální.</span><span class="sxs-lookup"><span data-stu-id="48d31-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="48d31-117">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="48d31-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="48d31-118">Nelze kombinovat s `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="48d31-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="48d31-119">Pokud nezadáte tuto možnost, musíte zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="48d31-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="48d31-120">Příklady</span><span class="sxs-lookup"><span data-stu-id="48d31-120">Examples</span></span>

<span data-ttu-id="48d31-121">Obsahuje všechny globální nástroje nainstalované uživatele celou na počítači (aktuální profil uživatele):</span><span class="sxs-lookup"><span data-stu-id="48d31-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="48d31-122">Obsahuje seznam nástrojů globální z určité složky systému Windows:</span><span class="sxs-lookup"><span data-stu-id="48d31-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="48d31-123">Obsahuje seznam nástrojů globální z určité složky systému Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="48d31-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="48d31-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48d31-124">See also</span></span>

[<span data-ttu-id="48d31-125">.NET core globální nástroje</span><span class="sxs-lookup"><span data-stu-id="48d31-125">.NET Core Global Tools</span></span>](global-tools.md)