---
title: příkaz pro instalaci nástroje dotnet
description: Příkaz pro instalaci nástroje dotnet nainstaluje na váš počítač zadaný nástroj .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 067f90124833da537370a36934ff212aba7577f3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702810"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="09932-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="09932-103">dotnet tool install</span></span>

<span data-ttu-id="09932-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="09932-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="09932-105">Name</span><span class="sxs-lookup"><span data-stu-id="09932-105">Name</span></span>

<span data-ttu-id="09932-106">`dotnet tool install`– Nainstaluje na váš počítač zadaný [nástroj .NET Core](global-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="09932-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="09932-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="09932-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a><span data-ttu-id="09932-108">Popis</span><span class="sxs-lookup"><span data-stu-id="09932-108">Description</span></span>

<span data-ttu-id="09932-109">`dotnet tool install`Příkaz nabízí způsob, jak nainstalovat nástroje .NET Core na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="09932-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="09932-110">Chcete-li použít příkaz, zadejte jednu z následujících možností instalace:</span><span class="sxs-lookup"><span data-stu-id="09932-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="09932-111">Pokud chcete nainstalovat globální nástroj ve výchozím umístění, použijte `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="09932-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="09932-112">Pokud chcete nainstalovat globální nástroj ve vlastním umístění, použijte `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="09932-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="09932-113">Chcete-li nainstalovat místní nástroj, vynechejte `--global` `--tool-path` Možnosti a.</span><span class="sxs-lookup"><span data-stu-id="09932-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="09932-114">**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="09932-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="09932-115">Globální nástroje jsou ve výchozím nastavení nainstalovány v následujících adresářích při zadání `-g` Možnosti nebo `--global` :</span><span class="sxs-lookup"><span data-stu-id="09932-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="09932-116">Operační systém</span><span class="sxs-lookup"><span data-stu-id="09932-116">OS</span></span>          | <span data-ttu-id="09932-117">Cesta</span><span class="sxs-lookup"><span data-stu-id="09932-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="09932-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="09932-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="09932-119">Windows</span><span class="sxs-lookup"><span data-stu-id="09932-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="09932-120">Místní nástroje jsou přidány do souboru *dotnet-Tools. JSON* v adresáři *. config* v rámci aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="09932-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="09932-121">Pokud soubor manifestu ještě neexistuje, vytvořte ho spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="09932-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="09932-122">Další informace najdete v tématu [instalace místního nástroje](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="09932-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="09932-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="09932-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="09932-124">Název nebo ID balíčku NuGet, který obsahuje nástroj .NET Core, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="09932-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="09932-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="09932-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="09932-126">Přidá další zdroj balíčku NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="09932-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="09932-127">Soubor konfigurace NuGet (*NuGet. config*), který se má použít.</span><span class="sxs-lookup"><span data-stu-id="09932-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="09932-128">Určuje [cílovou platformu](../../standard/frameworks.md) pro instalaci nástroje pro.</span><span class="sxs-lookup"><span data-stu-id="09932-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="09932-129">Ve výchozím nastavení se .NET Core SDK pokusí zvolit nejvhodnější cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="09932-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="09932-130">Určuje, že instalace je rozsáhlá pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="09932-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="09932-131">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="09932-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="09932-132">Vynechání obou `--global` a `--tool-path` určí instalaci místního nástroje.</span><span class="sxs-lookup"><span data-stu-id="09932-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="09932-133">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="09932-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="09932-134">Určuje umístění, kam se má nainstalovat globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="09932-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="09932-135">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="09932-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="09932-136">Pokud cesta neexistuje, příkaz se pokusí ho vytvořit.</span><span class="sxs-lookup"><span data-stu-id="09932-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="09932-137">Vynechání obou `--global` a `--tool-path` určí instalaci místního nástroje.</span><span class="sxs-lookup"><span data-stu-id="09932-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="09932-138">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="09932-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="09932-139">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="09932-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="09932-140">Verze nástroje, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="09932-140">The version of the tool to install.</span></span> <span data-ttu-id="09932-141">Ve výchozím nastavení je nainstalovaná nejnovější stabilní verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="09932-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="09932-142">Tuto možnost použijte k instalaci verze Preview nebo starší verze nástroje.</span><span class="sxs-lookup"><span data-stu-id="09932-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="09932-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="09932-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="09932-144">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj ve výchozím umístění.</span><span class="sxs-lookup"><span data-stu-id="09932-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="09932-145">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj do konkrétního adresáře Windows.</span><span class="sxs-lookup"><span data-stu-id="09932-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="09932-146">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj do konkrétního adresáře Linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="09932-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="09932-147">Nainstaluje 2.0.0 verze [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="09932-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="09932-148">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako místní Nástroj pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="09932-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="09932-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="09932-149">See also</span></span>

- [<span data-ttu-id="09932-150">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="09932-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="09932-151">Kurz: instalace a použití globálního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="09932-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="09932-152">Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="09932-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
