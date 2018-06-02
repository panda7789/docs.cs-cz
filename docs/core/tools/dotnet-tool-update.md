---
title: příkaz aktualizace DotNet nástroj - .NET Core rozhraní příkazového řádku
description: Příkaz aktualizace nástrojů dotnet aktualizuje zadaný .NET Core globální nástroj na počítači.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 35a0bd0f85f0beed06d4250d8f195ce4fe4fcca4
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696686"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="90b9b-103">aktualizace nástrojů DotNet.</span><span class="sxs-lookup"><span data-stu-id="90b9b-103">dotnet tool update</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="90b9b-104">Název</span><span class="sxs-lookup"><span data-stu-id="90b9b-104">Name</span></span>

<span data-ttu-id="90b9b-105">`dotnet tool update` -Aktualizace zadaný [.NET Core globální nástroj](global-tools.md) na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="90b9b-105">`dotnet tool update` - Updates the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="90b9b-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="90b9b-106">Synopsis</span></span>

```
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="90b9b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="90b9b-107">Description</span></span>

<span data-ttu-id="90b9b-108">`dotnet tool update` Příkaz nabízí způsob, jak můžete aktualizovat .NET Core globální nástroje na váš počítač nejnovější stabilní verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="90b9b-108">The `dotnet tool update` command provides a way for you to update .NET Core Global Tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="90b9b-109">Příkaz odinstaluje a přeinstaluje nástroj efektivně jeho aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="90b9b-109">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="90b9b-110">Použití příkazu, buď musíte zadat, že chcete aktualizovat nástroj z instalace celou uživatele pomocí `--global` možnost nebo zadejte cestu k umístění, kde je nástroj nainstalován pomocí `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="90b9b-110">To use the command, you either have to specify that you want to update a tool from a user-wide installation using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="90b9b-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="90b9b-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="90b9b-112">Název nebo ID balíčku NuGet, který obsahuje rozhraní .NET Core globální nástroj k aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="90b9b-112">Name/ID of the NuGet package that contains the .NET Core Global Tool to update.</span></span> <span data-ttu-id="90b9b-113">Můžete najít pomocí názvu balíčku [seznam nástrojů dotnet](dotnet-tool-list.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="90b9b-113">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="90b9b-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="90b9b-114">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="90b9b-115">Přidá další zdroj balíčku NuGet chcete použít během instalace.</span><span class="sxs-lookup"><span data-stu-id="90b9b-115">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="90b9b-116">Konfigurace NuGet (*nuget.config*) souboru k použití.</span><span class="sxs-lookup"><span data-stu-id="90b9b-116">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="90b9b-117">Určuje, [cílové rozhraní](../../standard/frameworks.md) aktualizovat nástroj pro.</span><span class="sxs-lookup"><span data-stu-id="90b9b-117">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

`-g|--global`

<span data-ttu-id="90b9b-118">Určuje, že aktualizace je pro nástroj na úrovni uživatele.</span><span class="sxs-lookup"><span data-stu-id="90b9b-118">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="90b9b-119">Nelze kombinovat s `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="90b9b-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="90b9b-120">Pokud nezadáte tuto možnost, musíte zadat `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="90b9b-120">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="90b9b-121">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="90b9b-121">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="90b9b-122">Určuje umístění, kde je nainstalován nástroj globální.</span><span class="sxs-lookup"><span data-stu-id="90b9b-122">Specifies the location where the Global Tool is installed.</span></span> <span data-ttu-id="90b9b-123">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="90b9b-123">PATH can be absolute or relative.</span></span> <span data-ttu-id="90b9b-124">Nelze kombinovat s `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="90b9b-124">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="90b9b-125">Pokud nezadáte tuto možnost, musíte zadat `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="90b9b-125">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="90b9b-126">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="90b9b-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="90b9b-127">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="90b9b-127">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="90b9b-128">Příklady</span><span class="sxs-lookup"><span data-stu-id="90b9b-128">Examples</span></span>

<span data-ttu-id="90b9b-129">Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="90b9b-129">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool update -g dotnetsay`

<span data-ttu-id="90b9b-130">Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální umístěný v konkrétní složce systému Windows:</span><span class="sxs-lookup"><span data-stu-id="90b9b-130">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Windows folder:</span></span>

`dotnet tool update dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="90b9b-131">Aktualizace [dotnetsay](https://www.nuget.org/packages/dotnetsay/) globální umístěný v konkrétní složce systému Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="90b9b-131">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Linux/macOS folder:</span></span>

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="90b9b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90b9b-132">See also</span></span>

[<span data-ttu-id="90b9b-133">.NET core globální nástroje</span><span class="sxs-lookup"><span data-stu-id="90b9b-133">.NET Core Global Tools</span></span>](global-tools.md)