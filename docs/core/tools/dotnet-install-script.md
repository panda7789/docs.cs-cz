---
title: dotnet-install scripts
description: Přečtěte si o příkazu dotnet – instalace skriptů pro instalaci .NET Core SDK a sdíleného modulu runtime.
ms.date: 04/30/2020
ms.openlocfilehash: c3aa6549a0b521db7fc19c6ff44665e3c4ba0c5f
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024651"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="e59a6-103">dotnet – Reference k instalaci skriptů</span><span class="sxs-lookup"><span data-stu-id="e59a6-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="e59a6-104">Name</span><span class="sxs-lookup"><span data-stu-id="e59a6-104">Name</span></span>

<span data-ttu-id="e59a6-105">`dotnet-install.ps1` | `dotnet-install.sh`-Skript použitý k instalaci .NET Core SDK a sdíleného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e59a6-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e59a6-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="e59a6-106">Synopsis</span></span>

<span data-ttu-id="e59a6-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="e59a6-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress] [-ProxyBypassList <LIST_OF_URLS>]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

Get-Help ./dotnet-install.ps1
```

<span data-ttu-id="e59a6-108">Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="e59a6-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

<span data-ttu-id="e59a6-109">Skript bash také čte přepínače prostředí PowerShell, takže můžete použít přepínače prostředí PowerShell se skriptem v systémech Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="e59a6-109">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

## <a name="description"></a><span data-ttu-id="e59a6-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e59a6-110">Description</span></span>

<span data-ttu-id="e59a6-111">`dotnet-install`Skripty provádějí instalaci .NET Core SDK bez správy, což zahrnuje .NET Core CLI a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="e59a6-111">The `dotnet-install` scripts perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span> <span data-ttu-id="e59a6-112">K dispozici jsou dva skripty:</span><span class="sxs-lookup"><span data-stu-id="e59a6-112">There are two scripts:</span></span>

* <span data-ttu-id="e59a6-113">PowerShellový skript, který funguje v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e59a6-113">A PowerShell script that works on Windows.</span></span>
* <span data-ttu-id="e59a6-114">Skript bash, který funguje v systému Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="e59a6-114">A bash script that works on Linux/macOS.</span></span>

### <a name="purpose"></a><span data-ttu-id="e59a6-115">Účel</span><span class="sxs-lookup"><span data-stu-id="e59a6-115">Purpose</span></span>

 <span data-ttu-id="e59a6-116">Zamýšlené použití skriptů je pro scénáře průběžné integrace (CI), kde:</span><span class="sxs-lookup"><span data-stu-id="e59a6-116">The intended use of the scripts is for Continuous Integration (CI) scenarios, where:</span></span>

* <span data-ttu-id="e59a6-117">Sadu SDK je potřeba nainstalovat bez zásahu uživatele a bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="e59a6-117">The SDK needs to be installed without user interaction and without admin rights.</span></span>
* <span data-ttu-id="e59a6-118">Instalace sady SDK není nutné uchovávat v několika spuštěních CI.</span><span class="sxs-lookup"><span data-stu-id="e59a6-118">The SDK installation doesn't need to persist across multiple CI runs.</span></span>

  <span data-ttu-id="e59a6-119">Typická posloupnost událostí:</span><span class="sxs-lookup"><span data-stu-id="e59a6-119">The typical sequence of events:</span></span>
  * <span data-ttu-id="e59a6-120">CI se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="e59a6-120">CI is triggered.</span></span>
  * <span data-ttu-id="e59a6-121">CI nainstaluje sadu SDK pomocí jednoho z těchto skriptů.</span><span class="sxs-lookup"><span data-stu-id="e59a6-121">CI installs the SDK using one of these scripts.</span></span>
  * <span data-ttu-id="e59a6-122">CI dokončí svou práci a vymaže dočasná data včetně instalace sady SDK.</span><span class="sxs-lookup"><span data-stu-id="e59a6-122">CI finishes its work and clears temporary data including the SDK installation.</span></span>

<span data-ttu-id="e59a6-123">Chcete-li nastavit vývojové prostředí nebo spustit aplikace, použijte instalační programy a nikoli tyto skripty.</span><span class="sxs-lookup"><span data-stu-id="e59a6-123">To set up a development environment or to run apps, use the installers rather than these scripts.</span></span>

### <a name="recommended-version"></a><span data-ttu-id="e59a6-124">Doporučená verze</span><span class="sxs-lookup"><span data-stu-id="e59a6-124">Recommended version</span></span>

<span data-ttu-id="e59a6-125">Doporučujeme používat stabilní verzi skriptů:</span><span class="sxs-lookup"><span data-stu-id="e59a6-125">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="e59a6-126">Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="e59a6-126">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="e59a6-127">PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="e59a6-127">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

### <a name="script-behavior"></a><span data-ttu-id="e59a6-128">Chování skriptu</span><span class="sxs-lookup"><span data-stu-id="e59a6-128">Script behavior</span></span>

<span data-ttu-id="e59a6-129">Oba skripty mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="e59a6-129">Both scripts have the same behavior.</span></span> <span data-ttu-id="e59a6-130">Stáhnou soubor ZIP/tarballu z buildu CLI a budou pokračovat v jeho instalaci buď ve výchozím umístění, nebo v umístění určeném parametrem `-InstallDir|--install-dir` .</span><span class="sxs-lookup"><span data-stu-id="e59a6-130">They download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span>

<span data-ttu-id="e59a6-131">Ve výchozím nastavení stáhnou instalační skripty sadu SDK a nainstaluje ji.</span><span class="sxs-lookup"><span data-stu-id="e59a6-131">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="e59a6-132">Pokud chcete získat pouze sdílený modul runtime, zadejte `-Runtime|--runtime` argument.</span><span class="sxs-lookup"><span data-stu-id="e59a6-132">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="e59a6-133">Ve výchozím nastavení skript přidá umístění instalace do $PATH pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="e59a6-133">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="e59a6-134">Přepsat toto výchozí chování zadáním `-NoPath|--no-path` argumentu.</span><span class="sxs-lookup"><span data-stu-id="e59a6-134">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span> <span data-ttu-id="e59a6-135">Skript nenastavuje `DOTNET_ROOT` proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="e59a6-135">The script doesn't set the `DOTNET_ROOT` environment variable.</span></span>

<span data-ttu-id="e59a6-136">Před spuštěním skriptu nainstalujte požadované [závislosti](../install/windows.md#dependencies).</span><span class="sxs-lookup"><span data-stu-id="e59a6-136">Before running the script, install the required [dependencies](../install/windows.md#dependencies).</span></span>

<span data-ttu-id="e59a6-137">Konkrétní verzi můžete nainstalovat pomocí `-Version|--version` argumentu.</span><span class="sxs-lookup"><span data-stu-id="e59a6-137">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="e59a6-138">Verze musí být zadána jako číslo verze se třemi částmi, například `2.1.0` .</span><span class="sxs-lookup"><span data-stu-id="e59a6-138">The version must be specified as a three-part version number, such as `2.1.0`.</span></span> <span data-ttu-id="e59a6-139">Pokud není zadaná verze, skript nainstaluje `latest` verzi.</span><span class="sxs-lookup"><span data-stu-id="e59a6-139">If the version isn't specified, the script installs the `latest` version.</span></span>

<span data-ttu-id="e59a6-140">Instalační skripty neaktualizují registr ve Windows.</span><span class="sxs-lookup"><span data-stu-id="e59a6-140">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="e59a6-141">Stačí stáhnout binární soubory zip a zkopírovat je do složky.</span><span class="sxs-lookup"><span data-stu-id="e59a6-141">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="e59a6-142">Pokud chcete aktualizovat hodnoty klíčů registru, použijte instalátory .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e59a6-142">If you want registry key values to be updated, use the .NET Core installers.</span></span>

## <a name="options"></a><span data-ttu-id="e59a6-143">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e59a6-143">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="e59a6-144">Architektura binárních souborů .NET Core, které se mají nainstalovat</span><span class="sxs-lookup"><span data-stu-id="e59a6-144">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="e59a6-145">Možné hodnoty jsou `<auto>` , `amd64` , `x64` , `x86` , a `arm64` `arm` .</span><span class="sxs-lookup"><span data-stu-id="e59a6-145">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="e59a6-146">Výchozí hodnota je `<auto>` , která představuje aktuálně běžící architekturu OS.</span><span class="sxs-lookup"><span data-stu-id="e59a6-146">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="e59a6-147">Určuje adresu URL pro instalační službu Azure feed.</span><span class="sxs-lookup"><span data-stu-id="e59a6-147">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="e59a6-148">Doporučujeme, abyste tuto hodnotu nezměnili.</span><span class="sxs-lookup"><span data-stu-id="e59a6-148">We recommended that you don't change this value.</span></span> <span data-ttu-id="e59a6-149">Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="e59a6-149">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="e59a6-150">Určuje zdrojový kanál pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="e59a6-150">Specifies the source channel for the installation.</span></span> <span data-ttu-id="e59a6-151">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="e59a6-151">The possible values are:</span></span>

  - <span data-ttu-id="e59a6-152">`Current`– Nejvíc aktuální verze</span><span class="sxs-lookup"><span data-stu-id="e59a6-152">`Current` - Most current release.</span></span>
  - <span data-ttu-id="e59a6-153">`LTS`– Kanál dlouhodobé podpory (aktuálně podporovaná verze).</span><span class="sxs-lookup"><span data-stu-id="e59a6-153">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="e59a6-154">Verze se dvěma částmi ve formátu X. Y představující specifickou verzi (například `2.1` nebo `3.0` ).</span><span class="sxs-lookup"><span data-stu-id="e59a6-154">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="e59a6-155">Název větve: například `release/3.1.1xx` nebo `master` (pro noční vydání).</span><span class="sxs-lookup"><span data-stu-id="e59a6-155">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="e59a6-156">Tuto možnost použijte, pokud chcete nainstalovat verzi z kanálu verze Preview.</span><span class="sxs-lookup"><span data-stu-id="e59a6-156">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="e59a6-157">Použijte název kanálu, který je uvedený v části [instalátory a binární soubory](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="e59a6-157">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="e59a6-158">Výchozí hodnota je `LTS`.</span><span class="sxs-lookup"><span data-stu-id="e59a6-158">The default value is `LTS`.</span></span> <span data-ttu-id="e59a6-159">Další informace o kanálech podpory rozhraní .NET najdete na stránce [zásady podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="e59a6-159">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="e59a6-160">Když se tato nastavení nastaví, skript neprovede instalaci.</span><span class="sxs-lookup"><span data-stu-id="e59a6-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="e59a6-161">Místo toho zobrazí příkazový řádek, který se má použít k konzistentně instalaci požadované verze .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="e59a6-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="e59a6-162">Pokud například zadáte verzi `latest` , zobrazí se odkaz s konkrétní verzí, aby se tento příkaz mohl ve skriptu sestavení použít deterministické.</span><span class="sxs-lookup"><span data-stu-id="e59a6-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="e59a6-163">Také se zobrazí umístění binárního souboru, pokud dáváte přednost instalaci nebo stažení.</span><span class="sxs-lookup"><span data-stu-id="e59a6-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="e59a6-164">Slouží jako řetězec dotazu, který se má připojit k datovému kanálu Azure.</span><span class="sxs-lookup"><span data-stu-id="e59a6-164">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="e59a6-165">Umožňuje změnit adresu URL tak, aby používala neveřejné účty úložiště BLOB.</span><span class="sxs-lookup"><span data-stu-id="e59a6-165">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--help`**

  <span data-ttu-id="e59a6-166">Vytiskne nápovědu pro skript.</span><span class="sxs-lookup"><span data-stu-id="e59a6-166">Prints out help for the script.</span></span> <span data-ttu-id="e59a6-167">Platí jenom pro skript bash.</span><span class="sxs-lookup"><span data-stu-id="e59a6-167">Applies only to bash script.</span></span> <span data-ttu-id="e59a6-168">Pro prostředí PowerShell použijte `Get-Help ./dotnet-install.ps1` .</span><span class="sxs-lookup"><span data-stu-id="e59a6-168">For PowerShell, use `Get-Help ./dotnet-install.ps1`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="e59a6-169">Určuje instalační cestu.</span><span class="sxs-lookup"><span data-stu-id="e59a6-169">Specifies the installation path.</span></span> <span data-ttu-id="e59a6-170">Adresář se vytvoří, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e59a6-170">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="e59a6-171">Výchozí hodnota je *%localappdata%\Microsoft\dotnet* ve Windows a */usr/share/dotnet* v systému Linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="e59a6-171">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="e59a6-172">Binární soubory jsou umístěny přímo v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="e59a6-172">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="e59a6-173">Určuje cestu k [global.jsv](global-json.md) souboru, který se použije k určení verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="e59a6-173">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="e59a6-174">*global.jsv* souboru musí mít hodnotu pro `sdk:version` .</span><span class="sxs-lookup"><span data-stu-id="e59a6-174">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="e59a6-175">Zakáže stahování z [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a používá neuložené kanály přímo.</span><span class="sxs-lookup"><span data-stu-id="e59a6-175">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="e59a6-176">Je-li nastavena, instalační složka není exportována do cesty pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="e59a6-176">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="e59a6-177">Ve výchozím nastavení skript upraví cestu, která zpřístupní .NET Core CLI hned po instalaci.</span><span class="sxs-lookup"><span data-stu-id="e59a6-177">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="e59a6-178">Pokud je tato nastavení nastavena, instalační program při vytváření webových požadavků používá proxy server.</span><span class="sxs-lookup"><span data-stu-id="e59a6-178">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="e59a6-179">(Platí jenom pro Windows.)</span><span class="sxs-lookup"><span data-stu-id="e59a6-179">(Only valid for Windows.)</span></span>

- **`-ProxyBypassList <LIST_OF_URLS>`**

  <span data-ttu-id="e59a6-180">Pokud je nastaveno `ProxyAddress` na, poskytuje seznam adres URL oddělených čárkami, které budou proxy obcházet.</span><span class="sxs-lookup"><span data-stu-id="e59a6-180">If set with `ProxyAddress`, provides a list of comma-separated urls that will bypass the proxy.</span></span> <span data-ttu-id="e59a6-181">(Platí jenom pro Windows.)</span><span class="sxs-lookup"><span data-stu-id="e59a6-181">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="e59a6-182">Pokud je nastaveno, instalační program při použití adresy proxy používá přihlašovací údaje aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="e59a6-182">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="e59a6-183">(Platí jenom pro Windows.)</span><span class="sxs-lookup"><span data-stu-id="e59a6-183">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="e59a6-184">Nainstaluje pouze sdílený modul runtime, nikoli celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="e59a6-184">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="e59a6-185">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="e59a6-185">The possible values are:</span></span>

  - <span data-ttu-id="e59a6-186">`dotnet`– `Microsoft.NETCore.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="e59a6-186">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="e59a6-187">`aspnetcore`– `Microsoft.AspNetCore.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="e59a6-187">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="e59a6-188">`windowsdesktop`– `Microsoft.WindowsDesktop.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="e59a6-188">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="e59a6-189">Určuje [identifikátor modulu runtime](../rid-catalog.md) , pro který jsou nástroje nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="e59a6-189">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="e59a6-190">Používá se `linux-x64` pro přenosné Linux.</span><span class="sxs-lookup"><span data-stu-id="e59a6-190">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="e59a6-191">(Platí jenom pro Linux/macOS.)</span><span class="sxs-lookup"><span data-stu-id="e59a6-191">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="e59a6-192">Tento parametr je zastaralý a v budoucí verzi skriptu ho můžete odebrat.</span><span class="sxs-lookup"><span data-stu-id="e59a6-192">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="e59a6-193">Doporučená alternativa je `-Runtime|--runtime` možnost.</span><span class="sxs-lookup"><span data-stu-id="e59a6-193">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="e59a6-194">Nainstaluje jenom sdílené běhové bity, ne celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="e59a6-194">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="e59a6-195">Tato možnost je ekvivalentní se zadáním `-Runtime|--runtime dotnet` .</span><span class="sxs-lookup"><span data-stu-id="e59a6-195">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="e59a6-196">Přeskočí instalaci souborů bez verze, například *dotnet.exe*, pokud již existují.</span><span class="sxs-lookup"><span data-stu-id="e59a6-196">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="e59a6-197">Umožňuje změnit adresu URL informačního kanálu neuloženého v mezipaměti, který používá tento instalační program.</span><span class="sxs-lookup"><span data-stu-id="e59a6-197">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="e59a6-198">Doporučujeme, abyste tuto hodnotu nezměnili.</span><span class="sxs-lookup"><span data-stu-id="e59a6-198">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="e59a6-199">Zobrazí diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="e59a6-199">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="e59a6-200">Představuje konkrétní verzi buildu.</span><span class="sxs-lookup"><span data-stu-id="e59a6-200">Represents a specific build version.</span></span> <span data-ttu-id="e59a6-201">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="e59a6-201">The possible values are:</span></span>

  - <span data-ttu-id="e59a6-202">`latest`– Nejnovější sestavení kanálu (používá se s `-Channel` možností)</span><span class="sxs-lookup"><span data-stu-id="e59a6-202">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="e59a6-203">`coherent`-Nejnovější souvislý Build na kanálu; používá nejnovější kombinaci stabilního balíčku (používá se s `-Channel` možnostmi názvu větve).</span><span class="sxs-lookup"><span data-stu-id="e59a6-203">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="e59a6-204">Verze se třemi částmi ve formátu X. Y. Z představující specifickou verzi buildu; nahrazuje `-Channel` možnost.</span><span class="sxs-lookup"><span data-stu-id="e59a6-204">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="e59a6-205">Příklad: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="e59a6-205">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="e59a6-206">Pokud není zadaný, `-Version` použije se výchozí hodnota `latest` .</span><span class="sxs-lookup"><span data-stu-id="e59a6-206">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="e59a6-207">Příklady</span><span class="sxs-lookup"><span data-stu-id="e59a6-207">Examples</span></span>

- <span data-ttu-id="e59a6-208">Nainstalujte nejnovější dlouhodobou podporovanou verzi (LTS) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="e59a6-208">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="e59a6-209">Windows:</span><span class="sxs-lookup"><span data-stu-id="e59a6-209">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="e59a6-210">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="e59a6-210">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="e59a6-211">Nainstalujte nejnovější verzi z kanálu 3,1 do zadaného umístění:</span><span class="sxs-lookup"><span data-stu-id="e59a6-211">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="e59a6-212">Windows:</span><span class="sxs-lookup"><span data-stu-id="e59a6-212">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="e59a6-213">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="e59a6-213">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="e59a6-214">Instalace verze 3.0.0 sdíleného modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="e59a6-214">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="e59a6-215">Windows:</span><span class="sxs-lookup"><span data-stu-id="e59a6-215">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="e59a6-216">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="e59a6-216">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="e59a6-217">Získání skriptu a instalace verze 2.1.2 za podnikovým proxy serverem (pouze Windows):</span><span class="sxs-lookup"><span data-stu-id="e59a6-217">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="e59a6-218">Získání skriptu a instalace .NET Core CLI v jednom-linii příkladech:</span><span class="sxs-lookup"><span data-stu-id="e59a6-218">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="e59a6-219">Windows:</span><span class="sxs-lookup"><span data-stu-id="e59a6-219">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="e59a6-220">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="e59a6-220">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="e59a6-221">Viz také</span><span class="sxs-lookup"><span data-stu-id="e59a6-221">See also</span></span>

- [<span data-ttu-id="e59a6-222">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="e59a6-222">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="e59a6-223">Archiv rozhraní .NET Core Runtime a sady SDK ke stažení</span><span class="sxs-lookup"><span data-stu-id="e59a6-223">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
