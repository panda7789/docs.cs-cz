---
title: Požadavky pro .NET Core v Linuxu
description: Podporované verze systému Linux a závislosti .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na počítačích s Linuxem.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 5ef1737185ad41de7bd5e7a9b8db048ff577811f
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083883"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Požadavky pro .NET Core v Linuxu

Tento článek popisuje závislosti, které potřebujete pro vývoj aplikací .NET Core v Linuxu. Podporované distribuce systému Linux/verze a závislosti, které následují platí na dva způsoby, jak vyvíjet aplikace .NET Core v Linuxu:

* [Pomocí oblíbeného editoru příkazového řádku](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Balíček .NET Core SDK není potřeba pro produkční servery pro/prostředí. Pro aplikace nasazené do produkčního prostředí se vyžaduje jenom balíček modulu runtime .NET Core. Modul runtime .NET Core je nasazený s aplikacemi jako součást samostatná nasazení, ale se musí nasadit pro závisí na architektuře nasazené aplikace samostatně. Další informace o typech nasazení závisí na architektuře a samostatná najdete v tématu [nasazení aplikace .NET Core](./deploying/index.md). Viz také [Self-contained Linuxové aplikace](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) konkrétní pokyny.

## <a name="supported-linux-versions"></a>Podporované verze Linuxu

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET core 2.x považuje Linux jako jeden operační systém. Existuje jedno sestavení Linux (za architektura procesoru) podporované distribuce systému Linux. 

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 2.2](https://www.microsoft.com/net/download/dotnet-core/2.2) nebo [soubory ke stažení rozhraní .NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1).

.NET core 2.x je podporovaný v následujících distribucích systému Linux/verzích:

* Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` nebo `amd64`)
* CentOS 7 - 64-bit (`x86_64` nebo `amd64`) 
* Oracle Linux 7 - 64-bit (`x86_64` nebo `amd64`) 
* Fedora 28, 27 - 64-bit (`x86_64` nebo `amd64`) 
* Debian 9 (64-bit, `arm32`), 8.7 nebo novější verze - 64-bit (`x86_64` nebo `amd64`)
* Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` nebo `amd64`)
* Linux Mint 18, 17 – 64-bit (`x86_64` nebo `amd64`)
* openSUSE 42.3 nebo novější verze - 64-bit (`x86_64` nebo `amd64`)
* SUSE Enterprise Linux (SLES) 12 aktualizace Service Pack 2 nebo novější - 64-bit (`x86_64` nebo `amd64`)
* Nástroj Alpine Linuxu 3.7 nebo novější verze - 64-bit (`x86_64` nebo `amd64`)

Zobrazit [podporované verze operačního systému .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) a [podporované verze operačního systému .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) úplný seznam .NET Core 2.1 a .NET Core 2.2 podporované operační systémy, distribuce a verze, z celkového počtu Podpora verze operačního systému a propojení zásad životního cyklu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) nebo [.NET Core 1.0 stáhne](https://www.microsoft.com/net/download/dotnet-core/1.0).

.NET core 1.x podporuje následující Linux 64-bit (`x86_64` nebo `amd64`) distribuce a verze:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1.1), 27
* Debian 8.2 nebo novější verze
* Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04
* Linux Mint 17
* openSUSE 42.3 nebo novější verze (.NET Core 1.1)

Zobrazit [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, z verze podporu operačního systému a propojení zásad životního cyklu.

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET core 3.0 ve verzi Preview 1](#tab/netcore30)

.NET core 3.0 ve verzi Preview 1 považuje za jeden operační systém Linux. Existuje jedno sestavení Linux (za architektura procesoru) podporované distribuce systému Linux. 

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

.NET core 3.0 ve verzi Preview 1 se podporuje v následujících distribucích systému Linux/verzích. 

Operační systém                            | Version               | Architektury  
------------------------------|-----------------------|----------------
Red Hat Enterprise Linux      | 6                     | x64
Red Hat Enterprise Linux<br>CentOS<br>Oracle Linux  | 7                     | x64
Fedora                        | 28                    | x64
Debian                        | 9                     | x64, ARM32\*, ARM64\*
Ubuntu                        | 16.04+, 18.04+        | x64, ARM32\*, ARM64\*
Linux Mint                    | 18                    | x64
openSUSE                      | 42.3+                 | x64
SUSE Linux Enterprise (SLES)  | 12 SP2+               | x64
Nástroj Alpine Linuxu                  | 3.8+                  | x64, ARM64

\* Podpora ARM32 a ARM64 začíná Debian 9 a Ubuntu 16.04. Starší verze těchto distribuce nejsou podporovány na čipech ARM.

Zobrazit [podporované verze operačního systému .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pro .NET Core 3.0 na úplný seznam podporovaných operačních systémů, distribuce a verze z verze podporu operačního systému a propojení zásad životního cyklu.

Další informace o tom, jak nainstalovat .NET Core 3.0 na ARM64 najdete v tématu [instalace .NET Core 3.0 v systému Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).



---

## <a name="linux-distribution-dependencies"></a>Závislosti distribuce Linuxu

Následující jsou určeny jako příklady. Přesné verze a názvy se mohou mírně lišit na vaší distribuci Linuxu podle výběru.

### <a name="ubuntu"></a>Ubuntu

Ubuntu distribuce vyžaduje nainstalované následující knihovny:

* liblttng-ust0
* libcurl3 (pro 14.x a 16.x)
* libcurl4 (pro 18.x)
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (pro 14.x)
* libicu55 (pro 16.x)
* libicu57 (pro 17.x)
* libicu60 (pro 18.x)

Pro verze starší než .NET Core 2.1 následující závislosti se rovněž vyžadují:

* libunwind8
* libuuid1

### <a name="centos-and-fedora"></a>CentOS i Fedora

CentOS distribuce vyžaduje nainstalované následující knihovny:

* lttng tým ust
* libcurl
* knihovny OpenSSL
* krb5-libs
* libicu
* zlib

Uživatelé, fedora: Pokud vaše openssl verze > = 1.1, budete muset nainstalovat openssl10 kompatibility.

Pro verze starší než .NET Core 2.1 následující závislosti se rovněž vyžadují:

* libunwind
* libuuid

Další informace o závislostech najdete v tématu [Self-contained Linuxové aplikace](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalování závislostí pro .NET Core pomocí nativních instalačních programů

.NET core, které jsou k dispozici pro nativních instalačních programů podporované distribuce systému Linux/verze. Nativních instalačních programů vyžadovat přístup správce (sudo) na server. Výhodou použití nativní instalačního programu je, že jsou nainstalovány všechny závislosti nativní .NET Core. Nativních instalačních programů nainstalovat také systémová sada .NET Core SDK.

V Linuxu existují dvě možnosti balíček instalačního programu:

* Pomocí Správce balíčků založená na informační kanál, třeba apt-get pro Ubuntu nebo yumu pro CentOS/RHEL.
* Použití balíčků, sami, DEB nebo ot. / min.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Skriptování nainstaluje s skript instalačního programu .NET Core

[Dotnet instalačních skriptů](./tools/dotnet-install-script.md) umožňují provést instalaci bez oprávnění správce. Sada nástrojů rozhraní příkazového řádku a sdílený modul runtime. Můžete stáhnout skript z [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).

Výchozí hodnoty skriptu k instalaci nejnovější verze "L", která je aktuálně .NET Core 1.1. Pokud chcete nainstalovat rozhraní .NET Core 2.1, spusťte skript s přepínačem následující:

```console
./dotnet-install.sh -c Current
```

Skript bash instalačního programu se používá v scénáře automatizace a zařízení bez oprávnění správce. Tento skript také přečte přepínače prostředí PowerShell, aby je bylo možné použít pomocí skriptu v systémech Linux nebo OS X.

## <a name="troubleshoot"></a>Řešení potíží

Pokud máte problémy s instalací rozhraní .NET Core na podporované distribuce systému Linux/version, najdete v následujících tématech nainstalovaných distribucí a verzí:

* [Známé problémy s .NET core 3.0](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [Známé problémy s .NET core 2.2](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [Známé problémy s .NET core 2.1](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [Známé problémy s .NET core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [Známé problémy s .NET core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0)
