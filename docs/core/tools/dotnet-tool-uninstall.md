---
title: Příkaz odinstalovat nástroj dotnet
description: Příkaz odinstalace nástroje dotnet odinstaluje zadaný nástroj .NET Core z vašeho počítače.
ms.date: 02/14/2020
ms.openlocfilehash: 0416f91019a49e17f1be14a1d928ad1fafaa736c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463315"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="aec4f-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="aec4f-103">dotnet tool uninstall</span></span>

<span data-ttu-id="aec4f-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="aec4f-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="aec4f-105">Název</span><span class="sxs-lookup"><span data-stu-id="aec4f-105">Name</span></span>

<span data-ttu-id="aec4f-106">`dotnet tool uninstall`- Odinstaluje zadaný [nástroj .NET Core](global-tools.md) z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="aec4f-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="aec4f-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="aec4f-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a><span data-ttu-id="aec4f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="aec4f-108">Description</span></span>

<span data-ttu-id="aec4f-109">Příkaz `dotnet tool uninstall` umožňuje odinstalovat nástroje .NET Core ze zařízení.</span><span class="sxs-lookup"><span data-stu-id="aec4f-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="aec4f-110">Chcete-li použít příkaz, zadejte jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="aec4f-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="aec4f-111">Chcete-li odinstalovat globální nástroj, který byl `--global` nainstalován ve výchozím umístění, použijte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="aec4f-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="aec4f-112">Chcete-li odinstalovat globální nástroj, který byl `--tool-path` nainstalován ve vlastním umístění, použijte tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="aec4f-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="aec4f-113">Chcete-li odinstalovat místní nástroj, `--global` `--tool-path` vynechte možnosti a.</span><span class="sxs-lookup"><span data-stu-id="aec4f-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="aec4f-114">**Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="aec4f-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="aec4f-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="aec4f-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="aec4f-116">Název/ID balíčku NuGet, který obsahuje nástroj .NET Core k odinstalaci.</span><span class="sxs-lookup"><span data-stu-id="aec4f-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="aec4f-117">Název balíčku můžete najít pomocí příkazu [seznamu nástrojů dotnet.](dotnet-tool-list.md)</span><span class="sxs-lookup"><span data-stu-id="aec4f-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="aec4f-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="aec4f-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="aec4f-119">Určuje, že nástroj, který má být odebrán, pochází z instalace pro celý uživatel.</span><span class="sxs-lookup"><span data-stu-id="aec4f-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="aec4f-120">Nelze kombinovat s `--tool-path` možností.</span><span class="sxs-lookup"><span data-stu-id="aec4f-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="aec4f-121">Vynechání obou `--global` `--tool-path` a určuje, že nástroj, který má být odebrán, je místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="aec4f-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="aec4f-122">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="aec4f-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="aec4f-123">Určuje umístění, kam chcete nástroj odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="aec4f-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="aec4f-124">CESTA může být absolutní nebo relativní.</span><span class="sxs-lookup"><span data-stu-id="aec4f-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="aec4f-125">Nelze kombinovat s `--global` možností.</span><span class="sxs-lookup"><span data-stu-id="aec4f-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="aec4f-126">Vynechání obou `--global` `--tool-path` a určuje, že nástroj, který má být odebrán, je místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="aec4f-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="aec4f-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="aec4f-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="aec4f-128">Odinstaluje globální nástroj [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)</span><span class="sxs-lookup"><span data-stu-id="aec4f-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="aec4f-129">Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z konkrétního adresáře systému Windows.</span><span class="sxs-lookup"><span data-stu-id="aec4f-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="aec4f-130">Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z konkrétního adresáře Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="aec4f-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="aec4f-131">Odinstaluje místní nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="aec4f-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="aec4f-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="aec4f-132">See also</span></span>

- [<span data-ttu-id="aec4f-133">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="aec4f-133">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="aec4f-134">Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="aec4f-134">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="aec4f-135">Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="aec4f-135">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
