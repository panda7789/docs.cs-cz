---
title: Průběžná integrace (CI) s .NET Core SDK a nástroji
description: Zjistěte, jak používat sadku .NET Core SDK a její nástroje na serveru sestavení s průběžnou integrací.
ms.date: 05/18/2017
ms.openlocfilehash: 6e23a21dd36422a095e56519c9aa28ce2549f7b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451035"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Použití sady .NET Core SDK a nástrojů v průběžné integraci (CI)

Tento dokument popisuje použití sady .NET Core SDK a jejích nástrojů na serveru sestavení. Sada nástrojů .NET Core funguje interaktivně, kde vývojář zadá příkazy na příkazovém řádku a automaticky, kde server průběžné integrace (CI) spustí skript sestavení. Příkazy, možnosti, vstupy a výstupy jsou stejné a jediné, co zadáte, jsou způsob, jak získat nástroje a systém pro sestavení aplikace. Tento dokument se zaměřuje na scénáře nástroje pořízení pro CI s doporučeními, jak navrhnout a strukturovat skripty sestavení.

## <a name="installation-options-for-ci-build-servers"></a>Možnosti instalace pro servery sestavení CI

### <a name="using-the-native-installers"></a>Použití nativních instalačních techniků

Nativní instalační programy jsou k dispozici pro macOS, Linux a Windows. Instalátory vyžadují přístup správce (sudo) k serveru sestavení. Výhodou použití nativního instalačního programu je, že nainstaluje všechny nativní závislosti potřebné ke spuštění nástrojů. Nativní instalační programy také poskytují celosystémovou instalaci sady SDK.

Uživatelé macOS by měli používat instalační programy PKG. Na Linuxu je na výběr použití správce balíčků založených na zdroji, jako je apt-get pro Ubuntu nebo yum pro CentOS, nebo pomocí samotných balíčků, DEB nebo RPM. V systému Windows použijte instalační program MSI.

Nejnovější stabilní binární soubory se nacházejí v [souborech ke stažení .NET](https://dotnet.microsoft.com/download). Pokud chcete použít nejnovější (a potenciálně nestabilní) předběžné nástroje, použijte odkazy uvedené v [úložišti GitHub dotnet/core-sdk](https://github.com/dotnet/core-sdk#installers-and-binaries). Pro linuxové `tar.gz` distribuce jsou k `tarballs`dispozici archivy (známé také jako); K instalaci rozhraní .NET Core použijte instalační skripty v archivu.

### <a name="using-the-installer-script"></a>Použití instalačního skriptu

Použití instalačního skriptu umožňuje instalaci bez oprávnění správce na serveru sestavení a snadnou automatizaci pro získání nástrojů. Skript se postará o stažení nástrojů a jeho extrahování do výchozího nebo určeného umístění pro použití. Můžete také určit verzi nástroje, kterou chcete nainstalovat, a zda chcete nainstalovat celou sadu SDK nebo pouze sdílený běh ový čas.

Instalační skript je automatizován pro spuštění na začátku sestavení pro načtení a instalaci požadované verze sady SDK. *Požadovaná verze* je bez ohledu na verzi sady SDK vaše projekty vyžadují k sestavení. Skript umožňuje nainstalovat sadu SDK v místním adresáři na serveru, spustit nástroje z nainstalovaného umístění a poté vyčistit (nebo nechat službu CI vyčistit) po sestavení. To poskytuje zapouzdření a izolace na celý proces sestavení. Odkaz na instalační skript se nachází v článku [dotnet-install.](dotnet-install-script.md)

> [!NOTE]
> **Azure DevOps Services**
>
> Při použití instalačního skriptu se nativní závislosti neinstalují automaticky. Nativní závislosti je nutné nainstalovat, pokud je operační systém nemá. Další informace naleznete v tématu [.NET Core závislosti a požadavky](../install/dependencies.md).

## <a name="ci-setup-examples"></a>Příklady nastavení CI

Tato část popisuje ruční nastavení pomocí skriptu PowerShell nebo bash spolu s popisem několika řešení CI softwaru jako služby (SaaS). Řešení SaaS CI, na které se [vztahuje,](https://travis-ci.org/)jsou Travis CI , [AppVeyor](https://www.appveyor.com/)a [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

### <a name="manual-setup"></a>Ruční nastavení

Každá služba SaaS má své vlastní metody pro vytváření a konfiguraci procesu sestavení. Pokud používáte jiné řešení SaaS než uvedené nebo vyžadují přizpůsobení nad rámec předběžné podpory, je nutné provést alespoň některé ruční konfigurace.

Obecně platí ruční nastavení vyžaduje, abyste získali verzi nástrojů (nebo nejnovější noční sestavení nástrojů) a spusťte skript sestavení. Skript PowerShellu nebo bash můžete použít k orchestraci příkazů jádra .NET nebo použít soubor projektu, který nastiňuje proces sestavení. [Část orchestrace](#orchestrating-the-build) obsahuje další podrobnosti o těchto možnostech.

Po vytvoření skriptu, který provádí ruční nastavení serveru sestavení CI, použijte jej na počítači pro účely dev k sestavení kódu místně pro účely testování. Jakmile potvrdíte, že skript běží dobře místně, nasaďte jej na server sestavení CI. Relativně jednoduchý skript prostředí PowerShell ukazuje, jak získat sadku .NET Core SDK a nainstalovat ji na server sestavení systému Windows:

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

Můžete zadat implementaci pro proces sestavení na konci skriptu. Skript získá nástroje a potom spustí proces sestavení. U počítačů se systémem UNIX provádí následující skript bash akce popsané ve skriptu prostředí PowerShell podobným způsobem:

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

Můžete nakonfigurovat [Travis CI](https://travis-ci.org/) nainstalovat .NET Core `csharp` SDK `dotnet` pomocí jazyka a klíče. Další informace naleznete v oficiálních dokumentech Travis CI na [stavební C #, F# nebo Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/). Všimněte si, že při přístupu `language: csharp` k informacím Travis CI, že identifikátor jazyka spravované komunitou funguje pro všechny jazyky .NET, včetně F#, a Mono.

Travis CI spouští úlohy macOS i Linux v *matici sestavení*, kde zadáte kombinaci runtime, prostředí a vyloučení/inkluzí, které pokryjí kombinace sestavení pro vaši aplikaci. Další informace naleznete v [tématu Přizpůsobení sestavení](https://docs.travis-ci.com/user/customizing-the-build) článku v dokumentaci Travis CI. Nástroje založené na MSBuild zahrnují běhové časy LTS (1.0.x) a Current (1.1.x) v balíčku; takže instalací sady SDK obdržíte vše, co potřebujete k sestavení.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) nainstaluje .NET Core 1.0.1 SDK s bitovou kopii pracovního procesu `Visual Studio 2017` sestavení. Další image sestavení s různými verzemi sady .NET Core SDK jsou k dispozici. Další informace naleznete [v příkladu appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) a v článku [Sestavení pracovních bitových kopií](https://www.appveyor.com/docs/build-environment/#build-worker-images) v dokumentech AppVeyor.

Binární soubory sady .NET Core SDK se stahují a rozbalují v podadresáři `PATH` pomocí instalačního skriptu a pak jsou přidány do proměnné prostředí. Přidejte matici sestavení pro spuštění integračních testů s více verzemi sady .NET Core SDK:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a>Azure DevOps Services

Nakonfigurujte služby Azure DevOps services pro vytváření projektů .NET Core pomocí jednoho z těchto přístupů:

1. Spusťte skript z [kroku ručního nastavení](#manual-setup) pomocí příkazů.
1. Vytvořte sestavení složené z několika předdefinovaných úloh sestavení služby Azure DevOps Services, které jsou nakonfigurované pro použití nástrojů .NET Core.

Obě řešení jsou platná. Pomocí skriptu ručního nastavení řídíte verzi nástrojů, které obdržíte, protože je stáhnete jako součást sestavení. Sestavení je spuštěno ze skriptu, který je nutné vytvořit. Tento článek se vztahuje pouze na ruční možnost. Další informace o vytváření sestavení pomocí úloh sestavení služby Azure DevOps Services najdete v dokumentaci [k Azure Pipelines.](https://docs.microsoft.com/azure/devops/pipelines/index)

Chcete-li použít skript ručního nastavení ve službě Azure DevOps Services, vytvořte novou definici sestavení a zadejte skript, který se má spustit pro krok sestavení. Toho se provádí pomocí uživatelského rozhraní služby Azure DevOps Services:

1. Začněte vytvořením nové definice sestavení. Jakmile se dostanete na obrazovku, která vám poskytuje možnost definovat, jaký druh sestavení chcete vytvořit, vyberte možnost **Prázdné.**

   ![Výběr prázdné definice sestavení](./media/using-ci-with-cli/select-empty-build-definition.png)

1. Po konfiguraci úložiště k sestavení, budete přesměrováni na definice sestavení. Vyberte **Přidat krok sestavení**:

   ![Přidání kroku sestavení](./media/using-ci-with-cli/add-build-step.png)

1. Zobrazí se katalog **úkolů**. Katalog obsahuje úkoly, které používáte v sestavení. Vzhledem k tomu, že máte skript, vyberte tlačítko **Přidat** pro **PowerShell: Spuštění skriptu PowerShellu**.

   ![Přidání kroku skriptu prostředí PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. Nakonfigurujte krok sestavení. Přidejte skript z úložiště, které vytváříte:

   ![Určení skriptu Prostředí PowerShell, který se má spustit](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a>Orchestrace sestavení

Většina tohoto dokumentu popisuje, jak získat nástroje .NET Core a konfigurovat různé služby CI bez poskytnutí informací o tom, jak organizovat nebo *skutečně sestavit*, váš kód s .NET Core. Možnosti, jak strukturovat proces sestavení, závisí na mnoha faktorech, které zde nelze obecně pokrýt. Další informace o orchestraci sestavení s každou technologií, prozkoumejte prostředky a ukázky uvedené v dokumentaci sady [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)a [Azure pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

Dva obecné přístupy, které budete mít při strukturování procesu sestavení pro kód .NET Core pomocí nástrojů .NET Core používají msbuild přímo nebo pomocí příkazů příkazového řádku .NET Core. Jaký přístup byste měli vzít, je určen vaší úrovně pohodlí s přístupy a kompromisy ve složitosti. MSBuild poskytuje možnost vyjádřit proces sestavení jako úkoly a cíle, ale přichází s přidanou složitost učení MSBuild syntaxe souboru projektu. Použití nástrojů příkazového řádku .NET Core je možná jednodušší, ale vyžaduje, abyste `bash` zapisovali logiku orchestrace ve skriptovacím jazyce, jako je powershell nebo PowerShell.

## <a name="see-also"></a>Viz také

- [.NET ke stažení - Linux](https://dotnet.microsoft.com/download?initial-os=linux)
