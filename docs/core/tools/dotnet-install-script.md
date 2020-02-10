---
title: dotnet-install scripts
description: Přečtěte si o příkazu dotnet – instalace skriptů pro instalaci .NET Core SDK a sdíleného modulu runtime.
ms.date: 01/23/2020
ms.openlocfilehash: bf28f872be3ac2b4115b1d5e5c06e32afec0b49e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092860"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="eb70d-103">dotnet – Reference k instalaci skriptů</span><span class="sxs-lookup"><span data-stu-id="eb70d-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="eb70d-104">Název</span><span class="sxs-lookup"><span data-stu-id="eb70d-104">Name</span></span>

<span data-ttu-id="eb70d-105">`dotnet-install.ps1` | `dotnet-install.sh`-skript používaný k instalaci .NET Core SDK a sdíleného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="eb70d-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="eb70d-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="eb70d-106">Synopsis</span></span>

<span data-ttu-id="eb70d-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="eb70d-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Channel] [-Version] [-JSonFile] [-InstallDir] [-Architecture]
    [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential]
    [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]
```

<span data-ttu-id="eb70d-108">Linux/macOs:</span><span class="sxs-lookup"><span data-stu-id="eb70d-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh [--channel] [--version] [--jsonfile] [--install-dir] [--architecture]
    [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential]
    [--runtime-id] [--skip-non-versioned-files] [--help]
```

## <a name="description"></a><span data-ttu-id="eb70d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="eb70d-109">Description</span></span>

<span data-ttu-id="eb70d-110">Skripty `dotnet-install` slouží k provedení instalace .NET Core SDK bez správy, která zahrnuje .NET Core CLI a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="eb70d-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="eb70d-111">Doporučujeme používat stabilní verzi skriptů:</span><span class="sxs-lookup"><span data-stu-id="eb70d-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="eb70d-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="eb70d-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="eb70d-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="eb70d-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="eb70d-114">Hlavní užitečnost těchto skriptů je ve scénářích automatizace a v instalacích bez správy.</span><span class="sxs-lookup"><span data-stu-id="eb70d-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="eb70d-115">Existují dva skripty: jeden je PowerShellový skript, který funguje ve Windows, a druhý je bash skript, který funguje na Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="eb70d-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="eb70d-116">Oba skripty mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="eb70d-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="eb70d-117">Skript bash také čte přepínače prostředí PowerShell, takže můžete použít přepínače prostředí PowerShell se skriptem v systémech Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="eb70d-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="eb70d-118">Instalační skripty stáhnou soubor ZIP/tarballu z buildu CLI a budou pokračovat v jeho instalaci buď ve výchozím umístění, nebo v umístění určeném parametrem `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="eb70d-119">Ve výchozím nastavení stáhnou instalační skripty sadu SDK a nainstaluje ji.</span><span class="sxs-lookup"><span data-stu-id="eb70d-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="eb70d-120">Pokud chcete získat pouze sdílený modul runtime, zadejte argument `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="eb70d-121">Ve výchozím nastavení skript přidá umístění instalace do $PATH pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="eb70d-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="eb70d-122">Přepsat toto výchozí chování zadáním argumentu `-NoPath|--no-path`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="eb70d-123">Před spuštěním skriptu nainstalujte požadované [závislosti](../install/dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="eb70d-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="eb70d-124">Konkrétní verzi můžete nainstalovat pomocí argumentu `-Version|--version`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="eb70d-125">Verze musí být zadána jako verze se třemi částmi (například `2.1.0`).</span><span class="sxs-lookup"><span data-stu-id="eb70d-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="eb70d-126">Pokud není k dispozici, používá `latest` verzi.</span><span class="sxs-lookup"><span data-stu-id="eb70d-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="eb70d-127">Možnosti</span><span class="sxs-lookup"><span data-stu-id="eb70d-127">Options</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="eb70d-128">Určuje zdrojový kanál pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="eb70d-128">Specifies the source channel for the installation.</span></span> <span data-ttu-id="eb70d-129">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="eb70d-129">The possible values are:</span></span>

  - <span data-ttu-id="eb70d-130">`Current` – aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="eb70d-130">`Current` - Most current release.</span></span>
  - <span data-ttu-id="eb70d-131">`LTS` – kanál dlouhodobé podpory (aktuálně podporovaná verze).</span><span class="sxs-lookup"><span data-stu-id="eb70d-131">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="eb70d-132">Verze se dvěma částmi ve formátu X. Y představující specifickou verzi (například `2.1` nebo `3.0`).</span><span class="sxs-lookup"><span data-stu-id="eb70d-132">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="eb70d-133">Název větve: například `release/3.1.1xx` nebo `master` (pro noční vydání).</span><span class="sxs-lookup"><span data-stu-id="eb70d-133">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="eb70d-134">Tuto možnost použijte, pokud chcete nainstalovat verzi z kanálu verze Preview.</span><span class="sxs-lookup"><span data-stu-id="eb70d-134">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="eb70d-135">Použijte název kanálu, který je uvedený v části [instalátory a binární soubory](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="eb70d-135">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="eb70d-136">Výchozí hodnota je `LTS`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-136">The default value is `LTS`.</span></span> <span data-ttu-id="eb70d-137">Další informace o kanálech podpory rozhraní .NET najdete na stránce [zásady podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="eb70d-137">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="eb70d-138">Představuje konkrétní verzi buildu.</span><span class="sxs-lookup"><span data-stu-id="eb70d-138">Represents a specific build version.</span></span> <span data-ttu-id="eb70d-139">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="eb70d-139">The possible values are:</span></span>

  - <span data-ttu-id="eb70d-140">`latest` – nejnovější sestavení kanálu (používá se s možností `-Channel`)</span><span class="sxs-lookup"><span data-stu-id="eb70d-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="eb70d-141">`coherent` – nejnovější souvislé sestavení na kanálu; používá nejnovější kombinaci stabilního balíčku (používá se s názvem větve `-Channel` možností).</span><span class="sxs-lookup"><span data-stu-id="eb70d-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="eb70d-142">Verze se třemi částmi ve formátu X. Y. Z představující specifickou verzi buildu; nahrazuje možnost `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="eb70d-143">Například: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="eb70d-144">Pokud není zadaný, `-Version` výchozí nastavení `latest`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="eb70d-145">Určuje cestu k souboru [Global. JSON](global-json.md) , který se použije k určení verze sady SDK.</span><span class="sxs-lookup"><span data-stu-id="eb70d-145">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="eb70d-146">Soubor *Global. JSON* musí mít hodnotu pro `sdk:version`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-146">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="eb70d-147">Určuje instalační cestu.</span><span class="sxs-lookup"><span data-stu-id="eb70d-147">Specifies the installation path.</span></span> <span data-ttu-id="eb70d-148">Adresář se vytvoří, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="eb70d-148">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="eb70d-149">Výchozí hodnota je *%localappdata%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="eb70d-149">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="eb70d-150">Binární soubory jsou umístěny přímo v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="eb70d-150">Binaries are placed directly in this directory.</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="eb70d-151">Architektura binárních souborů .NET Core, které se mají nainstalovat</span><span class="sxs-lookup"><span data-stu-id="eb70d-151">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="eb70d-152">Možné hodnoty jsou `<auto>`, `amd64`, `x64`, `x86`, `arm64`a `arm`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-152">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="eb70d-153">Výchozí hodnota je `<auto>`, která představuje aktuálně běžící architekturu OS.</span><span class="sxs-lookup"><span data-stu-id="eb70d-153">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="eb70d-154">Tento parametr je zastaralý a v budoucí verzi skriptu ho můžete odebrat.</span><span class="sxs-lookup"><span data-stu-id="eb70d-154">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="eb70d-155">Doporučená alternativa je `-Runtime|--runtime` možnost.</span><span class="sxs-lookup"><span data-stu-id="eb70d-155">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="eb70d-156">Nainstaluje jenom sdílené běhové bity, ne celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="eb70d-156">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="eb70d-157">Tato možnost je ekvivalentní s určením `-Runtime|--runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-157">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="eb70d-158">Nainstaluje pouze sdílený modul runtime, nikoli celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="eb70d-158">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="eb70d-159">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="eb70d-159">The possible values are:</span></span>

  - <span data-ttu-id="eb70d-160">`dotnet` – `Microsoft.NETCore.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="eb70d-160">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="eb70d-161">`aspnetcore` – `Microsoft.AspNetCore.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="eb70d-161">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="eb70d-162">`windowsdesktop` – `Microsoft.WindowsDesktop.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="eb70d-162">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="eb70d-163">Když se tato nastavení nastaví, skript neprovede instalaci.</span><span class="sxs-lookup"><span data-stu-id="eb70d-163">If set, the script won't perform the installation.</span></span> <span data-ttu-id="eb70d-164">Místo toho zobrazí příkazový řádek, který se má použít k konzistentně instalaci požadované verze .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="eb70d-164">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="eb70d-165">Například pokud zadáte `latest`verze, zobrazí se odkaz s konkrétní verzí, aby tento příkaz bylo možné použít ve skriptu sestavení deterministické.</span><span class="sxs-lookup"><span data-stu-id="eb70d-165">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="eb70d-166">Také se zobrazí umístění binárního souboru, pokud dáváte přednost instalaci nebo stažení.</span><span class="sxs-lookup"><span data-stu-id="eb70d-166">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="eb70d-167">Je-li nastavena, instalační složka není exportována do cesty pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="eb70d-167">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="eb70d-168">Ve výchozím nastavení skript upraví cestu, která zpřístupní .NET Core CLI hned po instalaci.</span><span class="sxs-lookup"><span data-stu-id="eb70d-168">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="eb70d-169">Zobrazí diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="eb70d-169">Displays diagnostics information.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="eb70d-170">Určuje adresu URL pro instalační službu Azure feed.</span><span class="sxs-lookup"><span data-stu-id="eb70d-170">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="eb70d-171">Doporučujeme, abyste tuto hodnotu nezměnili.</span><span class="sxs-lookup"><span data-stu-id="eb70d-171">We recommended that you don't change this value.</span></span> <span data-ttu-id="eb70d-172">Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-172">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="eb70d-173">Umožňuje změnit adresu URL informačního kanálu neuloženého v mezipaměti, který používá tento instalační program.</span><span class="sxs-lookup"><span data-stu-id="eb70d-173">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="eb70d-174">Doporučujeme, abyste tuto hodnotu nezměnili.</span><span class="sxs-lookup"><span data-stu-id="eb70d-174">We recommended that you don't change this value.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="eb70d-175">Zakáže stahování z [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a používá neuložené kanály přímo.</span><span class="sxs-lookup"><span data-stu-id="eb70d-175">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="eb70d-176">Slouží jako řetězec dotazu, který se má připojit k datovému kanálu Azure.</span><span class="sxs-lookup"><span data-stu-id="eb70d-176">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="eb70d-177">Umožňuje změnit adresu URL tak, aby používala neveřejné účty úložiště BLOB.</span><span class="sxs-lookup"><span data-stu-id="eb70d-177">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--runtime-id`**

  <span data-ttu-id="eb70d-178">Určuje [identifikátor modulu runtime](../rid-catalog.md) , pro který jsou nástroje nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="eb70d-178">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="eb70d-179">Pro přenosné Linuxy použijte `linux-x64`.</span><span class="sxs-lookup"><span data-stu-id="eb70d-179">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="eb70d-180">(Platí jenom pro Linux/macOS)</span><span class="sxs-lookup"><span data-stu-id="eb70d-180">(Only valid for Linux/macOS)</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="eb70d-181">Pokud je tato nastavení nastavena, instalační program při vytváření webových požadavků používá proxy server.</span><span class="sxs-lookup"><span data-stu-id="eb70d-181">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="eb70d-182">(Platí jenom pro Windows)</span><span class="sxs-lookup"><span data-stu-id="eb70d-182">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="eb70d-183">Pokud je nastaveno, instalační program při použití adresy proxy používá přihlašovací údaje aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="eb70d-183">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="eb70d-184">(Platí jenom pro Windows)</span><span class="sxs-lookup"><span data-stu-id="eb70d-184">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="eb70d-185">Přeskočí instalaci souborů bez verze, jako je například *dotnet. exe*, pokud již existují.</span><span class="sxs-lookup"><span data-stu-id="eb70d-185">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="eb70d-186">Vytiskne nápovědu pro skript.</span><span class="sxs-lookup"><span data-stu-id="eb70d-186">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="eb70d-187">Příklady</span><span class="sxs-lookup"><span data-stu-id="eb70d-187">Examples</span></span>

- <span data-ttu-id="eb70d-188">Nainstalujte nejnovější dlouhodobou podporovanou verzi (LTS) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="eb70d-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="eb70d-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="eb70d-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="eb70d-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="eb70d-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="eb70d-191">Nainstalujte nejnovější verzi z kanálu 3,1 do zadaného umístění:</span><span class="sxs-lookup"><span data-stu-id="eb70d-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="eb70d-192">Windows:</span><span class="sxs-lookup"><span data-stu-id="eb70d-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="eb70d-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="eb70d-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="eb70d-194">Instalace verze 3.0.0 sdíleného modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="eb70d-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="eb70d-195">Windows:</span><span class="sxs-lookup"><span data-stu-id="eb70d-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="eb70d-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="eb70d-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="eb70d-197">Získání skriptu a instalace verze 2.1.2 za podnikovým proxy serverem (pouze Windows):</span><span class="sxs-lookup"><span data-stu-id="eb70d-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="eb70d-198">Získání skriptu a instalace .NET Core CLI v jednom-linii příkladech:</span><span class="sxs-lookup"><span data-stu-id="eb70d-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="eb70d-199">Windows:</span><span class="sxs-lookup"><span data-stu-id="eb70d-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="eb70d-200">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="eb70d-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="eb70d-201">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb70d-201">See also</span></span>

- [<span data-ttu-id="eb70d-202">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="eb70d-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="eb70d-203">Archiv rozhraní .NET Core Runtime a sady SDK ke stažení</span><span class="sxs-lookup"><span data-stu-id="eb70d-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
