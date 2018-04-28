---
title: skriptů instalace DotNet.
description: Další informace o skriptů dotnet instalace k instalaci nástroje příkazového řádku .NET Core a sdílený modul runtime.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 96336df087ea2ad01584010f0715ad31e079b663
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="5889a-103">referenční skriptů instalace DotNet.</span><span class="sxs-lookup"><span data-stu-id="5889a-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="5889a-104">Název</span><span class="sxs-lookup"><span data-stu-id="5889a-104">Name</span></span>

<span data-ttu-id="5889a-105">`dotnet-install.ps1` | `dotnet-install.sh` -Skriptu použít k instalaci nástroje příkazového řádku .NET Core a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="5889a-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5889a-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="5889a-106">Synopsis</span></span>

<span data-ttu-id="5889a-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="5889a-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="5889a-108">systému macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5889a-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="5889a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5889a-109">Description</span></span>

<span data-ttu-id="5889a-110">`dotnet-install` Skripty se používají k provedení instalace bez oprávnění správce systému .NET Core SDK, která zahrnuje nástroje příkazového řádku .NET Core a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="5889a-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="5889a-111">Doporučujeme použít stabilní verze, která je hostovaná na [hlavní webové stránky .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="5889a-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="5889a-112">Přímé cest k skripty jsou:</span><span class="sxs-lookup"><span data-stu-id="5889a-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="5889a-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="5889a-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="5889a-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="5889a-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="5889a-115">Hlavní užitečnost tyto skripty se automatizace scénáře a instalace bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="5889a-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="5889a-116">Existují dva skripty: jeden je skript prostředí PowerShell, který funguje v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5889a-116">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="5889a-117">Další skript je bash skript, který funguje na systému Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="5889a-117">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="5889a-118">Oba skripty mají stejné chování.</span><span class="sxs-lookup"><span data-stu-id="5889a-118">Both scripts have the same behavior.</span></span> <span data-ttu-id="5889a-119">Skript bash také přečte přepínače prostředí PowerShell, abyste je mohli používat přepínače prostředí PowerShell pomocí skriptu v systémech Linux/systému macOS.</span><span class="sxs-lookup"><span data-stu-id="5889a-119">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span> 

<span data-ttu-id="5889a-120">Skripty instalace stáhnout soubor ZIP nebo tarball z vyřazuje sestavení rozhraní příkazového řádku a přejděte k jeho instalaci ve výchozím umístění nebo do umístění určeného `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="5889a-120">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="5889a-121">Ve výchozím nastavení instalační skripty stažení sady SDK a nainstalujte ji.</span><span class="sxs-lookup"><span data-stu-id="5889a-121">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="5889a-122">Pokud chcete jen získat sdílený modul runtime, zadejte `--shared-runtime` argument.</span><span class="sxs-lookup"><span data-stu-id="5889a-122">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="5889a-123">Ve výchozím nastavení přidá skript umístění instalace $PATH pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="5889a-123">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="5889a-124">Toto výchozí chování potlačit zadáním `--no-path` argument.</span><span class="sxs-lookup"><span data-stu-id="5889a-124">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="5889a-125">Před spuštěním skriptu nainstalujte požadované [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="5889a-125">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="5889a-126">Můžete nainstalovat konkrétní verzi pomocí `--version` argument.</span><span class="sxs-lookup"><span data-stu-id="5889a-126">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="5889a-127">Verze musí být zadán jako část 3 verze (například 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="5889a-127">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="5889a-128">Pokud se vynechá, použije `latest` verze.</span><span class="sxs-lookup"><span data-stu-id="5889a-128">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="5889a-129">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5889a-129">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="5889a-130">Určuje zdroj kanál pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="5889a-130">Specifies the source channel for the installation.</span></span> <span data-ttu-id="5889a-131">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5889a-131">The possible values are:</span></span>

- <span data-ttu-id="5889a-132">`Current` -Aktuální verzi</span><span class="sxs-lookup"><span data-stu-id="5889a-132">`Current` - Current release</span></span>
- <span data-ttu-id="5889a-133">`LTS` -Dlouhodobé podporu kanál (aktuální podporovanou verzi)</span><span class="sxs-lookup"><span data-stu-id="5889a-133">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="5889a-134">Dvě části verze ve formátu X.Y představující konkrétní vydání (například `2.0` nebo `1.0`)</span><span class="sxs-lookup"><span data-stu-id="5889a-134">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="5889a-135">Název větve [například `release/2.0.0`, `release/2.0.0-preview2`, nebo `master` nejnovější z `master` větve ("vykrvení edge" noční verzích)]</span><span class="sxs-lookup"><span data-stu-id="5889a-135">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="5889a-136">Výchozí hodnota je `LTS`.</span><span class="sxs-lookup"><span data-stu-id="5889a-136">The default value is `LTS`.</span></span> <span data-ttu-id="5889a-137">Další informace o kanály podpory rozhraní .NET najdete v tématu [životní cyklus podpory na .NET Core](https://www.microsoft.com/net/core/support) tématu.</span><span class="sxs-lookup"><span data-stu-id="5889a-137">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="5889a-138">Představuje verzi konkrétní sestavení.</span><span class="sxs-lookup"><span data-stu-id="5889a-138">Represents a specific build version.</span></span> <span data-ttu-id="5889a-139">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5889a-139">The possible values are:</span></span>

- <span data-ttu-id="5889a-140">`latest` -Nejnovější sestavení na kanálu (používá se `-Channel` možnost)</span><span class="sxs-lookup"><span data-stu-id="5889a-140">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="5889a-141">`coherent` -Nejnovější souvislý sestavení na kanálu; používá kombinaci nejnovější stabilní balíčku (použít s názvu větve `-Channel` možnosti)</span><span class="sxs-lookup"><span data-stu-id="5889a-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="5889a-142">Verze třemi částmi ve formátu X.Y.Z představující konkrétní sestavení verze; nahrazuje `-Channel` možnost.</span><span class="sxs-lookup"><span data-stu-id="5889a-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="5889a-143">Například: `2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="5889a-143">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="5889a-144">Pokud tento parametr vynechán, `-Version` výchozí `latest`.</span><span class="sxs-lookup"><span data-stu-id="5889a-144">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="5889a-145">Určuje cestu instalace.</span><span class="sxs-lookup"><span data-stu-id="5889a-145">Specifies the installation path.</span></span> <span data-ttu-id="5889a-146">Daný adresář je vytvořen, pokud neexistuje.</span><span class="sxs-lookup"><span data-stu-id="5889a-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="5889a-147">Výchozí hodnota je *LocalAppData %\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="5889a-147">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="5889a-148">Všimněte si, že binární soubory jsou umístěny přímo v adresáři.</span><span class="sxs-lookup"><span data-stu-id="5889a-148">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="5889a-149">Architektura .NET Core binární soubory pro instalaci.</span><span class="sxs-lookup"><span data-stu-id="5889a-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="5889a-150">Možné hodnoty jsou `auto`, `x64`, a `x86`.</span><span class="sxs-lookup"><span data-stu-id="5889a-150">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="5889a-151">Výchozí hodnota je `auto`, který reprezentuje probíhající architektury operačního systému.</span><span class="sxs-lookup"><span data-stu-id="5889a-151">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="5889a-152">Pokud nastavíte, tento přepínač omezuje na sdílený modul runtime instalace.</span><span class="sxs-lookup"><span data-stu-id="5889a-152">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="5889a-153">Celá sada SDK není nainstalována.</span><span class="sxs-lookup"><span data-stu-id="5889a-153">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="5889a-154">Pokud nastavíte, neprovede skript instalace; ale místo toho zobrazí jaké příkazového řádku pomocí konzistentně nainstalovat aktuálně požadovanou verzi rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5889a-154">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="5889a-155">Například pokud zadejte verzi `latest`, se zobrazí odkaz s konkrétní verzi, aby tento příkaz lze použít nepodmíněně ve skriptu buildu.</span><span class="sxs-lookup"><span data-stu-id="5889a-155">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="5889a-156">Pokud chcete nainstalovat nebo stáhnout sami umístění na binární soubor, zobrazí se také.</span><span class="sxs-lookup"><span data-stu-id="5889a-156">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="5889a-157">Pokud nastavíte, předponu/installdir neexportují k cestě pro aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="5889a-157">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="5889a-158">Ve výchozím nastavení bude skript upravit cesta, která zpřístupňuje nástrojů příkazového řádku okamžitě po instalaci.</span><span class="sxs-lookup"><span data-stu-id="5889a-158">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="5889a-159">Určuje, že adresa URL pro Azure kanálu pro instalační program.</span><span class="sxs-lookup"><span data-stu-id="5889a-159">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="5889a-160">Není doporučeno tuto hodnotu změnit.</span><span class="sxs-lookup"><span data-stu-id="5889a-160">It isn't recommended that you change this value.</span></span> <span data-ttu-id="5889a-161">Výchozí hodnota je `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="5889a-161">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="5889a-162">Pokud sadu, instalační program používá proxy server při vytváření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="5889a-162">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="5889a-163">(Platné pouze pro Windows)</span><span class="sxs-lookup"><span data-stu-id="5889a-163">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="5889a-164">Zobrazit diagnostické informace.</span><span class="sxs-lookup"><span data-stu-id="5889a-164">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="5889a-165">Vytiskne nápovědy pro skript.</span><span class="sxs-lookup"><span data-stu-id="5889a-165">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="5889a-166">Příklady</span><span class="sxs-lookup"><span data-stu-id="5889a-166">Examples</span></span>

<span data-ttu-id="5889a-167">Nainstalujte nejnovější dlouhodobé podporovanou verzi (LTS) do výchozího umístění:</span><span class="sxs-lookup"><span data-stu-id="5889a-167">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="5889a-168">Windows:</span><span class="sxs-lookup"><span data-stu-id="5889a-168">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="5889a-169">systému macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5889a-169">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="5889a-170">Nainstalujte nejnovější verzi z 2.0 kanálu do zadaného umístění:</span><span class="sxs-lookup"><span data-stu-id="5889a-170">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="5889a-171">Windows:</span><span class="sxs-lookup"><span data-stu-id="5889a-171">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="5889a-172">systému macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5889a-172">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="5889a-173">Nainstalujte 1.1.0 verzi sdílený modul runtime:</span><span class="sxs-lookup"><span data-stu-id="5889a-173">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="5889a-174">Windows:</span><span class="sxs-lookup"><span data-stu-id="5889a-174">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="5889a-175">systému macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5889a-175">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="5889a-176">Získat skript a nainstalovat .NET Core rozhraní příkazového řádku one-liner příklady:</span><span class="sxs-lookup"><span data-stu-id="5889a-176">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="5889a-177">Windows:</span><span class="sxs-lookup"><span data-stu-id="5889a-177">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="5889a-178">systému macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="5889a-178">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="5889a-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="5889a-179">See also</span></span>

<span data-ttu-id="5889a-180">[Verze .NET core](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="5889a-180">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="5889a-181">.NET core Runtime a sadu SDK stáhněte archivu</span><span class="sxs-lookup"><span data-stu-id="5889a-181">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
