---
title: Průběžná integrace (CI) s .NET Core SDK a nástroji
description: Naučte se používat .NET Core SDK a jeho nástroje na serveru sestavení s nepřetržitou integrací.
ms.date: 05/18/2017
ms.openlocfilehash: ddccb477bc112157a155e2217e04c329e7ab51c5
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2020
ms.locfileid: "86415995"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Používání .NET Core SDK a nástrojů v kontinuální integraci (CI)

Tento dokument popisuje použití .NET Core SDK a jeho nástrojů na serveru sestavení. Sada nástrojů .NET Core funguje interaktivně, pokud vývojář zadá příkazy na příkazovém řádku a automaticky, kde server průběžné integrace (CI) spouští skript sestavení. Příkazy, možnosti, vstupy a výstupy jsou stejné a jediné, co zadáte, je způsob, jak získat nástroje a systém pro sestavení vaší aplikace. Tento dokument se zaměřuje na scénáře získání nástrojů pro CI s doporučeními, jak navrhovat a strukturovat skripty sestavení.

## <a name="installation-options-for-ci-build-servers"></a>Možnosti instalace pro servery sestavení CI

### <a name="using-the-native-installers"></a>Použití nativních instalačních programů

Nativní instalační programy jsou k dispozici pro macOS, Linux a Windows. Instalační programy vyžadují přístup správce (sudo) k serveru sestavení. Výhodou použití nativního instalačního programu je instalace všech nativních závislostí potřebných ke spuštění nástrojů. Nativní instalační programy také poskytují instalaci sady SDK pro všechny systémy.

macOS uživatelé by měli používat instalační programy PKG. V systému Linux existuje možnost použití Správce balíčků na základě informačního kanálu, jako je apt-get pro Ubuntu nebo Yumu pro CentOS, nebo použití samotných balíčků, DEB nebo ot./min.. Ve Windows použijte instalační program MSI.

Nejnovější stabilní binární soubory najdete v části [soubory ke stažení pro .NET](https://dotnet.microsoft.com/download). Pokud chcete použít nejnovější (a potenciálně nestabilní) předběžné verze nástrojů, použijte odkazy, které jsou k dispozici v [úložišti GitHub/Core-SDK](https://github.com/dotnet/core-sdk#installers-and-binaries). V případě distribucí systému Linux `tar.gz` jsou k dispozici archivy (známé také jako `tarballs` ); pomocí instalačních skriptů v archivech nainstalujte rozhraní .NET Core.

### <a name="using-the-installer-script"></a>Použití skriptu instalačního programu

Použití skriptu instalačního programu umožňuje instalaci bez oprávnění správce na serveru sestavení a snadné automatizace pro získání nástrojů. Skript se postará o stažení nástrojů a jejich extrakci do výchozího nebo zadaného umístění, které se má použít. Můžete také zadat verzi nástrojů, které chcete nainstalovat, a zda chcete nainstalovat celou sadu SDK nebo pouze sdílený modul runtime.

Skript instalačního programu je automatizovaný pro spuštění na začátku sestavení za účelem načtení a instalaci požadované verze sady SDK. *Požadovaná verze* je libovolná verze sady SDK, kterou vaše projekty vyžadují pro sestavení. Skript vám umožní nainstalovat sadu SDK do místního adresáře na serveru, spustit nástroje z nainstalovaného umístění a potom vyčistit (nebo nechat službu CI vyčistit) po sestavení. To zajišťuje zapouzdření a izolaci pro celý proces sestavení. Odkaz na instalační skript najdete v článku [dotnet-Install](dotnet-install-script.md) .

> [!NOTE]
> **Azure DevOps Services**
>
> Při použití skriptu instalačního programu nejsou nativní závislosti automaticky nainstalovány. Nativní závislosti je nutné nainstalovat, pokud je operační systém neobsahuje. Další informace najdete v tématu [závislosti a požadavky .NET Core](../install/windows.md#dependencies).

## <a name="ci-setup-examples"></a>Příklady nastavení CI

Tato část popisuje ruční instalaci pomocí skriptu PowerShellu nebo bash spolu s popisem několika řešení CI pro software jako služba (SaaS). Zahrnutá řešení SaaS CI jsou [TRAVIS CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)a [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

### <a name="manual-setup"></a>Ruční instalace

Každá služba SaaS má své vlastní metody pro vytváření a konfiguraci procesu sestavení. Pokud používáte jiné řešení SaaS, než je uvedené v seznamu nebo vyžadovat přizpůsobení nad rámec předběžného použití, musíte provést alespoň nějakou ruční konfiguraci.

Obecně platí, že ruční instalace vyžaduje, abyste získali verzi nástrojů (nebo nejnovější noční sestavení nástrojů) a spustili skript sestavení. Pomocí skriptu PowerShell nebo bash můžete orchestrovat příkazy .NET Core nebo použít soubor projektu, který popisuje proces sestavení. Další informace o těchto možnostech najdete v [části orchestrace](#orchestrating-the-build) .

Po vytvoření skriptu, který provede ruční instalaci serveru sestavení CI, ho použijte ve vývojovém počítači k místnímu sestavení kódu pro účely testování. Jakmile ověříte, že se skript spouští dobře místně, nasaďte ho do svého serveru sestavení CI. Poměrně jednoduchý skript PowerShellu ukazuje, jak získat .NET Core SDK a jak ho nainstalovat na server sestavení Windows.

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

Implementaci pro proces sestavení zadáte na konci skriptu. Skript získá nástroje a pak provede proces sestavení. Pro počítače se systémem UNIX provede následující skript bash akce popsané ve skriptu prostředí PowerShell podobným způsobem:

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

[TRAVIS CI](https://travis-ci.org/) můžete nakonfigurovat pro instalaci .NET Core SDK pomocí `csharp` jazyka a `dotnet` klíče. Další informace najdete v oficiální dokumentaci k Travis CI o [vytváření projektů v jazyce C#, F # nebo Visual Basic](https://docs.travis-ci.com/user/languages/csharp/). Mějte na paměti, že při přístupu k informacím o Travis CI, které udržuje komunitní `language: csharp` identifikátor jazyka, funguje pro všechny jazyky .NET, včetně F # a mono.

Travis CI spouští úlohy macOS a Linux v *matrici sestavení*, kde zadáváte kombinaci modulu runtime, prostředí a vyloučení a zahrnutí, která budou zahrnovat vaše kombinace sestavení pro vaši aplikaci. Další informace naleznete v článku [přizpůsobení sestavení](https://docs.travis-ci.com/user/customizing-the-build) v dokumentaci k Travis CI. Nástroje založené na MSBuildu zahrnují do balíčku modul runtime LTS (1.0. x) a aktuální (1.1. x). instalace sady SDK proto obdržíte všechno, co potřebujete k sestavení.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) nainstaluje sadu SDK .NET Core 1.0.1 pomocí `Visual Studio 2017` Image pracovního procesu sestavení. K dispozici jsou další image sestavení s různými verzemi .NET Core SDK. Další informace najdete v článku [příklad AppVeyor. yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) a [Build Worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) v dokumentaci AppVeyor.

.NET Core SDK binární soubory byly staženy a extrahovány v podadresáři pomocí instalačního skriptu a poté přidány do `PATH` proměnné prostředí. Přidejte matrici sestavení pro spuštění testů integrace s více verzemi .NET Core SDK:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a>Azure DevOps Services

Nakonfigurujte Azure DevOps Services pro sestavení projektů .NET Core pomocí jednoho z těchto přístupů:

1. Spusťte skript z [kroku ruční instalace](#manual-setup) pomocí příkazů.
1. Vytvořte sestavení složené z několika Azure DevOps Services integrovaných úloh sestavení, které jsou nakonfigurovány pro použití nástrojů .NET Core.

Obě řešení jsou platná. Pomocí skriptu ručního nastavení můžete řídit verzi nástrojů, které obdržíte, protože je stáhnete jako součást sestavení. Sestavení je spuštěno ze skriptu, který je třeba vytvořit. Tento článek se týká pouze ručních možností. Další informace o vytváření sestavení pomocí Azure DevOps Services úloh sestavení naleznete v dokumentaci k [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) .

Chcete-li použít skript ručního nastavení v Azure DevOps Services, vytvořte novou definici sestavení a zadejte skript, který bude spuštěn pro krok sestavení. K tomu je možné použít Azure DevOps Services uživatelské rozhraní:

1. Začněte vytvořením nové definice sestavení. Až se dostanete na obrazovku, která vám poskytne možnost definovat typ sestavení, který chcete vytvořit, vyberte **prázdnou** možnost.

   ![Výběr prázdné definice sestavení](./media/using-ci-with-cli/select-empty-build-definition.png)

1. Po nakonfigurování úložiště, které se má sestavit, budete přesměrováni na definice sestavení. Vyberte **Přidat krok sestavení**:

   ![Přidání kroku sestavení](./media/using-ci-with-cli/add-build-step.png)

1. Zobrazuje se v **katalogu úloh**. Katalog obsahuje úlohy, které v sestavení používáte. Vzhledem k tomu, že máte skript, vyberte tlačítko **Přidat** pro **PowerShell: Spusťte powershellový skript**.

   ![Přidání kroku skriptu PowerShellu](./media/using-ci-with-cli/add-powershell-script.png)

1. Nakonfigurujte krok sestavení. Přidejte skript z úložiště, které vytváříte:

   ![Určení skriptu prostředí PowerShell, který se má spustit](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a>Orchestrace sestavení

Většina tohoto dokumentu popisuje, jak získat nástroje .NET Core a nakonfigurovat různé služby CI bez poskytování informací o tom, jak orchestrovat, nebo *ve skutečnosti sestavit*kód pomocí .NET Core. Volby, jak strukturovat proces sestavení, závisí na mnoha faktorech, které se tady nedají zakrýt obecným způsobem. Další informace o orchestraci vašich sestavení s každou technologií najdete v dokumentaci k prostředkům a ukázkám, které jsou k dispozici v dokumentaci sady [TRAVIS CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)a [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

Dva obecné přístupy, které přiberete při vytváření struktury procesu sestavení pro kód .NET Core pomocí nástrojů .NET Core, používají přímo nástroj MSBuild nebo pomocí příkazů příkazového řádku .NET Core. Jaký přístup byste měli vzít v úvahu, závisí na vaší úrovni pohodlí s ohledem na složitost a kompromisy. Nástroj MSBuild poskytuje možnost vyjádřit svůj proces sestavení jako úkoly a cíle, ale obsahuje i zvýšení složitosti syntaxe souboru projektu MSBuild. Použití nástrojů příkazového řádku .NET Core je možná jednodušší, ale vyžaduje, abyste napsali logiku orchestrace ve skriptovacím jazyce, jako je například `bash` PowerShell.

## <a name="see-also"></a>Viz také

- [Soubory ke stažení pro .NET – Linux](https://dotnet.microsoft.com/download?initial-os=linux)
