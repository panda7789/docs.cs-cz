---
title: Předpoklady pro .NET Core v systému Linux
description: Podporované verze systému Linux a závislosti rozhraní .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na počítačích se systémem Linux.
author: leecow
ms.author: leecow
ms.date: 10/11/2019
ms.openlocfilehash: bb9049059de9d8208fc92234b28acdfb3d7f0cb3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318329"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Předpoklady pro .NET Core v systému Linux

Tento článek ukazuje závislosti potřebné pro vývoj aplikací .NET Core v systému Linux. Podporované distribuce a verze systému Linux a závislosti, které následují, se vztahují na dva způsoby vývoje aplikací .NET Core v systému Linux:

* [Příkazový řádek s oblíbeným editorem](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Pro produkční servery a prostředí se .NET Core SDK balíček nevyžaduje. Pro aplikace nasazené do produkčního prostředí je potřeba jenom balíček runtime .NET Core. Modul runtime .NET Core je nasazen s aplikacemi jako součást samostatného nasazení, ale musí být nasazen pro samostatně nasazené aplikace závislé na rozhraní. Další informace o typech nasazení závislých na rozhraní a samostatně obsažených typů naleznete v tématu [nasazení aplikace .NET Core](./deploying/index.md). Konkrétní pokyny najdete také v části [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) .

## <a name="supported-linux-versions"></a>Podporované verze systému Linux

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3,0 považuje Linux za jeden operační systém. Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu). 

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

.NET Core 3,0 se podporuje na následujících distribucích a verzích systému Linux:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| JINÉHO                             | Version               | Architektury    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6 +, 7                 | x64 |
| Oracle Linux                   | čl                     | x64 |
| CentOS                         | čl                     | x64 |
| Fedora                         | 29 +                   | x64 |
| Debian                         | 9 +                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 +                | x64, ARM32, ARM64 |
| Linux mentolová                     | 18 +                   | x64 |
| openSUSE                       | 15 +                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2 +               | x64 |
| Alpine Linux                   | 3.8 +                  | x64, ARM64 |

Úplný 3,0 seznam podporovaných operačních systémů, distribucí a verzí operačního systému a odkazů na zásady životního cyklu najdete v tématu podporované verze operačního systému .NET [core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .

Další informace o tom, jak nainstalovat .NET Core 3,0 na ARM64, najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

.NET Core 2,2 považuje Linux za jeden operační systém. Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení pro .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2).

.NET Core 2,2 se podporuje v následujících distribucích a verzích systému Linux:

> [!NOTE]
> Symbol `+` představuje minimální verzi.

| JINÉHO                             |  Version                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| Oracle Linux                   |  čl                      | x64 |
| CentOS                         |  čl                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 18,10    | x64, ARM32 |
| Linux mentolová                     |  17, 18                 | x64 |
| openSUSE                       |  15 +                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2 +                | x64 |
| Alpine Linux                   |  3.7 +                   | x64 |

Úplný 2,2 seznam podporovaných operačních systémů, distribucí a verzí operačního systému a odkazů na zásady životního cyklu najdete v tématu podporované verze operačního systému .NET [core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) .

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

.NET Core 2,1 považuje Linux za jeden operační systém. Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu).

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení pro .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

.NET Core 2,1 se podporuje v následujících distribucích a verzích systému Linux:

| JINÉHO                             |  Version                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| Oracle Linux                   |  čl                      | x64 |
| CentOS                         |  čl                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 19,04    | x64, ARM32 |
| Linux mentolová                     |  17, 18                 | x64 |
| openSUSE                       |  42.3 +                  | x64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2 +                | x64 |
| Alpine Linux                   |  3.7 +                   | x64 |

Úplný 2,1 seznam podporovaných operačních systémů, distribucí a verzí operačního systému a odkazů na zásady životního cyklu najdete v tématu podporované verze operačního systému .NET [core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) .

---

## <a name="linux-distribution-dependencies"></a>Závislosti distribuce systému Linux

Níže jsou uvedené příklady. Přesné verze a názvy se mohou mírně lišit podle vaší možnosti rozšíření pro Linux.

### <a name="ubuntu"></a>Ubuntu

Ubuntu distribuce vyžadují následující nainstalované knihovny:

* liblttng-ust0
* libcurl3 (pro 14. x a 16. x)
* libcurl4 (pro 18. x)
* libssl 1.0.0
* libkrb5-3
* zlib1g
* libicu52 (pro 14. x)
* libicu55 (pro 16. x)
* libicu57 (pro 17. x)
* libicu60 (pro 18. x)

Pro verze starší než .NET Core 2,1 jsou vyžadovány i následující závislosti:

* libunwind8
* libuuid1

Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , potřebujete také následující závislost:

* libgdiplus (verze 6.0.1 nebo novější)

> [!NOTE]
> Většina verzí Ubuntu zahrnuje starší verzi libgdiplus. Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému. Další informace najdete v tématu <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS a Fedora

CentOS distribuce vyžadují následující nainstalované knihovny:

* lttng – tým UST
* libcurl
* OpenSSL – knihovny
* krb5 – knihovny
* libicu
* ZLIB

Fedora uživatelé: Pokud verze vašeho opensslu je > = 1,1, budete muset nainstalovat kompatibilní s openssl10.

Pro verze starší než .NET Core 2,1 jsou vyžadovány i následující závislosti:

* libunwind
* libuuid

Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

Pro aplikace .NET Core, které používají sestavení *System. Drawing. Common* , budete také potřebovat následující závislost:

* libgdiplus (verze 6.0.1 nebo novější)

> [!NOTE]
> Většina verzí CentOS a Fedora zahrnuje starší verzi libgdiplus. Můžete nainstalovat nejnovější verzi libgdiplus přidáním úložiště mono do systému. Další informace najdete v tématu <https://www.mono-project.com/download/stable/>.

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalace závislostí .NET Core s nativními instalačními programy

Nativní instalační programy .NET Core jsou k dispozici pro podporované distribuce a verze systému Linux. Nativní instalační programy vyžadují přístup správce (sudo) k serveru. Výhodou použití nativního instalačního programu je, že jsou nainstalované všechny nativní závislosti .NET Core. Nativní instalační programy také instalují .NET Core SDK systém.

V systému Linux jsou k dispozici dvě možnosti balíčku instalačního programu:

* Pomocí Správce balíčků na základě informačního kanálu, jako je apt-get pro Ubuntu, nebo Yumu pro CentOS/RHEL.
* Použití samotných balíčků, DEB nebo ot./min.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Skripty se instalují pomocí skriptu Instalační služby .NET Core.

[Příkaz dotnet – instalace skriptů](./tools/dotnet-install-script.md) slouží k provedení instalace rozhraní příkazového řádku CLI sada nástrojů a sdíleného modulu runtime bez správy. Skript si můžete stáhnout z <https://dot.net/v1/dotnet-install.sh>.

Skript ve výchozím nastavení instaluje nejnovější verzi "LTS", která je aktuálně .NET Core 1,1. Pokud chcete nainstalovat .NET Core 2,1, spusťte skript s následujícím přepínačem:

```bash
./dotnet-install.sh -c Current
```

Skript bash instalačního programu se používá ve scénářích automatizace a v instalacích bez správy. Tento skript také přečte přepínače prostředí PowerShell, takže je možné ho použít se skriptem v systémech Linux/OS X.

## <a name="troubleshoot"></a>Řešení potíží

Pokud máte problémy s instalací .NET Core v podporované distribuci/verzi systému Linux, přečtěte si následující témata o nainstalovaných distribucích a verzích:

* [Známé problémy s .NET Core 3,0](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [Známé problémy s .NET Core 2,2](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [Známé problémy s .NET Core 2,1](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [Známé problémy s .NET Core 1,1](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [Známé problémy s .NET Core 1,0](https://github.com/dotnet/core/blob/master/release-notes/1.0)
