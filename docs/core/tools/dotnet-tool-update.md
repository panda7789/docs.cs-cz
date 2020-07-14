---
title: příkaz pro aktualizaci nástroje dotnet
description: Příkaz pro aktualizaci nástroje dotnet aktualizuje zadaný nástroj .NET Core na vašem počítači.
ms.date: 07/08/2020
ms.openlocfilehash: 7c4bde44ac9964828074baeb1a697ba64ed17887
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226618"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="e94e2-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="e94e2-103">dotnet tool update</span></span>

<span data-ttu-id="e94e2-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="e94e2-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e94e2-105">Name</span><span class="sxs-lookup"><span data-stu-id="e94e2-105">Name</span></span>

<span data-ttu-id="e94e2-106">`dotnet tool update`– Aktualizuje zadaný [nástroj .NET Core](global-tools.md) na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="e94e2-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e94e2-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="e94e2-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="e94e2-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e94e2-108">Description</span></span>

<span data-ttu-id="e94e2-109">`dotnet tool update`Příkaz nabízí způsob, jak aktualizovat nástroje .NET Core na vašem počítači na nejnovější stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="e94e2-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="e94e2-110">Příkaz odinstaluje a znovu nainstaluje nástroj a efektivně ho aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="e94e2-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="e94e2-111">Chcete-li použít příkaz, zadejte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="e94e2-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="e94e2-112">Pokud chcete aktualizovat globální nástroj, který byl nainstalovaný ve výchozím umístění, použijte `--global` možnost.</span><span class="sxs-lookup"><span data-stu-id="e94e2-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="e94e2-113">Chcete-li aktualizovat globální nástroj, který byl nainstalován ve vlastním umístění, použijte `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="e94e2-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="e94e2-114">Pokud chcete aktualizovat místní nástroj, použijte `--local` možnost.</span><span class="sxs-lookup"><span data-stu-id="e94e2-114">To update a local tool, use the `--local` option.</span></span>

<span data-ttu-id="e94e2-115">**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="e94e2-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="e94e2-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="e94e2-116">Arguments</span></span>

- **`PACKAGE_ID`**

  <span data-ttu-id="e94e2-117">Název nebo ID balíčku NuGet, který obsahuje globální nástroj .NET Core, který se má aktualizovat</span><span class="sxs-lookup"><span data-stu-id="e94e2-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="e94e2-118">Název balíčku můžete najít pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="e94e2-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="e94e2-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e94e2-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="e94e2-120">Přidá další zdroj balíčku NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="e94e2-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="e94e2-121">Soubor konfigurace NuGet (*nuget.config*), který se má použít.</span><span class="sxs-lookup"><span data-stu-id="e94e2-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="e94e2-122">Zabránit v paralelním obnovení více projektů.</span><span class="sxs-lookup"><span data-stu-id="e94e2-122">Prevent restoring multiple projects in parallel.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="e94e2-123">Určuje [cílovou platformu](../../standard/frameworks.md) , pro kterou chcete nástroj aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="e94e2-123">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="e94e2-124">Považovat selhání zdroje balíčku za upozornění.</span><span class="sxs-lookup"><span data-stu-id="e94e2-124">Treat package source failures as warnings.</span></span>

- **`--interactive`**

  <span data-ttu-id="e94e2-125">Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování).</span><span class="sxs-lookup"><span data-stu-id="e94e2-125">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`--local`**

  <span data-ttu-id="e94e2-126">Aktualizujte nástroj a manifest místního nástroje.</span><span class="sxs-lookup"><span data-stu-id="e94e2-126">Update the tool and the local tool manifest.</span></span> <span data-ttu-id="e94e2-127">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="e94e2-127">Can't be combined with the `--global` option.</span></span>

- **`--no-cache`**

  <span data-ttu-id="e94e2-128">Neukládat balíčky a požadavky HTTP do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e94e2-128">Do not cache packages and HTTP requests.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="e94e2-129">Cesta k souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="e94e2-129">Path to the manifest file.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="e94e2-130">Určuje umístění, kde je nainstalován globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="e94e2-130">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="e94e2-131">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="e94e2-131">PATH can be absolute or relative.</span></span> <span data-ttu-id="e94e2-132">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="e94e2-132">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="e94e2-133">Vynechání obou `--global` a `--tool-path` určí, že nástroj, který má být aktualizován, je místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="e94e2-133">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`--version <VERSION>`**

  <span data-ttu-id="e94e2-134">Rozsah verzí balíčku nástroje, na který se má aktualizace aktualizovat</span><span class="sxs-lookup"><span data-stu-id="e94e2-134">The version range of the tool package to update to.</span></span> <span data-ttu-id="e94e2-135">Tato verze se nedá použít k downgradům verzí, ale `uninstall` nejdřív je potřeba novější verze.</span><span class="sxs-lookup"><span data-stu-id="e94e2-135">This cannot be used to downgrade versions, you must `uninstall` newer versions first.</span></span>

- **`-g|--global`**

  <span data-ttu-id="e94e2-136">Určuje, že je aktualizace určena pro nástroj pro uživatelský rozsah.</span><span class="sxs-lookup"><span data-stu-id="e94e2-136">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="e94e2-137">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="e94e2-137">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="e94e2-138">Vynechání obou `--global` a `--tool-path` určí, že nástroj, který má být aktualizován, je místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="e94e2-138">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e94e2-139">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="e94e2-139">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e94e2-140">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="e94e2-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e94e2-141">Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="e94e2-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="e94e2-142">Příklady</span><span class="sxs-lookup"><span data-stu-id="e94e2-142">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="e94e2-143">Aktualizuje nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global.</span><span class="sxs-lookup"><span data-stu-id="e94e2-143">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="e94e2-144">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři Windows.</span><span class="sxs-lookup"><span data-stu-id="e94e2-144">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="e94e2-145">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři Linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="e94e2-145">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="e94e2-146">Aktualizuje místní nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) nainstalovaný pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="e94e2-146">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  <span data-ttu-id="e94e2-147">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) na nejnovější verzi opravy s hlavní verzí `2` a podverzí nástroje `0` .</span><span class="sxs-lookup"><span data-stu-id="e94e2-147">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the latest patch version, with a major version of `2`, and a minor version of `0`.</span></span>

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  <span data-ttu-id="e94e2-148">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) na nejnižší verzi v zadaném rozsahu `(> 2.0.0 && < 2.1.4)` , verze se `2.1.0` nainstaluje.</span><span class="sxs-lookup"><span data-stu-id="e94e2-148">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the lowest version within the specified range `(> 2.0.0 && < 2.1.4)`, version `2.1.0` would be installed.</span></span> <span data-ttu-id="e94e2-149">Další informace o rozsahu sémantických verzí najdete v tématu [rozsahy verzí balíčku NuGet](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="e94e2-149">For more information on semantic versioning ranges, see [NuGet packaging version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

## <a name="see-also"></a><span data-ttu-id="e94e2-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="e94e2-150">See also</span></span>

- [<span data-ttu-id="e94e2-151">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="e94e2-151">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="e94e2-152">Sémantická verze</span><span class="sxs-lookup"><span data-stu-id="e94e2-152">Semantic versioning</span></span>](https://semver.org)
- [<span data-ttu-id="e94e2-153">Kurz: instalace a použití globálního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="e94e2-153">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="e94e2-154">Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="e94e2-154">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
