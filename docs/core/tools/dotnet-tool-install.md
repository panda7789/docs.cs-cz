---
title: příkaz - .NET Core rozhraní příkazového řádku instalovat nástroj DotNet.
description: Nástroj dotnet. Nainstalujte příkaz nainstaluje zadaný rozhraní .NET Core globální nástroj na váš počítač.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f3068848910d6672a10ecfb639bac8e18a72818d
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697284"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="77c1b-103">Instalace nástroje pro DotNet.</span><span class="sxs-lookup"><span data-stu-id="77c1b-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="77c1b-104">Název</span><span class="sxs-lookup"><span data-stu-id="77c1b-104">Name</span></span>

<span data-ttu-id="77c1b-105">`dotnet tool install` -Nainstaluje zadaný [.NET Core globální nástroj](global-tools.md) na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="77c1b-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="77c1b-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="77c1b-106">Synopsis</span></span>

```
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="77c1b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="77c1b-107">Description</span></span>

<span data-ttu-id="77c1b-108">`dotnet tool install` Příkaz nabízí způsob, jak k instalaci .NET Core globální nástroje na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="77c1b-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="77c1b-109">Použití příkazu, buď musíte zadat, že chcete uživatele celou instalace pomocí `--global` možnost nebo zadejte cestu k instalaci pomocí `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="77c1b-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="77c1b-110">Globální nástroje jsou nainstalovány v následujících adresářích ve výchozím nastavení, když zadáte `-g` (nebo `--global`) možnost:</span><span class="sxs-lookup"><span data-stu-id="77c1b-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="77c1b-111">OPERAČNÍ SYSTÉM</span><span class="sxs-lookup"><span data-stu-id="77c1b-111">OS</span></span>          | <span data-ttu-id="77c1b-112">Cesta</span><span class="sxs-lookup"><span data-stu-id="77c1b-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="77c1b-113">Linux/systému macOS</span><span class="sxs-lookup"><span data-stu-id="77c1b-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="77c1b-114">Windows</span><span class="sxs-lookup"><span data-stu-id="77c1b-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="77c1b-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="77c1b-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="77c1b-116">Název nebo ID balíčku NuGet, který obsahuje rozhraní .NET Core globální nástroj pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="77c1b-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="77c1b-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="77c1b-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="77c1b-118">Přidá další zdroj balíčku NuGet chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="77c1b-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="77c1b-119">Konfigurace NuGet (*nuget.config*) souboru k použití.</span><span class="sxs-lookup"><span data-stu-id="77c1b-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="77c1b-120">Určuje, [cílové rozhraní](../../standard/frameworks.md) k instalaci nástroje pro.</span><span class="sxs-lookup"><span data-stu-id="77c1b-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="77c1b-121">Ve výchozím nastavení se pokusí vybrat nejvhodnější cílové rozhraní .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="77c1b-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="77c1b-122">Určuje, že instalace je uživatel široké.</span><span class="sxs-lookup"><span data-stu-id="77c1b-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="77c1b-123">Nelze kombinovat s `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="77c1b-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="77c1b-124">Pokud nezadáte tuto možnost, musíte zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="77c1b-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="77c1b-125">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="77c1b-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="77c1b-126">Určuje umístění, kam se má nainstalovat nástroj globální.</span><span class="sxs-lookup"><span data-stu-id="77c1b-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="77c1b-127">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="77c1b-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="77c1b-128">Pokud cesta neexistuje, příkaz se pokusí se ji vytvořit.</span><span class="sxs-lookup"><span data-stu-id="77c1b-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="77c1b-129">Nelze kombinovat s `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="77c1b-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="77c1b-130">Pokud nezadáte tuto možnost, musíte zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="77c1b-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="77c1b-131">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="77c1b-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="77c1b-132">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="77c1b-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="77c1b-133">Používaná verze nástroje pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="77c1b-133">The version of the tool to install.</span></span> <span data-ttu-id="77c1b-134">Ve výchozím nastavení je nainstalovaná nejnovější verze stabilní balíčku.</span><span class="sxs-lookup"><span data-stu-id="77c1b-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="77c1b-135">Tuto možnost použijte k instalaci preview nebo starší verze nástroje.</span><span class="sxs-lookup"><span data-stu-id="77c1b-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="77c1b-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="77c1b-136">Examples</span></span>

<span data-ttu-id="77c1b-137">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj ve výchozím umístění:</span><span class="sxs-lookup"><span data-stu-id="77c1b-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="77c1b-138">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj určité složky systému Windows:</span><span class="sxs-lookup"><span data-stu-id="77c1b-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="77c1b-139">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj v konkrétní složce systému Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="77c1b-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="77c1b-140">Nainstaluje verzi 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="77c1b-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="77c1b-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77c1b-141">See also</span></span>

[<span data-ttu-id="77c1b-142">.NET core globální nástroje</span><span class="sxs-lookup"><span data-stu-id="77c1b-142">.NET Core Global Tools</span></span>](global-tools.md)