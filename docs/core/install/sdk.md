---
title: Instalace .NET Core SDK v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné pro vývoj aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 4a6c8b27812e9f60e52132169dda0464c24abcc2
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740563"
---
# <a name="install-the-net-core-sdk"></a>Instalace .NET Core SDK

V tomto článku se naučíte, jak nainstalovat .NET Core SDK. .NET Core SDK slouží k vytváření aplikací a knihoven .NET Core. Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

Systém Windows obsahuje samostatné instalační programy, které lze použít k instalaci sady .NET Core 3,1 SDK:

- [Procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Procesory x86 (32 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

macOS má samostatné instalační programy, které se dají použít k instalaci sady .NET Core 3,1 SDK:

- [Procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalace pomocí Správce balíčků

.NET Core SDK můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux. Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-managers.md).

Instalace pomocí Správce balíčků se podporuje jenom v architektuře x64. Pokud .NET Core SDK instalujete s jinou architekturou, jako je například ARM, postupujte podle pokynů níže v části [Stažení a ruční instalace](#download-and-manually-install) . Další informace o podporovaných architekturách najdete v tématu [závislosti a požadavky .NET Core](dependencies.md).

## <a name="download-and-manually-install"></a>Stažení a ruční instalace

K extrakci sady SDK a zpřístupnění .NET Core CLI příkazů v terminálu, nejprve [Stáhněte](#all-net-core-downloads) binární verzi .NET Core. Pak otevřete terminál a spusťte následující příkazy.

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
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

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Instalace se sadou Visual Studio

Pokud používáte Visual Studio pro vývoj aplikací .NET Core, v následující tabulce je popsána minimální požadovaná verze sady Visual Studio na základě cílové verze .NET Core SDK.

| Verze .NET Core SDK | Verze sady Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 verze 16,4 nebo vyšší. |
| 3,0                   | Visual Studio 2019 verze 16,3 nebo vyšší. |
| 2.2                   | Visual Studio 2017 verze 15,9 nebo vyšší. |
| 2.1                   | Visual Studio 2017 verze 15,7 nebo vyšší. |

Pokud již máte nainstalováno Visual Studio, můžete si ověřit verzi pomocí následujících kroků.

01. Otevřít Visual Studio.
01. Vyberte **nápovědu** > **o Microsoft Visual Studio**.
01. Přečtěte si číslo verze v dialogovém okně **o produktu** .

Visual Studio může nainstalovat nejnovější .NET Core SDK a modul runtime.

- [Stáhněte si Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Vyberte úlohu.

Při instalaci nebo úpravách sady Visual Studio vyberte jednu nebo více následujících úloh v závislosti na typu aplikace, kterou vytváříte:

- Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .
- Úlohy **vývoje ASP.NET a webu** v části **web & Cloud** .
- Úlohy **vývoje Azure** v části **web & cloudu** .
- Úloha **vývoj desktopových aplikací .NET** v části **Desktop & Mobile** .

[![Windows Visual Studio 2019 s úlohou .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Instalace pomocí Visual Studio pro Mac

Visual Studio pro Mac nainstaluje .NET Core SDK při výběru úlohy **.NET Core** . Chcete-li začít s vývojem .NET Core v macOS, přečtěte si téma [instalace sady Visual Studio 2019 for Mac](/visualstudio/mac/installation). Pro nejnovější vydání .NET Core 3,1 je nutné použít Visual Studio pro Mac 8,4 Preview.

[![macOS sady Visual Studio 2019 pro Mac s funkcí úlohy .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-alongside-visual-studio-code"></a>Nainstalovat společně Visual Studio Code

Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači. Visual Studio Code je k dispozici pro Windows, macOS a Linux.

I když Visual Studio Code nepřichází s automatizovaným instalačním programem .NET Core, jako je Visual Studio, přidání podpory .NET Core je jednoduché.

01. [Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).
01. [Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).
01. [Nainstalujte C# rozšíření z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalace pomocí automatizace PowerShellu

[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy. Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1. Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalace pomocí služby bash Automation

[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy. Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1. Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.

```bash
./dotnet-install.sh -c Current
```

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

::: zone pivot="os-windows"

- [Kurz: kurz Hello World](../tutorials/with-visual-studio.md).
- [Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)

::: zone-end

::: zone pivot="os-macos"

- [Kurz: Začínáme s MacOS](../tutorials/using-on-mac-vs.md).
- [Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)

::: zone-end

::: zone pivot="os-linux"

- [Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)

::: zone-end
