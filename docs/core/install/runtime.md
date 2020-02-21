---
title: Instalace modulu runtime .NET Core v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné ke spouštění aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ba50eb222d9eab6bffbb8ebfdf0ecf47951ce719
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543518"
---
# <a name="install-the-net-core-runtime"></a>Instalace modulu runtime .NET Core

V tomto článku se dozvíte, jak stáhnout a nainstalovat modul runtime .NET Core. Modul runtime .NET Core se používá ke spouštění aplikací vytvořených pomocí .NET Core.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

Systém Windows obsahuje samostatné instalační programy, které lze použít k instalaci modulu runtime .NET Core 3,1:

- [Procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Procesory x86 (32 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

macOS má samostatné instalační programy, které se dají použít k instalaci modulu runtime .NET Core 3,1:

- [Procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalace pomocí Správce balíčků

Modul runtime .NET Core můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux. Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-managers.md).

Instalace pomocí Správce balíčků se podporuje jenom v architektuře x64. Pokud instalujete modul runtime .NET Core s jinou architekturou, jako je například ARM, postupujte podle pokynů v části [Stažení a ruční instalace](#download-and-manually-install) . Další informace o podporovaných architekturách najdete v tématu [závislosti a požadavky .NET Core](dependencies.md).

## <a name="download-and-manually-install"></a>Stažení a ruční instalace

Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core. Pak otevřete terminál a spusťte následující příkazy.

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Předchozí příkazy `export` zpřístupňují pouze příkazy .NET Core CLI dostupné pro relaci terminálu, ve které byla spuštěna.
>
> Úpravou profilu prostředí můžete tyto příkazy trvale přidat. K dispozici je řada různých prostředí pro Linux a každá má jiný profil. Příklad:
>
> - **Prostředí bash**: *~/. bash_profile*, *~/.bashrc*
> - **Korn shell**: *~/.KSHRC* nebo *. Profile*
> - **Prostředí Z**: *~/.zshrc* nebo *. zprofile*
> 
> Upravte příslušný zdrojový soubor pro prostředí a přidejte `:$HOME/dotnet` na konec existujícího příkazu `PATH`. Pokud není zahrnutý žádný příkaz `PATH`, přidejte nový řádek s `export PATH=$PATH:$HOME/dotnet`.
>
> Přidejte také `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.

Tento přístup umožňuje nainstalovat různé verze do samostatných umístění a zvolit, která z nich se má použít pro kterou aplikaci.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalace pomocí automatizace PowerShellu

[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime. Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1. Konkrétní vydání můžete zvolit zadáním přepínače `Channel`. Pokud chcete nainstalovat modul runtime, přidejte přepínač `Runtime`. V opačném případě skript nainstaluje [sadu SDK](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> Výše uvedený příkaz nainstaluje modul runtime ASP.NET Core, aby se maximální kompatibilita mohla. Modul runtime ASP.NET Core zahrnuje také standardní modul runtime .NET Core.

## <a name="download-and-manually-install"></a>Stažení a ruční instalace

Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core. Pak vytvořte adresář, do kterého chcete nainstalovat, například `%USERPROFILE%\dotnet`. Nakonec Extrahujte stažený soubor zip do tohoto adresáře.

Ve výchozím nastavení nepoužívají .NET Core CLI příkazy a aplikace tímto způsobem instalaci .NET Core. Musíte ho výslovně použít. Provedete to tak, že změníte proměnné prostředí, se kterými je aplikace spuštěná:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

Tento přístup umožňuje nainstalovat více verzí do samostatných umístění a pak explicitně zvolit umístění instalace, které by měla aplikace používat, a to spuštěním aplikace s proměnnými prostředí, které ukazují na toto umístění.

I v případě, že jsou tyto proměnné prostředí nastaveny, .NET Core při výběru nejlepšího rozhraní pro spuštění aplikace i nadále posuzuje výchozí globální umístění instalace. Výchozí hodnota je obvykle `C:\Program Files\dotnet`, kterou instalační programy používají. Modulu runtime můžete dát pokyn, aby používal pouze vlastní umístění instalace, a to nastavením této proměnné prostředí:

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalace pomocí služby bash Automation

[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime. Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1. Konkrétní vydání můžete zvolit zadáním přepínače `current`. Pokud chcete nainstalovat modul runtime, přidejte přepínač `runtime`. V opačném případě skript nainstaluje [sadu SDK](sdk.md).

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> Výše uvedený příkaz nainstaluje modul runtime ASP.NET Core, aby se maximální kompatibilita mohla. Modul runtime ASP.NET Core zahrnuje také standardní modul runtime .NET Core.

::: zone-end

## <a name="all-net-core-downloads"></a>Všechny soubory ke stažení pro .NET Core

.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:

- [Soubory ke stažení pro .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Soubory ke stažení pro .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Soubory ke stažení pro .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému. Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.

.NET Core může běžet v kontejneru Docker. Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.

Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře. Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.

Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Další kroky

- [Jak zjistit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md).
