---
title: Předpoklady pro .NET Core v systému Linux
description: Podporované verze systému Linux a závislosti rozhraní .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na počítačích se systémem Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 5fcf931572f3c7e9b9857d2e91e9d620c7aad0bd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969871"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Předpoklady pro .NET Core v systému Linux

Tento článek ukazuje závislosti potřebné pro vývoj aplikací .NET Core v systému Linux. Podporované distribuce a verze systému Linux a závislosti, které následují, se vztahují na dva způsoby vývoje aplikací .NET Core v systému Linux:

* [Příkazový řádek s oblíbeným editorem](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Pro produkční servery a prostředí se .NET Core SDK balíček nevyžaduje. Pro aplikace nasazené do produkčního prostředí je potřeba jenom balíček runtime .NET Core. Modul runtime .NET Core je nasazen s aplikacemi jako součást samostatného nasazení, ale musí být nasazen pro samostatně nasazené aplikace závislé na rozhraní. Další informace o typech nasazení závislých na rozhraní a samostatně obsažených typů naleznete v tématu [nasazení aplikace .NET Core](./deploying/index.md). Konkrétní pokyny najdete také v části [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) .

## <a name="supported-linux-versions"></a>Podporované verze systému Linux

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core 2. x považuje Linux za jeden operační systém. Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu). 

Odkazy ke stažení a další informace najdete v tématu soubory ke stažení pro [.NET core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) nebo soubory ke stažení pro [.NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

Rozhraní .NET Core 2. x je podporováno v následujících distribucích a verzích systému Linux:

* Red Hat Enterprise Linux 7, 6-64 – bit (`x86_64` nebo `amd64`)
* CentOS 7-64-bit (`x86_64` nebo `amd64`) 
* Oracle Linux 7-64-bit (`x86_64` nebo `amd64`) 
* Fedora 28, 27-64 – bit (`x86_64` nebo `amd64`) 
* Debian 9 (64-bit, `arm32`), 8,7 nebo novější verze-64-bit (`x86_64` nebo `amd64`)
* Ubuntu 18,04 (64-bit, `arm32`), 16,04, 14,04-64-bit (`x86_64` nebo `amd64`)
* Linux mentolová 18, 17-64 – bit (`x86_64` nebo `amd64`)
* openSUSE 42,3 nebo novější verze – 64-bit (`x86_64` nebo `amd64`)
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 nebo novější-64-bit (`x86_64` nebo `amd64`)
* Alpine Linux 3,7 nebo novější verze – 64-bit (`x86_64` nebo `amd64`)

Úplný seznam operačních systémů .NET Core 2,1 2,2 a .NET Core 2,2 s podporovanými operačními systémy, distribuce a verze, nepodporované verze operačního systému a zásady životního cyklu najdete v článku podporované verze operačního systému .NET [core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) a .net Core [](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) . odkazy.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Odkazy ke stažení a další informace najdete v tématu soubory ke stažení pro [.NET core 1,1](https://dotnet.microsoft.com/download/dotnet-core/1.1) nebo soubory ke stažení pro [.NET Core 1,0](https://dotnet.microsoft.com/download/dotnet-core/1.0).

Rozhraní .NET Core 1. x je podporováno v následujících distribucích a verzích systému`x86_64` Linux `amd64`64-bit:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1,1), 27
* Debian 8,2 nebo novější verze
* Ubuntu 18,04 (.NET Core 1,1), 16,04, 14,04
* Linux Mint 17
* openSUSE 42,3 nebo novější verze (.NET Core 1,1)

Úplný seznam podporovaných operačních systémů pro .NET Core 1. x najdete v článku podporované verze operačního systému s podporou rozhraní .NET [Core](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) 1. x, verze operačních systémů a odkazy na zásady životního cyklu.

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET Core 3,0 Preview 1](#tab/netcore30)

.NET Core 3,0 Preview 1 považuje Linux za jeden operační systém. Pro podporovaná distribuce systému Linux existuje jedno sestavení pro Linux (na architekturu čipu). 

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Verze .NET Core 3,0 Preview 1 je podporována v následujících distribucích a verzích systému Linux. 

OS                            | Version               | Architektury  
------------------------------|-----------------------|----------------
Red Hat Enterprise Linux      | 6                     | x64
Red Hat Enterprise Linux<br>CentOS<br>Oracle Linux  | 7                     | x64
Fedora                        | 28                    | x64
Debian                        | 9                     | x64, ARM32\*, ARM64\*
Ubuntu                        | 16.04+, 18.04+        | x64, ARM32\*, ARM64\*
Linux mentolová                    | 18                    | x64
openSUSE                      | 42.3 +                 | x64
SUSE Enterprise Linux (SLES)  | 12 SP2+               | x64
Alpine Linux                  | 3.8 +                  | x64, ARM64

\*Podpora ARM32 a ARM64 začíná na Debian 9 a Ubuntu 16,04. V čipy ARM nejsou starší verze těchto distribuce podporovány.

Úplný 3,0 seznam podporovaných operačních systémů, distribucí a verzí operačního systému a odkazů na zásady životního cyklu najdete v tématu podporované verze operačního systému .NET [core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .

Další informace o tom, jak nainstalovat .NET Core 3,0 na ARM64, najdete v tématu [instalace .NET core 3,0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

---

## <a name="linux-distribution-dependencies"></a>Závislosti distribuce systému Linux

Níže jsou uvedené příklady. Přesné verze a názvy se mohou mírně lišit podle vaší možnosti rozšíření pro Linux.

### <a name="ubuntu"></a>Ubuntu

Ubuntu distribuce vyžadují následující nainstalované knihovny:

* liblttng-ust0
* libcurl3 (pro 14. x a 16. x)
* libcurl4 (pro 18. x)
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (pro 14. x)
* libicu55 (pro 16. x)
* libicu57 (pro 17. x)
* libicu60 (pro 18. x)

Pro verze starší než .NET Core 2,1 jsou vyžadovány i následující závislosti:

* libunwind8
* libuuid1

### <a name="centos-and-fedora"></a>CentOS a Fedora

CentOS distribuce vyžadují následující nainstalované knihovny:

* lttng – tým UST
* libcurl
* OpenSSL – knihovny
* krb5-libs
* libicu
* ZLIB

Fedora uživatelé: Pokud vaše verze OpenSSL > = 1,1, budete muset nainstalovat openssl10.

Pro verze starší než .NET Core 2,1 jsou vyžadovány i následující závislosti:

* libunwind
* libuuid

Další informace o závislostech najdete v tématu [samostatné aplikace pro Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalace závislostí .NET Core s nativními instalačními programy

Nativní instalační programy .NET Core jsou k dispozici pro podporované distribuce a verze systému Linux. Nativní instalační programy vyžadují přístup správce (sudo) k serveru. Výhodou použití nativního instalačního programu je, že jsou nainstalované všechny nativní závislosti .NET Core. Nativní instalační programy také instalují .NET Core SDK systém.

V systému Linux jsou k dispozici dvě možnosti balíčku instalačního programu:

* Pomocí Správce balíčků na základě informačního kanálu, jako je apt-get pro Ubuntu, nebo Yumu pro CentOS/RHEL.
* Použití samotných balíčků, DEB nebo ot./min.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Skripty se instalují pomocí skriptu Instalační služby .NET Core.

[Příkaz dotnet – instalace skriptů](./tools/dotnet-install-script.md) slouží k provedení instalace rozhraní příkazového řádku CLI sada nástrojů a sdíleného modulu runtime bez správy. Skript si můžete stáhnout z <https://dot.net/v1/dotnet-install.sh>.

Skript ve výchozím nastavení instaluje nejnovější verzi "LTS", která je aktuálně .NET Core 1,1. Pokud chcete nainstalovat .NET Core 2,1, spusťte skript s následujícím přepínačem:

```console
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
