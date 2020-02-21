---
title: příkaz pro aktualizaci nástroje dotnet
description: Příkaz pro aktualizaci nástroje dotnet aktualizuje zadaný nástroj .NET Core na vašem počítači.
ms.date: 02/14/2020
ms.openlocfilehash: 50bb366fedfb0ea69b8b6007ff89e366b4f689de
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543414"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="2a164-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="2a164-103">dotnet tool update</span></span>

<span data-ttu-id="2a164-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="2a164-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2a164-105">Název</span><span class="sxs-lookup"><span data-stu-id="2a164-105">Name</span></span>

<span data-ttu-id="2a164-106">`dotnet tool update` – aktualizuje zadaný [nástroj .NET Core](global-tools.md) na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="2a164-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2a164-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="2a164-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="2a164-108">Popis</span><span class="sxs-lookup"><span data-stu-id="2a164-108">Description</span></span>

<span data-ttu-id="2a164-109">Příkaz `dotnet tool update` poskytuje způsob, jak aktualizovat nástroje .NET Core na vašem počítači na nejnovější stabilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="2a164-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="2a164-110">Příkaz odinstaluje a znovu nainstaluje nástroj a efektivně ho aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="2a164-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="2a164-111">Chcete-li použít příkaz, zadejte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="2a164-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="2a164-112">Pokud chcete aktualizovat globální nástroj, který byl nainstalovaný ve výchozím umístění, použijte možnost `--global`.</span><span class="sxs-lookup"><span data-stu-id="2a164-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="2a164-113">Chcete-li aktualizovat globální nástroj, který byl nainstalován ve vlastním umístění, použijte možnost `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="2a164-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="2a164-114">Chcete-li aktualizovat místní nástroj, vynechejte možnosti `--global` a `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="2a164-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="2a164-115">**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="2a164-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="2a164-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2a164-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="2a164-117">Název nebo ID balíčku NuGet, který obsahuje globální nástroj .NET Core, který se má aktualizovat</span><span class="sxs-lookup"><span data-stu-id="2a164-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="2a164-118">Název balíčku můžete najít pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="2a164-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="2a164-119">Možnosti</span><span class="sxs-lookup"><span data-stu-id="2a164-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="2a164-120">Přidá další zdroj balíčku NuGet, který se použije při instalaci.</span><span class="sxs-lookup"><span data-stu-id="2a164-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="2a164-121">Soubor konfigurace NuGet (*NuGet. config*), který se má použít.</span><span class="sxs-lookup"><span data-stu-id="2a164-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="2a164-122">Určuje [cílovou platformu](../../standard/frameworks.md) , pro kterou chcete nástroj aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="2a164-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="2a164-123">Určuje, že je aktualizace určena pro nástroj pro uživatelský rozsah.</span><span class="sxs-lookup"><span data-stu-id="2a164-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="2a164-124">Nelze kombinovat s možností `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="2a164-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="2a164-125">Vynechání `--global` a `--tool-path` určuje, že nástroj, který se má aktualizovat, je místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="2a164-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="2a164-126">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="2a164-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="2a164-127">Určuje umístění, kde je nainstalován globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="2a164-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="2a164-128">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="2a164-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="2a164-129">Nelze kombinovat s možností `--global`.</span><span class="sxs-lookup"><span data-stu-id="2a164-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="2a164-130">Vynechání `--global` a `--tool-path` určuje, že nástroj, který se má aktualizovat, je místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="2a164-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span> 

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="2a164-131">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="2a164-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2a164-132">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2a164-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="2a164-133">Příklady</span><span class="sxs-lookup"><span data-stu-id="2a164-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="2a164-134">Aktualizuje nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global.</span><span class="sxs-lookup"><span data-stu-id="2a164-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="2a164-135">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři Windows.</span><span class="sxs-lookup"><span data-stu-id="2a164-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="2a164-136">Aktualizuje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) umístěný v určitém adresáři Linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="2a164-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="2a164-137">Aktualizuje místní nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) nainstalovaný pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="2a164-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a164-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a164-138">See also</span></span>

- [<span data-ttu-id="2a164-139">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="2a164-139">.NET Core tools</span></span>](global-tools.md)
