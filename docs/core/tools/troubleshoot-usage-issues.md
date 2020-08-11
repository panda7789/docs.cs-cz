---
title: Řešení potíží s používáním nástrojů .NET Core
description: Seznamte se s běžnými problémy při používání nástrojů .NET Core a možných řešení.
author: kdollard
ms.topic: troubleshooting
ms.date: 02/14/2020
ms.openlocfilehash: b98b2735770c8259c2daf94575fc087b91bb61fd
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062633"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="5bb21-103">Řešení potíží s používáním nástrojů .NET Core</span><span class="sxs-lookup"><span data-stu-id="5bb21-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="5bb21-104">Při pokusu o instalaci nebo spuštění nástroje .NET Core, který může být globálním nástrojem nebo místním nástrojem, může docházet k problémům.</span><span class="sxs-lookup"><span data-stu-id="5bb21-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="5bb21-105">Tento článek popisuje běžné hlavní příčiny a některá možná řešení.</span><span class="sxs-lookup"><span data-stu-id="5bb21-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="5bb21-106">Nepodařilo se spustit nainstalovaný nástroj .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb21-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="5bb21-107">Když se nepovede spustit nástroj .NET Core, pravděpodobně došlo k jednomu z následujících problémů:</span><span class="sxs-lookup"><span data-stu-id="5bb21-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="5bb21-108">Spustitelný soubor pro nástroj se nenašel.</span><span class="sxs-lookup"><span data-stu-id="5bb21-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="5bb21-109">Nenašla se správná verze modulu runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb21-109">The correct version of the .NET Core runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="5bb21-110">Spustitelný soubor se nenašel.</span><span class="sxs-lookup"><span data-stu-id="5bb21-110">Executable file not found</span></span>

<span data-ttu-id="5bb21-111">Pokud se spustitelný soubor nenajde, zobrazí se zpráva podobná následující:</span><span class="sxs-lookup"><span data-stu-id="5bb21-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="5bb21-112">Název spustitelného souboru určuje způsob, jakým se nástroj vyvolá.</span><span class="sxs-lookup"><span data-stu-id="5bb21-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="5bb21-113">Následující tabulka popisuje formát:</span><span class="sxs-lookup"><span data-stu-id="5bb21-113">The following table describes the format:</span></span>

| <span data-ttu-id="5bb21-114">Formát názvu spustitelného souboru</span><span class="sxs-lookup"><span data-stu-id="5bb21-114">Executable name format</span></span>  | <span data-ttu-id="5bb21-115">Formát vyvolání</span><span class="sxs-lookup"><span data-stu-id="5bb21-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="5bb21-116">Globální nástroje</span><span class="sxs-lookup"><span data-stu-id="5bb21-116">Global tools</span></span>

  <span data-ttu-id="5bb21-117">Globální nástroje mohou být nainstalovány ve výchozím adresáři nebo v určitém umístění.</span><span class="sxs-lookup"><span data-stu-id="5bb21-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="5bb21-118">Výchozí adresáře jsou:</span><span class="sxs-lookup"><span data-stu-id="5bb21-118">The default directories are:</span></span>

  | <span data-ttu-id="5bb21-119">Operační systém</span><span class="sxs-lookup"><span data-stu-id="5bb21-119">OS</span></span>          | <span data-ttu-id="5bb21-120">Cesta</span><span class="sxs-lookup"><span data-stu-id="5bb21-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="5bb21-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="5bb21-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="5bb21-122">Windows</span><span class="sxs-lookup"><span data-stu-id="5bb21-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="5bb21-123">Pokud se pokoušíte spustit globální nástroj, ověřte, že `PATH` Proměnná prostředí na vašem počítači obsahuje cestu, kam jste nainstalovali globální nástroj a že je spustitelný soubor v této cestě.</span><span class="sxs-lookup"><span data-stu-id="5bb21-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="5bb21-124">.NET Core CLI se pokusí přidat výchozí umístění do proměnné prostředí PATH při prvním použití.</span><span class="sxs-lookup"><span data-stu-id="5bb21-124">The .NET Core CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="5bb21-125">Existují však situace, kdy není možné do cesty automaticky přidat umístění:</span><span class="sxs-lookup"><span data-stu-id="5bb21-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="5bb21-126">Pokud používáte Linux a nainstalujete .NET Core SDK pomocí souborů *. tar. gz* , a ne apt-get nebo ot/min.</span><span class="sxs-lookup"><span data-stu-id="5bb21-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="5bb21-127">Pokud používáte macOS 10,15 "Catalina" nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="5bb21-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="5bb21-128">Pokud používáte macOS 10,14 "Mojave" nebo starší verze a nainstalovali jste .NET Core SDK pomocí souborů *. tar. gz* , a ne *. pkg*.</span><span class="sxs-lookup"><span data-stu-id="5bb21-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="5bb21-129">Pokud jste nainstalovali sadu .NET Core 3,0 SDK a nastavili jste `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` proměnnou prostředí na `false` .</span><span class="sxs-lookup"><span data-stu-id="5bb21-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="5bb21-130">Pokud jste nainstalovali sadu .NET Core 2,2 SDK nebo starší verze a nastavili jste `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` proměnnou prostředí na `true` .</span><span class="sxs-lookup"><span data-stu-id="5bb21-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="5bb21-131">V těchto scénářích nebo pokud jste zadali `--tool-path` možnost, `PATH` Proměnná prostředí na vašem počítači automaticky nezahrnuje cestu, do které jste nainstalovali globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="5bb21-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="5bb21-132">V takovém případě připojíte umístění nástroje (například `$HOME/.dotnet/tools` ) k `PATH` proměnné prostředí pomocí libovolné metody, kterou vaše prostředí nabízí pro aktualizaci proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="5bb21-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="5bb21-133">Další informace najdete v tématu [nástroje .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5bb21-133">For more information, see [.NET Core tools](global-tools.md).</span></span>

* <span data-ttu-id="5bb21-134">Místní nástroje</span><span class="sxs-lookup"><span data-stu-id="5bb21-134">Local tools</span></span>

  <span data-ttu-id="5bb21-135">Pokud se pokoušíte spustit místní nástroj, ověřte, zda je v aktuálním adresáři nebo v některém z jeho nadřazených adresářů k dispozici soubor manifestu s názvem *dotnet-tools.js* .</span><span class="sxs-lookup"><span data-stu-id="5bb21-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="5bb21-136">Tento soubor může být také živý v rámci složky s názvem *. config* kdekoli v hierarchii složek projektu místo kořenové složky.</span><span class="sxs-lookup"><span data-stu-id="5bb21-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="5bb21-137">Pokud *dotnet-tools.js* existuje, otevřete ho a vyhledejte nástroj, který se pokoušíte spustit.</span><span class="sxs-lookup"><span data-stu-id="5bb21-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="5bb21-138">Pokud soubor neobsahuje položku pro `"isRoot": true` , zkontrolujte také hierarchii souborů pro další soubory manifestu nástroje.</span><span class="sxs-lookup"><span data-stu-id="5bb21-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="5bb21-139">Pokud se pokoušíte spustit nástroj .NET Core, který byl nainstalován se zadanou cestou, je nutné při používání nástroje použít tuto cestu.</span><span class="sxs-lookup"><span data-stu-id="5bb21-139">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="5bb21-140">Příklad použití nástroje, který je nainstalovaný nástrojem Path, je:</span><span class="sxs-lookup"><span data-stu-id="5bb21-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="5bb21-141">Modul runtime se nenašel.</span><span class="sxs-lookup"><span data-stu-id="5bb21-141">Runtime not found</span></span>

<span data-ttu-id="5bb21-142">Nástroje .NET Core jsou [aplikace závislé na rozhraních](../deploying/index.md#publish-runtime-dependent), což znamená, že spoléhají na modul runtime .NET Core nainstalovaný na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="5bb21-142">.NET Core tools are [framework-dependent applications](../deploying/index.md#publish-runtime-dependent), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="5bb21-143">Pokud se očekávaný modul runtime nenajde, dodržuje normální pravidla předávaných modulem runtime .NET Core, jako například:</span><span class="sxs-lookup"><span data-stu-id="5bb21-143">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="5bb21-144">Aplikace se vrátí k nejvyšší verzi opravy zadané hlavní a dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="5bb21-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="5bb21-145">Pokud neexistuje žádný vyhovující modul runtime s párové číslo hlavní verze a podverze, použije se další vyšší dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="5bb21-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="5bb21-146">Mezi verzemi verze Preview modulu runtime nebo verzí Preview a verzí verze Preview nedochází k posunutí.</span><span class="sxs-lookup"><span data-stu-id="5bb21-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="5bb21-147">Proto musí být nástroje .NET Core vytvořené pomocí verzí Preview znovu sestavené a znovu publikovány autorem a opětovnou instalací.</span><span class="sxs-lookup"><span data-stu-id="5bb21-147">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="5bb21-148">Ve výchozím nastavení se v obou běžných scénářích neobjevují žádné možnosti přeposlání:</span><span class="sxs-lookup"><span data-stu-id="5bb21-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="5bb21-149">K dispozici jsou pouze nižší verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5bb21-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="5bb21-150">Přeposílání jenom vybírá novější verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5bb21-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="5bb21-151">K dispozici jsou pouze vyšší hlavní verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5bb21-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="5bb21-152">Přeposílání nepřekračuje hlavní hranice verze.</span><span class="sxs-lookup"><span data-stu-id="5bb21-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="5bb21-153">Pokud aplikace nemůže najít vhodný modul runtime, spuštění se nespustí a ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="5bb21-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="5bb21-154">Pomocí jednoho z následujících příkazů můžete zjistit, které moduly runtime .NET Core jsou nainstalovány na vašem počítači:</span><span class="sxs-lookup"><span data-stu-id="5bb21-154">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="5bb21-155">Pokud si myslíte, že by měl nástroj podporovat verzi modulu runtime, kterou máte aktuálně nainstalovanou, můžete se obrátit na autora nástroje a zjistit, jestli můžou aktualizovat číslo verze nebo více cílů.</span><span class="sxs-lookup"><span data-stu-id="5bb21-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="5bb21-156">Jakmile znovu zkompilujete a znovu publikujete balíček nástrojů do NuGet s aktualizovaným číslem verze, můžete kopii aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="5bb21-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="5bb21-157">I když k tomu nedojde, nejrychlejší řešení pro vás je instalace verze modulu runtime, která by fungovala s nástrojem, který se pokoušíte spustit.</span><span class="sxs-lookup"><span data-stu-id="5bb21-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="5bb21-158">Pokud si chcete stáhnout specifickou verzi modulu runtime .NET Core, navštivte [stránku ke stažení pro .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="5bb21-158">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="5bb21-159">Pokud nainstalujete .NET Core SDK do jiného než výchozího umístění, budete muset nastavit proměnnou prostředí `DOTNET_ROOT` na adresář, který obsahuje `dotnet` spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="5bb21-159">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="5bb21-160">Instalace nástroje .NET Core Tool se nezdařila</span><span class="sxs-lookup"><span data-stu-id="5bb21-160">.NET Core tool installation fails</span></span>

<span data-ttu-id="5bb21-161">Existuje několik důvodů, proč nemusí dojít k selhání instalace globálního nebo místního nástroje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb21-161">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="5bb21-162">Pokud se instalace nástroje nezdařila, zobrazí se zpráva podobná následující:</span><span class="sxs-lookup"><span data-stu-id="5bb21-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="5bb21-163">Abychom vám pomohli diagnostikovat tyto chyby, zobrazují se zprávy NuGet přímo uživateli společně s předchozí zprávou.</span><span class="sxs-lookup"><span data-stu-id="5bb21-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="5bb21-164">Zpráva NuGet vám může pomohly tento problém identifikovat.</span><span class="sxs-lookup"><span data-stu-id="5bb21-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="5bb21-165">Vynucení pojmenování balíčků</span><span class="sxs-lookup"><span data-stu-id="5bb21-165">Package naming enforcement</span></span>

<span data-ttu-id="5bb21-166">Společnost Microsoft změnila své doprovodné materiály na ID balíčku pro nástroje, což vede k tomu, že se nenalezne řada nástrojů s předpokládaným názvem.</span><span class="sxs-lookup"><span data-stu-id="5bb21-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="5bb21-167">Nové doprovodné materiály jsou všechny nástroje Microsoftu s předponou "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="5bb21-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="5bb21-168">Tato předpona je vyhrazená a dá se použít jenom pro balíčky podepsané certifikátem autorizovaným společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bb21-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="5bb21-169">V průběhu přechodu budou mít některé nástroje Microsoftu starou formu ID balíčku, zatímco ostatní budou mít novou formu:</span><span class="sxs-lookup"><span data-stu-id="5bb21-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="5bb21-170">ID balíčků se aktualizují, takže budete muset přejít na nové ID balíčku, abyste získali nejnovější aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5bb21-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="5bb21-171">Balíčky s zjednodušeným názvem nástroje budou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="5bb21-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="5bb21-172">Verze Preview</span><span class="sxs-lookup"><span data-stu-id="5bb21-172">Preview releases</span></span>

* <span data-ttu-id="5bb21-173">Pokoušíte se nainstalovat verzi Preview a nepoužili jste ji `--version` k určení verze.</span><span class="sxs-lookup"><span data-stu-id="5bb21-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="5bb21-174">Nástroje .NET Core, které jsou ve verzi Preview, se musí zadat s částí názvu, aby označovaly, že jsou ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="5bb21-174">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="5bb21-175">Nemusíte zahrnovat celou verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="5bb21-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="5bb21-176">Za předpokladu, že čísla verzí jsou v očekávaném formátu, můžete použít něco podobného jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="5bb21-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="5bb21-177">Balíček není nástroj .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb21-177">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="5bb21-178">Našel se balíček NuGet s tímto názvem, ale Nejednalo se o nástroj .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb21-178">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="5bb21-179">Pokud se pokusíte nainstalovat balíček NuGet, který je regulárním balíčkem NuGet, a ne nástrojem .NET Core, zobrazí se chybová zpráva podobná následující:</span><span class="sxs-lookup"><span data-stu-id="5bb21-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="5bb21-180">NU1212: Neplatná kombinace projektu a balíčku pro `<ToolName>` .</span><span class="sxs-lookup"><span data-stu-id="5bb21-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="5bb21-181">Styl projektu DotnetToolReference může obsahovat pouze odkazy na typ DotnetTool.</span><span class="sxs-lookup"><span data-stu-id="5bb21-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="5bb21-182">K informačnímu kanálu NuGet nelze přicházet.</span><span class="sxs-lookup"><span data-stu-id="5bb21-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="5bb21-183">Požadovaný informační kanál NuGet není k dispozici, možná kvůli problému s připojením k Internetu.</span><span class="sxs-lookup"><span data-stu-id="5bb21-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="5bb21-184">Instalace nástroje vyžaduje přístup k informačnímu kanálu NuGet, který obsahuje balíček nástroje.</span><span class="sxs-lookup"><span data-stu-id="5bb21-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="5bb21-185">Dojde k chybě, pokud informační kanál není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5bb21-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="5bb21-186">Kanály můžete upravovat pomocí `nuget.config` , vyžádat si konkrétní `nuget.config` soubor nebo zadat další kanály s `--add-source` přepínačem.</span><span class="sxs-lookup"><span data-stu-id="5bb21-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="5bb21-187">Ve výchozím nastavení vyvolá NuGet chybu pro jakýkoliv informační kanál, který se nemůže připojit.</span><span class="sxs-lookup"><span data-stu-id="5bb21-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="5bb21-188">Příznak `--ignore-failed-sources` může přeskočit tyto nedostupné zdroje.</span><span class="sxs-lookup"><span data-stu-id="5bb21-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="5bb21-189">ID balíčku je nesprávné.</span><span class="sxs-lookup"><span data-stu-id="5bb21-189">Package ID incorrect</span></span>

* <span data-ttu-id="5bb21-190">Nezadali jste název nástroje.</span><span class="sxs-lookup"><span data-stu-id="5bb21-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="5bb21-191">Běžným důvodem selhání je, že název nástroje není správný.</span><span class="sxs-lookup"><span data-stu-id="5bb21-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="5bb21-192">K tomu může dojít z důvodu neúspěšného zadání, nebo proto, že se nástroj přesunul nebo byl zastaralý.</span><span class="sxs-lookup"><span data-stu-id="5bb21-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="5bb21-193">V případě nástrojů na NuGet.org je třeba, abyste si ověřili, že je správný název, hledání nástroje na NuGet.org a zkopírování instalačního příkazu.</span><span class="sxs-lookup"><span data-stu-id="5bb21-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bb21-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bb21-194">See also</span></span>

* [<span data-ttu-id="5bb21-195">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="5bb21-195">.NET Core tools</span></span>](global-tools.md)
