---
title: Instalace nástrojů DotNet příkaz – rozhraní příkazového řádku .NET Core
description: Nástroj dotnet nainstalovat příkaz nainstaluje zadaný globální nástroji .NET Core na počítači.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: aad5a3e815936749d90f40975a8b13d34e89386c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512192"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="8703e-103">Instalace nástrojů DotNet</span><span class="sxs-lookup"><span data-stu-id="8703e-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="8703e-104">Název</span><span class="sxs-lookup"><span data-stu-id="8703e-104">Name</span></span>

<span data-ttu-id="8703e-105">`dotnet tool install` -Nainstaluje zadaný [globální nástroje .NET Core](global-tools.md) na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="8703e-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8703e-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="8703e-106">Synopsis</span></span>

```console
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="8703e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8703e-107">Description</span></span>

<span data-ttu-id="8703e-108">`dotnet tool install` Příkaz poskytuje způsob, jak k instalaci globální nástroje .NET Core na počítači.</span><span class="sxs-lookup"><span data-stu-id="8703e-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="8703e-109">Chcete-li použít příkaz, potřebujete buď určete, jestli má uživatel celou instalaci pomocí `--global` možnost nebo můžete zadat cestu k ho nainstalovat pomocí `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="8703e-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="8703e-110">Globální nástroje jsou nainstalovány v následujících adresářích ve výchozím nastavení při zadání `-g` (nebo `--global`) možnost:</span><span class="sxs-lookup"><span data-stu-id="8703e-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="8703e-111">OPERAČNÍ SYSTÉM</span><span class="sxs-lookup"><span data-stu-id="8703e-111">OS</span></span>          | <span data-ttu-id="8703e-112">Cesta</span><span class="sxs-lookup"><span data-stu-id="8703e-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="8703e-113">Linux nebo macOS</span><span class="sxs-lookup"><span data-stu-id="8703e-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="8703e-114">Windows</span><span class="sxs-lookup"><span data-stu-id="8703e-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="8703e-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="8703e-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="8703e-116">Název nebo ID, která nástroj obsahuje, .NET Core globální instalace balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="8703e-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="8703e-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8703e-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="8703e-118">Přidá další zdroj balíčku NuGet pro použití během instalace.</span><span class="sxs-lookup"><span data-stu-id="8703e-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="8703e-119">Konfigurace NuGet (*nuget.config*) soubor se má použít.</span><span class="sxs-lookup"><span data-stu-id="8703e-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="8703e-120">Určuje, [cílovou architekturu](../../standard/frameworks.md) instalace nástroje pro.</span><span class="sxs-lookup"><span data-stu-id="8703e-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="8703e-121">Ve výchozím nastavení .NET Core SDK se pokusí zvolte nejvhodnější cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="8703e-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="8703e-122">Určuje, že instalace je uživatel široké.</span><span class="sxs-lookup"><span data-stu-id="8703e-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="8703e-123">Nelze kombinovat s `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="8703e-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="8703e-124">Pokud nezadáte tuto možnost, je nutné zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="8703e-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="8703e-125">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="8703e-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="8703e-126">Určuje umístění, kam se má nainstalovat nástroj globální.</span><span class="sxs-lookup"><span data-stu-id="8703e-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="8703e-127">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="8703e-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="8703e-128">Pokud cesta neexistuje, příkaz se pokusí se ji vytvořit.</span><span class="sxs-lookup"><span data-stu-id="8703e-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="8703e-129">Nelze kombinovat s `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="8703e-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="8703e-130">Pokud nezadáte tuto možnost, je nutné zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="8703e-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="8703e-131">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="8703e-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8703e-132">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="8703e-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="8703e-133">Verze nástroje k instalaci.</span><span class="sxs-lookup"><span data-stu-id="8703e-133">The version of the tool to install.</span></span> <span data-ttu-id="8703e-134">Ve výchozím nastavení je nainstalovaná nejnovější verze stabilní balíček.</span><span class="sxs-lookup"><span data-stu-id="8703e-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="8703e-135">Tuto možnost použijte, chcete-li nainstalovat verzi preview nebo starší verze nástroje.</span><span class="sxs-lookup"><span data-stu-id="8703e-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="8703e-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="8703e-136">Examples</span></span>

<span data-ttu-id="8703e-137">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj ve výchozím umístění:</span><span class="sxs-lookup"><span data-stu-id="8703e-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="8703e-138">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj v určité složce Windows:</span><span class="sxs-lookup"><span data-stu-id="8703e-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="8703e-139">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroj v určité složce Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="8703e-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="8703e-140">Nainstaluje verzi 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="8703e-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="8703e-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8703e-141">See also</span></span>

* [<span data-ttu-id="8703e-142">Globální nástroje .NET core</span><span class="sxs-lookup"><span data-stu-id="8703e-142">.NET Core Global Tools</span></span>](global-tools.md)