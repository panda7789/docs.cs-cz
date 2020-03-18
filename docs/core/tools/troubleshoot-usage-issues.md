---
title: Poradce při potížích s používáním nástroje .NET Core
description: Seznamte se s běžnými problémy při spouštění nástrojů .NET Core a možných řešení.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146447"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="16615-103">Poradce při potížích s používáním nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="16615-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="16615-104">Při pokusu o instalaci nebo spuštění nástroje .NET Core, který může být globálním nástrojem nebo místním nástrojem, se mohou narazit na problémy.</span><span class="sxs-lookup"><span data-stu-id="16615-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="16615-105">Tento článek popisuje běžné hlavní příčiny a některá možná řešení.</span><span class="sxs-lookup"><span data-stu-id="16615-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="16615-106">Nainstalovaný nástroj .NET Core se nepodařilo spustit</span><span class="sxs-lookup"><span data-stu-id="16615-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="16615-107">Pokud se nástroj .NET Core nepodaří spustit, s největší pravděpodobností jste narazili na jeden z následujících problémů:</span><span class="sxs-lookup"><span data-stu-id="16615-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="16615-108">Spustitelný soubor nástroje nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="16615-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="16615-109">Nebyla nalezena správná verze runtime jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="16615-109">The correct version of the .NET Core runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="16615-110">Spustitelný soubor nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="16615-110">Executable file not found</span></span>

<span data-ttu-id="16615-111">Pokud se spustitelný soubor nenašel, zobrazí se zpráva podobná následující:</span><span class="sxs-lookup"><span data-stu-id="16615-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="16615-112">Název spustitelného souboru určuje způsob vyvolání nástroje.</span><span class="sxs-lookup"><span data-stu-id="16615-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="16615-113">Následující tabulka popisuje formát:</span><span class="sxs-lookup"><span data-stu-id="16615-113">The following table describes the format:</span></span>

| <span data-ttu-id="16615-114">Formát spustitelného názvu</span><span class="sxs-lookup"><span data-stu-id="16615-114">Executable name format</span></span>  | <span data-ttu-id="16615-115">Formát vyvolání</span><span class="sxs-lookup"><span data-stu-id="16615-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="16615-116">Globální nástroje</span><span class="sxs-lookup"><span data-stu-id="16615-116">Global tools</span></span>

  <span data-ttu-id="16615-117">Globální nástroje lze nainstalovat do výchozího adresáře nebo do určitého umístění.</span><span class="sxs-lookup"><span data-stu-id="16615-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="16615-118">Výchozí adresáře jsou:</span><span class="sxs-lookup"><span data-stu-id="16615-118">The default directories are:</span></span>

  | <span data-ttu-id="16615-119">Operační systém</span><span class="sxs-lookup"><span data-stu-id="16615-119">OS</span></span>          | <span data-ttu-id="16615-120">Cesta</span><span class="sxs-lookup"><span data-stu-id="16615-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="16615-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="16615-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="16615-122">Windows</span><span class="sxs-lookup"><span data-stu-id="16615-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="16615-123">Pokud se pokoušíte spustit globální nástroj, `PATH` zkontrolujte, zda proměnná prostředí v počítači obsahuje cestu, kam jste nainstalovali globální nástroj, a zda je spustitelný soubor v této cestě.</span><span class="sxs-lookup"><span data-stu-id="16615-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="16615-124">Rozhraní .NET Core CLI se pokusí přidat výchozí umístění do proměnné prostředí PATH při prvním použití.</span><span class="sxs-lookup"><span data-stu-id="16615-124">The .NET Core CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="16615-125">Existují však některé scénáře, kde umístění nemusí být přidáno do cesty automaticky:</span><span class="sxs-lookup"><span data-stu-id="16615-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="16615-126">Pokud používáte Linux a nainstalovali jste sdk .NET Core SDK pomocí souborů *.tar.gz* a ne apt-get nebo rpm.</span><span class="sxs-lookup"><span data-stu-id="16615-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="16615-127">Pokud používáte macOS 10.15 "Catalina" nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="16615-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="16615-128">Pokud používáte macOS 10.14 "Mojave" nebo starší verze a nainstalovali jste sdk .NET Core SDK pomocí souborů *.tar.gz* a ne *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="16615-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="16615-129">Pokud jste nainstalovali sadu .NET Core 3.0 SDK `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` a `false`nastavili jste proměnnou prostředí na .</span><span class="sxs-lookup"><span data-stu-id="16615-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="16615-130">Pokud jste nainstalovali sadu .NET Core 2.2 SDK nebo starší `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` verze `true`a nastavili jste proměnnou prostředí na .</span><span class="sxs-lookup"><span data-stu-id="16615-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="16615-131">V těchto scénářích nebo `--tool-path` pokud `PATH` jste zadali možnost, proměnná prostředí v počítači automaticky neobsahuje cestu, kam jste nainstalovali globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="16615-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="16615-132">V takovém případě přidejte umístění nástroje `$HOME/.dotnet/tools`(například) k proměnné `PATH` prostředí pomocí jakékoli metody, kterou prostředí poskytuje pro aktualizaci proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="16615-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="16615-133">Další informace naleznete v tématu [.NET Core tools](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="16615-133">For more information, see [.NET Core tools](global-tools.md).</span></span>

* <span data-ttu-id="16615-134">Místní nástroje</span><span class="sxs-lookup"><span data-stu-id="16615-134">Local tools</span></span>

  <span data-ttu-id="16615-135">Pokud se pokoušíte spustit místní nástroj, ověřte, zda je v aktuálním adresáři nebo v některém z nadřazených adresářů soubor manifestu nazývaný *dotnet-tools.json.*</span><span class="sxs-lookup"><span data-stu-id="16615-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="16615-136">Tento soubor může také žít pod složkou s názvem *.config* kdekoli v hierarchii složek projektu, namísto kořenové složky.</span><span class="sxs-lookup"><span data-stu-id="16615-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="16615-137">Pokud *dotnet-tools.json* existuje, otevřete jej a zkontrolujte nástroj, který se pokoušíte spustit.</span><span class="sxs-lookup"><span data-stu-id="16615-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="16615-138">Pokud soubor neobsahuje položku `"isRoot": true`pro aplikaci , zkontrolujte také další hierarchii souborů pro další soubory manifestu nástroje.</span><span class="sxs-lookup"><span data-stu-id="16615-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="16615-139">Pokud se pokoušíte spustit nástroj .NET Core, který byl nainstalován se zadanou cestou, je třeba tuto cestu zahrnout při používání nástroje.</span><span class="sxs-lookup"><span data-stu-id="16615-139">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="16615-140">Příkladem použití nástroje nainstalovaného nástroje je:</span><span class="sxs-lookup"><span data-stu-id="16615-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="16615-141">Doba běhu nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="16615-141">Runtime not found</span></span>

<span data-ttu-id="16615-142">Nástroje .NET Core jsou [aplikace závislé na rámci](../deploying/index.md#publish-runtime-dependent), což znamená, že spoléhají na runtime .NET Core nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="16615-142">.NET Core tools are [framework-dependent applications](../deploying/index.md#publish-runtime-dependent), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="16615-143">Pokud není nalezen očekávaný čas runtime, postupujte podle normálních pravidel pro přetápění vpřed .NET Core, například:</span><span class="sxs-lookup"><span data-stu-id="16615-143">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="16615-144">Aplikace se převádí dopředu na nejvyšší verzi opravy zadané hlavní a dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="16615-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="16615-145">Pokud neexistuje žádný odpovídající runtime s odpovídajícím hlavním a dílčím číslem verze, použije se další vyšší dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="16615-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="16615-146">Posunout vpřed nedochází mezi verzemi náhledu runtime nebo mezi verzemi náhledu a verzemi vydání.</span><span class="sxs-lookup"><span data-stu-id="16615-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="16615-147">Nástroje .NET Core vytvořené pomocí verzí ve verzi preview musí být autorem znovu sestaveny a znovu publikovány a znovu nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="16615-147">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="16615-148">K přechodu vpřed ve výchozím nastavení nedojde ve dvou běžných scénářích:</span><span class="sxs-lookup"><span data-stu-id="16615-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="16615-149">K dispozici jsou pouze nižší verze runtime.</span><span class="sxs-lookup"><span data-stu-id="16615-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="16615-150">Posunutím vpřed vyberete pouze novější verze běhu.</span><span class="sxs-lookup"><span data-stu-id="16615-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="16615-151">K dispozici jsou pouze vyšší hlavní verze runtime.</span><span class="sxs-lookup"><span data-stu-id="16615-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="16615-152">Posun vpřed nepřekračuje hranice hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="16615-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="16615-153">Pokud aplikace nemůže najít vhodný běh, se nepodaří spustit a hlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="16615-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="16615-154">Pomocí jednoho z následujících příkazů můžete zjistit, které runčasy jádra .NET jsou v počítači nainstalovány:</span><span class="sxs-lookup"><span data-stu-id="16615-154">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="16615-155">Pokud se domníváte, že by nástroj měl podporovat aktuálně nainstalovanou verzi runtime, můžete se obrátit na autora nástroje a zjistit, zda mohou aktualizovat číslo verze nebo více cílů.</span><span class="sxs-lookup"><span data-stu-id="16615-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="16615-156">Po překompilované a znovu publikovat jejich balíček nástrojů nuget s aktualizovaným číslem verze, můžete aktualizovat kopii.</span><span class="sxs-lookup"><span data-stu-id="16615-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="16615-157">I když k tomu nedojde, nejrychlejším řešením je instalace verze runtime, která by fungovala s nástrojem, který se pokoušíte spustit.</span><span class="sxs-lookup"><span data-stu-id="16615-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="16615-158">Chcete-li stáhnout konkrétní verzi runtime .NET Core, navštivte [stránku pro stažení jádra .NET](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="16615-158">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="16615-159">Pokud nainstalujete sadu .NET Core SDK do jiného než `DOTNET_ROOT` výchozího umístění, `dotnet` je třeba nastavit proměnnou prostředí na adresář, který obsahuje spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="16615-159">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="16615-160">Instalace nástroje .NET Core se nezdaří</span><span class="sxs-lookup"><span data-stu-id="16615-160">.NET Core tool installation fails</span></span>

<span data-ttu-id="16615-161">Existuje několik důvodů, proč instalace globálního nebo místního nástroje .NET Core může selhat.</span><span class="sxs-lookup"><span data-stu-id="16615-161">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="16615-162">Pokud se instalace nástroje nezdaří, zobrazí se zpráva podobná následující:</span><span class="sxs-lookup"><span data-stu-id="16615-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="16615-163">Chcete-li diagnostikovat tyto chyby, NuGet zprávy jsou zobrazeny přímo uživateli, spolu s předchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="16615-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="16615-164">Zpráva NuGet vám může pomoci identifikovat problém.</span><span class="sxs-lookup"><span data-stu-id="16615-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="16615-165">Vynucení pojmenování balíčků</span><span class="sxs-lookup"><span data-stu-id="16615-165">Package naming enforcement</span></span>

<span data-ttu-id="16615-166">Společnost Microsoft změnila pokyny k ID balíčku pro nástroje, což má za následek řadu nástrojů, které nebyly nalezeny s předpokládaným názvem.</span><span class="sxs-lookup"><span data-stu-id="16615-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="16615-167">Nové pokyny je, že všechny nástroje společnosti Microsoft s předponou "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="16615-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="16615-168">Tato předpona je vyhrazena a lze ji použít pouze pro balíčky podepsané autorizovaným certifikátem společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="16615-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="16615-169">Během přechodu budou mít některé nástroje společnosti Microsoft starou formu ID balíčku, zatímco jiné budou mít nový formulář:</span><span class="sxs-lookup"><span data-stu-id="16615-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="16615-170">Při aktualizaci ID balíčků budete muset změnit na nové ID balíčku, abyste získali nejnovější aktualizace.</span><span class="sxs-lookup"><span data-stu-id="16615-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="16615-171">Balíčky se zjednodušeným názvem nástroje budou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="16615-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="16615-172">Náhled vydání</span><span class="sxs-lookup"><span data-stu-id="16615-172">Preview releases</span></span>

* <span data-ttu-id="16615-173">Pokoušíte se nainstalovat verzi preview a nepoužili `--version` jste možnost k zadání verze.</span><span class="sxs-lookup"><span data-stu-id="16615-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="16615-174">Nástroje .NET Core, které jsou ve verzi Preview, musí být zadány s částí názvu, která označuje, že jsou ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="16615-174">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="16615-175">Není nutné zahrnout celý náhled.</span><span class="sxs-lookup"><span data-stu-id="16615-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="16615-176">Za předpokladu, že čísla verzí jsou v očekávaném formátu, můžete použít něco jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="16615-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="16615-177">Balíček není nástroj .NET Core</span><span class="sxs-lookup"><span data-stu-id="16615-177">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="16615-178">Balíček NuGet s tímto názvem byl nalezen, ale nebyl nástrojem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16615-178">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="16615-179">Pokud se pokusíte nainstalovat balíček NuGet, který je běžným balíčkem NuGet a nikoli nástrojem .NET Core, zobrazí se chyba podobná následující:</span><span class="sxs-lookup"><span data-stu-id="16615-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="16615-180">NU1212: Neplatná kombinace `<ToolName>`balíčku projektu pro .</span><span class="sxs-lookup"><span data-stu-id="16615-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="16615-181">DotnetToolReference styl projektu může obsahovat pouze odkazy typu DotnetTool.</span><span class="sxs-lookup"><span data-stu-id="16615-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="16615-182">NuGet krmivo nelze získat přístup</span><span class="sxs-lookup"><span data-stu-id="16615-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="16615-183">Požadovaný informační kanál NuGet nelze získat přístup, například z důvodu problému s připojením k Internetu.</span><span class="sxs-lookup"><span data-stu-id="16615-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="16615-184">Instalace nástroje vyžaduje přístup k nugetový informační kanál, který obsahuje balíček nástrojů.</span><span class="sxs-lookup"><span data-stu-id="16615-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="16615-185">Selže, pokud zdroj není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="16615-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="16615-186">Pomocí souborů můžete `nuget.config`měnit , `nuget.config` požadovat konkrétní soubor nebo určit `--add-source` další informační kanály pomocí přepínače.</span><span class="sxs-lookup"><span data-stu-id="16615-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="16615-187">Ve výchozím nastavení NuGet vyvolá chybu pro všechny zdroje, které nelze připojit.</span><span class="sxs-lookup"><span data-stu-id="16615-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="16615-188">Příznak `--ignore-failed-sources` můžete přeskočit tyto nedosažitelné zdroje.</span><span class="sxs-lookup"><span data-stu-id="16615-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="16615-189">ID balíčku nesprávné</span><span class="sxs-lookup"><span data-stu-id="16615-189">Package ID incorrect</span></span>

* <span data-ttu-id="16615-190">Chybně jste zadali název nástroje.</span><span class="sxs-lookup"><span data-stu-id="16615-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="16615-191">Častým důvodem selhání je, že název nástroje není správný.</span><span class="sxs-lookup"><span data-stu-id="16615-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="16615-192">K tomu může dojít z důvodu nesprávného zapsaní nebo proto, že nástroj byl přesunut nebo byl zastaral.</span><span class="sxs-lookup"><span data-stu-id="16615-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="16615-193">Pro nástroje na NuGet.org, jeden způsob, jak zajistit, že máte správný název, je vyhledat nástroj na NuGet.org a zkopírovat příkaz instalace.</span><span class="sxs-lookup"><span data-stu-id="16615-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="16615-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="16615-194">See also</span></span>

* [<span data-ttu-id="16615-195">Nástroje .NET Core</span><span class="sxs-lookup"><span data-stu-id="16615-195">.NET Core tools</span></span>](global-tools.md)
