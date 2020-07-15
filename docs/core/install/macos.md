---
title: Nainstalovat .NET Core na macOS
description: Přečtěte si, na jaké verze macOS můžete .NET Core nainstalovat.
author: adegeo
ms.author: adegeo
ms.date: 06/25/2020
ms.openlocfilehash: 2900d98dbd30c51f689cdce37ea273ccc4f598b5
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308920"
---
# <a name="install-net-core-on-macos"></a>Nainstalovat .NET Core na macOS

> [!div class="op_single_selector"]
>
> - [Instalace v systému Windows](windows.md)
> - [Instalace v systému macOS](macos.md)
> - [Instalace v systému Linux](linux.md)

V tomto článku se dozvíte, jak nainstalovat .NET Core na macOS. .NET Core se skládá z modulu runtime a sady SDK. Modul runtime se používá ke spuštění aplikace .NET Core a může nebo nemusí být součástí aplikace. Sada SDK se používá k vytváření aplikací a knihoven .NET Core. Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.

Nejnovější verze .NET Core je 3,1.

> [!div class="button"]
> [Stáhnout .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>Podporované verze

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze macOS, na kterých jsou podporované. Tato verze zůstane podporovaná, protože verze [.NET Core dosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

- ✔️ označuje, že verze rozhraní .NET Core je stále podporovaná.
- A ❌ označuje, že verze rozhraní .NET Core není podporována.

| Operační systém          | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview |
|---------------------------|---------------|---------------|----------------|
| macOS 10,15 "Catalina"    | ✔️ 2,1 ([poznámky k verzi][release-notes-21]) | ✔️ 3,1 ([poznámky k verzi][release-notes-31]) | ✔️ 5,0 Preview ([poznámky k verzi][release-notes-50]) |
| macOS 10,14 "Mojave"      | ✔️ 2,1 ([poznámky k verzi][release-notes-21]) | ✔️ 3,1 ([poznámky k verzi][release-notes-31]) | ✔️ 5,0 Preview ([poznámky k verzi][release-notes-50]) |
| macOS 10,13 "High Sierra" | ✔️ 2,1 ([poznámky k verzi][release-notes-21]) | ✔️ 3,1 ([poznámky k verzi][release-notes-31]) | ✔️ 5,0 Preview ([poznámky k verzi][release-notes-50]) |
| macOS 10,12 "Sierra"      | ✔️ 2,1 ([poznámky k verzi][release-notes-21]) | ❌3,1 ([poznámky k verzi][release-notes-31]) | ❌5,0 Preview ([poznámky k verzi][release-notes-50]) |

## <a name="unsupported-releases"></a>Nepodporované verze

Následující verze rozhraní .NET Core již nejsou ❌ podporovány. Soubory ke stažení pro tyto soubory zůstanou publikované:

- 3,0 ([poznámky k verzi][release-notes-30])
- 2,2 ([poznámky k verzi][release-notes-22])
- 2,0 ([poznámky k verzi][release-notes-20])

## <a name="runtime-information"></a>Běhové informace

Modul runtime se používá ke spouštění aplikací vytvořených pomocí .NET Core. Když autor aplikace publikuje aplikaci, může do své aplikace zahrnout modul runtime. Pokud neobsahují modul runtime, je uživatel k instalaci modulu runtime.

V macOS můžete nainstalovat tři různé moduly runtime:

*Modul runtime ASP.NET Core*\
Spustí aplikace ASP.NET Core. Zahrnuje modul runtime .NET Core.

*Modul runtime .NET Core*\
Tento modul runtime je nejjednodušším modulem runtime a neobsahuje žádné další moduly runtime. Pro zajištění nejlepší kompatibility s aplikacemi .NET Core důrazně doporučujeme nainstalovat *ASP.NET Core Runtime* .

> [!div class="button"]
> [Stáhnout .NET Core Runtime](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>Informace o sadě SDK

Sada SDK se používá k sestavování a publikování aplikací a knihoven .NET Core. Instalace sady SDK zahrnuje jak [běhové prostředí](#runtime-information): ASP.NET Core, tak .NET Core.

> [!div class="button"]
> [Stáhnout .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a>Závislosti

Rozhraní .NET Core je podporované v následujících verzích macOS:

> [!NOTE]
> `+`Symbol představuje minimální verzi.

| Verze .NET Core | macOS                 | Architektury |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | Velký Sierra (10.13 +)  | x64 | [Další informace](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | Velký Sierra (10.13 +)  | x64 | [Další informace](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2,2               | Sierra (10.12 +)       | x64 | [Další informace](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12 +)       | x64 | [Další informace](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

Od macOS Catalina (verze 10,15) je nutné, aby byl veškerý software sestavený po 1. června 2019, který je distribuován s ID vývojáře, notarized. Tento požadavek se vztahuje na modul runtime .NET Core, .NET Core SDK a software vytvořený pomocí .NET Core.

Instalační programy pro .NET Core (běhové i sady SDK) verze 3,1, 3,0 a 2,1 byly notarized od 18. února 2020. Předchozí vydané verze nejsou notarized. Pokud spustíte aplikaci, která není notarized, zobrazí se chybová zpráva podobná následujícímu obrázku:

![Výstraha macOS Catalina notarization](media/dependencies/macos-notarized-pkg-warning.png)

Další informace o tom, jak vynucované notarization má vliv na rozhraní .NET Core (a aplikace .NET Core), najdete v tématu [Working with MacOS Catalina notarization](macos-notarization-issues.md).

## <a name="libgdiplus"></a>libgdiplus

Aplikace .NET Core, které používají *System. Drawing. Common* Assembly, vyžadují, aby bylo možné nainstalovat libgdiplus.

Snadný způsob, jak získat libgdiplus, je použít Správce balíčků [homebrew ("Brew")](https://brew.sh/) pro MacOS. Po instalaci *Brew*nainstalujte libgdiplus spuštěním následujících příkazů na příkazovém řádku terminálu (Command):

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

macOS má samostatné instalační programy, které se dají použít k instalaci sady .NET Core 3,1 SDK:

- [Procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Stažení a ruční instalace

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

Jako alternativu k instalačním modulům macOS pro .NET Core si můžete stáhnout a ručně nainstalovat sadu SDK a modul runtime. Ruční instalace se obvykle provádí jako součást testování průběžné integrace. Pro vývojáře nebo uživatele je obecně lepší použít [instalační program](https://dotnet.microsoft.com/download/dotnet-core).

Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime. Nejprve stáhněte **binární** verzi pro sadu SDK nebo modul runtime z jednoho z následujících lokalit:

- [soubory ke stažení ✔️ .net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)
- [soubory ke stažení ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [soubory ke stažení ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Všechny soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

Dále Extrahujte stažený soubor a pomocí `export` příkazu nastavte proměnné používané .NET Core a pak zajistěte, aby byl .NET Core v cestě.

Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve Stáhněte binární verzi .NET Core. Pak otevřete terminál a spusťte následující příkazy z adresáře, kam byl soubor uložen. Název souboru archivu se může lišit v závislosti na tom, co jste stáhli.

**K extrakci modulu runtime použijte následující příkaz**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.5-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**K extrakci sady SDK použijte následující příkaz**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Předchozí `export` příkazy zpřístupní pouze příkazy .NET Core CLI pro relaci terminálu, ve které byla spuštěna.
>
> Úpravou profilu prostředí můžete tyto příkazy trvale přidat. K dispozici je řada různých prostředí pro Linux a každá má jiný profil. Příklad:
>
> - **Prostředí bash**: *~/. bash_profile*, *~/.bashrc*
> - **Korn shell**: *~/.KSHRC* nebo *. Profile*
> - **Prostředí Z**: *~/.zshrc* nebo *. zprofile*
>
> Upravte příslušný zdrojový soubor pro prostředí a přidejte `:$HOME/dotnet` na konec existujícího `PATH` příkazu. Pokud `PATH` není žádný příkaz zahrnutý, přidejte nový řádek s `export PATH=$PATH:$HOME/dotnet` .
>
> Přidejte také `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.

Tento přístup umožňuje nainstalovat různé verze do samostatných umístění a zvolit, která z nich se má použít pro kterou aplikaci.

## <a name="install-with-visual-studio-for-mac"></a>Instalace pomocí Visual Studio pro Mac

Visual Studio pro Mac nainstaluje .NET Core SDK při výběru úlohy **.NET Core** . Chcete-li začít s vývojem .NET Core v macOS, přečtěte si téma [instalace sady Visual Studio 2019 for Mac](/visualstudio/mac/installation). Pro nejnovější vydání .NET Core 3,1 je nutné použít Visual Studio pro Mac 8,4 Preview.

[![macOS Visual Studio 2019 for Mac s funkcí úlohy .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>Nainstalovat společně Visual Studio Code

Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači. Visual Studio Code je k dispozici pro Windows, macOS a Linux.

I když Visual Studio Code nepřichází s automatizovaným instalačním programem .NET Core, jako je Visual Studio, přidání podpory .NET Core je jednoduché.

01. [Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).
01. [Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).
01. [Nainstalujte rozšíření C# z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

## <a name="install-with-bash-automation"></a>Instalace pomocí služby bash Automation

[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime. Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1. Konkrétní vydání můžete zvolit zadáním `current` přepínače. Zahrňte `runtime` přepínač pro instalaci modulu runtime. V opačném případě skript nainstaluje [sadu SDK](sdk.md).

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> Výše uvedený příkaz nainstaluje modul runtime ASP.NET Core, aby se maximální kompatibilita mohla. Modul runtime ASP.NET Core zahrnuje také standardní modul runtime .NET Core.

## <a name="docker"></a>Docker

Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému. Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.

.NET Core může běžet v kontejneru Docker. Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.

Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře. Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.

Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Další kroky

- [Jak zjistit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md?pivots=os-macos).
- [Práce s MacOS Catalina notarization](macos-notarization-issues.md).
- [Kurz: Začínáme s MacOS](../tutorials/using-on-mac-vs.md).
- [Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
