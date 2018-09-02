---
title: DotNet odinstalační příkaz – rozhraní příkazového řádku .NET Core
description: Příkaz odinstalovat nástroj dotnet odinstaluje zadané globální nástroji .NET Core z vašeho počítače.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 93a43e19df4c7f220ac1e2d2db397cba4d791e83
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389835"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="2ced7-103">Odinstalace nástrojů DotNet</span><span class="sxs-lookup"><span data-stu-id="2ced7-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="2ced7-104">Název</span><span class="sxs-lookup"><span data-stu-id="2ced7-104">Name</span></span>

<span data-ttu-id="2ced7-105">`dotnet tool uninstall` -Odinstaluje zadané [globální nástroje .NET Core](global-tools.md) z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="2ced7-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2ced7-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="2ced7-106">Synopsis</span></span>

```console
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="2ced7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2ced7-107">Description</span></span>

<span data-ttu-id="2ced7-108">`dotnet tool uninstall` Příkaz poskytuje způsob, jak vás k odinstalaci globální nástroje .NET Core z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="2ced7-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="2ced7-109">Použití příkazu, buď musíte zadat, že chcete odebrat uživatele celou nástroj pomocí `--global` možnost nebo zadejte cestu k umístění, kde je nástroj nainstalován pomocí `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="2ced7-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="2ced7-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="2ced7-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="2ced7-111">Název nebo ID balíčku NuGet, který obsahuje globální nástroji .NET Core pro odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="2ced7-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="2ced7-112">Můžete najít pomocí názvu balíčku [seznam nástrojů dotnet](dotnet-tool-list.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="2ced7-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="2ced7-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="2ced7-113">Options</span></span>

`-g|--global`

<span data-ttu-id="2ced7-114">Určuje, že nástroj má být odebrán z instalace na úrovni uživatele.</span><span class="sxs-lookup"><span data-stu-id="2ced7-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="2ced7-115">Nelze kombinovat s `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="2ced7-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="2ced7-116">Pokud nezadáte tuto možnost, je nutné zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="2ced7-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="2ced7-117">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="2ced7-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="2ced7-118">Určuje umístění, kam chcete-li odinstalovat nástroj globální.</span><span class="sxs-lookup"><span data-stu-id="2ced7-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="2ced7-119">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="2ced7-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="2ced7-120">Nelze kombinovat s `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="2ced7-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="2ced7-121">Pokud nezadáte tuto možnost, je nutné zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="2ced7-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="2ced7-122">Příklady</span><span class="sxs-lookup"><span data-stu-id="2ced7-122">Examples</span></span>

<span data-ttu-id="2ced7-123">Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="2ced7-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="2ced7-124">Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj z konkrétní složky Windows:</span><span class="sxs-lookup"><span data-stu-id="2ced7-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="2ced7-125">Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj z konkrétní složky Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="2ced7-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="2ced7-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ced7-126">See also</span></span>

* [<span data-ttu-id="2ced7-127">Globální nástroje .NET core</span><span class="sxs-lookup"><span data-stu-id="2ced7-127">.NET Core Global Tools</span></span>](global-tools.md)