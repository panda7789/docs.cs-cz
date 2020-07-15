---
title: Nainstalovat .NET Core v systému Windows
description: Seznamte se s verzemi Windows, na kterých můžete nainstalovat .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 06/22/2020
ms.openlocfilehash: 97f67d00b3eb4dafc55256aea51f4295bb0ef06a
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308946"
---
# <a name="install-net-core-on-windows"></a>Nainstalovat .NET Core v systému Windows

> [!div class="op_single_selector"]
>
> - [Instalace v systému Windows](windows.md)
> - [Instalace v systému macOS](macos.md)
> - [Instalace v systému Linux](linux.md)

V tomto článku se dozvíte, jak nainstalovat .NET Core v systému Windows. .NET Core se skládá z modulu runtime a sady SDK. Modul runtime se používá ke spuštění aplikace .NET Core a může nebo nemusí být součástí aplikace. Sada SDK se používá k vytváření aplikací a knihoven .NET Core. Modul runtime .NET Core je vždy nainstalován společně se sadou SDK.

Nejnovější verze .NET Core je 3,1.

> [!div class="button"]
> [Stáhnout .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>Podporované verze

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze Windows, na kterých jsou podporované. Tato verze zůstane podporovaná, dokud žádná verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [Windows dosáhne konce životnosti](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

Verze Windows 10 pro data ukončení služby jsou rozdělené podle edice. V následující tabulce jsou zváženy pouze edice **Home**, **pro**, **pro vzdělávání**a **sady pro for for Workstation** . Konkrétní podrobnosti najdete v [tabulce faktů pro životní cyklus systému Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) .

- ✔️ označuje, že verze Windows nebo .NET Core je stále podporovaná.
- ❌Indikuje, že verze Windows nebo .NET Core není v této verzi Windows podporována.
- Pokud se ✔️á verze Windows i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| Operační systém                      | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview |
|-----------------------------|---------------|---------------|----------------|
| ✔️ Windows 10 verze 2004 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ Windows 10 verze 1909 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ Windows 10 verze 1903 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ Windows 10 verze 1809 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌Windows 10 verze 1803 | ✔️ 2,1        | ❌3,1        | ❌5,0 Preview |
| ❌Windows 10 verze 1709 | ❌2,1        | ❌3,1        | ❌5,0 Preview |
| ❌Windows 10 verze 1703 | ❌2,1        | ❌3,1        | ❌5,0 Preview |
| ❌Windows 10 verze 1607 | ❌2,1        | ❌3,1        | ❌5,0 Preview |
| ❌Windows 10 verze 1511 | ❌2,1        | ❌3,1        | ❌5,0 Preview |
| ❌Windows 10 verze 1507 | ❌2,1        | ❌3,1        | ❌5,0 Preview |

## <a name="unsupported-releases"></a>Nepodporované verze

Následující verze rozhraní .NET Core již nejsou ❌ podporovány. Soubory ke stažení pro tyto soubory zůstanou publikované:

- 3.0
- 2,2
- 2.0

## <a name="runtime-information"></a>Běhové informace

Modul runtime se používá ke spouštění aplikací vytvořených pomocí .NET Core. Když autor aplikace publikuje aplikaci, může do své aplikace zahrnout modul runtime. Pokud neobsahují modul runtime, je uživatel k instalaci modulu runtime.

V systému Windows můžete nainstalovat tři různé moduly runtime:

*Modul runtime ASP.NET Core*\
Spustí aplikace ASP.NET Core. Zahrnuje modul runtime .NET Core.

*Běhové prostředí plochy*\
Spustí aplikace .NET Core WPF a .NET Core model Windows Forms desktopové aplikace pro Windows. Zahrnuje modul runtime .NET Core.

*Modul runtime .NET Core*\
Tento modul runtime je nejjednodušším modulem runtime a neobsahuje žádné další moduly runtime. Pro zajištění nejlepší kompatibility s aplikacemi .NET Core doporučujeme nainstalovat modul runtime *ASP.NET Core* a *modul runtime pro stolní počítače* .

> [!div class="button"]
> [Stáhnout .NET Core Runtime](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>Informace o sadě SDK

Sada SDK se používá k sestavování a publikování aplikací a knihoven .NET Core. Instalace sady SDK zahrnuje všechny tři [moduly runtime](#runtime-information): ASP.NET Core, Desktop a .NET Core.

> [!div class="button"]
> [Stáhnout .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a>Závislosti

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3,1](#tab/netcore31)

Rozhraní .NET Core 3,1 podporuje následující verze systému Windows:

> [!NOTE]
> `+`Symbol představuje minimální verzi.

| Operační systém                            | Verze                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient Windows                | 8.1                            | x64, x86        |
| Klient Windows 10             | Verze 1609 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Verze 1803 +                  | x64, ARM32      |

Další informace o podporovaných operačních systémech .NET Core 3,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*.NET Core 3,0 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Rozhraní .NET Core 3,0 podporuje následující verze systému Windows:

> [!NOTE]
> `+`Symbol představuje minimální verzi.

| Operační systém                            | Verze                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Klient Windows 10             | Verze 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Verze 1803 +                  | x64, ARM32      |

Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2,2](#tab/netcore22)

*.NET Core 2,2 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Rozhraní .NET Core 2,2 podporuje následující verze systému Windows:

> [!NOTE]
> `+`Symbol představuje minimální verzi.

| Operační systém                            | Verze                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Klient Windows 10             | Verze 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Server                   | Verze 1803 +                   | x64, ARM32      |

Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

Rozhraní .NET Core 2,1 podporuje následující verze systému Windows:

> [!NOTE]
> `+`Symbol představuje minimální verzi.

| Operační systém                            | Verze                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Klient Windows 10             | Verze 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Server                   | Verze 1803 +                  | platformě            |

Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a>Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2

Pokud instalujete sadu .NET SDK nebo modul runtime v následujících verzích systému Windows, jsou vyžadovány další závislosti:

- ❌Windows 7 SP1
- ❌Windows Vista SP 2
- ✔️ Windows 8.1
- ✔️ Windows Server 2008 R2
- ✔️ Windows Server 2012 R2

Nainstalujte následující:

- [Microsoft Visual C++ 2015 Distribuovatelný Update 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Výše uvedené požadavky se vyžadují také v případě, že dojde k jedné z následujících chyb:

> Program nelze spustit, protože ve vašem počítači chybí *api-ms-win-crt-runtime-l1-1-0.dll* . Zkuste tento problém vyřešit tak, že znovu nainstalujete program.
>
> \-ani
>
> Program nelze spustit, protože ve vašem počítači chybí *api-ms-win-cor-timezone-l1-1-0.dll* . Zkuste tento problém vyřešit tak, že znovu nainstalujete program.
>
> \-ani
>
> *hostfxr.dll* knihovny bylo nalezeno, ale bylo načteno z *C: \\ \<path_to_app> \\hostfxr.dll* se nezdařilo.

## <a name="install-with-powershell-automation"></a>Instalace pomocí automatizace PowerShellu

[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci ci a nesprávce modulu runtime. Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1. Konkrétní vydání můžete zvolit zadáním `Channel` přepínače. Zahrňte `Runtime` přepínač pro instalaci modulu runtime. V opačném případě skript nainstaluje [sadu SDK](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

Nainstalujte sadu SDK tak, že tento přepínač vynecháte `-Runtime` . `-Channel`V tomto příkladu je nastaven přepínač na `Current` , který nainstaluje nejnovější podporovanou verzi.

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a>Instalace se sadou Visual Studio

Pokud používáte Visual Studio pro vývoj aplikací .NET Core, v následující tabulce je popsána minimální požadovaná verze sady Visual Studio na základě cílové verze .NET Core SDK.

| Verze .NET Core SDK | Verze sady Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 verze 16,4 nebo vyšší. |
| 3.0                   | Visual Studio 2019 verze 16,3 nebo vyšší. |
| 2,2                   | Visual Studio 2017 verze 15,9 nebo vyšší. |
| 2.1                   | Visual Studio 2017 verze 15,7 nebo vyšší. |

Pokud již máte nainstalováno Visual Studio, můžete si ověřit verzi pomocí následujících kroků.

01. Otevřete sadu Visual Studio.
01. Vyberte **nápovědu**  >  **o Microsoft Visual Studio**.
01. Přečtěte si číslo verze v dialogovém okně **o produktu** .

Visual Studio může nainstalovat nejnovější .NET Core SDK a modul runtime.

> [!div class="button"]
> [Stáhněte si Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Vyberte úlohu.

Při instalaci nebo úpravách sady Visual Studio vyberte jednu nebo více následujících úloh v závislosti na typu aplikace, kterou vytváříte:

- Úloha **vývoje .NET Core pro více platforem** v části **Další sady nástrojů** .
- Úlohy **vývoje ASP.NET a webu** v části **Web & Cloud** .
- Úlohy **vývoje Azure** v části **Web & cloudu** .
- Úloha **vývoj desktopových aplikací .NET** v části **Desktop & Mobile** .

[![Windows Visual Studio 2019 s úlohou .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>Nainstalovat společně Visual Studio Code

Visual Studio Code je výkonný a prostý Editor zdrojového kódu, který běží na vašem počítači. Visual Studio Code je k dispozici pro Windows, macOS a Linux.

I když Visual Studio Code nepřichází s automatizovaným instalačním programem .NET Core, jako je Visual Studio, přidání podpory .NET Core je jednoduché.

01. [Stáhněte a nainstalujte Visual Studio Code](https://code.visualstudio.com/Download).
01. [Stáhněte a nainstalujte .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).
01. [Nainstalujte rozšíření C# z webu Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

## <a name="download-and-manually-install"></a>Stažení a ruční instalace

Jako alternativu k instalačním programům Windows pro .NET Core si můžete stáhnout a ručně nainstalovat sadu SDK nebo modul runtime. Ruční instalace se obvykle provádí jako součást testování průběžné integrace. Pro vývojáře nebo uživatele je obecně lepší použít [instalační program](https://dotnet.microsoft.com/download/dotnet-core).

.NET Core SDK i modul runtime .NET Core lze po stažení ručně nainstalovat. Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime. Nejprve Stáhněte binární verzi pro sadu SDK nebo modul runtime z jednoho z následujících lokalit:

- [soubory ke stažení ✔️ .net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)
- [soubory ke stažení ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [soubory ke stažení ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Všechny soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

Vytvořte adresář pro extrakci rozhraní .NET, například `%USERPROFILE%\dotnet` . Pak Extrahujte stažený soubor zip do tohoto adresáře.

Ve výchozím nastavení nepoužívají .NET Core CLI příkazy a aplikace tímto způsobem nainstalované rozhraní .NET Core a musíte ho explicitně použít. Provedete to tak, že změníte proměnné prostředí, se kterými je aplikace spuštěná:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

Tento přístup umožňuje nainstalovat více verzí do samostatných umístění a pak explicitně zvolit umístění instalace, které by měla aplikace používat, a to spuštěním aplikace s proměnnými prostředí, které ukazují na toto umístění.

Když `DOTNET_MULTILEVEL_LOOKUP` je nastavená na `0` , rozhraní .NET Core ignoruje všechny globálně nainstalované verze .NET Core. Odeberte toto nastavení prostředí, aby rozhraní .NET Core při výběru nejlepšího rozhraní pro spuštění aplikace bralo v úvahu výchozí globální umístění instalace. Výchozí hodnota je obvykle `C:\Program Files\dotnet` , což znamená, že instalační programy instalují .NET Core.

## <a name="docker"></a>Docker

Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému. Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.

.NET Core může běžet v kontejneru Docker. Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.

Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře. Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.

Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Další kroky

- [Jak zjistit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md?pivots=os-windows).
- [Kurz: kurz Hello World](../tutorials/with-visual-studio.md).
- [Kurz: vytvoření nové aplikace pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md).
- [Kurz: kontejnerizace aplikace .NET Core](../docker/build-container.md)
