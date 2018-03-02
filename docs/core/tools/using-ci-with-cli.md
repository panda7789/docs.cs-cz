---
title: "Pomocí rozhraní .NET Core SDK a nástrojů v nepřetržité integrace (CI)"
description: "Informace o použití rozhraní .NET Core SDK a její nástroje na buildovacím serveru."
keywords: "Rozhraní .NET, .NET core, průběžnou integraci, ci, sestavení, automatizace, Travis CI, AppVeyor, Visual Studio Team Services, služby vsts"
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0d6e1e34-277c-4aaf-9880-3ebf81023857
ms.workload:
- dotnetcore
ms.openlocfilehash: 552865f225ceac9e7a365452ee06d7fefeeb7213
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Pomocí rozhraní .NET Core SDK a nástrojů v nepřetržité integrace (CI)

## <a name="overview"></a>Přehled

Tento dokument popisuje pomocí jeho nástroje a rozhraní .NET Core SDK na sestavení serveru. .NET Core nástrojů funguje jak interaktivně, kde vývojář typy příkazů do příkazového řádku a automaticky, kde nepřetržité integrace konfigurace serveru spouští skript sestavení. Příkazy, možnosti, vstupy a výstupy jsou stejné, a pouze věcí, které zadáte představují způsob, jak získat nástroje a systém k sestavení aplikace. Tento dokument se zaměřuje na scénáře pořízení nástroj pro nepřetržitou Integraci s doporučeními pro návrh a struktury skripty sestavení.

## <a name="installation-options-for-ci-build-servers"></a>Možnosti instalace pro nepřetržitou Integraci sestavení servery

### <a name="using-the-native-installers"></a>Pomocí nativní instalační programy

Nativní instalační programy jsou k dispozici pro systému macOS, Linux a Windows. Instalační programy vyžadují správce (sudo) přístup k serveru sestavení. Výhodou použití nativní instalační program je nainstaluje všechny nativní závislosti potřebné pro nástrojů ke spuštění. Nativní instalační programy také poskytují systémové instalace sady SDK.

Uživatelé systému macOS by měl používat PKG instalační programy. V systému Linux je volba pomocí Správce balíčků na základě informačního kanálu, jako například výstižný get pro Ubuntu nebo yum pro CentOS, nebo pomocí balíčků, sami bázi DEB nebo ot. / min. V systému Windows použijte instalační služby MSI.

Nejnovější stabilní binární soubory se nacházejí v [Začínáme s .NET Core](https://aka.ms/dotnetcoregs). Pokud chcete použít předběžné verze nástroje nejnovější (a potenciálně nestabilním), pomocí odkazů uvedených v [úložiště GitHub dotnet nebo rozhraní příkazového řádku](https://github.com/dotnet/cli#installers-and-binaries). Pro Linux distribuce `tar.gz` archivy (také označované jako `tarballs`) jsou k dispozici, pomocí skriptů instalace v rámci archivu pro instalaci .NET Core.

### <a name="using-the-installer-script"></a>Pomocí skriptu Instalační program

Pomocí skriptu Instalační program umožňuje instalaci bez oprávnění správce na serveru sestavení a snadno automatizace pro získání nástrojů. Tento skript má na starosti stahování nástroje a extrahování do výchozí hodnotu nebo zadané umístění pro použití. Můžete také zadat verzi nástrojů, který chcete nainstalovat a jestli chcete nainstalovat celý SDK nebo pouze sdílený modul runtime.

Skript instalačního programu je automatizované ke spuštění na začátku sestavení pro načtení a nainstalujte požadovanou verzi sady SDK. *Požadovanou verzi* libovolnou verzi sady SDK vyžadovat projekty k sestavení. Skript můžete nainstalovat sadu SDK do místního adresáře na serveru, spusťte nástroje z umístění instalace a pak vyčistit (nebo nechat službu CI vyčištění) po sestavení. To poskytuje zapouzdření a izolaci celého procesu vytváření. Odkaz na instalační skript se nachází v [dotnet instalace](dotnet-install-script.md) tématu.

> [!NOTE]
> Pokud používáte skript instalačního programu, nativní závislosti se neinstalují automaticky. Pokud je operační systém nemá, je nutné nainstalovat nativní závislosti. Najdete v seznamu požadavky [.NET Core nativní požadavky](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) tématu.

## <a name="ci-setup-examples"></a>Instalační program Příklady položek konfigurace

Tato část popisuje ruční instalaci pomocí skriptu prostředí PowerShell nebo bash, společně s popis několik softwaru jako řešení položek konfigurace služba (SaaS). Řešení SaaS CI popsaná jsou [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), a [Visual Studio Team Services Build](https://docs.microsoft.com/vsts/build-release/index).

### <a name="manual-setup"></a>Ruční instalace

Každá služba SaaS má svou vlastní metody pro vytváření a konfigurace procesu sestavení. Pokud používáte jiné řešení SaaS než uvedených nebo vyžadují přizpůsobení kromě předem zabalené podpory, musíte provést minimálně část konfigurace ručně.

Obecně platí ruční instalaci, musíte získat verzi nástroje (nebo noční sestavení nástroje) a spusťte skript buildu. Můžete použít prostředí PowerShell nebo bash skript k orchestraci příkazy .NET Core nebo použít soubor projektu, který popisuje proces vytváření. [Orchestration části](#orchestrating-the-build) poskytující víc podrobností o těchto možnostech.

Jakmile vytvoříte skript, který provede ruční vytvoření položek konfigurace nastavení serveru, používejte ji na vývojářském počítači k vytvoření kódu místně pro účely testování. Jakmile potvrdíte, že skript běží i místně, nasaďte ho na vašem serveru sestavení položek konfigurace. Relativně jednoduché skript prostředí PowerShell ukazuje, jak získat .NET Core SDK a nainstalujte ji na server Windows sestavení:

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

Poskytnete implementace pro proces sestavení na konci tohoto skriptu. Skript získá nástroje a potom provede vašeho procesu sestavení. Následující skript bash pro počítače, UNIX, provede akce popsané v skriptu prostředí PowerShell podobným způsobem:

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

Můžete nakonfigurovat [Travis CI](https://travis-ci.org/) a nainstalovat .NET Core SDK `csharp` jazyk a `dotnet` klíč. O najdete v oficiální dokumentaci Travis CI [vytváření C#, F # nebo Visual Basic projektu](https://docs.travis-ci.com/user/languages/csharp/) Další informace. Všimněte si, jak je přístup k informacím Travis CI který udržuje komunitní `language: csharp` identifikátor jazyka funguje pro všechny jazyky rozhraní .NET, včetně F # a Mono.

Travis CI běží obou systému macOS (OS X 10.11, OS X 10.12) a Linux (Ubuntu 14.04) úlohy v *sestavení matice*, kde můžete určit kombinaci modul runtime, prostředí a vyloučení nebo zahrnutí tak, aby pokrývalo vaší kombinace sestavení pro vaši aplikaci. Najdete v článku [. Příklad travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml) souboru a [přizpůsobení sestavení](https://docs.travis-ci.com/user/customizing-the-build) v Travis CI dokumentace pro další informace. Nástroje využívající MSBuild zahrnout LTS (1.0.x) a aktuální moduly runtime (1.1.x) do balíčku. takže instalací sady SDK, se zobrazí všechny objekty, které potřebujete k vytváření.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) nainstaluje .NET Core 1.0.1 SDK `Visual Studio 2017` sestavení pracovní bitové kopie. Ostatní sestavení Image s různými verzemi nástroje .NET Core SDK jsou k dispozici. najdete v článku [appveyor.yml příklad](https://github.com/dotnet/docs/blob/master/appveyor.yml) a [vytvářet bitové kopie pracovní](https://www.appveyor.com/docs/build-environment/#build-worker-images) téma v AppVeyor dokumentace pro další informace.

.NET Core SDK binární soubory jsou stažené a rozbalené v podadresáři pomocí skriptu install a pak se přidá do `PATH` proměnné prostředí. Přidáte matici sestavení testy integrace s více verzemi .NET Core SDK:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="visual-studio-team-services-vsts"></a>Visual Studio Team Services (VSTS)

Konfigurace Visual Studio Team Services (služby VSTS) k vytvoření projektů .NET Core pomocí jedné z těchto postupů:

1. Spusťte skript ze [ruční instalaci krok](#manual-setup) vaše příkazy.
1. Vytvořte sestavení skládá z několika služby VSTS předdefinované sestavení úlohy, které jsou nakonfigurovány pro použití nástroje pro .NET Core.

Obě řešení jsou platné. Pomocí skriptu ruční instalace, můžete řídit verzi nástroje, které se zobrazí, protože jste je stáhnout jako součást sestavení. Sestavení se spouští ze skriptu, který je nutné vytvořit. Toto téma se vztahuje pouze na ruční. Další informace o sestavení pomocí služby VSTS skládání úlohy sestavení, přejděte služby VSTS [průběžnou integraci a nasazení](https://docs.microsoft.com/vsts/build-release/index) tématu.

Použití skriptu ruční instalaci v služby VSTS, vytvořte novou definici sestavení a zadejte skript, který chcete spustit pro krok sestavení. To se provádí pomocí uživatelského rozhraní služby VSTS:

1. Začněte vytvořením nové definice buildu. Jakmile se na obrazovce, která poskytuje možnost definovat, jaký druh sestavení, které chcete vytvořit, vyberte **prázdný** možnost.

   ![Výběr definici prázdný sestavení](./media/using-ci-with-cli/screen1.png)

1. Po dokončení konfigurace úložiště k sestavení, se přesměruje na definice sestavení. Vyberte **přidat krok sestavení**:

   ![Přidání kroku sestavení](./media/using-ci-with-cli/screen2.png)

1. Nabízí **úloha katalogu**. Katalog obsahuje úlohy, které použijete v buildu. Vzhledem k tomu, že máte skript, vyberte **přidat** tlačítko pro **prostředí PowerShell: spustit skript prostředí PowerShell**.

   ![Přidání kroku skriptu prostředí PowerShell](./media/using-ci-with-cli/screen3.png)

1. Nakonfigurujte krok sestavení. Přidejte skript z úložiště, který umožňuje vytvářet:

   ![Určení spuštění skriptu prostředí PowerShell](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a>Orchestrace sestavení

Většina tento dokument popisuje, jak získat nástroje .NET Core a nakonfigurovat různé služby CI bez zadání informací o tom, jak orchestraci, nebo *ve skutečnosti sestavení*, kódu s .NET Core. Volby o tom, jak struktury procesu sestavení závisí na mnoha faktorech, které nejde pokrýt obecné způsobem. Prozkoumejte prostředků a ukázky, které jsou součástí sady dokumentace [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), a [služby VSTS](https://docs.microsoft.com/vsts/build-release/index) Další informace o Orchestrace buildy s každým technologie.

Dva obecné přístupy, které provedete v procesu sestavení pro kód .NET Core pomocí nástrojů .NET Core strukturování jsou přímo pomocí nástroje MSBuild nebo používá příkazy příkazového řádku .NET Core. Jaký přístup byste měli vzít je určen podle vaše pohodlí úroveň s přístupy a kompromis složitostí. MSBuild poskytuje schopnost express vašeho procesu sestavení jako úlohy a cíle, ale se dodává s přidané složitosti učení syntaxe souboru projektu nástroje MSBuild. Pomocí nástroje příkazového řádku .NET Core je možná jednodušší, ale vyžaduje zapisovat orchestration logiku v skriptovací jazyk jako `bash` nebo prostředí PowerShell.

## <a name="see-also"></a>Viz také

[Postup získání Ubuntu](https://www.microsoft.com/net/core#linuxubuntu)   
