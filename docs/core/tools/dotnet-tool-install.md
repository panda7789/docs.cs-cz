---
title: dotnet nástroj instalace, příkaz
description: Příkaz instalace nástroje dotnet nainstaluje do počítače zadaný nástroj .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 1e142773d1f981a8dc3b552d5a23d2864cdd82c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146460"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="5385b-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="5385b-103">dotnet tool install</span></span>

<span data-ttu-id="5385b-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="5385b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5385b-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="5385b-105">Name</span></span>

<span data-ttu-id="5385b-106">`dotnet tool install`- Nainstaluje do počítače zadaný [nástroj .NET Core.](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="5385b-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5385b-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="5385b-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME> <--tool-path>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="5385b-108">Popis</span><span class="sxs-lookup"><span data-stu-id="5385b-108">Description</span></span>

<span data-ttu-id="5385b-109">Příkaz `dotnet tool install` umožňuje instalaci nástrojů .NET Core do počítače.</span><span class="sxs-lookup"><span data-stu-id="5385b-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="5385b-110">Chcete-li použít příkaz, zadejte jednu z následujících možností instalace:</span><span class="sxs-lookup"><span data-stu-id="5385b-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="5385b-111">Chcete-li nainstalovat globální nástroj do `--global` výchozího umístění, použijte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="5385b-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="5385b-112">Chcete-li nainstalovat globální nástroj do `--tool-path` vlastního umístění, použijte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="5385b-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="5385b-113">Chcete-li nainstalovat místní nástroj, `--global` `--tool-path` vynechte možnosti a.</span><span class="sxs-lookup"><span data-stu-id="5385b-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="5385b-114">**Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="5385b-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="5385b-115">Globální nástroje jsou nainstalovány v následujících adresářích ve výchozím nastavení, když zadáte `-g` možnost nebo: `--global`</span><span class="sxs-lookup"><span data-stu-id="5385b-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="5385b-116">Operační systém</span><span class="sxs-lookup"><span data-stu-id="5385b-116">OS</span></span>          | <span data-ttu-id="5385b-117">Cesta</span><span class="sxs-lookup"><span data-stu-id="5385b-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="5385b-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="5385b-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="5385b-119">Windows</span><span class="sxs-lookup"><span data-stu-id="5385b-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="5385b-120">Místní nástroje jsou přidány do souboru *tool-manifest.json* v *adresáři .config* pod aktuálním adresářem.</span><span class="sxs-lookup"><span data-stu-id="5385b-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="5385b-121">Pokud soubor manifestu ještě neexistuje, vytvořte jej spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="5385b-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="5385b-122">Další informace naleznete [v tématu Instalace místního nástroje](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="5385b-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="5385b-123">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5385b-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="5385b-124">Název/ID balíčku NuGet, který obsahuje nástroj .NET Core k instalaci.</span><span class="sxs-lookup"><span data-stu-id="5385b-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="5385b-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5385b-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="5385b-126">Přidá další zdroj balíčku NuGet pro použití během instalace.</span><span class="sxs-lookup"><span data-stu-id="5385b-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="5385b-127">Soubor konfigurace NuGet (*nuget.config).*</span><span class="sxs-lookup"><span data-stu-id="5385b-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="5385b-128">Určuje [cílovou architekturu,](../../standard/frameworks.md) pro kterou má být nástroj nainstalován.</span><span class="sxs-lookup"><span data-stu-id="5385b-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="5385b-129">Ve výchozím nastavení se sada .NET Core SDK pokusí vybrat nejvhodnější cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="5385b-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="5385b-130">Určuje, že instalace je široká jako uživatel.</span><span class="sxs-lookup"><span data-stu-id="5385b-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="5385b-131">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="5385b-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="5385b-132">Vynechání obou `--global` `--tool-path` a určuje instalaci místního nástroje.</span><span class="sxs-lookup"><span data-stu-id="5385b-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5385b-133">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="5385b-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="5385b-134">Určuje umístění, kam má být globální nástroj nainstalován.</span><span class="sxs-lookup"><span data-stu-id="5385b-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="5385b-135">CESTA může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="5385b-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="5385b-136">Pokud cesta neexistuje, příkaz se pokusí vytvořit.</span><span class="sxs-lookup"><span data-stu-id="5385b-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="5385b-137">Vynechání obou `--global` `--tool-path` a určuje instalaci místního nástroje.</span><span class="sxs-lookup"><span data-stu-id="5385b-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5385b-138">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="5385b-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5385b-139">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="5385b-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="5385b-140">Verze nástroje k instalaci.</span><span class="sxs-lookup"><span data-stu-id="5385b-140">The version of the tool to install.</span></span> <span data-ttu-id="5385b-141">Ve výchozím nastavení je nainstalována nejnovější stabilní verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="5385b-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="5385b-142">Tuto možnost použijte k instalaci náhledu nebo starších verzí nástroje.</span><span class="sxs-lookup"><span data-stu-id="5385b-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="5385b-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="5385b-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="5385b-144">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj ve výchozím umístění.</span><span class="sxs-lookup"><span data-stu-id="5385b-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="5385b-145">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj v určitém adresáři systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5385b-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="5385b-146">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj v určitém adresáři Linux / macOS.</span><span class="sxs-lookup"><span data-stu-id="5385b-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="5385b-147">Nainstaluje verzi 2.0.0 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="5385b-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="5385b-148">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako místní nástroj pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="5385b-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="5385b-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="5385b-149">See also</span></span>

- [<span data-ttu-id="5385b-150">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="5385b-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="5385b-151">Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="5385b-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="5385b-152">Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="5385b-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
