---
title: dotnet-install scripts
description: Přečtěte si o příkazu dotnet – instalace skriptů pro instalaci .NET Core SDK a sdíleného modulu runtime.
ms.date: 04/30/2020
ms.openlocfilehash: 6728708ac5154f558954b46a22a434b05a548e84
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205931"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="0c593-103">dotnet – Reference k instalaci skriptů</span><span class="sxs-lookup"><span data-stu-id="0c593-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="0c593-104">Name</span><span class="sxs-lookup"><span data-stu-id="0c593-104">Name</span></span>

<span data-ttu-id="0c593-105">`dotnet-install.ps1` | `dotnet-install.sh`-Skript použitý k instalaci .NET Core SDK a sdíleného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0c593-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0c593-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="0c593-106">Synopsis</span></span>

<span data-ttu-id="0c593-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="0c593-107">Windows:</span></span>

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

<span data-ttu-id="0c593-108">Linux/macOs:</span><span class="sxs-lookup"><span data-stu-id="0c593-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a><span data-ttu-id="0c593-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0c593-109">Description</span></span>

<span data-ttu-id="0c593-110">`dotnet-install`Skripty se používají k provedení instalace .NET Core SDK bez správy, která zahrnuje .NET Core CLI a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="0c593-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="0c593-111">Doporučujeme používat stabilní verzi skriptů:</span><span class="sxs-lookup"><span data-stu-id="0c593-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="0c593-112">Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="0c593-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="0c593-113">PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="0c593-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="0c593-114">Hlavní užitečnost těchto skriptů je ve scénářích automatizace a v instalacích bez správy.</span><span class="sxs-lookup"><span data-stu-id="0c593-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="0c593-115">Existují dva skripty: jeden je PowerShellový skript, který funguje ve Windows, a druhý je bash skript, který funguje na Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="0c593-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="0c593-116">Oba skripty mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="0c593-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="0c593-117">Skript bash také čte přepínače prostředí PowerShell, takže můžete použít přepínače prostředí PowerShell se skriptem v systémech Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="0c593-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="0c593-118">Instalační skripty stáhnou soubor ZIP/tarballu z buildu CLI a budou pokračovat v jeho instalaci buď ve výchozím umístění, nebo v umístění určeném parametrem `-InstallDir|--install-dir` .</span><span class="sxs-lookup"><span data-stu-id="0c593-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="0c593-119">Ve výchozím nastavení stáhnou instalační skripty sadu SDK a nainstaluje ji.</span><span class="sxs-lookup"><span data-stu-id="0c593-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="0c593-120">Pokud chcete získat pouze sdílený modul runtime, zadejte `-Runtime|--runtime` argument.</span><span class="sxs-lookup"><span data-stu-id="0c593-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="0c593-121">Ve výchozím nastavení skript přidá umístění instalace do $PATH pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="0c593-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="0c593-122">Přepsat toto výchozí chování zadáním `-NoPath|--no-path` argumentu.</span><span class="sxs-lookup"><span data-stu-id="0c593-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="0c593-123">Před spuštěním skriptu nainstalujte požadované [závislosti](../install/dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="0c593-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="0c593-124">Konkrétní verzi můžete nainstalovat pomocí `-Version|--version` argumentu.</span><span class="sxs-lookup"><span data-stu-id="0c593-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="0c593-125">Verze musí být zadána jako verze se třemi částmi (například `2.1.0` ).</span><span class="sxs-lookup"><span data-stu-id="0c593-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="0c593-126">Pokud není zadaný, použije se `latest` verze.</span><span class="sxs-lookup"><span data-stu-id="0c593-126">If not provided, it uses the `latest` version.</span></span>

<span data-ttu-id="0c593-127">Instalační skripty neaktualizují registr ve Windows.</span><span class="sxs-lookup"><span data-stu-id="0c593-127">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="0c593-128">Stačí stáhnout binární soubory zip a zkopírovat je do složky.</span><span class="sxs-lookup"><span data-stu-id="0c593-128">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="0c593-129">Pokud chcete aktualizovat hodnoty klíčů registru, použijte instalátory .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0c593-129">If you want registry key values to be updated, use the .NET Core installers.</span></span>

## <a name="options"></a><span data-ttu-id="0c593-130">Možnosti</span><span class="sxs-lookup"><span data-stu-id="0c593-130">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="0c593-131">Architektura binárních souborů .NET Core, které se mají nainstalovat</span><span class="sxs-lookup"><span data-stu-id="0c593-131">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="0c593-132">Možné hodnoty jsou `<auto>` , `amd64` , `x64` , `x86` , a `arm64` `arm` .</span><span class="sxs-lookup"><span data-stu-id="0c593-132">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="0c593-133">Výchozí hodnota je `<auto>` , která představuje aktuálně běžící architekturu OS.</span><span class="sxs-lookup"><span data-stu-id="0c593-133">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="0c593-134">Určuje adresu URL pro instalační službu Azure feed.</span><span class="sxs-lookup"><span data-stu-id="0c593-134">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="0c593-135">Doporučujeme, abyste tuto hodnotu nezměnili.</span><span class="sxs-lookup"><span data-stu-id="0c593-135">We recommended that you don't change this value.</span></span> <span data-ttu-id="0c593-136">Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="0c593-136">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="0c593-137">Určuje zdrojový kanál pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="0c593-137">Specifies the source channel for the installation.</span></span> <span data-ttu-id="0c593-138">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0c593-138">The possible values are:</span></span>

  - <span data-ttu-id="0c593-139">`Current`– Nejvíc aktuální verze</span><span class="sxs-lookup"><span data-stu-id="0c593-139">`Current` - Most current release.</span></span>
  - <span data-ttu-id="0c593-140">`LTS`– Kanál dlouhodobé podpory (aktuálně podporovaná verze).</span><span class="sxs-lookup"><span data-stu-id="0c593-140">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="0c593-141">Verze se dvěma částmi ve formátu X. Y představující specifickou verzi (například `2.1` nebo `3.0` ).</span><span class="sxs-lookup"><span data-stu-id="0c593-141">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="0c593-142">Název větve: například `release/3.1.1xx` nebo `master` (pro noční vydání).</span><span class="sxs-lookup"><span data-stu-id="0c593-142">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="0c593-143">Tuto možnost použijte, pokud chcete nainstalovat verzi z kanálu verze Preview.</span><span class="sxs-lookup"><span data-stu-id="0c593-143">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="0c593-144">Použijte název kanálu, který je uvedený v části [instalátory a binární soubory](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="0c593-144">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="0c593-145">Výchozí hodnota je `LTS`.</span><span class="sxs-lookup"><span data-stu-id="0c593-145">The default value is `LTS`.</span></span> <span data-ttu-id="0c593-146">Další informace o kanálech podpory rozhraní .NET najdete na stránce [zásady podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="0c593-146">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="0c593-147">Když se tato nastavení nastaví, skript neprovede instalaci.</span><span class="sxs-lookup"><span data-stu-id="0c593-147">If set, the script won't perform the installation.</span></span> <span data-ttu-id="0c593-148">Místo toho zobrazí příkazový řádek, který se má použít k konzistentně instalaci požadované verze .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="0c593-148">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="0c593-149">Pokud například zadáte verzi `latest` , zobrazí se odkaz s konkrétní verzí, aby se tento příkaz mohl ve skriptu sestavení použít deterministické.</span><span class="sxs-lookup"><span data-stu-id="0c593-149">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="0c593-150">Také se zobrazí umístění binárního souboru, pokud dáváte přednost instalaci nebo stažení.</span><span class="sxs-lookup"><span data-stu-id="0c593-150">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="0c593-151">Slouží jako řetězec dotazu, který se má připojit k datovému kanálu Azure.</span><span class="sxs-lookup"><span data-stu-id="0c593-151">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="0c593-152">Umožňuje změnit adresu URL tak, aby používala neveřejné účty úložiště BLOB.</span><span class="sxs-lookup"><span data-stu-id="0c593-152">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="0c593-153">Vytiskne nápovědu pro skript.</span><span class="sxs-lookup"><span data-stu-id="0c593-153">Prints out help for the script.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="0c593-154">Určuje instalační cestu.</span><span class="sxs-lookup"><span data-stu-id="0c593-154">Specifies the installation path.</span></span> <span data-ttu-id="0c593-155">Adresář se vytvoří, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="0c593-155">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="0c593-156">Výchozí hodnota je *%localappdata%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="0c593-156">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="0c593-157">Binární soubory jsou umístěny přímo v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="0c593-157">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="0c593-158">Určuje cestu k souboru [Global. JSON](global-json.md) , který se použije k určení verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="0c593-158">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="0c593-159">Soubor *Global. JSON* musí mít hodnotu pro `sdk:version` .</span><span class="sxs-lookup"><span data-stu-id="0c593-159">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="0c593-160">Zakáže stahování z [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a používá neuložené kanály přímo.</span><span class="sxs-lookup"><span data-stu-id="0c593-160">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="0c593-161">Je-li nastavena, instalační složka není exportována do cesty pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="0c593-161">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="0c593-162">Ve výchozím nastavení skript upraví cestu, která zpřístupní .NET Core CLI hned po instalaci.</span><span class="sxs-lookup"><span data-stu-id="0c593-162">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="0c593-163">Pokud je tato nastavení nastavena, instalační program při vytváření webových požadavků používá proxy server.</span><span class="sxs-lookup"><span data-stu-id="0c593-163">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="0c593-164">(Platí jenom pro Windows.)</span><span class="sxs-lookup"><span data-stu-id="0c593-164">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="0c593-165">Pokud je nastaveno, instalační program při použití adresy proxy používá přihlašovací údaje aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="0c593-165">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="0c593-166">(Platí jenom pro Windows.)</span><span class="sxs-lookup"><span data-stu-id="0c593-166">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="0c593-167">Nainstaluje pouze sdílený modul runtime, nikoli celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="0c593-167">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="0c593-168">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0c593-168">The possible values are:</span></span>

  - <span data-ttu-id="0c593-169">`dotnet`– `Microsoft.NETCore.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="0c593-169">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="0c593-170">`aspnetcore`– `Microsoft.AspNetCore.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="0c593-170">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="0c593-171">`windowsdesktop`– `Microsoft.WindowsDesktop.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="0c593-171">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="0c593-172">Určuje [identifikátor modulu runtime](../rid-catalog.md) , pro který jsou nástroje nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="0c593-172">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="0c593-173">Používá se `linux-x64` pro přenosné Linux.</span><span class="sxs-lookup"><span data-stu-id="0c593-173">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="0c593-174">(Platí jenom pro Linux/macOS.)</span><span class="sxs-lookup"><span data-stu-id="0c593-174">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="0c593-175">Tento parametr je zastaralý a v budoucí verzi skriptu ho můžete odebrat.</span><span class="sxs-lookup"><span data-stu-id="0c593-175">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="0c593-176">Doporučená alternativa je `-Runtime|--runtime` možnost.</span><span class="sxs-lookup"><span data-stu-id="0c593-176">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="0c593-177">Nainstaluje jenom sdílené běhové bity, ne celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="0c593-177">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="0c593-178">Tato možnost je ekvivalentní se zadáním `-Runtime|--runtime dotnet` .</span><span class="sxs-lookup"><span data-stu-id="0c593-178">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="0c593-179">Přeskočí instalaci souborů bez verze, jako je například *dotnet. exe*, pokud již existují.</span><span class="sxs-lookup"><span data-stu-id="0c593-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="0c593-180">Umožňuje změnit adresu URL informačního kanálu neuloženého v mezipaměti, který používá tento instalační program.</span><span class="sxs-lookup"><span data-stu-id="0c593-180">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="0c593-181">Doporučujeme, abyste tuto hodnotu nezměnili.</span><span class="sxs-lookup"><span data-stu-id="0c593-181">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="0c593-182">Zobrazí diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="0c593-182">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="0c593-183">Představuje konkrétní verzi buildu.</span><span class="sxs-lookup"><span data-stu-id="0c593-183">Represents a specific build version.</span></span> <span data-ttu-id="0c593-184">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="0c593-184">The possible values are:</span></span>

  - <span data-ttu-id="0c593-185">`latest`– Nejnovější sestavení kanálu (používá se s `-Channel` možností)</span><span class="sxs-lookup"><span data-stu-id="0c593-185">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="0c593-186">`coherent`-Nejnovější souvislý Build na kanálu; používá nejnovější kombinaci stabilního balíčku (používá se s `-Channel` možnostmi názvu větve).</span><span class="sxs-lookup"><span data-stu-id="0c593-186">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="0c593-187">Verze se třemi částmi ve formátu X. Y. Z představující specifickou verzi buildu; nahrazuje `-Channel` možnost.</span><span class="sxs-lookup"><span data-stu-id="0c593-187">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="0c593-188">Například: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="0c593-188">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="0c593-189">Pokud není zadaný, `-Version` použije se výchozí hodnota `latest` .</span><span class="sxs-lookup"><span data-stu-id="0c593-189">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="0c593-190">Příklady</span><span class="sxs-lookup"><span data-stu-id="0c593-190">Examples</span></span>

- <span data-ttu-id="0c593-191">Nainstalujte nejnovější dlouhodobou podporovanou verzi (LTS) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="0c593-191">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="0c593-192">Windows:</span><span class="sxs-lookup"><span data-stu-id="0c593-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="0c593-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="0c593-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="0c593-194">Nainstalujte nejnovější verzi z kanálu 3,1 do zadaného umístění:</span><span class="sxs-lookup"><span data-stu-id="0c593-194">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="0c593-195">Windows:</span><span class="sxs-lookup"><span data-stu-id="0c593-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="0c593-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="0c593-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="0c593-197">Instalace verze 3.0.0 sdíleného modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="0c593-197">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="0c593-198">Windows:</span><span class="sxs-lookup"><span data-stu-id="0c593-198">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="0c593-199">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="0c593-199">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="0c593-200">Získání skriptu a instalace verze 2.1.2 za podnikovým proxy serverem (pouze Windows):</span><span class="sxs-lookup"><span data-stu-id="0c593-200">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="0c593-201">Získání skriptu a instalace .NET Core CLI v jednom-linii příkladech:</span><span class="sxs-lookup"><span data-stu-id="0c593-201">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="0c593-202">Windows:</span><span class="sxs-lookup"><span data-stu-id="0c593-202">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="0c593-203">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="0c593-203">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="0c593-204">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c593-204">See also</span></span>

- [<span data-ttu-id="0c593-205">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="0c593-205">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="0c593-206">Archiv rozhraní .NET Core Runtime a sady SDK ke stažení</span><span class="sxs-lookup"><span data-stu-id="0c593-206">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
