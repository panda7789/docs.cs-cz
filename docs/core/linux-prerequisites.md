---
title: Požadavky pro .NET Core v Linuxu
description: Podporované verze systému Linux a závislosti .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na počítačích s Linuxem.
author: jralexander
ms.author: johalex
ms.date: 08/20/2018
ms.openlocfilehash: 4939dfb642c2aef9da593a193f42334f1d57e067
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580731"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Požadavky pro .NET Core v Linuxu

Tento článek popisuje závislosti, které potřebujete pro vývoj aplikací .NET Core v Linuxu. Podporované distribuce systému Linux/verze a závislosti, které následují platí na dva způsoby, jak vyvíjet aplikace .NET Core v Linuxu:

* [Pomocí oblíbeného editoru příkazového řádku](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Balíček .NET Core SDK není potřeba pro produkční servery pro/prostředí. Pro aplikace nasazené do produkčního prostředí se vyžaduje jenom balíček modulu runtime .NET Core. Modul runtime .NET Core je nasazený s aplikacemi jako součást samostatná nasazení, ale se musí nasadit pro závisí na architektuře nasazené aplikace samostatně. Další informace o typech nasazení závisí na architektuře a samostatná najdete v tématu [nasazení aplikace .NET Core](./deploying/index.md). Viz také [Self-contained Linuxové aplikace](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) konkrétní pokyny.

## <a name="supported-linux-versions"></a>Podporované verze Linuxu

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

.NET core 2.x považuje Linux jako jeden operační systém. Existuje jedno sestavení Linux (za architektura procesoru) podporované distribuce systému Linux.

**.NET Core 2.1**

NET Core 2.1 je podporována v následujících distribucích systému Linux/verzích:

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

Zobrazit [podporované verze operačního systému .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) úplný seznam .NET Core 2.1 podporované operační systémy, distribuce a verze z verze podporu operačního systému a propojení zásad životního cyklu.

**.NET Core 2.0**

NET Core 2.0 je podporováno v následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce a verze:

* Red Hat Enterprise Linux 7, 6
* CentOS 7
* Oracle Linux 7
* Fedora 27
* Debian 9 8.7 nebo novější verze
* Ubuntu 18.04, 16.04, 14.04
* Linux Mint 18, 17
* openSUSE 42.3 nebo novější verze
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 nebo novější

Zobrazit [podporované verze operačního systému .NET Core 2.0](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) úplný seznam .NET Core 2.0 podporované operační systémy, distribuce a verze z verze podporu operačního systému a propojení zásad životního cyklu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

.NET core 1.x podporuje následující Linux 64-bit (`x86_64` nebo `amd64`) distribuce a verze:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1.1), z 27.
* Debian 8.2 nebo novější verze
* 18.04 (.NET Core 1.1), Ubuntu 16.04, 14.04
* Linux Mint 17
* openSUSE 42.3 nebo novější verze (.NET Core 1.1)

Zobrazit [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, z verze podporu operačního systému a propojení zásad životního cyklu.

---

## <a name="linux-distribution-dependencies"></a>Závislosti distribuce Linuxu

Následující jsou určeny jako příklady. Přesné verze a názvy se mohou mírně lišit na vaší distribuci Linuxu podle výběru.

### <a name="ubuntu"></a>Ubuntu

Ubuntu distribuce vyžaduje nainstalované následující knihovny:

* liblttng ust0
* libcurl3
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
* krb5 knihovny
* libicu
* zlib

Uživatelé fedora: Pokud vaše openssl verze > = 1.1, budete muset nainstalovat openssl10 kompatibility.

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

Výchozí hodnoty skriptu k instalaci nejnovější verze "L", která je aktuálně .NET Core 1.1. Chcete-li nainstalovat sadu .NET Core 2.x, spusťte skript pomocí následující přepínače:

```console
./dotnet-install.sh -c Current
```

Skript bash instalačního programu se používá v scénáře automatizace a zařízení bez oprávnění správce. Tento skript také přečte přepínače prostředí PowerShell, aby je bylo možné použít pomocí skriptu v systémech Linux nebo OS X.

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a>Nainstalovat sadu .NET Core pro podporované verze Red Hat Enterprise Linux (RHEL)

Instalace .NET Core na podporované verze RHEL:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

**.NET core 2.1**

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Nejnovější rozhraní .NET Core 2.1 na informace o instalaci Red Hat Enterprise Linux, najdete v části [.NET Core 2.1 Příručka Začínáme](https://access.redhat.com/documentation/en-us/net_core/2.1/html/getting_started_guide/)

**.NET core 2.0**

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Nejnovější rozhraní .NET Core 2.0 na informace o instalaci Red Hat Enterprise Linux, najdete v části [.NET Core 2.0 Příručka Začínáme](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/) 

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**.NET core 1.1**

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2.  Nejnovější 1.1 rozhraní .NET Core na informace o instalaci Red Hat Enterprise Linux, najdete v části [.NET Core 1.1 Příručka Začínáme](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)
     
**.NET core 1.0**

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2.  Nejnovější rozhraní .NET Core 1.0 na informace o instalaci Red Hat Enterprise Linux, najdete v části [.NET Core 1.0 Příručka Začínáme](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)

Nápovědu Red Hat .NET kanál přístup k registraci najdete v tématu [kapitoly 1 v .NET Core 1.1 úvodní příručce k](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) na Red Hat.

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a>Nainstalovat sadu .NET Core pro podporované systémem Ubuntu a Linux Mint distribuce/verze (64bitová verze)

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Instalace .NET Core 2.x na podporované systémem Ubuntu a Linux Mint distribuce/verze (64bitová verze):

**.NET core 2.0**

|Moduly runtime a sady SDK          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux Mint 18|Ubuntu 14.04 / Linux Mint 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET core Runtime 2.0.9  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.9)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.9)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.9)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.9)            |
|.NET core Runtime 2.0.8  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.8)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.8)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.8)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.8)            |
|.NET core Runtime 2.0.7  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.7)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.7)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.7)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.7)            |
|.NET core Runtime 2.0.6  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.6)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|.NET core Runtime 2.0.5  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.5)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|.NET core SDK 2.1.202    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.202)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.202)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.202)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.202)            |
|.NET core SDK 2.1.201    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.201)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.201)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.201)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.201)            |
|.NET core SDK 2.1.200    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.200)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.200)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.200)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.200)            |
|.NET core SDK 2.1.105    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.105)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.105)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.105)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.105)            |
|.NET core SDK 2.1.103    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.103)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|.NET core SDK 2.0.3      |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.3)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |
|.NET core SDK 2.0.0      |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.0)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.0)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.0)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.0)            |

**.NET core 2.1**

>[!IMPORTANT]
> Použití .NET Core 2.1 pomocí sady Visual Studio, budete muset [nainstalovat Visual Studio 2017 15.7 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Moduly runtime a sady SDK          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux Mint 18|Ubuntu 14.04 / Linux Mint 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET core Runtime 2.1.2          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.2)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.2)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.2)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.2)            |
|.NET core SDK 2.1.400     |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.400)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.400)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.400)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.400)            |
|.NET core SDK 2.1.302     |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.302)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.302)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.302)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.302)            |
|.NET core Runtime 2.1.1          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.1)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.1)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.1)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.1)            |
|.NET core SDK 2.1.301     |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.301)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.301)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.301)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.301)            |
|.NET core Runtime 2.1.0          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.0)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0)            |
|.NET core SDK 2.1.300     |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.300)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300)            |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Instalace .NET Core 1.x na podporované systémem Ubuntu a Linux Mint distribuce/verze (64bitová verze):

| Moduly runtime a sady SDK         |Ubuntu 16.04 / Linux Mint 18|Ubuntu 14.04 / Linux Mint 17|
|-------------------------|----------------------------|----------------------------|
|.NET core Runtime 1.1.9  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime verzi 1.1.8  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.1.7  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.1.6  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.1.5  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.1.4  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.0.10 |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.0.9  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.0.8  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.0.7  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.0.5  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.0.4  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.10     |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.9      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK verzi 1.1.8      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.7      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.5      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.4      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.0.4      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.0.1      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a>Nainstalovat sadu .NET Core pro Debian podporované verze (64bitová verze)

Instalace .NET Core na podporované Debian verze (64bitová verze):

> [!NOTE]
> Adresář řízené uživatelem je vyžadován pro instalace z tar.gz systému Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Instalace .NET Core 2.x na podporované Debian verze (64bitová verze):

**.NET core 2.0**

|Moduly runtime a sady SDK          |Debian 9       |Debian 8       |
|-------------------------|---------------|---------------|
|.NET core Runtime 2.0.9  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.9)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.9)   |
|.NET core Runtime 2.0.8  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.8)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.8)   |
|.NET core Runtime 2.0.7  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.7)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.7)   |
|.NET core Runtime 2.0.6  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|.NET core Runtime 2.0.5  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|.NET core Runtime tedy 2.0.3  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.3)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.3)   |
|.NET core Runtime 2.0.0  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.0)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.0)   |
|.NET core SDK 2.1.202    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.202)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.202)   |
|.NET core SDK 2.1.201    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.201)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.201)   |
|.NET core SDK 2.1.200    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.200)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.200)   |
|.NET core SDK 2.1.105    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET core SDK 2.1.105    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET core SDK 2.1.104    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.104)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.104)   |
|.NET core SDK 2.1.103    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|.NET core SDK 2.1.102    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.102)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.102)   |
|.NET core SDK 2.1.101    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.101)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.101)   |
|.NET core SDK 2.0.3      |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |
|.NET core SDK 2.0.0      |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.0)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.0)   |

**.NET core 2.1**

>[!IMPORTANT]
> Použití .NET Core 2.1 pomocí sady Visual Studio, budete muset [nainstalovat Visual Studio 2017 15.7 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Moduly runtime a sady SDK                  |Debian 9       |Debian 8       |
|---------------------------------|---------------|---------------|
|.NET core Runtime 2.1.2          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.2)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.2)   |
|.NET core SDK 2.1.400        |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.400)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.400)        |
|.NET core SDK 2.1.302        |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.302)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.302)        |
|.NET core Runtime 2.1.1          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.1)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.1)   |
|.NET core SDK 2.1.301        |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.301)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.301)        |
|.NET core Runtime 2.1.0          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0)   |
|.NET core SDK 2.1.300        |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300)        |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Instalace rozhraní .NET Core 1.x na Debian 9 nebo Debian 8:

* .NET core Runtime 1.1.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-debian-x64-binaries)
* .NET core Runtime verzi 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-debian-x64-binaries)
* .NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)
* .NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)
* .NET core Runtime 1.1.5 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-debian-x64-binaries)
* .NET core Runtime 1.1.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-debian-x64-binaries)
* .NET core Runtime 1.1.2 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-debian-x64-binaries)
* Modulu Runtime .NET core 1.1.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-debian-x64-binaries)
* Modulu Runtime .NET core 1.1.0 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.0-linux-debian-x64-binaries)
* .NET core Runtime 1.0.10 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)
* .NET core Runtime 1.0.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)
* .NET core Runtime 1.0.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-debian-x64-binaries)
* .NET core Runtime 1.0.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-debian-x64-binaries)
* .NET core Runtime 1.0.5 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-debian-x64-binaries)
* .NET core Runtime 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-debian-x64-binaries)
* Sada .NET core SDK 1.1.10 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-debian-x64-binaries)
* Sada .NET core SDK 1.1.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-debian-x64-binaries)
* Sada .NET core SDK verzi 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)
* Sada .NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)
* Sada .NET core SDK 1.1.5 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-debian-x64-binaries)
* Sada .NET core SDK 1.1.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-debian-x64-binaries)
* Sada .NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)
* Sady SDK .NET core 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a>Nainstalovat sadu .NET Core pro podporované Fedora verze (64bitová verze)

Chcete-li nainstalovat sadu .NET Core o podporovaných verzích Fedora:

> [!NOTE]
> Adresář řízené uživatelem je vyžadován pro instalace z tar.gz systému Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Instalace .NET Core 2.x na podporované Fedora verze (64bitová verze):

**.NET core 2.0**

|Moduly runtime a sady SDK          |Fedora 26 nebo novější |Fedora 25 nebo předchozí |
|-------------------------|-------------------|----------------------|
|.NET core Runtime 2.0.9  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.9)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.9)           |
|.NET core Runtime 2.0.8  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.8)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.8)           |
|.NET core Runtime 2.0.7  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.7)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.7)           |
|.NET core Runtime 2.0.6  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|.NET core Runtime 2.0.5  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|.NET core Runtime tedy 2.0.3  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.3)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.3)           |
|.NET core Runtime 2.0.0  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.0)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.0)           |
|.NET core SDK 2.1.200    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.200)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.200)           |
|.NET core SDK 2.1.105    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.105)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.105)           |
|.NET core SDK 2.1.103    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|.NET core SDK 2.0.3      |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

**.NET core 2.1**

>[!IMPORTANT]
> Použití .NET Core 2.1 pomocí sady Visual Studio, budete muset [nainstalovat Visual Studio 2017 15.7 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Moduly runtime a sady SDK                  |Fedora 28          |Fedora 27             |
|---------------------------------|-------------------|----------------------|
|.NET core Runtime 2.1.2          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.2)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.2)           |
|.NET core SDK 2.1.400          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.400)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.400)           |
|.NET core SDK 2.1.302          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.302)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.302)           |
|.NET core Runtime 2.1.1          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.1)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.1)           |
|.NET core SDK 2.1.301          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.301)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.301)           |
|.NET core Runtime 2.1.0          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.0)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0)           |
|.NET core SDK 2.1.300          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.300)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.300)           |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Nainstalujte .NET Core 1.x nepodporuje Fedora verze (64bitová verze):

**Fedora 24**

* .NET core Runtime verzi 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-fedora-24-x64-binaries)
* .NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)
* .NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)
* .NET core Runtime 1.1.5 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-fedora-24-x64-binaries)
* .NET core Runtime 1.1.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-fedora-24-x64-binaries)
* .NET core Runtime 1.1.2 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-fedora-24-x64-binaries)
* Modulu Runtime .NET core 1.1.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-fedora-24-x64-binaries)
* Sada .NET core SDK 1.1.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-fedora-24-x64-binaries)
* Sada .NET core SDK verzi 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)
* Sada .NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)
* Sada .NET core SDK 1.1.5 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5linux-fedora-24-x64-binaries)
* Sada .NET core SDK 1.1.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5linux-fedora-24-x64-binaries)
* Sady SDK .NET core 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

**Fedora 23**

* .NET core Runtime 1.1.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-fedora-23-x64-binaries)
* .NET core Runtime 1.1.2 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-fedora-23-x64-binaries)
* Modulu Runtime .NET core 1.1.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-fedora-23-x64-binaries)
* .NET core Runtime 1.0.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)
* .NET core Runtime 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-fedora-23-x64-binaries)
* Sada .NET core SDK 1.1.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4linux-fedora-23-x64-binaries)
* Sada .NET core SDK 1.1.2 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.2linux-fedora-23-x64-binaries)
* Sada .NET core SDK 1.1.2 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.2linux-fedora-23-x64-binaries)
* Sada .NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)
* Sady SDK .NET core 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a>Nainstalovat sadu .NET Core pro podporované CentOS a Oracle Linux distribuce a verze (64bitová verze)

Chcete-li nainstalovat .NET Core pro podporované CentOS a Oracle Linux distribuce a verze (64bitová verze):

> [!NOTE]
> Adresář řízené uživatelem je vyžadován pro instalace z tar.gz systému Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Nainstalovat sadu .NET Core 2.x na podporované CentOS a Oracle Linux distribuce a verze (64bitová verze):

**.NET core 2.0**

* .NET core Runtime 2.0.9 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.9)
* .NET core Runtime 2.0.8 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.8)
* .NET core Runtime 2.0.7 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.7)
* .NET core Runtime 2.0.6 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)
* .NET core Runtime 2.0.5 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)
* .NET core Runtime tedy 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.3)
* .NET core Runtime 2.0.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.0)
* Sada .NET core SDK 2.1.202 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.202)
* Sada .NET core SDK 2.1.201 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.201)
* Sada .NET core SDK 2.1.200 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.200)
* Sada .NET core SDK 2.1.105 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.105)
* Sada .NET core SDK 2.1.104 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.104)
* Sada .NET core SDK 2.1.103 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)
* Sada .NET core SDK 2.1.102 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.102)
* Sada .NET core SDK 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)
* Sada .NET core SDK 2.0.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.0)
 
**.NET core 2.1**

>[!IMPORTANT]
> Použití .NET Core 2.1 pomocí sady Visual Studio, budete muset [nainstalovat Visual Studio 2017 15.7 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

* .NET core Runtime 2.1.2 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.2)
* Sada .NET core SDK 2.1.400 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.400)
* Sada .NET core SDK 2.1.302 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.302)
* .NET core Runtime 2.1.1 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.1)
* Sada .NET core SDK 2.1.301 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.301)
* .NET core Runtime 2.1.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0)
* Sada .NET core SDK 2.1.300 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300)

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Nainstalovat sadu .NET Core 1.x na podporované CentOS a Oracle Linux distribuce a verze (64bitová verze):

* .NET core Runtime 1.1.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-centos-x64-binaries)
* .NET core Runtime verzi 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-centos-x64-binaries)
* .NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)
* .NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)
* .NET core Runtime 1.1.5 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-centos-x64-binaries)
* .NET core Runtime 1.1.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-centos-x64-binaries)
* .NET core Runtime 1.1.2 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-centos-x64-binaries)
* Modulu Runtime .NET core 1.1.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-centos-x64-binaries)
* .NET core Runtime 1.0.12 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.12-linux-centos-x64-binaries)
* .NET core Runtime 1.0.11 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.11-linux-centos-x64-binaries)
* .NET core Runtime 1.0.10 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)
* .NET core Runtime 1.0.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)
* .NET core Runtime 1.0.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-centos-x64-binaries)
* .NET core Runtime 1.0.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-centos-x64-binaries)
* .NET core Runtime 1.0.5 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-centos-x64-binaries)
* .NET core Runtime 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-centos-x64-binaries)
* Sada .NET core SDK 1.1.10 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-centos-x64-binaries)
* Sada .NET core SDK 1.1.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-centos-x64-binaries)
* Sada .NET core SDK verzi 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)
* Sada .NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)
* Sada .NET core SDK 1.1.5 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-centos-x64-binaries)
* Sada .NET core SDK 1.1.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-centos-x64-binaries)
* Sada .NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)
* Sady SDK .NET core 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a>Nainstalovat sadu .NET Core pro podporované operačním systémem SUSE Linux Enterprise Server a OpenSUSE distribuce a verze (64bitová verze)

Chcete-li nainstalovat sadu .NET Core 2.x pro podporované operačním systémem SUSE Linux Enterprise Server a OpenSUSE distribuce/verze (64bitová verze):

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Instalace .NET Core 2.x na podporované operačním systémem SUSE Linux Enterprise Server a OpenSUSE distribuce a verze (64bitová verze):

**.NET core 2.0**

**SUSE Linux Enterprise Server**

* .NET core Runtime 2.0.9 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.9)
* .NET core Runtime 2.0.8 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.8)
* .NET core Runtime 2.0.7 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.7)
* .NET core Runtime 2.0.6 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.6)
* .NET core Runtime 2.0.5 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.5)
* .NET core Runtime tedy 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.3)
* .NET core Runtime 2.0.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.0)
* Sada .NET core SDK 2.1.202 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.202)
* Sada .NET core SDK 2.1.201 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.201)
* Sada .NET core SDK 2.1.200 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.200)
* Sada .NET core SDK 2.1.105 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.105)
* Sada .NET core SDK 2.1.104 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.104)
* Sada .NET core SDK 2.1.103 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.103)
* Sada .NET core SDK 2.1.102 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.102)
* Sada .NET core SDK 2.1.101 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.101)
* Sada .NET core SDK 2.1.100 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.100)
* Sada .NET core SDK 2.1.4 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.4)
* Sada .NET core SDK 2.1.2 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.2)
* Sada .NET core SDK 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.3)
* Sada .NET core SDK 2.0.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.0)

**openSUSE**

* .NET core Runtime 2.0.9 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.9)
* .NET core Runtime 2.0.8 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.8)
* .NET core Runtime 2.0.7 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.7)
* .NET core Runtime 2.0.6 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)
* .NET core Runtime 2.0.5 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)
* .NET core Runtime tedy 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.3)
* .NET core Runtime 2.0.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.0)
* Sada .NET core SDK 2.1.202 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.202)
* Sada .NET core SDK 2.1.201 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.201)
* Sada .NET core SDK 2.1.200 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.200)
* Sada .NET core SDK 2.1.105 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.105)
* Sada .NET core SDK 2.1.103 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)
* Sada .NET core SDK 2.1.102 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.102)
* Sada .NET core SDK 2.1.101 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.101)
* Sada .NET core SDK 2.1.100 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.100)
* Sada .NET core SDK 2.1.4 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.4)
* Sada .NET core SDK 2.1.2 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.2)
* Sada .NET core SDK 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)
* Sada .NET core SDK 2.0.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.0)
 
**.NET core 2.1**

>[!IMPORTANT]
> Použití .NET Core 2.1 pomocí sady Visual Studio, budete muset [nainstalovat Visual Studio 2017 15.7 nebo novější](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

**SUSE Linux Enterprise Server**

* .NET core Runtime 2.1.2 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.2)
* Sada .NET core SDK 2.1.400 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.400)
* Sada .NET core SDK 2.1.302 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.302)
* .NET core Runtime 2.1.1 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.1)
* Sada .NET core SDK 2.1.301 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.301)
* .NET core Runtime 2.1.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0)
* Sada .NET core SDK 2.1.300 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300)

**openSUSE**

* .NET core Runtime 2.1.2 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.2)
* Sada .NET core SDK 2.1.400 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.400)
* Sada .NET core SDK 2.1.302 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.302)
* .NET core Runtime 2.1.1 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.1)
* Sada .NET core SDK 2.1.301 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.301)
* .NET core Runtime 2.1.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0)
* Sada .NET core SDK 2.1.300 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300)

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Odeberte parametr **předchozí verze preview** verzích .NET Core z vašeho systému.

2. Instalace .NET Core 1.x na podporované operačním systémem SUSE Linux Enterprise Server a OpenSUSE distribuce a verze (64bitová verze):

**SUSE Linux Enterprise Server 13.2**

* .NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)
* .NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)
* Sada .NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)
* Sada .NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-13.2-x64-binaries)
* Sady SDK .NET core 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-13.2-x64-binaries)

---

## <a name="install-net-core-for-supported-alpine-linux-versions-64-bit"></a>Nainstalovat sadu .NET Core pro podporované verze Alpine Linux (64 bitů)

> [!NOTE]
> Adresář řízené uživatelem je vyžadován pro instalace z tar.gz systému Linux.

Stáhněte si a použijte pokyny k instalaci rozhraní .NET Core 2.1 pro podporované verze Alpine Linux (64-bit) na následujících odkazech:

* .NET core Runtime 2.1.2 [odkaz ke stažení](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.2-linux-x64-alpine-binaries)
* Sada .NET core SDK 2.1.400 [odkaz ke stažení](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.400-linux-x64-alpine-binaries)
* Sada .NET core SDK 2.1.302 [odkaz ke stažení](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.302-linux-x64-alpine-binaries)
* .NET core Runtime 2.1.1 [odkaz ke stažení](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.1-linux-x64-alpine-binaries)
* Sada .NET core SDK 2.1.301 [odkaz ke stažení](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.301-linux-x64-alpine-binaries)
* .NET core Runtime 2.1.0 [odkaz ke stažení](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.0-linux-x64-alpine-binaries)
* Sada .NET core SDK 2.1.300 [odkaz ke stažení](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.300-linux-x64-alpine-binaries)

> [!IMPORTANT]
> Pokud máte problémy s instalací rozhraní .NET Core na podporované distribuce systému Linux/version, najdete v následujících tématech nainstalovaných distribucí a verzí:
> * [Známé problémy s .NET core 2.1](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [Známé problémy s .NET core 2.0](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [Známé problémy s .NET core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [Známé problémy s .NET core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0)
