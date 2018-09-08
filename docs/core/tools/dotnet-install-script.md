---
title: DotNet – instalačních skriptů
description: Další informace o dotnet instalačních skriptů k instalaci nástroje rozhraní příkazového řádku .NET Core a sdílený modul runtime.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: 8d1c6ebb30bd45575bb61206799c9c3e5c47ff0c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180040"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="26040-103">odkazovat na DotNet instalačních skriptů</span><span class="sxs-lookup"><span data-stu-id="26040-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="26040-104">Název</span><span class="sxs-lookup"><span data-stu-id="26040-104">Name</span></span>

<span data-ttu-id="26040-105">`dotnet-install.ps1` | `dotnet-install.sh` -Skriptu pro instalaci nástroje rozhraní příkazového řádku .NET Core a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="26040-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="26040-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="26040-106">Synopsis</span></span>

<span data-ttu-id="26040-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="26040-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="26040-108">macOS nebo Linux:</span><span class="sxs-lookup"><span data-stu-id="26040-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="26040-109">Popis</span><span class="sxs-lookup"><span data-stu-id="26040-109">Description</span></span>

<span data-ttu-id="26040-110">`dotnet-install` Skripty se používají k provedení instalace bez oprávnění správce systému .NET Core SDK, které zahrnují nástroje příkazového řádku .NET Core a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="26040-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="26040-111">Doporučujeme použít stabilní verzi, která je hostována na [hlavní webové stránky .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="26040-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="26040-112">Přímé cesty pro skripty jsou:</span><span class="sxs-lookup"><span data-stu-id="26040-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="26040-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="26040-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="26040-114">https://dot.net/v1/dotnet-install.ps1 (Prostředí Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="26040-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="26040-115">Hlavní užitečnost tyto skripty se scénáře automatizace a zařízení bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="26040-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="26040-116">Existují dva skripty: jeden je skript prostředí PowerShell, který funguje ve Windows.</span><span class="sxs-lookup"><span data-stu-id="26040-116">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="26040-117">Tento skript je skriptu bash, která funguje v systému Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="26040-117">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="26040-118">Skripty mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="26040-118">Both scripts have the same behavior.</span></span> <span data-ttu-id="26040-119">Skriptu bash také přečte přepínače prostředí PowerShell, takže přepínače prostředí PowerShell můžete použít skript v systémech Linux nebo macOS s.</span><span class="sxs-lookup"><span data-stu-id="26040-119">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="26040-120">Instalační skripty stáhne soubor ZIP/tarballu z buildů rozhraní příkazového řádku a pokračovat v instalaci je ve výchozím umístění nebo v umístění určeném `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="26040-120">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="26040-121">Ve výchozím nastavení instalační skripty stáhnout sadu SDK a nainstalujte ho.</span><span class="sxs-lookup"><span data-stu-id="26040-121">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="26040-122">Pokud chcete jen získat sdílený modul runtime, zadejte `--shared-runtime` argument.</span><span class="sxs-lookup"><span data-stu-id="26040-122">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span>

<span data-ttu-id="26040-123">Ve výchozím nastavení přidá skript umístění instalace $PATH pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="26040-123">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="26040-124">Toto výchozí chování přepsat tak, že zadáte `--no-path` argument.</span><span class="sxs-lookup"><span data-stu-id="26040-124">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="26040-125">Před spuštěním skriptu, instalaci požadovaných [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="26040-125">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="26040-126">Můžete nainstalovat konkrétní verzi pomocí `--version` argument.</span><span class="sxs-lookup"><span data-stu-id="26040-126">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="26040-127">Verze musí být zadán jako část 3 verze (například 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="26040-127">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="26040-128">Pokud tento parametr vynechán, použije `latest` verze.</span><span class="sxs-lookup"><span data-stu-id="26040-128">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="26040-129">Možnosti</span><span class="sxs-lookup"><span data-stu-id="26040-129">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="26040-130">Určuje zdroj kanálu pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="26040-130">Specifies the source channel for the installation.</span></span> <span data-ttu-id="26040-131">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="26040-131">The possible values are:</span></span>

- <span data-ttu-id="26040-132">`Current` -Aktuální verze</span><span class="sxs-lookup"><span data-stu-id="26040-132">`Current` - Current release</span></span>
- <span data-ttu-id="26040-133">`LTS` – Dlouhodobé kanál podpory (aktuální podporovanou verzi)</span><span class="sxs-lookup"><span data-stu-id="26040-133">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="26040-134">Verze dvěma částmi ve formátu X.Y představující konkrétní verze (například `2.0` nebo `1.0`)</span><span class="sxs-lookup"><span data-stu-id="26040-134">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="26040-135">Název větve [například `release/2.0.0`, `release/2.0.0-preview2`, nebo `master` pro informace o novinkách od `master` větev ("vykrvení hrany" noční vydání)]</span><span class="sxs-lookup"><span data-stu-id="26040-135">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="26040-136">Výchozí hodnota je `LTS`.</span><span class="sxs-lookup"><span data-stu-id="26040-136">The default value is `LTS`.</span></span> <span data-ttu-id="26040-137">Další informace o kanály podpory .NET najdete v článku [životní cyklus podpory na .NET Core](https://www.microsoft.com/net/core/support) tématu.</span><span class="sxs-lookup"><span data-stu-id="26040-137">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="26040-138">Představuje verzi konkrétního sestavení.</span><span class="sxs-lookup"><span data-stu-id="26040-138">Represents a specific build version.</span></span> <span data-ttu-id="26040-139">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="26040-139">The possible values are:</span></span>

- <span data-ttu-id="26040-140">`latest` -Nejnovější build na kanálu (používá se `-Channel` možnost)</span><span class="sxs-lookup"><span data-stu-id="26040-140">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="26040-141">`coherent` -Nejnovější souvislé sestavení na kanálu; používá kombinaci nejnovější stabilní balíček (používá se název větve `-Channel` možnosti)</span><span class="sxs-lookup"><span data-stu-id="26040-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="26040-142">Verze třemi částmi ve formátu X.Y.Z představující konkrétní sestavení verze; nahrazuje `-Channel` možnost.</span><span class="sxs-lookup"><span data-stu-id="26040-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="26040-143">Příklad: `2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="26040-143">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="26040-144">Pokud tento parametr vynechán, `-Version` výchozí hodnota je `latest`.</span><span class="sxs-lookup"><span data-stu-id="26040-144">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="26040-145">Určuje cestu instalace.</span><span class="sxs-lookup"><span data-stu-id="26040-145">Specifies the installation path.</span></span> <span data-ttu-id="26040-146">Adresář se vytvoří, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="26040-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="26040-147">Výchozí hodnota je *% LocalAppData %\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="26040-147">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="26040-148">Všimněte si, že binární soubory jsou umístěné přímo v adresáři.</span><span class="sxs-lookup"><span data-stu-id="26040-148">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="26040-149">Architektury .NET Core binární soubory pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="26040-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="26040-150">Možné hodnoty jsou `auto`, `x64`, a `x86`.</span><span class="sxs-lookup"><span data-stu-id="26040-150">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="26040-151">Výchozí hodnota je `auto`, která představuje aktuálně spuštěné Architektura operačního systému.</span><span class="sxs-lookup"><span data-stu-id="26040-151">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="26040-152">Pokud nastavíte, tento přepínač omezuje na sdílený modul runtime instalace.</span><span class="sxs-lookup"><span data-stu-id="26040-152">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="26040-153">Celá sada SDK není nainstalovaná.</span><span class="sxs-lookup"><span data-stu-id="26040-153">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="26040-154">Pokud nastavíte, neprovede skriptu instalace; ale místo toho zobrazí jaké příkazový řádek použitý k instalaci konzistentně aktuálně požadovanou verzi rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="26040-154">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="26040-155">Například pokud zadáte verze `latest`, zobrazí odkaz s konkrétní verzí tak, aby tento příkaz můžete použít nepodmíněně ve skriptu buildu.</span><span class="sxs-lookup"><span data-stu-id="26040-155">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="26040-156">Pokud chcete nainstalovat nebo stáhnout sami umístění binárního souboru, zobrazí se také.</span><span class="sxs-lookup"><span data-stu-id="26040-156">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="26040-157">Pokud nastavíte, předponu/installdir se nebudou exportovat do cesty pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="26040-157">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="26040-158">Ve výchozím nastavení bude skript upravte CESTU, která díky nástrojům rozhraní příkazového řádku k dispozici okamžitě po instalaci.</span><span class="sxs-lookup"><span data-stu-id="26040-158">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="26040-159">Určuje že adresu URL pro Azure informačního kanálu do instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="26040-159">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="26040-160">Nedoporučujeme tuto hodnotu změnit.</span><span class="sxs-lookup"><span data-stu-id="26040-160">It isn't recommended that you change this value.</span></span> <span data-ttu-id="26040-161">Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="26040-161">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="26040-162">Pokud sada, instalační program používá proxy server při vytváření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="26040-162">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="26040-163">(Platí jenom pro Windows)</span><span class="sxs-lookup"><span data-stu-id="26040-163">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="26040-164">Zobrazit diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="26040-164">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="26040-165">Vytiskne nápovědy pro skript.</span><span class="sxs-lookup"><span data-stu-id="26040-165">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="26040-166">Příklady</span><span class="sxs-lookup"><span data-stu-id="26040-166">Examples</span></span>

<span data-ttu-id="26040-167">Nainstalujte nejnovější dlouhodobé podporovanou verzi (LTS) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="26040-167">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="26040-168">Windows:</span><span class="sxs-lookup"><span data-stu-id="26040-168">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="26040-169">macOS nebo Linux:</span><span class="sxs-lookup"><span data-stu-id="26040-169">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="26040-170">Nainstalujte nejnovější verzi z 2.0 kanál do zadaného umístění:</span><span class="sxs-lookup"><span data-stu-id="26040-170">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="26040-171">Windows:</span><span class="sxs-lookup"><span data-stu-id="26040-171">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="26040-172">macOS nebo Linux:</span><span class="sxs-lookup"><span data-stu-id="26040-172">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="26040-173">Nainstalujte 1.1.0 verzi sdílený modul runtime:</span><span class="sxs-lookup"><span data-stu-id="26040-173">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="26040-174">Windows:</span><span class="sxs-lookup"><span data-stu-id="26040-174">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="26040-175">macOS nebo Linux:</span><span class="sxs-lookup"><span data-stu-id="26040-175">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="26040-176">Získat skript a nainstalovat rozhraní příkazového řádku .NET Core one-liner příklady:</span><span class="sxs-lookup"><span data-stu-id="26040-176">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="26040-177">Windows:</span><span class="sxs-lookup"><span data-stu-id="26040-177">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="26040-178">macOS nebo Linux:</span><span class="sxs-lookup"><span data-stu-id="26040-178">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="26040-179">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26040-179">See also</span></span>

* [<span data-ttu-id="26040-180">Verze .NET core</span><span class="sxs-lookup"><span data-stu-id="26040-180">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
* [<span data-ttu-id="26040-181">.NET core Runtime a sadu SDK stáhněte archiv</span><span class="sxs-lookup"><span data-stu-id="26040-181">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
