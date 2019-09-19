---
title: příkaz pro instalaci nástroje dotnet
description: Instalační příkaz nástroje dotnet nainstaluje na svém počítači zadaný globální nástroj .NET Core.
ms.date: 05/29/2018
ms.openlocfilehash: d6f691117e93a39c9837b282dca19e452515c80a
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117469"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="c36b6-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="c36b6-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="c36b6-104">Name</span><span class="sxs-lookup"><span data-stu-id="c36b6-104">Name</span></span>

<span data-ttu-id="c36b6-105">`dotnet tool install`– Nainstaluje na váš počítač zadaný [globální nástroj .NET Core](global-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="c36b6-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c36b6-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="c36b6-106">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="c36b6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c36b6-107">Description</span></span>

<span data-ttu-id="c36b6-108">`dotnet tool install` Příkaz nabízí způsob, jak na svém počítači nainstalovat globální nástroje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c36b6-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="c36b6-109">Chcete-li použít příkaz, musíte určit, že chcete provést instalaci pro všechny uživatele pomocí `--global` možnosti, nebo zadat cestu k její instalaci `--tool-path` pomocí možnosti.</span><span class="sxs-lookup"><span data-stu-id="c36b6-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="c36b6-110">Globální nástroje jsou ve výchozím nastavení nainstalovány v následujících adresářích při zadání `-g` možnosti (nebo `--global`):</span><span class="sxs-lookup"><span data-stu-id="c36b6-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="c36b6-111">OS</span><span class="sxs-lookup"><span data-stu-id="c36b6-111">OS</span></span>          | <span data-ttu-id="c36b6-112">Cesta</span><span class="sxs-lookup"><span data-stu-id="c36b6-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="c36b6-113">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="c36b6-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="c36b6-114">Windows</span><span class="sxs-lookup"><span data-stu-id="c36b6-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="c36b6-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="c36b6-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="c36b6-116">Název nebo ID balíčku NuGet, který obsahuje globální nástroj .NET Core, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="c36b6-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="c36b6-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c36b6-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="c36b6-118">Přidá další zdroj balíčku NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="c36b6-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="c36b6-119">Soubor konfigurace NuGet (*NuGet. config*), který se má použít.</span><span class="sxs-lookup"><span data-stu-id="c36b6-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="c36b6-120">Určuje [cílovou platformu](../../standard/frameworks.md) pro instalaci nástroje pro.</span><span class="sxs-lookup"><span data-stu-id="c36b6-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="c36b6-121">Ve výchozím nastavení se .NET Core SDK pokusí zvolit nejvhodnější cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c36b6-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="c36b6-122">Určuje, že instalace je rozsáhlá pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="c36b6-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="c36b6-123">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="c36b6-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="c36b6-124">Pokud tuto možnost nezadáte, musíte zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="c36b6-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="c36b6-125">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="c36b6-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="c36b6-126">Určuje umístění, kam se má nainstalovat globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="c36b6-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="c36b6-127">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="c36b6-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="c36b6-128">Pokud cesta neexistuje, příkaz se pokusí ho vytvořit.</span><span class="sxs-lookup"><span data-stu-id="c36b6-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="c36b6-129">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="c36b6-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="c36b6-130">Pokud tuto možnost nezadáte, musíte zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="c36b6-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="c36b6-131">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="c36b6-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c36b6-132">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="c36b6-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="c36b6-133">Verze nástroje, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="c36b6-133">The version of the tool to install.</span></span> <span data-ttu-id="c36b6-134">Ve výchozím nastavení je nainstalovaná nejnovější stabilní verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="c36b6-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="c36b6-135">Tuto možnost použijte k instalaci verze Preview nebo starší verze nástroje.</span><span class="sxs-lookup"><span data-stu-id="c36b6-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="c36b6-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="c36b6-136">Examples</span></span>

<span data-ttu-id="c36b6-137">Nainstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="c36b6-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="c36b6-138">Nainstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do určité složky Windows:</span><span class="sxs-lookup"><span data-stu-id="c36b6-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="c36b6-139">Nainstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do konkrétní složky Linux/MacOS:</span><span class="sxs-lookup"><span data-stu-id="c36b6-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="c36b6-140">Nainstaluje 2.0.0 verze globálního nástroje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :</span><span class="sxs-lookup"><span data-stu-id="c36b6-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="c36b6-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c36b6-141">See also</span></span>

- [<span data-ttu-id="c36b6-142">Globální nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="c36b6-142">.NET Core Global Tools</span></span>](global-tools.md)
