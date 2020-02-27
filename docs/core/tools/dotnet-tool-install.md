---
title: příkaz pro instalaci nástroje dotnet
description: Příkaz pro instalaci nástroje dotnet nainstaluje na váš počítač zadaný nástroj .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 837d12bc807ad95ccdbd9c0e087c7d45418c6e74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626031"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="aae91-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="aae91-103">dotnet tool install</span></span>

<span data-ttu-id="aae91-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="aae91-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="aae91-105">Název</span><span class="sxs-lookup"><span data-stu-id="aae91-105">Name</span></span>

<span data-ttu-id="aae91-106">`dotnet tool install` – nainstaluje na váš počítač zadaný [nástroj .NET Core](global-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="aae91-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="aae91-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="aae91-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="aae91-108">Popis</span><span class="sxs-lookup"><span data-stu-id="aae91-108">Description</span></span>

<span data-ttu-id="aae91-109">Příkaz `dotnet tool install` poskytuje způsob, jak nainstalovat nástroje .NET Core na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="aae91-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="aae91-110">Chcete-li použít příkaz, zadejte jednu z následujících možností instalace:</span><span class="sxs-lookup"><span data-stu-id="aae91-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="aae91-111">Pokud chcete nainstalovat globální nástroj ve výchozím umístění, použijte možnost `--global`.</span><span class="sxs-lookup"><span data-stu-id="aae91-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="aae91-112">Pokud chcete nainstalovat globální nástroj ve vlastním umístění, použijte možnost `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="aae91-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="aae91-113">Chcete-li nainstalovat místní nástroj, vynechejte možnosti `--global` a `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="aae91-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="aae91-114">**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="aae91-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="aae91-115">Globální nástroje se ve výchozím nastavení nainstalují do následujících adresářů, když zadáte `-g` nebo `--global` možnosti:</span><span class="sxs-lookup"><span data-stu-id="aae91-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="aae91-116">Operační systém</span><span class="sxs-lookup"><span data-stu-id="aae91-116">OS</span></span>          | <span data-ttu-id="aae91-117">Cesta</span><span class="sxs-lookup"><span data-stu-id="aae91-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="aae91-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="aae91-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="aae91-119">Windows</span><span class="sxs-lookup"><span data-stu-id="aae91-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="aae91-120">Místní nástroje jsou přidány do souboru *nástroje-manifest. JSON* v adresáři *. config* v rámci aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="aae91-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="aae91-121">Pokud soubor manifestu ještě neexistuje, vytvořte ho spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="aae91-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="aae91-122">Další informace najdete v tématu [instalace místního nástroje](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="aae91-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="aae91-123">Argumenty</span><span class="sxs-lookup"><span data-stu-id="aae91-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="aae91-124">Název nebo ID balíčku NuGet, který obsahuje nástroj .NET Core, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="aae91-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="aae91-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="aae91-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="aae91-126">Přidá další zdroj balíčku NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="aae91-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="aae91-127">Soubor konfigurace NuGet (*NuGet. config*), který se má použít.</span><span class="sxs-lookup"><span data-stu-id="aae91-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="aae91-128">Určuje [cílovou platformu](../../standard/frameworks.md) pro instalaci nástroje pro.</span><span class="sxs-lookup"><span data-stu-id="aae91-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="aae91-129">Ve výchozím nastavení se .NET Core SDK pokusí zvolit nejvhodnější cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aae91-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="aae91-130">Určuje, že instalace je rozsáhlá pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="aae91-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="aae91-131">Nelze kombinovat s možností `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="aae91-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="aae91-132">Vynechání `--global` a `--tool-path` Určuje instalaci místního nástroje.</span><span class="sxs-lookup"><span data-stu-id="aae91-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="aae91-133">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="aae91-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="aae91-134">Určuje umístění, kam se má nainstalovat globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="aae91-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="aae91-135">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="aae91-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="aae91-136">Pokud cesta neexistuje, příkaz se pokusí ho vytvořit.</span><span class="sxs-lookup"><span data-stu-id="aae91-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="aae91-137">Vynechání `--global` a `--tool-path` Určuje instalaci místního nástroje.</span><span class="sxs-lookup"><span data-stu-id="aae91-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span> 

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="aae91-138">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="aae91-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="aae91-139">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="aae91-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="aae91-140">Verze nástroje, který se má nainstalovat</span><span class="sxs-lookup"><span data-stu-id="aae91-140">The version of the tool to install.</span></span> <span data-ttu-id="aae91-141">Ve výchozím nastavení je nainstalovaná nejnovější stabilní verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="aae91-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="aae91-142">Tuto možnost použijte k instalaci verze Preview nebo starší verze nástroje.</span><span class="sxs-lookup"><span data-stu-id="aae91-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="aae91-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="aae91-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="aae91-144">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj ve výchozím umístění.</span><span class="sxs-lookup"><span data-stu-id="aae91-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="aae91-145">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj do konkrétního adresáře Windows.</span><span class="sxs-lookup"><span data-stu-id="aae91-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="aae91-146">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj do konkrétního adresáře Linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="aae91-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="aae91-147">Nainstaluje 2.0.0 verze [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="aae91-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="aae91-148">Nainstaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako místní Nástroj pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="aae91-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="aae91-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="aae91-149">See also</span></span>

- [<span data-ttu-id="aae91-150">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="aae91-150">.NET Core tools</span></span>](global-tools.md)
