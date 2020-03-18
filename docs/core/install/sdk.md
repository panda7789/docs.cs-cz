---
title: Instalace sady .NET Core SDK ve Windows, Linuxu a macOS - .NET Core
description: Přečtěte si, jak nainstalovat jádro .NET do Windows, Linuxu a macOS. Seznamte se s závislostimi potřebnými k vývoji aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399005"
---
# <a name="install-the-net-core-sdk"></a>Nainstalujte sadu .NET Core SDK.

V tomto článku se dozvíte, jak nainstalovat sadu .NET Core SDK. Sada .NET Core SDK se používá k vytváření aplikací a knihoven .NET Core. Runtime jádra .NET je vždy nainstalován s sadou SDK.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

Systém Windows má samostatné instalační programy, které lze použít k instalaci sady .NET Core 3.1 SDK:

- [procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32bitové) procesory](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

macOS má samostatné instalační programy, které lze použít k instalaci sady .NET Core 3.1 SDK:

- [procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Stažení a ruční instalace

Jako alternativu k instalačním programům macOS pro .NET Core můžete stáhnout a ručně nainstalovat sdk.

Chcete-li extrahovat sadu SDK a zpřístupnit příkazy rozhraní PŘÍKAZOvého kódu .NET Core na terminálu, [stáhněte si nejprve](#all-net-core-downloads) binární verzi .NET Core. Potom otevřete terminál a spusťte následující příkazy. Předpokládá se, že runtime je `~/Downloads/dotnet-sdk.pkg` stažen do souboru.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalace pomocí správce balíčků

Sada .NET Core SDK můžete nainstalovat s mnoha běžnými správci balíčků Linuxu. Další informace naleznete v [tématu Linux Package Manager - Install .NET Core](linux-package-managers.md).

Instalace se správcem balíčků je podporována pouze na architektuře x64. Pokud instalujete sdk .NET Core SDK s jinou architekturou, jako je arm, postupujte podle pokynů [ke stažení a ručně nainstalujte](#download-and-manually-install) níže. Další informace o podporovaných architekturách naleznete v [tématu .NET Core závislosti a požadavky](dependencies.md).

## <a name="download-and-manually-install"></a>Stažení a ruční instalace

Chcete-li extrahovat sadu SDK a zpřístupnit příkazy rozhraní PŘÍKAZOvého kódu .NET Core na terminálu, [stáhněte si nejprve](#all-net-core-downloads) binární verzi .NET Core. Potom otevřete terminál a spusťte následující příkazy.

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Předchozí `export` příkazy zpřístupní pouze příkazy rozhraní PŘÍKAZU KONT .NET Core pro terminálovou relaci, ve které bylo spuštěno.
>
> Chcete-li trvale přidat příkazy, můžete upravit profil prostředí. Existuje celá řada různých shellů k dispozici pro Linux a každý má jiný profil. Například:
>
> - **Bash Shell**: *~/.bash_profile*, *~/.bashrc*
> - **Korn Shell**: *~/.kshrc* nebo *.profil*
> - **Z Shell**: *~/.zshrc* nebo *.zprofile*
>
> Upravte příslušný zdrojový soubor prostředí `:$HOME/dotnet` a přidejte `PATH` na konec existujícího příkazu. Pokud `PATH` není zahrnut žádný příkaz, `export PATH=$PATH:$HOME/dotnet`přidejte nový řádek s .
>
> Také přidejte `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Instalace pomocí sady Visual Studio

Pokud používáte Visual Studio k vývoji aplikací .NET Core, následující tabulka popisuje minimální požadovanou verzi sady Visual Studio založenou na cílové verzi sady .NET Core SDK.

| Verze sady .NET Core SDK | Verze sady Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 verze 16.4 nebo vyšší. |
| 3.0                   | Visual Studio 2019 verze 16.3 nebo vyšší. |
| 2,2                   | Visual Studio 2017 verze 15.9 nebo vyšší. |
| 2.1                   | Visual Studio 2017 verze 15.7 nebo vyšší. |

Pokud už máte nainstalovaný Visual Studio, můžete zkontrolovat verzi pomocí následujících kroků.

01. Otevřete sadu Visual Studio.
01. Vyberte **nápovědu k** > **aplikaci Microsoft Visual Studio**.
01. Přečtěte si číslo verze v dialogovém okně **Informace.**

Visual Studio můžete nainstalovat nejnovější .NET Core SDK a runtime.

- [Stáhnout visual studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Výběr pracovního vytížení

Při instalaci nebo úpravě sady Visual Studio vyberte jednu nebo více následujících úloh v závislosti na druhu vytvářené aplikace:

- Úloha **vývoje napříč platformami .NET Core** v části **Ostatní sady nástrojů.**
- **Úloha ASP.NET a vývoj webových** aplikací v části **Web & Cloud.**
- Úloha **vývoje Azure** v části **Web & Cloud.**
- Úloha **vývoje plochy .NET** v části **Desktop & Mobile.**

[![Windows Visual Studio 2019 s úlohami jádra .NET](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="download-and-manually-install"></a>Stažení a ruční instalace

Chcete-li extrahovat runtime a zpřístupnit příkazy rozhraní PŘÍKAZOvého kódu .NET Core na terminálu, [stáhněte si nejprve](#all-net-core-downloads) binární verzi .NET Core. Potom vytvořte adresář, do který `%USERPROFILE%\dotnet`se chcete nainstalovat, například . Nakonec extrahujte stažený soubor zip do tohoto adresáře.

Ve výchozím nastavení nebudou příkazy a aplikace rozhraní .NET Core CLI používat tímto způsobem nainstalované .NET Core. Musíte explicitně zvolit jeho použití. Chcete-li tak učinit, změňte proměnné prostředí, se kterými je aplikace spuštěna:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

Tento přístup umožňuje nainstalovat více verzí do samostatných umístění, pak explicitně zvolit, které umístění instalace aplikace by měla používat spuštěním aplikace s proměnnými prostředí ukazující na toto umístění.

I když jsou tyto proměnné prostředí nastaveny, .NET Core stále považuje výchozí globální umístění instalace při výběru nejlepší rozhraní pro spuštění aplikace. Výchozí hodnota je `C:\Program Files\dotnet`obvykle , které instalační programy používají. Můžete dát pokyn, aby runtime používal pouze vlastní umístění instalace nastavením této proměnné prostředí:

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Instalace pomocí Visual Studia pro Mac

Visual Studio pro Mac nainstaluje sdk jádra .NET, když je vybráno zatížení **jádra .NET.** Pokud chcete začít s vývojem jádra .NET v macOS, přečtěte si informace [o instalaci Visual Studia 2019 pro Mac](/visualstudio/mac/installation). Pro nejnovější verzi .NET Core 3.1, musíte použít Visual Studio pro Mac 8.4 Náhled.

[![macOS Visual Studio 2019 pro Mac s funkcí zatížení Jádra .NET](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-alongside-visual-studio-code"></a>Instalace vedle kódu sady Visual Studio

Visual Studio Code je výkonný a lehký editor zdrojového kódu, který běží na ploše. Visual Studio Code je k dispozici pro Windows, macOS a Linux.

Zatímco Visual Studio Code nepřichází s automatickou instalační službou .NET Core, jako je visual studio, přidání podpory .NET Core je jednoduché.

01. [Stáhněte a nainstalujte kód sady Visual Studio](https://code.visualstudio.com/Download).
01. [Stáhněte a nainstalujte sadu .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).
01. [Nainstalujte rozšíření C# ze tržiště kódu sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalace s automatizací Prostředí PowerShell

Skripty [dotnet-install](../tools/dotnet-install-script.md) se používají pro automatizaci a instalace sady SDK bez oprávnění správce. Skript si můžete stáhnout z [referenční stránky skriptu dotnet-install](../tools/dotnet-install-script.md).

Skript je výchozí pro instalaci nejnovější verze [dlouhodobé podpory (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) která je .NET Core 3.1. Chcete-li nainstalovat aktuální verzi rozhraní .NET Core, spusťte skript s následujícím přepínačem.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalace s automatizací bash

Skripty [dotnet-install](../tools/dotnet-install-script.md) se používají pro automatizaci a instalace sady SDK bez oprávnění správce. Skript si můžete stáhnout z [referenční stránky skriptu dotnet-install](../tools/dotnet-install-script.md).

Skript je výchozí pro instalaci nejnovější verze [dlouhodobé podpory (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) která je .NET Core 3.1. Chcete-li nainstalovat aktuální verzi rozhraní .NET Core, spusťte skript s následujícím přepínačem.

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>Všechny soubory ke stažení .NET Core

Můžete si stáhnout a nainstalovat .NET Core přímo s jedním z následujících odkazů:

- [Soubor ke stažení .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Soubor ke stažení .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Soubor ke stažení .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Soubor ke stažení .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kontejnery poskytují lehký způsob, jak izolovat aplikace od zbytku hostitelského systému. Kontejnery na stejném počítači sdílejí pouze jádro a používají prostředky dané vaší aplikaci.

Jádro .NET lze spustit v kontejneru Dockeru. Oficiální image .NET Core Docker umožnou v registru Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Každé úložiště obsahuje obrázky pro různé kombinace .NET (SDK nebo Runtime) a Operačního serveru, které můžete použít.

Společnost Microsoft poskytuje obrázky, které jsou přizpůsobeny pro konkrétní scénáře. [Například úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje image, které jsou vytvořené pro spouštění aplikací ASP.NET Core v produkčním prostředí.

Další informace o použití .NET Core v kontejneru Dockeru najdete v [tématu Úvod do .NET a Docker](../docker/introduction.md) a [ukázky](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Další kroky

::: zone pivot="os-windows"

- [Výukový program: Hello World tutorial](../tutorials/with-visual-studio.md).
- [Kurz: Vytvoření nové aplikace s visual studio kód](../tutorials/with-visual-studio-code.md).
- [Kurz: Kontejnerize .NET Core aplikace](../docker/build-container.md).

::: zone-end

::: zone pivot="os-macos"

- [Práce s notářizací macOS Catalina](macos-notarization-issues.md).
- [Kurz: Začínáme s macOS](../tutorials/using-on-mac-vs.md).
- [Kurz: Vytvoření nové aplikace s visual studio kód](../tutorials/with-visual-studio-code.md).
- [Kurz: Kontejnerize .NET Core aplikace](../docker/build-container.md).

::: zone-end

::: zone pivot="os-linux"

- [Kurz: Vytvoření nové aplikace s visual studio kód](../tutorials/with-visual-studio-code.md).
- [Kurz: Kontejnerize .NET Core aplikace](../docker/build-container.md).

::: zone-end
