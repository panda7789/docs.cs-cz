---
title: příkaz update DotNet nástroj – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet nástroj aktualizace aktualizuje zadaný nástroje rozhraní .NET Core globální na svém počítači.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 90b0dc91f74d890420dc7185642aa89100cadba8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44069390"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="c1b6f-103">aktualizace nástrojů DotNet</span><span class="sxs-lookup"><span data-stu-id="c1b6f-103">dotnet tool update</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="c1b6f-104">Název</span><span class="sxs-lookup"><span data-stu-id="c1b6f-104">Name</span></span>

<span data-ttu-id="c1b6f-105">`dotnet tool update` -Aktualizace zadaný [globální nástroje .NET Core](global-tools.md) na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-105">`dotnet tool update` - Updates the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c1b6f-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="c1b6f-106">Synopsis</span></span>

```console
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="c1b6f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c1b6f-107">Description</span></span>

<span data-ttu-id="c1b6f-108">`dotnet tool update` Příkaz poskytuje způsob, jak můžete aktualizovat globální nástroje .NET Core na svém počítači na nejnovější stabilní verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-108">The `dotnet tool update` command provides a way for you to update .NET Core Global Tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="c1b6f-109">Příkaz odinstaluje a přeinstaluje nástroj efektivně aktualizace.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-109">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="c1b6f-110">Použití příkazu, buď musíte zadat, že chcete nástroj z celé uživatelské instalace pomocí aktualizací `--global` možnost nebo zadejte cestu k umístění, kde je nástroj nainstalován pomocí `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-110">To use the command, you either have to specify that you want to update a tool from a user-wide installation using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="c1b6f-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="c1b6f-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="c1b6f-112">Název nebo ID balíčku NuGet, který obsahuje globální nástroji .NET Core k aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-112">Name/ID of the NuGet package that contains the .NET Core Global Tool to update.</span></span> <span data-ttu-id="c1b6f-113">Můžete najít pomocí názvu balíčku [seznam nástrojů dotnet](dotnet-tool-list.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-113">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="c1b6f-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c1b6f-114">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="c1b6f-115">Přidá další zdroj balíčku NuGet pro použití během instalace.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-115">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="c1b6f-116">Konfigurace NuGet (*nuget.config*) soubor se má použít.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-116">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="c1b6f-117">Určuje [Cílová architektura](../../standard/frameworks.md) aktualizovat nástroj pro.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-117">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

`-g|--global`

<span data-ttu-id="c1b6f-118">Určuje, že je aktualizace pro celé uživatelské nástroje.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-118">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="c1b6f-119">Nelze kombinovat s `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="c1b6f-120">Pokud nezadáte tuto možnost, je nutné zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-120">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="c1b6f-121">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-121">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="c1b6f-122">Určuje umístění, kde je nainstalován nástroj globální.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-122">Specifies the location where the Global Tool is installed.</span></span> <span data-ttu-id="c1b6f-123">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-123">PATH can be absolute or relative.</span></span> <span data-ttu-id="c1b6f-124">Nelze kombinovat s `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-124">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="c1b6f-125">Pokud nezadáte tuto možnost, je nutné zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-125">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="c1b6f-126">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c1b6f-127">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-127">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="c1b6f-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="c1b6f-128">Examples</span></span>

<span data-ttu-id="c1b6f-129">Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="c1b6f-129">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool update -g dotnetsay`

<span data-ttu-id="c1b6f-130">Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje nachází v určité složce Windows:</span><span class="sxs-lookup"><span data-stu-id="c1b6f-130">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Windows folder:</span></span>

`dotnet tool update dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="c1b6f-131">Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální umístěný do konkrétní složky Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="c1b6f-131">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Linux/macOS folder:</span></span>

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="c1b6f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1b6f-132">See also</span></span>

* [<span data-ttu-id="c1b6f-133">Globální nástroje .NET core</span><span class="sxs-lookup"><span data-stu-id="c1b6f-133">.NET Core Global Tools</span></span>](global-tools.md)