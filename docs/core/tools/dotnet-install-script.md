---
title: dotnet-install scripts
description: Přečtěte si o dotnet – instalace skriptů pro instalaci nástrojů .NET Core CLI a sdíleného modulu runtime.
ms.date: 01/16/2019
ms.openlocfilehash: 765141ae92645db448ac7c9c3448a79b895faac6
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964351"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="38d4d-103">dotnet – Reference k instalaci skriptů</span><span class="sxs-lookup"><span data-stu-id="38d4d-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="38d4d-104">Name</span><span class="sxs-lookup"><span data-stu-id="38d4d-104">Name</span></span>

<span data-ttu-id="38d4d-105">`dotnet-install.ps1` | `dotnet-install.sh`-skript používaný k instalaci nástrojů .NET Core CLI a sdíleného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="38d4d-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="38d4d-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="38d4d-106">Synopsis</span></span>

<span data-ttu-id="38d4d-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="38d4d-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

<span data-ttu-id="38d4d-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="38d4d-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a><span data-ttu-id="38d4d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="38d4d-109">Description</span></span>

<span data-ttu-id="38d4d-110">Skripty `dotnet-install` slouží k provedení instalace .NET Core SDK bez správy, která zahrnuje nástroje .NET Core CLI a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="38d4d-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="38d4d-111">Doporučujeme používat stabilní verzi, která je hostována na [hlavním webu .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="38d4d-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="38d4d-112">K přímým cestám ke skriptům patří:</span><span class="sxs-lookup"><span data-stu-id="38d4d-112">The direct paths to the scripts are:</span></span>

- <span data-ttu-id="38d4d-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="38d4d-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
- <span data-ttu-id="38d4d-114"><https://dot.net/v1/dotnet-install.ps1> (PowerShell, Windows)</span><span class="sxs-lookup"><span data-stu-id="38d4d-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="38d4d-115">Hlavní užitečnost těchto skriptů je ve scénářích automatizace a v instalacích bez správy.</span><span class="sxs-lookup"><span data-stu-id="38d4d-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="38d4d-116">Existují dva skripty: jeden je PowerShellový skript, který funguje ve Windows, a druhý je bash skript, který funguje na Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="38d4d-116">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="38d4d-117">Oba skripty mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="38d4d-117">Both scripts have the same behavior.</span></span> <span data-ttu-id="38d4d-118">Skript bash také čte přepínače prostředí PowerShell, takže můžete použít přepínače prostředí PowerShell se skriptem v systémech Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="38d4d-118">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="38d4d-119">Instalační skripty stáhnou soubor ZIP/tarballu z buildu CLI a budou pokračovat v jeho instalaci buď ve výchozím umístění, nebo v umístění určeném parametrem `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-119">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="38d4d-120">Ve výchozím nastavení stáhnou instalační skripty sadu SDK a nainstaluje ji.</span><span class="sxs-lookup"><span data-stu-id="38d4d-120">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="38d4d-121">Pokud chcete získat pouze sdílený modul runtime, zadejte argument `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-121">If you wish to only obtain the shared runtime, specify the `--runtime` argument.</span></span>

<span data-ttu-id="38d4d-122">Ve výchozím nastavení skript přidá umístění instalace do $PATH pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="38d4d-122">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="38d4d-123">Přepsat toto výchozí chování zadáním argumentu `--no-path`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-123">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="38d4d-124">Před spuštěním skriptu nainstalujte požadované [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="38d4d-124">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="38d4d-125">Konkrétní verzi můžete nainstalovat pomocí argumentu `--version`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-125">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="38d4d-126">Verze musí být zadaná jako verze se třemi částmi (například 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="38d4d-126">The version must be specified as a three-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="38d4d-127">Pokud není k dispozici, používá `latest` verzi.</span><span class="sxs-lookup"><span data-stu-id="38d4d-127">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="38d4d-128">Možnosti</span><span class="sxs-lookup"><span data-stu-id="38d4d-128">Options</span></span>

- **`-Channel <CHANNEL>`**

  <span data-ttu-id="38d4d-129">Určuje zdrojový kanál pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="38d4d-129">Specifies the source channel for the installation.</span></span> <span data-ttu-id="38d4d-130">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="38d4d-130">The possible values are:</span></span>

  - <span data-ttu-id="38d4d-131">`Current` – aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="38d4d-131">`Current` - Most current release.</span></span>
  - <span data-ttu-id="38d4d-132">`LTS` – kanál dlouhodobé podpory (aktuálně podporovaná verze).</span><span class="sxs-lookup"><span data-stu-id="38d4d-132">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="38d4d-133">Verze se dvěma částmi ve formátu X. Y představující specifickou verzi (například `2.0` nebo `1.0`).</span><span class="sxs-lookup"><span data-stu-id="38d4d-133">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`).</span></span>
  - <span data-ttu-id="38d4d-134">Název větve</span><span class="sxs-lookup"><span data-stu-id="38d4d-134">Branch name.</span></span> <span data-ttu-id="38d4d-135">Například `release/2.0.0`, `release/2.0.0-preview2`nebo `master` (pro noční vydání).</span><span class="sxs-lookup"><span data-stu-id="38d4d-135">For example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` (for nightly releases).</span></span>

  <span data-ttu-id="38d4d-136">Výchozí hodnota je `LTS`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-136">The default value is `LTS`.</span></span> <span data-ttu-id="38d4d-137">Další informace o kanálech podpory rozhraní .NET najdete na stránce [zásady podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="38d4d-137">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-Version <VERSION>`**

  <span data-ttu-id="38d4d-138">Představuje konkrétní verzi buildu.</span><span class="sxs-lookup"><span data-stu-id="38d4d-138">Represents a specific build version.</span></span> <span data-ttu-id="38d4d-139">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="38d4d-139">The possible values are:</span></span>

  - <span data-ttu-id="38d4d-140">`latest` – nejnovější sestavení kanálu (používá se s možností `-Channel`)</span><span class="sxs-lookup"><span data-stu-id="38d4d-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="38d4d-141">`coherent` – nejnovější souvislé sestavení na kanálu; používá nejnovější kombinaci stabilního balíčku (používá se s názvem větve `-Channel` možností).</span><span class="sxs-lookup"><span data-stu-id="38d4d-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="38d4d-142">Verze se třemi částmi ve formátu X. Y. Z představující specifickou verzi buildu; nahrazuje možnost `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="38d4d-143">Například: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="38d4d-144">Pokud není zadaný, `-Version` výchozí nastavení `latest`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-InstallDir <DIRECTORY>`**

  <span data-ttu-id="38d4d-145">Určuje instalační cestu.</span><span class="sxs-lookup"><span data-stu-id="38d4d-145">Specifies the installation path.</span></span> <span data-ttu-id="38d4d-146">Adresář se vytvoří, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="38d4d-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="38d4d-147">Výchozí hodnota je *%localappdata%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="38d4d-147">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="38d4d-148">Binární soubory jsou umístěny přímo v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="38d4d-148">Binaries are placed directly in this directory.</span></span>

- **`-Architecture <ARCHITECTURE>`**

  <span data-ttu-id="38d4d-149">Architektura binárních souborů .NET Core, které se mají nainstalovat</span><span class="sxs-lookup"><span data-stu-id="38d4d-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="38d4d-150">Možné hodnoty jsou `<auto>`, `amd64`, `x64`, `x86`, `arm64`a `arm`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-150">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="38d4d-151">Výchozí hodnota je `<auto>`, která představuje aktuálně běžící architekturu OS.</span><span class="sxs-lookup"><span data-stu-id="38d4d-151">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime`**

  > [!NOTE]
  > <span data-ttu-id="38d4d-152">Tento parametr je zastaralý a v budoucí verzi skriptu ho můžete odebrat.</span><span class="sxs-lookup"><span data-stu-id="38d4d-152">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="38d4d-153">Doporučená alternativa je `Runtime` možnost.</span><span class="sxs-lookup"><span data-stu-id="38d4d-153">The recommended alternative is the `Runtime` option.</span></span>

  <span data-ttu-id="38d4d-154">Nainstaluje jenom sdílené běhové bity, ne celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="38d4d-154">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="38d4d-155">Jedná se o ekvivalent určení `-Runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-155">This is equivalent to specifying `-Runtime dotnet`.</span></span>

- **`-Runtime <RUNTIME>`**

  <span data-ttu-id="38d4d-156">Nainstaluje pouze sdílený modul runtime, nikoli celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="38d4d-156">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="38d4d-157">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="38d4d-157">The possible values are:</span></span>

  - <span data-ttu-id="38d4d-158">`dotnet` – `Microsoft.NETCore.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="38d4d-158">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="38d4d-159">`aspnetcore` – `Microsoft.AspNetCore.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="38d4d-159">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>

- **`-DryRun`**

  <span data-ttu-id="38d4d-160">Když se tato nastavení nastaví, skript neprovede instalaci.</span><span class="sxs-lookup"><span data-stu-id="38d4d-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="38d4d-161">Místo toho zobrazí příkazový řádek, který se má použít k konzistentně instalaci požadované verze .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="38d4d-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="38d4d-162">Například pokud zadáte `latest`verze, zobrazí se odkaz s konkrétní verzí, aby tento příkaz bylo možné použít ve skriptu sestavení deterministické.</span><span class="sxs-lookup"><span data-stu-id="38d4d-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="38d4d-163">Také se zobrazí umístění binárního souboru, pokud dáváte přednost instalaci nebo stažení.</span><span class="sxs-lookup"><span data-stu-id="38d4d-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath`**

  <span data-ttu-id="38d4d-164">Je-li nastavena, instalační složka není exportována do cesty pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="38d4d-164">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="38d4d-165">Ve výchozím nastavení skript upraví cestu, která zpřístupňuje nástroje rozhraní příkazového řádku hned po instalaci.</span><span class="sxs-lookup"><span data-stu-id="38d4d-165">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

- **`-Verbose`**

  <span data-ttu-id="38d4d-166">Zobrazí diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="38d4d-166">Displays diagnostics information.</span></span>

- **`-AzureFeed`**

  <span data-ttu-id="38d4d-167">Určuje adresu URL pro instalační službu Azure feed.</span><span class="sxs-lookup"><span data-stu-id="38d4d-167">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="38d4d-168">Doporučujeme, abyste tuto hodnotu nezměnili.</span><span class="sxs-lookup"><span data-stu-id="38d4d-168">We recommended that you don't change this value.</span></span> <span data-ttu-id="38d4d-169">Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="38d4d-169">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed`**

  <span data-ttu-id="38d4d-170">Umožňuje změnit adresu URL informačního kanálu neuloženého v mezipaměti, který používá tento instalační program.</span><span class="sxs-lookup"><span data-stu-id="38d4d-170">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="38d4d-171">Doporučujeme, abyste tuto hodnotu nezměnili.</span><span class="sxs-lookup"><span data-stu-id="38d4d-171">We recommended that you don't change this value.</span></span>

- **`-NoCdn`**

  <span data-ttu-id="38d4d-172">Zakáže stahování z [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a používá neuložené kanály přímo.</span><span class="sxs-lookup"><span data-stu-id="38d4d-172">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential`**

  <span data-ttu-id="38d4d-173">Slouží jako řetězec dotazu, který se má připojit k datovému kanálu Azure.</span><span class="sxs-lookup"><span data-stu-id="38d4d-173">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="38d4d-174">Umožňuje změnit adresu URL tak, aby používala neveřejné účty úložiště BLOB.</span><span class="sxs-lookup"><span data-stu-id="38d4d-174">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="38d4d-175">Pokud je tato nastavení nastavena, instalační program při vytváření webových požadavků používá proxy server.</span><span class="sxs-lookup"><span data-stu-id="38d4d-175">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="38d4d-176">(Platí jenom pro Windows)</span><span class="sxs-lookup"><span data-stu-id="38d4d-176">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="38d4d-177">Pokud je nastaveno, instalační program při použití adresy proxy používá přihlašovací údaje aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="38d4d-177">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="38d4d-178">(Platí jenom pro Windows)</span><span class="sxs-lookup"><span data-stu-id="38d4d-178">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles`**

  <span data-ttu-id="38d4d-179">Přeskočí instalaci souborů bez verze, jako je například *dotnet. exe*, pokud již existují.</span><span class="sxs-lookup"><span data-stu-id="38d4d-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help`**

  <span data-ttu-id="38d4d-180">Vytiskne nápovědu pro skript.</span><span class="sxs-lookup"><span data-stu-id="38d4d-180">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="38d4d-181">Příklady</span><span class="sxs-lookup"><span data-stu-id="38d4d-181">Examples</span></span>

- <span data-ttu-id="38d4d-182">Nainstalujte nejnovější dlouhodobou podporovanou verzi (LTS) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="38d4d-182">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="38d4d-183">Windows:</span><span class="sxs-lookup"><span data-stu-id="38d4d-183">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="38d4d-184">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="38d4d-184">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="38d4d-185">Nainstalujte nejnovější verzi z kanálu 2,0 do zadaného umístění:</span><span class="sxs-lookup"><span data-stu-id="38d4d-185">Install the latest version from 2.0 channel to the specified location:</span></span>

  <span data-ttu-id="38d4d-186">Windows:</span><span class="sxs-lookup"><span data-stu-id="38d4d-186">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  <span data-ttu-id="38d4d-187">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="38d4d-187">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

- <span data-ttu-id="38d4d-188">Instalace verze 1.1.0 sdíleného modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="38d4d-188">Install the 1.1.0 version of the shared runtime:</span></span>

  <span data-ttu-id="38d4d-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="38d4d-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  <span data-ttu-id="38d4d-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="38d4d-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

- <span data-ttu-id="38d4d-191">Získání skriptu a instalace verze 2.1.2 za podnikovým proxy serverem (pouze Windows):</span><span class="sxs-lookup"><span data-stu-id="38d4d-191">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="38d4d-192">Získání skriptu a instalace .NET Core CLI v jednom-linii příkladech:</span><span class="sxs-lookup"><span data-stu-id="38d4d-192">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="38d4d-193">Windows:</span><span class="sxs-lookup"><span data-stu-id="38d4d-193">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="38d4d-194">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="38d4d-194">macOS/Linux:</span></span>

  ```bash
  curl -ssl https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="38d4d-195">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38d4d-195">See also</span></span>

- [<span data-ttu-id="38d4d-196">Verze .NET Core</span><span class="sxs-lookup"><span data-stu-id="38d4d-196">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="38d4d-197">Archiv rozhraní .NET Core Runtime a sady SDK ke stažení</span><span class="sxs-lookup"><span data-stu-id="38d4d-197">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
