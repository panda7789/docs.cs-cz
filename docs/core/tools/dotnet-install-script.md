---
title: dotnet-install scripts
description: Přečtěte si o dotnet – instalace skriptů pro instalaci nástrojů .NET Core CLI a sdíleného modulu runtime.
ms.date: 01/16/2019
ms.openlocfilehash: ed1a3341e678b405ae4aca35e3b49ada89eb069a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253901"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="ffcd6-103">dotnet – Reference k instalaci skriptů</span><span class="sxs-lookup"><span data-stu-id="ffcd6-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="ffcd6-104">Name</span><span class="sxs-lookup"><span data-stu-id="ffcd6-104">Name</span></span>

<span data-ttu-id="ffcd6-105">`dotnet-install.ps1` | `dotnet-install.sh`-Skript použitý k instalaci nástrojů .NET Core CLI a sdíleného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ffcd6-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="ffcd6-106">Synopsis</span></span>

<span data-ttu-id="ffcd6-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

<span data-ttu-id="ffcd6-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a><span data-ttu-id="ffcd6-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ffcd6-109">Description</span></span>

<span data-ttu-id="ffcd6-110">`dotnet-install` Skripty se používají k provedení instalace .NET Core SDK bez správy, která zahrnuje nástroje .NET Core CLI a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="ffcd6-111">Doporučujeme používat stabilní verzi, která je hostována na [hlavním webu .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="ffcd6-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="ffcd6-112">K přímým cestám ke skriptům patří:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-112">The direct paths to the scripts are:</span></span>

- <span data-ttu-id="ffcd6-113"><https://dot.net/v1/dotnet-install.sh>(bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="ffcd6-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
- <span data-ttu-id="ffcd6-114"><https://dot.net/v1/dotnet-install.ps1>(PowerShell, Windows)</span><span class="sxs-lookup"><span data-stu-id="ffcd6-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="ffcd6-115">Hlavní užitečnost těchto skriptů je ve scénářích automatizace a v instalacích bez správy.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="ffcd6-116">Existují dva skripty: jeden je PowerShellový skript, který funguje ve Windows, a druhý je bash skript, který funguje na Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-116">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="ffcd6-117">Oba skripty mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-117">Both scripts have the same behavior.</span></span> <span data-ttu-id="ffcd6-118">Skript bash také čte přepínače prostředí PowerShell, takže můžete použít přepínače prostředí PowerShell se skriptem v systémech Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-118">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="ffcd6-119">Instalační skripty stáhnou soubor ZIP/tarballu z buildu CLI a budou pokračovat v jeho instalaci buď ve výchozím umístění, nebo v umístění určeném parametrem `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-119">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="ffcd6-120">Ve výchozím nastavení stáhnou instalační skripty sadu SDK a nainstaluje ji.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-120">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="ffcd6-121">Pokud chcete získat pouze sdílený modul runtime, zadejte `--runtime` argument.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-121">If you wish to only obtain the shared runtime, specify the `--runtime` argument.</span></span>

<span data-ttu-id="ffcd6-122">Ve výchozím nastavení skript přidá umístění instalace do $PATH pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-122">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="ffcd6-123">Přepsat toto výchozí chování zadáním `--no-path` argumentu.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-123">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="ffcd6-124">Před spuštěním skriptu nainstalujte požadované [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="ffcd6-124">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="ffcd6-125">Konkrétní verzi můžete nainstalovat pomocí `--version` argumentu.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-125">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="ffcd6-126">Verze musí být zadaná jako verze se třemi částmi (například 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="ffcd6-126">The version must be specified as a three-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="ffcd6-127">Pokud není zadaný, použije se `latest` verze.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-127">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="ffcd6-128">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ffcd6-128">Options</span></span>

- **`-Channel <CHANNEL>`**

  <span data-ttu-id="ffcd6-129">Určuje zdrojový kanál pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-129">Specifies the source channel for the installation.</span></span> <span data-ttu-id="ffcd6-130">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-130">The possible values are:</span></span>

  - <span data-ttu-id="ffcd6-131">`Current`– Nejvíc aktuální verze</span><span class="sxs-lookup"><span data-stu-id="ffcd6-131">`Current` - Most current release.</span></span>
  - <span data-ttu-id="ffcd6-132">`LTS`– Kanál dlouhodobé podpory (aktuálně podporovaná verze).</span><span class="sxs-lookup"><span data-stu-id="ffcd6-132">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="ffcd6-133">Verze se dvěma částmi ve formátu X. Y představující specifickou verzi (například `2.0` nebo `1.0`).</span><span class="sxs-lookup"><span data-stu-id="ffcd6-133">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`).</span></span>
  - <span data-ttu-id="ffcd6-134">Název větve</span><span class="sxs-lookup"><span data-stu-id="ffcd6-134">Branch name.</span></span> <span data-ttu-id="ffcd6-135">Například `release/2.0.0` `master` ,, nebo (pro noční vydání). `release/2.0.0-preview2`</span><span class="sxs-lookup"><span data-stu-id="ffcd6-135">For example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` (for nightly releases).</span></span>

  <span data-ttu-id="ffcd6-136">Výchozí hodnota je `LTS`.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-136">The default value is `LTS`.</span></span> <span data-ttu-id="ffcd6-137">Další informace o kanálech podpory rozhraní .NET najdete na stránce [zásady podpory rozhraní .NET](https://www.microsoft.com/net/platform/support-policy#dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="ffcd6-137">For more information on .NET support channels, see the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy#dotnet-core) page.</span></span>

- **`-Version <VERSION>`**

  <span data-ttu-id="ffcd6-138">Představuje konkrétní verzi buildu.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-138">Represents a specific build version.</span></span> <span data-ttu-id="ffcd6-139">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-139">The possible values are:</span></span>

  - <span data-ttu-id="ffcd6-140">`latest`– Nejnovější sestavení kanálu (používá se s `-Channel` možností)</span><span class="sxs-lookup"><span data-stu-id="ffcd6-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="ffcd6-141">`coherent`-Nejnovější souvislý Build na kanálu; používá nejnovější kombinaci stabilního balíčku (používá se s možnostmi názvu `-Channel` větve).</span><span class="sxs-lookup"><span data-stu-id="ffcd6-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="ffcd6-142">Verze se třemi částmi ve formátu X. Y. Z představující specifickou verzi buildu; `-Channel` nahrazuje možnost.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="ffcd6-143">Například: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="ffcd6-144">Pokud není zadaný, `-Version` `latest`použije se výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-InstallDir <DIRECTORY>`**

  <span data-ttu-id="ffcd6-145">Určuje instalační cestu.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-145">Specifies the installation path.</span></span> <span data-ttu-id="ffcd6-146">Adresář se vytvoří, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="ffcd6-147">Výchozí hodnota je *%localappdata%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-147">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="ffcd6-148">Binární soubory jsou umístěny přímo v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-148">Binaries are placed directly in this directory.</span></span>

- **`-Architecture <ARCHITECTURE>`**

  <span data-ttu-id="ffcd6-149">Architektura binárních souborů .NET Core, které se mají nainstalovat</span><span class="sxs-lookup"><span data-stu-id="ffcd6-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="ffcd6-150">Možné hodnoty jsou `<auto>`, `amd64` `x64`,,, a`arm64` .`arm` `x86`</span><span class="sxs-lookup"><span data-stu-id="ffcd6-150">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="ffcd6-151">Výchozí hodnota je `<auto>`, která představuje aktuálně běžící architekturu OS.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-151">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime`**

  > [!NOTE]
  > <span data-ttu-id="ffcd6-152">Tento parametr je zastaralý a v budoucí verzi skriptu ho můžete odebrat.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-152">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="ffcd6-153">Doporučená alternativa je `Runtime` možnost.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-153">The recommended alternative is the `Runtime` option.</span></span>

  <span data-ttu-id="ffcd6-154">Nainstaluje jenom sdílené běhové bity, ne celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-154">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="ffcd6-155">To je ekvivalentní k zadání `-Runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-155">This is equivalent to specifying `-Runtime dotnet`.</span></span>

- **`-Runtime <RUNTIME>`**

  <span data-ttu-id="ffcd6-156">Nainstaluje pouze sdílený modul runtime, nikoli celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-156">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="ffcd6-157">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-157">The possible values are:</span></span>

  - <span data-ttu-id="ffcd6-158">`dotnet``Microsoft.NETCore.App` – sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-158">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="ffcd6-159">`aspnetcore``Microsoft.AspNetCore.App` – sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-159">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>

- **`-DryRun`**

  <span data-ttu-id="ffcd6-160">Když se tato nastavení nastaví, skript neprovede instalaci.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="ffcd6-161">Místo toho zobrazí příkazový řádek, který se má použít k konzistentně instalaci požadované verze .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="ffcd6-162">Pokud například zadáte verzi `latest`, zobrazí se odkaz s konkrétní verzí, aby se tento příkaz mohl ve skriptu sestavení použít deterministické.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="ffcd6-163">Také se zobrazí umístění binárního souboru, pokud dáváte přednost instalaci nebo stažení.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath`**

  <span data-ttu-id="ffcd6-164">Je-li nastavena, instalační složka není exportována do cesty pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-164">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="ffcd6-165">Ve výchozím nastavení skript upraví cestu, která zpřístupňuje nástroje rozhraní příkazového řádku hned po instalaci.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-165">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

- **`-Verbose`**

  <span data-ttu-id="ffcd6-166">Zobrazí diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-166">Displays diagnostics information.</span></span>

- **`-AzureFeed`**

  <span data-ttu-id="ffcd6-167">Určuje adresu URL pro instalační službu Azure feed.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-167">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="ffcd6-168">Doporučujeme, abyste tuto hodnotu nezměnili.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-168">We recommended that you don't change this value.</span></span> <span data-ttu-id="ffcd6-169">Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-169">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed`**

  <span data-ttu-id="ffcd6-170">Umožňuje změnit adresu URL informačního kanálu neuloženého v mezipaměti, který používá tento instalační program.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-170">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="ffcd6-171">Doporučujeme, abyste tuto hodnotu nezměnili.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-171">We recommended that you don't change this value.</span></span>

- **`-NoCdn`**

  <span data-ttu-id="ffcd6-172">Zakáže stahování z [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a používá neuložené kanály přímo.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-172">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential`**

  <span data-ttu-id="ffcd6-173">Slouží jako řetězec dotazu, který se má připojit k datovému kanálu Azure.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-173">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="ffcd6-174">Umožňuje změnit adresu URL tak, aby používala neveřejné účty úložiště BLOB.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-174">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="ffcd6-175">Pokud je tato nastavení nastavena, instalační program při vytváření webových požadavků používá proxy server.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-175">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="ffcd6-176">(Platí jenom pro Windows)</span><span class="sxs-lookup"><span data-stu-id="ffcd6-176">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="ffcd6-177">Pokud je nastaveno, instalační program při použití adresy proxy používá přihlašovací údaje aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-177">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="ffcd6-178">(Platí jenom pro Windows)</span><span class="sxs-lookup"><span data-stu-id="ffcd6-178">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles`**

  <span data-ttu-id="ffcd6-179">Přeskočí instalaci souborů bez verze, jako je například *dotnet. exe*, pokud již existují.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help`**

  <span data-ttu-id="ffcd6-180">Vytiskne nápovědu pro skript.</span><span class="sxs-lookup"><span data-stu-id="ffcd6-180">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="ffcd6-181">Příklady</span><span class="sxs-lookup"><span data-stu-id="ffcd6-181">Examples</span></span>

- <span data-ttu-id="ffcd6-182">Nainstalujte nejnovější dlouhodobou podporovanou verzi (LTS) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-182">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="ffcd6-183">Windows:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-183">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="ffcd6-184">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-184">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="ffcd6-185">Nainstalujte nejnovější verzi z kanálu 2,0 do zadaného umístění:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-185">Install the latest version from 2.0 channel to the specified location:</span></span>

  <span data-ttu-id="ffcd6-186">Windows:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-186">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  <span data-ttu-id="ffcd6-187">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-187">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

- <span data-ttu-id="ffcd6-188">Instalace verze 1.1.0 sdíleného modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-188">Install the 1.1.0 version of the shared runtime:</span></span>

  <span data-ttu-id="ffcd6-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  <span data-ttu-id="ffcd6-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

- <span data-ttu-id="ffcd6-191">Získání skriptu a instalace verze 2.1.2 za podnikovým proxy serverem (pouze Windows):</span><span class="sxs-lookup"><span data-stu-id="ffcd6-191">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="ffcd6-192">Získání skriptu a instalace .NET Core CLI v jednom-linii příkladech:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-192">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="ffcd6-193">Windows:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-193">Windows:</span></span>

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="ffcd6-194">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-194">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="ffcd6-195">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffcd6-195">See also</span></span>

- [<span data-ttu-id="ffcd6-196">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="ffcd6-196">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="ffcd6-197">Archiv rozhraní .NET Core Runtime a sady SDK ke stažení</span><span class="sxs-lookup"><span data-stu-id="ffcd6-197">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
