---
title: .NET core globální nástroje
description: Přehled o jaké jsou .NET Core globální nástroje a příkazy .NET Core rozhraní příkazového řádku pro ně k dispozici.
author: KathleenDollard
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 077ffd53f1ba2988c80a637aaa109a66139736b0
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697089"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="1142a-103">Přehled .NET core globální nástroje</span><span class="sxs-lookup"><span data-stu-id="1142a-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="1142a-104">Nástroj globální .NET Core je speciální balíčku NuGet, který obsahuje aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="1142a-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="1142a-105">Nástroj globální může být nainstalovaný na počítači, na výchozí umístění, která je zahrnutá v proměnné prostředí PATH nebo do vlastního umístění.</span><span class="sxs-lookup"><span data-stu-id="1142a-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="1142a-106">Pokud chcete použít nástroj globální .NET Core:</span><span class="sxs-lookup"><span data-stu-id="1142a-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="1142a-107">Najdete informace o nástroji (obvykle web nebo GitHub stránce).</span><span class="sxs-lookup"><span data-stu-id="1142a-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="1142a-108">Zkontrolujte autora a statistiky na domovské stránce pro informační kanál (obvykle NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="1142a-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="1142a-109">Nainstalujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="1142a-109">Install the tool.</span></span>
* <span data-ttu-id="1142a-110">Volání nástroj.</span><span class="sxs-lookup"><span data-stu-id="1142a-110">Call the tool.</span></span>
* <span data-ttu-id="1142a-111">Aktualizujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="1142a-111">Update the tool.</span></span>
* <span data-ttu-id="1142a-112">Odinstalujte nástroj.</span><span class="sxs-lookup"><span data-stu-id="1142a-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1142a-113">.NET core globální nástroje se zobrazují v cestu a spustit v režimu plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="1142a-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="1142a-114">.NET Core globální nástroje nainstalujte pouze v případě, že důvěřujete autorovi.</span><span class="sxs-lookup"><span data-stu-id="1142a-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="1142a-115">Najít nástroj globální .NET Core</span><span class="sxs-lookup"><span data-stu-id="1142a-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="1142a-116">V současné době není k dispozici funkce vyhledávání globální nástroj v rozhraní .NET Core rozhraní příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="1142a-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="1142a-117">.NET Core globální nástroje můžete najít na [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="1142a-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="1142a-118">Ale NuGet ještě neumožňuje prohledat speciálně pro .NET Core globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="1142a-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="1142a-119">Také je možné nástroj doporučení v příspěvcích na blogu nebo v [natemcmaster/dotnet nástroje](https://github.com/natemcmaster/dotnet-tools) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="1142a-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="1142a-120">Můžete také najdete ve zdrojovém kódu pro globální nástroje vytvořený týmem ASP.NET na [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="1142a-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="1142a-121">Zkontrolujte autora a statistiky</span><span class="sxs-lookup"><span data-stu-id="1142a-121">Check the author and statistics</span></span>

<span data-ttu-id="1142a-122">Vzhledem k tomu, že .NET Core globální nástroje spustit v režimu plné důvěryhodnosti a jsou obvykle instaluje na cestu, mohou být velmi mocné.</span><span class="sxs-lookup"><span data-stu-id="1142a-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="1142a-123">Nestahovat nástroje před lidmi, kterým nedůvěřujete.</span><span class="sxs-lookup"><span data-stu-id="1142a-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="1142a-124">Pokud tento nástroj je hostovaná na NuGet, můžete zkontrolovat jejich autorovi a statistiky tak, že nástroj.</span><span class="sxs-lookup"><span data-stu-id="1142a-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="1142a-125">Nainstalujte nástroj globální</span><span class="sxs-lookup"><span data-stu-id="1142a-125">Install a Global Tool</span></span>

<span data-ttu-id="1142a-126">Chcete-li nainstalovat nástroj globální, je použít [instalace nástroje pro dotnet](dotnet-tool-install.md) .NET Core rozhraní příkazového řádku příkaz.</span><span class="sxs-lookup"><span data-stu-id="1142a-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="1142a-127">Následující příklad ukazuje, jak nainstalovat nástroj globální ve výchozím umístění:</span><span class="sxs-lookup"><span data-stu-id="1142a-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="1142a-128">Pokud nástroj nelze nainstalovat, zobrazí se chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="1142a-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="1142a-129">Zkontrolujte, jsou kontrolovány informační kanály, které jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="1142a-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="1142a-130">Pokud se pokoušíte nainstalovat předběžné verze nebo na konkrétní verzi nástroje, můžete zadat číslo verze v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="1142a-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="1142a-131">Pokud je instalace úspěšná, zobrazí se zpráva zobrazující příkaz používá k volání nástroj od verze nainstalované, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1142a-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="1142a-132">Ve výchozím adresáři nebo v konkrétní umístění může být nainstalované nástroje globální.</span><span class="sxs-lookup"><span data-stu-id="1142a-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="1142a-133">Výchozí adresáře jsou:</span><span class="sxs-lookup"><span data-stu-id="1142a-133">The default directories are:</span></span>

| <span data-ttu-id="1142a-134">OPERAČNÍ SYSTÉM</span><span class="sxs-lookup"><span data-stu-id="1142a-134">OS</span></span>          | <span data-ttu-id="1142a-135">Cesta</span><span class="sxs-lookup"><span data-stu-id="1142a-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="1142a-136">Linux/systému macOS</span><span class="sxs-lookup"><span data-stu-id="1142a-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="1142a-137">Windows</span><span class="sxs-lookup"><span data-stu-id="1142a-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="1142a-138">Tato umístění se přidají do cesty uživatele při prvním spuštění sady SDK, takže globální nástroje nainstalované existuje můžete volat přímo.</span><span class="sxs-lookup"><span data-stu-id="1142a-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="1142a-139">Upozorňujeme, že globální nástroje jsou specifické pro uživatele, není ve stavu globální.</span><span class="sxs-lookup"><span data-stu-id="1142a-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="1142a-140">Probíhá specifický pro uživatele znamená, že nemůžete nainstalovat nástroj globální, který je k dispozici pro všechny uživatele počítače.</span><span class="sxs-lookup"><span data-stu-id="1142a-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="1142a-141">Nástroj je k dispozici pouze pro každý uživatelský profil nainstalovanou nástroj.</span><span class="sxs-lookup"><span data-stu-id="1142a-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="1142a-142">Globální nástroje lze také nainstalovat v konkrétní adresář.</span><span class="sxs-lookup"><span data-stu-id="1142a-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="1142a-143">Při instalaci v konkrétního adresáře, musí se uživatel ujistit příkaz je k dispozici, včetně adresáře v cestě, voláním příkazu se adresář zadaný, nebo volání nástroj v rámci zadaného adresáře.</span><span class="sxs-lookup"><span data-stu-id="1142a-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="1142a-144">Rozhraní příkazového řádku .NET Core není toto umístění v tomto případě automaticky přidat do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="1142a-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="1142a-145">Pomocí nástroje</span><span class="sxs-lookup"><span data-stu-id="1142a-145">Use the tool</span></span>

<span data-ttu-id="1142a-146">Po instalaci nástroje ho můžete volat pomocí jeho příkazu.</span><span class="sxs-lookup"><span data-stu-id="1142a-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="1142a-147">Všimněte si, že příkaz nemusí být stejný jako název balíčku.</span><span class="sxs-lookup"><span data-stu-id="1142a-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="1142a-148">Pokud je příkaz `dotnetsay`, její volání:</span><span class="sxs-lookup"><span data-stu-id="1142a-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="1142a-149">Pokud nástroj Autor chtěli nástroj, který se zobrazí v kontextu `dotnet` řádku, může uživatel vytvořil ho způsobem volání jej jako `dotnet <command>`, jako například:</span><span class="sxs-lookup"><span data-stu-id="1142a-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="1142a-150">Zjistíte, které nástroje jsou součástí nainstalovaným balíčkem globální nástroj tak, že uvedete nainstalované balíčky pomocí [seznam nástrojů dotnet](dotnet-tool-list.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="1142a-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="1142a-151">Můžete také vyhledat pokyny k použití na webu nástroje nebo zadáním jednoho z následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="1142a-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="1142a-152">Co může dojít k chybě</span><span class="sxs-lookup"><span data-stu-id="1142a-152">What could go wrong</span></span>

<span data-ttu-id="1142a-153">Globální nástroje jsou [framework závislé aplikace,](../deploying/index.md#framework-dependent-deployments-fdd), což znamená, že spoléhají na .NET Core runtime v počítači nainstalován.</span><span class="sxs-lookup"><span data-stu-id="1142a-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="1142a-154">Pokud není nalezen očekávaný modulu runtime, se řídí normální .NET Core runtime úplné dopředné pravidla jako:</span><span class="sxs-lookup"><span data-stu-id="1142a-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="1142a-155">Aplikace posunete na nejvyšší verzi opravy systému zadaná verze hlavní a podverze.</span><span class="sxs-lookup"><span data-stu-id="1142a-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="1142a-156">Pokud neexistuje žádný odpovídající runtime s odpovídající hlavní a podverze číslo, použije se další vyšší podverze.</span><span class="sxs-lookup"><span data-stu-id="1142a-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="1142a-157">Dopředné posunutí nedojde mezi verze preview modulu runtime nebo mezi verze preview a verze.</span><span class="sxs-lookup"><span data-stu-id="1142a-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="1142a-158">Proto globální nástroje, které jsou vytvořené pomocí verze preview musí být znovu sestavit a publikovat autorem a přeinstalovat.</span><span class="sxs-lookup"><span data-stu-id="1142a-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="1142a-159">Další problémy mohou nastat u globální nástrojů vytvořené v rozhraní .NET Core 2.1 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="1142a-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="1142a-160">Další informace najdete v tématu [.NET Core 2.1 Preview 2 – známé problémy s](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="1142a-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="1142a-161">Pokud aplikace nemůže najít vhodné modulu runtime, se nezdaří a zobrazí chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="1142a-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="1142a-162">Jiný problém, který může dojít, je, že globální nástroj, který jste vytvořili během starší verze preview nemusí s vaší aktuálně nainstalované moduly runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1142a-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="1142a-163">Můžete zjistit, jaké moduly runtime jsou nainstalovány na počítači, pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="1142a-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="1142a-164">Obraťte se na autora nástroj globální a zda lze znovu zkompiluje a znovu publikovat své nástroj balíček NuGet s číslem aktualizovaná verze.</span><span class="sxs-lookup"><span data-stu-id="1142a-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="1142a-165">Jakmile budou mít aktualizovat balíček na NuGet, můžete aktualizovat svou kopii.</span><span class="sxs-lookup"><span data-stu-id="1142a-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="1142a-166">Rozhraní příkazového řádku .NET Core se pokusí přidat výchozí umístění do proměnné prostředí PATH na jeho první použití.</span><span class="sxs-lookup"><span data-stu-id="1142a-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="1142a-167">Existuje však několik scénářů, kde umístění nemusí být přidat cestu automaticky, jako například:</span><span class="sxs-lookup"><span data-stu-id="1142a-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="1142a-168">Pokud jste nastavili `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="1142a-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="1142a-169">V systému macOS, pokud jste nainstalovali pomocí rozhraní .NET Core SDK *. tar.gz* soubory a zda není *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="1142a-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="1142a-170">V systému Linux musíte upravit soubor prostředí shell můžete nastavit CESTU.</span><span class="sxs-lookup"><span data-stu-id="1142a-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="1142a-171">Další příkazy rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="1142a-171">Other CLI commands</span></span>

<span data-ttu-id="1142a-172">.NET Core SDK obsahuje jinými příkazy, které podporují .NET Core globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="1142a-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="1142a-173">Použít některou z `dotnet tool` příkazy s jedním z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="1142a-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="1142a-174">`--global` nebo `-g` Určuje, že příkaz se vztahuje na úrovni uživatele globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="1142a-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="1142a-175">`--tool-path` Určuje vlastní umístění pro globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="1142a-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="1142a-176">Chcete-li zjistit, které příkazy, které jsou k dispozici pro globální nástroje:</span><span class="sxs-lookup"><span data-stu-id="1142a-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="1142a-177">Aktualizace nástroj globální zahrnuje odinstalace a opětovné instalace s nejnovější stabilní verze.</span><span class="sxs-lookup"><span data-stu-id="1142a-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="1142a-178">Chcete-li aktualizovat nástroj globální, použijte [aktualizace nástrojů dotnet](dotnet-tool-update.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="1142a-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="1142a-179">Odeberte nástroj globální pomocí [dotnet odinstalační](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="1142a-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="1142a-180">Zobrazit všechny nástroje globální aktuálně nainstalovaný v počítači, spolu s jejich verzi a příkazy, pomocí [seznam nástrojů dotnet](dotnet-tool-list.md) příkaz:</span><span class="sxs-lookup"><span data-stu-id="1142a-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```