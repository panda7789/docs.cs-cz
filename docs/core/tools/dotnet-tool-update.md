---
title: příkaz pro aktualizaci nástroje dotnet
description: Příkaz pro aktualizaci nástroje dotnet aktualizuje zadaný globální nástroj .NET Core na vašem počítači.
ms.date: 05/29/2018
ms.openlocfilehash: b10ce39c8b9d4df23243bcf672454a455e34eec1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117531"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="f7804-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="f7804-103">dotnet tool update</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="f7804-104">Name</span><span class="sxs-lookup"><span data-stu-id="f7804-104">Name</span></span>

<span data-ttu-id="f7804-105">`dotnet tool update`– Aktualizuje zadaný [globální nástroj .NET Core](global-tools.md) na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="f7804-105">`dotnet tool update` - Updates the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f7804-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="f7804-106">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="f7804-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f7804-107">Description</span></span>

<span data-ttu-id="f7804-108">`dotnet tool update` Příkaz nabízí způsob, jak aktualizovat globální nástroje .NET Core na vašem počítači na nejnovější stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="f7804-108">The `dotnet tool update` command provides a way for you to update .NET Core Global Tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="f7804-109">Příkaz odinstaluje a znovu nainstaluje nástroj a efektivně ho aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="f7804-109">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="f7804-110">Chcete-li použít příkaz, musíte určit, že chcete nástroj aktualizovat z uživatelské instalace pomocí `--global` možnosti nebo zadat cestu k umístění nástroje `--tool-path` pomocí možnosti.</span><span class="sxs-lookup"><span data-stu-id="f7804-110">To use the command, you either have to specify that you want to update a tool from a user-wide installation using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="f7804-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="f7804-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="f7804-112">Název nebo ID balíčku NuGet, který obsahuje globální nástroj .NET Core, který se má aktualizovat</span><span class="sxs-lookup"><span data-stu-id="f7804-112">Name/ID of the NuGet package that contains the .NET Core Global Tool to update.</span></span> <span data-ttu-id="f7804-113">Název balíčku můžete najít pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="f7804-113">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="f7804-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f7804-114">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="f7804-115">Přidá další zdroj balíčku NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="f7804-115">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="f7804-116">Soubor konfigurace NuGet (*NuGet. config*), který se má použít.</span><span class="sxs-lookup"><span data-stu-id="f7804-116">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="f7804-117">Určuje [cílovou platformu](../../standard/frameworks.md) , pro kterou chcete nástroj aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="f7804-117">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

`-g|--global`

<span data-ttu-id="f7804-118">Určuje, že je aktualizace určena pro nástroj pro uživatelský rozsah.</span><span class="sxs-lookup"><span data-stu-id="f7804-118">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="f7804-119">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="f7804-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="f7804-120">Pokud tuto možnost nezadáte, musíte zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="f7804-120">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="f7804-121">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="f7804-121">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="f7804-122">Určuje umístění, kde je nainstalován globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="f7804-122">Specifies the location where the Global Tool is installed.</span></span> <span data-ttu-id="f7804-123">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="f7804-123">PATH can be absolute or relative.</span></span> <span data-ttu-id="f7804-124">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="f7804-124">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="f7804-125">Pokud tuto možnost nezadáte, musíte zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="f7804-125">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f7804-126">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f7804-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f7804-127">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="f7804-127">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="f7804-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="f7804-128">Examples</span></span>

<span data-ttu-id="f7804-129">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :</span><span class="sxs-lookup"><span data-stu-id="f7804-129">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool update -g dotnetsay`

<span data-ttu-id="f7804-130">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v konkrétní složce systému Windows:</span><span class="sxs-lookup"><span data-stu-id="f7804-130">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Windows folder:</span></span>

`dotnet tool update dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="f7804-131">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v konkrétní složce Linux/MacOS:</span><span class="sxs-lookup"><span data-stu-id="f7804-131">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Linux/macOS folder:</span></span>

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="f7804-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7804-132">See also</span></span>

- [<span data-ttu-id="f7804-133">Globální nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="f7804-133">.NET Core Global Tools</span></span>](global-tools.md)
