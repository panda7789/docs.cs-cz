---
title: dotnet nástroj aktualizovat, příkaz
description: Příkaz aktualizace nástroje dotnet aktualizuje zadaný nástroj .NET Core v počítači.
ms.date: 02/14/2020
ms.openlocfilehash: 6176846dbe8e2a91d9c6959dede15718d8f983b2
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463301"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="5a936-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="5a936-103">dotnet tool update</span></span>

<span data-ttu-id="5a936-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="5a936-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5a936-105">Název</span><span class="sxs-lookup"><span data-stu-id="5a936-105">Name</span></span>

<span data-ttu-id="5a936-106">`dotnet tool update`- Aktualizuje zadaný [nástroj .NET Core v](global-tools.md) počítači.</span><span class="sxs-lookup"><span data-stu-id="5a936-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5a936-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="5a936-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="5a936-108">Popis</span><span class="sxs-lookup"><span data-stu-id="5a936-108">Description</span></span>

<span data-ttu-id="5a936-109">Příkaz `dotnet tool update` poskytuje způsob, jak aktualizovat nástroje .NET Core v počítači na nejnovější stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="5a936-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="5a936-110">Příkaz odinstaluje a přeinstaluje nástroj, efektivně jej aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="5a936-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="5a936-111">Chcete-li použít příkaz, zadejte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="5a936-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="5a936-112">Chcete-li aktualizovat globální nástroj, který byl `--global` nainstalován ve výchozím umístění, použijte možnost</span><span class="sxs-lookup"><span data-stu-id="5a936-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="5a936-113">Chcete-li aktualizovat globální nástroj, který byl `--tool-path` nainstalován ve vlastním umístění, použijte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="5a936-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="5a936-114">Chcete-li aktualizovat místní nástroj, `--global` `--tool-path` vynechte možnosti a.</span><span class="sxs-lookup"><span data-stu-id="5a936-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="5a936-115">**Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="5a936-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="5a936-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5a936-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="5a936-117">Název/ID balíčku NuGet, který obsahuje globální nástroj .NET Core, který má být aktualizován.</span><span class="sxs-lookup"><span data-stu-id="5a936-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="5a936-118">Název balíčku můžete najít pomocí příkazu [seznamu nástrojů dotnet.](dotnet-tool-list.md)</span><span class="sxs-lookup"><span data-stu-id="5a936-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="5a936-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5a936-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="5a936-120">Přidá další zdroj balíčku NuGet pro použití během instalace.</span><span class="sxs-lookup"><span data-stu-id="5a936-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="5a936-121">Soubor konfigurace NuGet (*nuget.config).*</span><span class="sxs-lookup"><span data-stu-id="5a936-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="5a936-122">Určuje [cílovou architekturu,](../../standard/frameworks.md) pro kterou má být nástroj aktualizován.</span><span class="sxs-lookup"><span data-stu-id="5a936-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="5a936-123">Určuje, že aktualizace je určen pro nástroj pro celý uživatele.</span><span class="sxs-lookup"><span data-stu-id="5a936-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="5a936-124">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="5a936-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="5a936-125">Vynechání obou `--global` `--tool-path` a určuje, že nástroj, který má být aktualizován, je místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="5a936-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5a936-126">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="5a936-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="5a936-127">Určuje umístění, kde je globální nástroj nainstalován.</span><span class="sxs-lookup"><span data-stu-id="5a936-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="5a936-128">CESTA může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="5a936-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="5a936-129">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="5a936-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="5a936-130">Vynechání obou `--global` `--tool-path` a určuje, že nástroj, který má být aktualizován, je místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="5a936-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5a936-131">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="5a936-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5a936-132">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="5a936-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="5a936-133">Příklady</span><span class="sxs-lookup"><span data-stu-id="5a936-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="5a936-134">Aktualizuje globální nástroj [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)</span><span class="sxs-lookup"><span data-stu-id="5a936-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="5a936-135">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5a936-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="5a936-136">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="5a936-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="5a936-137">Aktualizuje místní nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) nainstalovaný pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="5a936-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a936-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a936-138">See also</span></span>

- [<span data-ttu-id="5a936-139">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="5a936-139">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="5a936-140">Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="5a936-140">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="5a936-141">Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="5a936-141">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
