---
title: DotNet – instalačních skriptů
description: Další informace o dotnet instalačních skriptů k instalaci nástroje rozhraní příkazového řádku .NET Core a sdílený modul runtime.
ms.date: 01/16/2019
ms.openlocfilehash: f796ac494c0be5458b3ea192e809a4d875bcc6dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608786"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="fa16d-103">odkazovat na DotNet instalačních skriptů</span><span class="sxs-lookup"><span data-stu-id="fa16d-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="fa16d-104">Název</span><span class="sxs-lookup"><span data-stu-id="fa16d-104">Name</span></span>

<span data-ttu-id="fa16d-105">`dotnet-install.ps1` | `dotnet-install.sh` -Skriptu pro instalaci nástroje rozhraní příkazového řádku .NET Core a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="fa16d-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fa16d-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="fa16d-106">Synopsis</span></span>

<span data-ttu-id="fa16d-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="fa16d-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

<span data-ttu-id="fa16d-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="fa16d-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a><span data-ttu-id="fa16d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fa16d-109">Description</span></span>

<span data-ttu-id="fa16d-110">`dotnet-install` Skripty se používají k provedení instalace bez oprávnění správce systému .NET Core SDK, které zahrnují nástroje příkazového řádku .NET Core a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="fa16d-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="fa16d-111">Doporučujeme použít stabilní verzi, která je hostována na [hlavní webové stránky .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="fa16d-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="fa16d-112">Přímé cesty pro skripty jsou:</span><span class="sxs-lookup"><span data-stu-id="fa16d-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="fa16d-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="fa16d-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
* <span data-ttu-id="fa16d-114"><https://dot.net/v1/dotnet-install.ps1> (Prostředí Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="fa16d-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="fa16d-115">Hlavní užitečnost tyto skripty se scénáře automatizace a zařízení bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="fa16d-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="fa16d-116">Existují dva skripty: jeden je skript prostředí PowerShell, který funguje ve Windows a druhá je skript bash, která funguje v systému Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="fa16d-116">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="fa16d-117">Skripty mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="fa16d-117">Both scripts have the same behavior.</span></span> <span data-ttu-id="fa16d-118">Skriptu bash také přečte přepínače prostředí PowerShell, takže přepínače prostředí PowerShell můžete použít skript v systémech Linux nebo macOS s.</span><span class="sxs-lookup"><span data-stu-id="fa16d-118">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="fa16d-119">Instalační skripty stáhne soubor ZIP/tarballu z buildů rozhraní příkazového řádku a pokračovat v instalaci je ve výchozím umístění nebo v umístění určeném `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="fa16d-119">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="fa16d-120">Ve výchozím nastavení instalační skripty stáhnout sadu SDK a nainstalujte ho.</span><span class="sxs-lookup"><span data-stu-id="fa16d-120">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="fa16d-121">Pokud chcete jen získat sdílený modul runtime, zadejte `--shared-runtime` argument.</span><span class="sxs-lookup"><span data-stu-id="fa16d-121">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span>

<span data-ttu-id="fa16d-122">Ve výchozím nastavení přidá skript umístění instalace $PATH pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="fa16d-122">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="fa16d-123">Toto výchozí chování přepsat tak, že zadáte `--no-path` argument.</span><span class="sxs-lookup"><span data-stu-id="fa16d-123">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="fa16d-124">Před spuštěním skriptu, instalaci požadovaných [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="fa16d-124">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="fa16d-125">Můžete nainstalovat konkrétní verzi pomocí `--version` argument.</span><span class="sxs-lookup"><span data-stu-id="fa16d-125">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="fa16d-126">Verze musí být zadán jako část třídílné verze (například 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="fa16d-126">The version must be specified as a three-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="fa16d-127">Pokud se nezadá, použije `latest` verze.</span><span class="sxs-lookup"><span data-stu-id="fa16d-127">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="fa16d-128">Možnosti</span><span class="sxs-lookup"><span data-stu-id="fa16d-128">Options</span></span>

* **`-Channel <CHANNEL>`**

  <span data-ttu-id="fa16d-129">Určuje zdroj kanálu pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="fa16d-129">Specifies the source channel for the installation.</span></span> <span data-ttu-id="fa16d-130">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="fa16d-130">The possible values are:</span></span>

  * <span data-ttu-id="fa16d-131">`Current` -Nejaktuálnější verze.</span><span class="sxs-lookup"><span data-stu-id="fa16d-131">`Current` - Most current release.</span></span>
  * <span data-ttu-id="fa16d-132">`LTS` – Dlouhodobé kanál podpory (nejnovější podporovanou verzi).</span><span class="sxs-lookup"><span data-stu-id="fa16d-132">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  * <span data-ttu-id="fa16d-133">Verze dvěma částmi ve formátu X.Y představující konkrétní verze (například `2.0` nebo `1.0`).</span><span class="sxs-lookup"><span data-stu-id="fa16d-133">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`).</span></span>
  * <span data-ttu-id="fa16d-134">Název větve.</span><span class="sxs-lookup"><span data-stu-id="fa16d-134">Branch name.</span></span> <span data-ttu-id="fa16d-135">Například `release/2.0.0`, `release/2.0.0-preview2`, nebo `master` (pro noční vydání).</span><span class="sxs-lookup"><span data-stu-id="fa16d-135">For example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` (for nightly releases).</span></span>

  <span data-ttu-id="fa16d-136">Výchozí hodnota je `LTS`.</span><span class="sxs-lookup"><span data-stu-id="fa16d-136">The default value is `LTS`.</span></span> <span data-ttu-id="fa16d-137">Další informace o kanály podpory .NET najdete v článku [zásady podpory .NET](https://www.microsoft.com/net/platform/support-policy#dotnet-core) stránky.</span><span class="sxs-lookup"><span data-stu-id="fa16d-137">For more information on .NET support channels, see the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy#dotnet-core) page.</span></span>

* **`-Version <VERSION>`**

  <span data-ttu-id="fa16d-138">Představuje verzi konkrétního sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa16d-138">Represents a specific build version.</span></span> <span data-ttu-id="fa16d-139">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="fa16d-139">The possible values are:</span></span>

  * <span data-ttu-id="fa16d-140">`latest` -Nejnovější build na kanálu (používá se `-Channel` možnost).</span><span class="sxs-lookup"><span data-stu-id="fa16d-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  * <span data-ttu-id="fa16d-141">`coherent` -Nejnovější souvislé sestavení na kanálu; používá kombinaci nejnovější stabilní balíček (používá se název větve `-Channel` možnosti).</span><span class="sxs-lookup"><span data-stu-id="fa16d-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  * <span data-ttu-id="fa16d-142">Verze třemi částmi ve formátu X.Y.Z představující konkrétní sestavení verze; nahrazuje `-Channel` možnost.</span><span class="sxs-lookup"><span data-stu-id="fa16d-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="fa16d-143">Například: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="fa16d-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="fa16d-144">Pokud není zadán, `-Version` výchozí hodnota je `latest`.</span><span class="sxs-lookup"><span data-stu-id="fa16d-144">If not specified, `-Version` defaults to `latest`.</span></span>

* **`-InstallDir <DIRECTORY>`**

  <span data-ttu-id="fa16d-145">Určuje cestu instalace.</span><span class="sxs-lookup"><span data-stu-id="fa16d-145">Specifies the installation path.</span></span> <span data-ttu-id="fa16d-146">Adresář se vytvoří, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="fa16d-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="fa16d-147">Výchozí hodnota je *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="fa16d-147">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="fa16d-148">Binární soubory jsou umístěny přímo v tomto adresáři.</span><span class="sxs-lookup"><span data-stu-id="fa16d-148">Binaries are placed directly in this directory.</span></span>

* **`-Architecture <ARCHITECTURE>`**

  <span data-ttu-id="fa16d-149">Architektury .NET Core binární soubory pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="fa16d-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="fa16d-150">Možné hodnoty jsou `<auto>`, `amd64`, `x64`, `x86`, `arm64`, a `arm`.</span><span class="sxs-lookup"><span data-stu-id="fa16d-150">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="fa16d-151">Výchozí hodnota je `<auto>`, která představuje aktuálně spuštěné Architektura operačního systému.</span><span class="sxs-lookup"><span data-stu-id="fa16d-151">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

* **`-SharedRuntime`**

  > [!NOTE]
  > <span data-ttu-id="fa16d-152">Tento parametr je zastaralá a v budoucí verzi souboru, který může být odebrán.</span><span class="sxs-lookup"><span data-stu-id="fa16d-152">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="fa16d-153">Doporučenou alternativou je `Runtime` možnost.</span><span class="sxs-lookup"><span data-stu-id="fa16d-153">The recommended alternative is the `Runtime` option.</span></span>

  <span data-ttu-id="fa16d-154">Nainstaluje pouze bity sdílený modul runtime, ne celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="fa16d-154">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="fa16d-155">To je ekvivalentní se zadáním `-Runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="fa16d-155">This is equivalent to specifying `-Runtime dotnet`.</span></span>

* **`-Runtime <RUNTIME>`**

  <span data-ttu-id="fa16d-156">Nainstaluje jenom sdílený modul runtime, ne celou sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="fa16d-156">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="fa16d-157">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="fa16d-157">The possible values are:</span></span>

  * <span data-ttu-id="fa16d-158">`dotnet` - `Microsoft.NETCore.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="fa16d-158">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  * <span data-ttu-id="fa16d-159">`aspnetcore` - `Microsoft.AspNetCore.App` sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="fa16d-159">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>

* **`-DryRun`**

  <span data-ttu-id="fa16d-160">Pokud nastavíte, neprovede skriptu instalace.</span><span class="sxs-lookup"><span data-stu-id="fa16d-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="fa16d-161">Místo toho zobrazí jaké příkazový řádek použitý k instalaci konzistentně aktuálně požadovanou verzi rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fa16d-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="fa16d-162">Například, pokud zadáte verze `latest`, zobrazí odkaz s konkrétní verzí tak, aby tento příkaz můžete použít nepodmíněně ve skriptu buildu.</span><span class="sxs-lookup"><span data-stu-id="fa16d-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="fa16d-163">Pokud chcete nainstalovat nebo stáhnout sami umístění binárního souboru, zobrazí se také.</span><span class="sxs-lookup"><span data-stu-id="fa16d-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

* **`-NoPath`**

  <span data-ttu-id="fa16d-164">Pokud sada instalační složky sady neexportoval k cestě pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="fa16d-164">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="fa16d-165">Ve výchozím nastavení skript změní cesty, která díky nástrojům rozhraní příkazového řádku k dispozici okamžitě po instalaci.</span><span class="sxs-lookup"><span data-stu-id="fa16d-165">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

* **`-Verbose`**

  <span data-ttu-id="fa16d-166">Zobrazí diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="fa16d-166">Displays diagnostics information.</span></span>

* **`-AzureFeed`**

  <span data-ttu-id="fa16d-167">Určuje že adresu URL pro Azure informačního kanálu do instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="fa16d-167">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="fa16d-168">Doporučujeme tuto hodnotu nechcete změnit.</span><span class="sxs-lookup"><span data-stu-id="fa16d-168">We recommended that you don't change this value.</span></span> <span data-ttu-id="fa16d-169">Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="fa16d-169">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

* **`-UncachedFeed`**

  <span data-ttu-id="fa16d-170">Umožňuje změnit adresu URL bez mezipaměti kanál používá tento instalační program.</span><span class="sxs-lookup"><span data-stu-id="fa16d-170">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="fa16d-171">Doporučujeme tuto hodnotu nechcete změnit.</span><span class="sxs-lookup"><span data-stu-id="fa16d-171">We recommended that you don't change this value.</span></span>

* **`-NoCdn`**

  <span data-ttu-id="fa16d-172">Zakáže stahování [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) a mezipamětí informační kanál používá přímo.</span><span class="sxs-lookup"><span data-stu-id="fa16d-172">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

* **`-FeedCredential`**

  <span data-ttu-id="fa16d-173">Použít jako řetězec dotazu pro připojení k Azure informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="fa16d-173">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="fa16d-174">To umožňuje změnit adresu URL, aby používaly účty úložiště blob neveřejné.</span><span class="sxs-lookup"><span data-stu-id="fa16d-174">It allows changing the URL to use non-public blob storage accounts.</span></span>

* **`-ProxyAddress`**

  <span data-ttu-id="fa16d-175">Pokud sada, instalační program používá proxy server při vytváření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="fa16d-175">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="fa16d-176">(Platí jenom pro Windows)</span><span class="sxs-lookup"><span data-stu-id="fa16d-176">(Only valid for Windows)</span></span>

* **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="fa16d-177">Pokud sada, instalační program používá přihlašovací údaje aktuálního uživatele při použití adresa proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="fa16d-177">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="fa16d-178">(Platí jenom pro Windows)</span><span class="sxs-lookup"><span data-stu-id="fa16d-178">(Only valid for Windows)</span></span>

* **`-SkipNonVersionedFiles`**

  <span data-ttu-id="fa16d-179">Přeskočí instalaci bez správy verzí souborů, jako například *dotnet.exe*, pokud ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="fa16d-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

* **`-Help`**

  <span data-ttu-id="fa16d-180">Vytiskne nápovědy pro skript.</span><span class="sxs-lookup"><span data-stu-id="fa16d-180">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="fa16d-181">Příklady</span><span class="sxs-lookup"><span data-stu-id="fa16d-181">Examples</span></span>

* <span data-ttu-id="fa16d-182">Nainstalujte nejnovější dlouhodobé podporovanou verzi (LTS) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="fa16d-182">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="fa16d-183">Windows:</span><span class="sxs-lookup"><span data-stu-id="fa16d-183">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="fa16d-184">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="fa16d-184">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

* <span data-ttu-id="fa16d-185">Nainstalujte nejnovější verzi z 2.0 kanál do zadaného umístění:</span><span class="sxs-lookup"><span data-stu-id="fa16d-185">Install the latest version from 2.0 channel to the specified location:</span></span>

  <span data-ttu-id="fa16d-186">Windows:</span><span class="sxs-lookup"><span data-stu-id="fa16d-186">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  <span data-ttu-id="fa16d-187">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="fa16d-187">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

* <span data-ttu-id="fa16d-188">Nainstalujte 1.1.0 verzi sdílený modul runtime:</span><span class="sxs-lookup"><span data-stu-id="fa16d-188">Install the 1.1.0 version of the shared runtime:</span></span>

  <span data-ttu-id="fa16d-189">Windows:</span><span class="sxs-lookup"><span data-stu-id="fa16d-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -SharedRuntime -Version 1.1.0
  ```

  <span data-ttu-id="fa16d-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="fa16d-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --shared-runtime --version 1.1.0
  ```

* <span data-ttu-id="fa16d-191">Získat skript a nainstalovat 2.1.2 verze za firemním proxy (jenom Windows):</span><span class="sxs-lookup"><span data-stu-id="fa16d-191">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

* <span data-ttu-id="fa16d-192">Získat skript a nainstalovat rozhraní příkazového řádku .NET Core one-liner příklady:</span><span class="sxs-lookup"><span data-stu-id="fa16d-192">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="fa16d-193">Windows:</span><span class="sxs-lookup"><span data-stu-id="fa16d-193">Windows:</span></span>

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="fa16d-194">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="fa16d-194">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="fa16d-195">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa16d-195">See also</span></span>

- [<span data-ttu-id="fa16d-196">Verze .NET core</span><span class="sxs-lookup"><span data-stu-id="fa16d-196">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="fa16d-197">.NET core Runtime a sadu SDK stáhněte archiv</span><span class="sxs-lookup"><span data-stu-id="fa16d-197">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
