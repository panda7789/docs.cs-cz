---
title: Globální nástroje .NET Core
description: Přehled toho, jaké globální nástroje .NET Core jsou a jaké jsou .NET Core CLI příkazy, které jsou pro ně k dispozici.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 01c1463ceddcd64e5bab05b95a5ae4a91b6da838
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117458"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="2ee5c-103">Přehled globálních nástrojů .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ee5c-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="2ee5c-104">Globální nástroj .NET Core je speciální balíček NuGet, který obsahuje konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="2ee5c-105">Globální nástroj lze nainstalovat do počítače ve výchozím umístění, které je součástí proměnné prostředí PATH nebo ve vlastním umístění.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="2ee5c-106">Pokud chcete použít globální nástroj .NET Core:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="2ee5c-107">Vyhledejte informace o nástroji (obvykle stránka webu nebo GitHub).</span><span class="sxs-lookup"><span data-stu-id="2ee5c-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="2ee5c-108">Podívejte se na údaje o autorovi a statistice v domovském kanálu (obvykle NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="2ee5c-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="2ee5c-109">Nainstalujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-109">Install the tool.</span></span>
* <span data-ttu-id="2ee5c-110">Zavolejte nástroj.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-110">Call the tool.</span></span>
* <span data-ttu-id="2ee5c-111">Aktualizujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-111">Update the tool.</span></span>
* <span data-ttu-id="2ee5c-112">Odinstalujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ee5c-113">Globální nástroje .NET Core se zobrazí ve vaší cestě a spustí se v úplném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="2ee5c-114">Neinstalujte globální nástroje .NET Core, pokud nedůvěřujete autorovi.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="2ee5c-115">Najít globální nástroj .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ee5c-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="2ee5c-116">V současné době není v rozhraní příkazového řádku (CLI) .NET Core k dispozici funkce pro vyhledávání globálních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="2ee5c-117">Globální nástroje .NET Core najdete na [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="2ee5c-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="2ee5c-118">NuGet ale ještě neumožňuje vyhledávat konkrétně globální nástroje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="2ee5c-119">Doporučení k nástrojům můžete najít také v blogu blogové příspěvky nebo v úložišti GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .</span><span class="sxs-lookup"><span data-stu-id="2ee5c-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="2ee5c-120">Zdrojový kód globálních nástrojů, které vytvořil tým ASP.NET, můžete zobrazit také v úložišti GitHub [/DotNetTools](https://github.com/aspnet/DotNetTools/) .</span><span class="sxs-lookup"><span data-stu-id="2ee5c-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="2ee5c-121">Kontrolovat autora a statistiky</span><span class="sxs-lookup"><span data-stu-id="2ee5c-121">Check the author and statistics</span></span>

<span data-ttu-id="2ee5c-122">Vzhledem k tomu, že globální nástroje .NET Core běží v úplném vztahu důvěryhodnosti a jsou všeobecně nainstalované v cestě, můžou být velmi výkonné.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="2ee5c-123">Nestahujte nástroje od lidí, kterým nedůvěřujete.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="2ee5c-124">Pokud je nástroj hostovaný na NuGet, můžete si ho vyhledat pomocí hledání tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="2ee5c-125">Instalace globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="2ee5c-125">Install a Global Tool</span></span>

<span data-ttu-id="2ee5c-126">K instalaci globálního nástroje použijte příkaz [dotnet nástroje install](dotnet-tool-install.md) .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="2ee5c-127">Následující příklad ukazuje, jak nainstalovat globální nástroj ve výchozím umístění:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-127">The following example shows how to install a Global Tool in the default location:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="2ee5c-128">Pokud nástroj není možné nainstalovat, zobrazí se chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="2ee5c-129">Ověřte, zda jsou kontrolovány informační kanály, které jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="2ee5c-130">Pokud se pokoušíte nainstalovat předběžnou verzi nebo konkrétní verzi nástroje, můžete číslo verze zadat v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="2ee5c-131">Pokud je instalace úspěšná, zobrazí se zpráva s příkazem použitým pro volání nástroje a nainstalované verze, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="2ee5c-132">Globální nástroje mohou být nainstalovány ve výchozím adresáři nebo v určitém umístění.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="2ee5c-133">Výchozí adresáře jsou:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-133">The default directories are:</span></span>

| <span data-ttu-id="2ee5c-134">OS</span><span class="sxs-lookup"><span data-stu-id="2ee5c-134">OS</span></span>          | <span data-ttu-id="2ee5c-135">Cesta</span><span class="sxs-lookup"><span data-stu-id="2ee5c-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="2ee5c-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="2ee5c-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="2ee5c-137">Windows</span><span class="sxs-lookup"><span data-stu-id="2ee5c-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="2ee5c-138">Tato umístění jsou přidána do cesty uživatele při prvním spuštění sady SDK, takže je možné nainstalovanou sadu globálních nástrojů volat přímo.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="2ee5c-139">Všimněte si, že globální nástroje jsou specifické pro uživatele, ne jako globální počítač.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="2ee5c-140">To znamená, že nemůžete nainstalovat globální nástroj, který je k dispozici pro všechny uživatele počítače.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="2ee5c-141">Nástroj je k dispozici pouze pro každý profil uživatele, ve kterém byl nástroj nainstalován.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="2ee5c-142">Globální nástroje je také možné nainstalovat do konkrétního adresáře.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="2ee5c-143">Při instalaci do konkrétního adresáře musí uživatel ověřit, zda je příkaz k dispozici, zahrnutím tohoto adresáře do cesty, voláním příkazu se zadaným adresářem nebo voláním nástroje ze zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="2ee5c-144">V takovém případě .NET Core CLI nepřidá toto umístění automaticky do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="2ee5c-145">Použití nástroje</span><span class="sxs-lookup"><span data-stu-id="2ee5c-145">Use the tool</span></span>

<span data-ttu-id="2ee5c-146">Po instalaci nástroje jej můžete zavolat pomocí jeho příkazu.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="2ee5c-147">Všimněte si, že tento příkaz nemůže být stejný jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="2ee5c-148">Pokud je `dotnetsay`příkaz, zavolejte ho s:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="2ee5c-149">Pokud autor nástroje chtěl, aby se nástroj objevil v kontextu `dotnet` výzvy, mohl by ho napsat způsobem, který ho zavolá, jako `dotnet <command>`například:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="2ee5c-150">To, které nástroje jsou součástí nainstalovaného globálního balíčku nástroje, můžete najít tak, že zobrazíte nainstalované balíčky pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="2ee5c-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="2ee5c-151">Pokyny k použití můžete vyhledat také na webu nástroje nebo zadáním jednoho z následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="2ee5c-152">Co by mohlo jít špatně</span><span class="sxs-lookup"><span data-stu-id="2ee5c-152">What could go wrong</span></span>

<span data-ttu-id="2ee5c-153">Globální nástroje jsou [závislé na architektuře](../deploying/index.md#framework-dependent-deployments-fdd), což znamená, že spoléhají na modul runtime .NET Core nainstalovaný na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="2ee5c-154">Pokud se očekávaný modul runtime nenajde, dodržuje normální pravidla předávaných modulem runtime .NET Core, jako například:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="2ee5c-155">Aplikace se vrátí k nejvyšší verzi opravy zadané hlavní a dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="2ee5c-156">Pokud neexistuje žádný vyhovující modul runtime se shodným číslem hlavní verze a podverze, použije se další vyšší dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="2ee5c-157">Mezi verzemi verze Preview modulu runtime nebo verzí Preview a verzí verze Preview nedochází k posunutí.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="2ee5c-158">Proto musí být globální nástroje vytvořené pomocí verze Preview znovu sestaveny a znovu publikovány autorem a opětovnou instalací.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="2ee5c-159">U globálních nástrojů vytvořených v rozhraní .NET Core 2,1 Preview 1 se můžou vyskytovat další problémy.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="2ee5c-160">Další informace najdete v tématu [známé problémy pro .NET Core 2,1 Preview 2](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5c-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="2ee5c-161">Pokud aplikace nemůže najít vhodný modul runtime, spuštění se nespustí a ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="2ee5c-162">Dalším problémem, ke kterému může dojít, je, že globální nástroj, který byl vytvořen v dřívější verzi Preview, nemusí běžet s aktuálně nainstalovanými moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="2ee5c-163">To, které moduly runtime jsou nainstalovány na počítači, můžete zjistit pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="2ee5c-164">Kontaktujte autora globálního nástroje a podívejte se, jestli můžou znovu kompilovat a znovu publikovat svůj balíček nástrojů do NuGet s aktualizovaným číslem verze.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="2ee5c-165">Po aktualizaci balíčku na NuGet můžete kopii aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="2ee5c-166">.NET Core CLI se pokusí přidat výchozí umístění do proměnné prostředí PATH při prvním použití.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="2ee5c-167">Existuje však několik scénářů, kde umístění nemusí být přidáno do cesty automaticky, například:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="2ee5c-168">Pokud jste nastavili `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="2ee5c-169">V macOS, pokud jste nainstalovali .NET Core SDK pomocí souborů *. tar. gz* a NOT *. pkg*.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="2ee5c-170">V systému Linux je potřeba upravit soubor prostředí prostředí a nakonfigurovat cestu.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="2ee5c-171">Další příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2ee5c-171">Other CLI commands</span></span>

<span data-ttu-id="2ee5c-172">.NET Core SDK obsahuje další příkazy, které podporují globální nástroje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="2ee5c-173">Použijte libovolný z `dotnet tool` těchto příkazů s jednou z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="2ee5c-174">`--global`nebo `-g` určuje, že se příkaz vztahuje na globální nástroje pro všechny uživatele.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="2ee5c-175">`--tool-path`Určuje vlastní umístění pro globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="2ee5c-176">Zjistit, které příkazy jsou k dispozici pro globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="2ee5c-176">To find out which commands are available for Global Tools:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="2ee5c-177">Aktualizace globálního nástroje zahrnuje odinstalaci a opětovnou instalaci s nejnovější stabilní verzí.</span><span class="sxs-lookup"><span data-stu-id="2ee5c-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="2ee5c-178">Pokud chcete aktualizovat globální nástroj, použijte příkaz [dotnet nástroje Update](dotnet-tool-update.md) :</span><span class="sxs-lookup"><span data-stu-id="2ee5c-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```dotnetcli
dotnet tool update -g <packagename>
```

<span data-ttu-id="2ee5c-179">Odeberte globální nástroj pomocí [odinstalace nástroje dotnet](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="2ee5c-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```dotnetcli
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="2ee5c-180">Chcete-li zobrazit všechny globální nástroje, které jsou aktuálně nainstalovány v počítači, spolu s jejich verzí a příkazy, použijte příkaz pro [seznam nástrojů dotnet](dotnet-tool-list.md) :</span><span class="sxs-lookup"><span data-stu-id="2ee5c-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list -g
```
