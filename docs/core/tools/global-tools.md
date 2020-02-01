---
title: Globální nástroje .NET Core
description: Přehled toho, jaké globální nástroje .NET Core jsou a jaké jsou .NET Core CLI příkazy, které jsou pro ně k dispozici.
author: KathleenDollard
ms.date: 05/29/2018
ms.openlocfilehash: 1531df48b7ca9c816b897d06e725ec375f6cae31
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920496"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="25f56-103">Přehled globálních nástrojů .NET Core</span><span class="sxs-lookup"><span data-stu-id="25f56-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="25f56-104">Globální nástroj .NET Core je speciální balíček NuGet, který obsahuje konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="25f56-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="25f56-105">Globální nástroj lze nainstalovat do počítače ve výchozím umístění, které je součástí proměnné prostředí PATH nebo ve vlastním umístění.</span><span class="sxs-lookup"><span data-stu-id="25f56-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="25f56-106">Pokud chcete použít globální nástroj .NET Core:</span><span class="sxs-lookup"><span data-stu-id="25f56-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="25f56-107">Vyhledejte informace o nástroji (obvykle stránka webu nebo GitHub).</span><span class="sxs-lookup"><span data-stu-id="25f56-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="25f56-108">Podívejte se na údaje o autorovi a statistice v domovském kanálu (obvykle NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="25f56-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="25f56-109">Nainstalujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="25f56-109">Install the tool.</span></span>
* <span data-ttu-id="25f56-110">Zavolejte nástroj.</span><span class="sxs-lookup"><span data-stu-id="25f56-110">Call the tool.</span></span>
* <span data-ttu-id="25f56-111">Aktualizujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="25f56-111">Update the tool.</span></span>
* <span data-ttu-id="25f56-112">Odinstalujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="25f56-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25f56-113">Globální nástroje .NET Core se zobrazí ve vaší cestě a spustí se v úplném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="25f56-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="25f56-114">Neinstalujte globální nástroje .NET Core, pokud nedůvěřujete autorovi.</span><span class="sxs-lookup"><span data-stu-id="25f56-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="25f56-115">Najít globální nástroj .NET Core</span><span class="sxs-lookup"><span data-stu-id="25f56-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="25f56-116">V současné době není k dispozici žádná funkce hledání globálních nástrojů v .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="25f56-116">Currently, there isn't a Global Tool search feature in the .NET Core CLI.</span></span> <span data-ttu-id="25f56-117">Níže jsou uvedená doporučení pro hledání nástrojů:</span><span class="sxs-lookup"><span data-stu-id="25f56-117">The following are some recommendations on how to find tools:</span></span>

* <span data-ttu-id="25f56-118">Globální nástroje .NET Core najdete na [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="25f56-118">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="25f56-119">NuGet ale ještě neumožňuje vyhledávat konkrétně globální nástroje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25f56-119">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>
* <span data-ttu-id="25f56-120">Doporučení k nástrojům můžete najít v blogovém příspěvku nebo v úložišti GitHubu [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .</span><span class="sxs-lookup"><span data-stu-id="25f56-120">You may find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="25f56-121">Zdrojový kód pro globální nástroje vytvořené týmem ASP.NET můžete zobrazit v úložišti GitHub [/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools) .</span><span class="sxs-lookup"><span data-stu-id="25f56-121">You can see the source code for the Global Tools created by the ASP.NET team at the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools) GitHub repository.</span></span>
* <span data-ttu-id="25f56-122">Informace o diagnostických nástrojích najdete v [části .NET Core dotnet – globální nástroje diagnostiky](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="25f56-122">You can learn about diagnostic tools at [.NET Core dotnet diagnostic Global Tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="25f56-123">Kontrolovat autora a statistiky</span><span class="sxs-lookup"><span data-stu-id="25f56-123">Check the author and statistics</span></span>

<span data-ttu-id="25f56-124">Vzhledem k tomu, že globální nástroje .NET Core běží v úplném vztahu důvěryhodnosti a jsou všeobecně nainstalované v cestě, můžou být velmi výkonné.</span><span class="sxs-lookup"><span data-stu-id="25f56-124">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="25f56-125">Nestahujte nástroje od lidí, kterým nedůvěřujete.</span><span class="sxs-lookup"><span data-stu-id="25f56-125">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="25f56-126">Pokud je nástroj hostovaný na NuGet, můžete si ho vyhledat pomocí hledání tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="25f56-126">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="25f56-127">Instalace globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="25f56-127">Install a Global Tool</span></span>

<span data-ttu-id="25f56-128">K instalaci globálního nástroje použijte příkaz [dotnet nástroje install](dotnet-tool-install.md) .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="25f56-128">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="25f56-129">Následující příklad ukazuje, jak nainstalovat globální nástroj ve výchozím umístění:</span><span class="sxs-lookup"><span data-stu-id="25f56-129">The following example shows how to install a Global Tool in the default location:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="25f56-130">Pokud nástroj není možné nainstalovat, zobrazí se chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="25f56-130">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="25f56-131">Ověřte, zda jsou kontrolovány informační kanály, které jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="25f56-131">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="25f56-132">Pokud se pokoušíte nainstalovat předběžnou verzi nebo konkrétní verzi nástroje, můžete číslo verze zadat v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="25f56-132">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="25f56-133">Pokud je instalace úspěšná, zobrazí se zpráva s příkazem použitým pro volání nástroje a nainstalované verze, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="25f56-133">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="25f56-134">Globální nástroje mohou být nainstalovány ve výchozím adresáři nebo v určitém umístění.</span><span class="sxs-lookup"><span data-stu-id="25f56-134">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="25f56-135">Výchozí adresáře jsou:</span><span class="sxs-lookup"><span data-stu-id="25f56-135">The default directories are:</span></span>

| <span data-ttu-id="25f56-136">OS</span><span class="sxs-lookup"><span data-stu-id="25f56-136">OS</span></span>          | <span data-ttu-id="25f56-137">Cesta</span><span class="sxs-lookup"><span data-stu-id="25f56-137">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="25f56-138">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="25f56-138">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="25f56-139">Windows</span><span class="sxs-lookup"><span data-stu-id="25f56-139">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="25f56-140">Tato umístění jsou přidána do cesty uživatele při prvním spuštění sady SDK, takže je možné nainstalovanou sadu globálních nástrojů volat přímo.</span><span class="sxs-lookup"><span data-stu-id="25f56-140">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="25f56-141">Všimněte si, že globální nástroje jsou specifické pro uživatele, ne jako globální počítač.</span><span class="sxs-lookup"><span data-stu-id="25f56-141">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="25f56-142">To znamená, že nemůžete nainstalovat globální nástroj, který je k dispozici pro všechny uživatele počítače.</span><span class="sxs-lookup"><span data-stu-id="25f56-142">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="25f56-143">Nástroj je k dispozici pouze pro každý profil uživatele, ve kterém byl nástroj nainstalován.</span><span class="sxs-lookup"><span data-stu-id="25f56-143">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="25f56-144">Globální nástroje je také možné nainstalovat do konkrétního adresáře.</span><span class="sxs-lookup"><span data-stu-id="25f56-144">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="25f56-145">Při instalaci do konkrétního adresáře musí uživatel ověřit, zda je příkaz k dispozici, zahrnutím tohoto adresáře do cesty, voláním příkazu se zadaným adresářem nebo voláním nástroje ze zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="25f56-145">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="25f56-146">V takovém případě .NET Core CLI nepřidá toto umístění automaticky do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="25f56-146">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="25f56-147">Použití nástroje</span><span class="sxs-lookup"><span data-stu-id="25f56-147">Use the tool</span></span>

<span data-ttu-id="25f56-148">Po instalaci nástroje jej můžete zavolat pomocí jeho příkazu.</span><span class="sxs-lookup"><span data-stu-id="25f56-148">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="25f56-149">Všimněte si, že tento příkaz nemůže být stejný jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="25f56-149">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="25f56-150">Pokud je příkaz `dotnetsay`, zavolejte ho pomocí:</span><span class="sxs-lookup"><span data-stu-id="25f56-150">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="25f56-151">Pokud autor nástroje chtěl zobrazit nástroj v kontextu `dotnet` výzvy, mohl by jej napsat způsobem, který ho zavolá jako `dotnet <command>`, například:</span><span class="sxs-lookup"><span data-stu-id="25f56-151">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="25f56-152">To, které nástroje jsou součástí nainstalovaného globálního balíčku nástroje, můžete najít tak, že zobrazíte nainstalované balíčky pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="25f56-152">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="25f56-153">Pokyny k použití můžete vyhledat také na webu nástroje nebo zadáním jednoho z následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="25f56-153">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a><span data-ttu-id="25f56-154">Další příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="25f56-154">Other CLI commands</span></span>

<span data-ttu-id="25f56-155">.NET Core SDK obsahuje další příkazy, které podporují globální nástroje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25f56-155">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="25f56-156">Použijte kterýkoli z `dotnet tool` příkazů s jednou z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="25f56-156">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="25f56-157">`--global` nebo `-g` určuje, že se příkaz vztahuje na globální nástroje pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="25f56-157">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="25f56-158">`--tool-path` určuje vlastní umístění pro globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="25f56-158">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="25f56-159">Zjistit, které příkazy jsou k dispozici pro globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="25f56-159">To find out which commands are available for Global Tools:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="25f56-160">Aktualizace globálního nástroje zahrnuje odinstalaci a opětovnou instalaci s nejnovější stabilní verzí.</span><span class="sxs-lookup"><span data-stu-id="25f56-160">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="25f56-161">Pokud chcete aktualizovat globální nástroj, použijte příkaz [dotnet nástroje Update](dotnet-tool-update.md) :</span><span class="sxs-lookup"><span data-stu-id="25f56-161">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```dotnetcli
dotnet tool update -g <packagename>
```

<span data-ttu-id="25f56-162">Odeberte globální nástroj pomocí [odinstalace nástroje dotnet](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="25f56-162">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```dotnetcli
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="25f56-163">Chcete-li zobrazit všechny globální nástroje, které jsou aktuálně nainstalovány v počítači, spolu s jejich verzí a příkazy, použijte příkaz pro [seznam nástrojů dotnet](dotnet-tool-list.md) :</span><span class="sxs-lookup"><span data-stu-id="25f56-163">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a><span data-ttu-id="25f56-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25f56-164">See also</span></span>

* [<span data-ttu-id="25f56-165">Řešení potíží s používáním nástrojů .NET Core</span><span class="sxs-lookup"><span data-stu-id="25f56-165">Troubleshoot .NET Core tool usage issues</span></span>](troubleshoot-usage-issues.md)
