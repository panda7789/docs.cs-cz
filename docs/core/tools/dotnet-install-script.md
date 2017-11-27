---
title: "skriptů instalace DotNet."
description: "Další informace o skriptů dotnet instalace k instalaci nástroje příkazového řádku .NET Core a sdílený modul runtime."
keywords: DotNet. instalace, skripty dotnet. nainstalujte .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
ms.openlocfilehash: 2f15f37016fe824d76b501e4793e0b28bbdbe167
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="29411-104">referenční skriptů instalace DotNet.</span><span class="sxs-lookup"><span data-stu-id="29411-104">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="29411-105">Název</span><span class="sxs-lookup"><span data-stu-id="29411-105">Name</span></span>

<span data-ttu-id="29411-106">`dotnet-install.ps1` | `dotnet-install.sh`-Skriptu použít k instalaci nástroje příkazového řádku .NET Core a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="29411-106">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="29411-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="29411-107">Synopsis</span></span>

<span data-ttu-id="29411-108">Windows:</span><span class="sxs-lookup"><span data-stu-id="29411-108">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="29411-109">systému macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="29411-109">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="29411-110">Popis</span><span class="sxs-lookup"><span data-stu-id="29411-110">Description</span></span>

<span data-ttu-id="29411-111">`dotnet-install` Skripty se používají k provedení instalace bez oprávnění správce systému .NET Core SDK, která zahrnuje nástroje příkazového řádku .NET Core a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="29411-111">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="29411-112">Doporučujeme použít stabilní verze, která je hostovaná na [hlavní webové stránky .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="29411-112">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="29411-113">Přímé cest k skripty jsou:</span><span class="sxs-lookup"><span data-stu-id="29411-113">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="29411-114">https://dot.NET/v1/DotNet-Install.SH (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="29411-114">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="29411-115">https://dot.NET/v1/DotNet-Install.ps1 (prostředí Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="29411-115">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="29411-116">Hlavní užitečnost tyto skripty se automatizace scénáře a instalace bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="29411-116">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="29411-117">Existují dva skripty: jeden je skript prostředí PowerShell, který funguje v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="29411-117">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="29411-118">Další skript je bash skript, který funguje na systému Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="29411-118">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="29411-119">Oba skripty mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="29411-119">Both scripts have the same behavior.</span></span> <span data-ttu-id="29411-120">Skript bash také přečte přepínače prostředí PowerShell, abyste je mohli používat přepínače prostředí PowerShell pomocí skriptu v systémech Linux/systému macOS.</span><span class="sxs-lookup"><span data-stu-id="29411-120">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span> 

<span data-ttu-id="29411-121">Skripty instalace stáhnout soubor ZIP nebo tarball z vyřazuje sestavení rozhraní příkazového řádku a přejděte k jeho instalaci ve výchozím umístění nebo do umístění určeného `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="29411-121">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="29411-122">Ve výchozím nastavení instalační skripty stažení sady SDK a nainstalujte ji.</span><span class="sxs-lookup"><span data-stu-id="29411-122">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="29411-123">Pokud chcete jen získat sdílený modul runtime, zadejte `--shared-runtime` argument.</span><span class="sxs-lookup"><span data-stu-id="29411-123">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="29411-124">Ve výchozím nastavení přidá skript umístění instalace $PATH pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="29411-124">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="29411-125">Toto výchozí chování potlačit zadáním `--no-path` argument.</span><span class="sxs-lookup"><span data-stu-id="29411-125">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="29411-126">Před spuštěním skriptu nainstalujte požadované [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="29411-126">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="29411-127">Můžete nainstalovat konkrétní verzi pomocí `--version` argument.</span><span class="sxs-lookup"><span data-stu-id="29411-127">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="29411-128">Verze musí být zadán jako část 3 verze (například 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="29411-128">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="29411-129">Pokud se vynechá, použije `latest` verze.</span><span class="sxs-lookup"><span data-stu-id="29411-129">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="29411-130">Možnosti</span><span class="sxs-lookup"><span data-stu-id="29411-130">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="29411-131">Určuje zdroj kanál pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="29411-131">Specifies the source channel for the installation.</span></span> <span data-ttu-id="29411-132">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="29411-132">The possible values are:</span></span>

- <span data-ttu-id="29411-133">`Current`-Aktuální verzi</span><span class="sxs-lookup"><span data-stu-id="29411-133">`Current` - Current release</span></span>
- <span data-ttu-id="29411-134">`LTS`-Dlouhodobé podporu kanál (aktuální podporovanou verzi)</span><span class="sxs-lookup"><span data-stu-id="29411-134">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="29411-135">Dvě části verze ve formátu X.Y představující konkrétní vydání (například `2.0` nebo `1.0`)</span><span class="sxs-lookup"><span data-stu-id="29411-135">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="29411-136">Název větve [například `release/2.0.0`, `release/2.0.0-preview2`, nebo `master` nejnovější z `master` větve ("vykrvení edge" noční verzích)]</span><span class="sxs-lookup"><span data-stu-id="29411-136">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="29411-137">Výchozí hodnota je `LTS`.</span><span class="sxs-lookup"><span data-stu-id="29411-137">The default value is `LTS`.</span></span> <span data-ttu-id="29411-138">Další informace o kanály podpory rozhraní .NET najdete v tématu [životní cyklus podpory na .NET Core](https://www.microsoft.com/net/core/support) tématu.</span><span class="sxs-lookup"><span data-stu-id="29411-138">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="29411-139">Představuje verzi konkrétní sestavení.</span><span class="sxs-lookup"><span data-stu-id="29411-139">Represents a specific build version.</span></span> <span data-ttu-id="29411-140">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="29411-140">The possible values are:</span></span>

- <span data-ttu-id="29411-141">`latest`-Nejnovější sestavení na kanálu (používá se `-Channel` možnost)</span><span class="sxs-lookup"><span data-stu-id="29411-141">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="29411-142">`coherent`-Nejnovější souvislý sestavení na kanálu; používá kombinaci nejnovější stabilní balíčku (použít s názvu větve `-Channel` možnosti)</span><span class="sxs-lookup"><span data-stu-id="29411-142">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="29411-143">Verze třemi částmi ve formátu X.Y.Z představující konkrétní sestavení verze; nahrazuje `-Channel` možnost.</span><span class="sxs-lookup"><span data-stu-id="29411-143">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="29411-144">Například:`2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="29411-144">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="29411-145">Pokud tento parametr vynechán, `-Version` výchozí `latest`.</span><span class="sxs-lookup"><span data-stu-id="29411-145">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="29411-146">Určuje cestu instalace.</span><span class="sxs-lookup"><span data-stu-id="29411-146">Specifies the installation path.</span></span> <span data-ttu-id="29411-147">Daný adresář je vytvořen, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="29411-147">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="29411-148">Výchozí hodnota je *LocalAppData %\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="29411-148">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="29411-149">Všimněte si, že binární soubory jsou umístěny přímo v adresáři.</span><span class="sxs-lookup"><span data-stu-id="29411-149">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="29411-150">Architektura .NET Core binární soubory pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="29411-150">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="29411-151">Možné hodnoty jsou `auto`, `x64`, a `x86`.</span><span class="sxs-lookup"><span data-stu-id="29411-151">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="29411-152">Výchozí hodnota je `auto`, který reprezentuje probíhající architektury operačního systému.</span><span class="sxs-lookup"><span data-stu-id="29411-152">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="29411-153">Pokud nastavíte, tento přepínač omezuje na sdílený modul runtime instalace.</span><span class="sxs-lookup"><span data-stu-id="29411-153">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="29411-154">Celá sada SDK není nainstalována.</span><span class="sxs-lookup"><span data-stu-id="29411-154">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="29411-155">Pokud nastavíte, neprovede skript instalace; ale místo toho zobrazí jaké příkazového řádku pomocí konzistentně nainstalovat aktuálně požadovanou verzi rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="29411-155">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="29411-156">Například pokud zadejte verzi `latest`, se zobrazí odkaz s konkrétní verzi, aby tento příkaz lze použít nepodmíněně ve skriptu buildu.</span><span class="sxs-lookup"><span data-stu-id="29411-156">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="29411-157">Pokud chcete nainstalovat nebo stáhnout sami umístění na binární soubor, zobrazí se také.</span><span class="sxs-lookup"><span data-stu-id="29411-157">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="29411-158">Pokud nastavíte, předponu/installdir neexportují k cestě pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="29411-158">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="29411-159">Ve výchozím nastavení bude skript upravit cesta, která zpřístupňuje nástrojů příkazového řádku okamžitě po instalaci.</span><span class="sxs-lookup"><span data-stu-id="29411-159">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="29411-160">Určuje, že adresa URL pro Azure kanálu pro instalační program.</span><span class="sxs-lookup"><span data-stu-id="29411-160">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="29411-161">Není doporučeno tuto hodnotu změnit.</span><span class="sxs-lookup"><span data-stu-id="29411-161">It isn't recommended that you change this value.</span></span> <span data-ttu-id="29411-162">Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="29411-162">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="29411-163">Pokud sadu, instalační program používá proxy server při vytváření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="29411-163">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="29411-164">(Platné pouze pro Windows)</span><span class="sxs-lookup"><span data-stu-id="29411-164">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="29411-165">Zobrazit diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="29411-165">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="29411-166">Vytiskne nápovědy pro skript.</span><span class="sxs-lookup"><span data-stu-id="29411-166">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="29411-167">Příklady</span><span class="sxs-lookup"><span data-stu-id="29411-167">Examples</span></span>

<span data-ttu-id="29411-168">Nainstalujte nejnovější dlouhodobé podporovanou verzi (LTS) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="29411-168">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="29411-169">Windows:</span><span class="sxs-lookup"><span data-stu-id="29411-169">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="29411-170">systému macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="29411-170">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="29411-171">Nainstalujte nejnovější verzi z 2.0 kanálu do zadaného umístění:</span><span class="sxs-lookup"><span data-stu-id="29411-171">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="29411-172">Windows:</span><span class="sxs-lookup"><span data-stu-id="29411-172">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="29411-173">systému macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="29411-173">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="29411-174">Nainstalujte 1.1.0 verzi sdílený modul runtime:</span><span class="sxs-lookup"><span data-stu-id="29411-174">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="29411-175">Windows:</span><span class="sxs-lookup"><span data-stu-id="29411-175">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="29411-176">systému macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="29411-176">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="29411-177">Získat skript a nainstalovat .NET Core rozhraní příkazového řádku one-liner příklady:</span><span class="sxs-lookup"><span data-stu-id="29411-177">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="29411-178">Windows:</span><span class="sxs-lookup"><span data-stu-id="29411-178">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="29411-179">systému macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="29411-179">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="29411-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="29411-180">See also</span></span>

<span data-ttu-id="29411-181">[Verze .NET core](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="29411-181">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="29411-182">.NET core Runtime a sadu SDK stáhněte archivu</span><span class="sxs-lookup"><span data-stu-id="29411-182">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
