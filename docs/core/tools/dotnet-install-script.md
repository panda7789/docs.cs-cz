---
title: dotnet-install scripts
description: Přečtěte si o skriptech dotnet-install pro instalaci sady .NET Core SDK a sdíleného běhu.
ms.date: 01/23/2020
ms.openlocfilehash: 591413a17db577560bd0324995066c8ea7a35895
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463678"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="c3c6e-103">Odkaz na skripty dotnet-install</span><span class="sxs-lookup"><span data-stu-id="c3c6e-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="c3c6e-104">Název</span><span class="sxs-lookup"><span data-stu-id="c3c6e-104">Name</span></span>

<span data-ttu-id="c3c6e-105">`dotnet-install.ps1` | `dotnet-install.sh`- Skript používaný k instalaci sady .NET Core SDK a sdíleného běhu.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c3c6e-106">Synopse</span><span class="sxs-lookup"><span data-stu-id="c3c6e-106">Synopsis</span></span>

<span data-ttu-id="c3c6e-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

dotnet-install.ps1 -Help
```

<span data-ttu-id="c3c6e-108">Linux/macOs:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a><span data-ttu-id="c3c6e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c3c6e-109">Description</span></span>

<span data-ttu-id="c3c6e-110">Skripty `dotnet-install` se používají k provedení instalace sady .NET Core SDK bez oprávnění správce, která zahrnuje rozhraní .NET Core CLI a sdílený běh.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="c3c6e-111">Doporučujeme používat stabilní verzi skriptů:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="c3c6e-112">Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="c3c6e-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="c3c6e-113">Prostředí PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="c3c6e-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="c3c6e-114">Hlavní užitečnost těchto skriptů je ve scénářích automatizace a instalace bez správce.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="c3c6e-115">Existují dva skripty: jeden je skript PowerShell, který funguje v systému Windows, a druhý je bash skript, který funguje na Linux / macOS.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="c3c6e-116">Oba skripty mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="c3c6e-117">Bash skript také čte PowerShell přepínače, takže můžete použít PowerShell přepínače se skriptem na Linux / macOS systémy.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="c3c6e-118">Instalační skripty stáhnout soubor ZIP/tarball z sestavení rozhraní CLI klesne a pokračovat v instalaci `-InstallDir|--install-dir`ve výchozím umístění nebo v umístění určeném .</span><span class="sxs-lookup"><span data-stu-id="c3c6e-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="c3c6e-119">Ve výchozím nastavení instalační skripty stáhnout sadu SDK a nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="c3c6e-120">Pokud chcete získat pouze sdílený runtime, `-Runtime|--runtime` zadejte argument.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="c3c6e-121">Ve výchozím nastavení skript přidá umístění instalace do $PATH pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="c3c6e-122">Toto výchozí chování přepište `-NoPath|--no-path` zadáním argumentu.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="c3c6e-123">Před spuštěním skriptu nainstalujte požadované [závislosti](../install/dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="c3c6e-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="c3c6e-124">Pomocí argumentu můžete nainstalovat `-Version|--version` určitou verzi.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="c3c6e-125">Verze musí být zadána jako třídílná `2.1.0`verze (například ).</span><span class="sxs-lookup"><span data-stu-id="c3c6e-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="c3c6e-126">Pokud není k dispozici, `latest` používá verzi.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="c3c6e-127">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c3c6e-127">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="c3c6e-128">Architektura binárních souborů .NET Core, které chcete nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-128">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="c3c6e-129">Možné hodnoty `<auto>` `amd64`jsou `x64` `x86`, `arm64`, `arm`, , a .</span><span class="sxs-lookup"><span data-stu-id="c3c6e-129">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="c3c6e-130">Výchozí hodnota `<auto>`je , která představuje aktuálně spuštěnou architekturu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-130">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="c3c6e-131">Určuje adresu URL zdroje Azure instalačnímu programu.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-131">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="c3c6e-132">Doporučujeme, abyste tuto hodnotu neměnili.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-132">We recommended that you don't change this value.</span></span> <span data-ttu-id="c3c6e-133">Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-133">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="c3c6e-134">Určuje zdrojový kanál pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-134">Specifies the source channel for the installation.</span></span> <span data-ttu-id="c3c6e-135">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-135">The possible values are:</span></span>

  - <span data-ttu-id="c3c6e-136">`Current`- Nejaktuálnější vydání.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-136">`Current` - Most current release.</span></span>
  - <span data-ttu-id="c3c6e-137">`LTS`- Kanál dlouhodobé podpory (nejaktuálnější podporovaná verze).</span><span class="sxs-lookup"><span data-stu-id="c3c6e-137">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="c3c6e-138">Dvoudílná verze ve formátu X.Y představující konkrétní `2.1` verzi `3.0`(například nebo ).</span><span class="sxs-lookup"><span data-stu-id="c3c6e-138">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="c3c6e-139">Název pobočky: `release/3.1.1xx` například, nebo `master` (pro noční zprávy).</span><span class="sxs-lookup"><span data-stu-id="c3c6e-139">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="c3c6e-140">Tuto možnost použijte k instalaci verze z kanálu náhledu.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-140">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="c3c6e-141">Použijte název kanálu uvedený v [části Instalační programy a binární soubory](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="c3c6e-141">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="c3c6e-142">Výchozí hodnota je `LTS`.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-142">The default value is `LTS`.</span></span> <span data-ttu-id="c3c6e-143">Další informace o kanálech podpory rozhraní .NET naleznete na stránce [zásad podpory rozhraní .NET.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="c3c6e-143">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="c3c6e-144">Pokud je nastavena, skript nebude provádět instalaci.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-144">If set, the script won't perform the installation.</span></span> <span data-ttu-id="c3c6e-145">Místo toho zobrazí, jaký příkazový řádek použít k onisnok nainstalovat aktuálně požadovanou verzi rozhraní příkazového příkazu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-145">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="c3c6e-146">Pokud například zadáte `latest`verzi , zobrazí se odkaz s konkrétní verzí, aby bylo možné tento příkaz deterministicky použít ve skriptu sestavení.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-146">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="c3c6e-147">Zobrazuje také umístění binárního souboru, pokud dáváte přednost instalaci nebo stažení sami.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-147">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="c3c6e-148">Používá se jako řetězec dotazu pro připojení k kanálu Azure.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-148">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="c3c6e-149">Umožňuje změnit adresu URL tak, aby používala neveřejné účty úložiště objektů blob.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-149">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="c3c6e-150">Vytiskne nápovědu pro skript.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-150">Prints out help for the script.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="c3c6e-151">Určuje instalační cestu.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-151">Specifies the installation path.</span></span> <span data-ttu-id="c3c6e-152">Adresář je vytvořen, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-152">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="c3c6e-153">Výchozí hodnota je *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-153">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="c3c6e-154">Binární soubory jsou umístěny přímo v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-154">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="c3c6e-155">Určuje cestu k souboru [global.json,](global-json.md) který bude použit k určení verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-155">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="c3c6e-156">Soubor *global.json* musí mít `sdk:version`hodnotu pro .</span><span class="sxs-lookup"><span data-stu-id="c3c6e-156">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="c3c6e-157">Zakáže stahování ze [sítě pro doručování obsahu Azure (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a přímo používá kanál bez mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-157">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="c3c6e-158">Pokud je nastavena, instalační složka není exportována do cesty pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-158">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="c3c6e-159">Ve výchozím nastavení skript upravuje PATH, který zpřístupňuje rozhraní CLI jádra .NET ihned po instalaci.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-159">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="c3c6e-160">Pokud je nastavena, instalační program používá proxy server při vytváření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-160">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="c3c6e-161">(Platí pouze pro systém Windows.)</span><span class="sxs-lookup"><span data-stu-id="c3c6e-161">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="c3c6e-162">Pokud je nastaveno, instalační program používá pověření aktuálního uživatele při použití proxy adresy.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-162">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="c3c6e-163">(Platí pouze pro systém Windows.)</span><span class="sxs-lookup"><span data-stu-id="c3c6e-163">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="c3c6e-164">Nainstaluje pouze sdílený runtime, nikoli celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-164">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="c3c6e-165">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-165">The possible values are:</span></span>

  - <span data-ttu-id="c3c6e-166">`dotnet`- `Microsoft.NETCore.App` sdíleného běhu.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-166">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="c3c6e-167">`aspnetcore`- `Microsoft.AspNetCore.App` sdíleného běhu.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-167">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="c3c6e-168">`windowsdesktop`- `Microsoft.WindowsDesktop.App` sdíleného běhu.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-168">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="c3c6e-169">Určuje [identifikátor za běhu,](../rid-catalog.md) pro který jsou nástroje instalovány.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-169">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="c3c6e-170">Používá `linux-x64` se pro přenosný Linux.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-170">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="c3c6e-171">(Platí pouze pro Linux/macOS.)</span><span class="sxs-lookup"><span data-stu-id="c3c6e-171">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="c3c6e-172">Tento parametr je zastaralý a může být odebrán v budoucí verzi skriptu.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-172">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="c3c6e-173">Doporučenou alternativou `-Runtime|--runtime` je možnost.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-173">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="c3c6e-174">Nainstaluje pouze sdílené bity runtime, nikoli celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-174">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="c3c6e-175">Tato možnost je ekvivalentní `-Runtime|--runtime dotnet`určení .</span><span class="sxs-lookup"><span data-stu-id="c3c6e-175">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="c3c6e-176">Přeskočí instalaci souborů s neverzí, například *dotnet.exe*, pokud již existují.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-176">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="c3c6e-177">Umožňuje změnu adresy URL informačního kanálu bez mezipaměti používaného tímto instalačním programem.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-177">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="c3c6e-178">Doporučujeme, abyste tuto hodnotu neměnili.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-178">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="c3c6e-179">Zobrazí diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-179">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="c3c6e-180">Představuje konkrétní verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-180">Represents a specific build version.</span></span> <span data-ttu-id="c3c6e-181">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-181">The possible values are:</span></span>

  - <span data-ttu-id="c3c6e-182">`latest`- Nejnovější stavět na kanálu `-Channel` (používá se s možností).</span><span class="sxs-lookup"><span data-stu-id="c3c6e-182">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="c3c6e-183">`coherent`- Nejnovější koherentní stavět na kanálu; používá nejnovější stabilní kombinaci balíčků `-Channel` (používá se s možnostmi názvu větve).</span><span class="sxs-lookup"><span data-stu-id="c3c6e-183">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="c3c6e-184">Třídílná verze ve formátu X.Y.Z představující konkrétní verzi sestavení; nahrazuje `-Channel` tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-184">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="c3c6e-185">Například: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="c3c6e-185">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="c3c6e-186">Pokud není `-Version` zadán, `latest`výchozí hodnota je .</span><span class="sxs-lookup"><span data-stu-id="c3c6e-186">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="c3c6e-187">Příklady</span><span class="sxs-lookup"><span data-stu-id="c3c6e-187">Examples</span></span>

- <span data-ttu-id="c3c6e-188">Nainstalujte nejnovější dlouhodobou podporovanou verzi (LTS) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="c3c6e-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="c3c6e-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="c3c6e-191">Nainstalujte nejnovější verzi z kanálu 3.1 do určeného umístění:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="c3c6e-192">Windows:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="c3c6e-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="c3c6e-194">Nainstalujte verzi sdíleného runtime 3.0.0:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="c3c6e-195">Windows:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="c3c6e-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="c3c6e-197">Získejte skript a nainstalujte verzi 2.1.2 za podnikový proxy server (pouze systém Windows):</span><span class="sxs-lookup"><span data-stu-id="c3c6e-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="c3c6e-198">Získat skript a nainstalovat příklady rozhraní .NET Core CLI s jednou vložkou:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="c3c6e-199">Windows:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="c3c6e-200">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="c3c6e-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="c3c6e-201">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3c6e-201">See also</span></span>

- [<span data-ttu-id="c3c6e-202">Verze jádra .NET</span><span class="sxs-lookup"><span data-stu-id="c3c6e-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="c3c6e-203">Archiv stahování .NET Core Runtime a SDK</span><span class="sxs-lookup"><span data-stu-id="c3c6e-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
