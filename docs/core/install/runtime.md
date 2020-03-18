---
title: Instalace runtime .NET Core ve Windows, Linuxu a macOS - .NET Core
description: Přečtěte si, jak nainstalovat jádro .NET do Windows, Linuxu a macOS. Seznamte se se závislostmi potřebnými ke spuštění aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399012"
---
# <a name="install-the-net-core-runtime"></a>Instalace rozhraní .NET Core Runtime

V tomto článku se dozvíte, jak stáhnout a nainstalovat zaběhu .NET Core. Runtime .NET Core se používá ke spouštění aplikací vytvořených pomocí .NET Core.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

Systém Windows má samostatné instalační programy, které lze použít k instalaci runtime .NET Core 3.1:

- [procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [x86 (32bitové) procesory](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

macOS má samostatné instalační programy, které lze použít k instalaci runtime .NET Core 3.1:

- [procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Stažení a ruční instalace

Jako alternativu k instalačním programům macOS pro .NET Core můžete stáhnout a ručně nainstalovat runtime.

Chcete-li nainstalovat runtime a povolit příkazy rozhraní PŘÍKAZU .NET Core, které jsou k dispozici na terminálu, [nejprve stáhněte](#all-net-core-downloads) binární verzi .NET Core. Potom otevřete terminál a spusťte následující příkazy. Předpokládá se, že runtime je `~/Downloads/dotnet-runtime.pkg` stažen do souboru.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalace pomocí správce balíčků

Runtime .NET Core Runtime můžete nainstalovat s mnoha běžnými správci balíčků Linuxu. Další informace naleznete v [tématu Linux Package Manager - Install .NET Core](linux-package-managers.md).

Instalace se správcem balíčků je podporována pouze na architektuře x64. Pokud instalujete rozhraní .NET Core Runtime s jinou architekturou, jako je arm, postupujte podle pokynů v části [Stáhnout a ručně nainstalovat.](#download-and-manually-install) Další informace o podporovaných architekturách naleznete v [tématu .NET Core závislosti a požadavky](dependencies.md).

## <a name="download-and-manually-install"></a>Stažení a ruční instalace

Chcete-li extrahovat runtime a zpřístupnit příkazy rozhraní PŘÍKAZOvého kódu .NET Core na terminálu, [stáhněte si nejprve](#all-net-core-downloads) binární verzi .NET Core. Potom otevřete terminál a spusťte následující příkazy.

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
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

Tento přístup umožňuje nainstalovat různé verze do samostatných umístění a explicitně zvolit, kterou z nich použít, kterou aplikací.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalace s automatizací Prostředí PowerShell

Skripty [dotnet-install](../tools/dotnet-install-script.md) se používají pro automatizaci a instalace runtime bez oprávnění správce. Skript si můžete stáhnout z [referenční stránky skriptu dotnet-install](../tools/dotnet-install-script.md).

Skript je výchozí pro instalaci nejnovější verze [dlouhodobé podpory (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) která je .NET Core 3.1. Určitou verzi můžete zvolit zadáním přepínače. `Channel` Zahrňte `Runtime` přepínač pro instalaci runtime. V opačném případě skript nainstaluje sadu [SDK](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> Výše uvedený příkaz nainstaluje ASP.NET core runtime pro maximální kompatibilitu. ASP.NET Core runtime také obsahuje standardní .NET Core runtime.

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

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalace s automatizací bash

Skripty [dotnet-install](../tools/dotnet-install-script.md) se používají pro automatizaci a instalace runtime bez oprávnění správce. Skript si můžete stáhnout z [referenční stránky skriptu dotnet-install](../tools/dotnet-install-script.md).

Skript je výchozí pro instalaci nejnovější verze [dlouhodobé podpory (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) která je .NET Core 3.1. Určitou verzi můžete zvolit zadáním přepínače. `current` Zahrňte `runtime` přepínač pro instalaci runtime. V opačném případě skript nainstaluje sadu [SDK](sdk.md).

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> Výše uvedený příkaz nainstaluje ASP.NET core runtime pro maximální kompatibilitu. ASP.NET Core runtime také obsahuje standardní .NET Core runtime.

::: zone-end

## <a name="all-net-core-downloads"></a>Všechny soubory ke stažení .NET Core

Můžete si stáhnout a nainstalovat .NET Core přímo s jedním z následujících odkazů:

- [Soubor ke stažení .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Soubor ke stažení .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kontejnery poskytují lehký způsob, jak izolovat aplikace od zbytku hostitelského systému. Kontejnery na stejném počítači sdílejí pouze jádro a používají prostředky dané vaší aplikaci.

Jádro .NET lze spustit v kontejneru Dockeru. Oficiální image .NET Core Docker umožnou v registru Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Každé úložiště obsahuje obrázky pro různé kombinace .NET (SDK nebo Runtime) a Operačního serveru, které můžete použít.

Společnost Microsoft poskytuje obrázky, které jsou přizpůsobeny pro konkrétní scénáře. [Například úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje image, které jsou vytvořené pro spouštění aplikací ASP.NET Core v produkčním prostředí.

Další informace o použití .NET Core v kontejneru Dockeru najdete v [tématu Úvod do .NET a Docker](../docker/introduction.md) a [ukázky](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Další kroky

- [Jak zkontrolovat, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md).
