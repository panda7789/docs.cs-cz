---
title: Závislosti .NET Core SDK a modulu runtime – .NET Core
description: Podrobně popisuje operační systém a požadavky na architekturu procesoru pro instalaci .NET Core SDK a modulu runtime v systémech Windows, Linux a macOS.
author: leecow
ms.author: leecow
ms.date: 06/01/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 81f6ab436428d71f71d9fd0f560bd2b0512a519b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590757"
---
# <a name="net-core-dependencies-and-requirements"></a>Závislosti a požadavky .NET Core

Tento článek podrobně popisuje, které operační systémy a architektura procesoru jsou podporovány rozhraním .NET Core.

## <a name="supported-operating-systems"></a>Podporované operační systémy

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3,1](#tab/netcore31)

Rozhraní .NET Core 3,1 podporuje následující verze systému Windows:

> [!NOTE]
> `+`Symbol představuje minimální verzi.

| Operační systém                            | Verze                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient Windows                | 7 SP1 +, 8,1                    | x64, x86        |
| Klient Windows 10             | Verze 1607 +                  | x64, x86        |
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

- Windows 7 SP1
- Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Nainstalujte následující:

- [Microsoft Visual C++ 2015 Distribuovatelný Update 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Výše uvedené požadavky se vyžadují také v případě, že dojde k jedné z následujících chyb:

> Program nelze spustit, protože v počítači chybí *rozhraní API-MS-Win-CRT-runtime-L1-1 -0. dll* . Zkuste tento problém vyřešit tak, že znovu nainstalujete program.
>
> \-ani
>
> Program nelze spustit, protože v počítači chybí *rozhraní API-MS-Win-cor-TimeZone-L1-1 -0. dll* . Zkuste tento problém vyřešit tak, že znovu nainstalujete program.
>
> \-ani
>
> Knihovna *hostfxr. dll* byla nalezena, ale načtení z *jazyka C: \\ \<path_to_app> \\ hostfxr. dll* se nezdařilo.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET Core 3,1](#tab/netcore31)

.NET Core 3,1 považuje Linux za jeden operační systém. Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).

.NET Core 3,1 se podporuje v následujících distribucích a verzích systému Linux:

> [!NOTE]
> `+`Symbol představuje minimální verzi.

| Operační systém                             | Verze               | Architektury    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7 +                    | x64 |
| Oracle Linux                   | 7 +                    | x64 |
| Fedora                         | 30 +                   | x64 |
| Debian                         | 9 +                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 +                | x64, ARM32, ARM64 |
| Linux mentolová                     | 18 +                   | x64 |
| openSUSE                       | 15 +                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2 +               | x64 |
| Alpine Linux                   | 3.10 +                 | x64, ARM64 |

Další informace o podporovaných operačních systémech .NET Core 3,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

Další informace o tom, jak nainstalovat .NET Core 3,1 na ARM64 (kernel 4.14 +), najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

> [!IMPORTANT]
> Podpora ARM64 vyžaduje Linux kernel 4,14 nebo vyšší. Některé distribuce systému Linux tento požadavek splňují, i když jiné ne. Například Ubuntu 18,04 je podporován, ale Ubuntu 16,04 ne.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*.NET Core 3,0 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

.NET Core 3,0 považuje Linux za jeden operační systém. Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).

.NET Core 3,0 se podporuje v následujících distribucích a verzích systému Linux:

> [!NOTE]
> `+`Symbol představuje minimální verzi.

| Operační systém                             | Verze               | Architektury    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7 +                    | x64 |
| Oracle Linux                   | 7 +                    | x64 |
| Fedora                         | 29 +                   | x64 |
| Debian                         | 9 +                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 +                | x64, ARM32, ARM64 |
| Linux mentolová                     | 18 +                   | x64 |
| openSUSE                       | 15 +                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2 +               | x64 |
| Alpine Linux                   | 3.8 +                  | x64, ARM64 |

Další informace o podporovaných operačních systémech .NET Core 3,0, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

Další informace o tom, jak nainstalovat .NET Core 3,0 na ARM64, najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22"></a>[.NET Core 2,2](#tab/netcore22)

*.NET Core 2,2 je aktuálně mimo podporu. Další informace najdete v tématu [zásady podpory pro .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

.NET Core 2,2 považuje Linux za jeden operační systém. Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).

.NET Core 2,2 se podporuje v následujících distribucích a verzích systému Linux:

> [!NOTE]
> `+`Symbol představuje minimální verzi.

| Operační systém                             |  Verze                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 18,10    | x64, ARM32 |
| Linux mentolová                     |  17, 18                 | x64 |
| openSUSE                       |  15 +                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2 +                | x64 |
| Alpine Linux                   |  3.8 +                   | x64 |

Další informace o podporovaných operačních systémech .NET Core 2,2, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2,1 považuje Linux za jeden operační systém. Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).

.NET Core 2,1 se podporuje v následujících distribucích a verzích systému Linux:

> [!NOTE]
> `+`Symbol představuje minimální verzi.

| Operační systém                             |  Verze                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7 +                     | x64 |
| Oracle Linux                   |  7 +                     | x64 |
| Fedora                         |  30 +                    | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 19,04, 19,10    | x64, ARM32 |
| Linux mentolová                     |  17 +                    | x64 |
| openSUSE                       |  15 +                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2 +                | x64 |
| Alpine Linux                   |  3.8 +                   | x64 |

Další informace o podporovaných operačních systémech .NET Core 2,1, distribucích a zásadách životního cyklu najdete v článku [podporované verze operačních systémů pro .NET core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

## <a name="linux-distribution-dependencies"></a>Závislosti distribuce systému Linux

Na základě distribuce systému Linux bude pravděpodobně nutné nainstalovat další závislosti.

> [!IMPORTANT]
> Přesné verze a názvy se mohou mírně lišit podle vaší možnosti rozšíření pro Linux.

### <a name="ubuntu"></a>Ubuntu

Ubuntu distribuce vyžadují, aby byly nainstalované následující knihovny:

- liblttng-ust0
- libcurl3 (pro 14. x a 16. x)
- libcurl4 (pro 18. x)
- libssl 1.0.0
- libkrb5-3
- zlib1g
- libicu52 (pro 14. x)
- libicu55 (pro 16. x)
- libicu57 (pro 17. x)
- libicu60 (pro 18. x)

Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:

- libgdiplus (verze 6.0.1 nebo novější)

> [!WARNING]
> Většina verzí Ubuntu zahrnuje starší verzi libgdiplus. Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému. Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS a Fedora

CentOS distribuce vyžadují následující nainstalované knihovny:

- lttng – tým UST
- libcurl
- OpenSSL – knihovny
- krb5 – knihovny
- libicu
- ZLIB

Fedora uživatelé: Pokud verze vašeho OpenSSLu je >= 1,1, budete muset nainstalovat **kompatibilní s openssl10**.

Pro .NET Core 2,0 jsou potřeba taky následující závislosti:

- libunwind
- libuuid

Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:

- libgdiplus (verze 6.0.1 nebo novější)

> [!WARNING]
> Většina verzí CentOS a Fedora zahrnuje starší verzi libgdiplus. Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému. Další informace naleznete v tématu <https://www.mono-project.com/download/stable/>.

### <a name="alpine"></a>Alpine

Alpské distribuce vyžadují instalaci následujících knihoven:

- ICU-knihovny (není nutné v případě, že je globalizace zakázána)
- krb5 – knihovny
- libcurl
- libintl
- libssl 1.1 (pro Alpine 3,9 nebo novější) nebo libssl 1.0 (pro starší verze)
- libstdc + +
- lttng – tým UST
- numactl (volitelné, užitečné jenom pro zařízení s podporou NUMA)
- ZLIB

Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:

- libgdiplus (je k dispozici pouze v úložišti Edge/testování)

::: zone-end

::: zone pivot="os-macos"

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

::: zone-end

## <a name="next-steps"></a>Další kroky

- Pro vývoj a spouštění aplikací nainstalujte [.NET Core SDK](sdk.md) (zahrnuje modul runtime).
- Pokud chcete spouštět aplikace, které vytvořili jiní uživatelé, nainstalujte [modul runtime .NET Core](runtime.md).
