---
title: Instalace .NET Core SDK v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné pro vývoj aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 6e9af6c84c81b1244e10fa7d5955ab67d34b1f0a
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552206"
---
# <a name="install-the-net-core-sdk"></a>Instalace .NET Core SDK

V tomto článku se naučíte, jak nainstalovat .NET Core SDK. .NET Core SDK slouží k vytváření aplikací a knihoven .NET Core. Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.

.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:

- [Soubory ke stažení pro .NET Core 3,1 Preview 3](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Soubory ke stažení pro .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Soubory ke stažení pro .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

.NET Core můžete nainstalovat také jako součást integrovaného vývojového prostředí (IDE), které jsou podrobně popsané v následujících částech.

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

Windows i macOS mají samostatné instalační programy, které je možné použít k instalaci sady .NET Core 3,0 SDK.

- Procesory Windows [x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [procesory x32](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)
- macOS [procesory x64](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalace pomocí Správce balíčků

.NET Core SDK můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux. Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-manager-rhel7.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Instalace se sadou Visual Studio

Pokud používáte Visual Studio pro vývoj aplikací .NET Core, v následující tabulce je popsána minimální požadovaná verze sady Visual Studio na základě cílové verze .NET Core SDK.

| Verze .NET Core SDK | Verze sady Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3,0                   | Visual Studio 2019 verze 16,3 nebo vyšší. |
| 2,2                   | Visual Studio 2017 verze 15,9 nebo vyšší. |
| 2,1                   | Visual Studio 2017 verze 15,7 nebo vyšší. |

Pokud již máte nainstalováno Visual Studio, můžete si ověřit verzi pomocí následujících kroků.

01. Otevřete Visual Studio.
01. Vyberte **nápovědu** > **o Microsoft Visual Studio**.
01. Přečtěte si číslo verze v dialogovém okně **o produktu** .

Visual Studio může nainstalovat nejnovější .NET Core SDK a modul runtime.

- [Stáhněte si Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Vyberte úlohu.

Při instalaci nebo úpravách sady Visual Studio vyberte jednu z následujících úloh v závislosti na typu aplikace, kterou sestavujete:

- Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .
- Úlohy **vývoje ASP.NET a webu** v části **web & Cloud** .
- Úlohy **vývoje Azure** v části **web & cloudu** .
- Úloha **vývoj desktopových aplikací .NET** v části **Desktop & Mobile** .

[![Windows Visual Studio 2019 s úlohou .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Instalace pomocí Visual Studio pro Mac

Visual Studio pro Mac nainstaluje .NET Core SDK při výběru úlohy **.NET Core** . Chcete-li začít s vývojem .NET Core v macOS, přečtěte si téma [instalace sady Visual Studio 2019 for Mac](/visualstudio/mac/installation).

[![macOS sady Visual Studio 2019 pro Mac s funkcí úlohy .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-from-visual-studio-code"></a>Nainstalovat z Visual Studio Code

Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači. Visual Studio Code je k dispozici pro Windows, macOS a Linux.

I když Visual Studio Code nepřináší podporu .NET Core, je přidání podpory .NET Core jednoduché.

01. [Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).
01. [Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).
01. [Nainstalujte C# rozšíření z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalace pomocí automatizace PowerShellu

[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy. Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1. Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalace pomocí služby bash Automation

[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci sady SDK bez správy. Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1. Chcete-li nainstalovat aktuální vydání rozhraní .NET Core, spusťte skript s následujícím přepínačem.

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a>Docker

Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému. Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.

.NET Core může běžet v kontejneru Docker. Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.

Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře. Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.

Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Další kroky

::: zone pivot="os-windows"

- [Kurz: C# kurz Hello World](../tutorials/with-visual-studio.md).
- [Kurz: kurz Hello World Visual Basic](../tutorials/vb-with-visual-studio.md).
- [Kurz: vytvoření nové aplikace pomocí Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).
- [Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)

::: zone-end

::: zone pivot="os-macos"

- [Kurz: Začínáme s MacOS](../tutorials/using-on-mac-vs.md).
- [Kurz: vytvoření nové aplikace pomocí Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).
- [Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)

::: zone-end
