---
title: příkaz dotnet nástroje pro odinstalaci
description: Příkaz pro odinstalaci nástroje dotnet odinstaluje zadaný nástroj .NET Core ze svého počítače.
ms.date: 02/14/2020
ms.openlocfilehash: 82dad0206d9c3e2ef0f41c353f4a608f10e4f127
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543440"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="8715e-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="8715e-103">dotnet tool uninstall</span></span>

<span data-ttu-id="8715e-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="8715e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8715e-105">Název</span><span class="sxs-lookup"><span data-stu-id="8715e-105">Name</span></span>

<span data-ttu-id="8715e-106">`dotnet tool uninstall` – odinstaluje zadaný [nástroj .NET Core](global-tools.md) ze svého počítače.</span><span class="sxs-lookup"><span data-stu-id="8715e-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8715e-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="8715e-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="8715e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="8715e-108">Description</span></span>

<span data-ttu-id="8715e-109">Příkaz `dotnet tool uninstall` poskytuje způsob, jak odinstalovat nástroje .NET Core z počítače.</span><span class="sxs-lookup"><span data-stu-id="8715e-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="8715e-110">Chcete-li použít příkaz, zadejte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="8715e-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="8715e-111">K odinstalaci globálního nástroje, který byl nainstalován ve výchozím umístění, použijte možnost `--global`.</span><span class="sxs-lookup"><span data-stu-id="8715e-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="8715e-112">K odinstalaci globálního nástroje, který byl nainstalován ve vlastním umístění, použijte možnost `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="8715e-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="8715e-113">Chcete-li odinstalovat místní nástroj, vynechejte možnosti `--global` a `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="8715e-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="8715e-114">**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**</span><span class="sxs-lookup"><span data-stu-id="8715e-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="8715e-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8715e-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="8715e-116">Název nebo ID balíčku NuGet, který obsahuje nástroj .NET Core, který se má odinstalovat</span><span class="sxs-lookup"><span data-stu-id="8715e-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="8715e-117">Název balíčku můžete najít pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="8715e-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="8715e-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="8715e-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="8715e-119">Určuje, že nástroj, který se má odebrat, pochází z instalace v rámci uživatele.</span><span class="sxs-lookup"><span data-stu-id="8715e-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="8715e-120">Nelze kombinovat s možností `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="8715e-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="8715e-121">Vynechání `--global` a `--tool-path` určuje, že nástroj, který má být odebrán, je místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="8715e-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="8715e-122">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="8715e-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="8715e-123">Určuje umístění pro odinstalaci nástroje.</span><span class="sxs-lookup"><span data-stu-id="8715e-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="8715e-124">Cesta může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="8715e-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="8715e-125">Nelze kombinovat s možností `--global`.</span><span class="sxs-lookup"><span data-stu-id="8715e-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="8715e-126">Vynechání `--global` a `--tool-path` určuje, že nástroj, který má být odebrán, je místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="8715e-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span> 

## <a name="examples"></a><span data-ttu-id="8715e-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="8715e-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="8715e-128">Odinstaluje nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global.</span><span class="sxs-lookup"><span data-stu-id="8715e-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="8715e-129">Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z určitého adresáře Windows.</span><span class="sxs-lookup"><span data-stu-id="8715e-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="8715e-130">Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z konkrétního adresáře Linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="8715e-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="8715e-131">Odinstaluje místní nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="8715e-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="8715e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8715e-132">See also</span></span>

- [<span data-ttu-id="8715e-133">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="8715e-133">.NET Core tools</span></span>](global-tools.md)
