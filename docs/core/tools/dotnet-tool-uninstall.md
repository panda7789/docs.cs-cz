---
title: příkaz - .NET Core rozhraní příkazového řádku odinstalovat nástroj DotNet.
description: Příkaz odinstalovat nástroj dotnet odinstaluje zadaný nástroj globální základní .NET z vašeho počítače.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5cf80d1756dbf4e88bb52a8028d186d44978f440
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696935"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="38555-103">Odinstalace nástroje pro DotNet.</span><span class="sxs-lookup"><span data-stu-id="38555-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="38555-104">Název</span><span class="sxs-lookup"><span data-stu-id="38555-104">Name</span></span>

<span data-ttu-id="38555-105">`dotnet tool uninstall` -Odinstaluje zadaný [.NET Core globální nástroj](global-tools.md) z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="38555-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="38555-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="38555-106">Synopsis</span></span>

```
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="38555-107">Popis</span><span class="sxs-lookup"><span data-stu-id="38555-107">Description</span></span>

<span data-ttu-id="38555-108">`dotnet tool uninstall` Příkaz nabízí způsob, jak můžete odinstalovat .NET Core globální nástroje z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="38555-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="38555-109">Použití příkazu, buď musíte zadat, že chcete odebrat uživatele celou nástroj pomocí `--global` možnost nebo zadejte cestu k umístění, kde je nástroj nainstalován pomocí `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="38555-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="38555-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="38555-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="38555-111">Název nebo ID balíčku NuGet, který obsahuje rozhraní .NET Core globální nástroj pro odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="38555-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="38555-112">Můžete najít pomocí názvu balíčku [seznam nástrojů dotnet](dotnet-tool-list.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="38555-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="38555-113">Možnosti</span><span class="sxs-lookup"><span data-stu-id="38555-113">Options</span></span>

`-g|--global`

<span data-ttu-id="38555-114">Určuje, že nástroj odeberou se z instalace úrovni uživatele.</span><span class="sxs-lookup"><span data-stu-id="38555-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="38555-115">Nelze kombinovat s `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="38555-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="38555-116">Pokud nezadáte tuto možnost, musíte zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="38555-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="38555-117">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="38555-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="38555-118">Určuje umístění, kde chcete-li odinstalovat nástroj globální.</span><span class="sxs-lookup"><span data-stu-id="38555-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="38555-119">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="38555-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="38555-120">Nelze kombinovat s `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="38555-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="38555-121">Pokud nezadáte tuto možnost, musíte zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="38555-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="38555-122">Příklady</span><span class="sxs-lookup"><span data-stu-id="38555-122">Examples</span></span>

<span data-ttu-id="38555-123">Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="38555-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="38555-124">Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj z určité složky systému Windows:</span><span class="sxs-lookup"><span data-stu-id="38555-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="38555-125">Odinstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj z určité složky systému Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="38555-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="38555-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38555-126">See also</span></span>

[<span data-ttu-id="38555-127">.NET core globální nástroje</span><span class="sxs-lookup"><span data-stu-id="38555-127">.NET Core Global Tools</span></span>](global-tools.md)