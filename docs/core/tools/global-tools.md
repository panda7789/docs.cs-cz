---
title: Globální nástroje .NET core
description: Přehled o co jsou globální nástroje .NET Core a .NET Core CLI příkazy pro ně k dispozici.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 3bbf1e7953482dc07f05570443cf640a9fab6258
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170837"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="2bee3-103">Přehled globální nástroje .NET core</span><span class="sxs-lookup"><span data-stu-id="2bee3-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="2bee3-104">Globální nástroje .NET Core je speciální balíčku NuGet, který obsahuje konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2bee3-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="2bee3-105">Globální nástroj může být nainstalován na svém počítači na výchozím umístění, které je zahrnutý v proměnné prostředí PATH nebo vlastního umístění.</span><span class="sxs-lookup"><span data-stu-id="2bee3-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="2bee3-106">Pokud chcete použít globální nástroje .NET Core:</span><span class="sxs-lookup"><span data-stu-id="2bee3-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="2bee3-107">Najdete informace o nástroji (obvykle webu nebo stránku na Githubu).</span><span class="sxs-lookup"><span data-stu-id="2bee3-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="2bee3-108">Zkontrolujte Autor a statistické údaje ve Domovská stránka pro kanál (obvykle NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="2bee3-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="2bee3-109">Nainstalujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="2bee3-109">Install the tool.</span></span>
* <span data-ttu-id="2bee3-110">Volání nástroje.</span><span class="sxs-lookup"><span data-stu-id="2bee3-110">Call the tool.</span></span>
* <span data-ttu-id="2bee3-111">Aktualizujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="2bee3-111">Update the tool.</span></span>
* <span data-ttu-id="2bee3-112">Odinstalujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="2bee3-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2bee3-113">Globální nástroje .NET core se zobrazí na vaší cestě a spustit v režimu plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="2bee3-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="2bee3-114">Neinstalujte globální nástroje .NET Core, pokud důvěřujete autorovi.</span><span class="sxs-lookup"><span data-stu-id="2bee3-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="2bee3-115">Najít globální nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="2bee3-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="2bee3-116">V současné době není k dispozici funkce Hledat globální nástroje v rozhraní příkazového řádku .NET Core (CLI).</span><span class="sxs-lookup"><span data-stu-id="2bee3-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="2bee3-117">Globální nástroje .NET Core můžete najít na [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="2bee3-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="2bee3-118">Nicméně NuGet ještě neumožňuje vyhledávání speciálně pro globální nástroje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bee3-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="2bee3-119">Můžete také zjistit v příspěvcích na blogu nebo v doporučení v nástroji [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="2bee3-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="2bee3-120">Můžete také zobrazit zdrojový kód pro globální nástroje vytvořil tým ASP.NET na [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="2bee3-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="2bee3-121">Zkontrolujte Autor a statistiky</span><span class="sxs-lookup"><span data-stu-id="2bee3-121">Check the author and statistics</span></span>

<span data-ttu-id="2bee3-122">Protože globální nástroje .NET Core spustit v režimu plné důvěryhodnosti a se obvykle instaluje na vaší cestě, můžou být velmi výkonné.</span><span class="sxs-lookup"><span data-stu-id="2bee3-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="2bee3-123">Nestahovat nástroje od lidí, kterým nedůvěřujete.</span><span class="sxs-lookup"><span data-stu-id="2bee3-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="2bee3-124">Pokud je hostitelem nástroje NuGet, můžete zkontrolovat tak, že nástroj Autor a statistiky.</span><span class="sxs-lookup"><span data-stu-id="2bee3-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="2bee3-125">Nainstalujte nástroj Global</span><span class="sxs-lookup"><span data-stu-id="2bee3-125">Install a Global Tool</span></span>

<span data-ttu-id="2bee3-126">Instalovat nástroj globální, použijte [instalace nástrojů dotnet](dotnet-tool-install.md) rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bee3-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="2bee3-127">Následující příklad ukazuje, jak nainstalovat globální nástroj ve výchozím umístění:</span><span class="sxs-lookup"><span data-stu-id="2bee3-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="2bee3-128">Pokud nástroj nejde nainstalovat, zobrazí se chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="2bee3-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="2bee3-129">Zkontrolujte, že se kontroluje informační kanály, které jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="2bee3-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="2bee3-130">Pokud se snažíte nainstalovat předběžné verzi nebo konkrétní verzi nástroje, můžete zadat číslo verze v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="2bee3-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="2bee3-131">Pokud je instalace úspěšná, zobrazí se zpráva zobrazující příkazu používaný k volání nástroje a verze nainstalovaná, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2bee3-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="2bee3-132">Globální nástroje mohou být nainstalovány ve výchozím adresáři nebo v konkrétním umístění.</span><span class="sxs-lookup"><span data-stu-id="2bee3-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="2bee3-133">Výchozí adresáře jsou:</span><span class="sxs-lookup"><span data-stu-id="2bee3-133">The default directories are:</span></span>

| <span data-ttu-id="2bee3-134">Operační systém</span><span class="sxs-lookup"><span data-stu-id="2bee3-134">OS</span></span>          | <span data-ttu-id="2bee3-135">Cesta</span><span class="sxs-lookup"><span data-stu-id="2bee3-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="2bee3-136">Linux nebo macOS</span><span class="sxs-lookup"><span data-stu-id="2bee3-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="2bee3-137">Windows</span><span class="sxs-lookup"><span data-stu-id="2bee3-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="2bee3-138">Tato místa jsou přidány do cesty uživatele při prvním spuštění sady SDK, tak že nainstalované nástroje pro globální mohou být volány.</span><span class="sxs-lookup"><span data-stu-id="2bee3-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="2bee3-139">Mějte na paměti, že globální nástroje jsou specifické pro uživatele, počítače nejsou globální.</span><span class="sxs-lookup"><span data-stu-id="2bee3-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="2bee3-140">Jsou specifické pro uživatele znamená, že nemůžete nainstalovat globální nástroj, který je k dispozici pro všechny uživatele počítače.</span><span class="sxs-lookup"><span data-stu-id="2bee3-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="2bee3-141">Nástroj je k dispozici pouze pro každý uživatelský profil ve kterém byl nainstalován nástroj.</span><span class="sxs-lookup"><span data-stu-id="2bee3-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="2bee3-142">Globální nástroje můžete také nainstalovat v konkrétní adresář.</span><span class="sxs-lookup"><span data-stu-id="2bee3-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="2bee3-143">Při instalaci v konkrétní adresář, uživatel musí zajistit příkaz je k dispozici, včetně tohoto adresáře v cestě, voláním příkazu se do adresáře určeného, nebo zavolání nástroj v rámci zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="2bee3-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="2bee3-144">Rozhraní příkazového řádku .NET Core nepodporuje toto umístění v tomto případě automaticky přidat do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="2bee3-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="2bee3-145">Pomocí nástroje</span><span class="sxs-lookup"><span data-stu-id="2bee3-145">Use the tool</span></span>

<span data-ttu-id="2bee3-146">Po instalaci nástroje zavoláte ho pomocí jeho příkazu.</span><span class="sxs-lookup"><span data-stu-id="2bee3-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="2bee3-147">Všimněte si, že příkaz nemusí být stejný jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="2bee3-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="2bee3-148">Pokud je příkaz `dotnetsay`, při volání s:</span><span class="sxs-lookup"><span data-stu-id="2bee3-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="2bee3-149">Pokud autor nástroj chtěli nástroj, který se zobrazí v kontextu `dotnet` řádku, může mít napsat ji tak, pojmenujte ji `dotnet <command>`, jako například:</span><span class="sxs-lookup"><span data-stu-id="2bee3-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="2bee3-150">Zjistíte, jaké nástroje jsou součástí nainstalovaným balíčkem globální nástroj uvedením nainstalované balíčky pomocí [seznam nástrojů dotnet](dotnet-tool-list.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="2bee3-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="2bee3-151">Můžete také vyhledat pokyny k použití na webu nástroje nebo zadáním jednoho z následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="2bee3-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="2bee3-152">Co může dojít k chybě</span><span class="sxs-lookup"><span data-stu-id="2bee3-152">What could go wrong</span></span>

<span data-ttu-id="2bee3-153">Globální nástroje jsou [aplikace závisí na architektuře](../deploying/index.md#framework-dependent-deployments-fdd), což znamená, že spoléhají na .NET Core runtime na vašem počítači nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="2bee3-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="2bee3-154">Pokud se nenajde očekávanou dobu běhu, sledují běžných pravidel vpřed modulu runtime .NET Core, jako:</span><span class="sxs-lookup"><span data-stu-id="2bee3-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="2bee3-155">Aplikace provede dopředné obnovení nejvyšší oprava vydanou verzi zadaný hlavní verze a podverze.</span><span class="sxs-lookup"><span data-stu-id="2bee3-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="2bee3-156">Pokud není žádný odpovídající modul runtime s odpovídající hlavní a vedlejší číslo verze, použije se další vyšší dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="2bee3-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="2bee3-157">Posunutí vpřed nedojde mezi ve verzi preview verze modulu runtime nebo verze preview a verze.</span><span class="sxs-lookup"><span data-stu-id="2bee3-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="2bee3-158">Díky tomu se globální nástroje vytvořené pomocí verze preview musí být znovu sestavit a znovu publikovat autorem a přeinstalovat.</span><span class="sxs-lookup"><span data-stu-id="2bee3-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="2bee3-159">Další problémy mohou nastat u globální nástroje vytvořené v .NET Core 2.1 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="2bee3-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="2bee3-160">Další informace najdete v tématu [.NET Core 2.1 Preview 2 známé problémy v sadě](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="2bee3-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="2bee3-161">Pokud aplikaci nejde najít odpovídající modul runtime, selže-li a nahlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="2bee3-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="2bee3-162">Jiný problém, který může dojít, je, že globální nástroj, který byl vytvořen starší verzi Preview se možná nespustí pomocí aktuálně nainstalované moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bee3-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="2bee3-163">Můžete zobrazit, které moduly runtime jsou nainstalovány v počítači pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="2bee3-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="2bee3-164">Obraťte se na autora nástroj globální a podívejte se, pokud můžete znovu zkompilovat a znovu publikovat své nástroje balíček NuGet s aktualizovaným číslem verze.</span><span class="sxs-lookup"><span data-stu-id="2bee3-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="2bee3-165">Až aktualizováni balíček na webu NuGet můžete aktualizovat kopii.</span><span class="sxs-lookup"><span data-stu-id="2bee3-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="2bee3-166">Rozhraní příkazového řádku .NET Core se pokusí přidat výchozí umístění pro proměnné prostředí PATH na jeho prvního použití.</span><span class="sxs-lookup"><span data-stu-id="2bee3-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="2bee3-167">Existuje ale několik scénářů, kde umístění pravděpodobně být přidány do cesty automaticky, jako například:</span><span class="sxs-lookup"><span data-stu-id="2bee3-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="2bee3-168">Pokud jste nastavili `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="2bee3-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="2bee3-169">V systému macOS, pokud jste nainstalovali aplikaci pomocí sady .NET Core SDK *. tar.gz* souborů a nikoli *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="2bee3-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="2bee3-170">V systému Linux budete muset upravit soubor prostředí shell abyste nakonfigurovali CESTU.</span><span class="sxs-lookup"><span data-stu-id="2bee3-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="2bee3-171">Další příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2bee3-171">Other CLI commands</span></span>

<span data-ttu-id="2bee3-172">.NET Core SDK obsahuje další příkazy, které podporují globální nástroje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bee3-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="2bee3-173">Použít některý z `dotnet tool` příkazů s jedním z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="2bee3-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="2bee3-174">`--global` nebo `-g` Určuje, že příkaz je globální nástroje lze použít na úrovni uživatele.</span><span class="sxs-lookup"><span data-stu-id="2bee3-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="2bee3-175">`--tool-path` Určuje vlastní umístění pro globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="2bee3-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="2bee3-176">Chcete-li zjistit, které příkazy jsou k dispozici pro globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="2bee3-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="2bee3-177">Aktualizuje se nástroj globální zahrnuje odinstalace a opětovné instalace s nejnovější stabilní verzi.</span><span class="sxs-lookup"><span data-stu-id="2bee3-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="2bee3-178">Chcete-li aktualizovat globální nástroj, použijte [aktualizace nástrojů dotnet](dotnet-tool-update.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="2bee3-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="2bee3-179">Odebrat globální nástroj pomocí [dotnet odinstalační](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="2bee3-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="2bee3-180">Chcete-li zobrazit všechny nástroje, globální aktuálně nainstalované na počítači, spolu s jejich verzi a příkazů, použijte [seznam nástrojů dotnet](dotnet-tool-list.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="2bee3-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```