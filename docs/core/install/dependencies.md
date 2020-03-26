---
title: Základní sada SDK a závislosti za běhu .NET – jádro .NET
description: Podrobnosti o předpokladech architektury operačního systému a procesoru pro instalaci sady .NET Core SDK a runtime ve Windows, Linux u macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 023b8fdf029dd6b17fe2186296d87dd7507c60b5
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546559"
---
# <a name="net-core-dependencies-and-requirements"></a>.NET Základní závislosti a požadavky

Tento článek podrobně popisuje, které operační systémy a architektura procesoru jsou podporovány rozhraním .NET Core.

## <a name="supported-operating-systems"></a>Podporované operační systémy

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Jádro 3.1](#tab/netcore31)

Pomocí rozhraní .NET Core 3.1 jsou podporovány následující verze systému Windows:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| Operační systém                            | Version                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient Windows                | 7 SP1+, 8,1                    | x64, x86        |
| Klient Windows 10             | Verze 1607+                  | x64, x86        |
| Windows Server                | 2012 R2+                       | x64, x86        |
| Nano Server                   | Verze 1803+                  | x64, ARM32      |

Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.1 naleznete v tématu .NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*Rozhraní .NET Core 3.0 je momentálně mimo podporu. Další informace naleznete v [zásadách základní podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Pomocí rozhraní .NET Core 3.0 jsou podporovány následující verze systému Windows:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| Operační systém                            | Version                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient Windows                | 7 SP1+, 8,1                    | x64, x86        |
| Klient Windows 10             | Verze 1607+                  | x64, x86        |
| Windows Server                | 2012 R2+                       | x64, x86        |
| Nano Server                   | Verze 1803+                  | x64, ARM32      |

Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.0 naleznete v tématu .NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*Rozhraní .NET Core 2.2 je momentálně mimo podporu. Další informace naleznete v [zásadách základní podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Pomocí rozhraní .NET Core 2.2 jsou podporovány následující verze systému Windows:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| Operační systém                            | Version                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient Windows                | 7 SP1+, 8,1                    | x64, x86        |
| Klient Windows 10             | Verze 1607+                  | x64, x86        |
| Windows Server                | 2008 R2 SP1+                   | x64, x86        |
| Nano Server                   | Verze 1803+                   | x64, ARM32      |

Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.2 naleznete v tématu .NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

Následující verze systému Windows jsou podporovány pomocí rozhraní .NET Core 2.1:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| Operační systém                            | Version                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient Windows                | 7 SP1+, 8,1                    | x64, x86        |
| Klient Windows 10             | Verze 1607+                  | x64, x86        |
| Windows Server                | 2008 R2 SP1+                   | x64, x86        |
| Nano Server                   | Verze 1803+                  | x64,            |

Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.1 naleznete v tématu .NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>Windows 7 / Vista / 8.1 / Server 2008 R2

Další závislosti jsou vyžadovány, pokud instalujete sdsad .NET nebo runtime v následujících verzích systému Windows:

- Windows 7 SP1
- Systém Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Nainstalujte následující:

- [Redistribuovatelná aktualizace 3 aplikace Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Výše uvedené požadavky jsou také vyžadovány, pokud narazíte na jednu z následujících chyb:

> Program nelze spustit, protože *api-ms-win-crt-runtime-l1-1-0.dll* chybí v počítači. Zkuste tento problém vyřešit přeinstalací programu.
>
> \-nebo -
>
> Knihovna *hostfxr.dll* byla nalezena, ale načítání z *C:\\\<path_to_app>\\hostfxr.dll* se nezdařilo.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET Jádro 3.1](#tab/netcore31)

.NET Core 3.1 zachází s Linuxem jako s jediným operačním systémem. Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.

.NET Core 3.1 je podporován na následujících linuxových distribucích/verzích:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| Operační systém                             | Version               | Architektury    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 30+                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux mincovna                     | 18+                   | x64 |
| openSUSE                       | 15+                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpský Linux                   | 3.10+                 | x64, ARM64 |

Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.1 naleznete v tématu .NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

Další informace o instalaci rozhraní .NET Core 3.1 na ARM64 (jádro 4.14+) najdete [v tématu Instalace rozhraní .NET Core 3.0 na Linuxarm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

> [!IMPORTANT]
> Podpora ARM64 vyžaduje linuxové jádro 4.14 nebo vyšší. Některé linuxové distribuce splňují tento požadavek, zatímco jiné ne. Například Ubuntu 18.04 je podporováno, ale Ubuntu 16.04 není.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*Rozhraní .NET Core 3.0 je momentálně mimo podporu. Další informace naleznete v [zásadách základní podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

.NET Core 3.0 zachází s Linuxem jako s jediným operačním systémem. Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.

Rozhraní .NET Core 3.0 je podporováno v následujících linuxových distribucích/verzích:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| Operační systém                             | Version               | Architektury    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29+                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux mincovna                     | 18+                   | x64 |
| openSUSE                       | 15+                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2+               | x64 |
| Alpský Linux                   | 3.8+                  | x64, ARM64 |

Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 3.0 naleznete v tématu .NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

Další informace o instalaci rozhraní .NET Core 3.0 na ARM64 naleznete [v tématu Instalace rozhraní .NET Core 3.0 na Linuxarm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*Rozhraní .NET Core 2.2 je momentálně mimo podporu. Další informace naleznete v [zásadách základní podpory rozhraní .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

.NET Core 2.2 zachází s Linuxem jako s jediným operačním systémem. Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.

Rozhraní .NET Core 2.2 je podporováno v následujících linuxových distribucích/verzích:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| Operační systém                             |  Version                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 18.10    | x64, ARM32 |
| Linux mincovna                     |  17, 18                 | x64 |
| openSUSE                       |  15+                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpský Linux                   |  3.8+                   | x64 |

Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.2 naleznete v tématu .NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 zachází s Linuxem jako s jediným operačním systémem. Existuje jeden linuxový build (na architekturu čipů) pro podporované distribuce Linuxu.

.NET Core 2.1 je podporován na následujících linuxových distribucích/verzích:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| Operační systém                             |  Version                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7+                     | x64 |
| Oracle Linux                   |  7+                     | x64 |
| Fedora                         |  30+                    | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 19.04, 19.10    | x64, ARM32 |
| Linux mincovna                     |  17+                    | x64 |
| openSUSE                       |  15+                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2+                | x64 |
| Alpský Linux                   |  3.8+                   | x64 |

Další informace o podporovaných operačních systémech, distribucích a zásadách životního cyklu [rozhraní .NET Core 2.1 naleznete v tématu .NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

## <a name="linux-distribution-dependencies"></a>Závislosti distribuce Linuxu

Na základě distribuce linuxu může být nutné nainstalovat další závislosti.

> [!IMPORTANT]
> Přesné verze a názvy se mohou mírně lišit v distribuci Linuxu.

### <a name="ubuntu"></a>Ubuntu

Distribuce Ubuntu vyžadují instalaci následujících knihoven:

- liblttng-ust0
- libcurl3 (pro 14.x a 16.x)
- libcurl4 (pro 18.x)
- libssl1.0.0
- libkrb5-3
- zlib1g
- libicu52 (pro 14.x)
- libicu55 (pro 16.x)
- libicu57 (pro 17.x)
- libicu60 (pro 18.x)

Pro aplikace .NET Core, které používají sestavení *System.Drawing.Common,* potřebujete také následující závislost:

- libgdiplus (verze 6.0.1 nebo novější)

> [!WARNING]
> Většina verzí Ubuntu obsahuje starší verzi libgdiplus. Můžete nainstalovat nejnovější verzi libgdiplus přidáním mono úložiště do vašeho systému. Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS a Fedora

Distribuce CentOS vyžadují nainstalovány následující knihovny:

- Lttng-ust
- libcurl
- openssl-libs
- krb5-libs
- libicu
- Zlib

Uživatelé Fedory: Pokud verze vašeho OpenSSL >= 1.1, budete muset nainstalovat **compat-openssl10**.

Pro rozhraní .NET Core 2.0 jsou také vyžadovány následující závislosti:

- libunwind
- libuuid

Další informace o závislostech naleznete v [tématu Samostatné linuxové aplikace](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pro aplikace .NET Core, které používají sestavení *System.Drawing.Common,* budete také potřebovat následující závislost:

- libgdiplus (verze 6.0.1 nebo novější)

> [!WARNING]
> Většina verzí CentOS a Fedory obsahuje starší verzi libgdiplus. Můžete nainstalovat nejnovější verzi libgdiplus přidáním mono úložiště do vašeho systému. Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.

::: zone-end

::: zone pivot="os-macos"

Jádro .NET je podporováno v následujících verzích macOS:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| Základní verze rozhraní .NET | macOS                 | Architektury |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | Vysoká Sierra (10.13+)  | x64 | [Více informací](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | Vysoká Sierra (10.13+)  | x64 | [Více informací](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2,2               | Sierra (10.12+)       | x64 | [Více informací](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12+)       | x64 | [Více informací](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

Počínaje macOS Catalina (verze 10.15), veškerý software postavený po červnu 1, 2019, který je distribuován s ID vývojáře, musí být notářsky.Rzavený až k MacS Catalina (verze 10.15), všechen software postavený po 1. Tento požadavek se vztahuje na modul runtime .NET Core, sadku .NET Core SDK a software vytvořený pomocí .NET Core.

Instalační programy pro .NET Core (runtime a SDK) verze 3.1, 3.0 a 2.1 byly notářsky oznamovány od 18. Předchozí vydané verze nejsou notářsky oslněny. Pokud spustíte aplikaci, která není notářsky vedena, zobrazí se chyba podobná následujícímu obrázku:

![macOS Catalina notářská výstraha](media/dependencies/macos-notarized-pkg-warning.png)

Další informace o tom, jak vynucená notářská činnost ovlivňuje .NET Core (a vaše aplikace .NET Core), najdete v [tématu Práce s macOS Catalina Notarization](macos-notarization-issues.md).

## <a name="libgdiplus"></a>libgdiplus řekl:

Základní aplikace .NET, které používají sestavení *System.Drawing.Common,* vyžadují instalaci libgdiplus.

Snadný způsob, jak získat libgdiplus, je pomocí Správce balíčků [Homebrew ("brew")](https://brew.sh/) pro macOS. Po instalaci *vařit*, nainstalujte libgdiplus provedením následujících příkazů na terminálu (příkaz) prompt:

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Další kroky

- Chcete-li vyvíjet a spouštět aplikace, nainstalujte sadu [.NET Core SDK](sdk.md) (včetně runtime).
- Chcete-li spustit aplikace, které vytvořili jiní uživatelé, nainstalujte [za běhu .NET Core](runtime.md).
