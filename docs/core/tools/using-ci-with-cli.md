---
title: Pomocí sady .NET Core SDK a nástroje v kontinuální integrace (CI)
description: Informace o použití sady .NET Core SDK a jeho nástroje na serveru sestavení.
author: guardrex
ms.date: 05/18/2017
ms.custom: seodec18
ms.openlocfilehash: c9fd9e359a22467cc8639109538522e4088df5ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647611"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Pomocí sady .NET Core SDK a nástroje v kontinuální integrace (CI)

Tento dokument popisuje, jak pomocí .NET Core SDK a jeho nástrojů na serveru sestavení. .NET Core nástrojů prací obou interaktivně, kde vývojář typů příkazy do příkazového řádku a automaticky, pokud server kontinuální integrace (CI) spustí skript sestavení. Příkazy, možnosti, vstupy a výstupy jsou stejné, a jedinou akcí, které zadáte představují způsob, jak získat nástroje a systém k sestavení aplikace. Tento dokument se zaměřuje na scénáře pořízení nástroj pro nepřetržitou Integraci s doporučeními o tom, jak navrhovat a strukturují vaše skripty sestavení.

## <a name="installation-options-for-ci-build-servers"></a>Možnosti instalace pro nepřetržitou Integraci sestavovacích serverů

### <a name="using-the-native-installers"></a>Použití nativních instalačních programů

Nativní instalační programy jsou dostupné pro macOS, Linux a Windows. Instalační programy vyžadují přístup správce (sudo) na serveru sestavení. Výhodou použití nativní instalačního programu se nainstaluje všechny komponenty nástroje nativní závislosti, které vyžaduje pro spuštění nástroje. Nativních instalačních programů poskytují také systémová instalace sady SDK.

macOS uživatelé by měli použít instalační programy balíčku. V systému Linux je pomocí Správce balíčků založená na informační kanál, třeba apt-get pro Ubuntu nebo yumu pro CentOS, nebo pomocí balíčků, sami, DEB nebo ot. / min. Ve Windows použijte instalační službu MSI.

Nejnovější stabilní binární soubory se nacházejí v [.NET stáhne](https://dotnet.microsoft.com/download). Pokud chcete používat nejnovější (a potenciálně nestabilní) předběžné verze nástroje, pomocí odkazů uvedených v [úložiště GitHub dotnet/core-sdk](https://github.com/dotnet/core-sdk#installers-and-binaries). Pro distribuce Linuxu `tar.gz` archivy (označované také jako `tarballs`) jsou k dispozici; nainstalujte .NET Core pomocí skriptů instalace v rámci archivu.

### <a name="using-the-installer-script"></a>Pomocí skriptů Instalační program

Pomocí skriptu instalačního programu umožňuje instalaci bez oprávnění správce na serveru sestavení a snadná automatizace pro získání nástrojů. Skript se postará o stažení nástrojů a extrahování do výchozí nebo zadané umístění pro použití. Můžete také určit verzi nástrojů, kterou chcete nainstalovat a určuje, zda chcete nainstalovat celou sadu SDK nebo pouze sdílený modul runtime.

Skript instalačního programu je automatické spouštění na začátku operace sestavení pro načtení a instalaci požadované verze sady SDK. *Požadovanou verzi* je libovolné verzi sady SDK vyžadovat vaše projekty k sestavení. Skript umožňuje nainstalovat sadu SDK do místního adresáře na serveru, spustit nástroje z umístění instalace a potom vyčištění (nebo umožní službě CI vyčistit) po sestavení. Poskytuje zapouzdření a izolace pro celý váš proces sestavení. Odkaz na instalační skript se nachází v [nainstalujte dotnet](dotnet-install-script.md) článku.

> [!NOTE]
> **Služby Azure DevOps**
>
> Pokud používáte skript instalačního programu, nativní závislosti nejsou nainstalovány automaticky. Pokud operační systém nemá, je nutné nainstalovat nativní závislosti. Další informace najdete v tématu [předpoklady pro .NET Core v Linuxu](../linux-prerequisites.md).

## <a name="ci-setup-examples"></a>Příklady nastavení položky konfigurace

Tato část popisuje ruční instalaci pomocí skriptu prostředí PowerShell nebo prostředí bash, popisy několik softwaru jako řešení CI služby (SaaS). Řešení SaaS CI popsaná jsou [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), a [kanály Azure](https://docs.microsoft.com/azure/devops/pipelines/index).

### <a name="manual-setup"></a>Ruční instalace

Každá služba SaaS má své vlastní metody vytvoření a konfigurace procesu sestavení. Pokud používáte jiné řešení SaaS, než je uveden nebo vyžadují přizpůsobení kromě předem zabalené podpory, je nutné provést nejméně část konfigurace ručně.

Obecně platí ruční instalaci je potřeba získat z verze nástroje (nebo noční sestavení nástrojů) a spusťte váš skript buildu. Můžete použít prostředí PowerShell nebo bash skript k orchestraci příkazy .NET Core nebo soubor projektu, který popisuje proces sestavení. [Orchestrace části](#orchestrating-the-build) poskytující víc podrobností o těchto možnostech.

Po vytvoření skriptu, který provádí ruční instalací serveru sestavení CI, používejte ji na vývojovém počítači k sestavení vašeho kódu místně pro účely testování. Jakmile se ujistíte, že je a místně spuštěný skript, nasaďte na server sestavení CI. Poměrně jednoduchý skript prostředí PowerShell ukazuje, jak získat sadu .NET Core SDK a nainstalujte ho na server sestavení Windows:

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it
#   does, it's removed. This is not strictly required, but it's a
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

Poskytuje implementaci pro proces sestavení na konci tohoto skriptu. Skript získá nástroje a poté spustí proces sestavení. Následující skript bash pro počítače platformy UNIX provede akce popsané v skriptu prostředí PowerShell podobným způsobem:

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a>Travis CI

Můžete nakonfigurovat [Travis CI](https://travis-ci.org/) nainstalovat s použitím sady .NET Core SDK `csharp` jazyka a `dotnet` klíč. Další informace najdete v oficiální dokumentace Travis CI na [budovy C#, F#, nebo projektu jazyka Visual Basic](https://docs.travis-ci.com/user/languages/csharp/). Všimněte si, jak přistupovat k informacím Travis CI, která udržuje komunity `language: csharp` identifikátor jazyka se dá použít pro všechny jazyky .NET, včetně F#a Mono.

Travis CI běží v systémech macOS a Linux úloh v *sestavení matice*, kde můžete určit kombinaci modulu runtime, prostředí a vyloučení nebo zahrnutí pokrýt kombinace vašeho sestavení pro vaši aplikaci. Další informace najdete v tématu [přizpůsobení sestavení](https://docs.travis-ci.com/user/customizing-the-build) článek v dokumentaci k Travis CI. Nástroje založené na MSBuild zahrnují LTS (1.0.x) a moduly runtime aktuální (1.1.x) v balíčku. takže nainstalováním sady SDK, zobrazí se všechno, co potřebujete k vytváření.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) nainstaluje .NET Core 1.0.1 SDK se `Visual Studio 2017` sestavení image pracovního procesu. Další sestavení Image s různými verzemi nástroje .NET Core SDK jsou k dispozici. Další informace najdete v tématu [appveyor.yml příklad](https://github.com/dotnet/docs/blob/master/appveyor.yml) a [sestavování imagí pro pracovníka](https://www.appveyor.com/docs/build-environment/#build-worker-images) článek v AppVeyor dokumentace.

Binární soubory sady SDK .NET Core stáhnou a odblokujte v podadresáři pomocí instalačního skriptu, a potom se přidají do `PATH` proměnné prostředí. Přidáte matici sestavení ke spuštění testů integrace s více verzemi nástroje .NET Core SDK:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a>Azure DevOps Services

Konfigurace služby Azure DevOps k sestavení projektů .NET Core pomocí jedné z těchto přístupů:

1. Spusťte skript ze [ruční instalaci krok](#manual-setup) pomocí příkazů.
1. Vytvořte sestavení se skládá z několik úloh služby Azure DevOps integrované sestavení, které jsou nakonfigurovány pro použití nástroje .NET Core.

Obě řešení jsou platné. Pomocí skriptu ruční instalace, řízení verze nástrojů, které jste dostali, protože si stáhnout jako součást sestavení. Sestavení je spuštěno ze skriptu, který je nutné vytvořit. Tento článek se týká pouze možnost ručně. Další informace o sestavování sestavení se službami Azure DevOps úlohy sestavení, najdete v článku [kanály Azure](https://docs.microsoft.com/azure/devops/pipelines/index) dokumentaci.

Použití skriptu ruční instalace služby Azure DevOps, vytvořte novou definici sestavení a určete skript, který chcete spustit kroku sestavení. To lze provést pomocí uživatelského rozhraní služby Azure DevOps:

1. Začněte vytvořením nové definice sestavení. Jakmile se obrazovka, která poskytuje možnost určit, jaký typ sestavení, kterou chcete vytvořit, vyberte **prázdný** možnost.

   ![Vyberte definici sestavení prázdný](./media/using-ci-with-cli/select-empty-build-definition.png)

1. Po dokončení konfigurace úložiště k sestavení, budete přesměrováni na definice sestavení. Vyberte **přidat krok sestavení**:

   ![Přidání kroku sestavení](./media/using-ci-with-cli/add-build-step.png)

1. Zobrazí se vám **katalogu úloh**. Katalog obsahuje úlohy, které můžete použít v sestavení. Protože máte skript, vyberte **přidat** tlačítko pro **prostředí PowerShell: Spustit skript prostředí PowerShell**.

   ![Přidání kroku skript prostředí PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. Nakonfigurujte krok sestavení. Přidáte z úložiště, kterou vytváříte skript:

   ![Určení spuštění skriptu prostředí PowerShell](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a>Orchestrace sestavení

Většina tento dokument popisuje, jak získat nástroje .NET Core a konfigurovat různé služby CI bez zadání informací o tom, jak orchestrovat, nebo *sestavují*, váš kód s .NET Core. Volby v tom, jak strukturovat proces sestavení závisí na mnoha faktorech, které nejde pokrýt obecné způsobem. Další informace o sestavení s každou technologii Orchestrace, prozkoumejte prostředky a ukázky, které jsou součástí sady dokumentace [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), a [Azure Kanály](https://docs.microsoft.com/azure/devops/pipelines/index).

Dvě obecné metody, které provedete v strukturování proces sestavení pro kód .NET Core pomocí nástroje .NET Core jsou přímo pomocí nástroje MSBuild nebo pomocí příkazů příkazového řádku .NET Core. Jaký přístup je potřeba se určuje podle vaší úrovně pohodlí přístupy a kompromisy složitost. Nástroj MSBuild poskytuje schopnost procesu sestavení je možné vyjádřit jako úlohy a cíle, ale obsahuje přidaná složitost studijních syntaxe souboru projektu MSBuild. Pomocí nástroje příkazového řádku .NET Core je možná jednodušší, ale vyžaduje, abyste psát logiku Orchestrace ve skriptovacím jazyce jako `bash` nebo prostředí PowerShell.

## <a name="see-also"></a>Viz také:

- [Stažení rozhraní .NET – Linux](https://dotnet.microsoft.com/download?initial-os=linux)
