---
title: Předpoklady pro .NET Core v systému Linux
description: Podporované verze systému Linux a závislostí .NET Core k vývoji, nasazení a spouštění aplikací .NET Core na počítače se systémem Linux.
author: jralexander
ms.author: johalex
ms.date: 05/30/2018
ms.openlocfilehash: 9fcbb6589bf22f7d95ecbb8acb54b2094fc0183d
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696556"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Předpoklady pro .NET Core v systému Linux

Tento článek ukazuje závislosti potřebné k vývoji aplikací .NET Core v systému Linux. Podporované distribuce systému Linux nebo verze a závislosti, které platí na dva způsoby, jak vývoj aplikací .NET Core v systému Linux:

* [Příkazového řádku pomocí vašeho oblíbeného editoru](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> Balíček .NET Core SDK není nutné pro produkční servery nebo prostředí. Pouze balíček .NET Core runtime je potřeba pro aplikace nasazené do produkčního prostředí. Nasazení na .NET Core runtime s aplikacemi v rámci samostatná nasazení, ale musí být nasazený pro závislé na Framework nasazených aplikací samostatně. Další informace o typech nasazení závislé na framework a nezávislý najdete v tématu [nasazení aplikace .NET Core](./deploying/index.md). Viz také [aplikace Self-contained Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) konkrétní pokyny.

## <a name="supported-linux-versions"></a>Podporované verze systému Linux

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

.NET core 2.x vyhodnotí jako jeden operační systém Linux. Neexistuje jeden Linux sestavení (podle architektura procesoru) podporované distribuce systému Linux.

NET základní 2.x je podporovaný na následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce/verze:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 27, 26
* Debian 9 8.7 nebo novější verze
* Ubuntu 18.04, 17.10, 14.04 a 16.04
* Linux máta 18, 17
* openSUSE 42.3 nebo novější verze
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 nebo novější

V tématu [2.x .NET Core, podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, distribucí a verzí, nedostatek verze podporu operačního systému a odkazy na zásady životního cyklu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

.NET core 1.x je podporována v následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce/verze:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 26
* Debian 8.2 nebo novější verze
* Ubuntu 16.04, 14.04
* Linux máta 18, 17
* openSUSE 42.3 nebo novější verze (.NET Core 1.1)

V tématu [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.

---

## <a name="linux-distribution-dependencies"></a>Linux distribuční závislosti

Následující by měla být příklady. Přesné verze a názvy se mohou mírně lišit na Linux distribuční výběru.

### <a name="ubuntu"></a>Ubuntu

Ubuntu distribuce vyžadovat nainstalované následující knihovny:

* liblttng ust0
* libcurl3
* libssl1.0.0
* libkrb5-3
* zlib1g
* libicu52 (pro 14.x)
* libicu55 (pro 16.x)
* libicu57 (pro 17.x)
* libicu60 (pro 18.x)

Verze starší než .NET Core 2.1, následující závislosti jsou také vyžaduje:

* libunwind8
* libuuid1

### <a name="centos"></a>CentOS

Distribuce centOS vyžadovat nainstalované následující knihovny:

* Upravit lttng
* libcurl
* knihovny OpenSSL
* krb5 knihovny
* libicu
* zlib

Verze starší než .NET Core 2.1, následující závislosti jsou také vyžaduje:

* libunwind
* libuuid

Další informace o závislostech najdete v tématu [aplikace Self-contained Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalování závislostí .NET Core s nativní instalační programy

.NET core, které jsou k dispozici pro nativní instalační programy podporované distribuce systému Linux nebo verze. Nativní instalační programy vyžadují správce (sudo) přístup k serveru. Výhodou použití nativní instalační program je, že jsou nainstalovány všechny závislosti nativní .NET Core. Nativní instalační programy také nainstalovat celý systém .NET Core SDK.

V systému Linux existují dvě možnosti balíček Instalační služby:

* Pomocí Správce balíčků na základě informačního kanálu, jako například výstižný get pro Ubuntu nebo yum pro CentOS/RHEL.
* Použití balíčků, sami bázi DEB nebo ot. / min.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Skriptování nainstaluje s skript instalačního programu .NET Core

[Skriptů instalace dotnet](./tools/dotnet-install-script.md) se používají k provedení instalace bez oprávnění správce nástrojů rozhraní příkazového řádku a sdílený modul runtime. Si můžete stáhnout skript z [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).

Skript bash instalačního programu se používá v automatizace scénáře a instalace bez oprávnění správce. Tento skript také přečte přepínače prostředí PowerShell, takže je můžete používat pomocí skriptu v systémech Linux nebo OS X.

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a>Instalace .NET Core pro podporované verze systému Red Hat Enterprise Linux (RHEL)

Instalace .NET Core na podporovaných verzích systému RHEL:

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

Zajistěte, abyste měli nejnovější informace o instalaci, postupujte podle [pokyny 2.x SDK a instalační program modulu Runtime .NET Core](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current) pro podporované verze systému RHEL.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

**.NET core 1.1**

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2.  Nejnovější 1.1 .NET Core na informace o instalaci Red Hat Enterprise Linux, najdete v části [.NET Core 1.1 Průvodce Začínáme](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)
     
**.NET core 1.0**

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2.  Nejnovější 1.0 .NET Core na informace o instalaci Red Hat Enterprise Linux, najdete v části [.NET Core 1.0 Průvodce Začínáme](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)

Red Hat .NET kanál přístup registrace pomoc najdete v tématu [kapitoly 1 .NET Core 1.1 – Příručka Začínáme](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) v Red Hat.

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a>Instalace .NET Core pro podporované Ubuntu Linux máta distribuce/verze a (64 bitů)

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Nainstalujte .NET Core 2.x na podporované Ubuntu a Linux máta distribuce/verze (64bitová verze):

**.NET core 2.0**

|Moduly runtime nebo sady SDK          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux máta 18|Ubuntu 14.04 / Linux máta 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET core Runtime 2.0.7  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.7)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.7)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.7)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.7)            |
|.NET core Runtime 2.0.6  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.6)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|.NET core Runtime 2.0.5  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.5)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|.NET core SDK 2.1.105    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.105)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.105)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.105)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.105)            |
|.NET core SDK 2.1.103    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.103)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|.NET core SDK 2.0.3      |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.3)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |
|.NET core SDK 2.0.0      |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.0)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.0)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.0)          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.0)            |

**.NET core 2.1**

>[!IMPORTANT]
> Chcete-li použít pomocí sady Visual Studio .NET Core 2.1, je potřeba [instalaci Visual Studia 2017 15.7 Preview 1 nebo novější](https://www.visualstudio.com/vs/preview).

|Moduly runtime nebo sady SDK                  |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux máta 18|Ubuntu 14.04 / Linux máta 17|
|---------------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET core Runtime 2.1.0          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.0)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0)            |
|.NET core SDK 2.1.300     |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.300)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300)|[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300)            |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300)            |

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Nainstalujte .NET Core 1.x na podporované Ubuntu a Linux máta distribuce/verze (64bitová verze):

| Moduly runtime nebo sady SDK         |Ubuntu 16.04 / Linux máta 18|Ubuntu 14.04 / Linux máta 17|
|-------------------------|----------------------------|----------------------------|
|.NET core Runtime 1.1.7  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.1.6  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.0.10 |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|.NET core Runtime 1.0.9  |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK bodem 1.1.8      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.1.7      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.0.4      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK 1.0.1      |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[Odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a>Instalace .NET Core pro podporované verze Debian (64 bitů)

Instalace .NET Core na podporované Debian verze (64bitová verze):

> [!NOTE]
> Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Nainstalujte .NET Core 2.x na podporované Debian verze (64bitová verze):

**.NET core 2.0**

|Moduly runtime nebo sady SDK          |Debian 9       |Debian 8       |
|-------------------------|---------------|---------------|
|.NET core Runtime 2.0.7  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.7)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.7)   |
|.NET core Runtime 2.0.6  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|.NET core Runtime 2.0.5  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|.NET core SDK 2.1.105    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET core SDK 2.1.103    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|.NET core SDK 2.0.3      |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |
|.NET core SDK 2.0.0      |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.0)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.0)   |

**.NET core 2.1**

>[!IMPORTANT]
> Chcete-li použít pomocí sady Visual Studio .NET Core 2.1, je potřeba [instalaci Visual Studia 2017 15.7 Preview 1 nebo novější](https://www.visualstudio.com/vs/preview).

|Moduly runtime nebo sady SDK                  |Debian 9       |Debian 8       |
|---------------------------------|---------------|---------------|
|.NET core Runtime 2.1.0          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0)   |
|.NET core SDK 2.1.300        |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300)   |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300)        |

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Instalace rozhraní .NET základní 1.x na Debian 9 nebo Debian 8:

* .NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)
* .NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)
* .NET core Runtime 1.0.10 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)
* .NET core Runtime 1.0.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)
* .NET core SDK bodem 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)
* .NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)
* .NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)
* .NET core SDK 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a>Instalace .NET Core pro podporované verze Fedora (64 bitů)

Instalace .NET Core na podporované verze Fedora:

> [!NOTE]
> Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Nainstalujte .NET Core 2.x na podporované Fedora verze (64bitová verze):

**.NET core 2.0**

|Moduly runtime nebo sady SDK          |Fedora 26 nebo novější |Fedora 25 nebo předchozí |
|-------------------------|-------------------|----------------------|
|.NET core Runtime 2.0.7  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.7)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.7)           |
|.NET core Runtime 2.0.6  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|.NET core Runtime 2.0.5  |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|.NET core SDK 2.1.105    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.105)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.105)           |
|.NET core SDK 2.1.103    |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|.NET core SDK 2.0.3      |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

**.NET core 2.1**

>[!IMPORTANT]
> Chcete-li použít pomocí sady Visual Studio .NET Core 2.1, je potřeba [instalaci Visual Studia 2017 15.7 Preview 1 nebo novější](https://www.visualstudio.com/vs/preview).

|Moduly runtime nebo sady SDK                  |Fedora 27          |Fedora 26             |
|---------------------------------|-------------------|----------------------|
|.NET core Runtime 2.1.0          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0)           |
|.NET core SDK 2.1.300          |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.300)       |[Odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300)           |

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Nainstalujte .NET Core 1.x podporované Fedora verze (64bitová verze):

**Fedora 24**

* .NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)
* .NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)
* .NET core SDK bodem 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)
* .NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)
* .NET core SDK 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

**Fedora 23**

* .NET core Runtime 1.0.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)
* .NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)
* .NET core SDK 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a>Instalace .NET Core pro podporované CentOS a Oracle Linux distribuce/verze (64bitová verze)

Chcete-li nainstalovat rozhraní .NET základní pro podporované CentOS a Oracle Linux distribuce/verze (64bitová verze):

> [!NOTE]
> Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Instalace .NET Core 2.x na podporované CentOS a Oracle Linux distribuce/verze (64bitová verze):

**.NET core 2.0**

* .NET core Runtime 2.0.7 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)
* .NET core Runtime 2.0.6 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)
* .NET core Runtime 2.0.5 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)
* .NET core SDK 2.1.105 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.105)
* .NET core SDK 2.1.103 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)
* .NET core SDK 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)
* .NET core SDK 2.0.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.0)
 
**.NET core 2.1**

>[!IMPORTANT]
> Chcete-li použít pomocí sady Visual Studio .NET Core 2.1, je potřeba [instalaci Visual Studia 2017 15.7 Preview 1 nebo novější](https://www.visualstudio.com/vs/preview/).

* .NET core Runtime 2.1.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0)
* .NET core SDK 2.1.300 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300)

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Instalace .NET Core 1.x na podporované CentOS a Oracle Linux distribuce/verze (64bitová verze):

* .NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)
* .NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)
* .NET core Runtime 1.0.10 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)
* .NET core Runtime 1.0.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)
* .NET core SDK bodem 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)
* .NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)
* .NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)
* .NET core SDK 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a>Instalace .NET Core podporované SUSE Linux Enterprise Server a OpenSUSE distribuce/verze (64bitová verze)

K instalaci .NET Core 2.x pro podporované SUSE Linux Enterprise Server a OpenSUSE distribuce/verze (64bitová verze):

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Nainstalujte .NET Core 2.x na podporované SUSE Linux Enterprise Server a OpenSUSE distribuce/verze (64bitová verze):

**.NET core 2.0**

**SUSE Linux Enterprise Server**

* .NET core Runtime 2.0.7 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.7)
* .NET core Runtime 2.0.6 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.6)
* .NET core Runtime 2.0.5 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.5)
* .NET core SDK 2.1.105 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.105)
* .NET core SDK 2.1.103 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.103)
* .NET core SDK 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.3)
* .NET core SDK 2.0.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.0)

**openSUSE**

* .NET core Runtime 2.0.7 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.7)
* .NET core Runtime 2.0.6 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)
* .NET core Runtime 2.0.5 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)
* .NET core SDK 2.1.105 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.105)
* .NET core SDK 2.1.103 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)
* .NET core SDK 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)
* .NET core SDK 2.0.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.0)
 
**.NET core 2.1**

>[!IMPORTANT]
> Chcete-li použít pomocí sady Visual Studio .NET Core 2.1, je potřeba [instalaci Visual Studia 2017 15.7 Preview 1 nebo novější](https://www.visualstudio.com/vs/preview).

**SUSE Linux Enterprise Server**

* .NET core Runtime 2.1.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0)
* .NET core SDK 2.1.300 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300)


**openSUSE**

* .NET core Runtime 2.1.0 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0)
* .NET core SDK 2.1.300 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300)

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Nainstalujte .NET Core 1.x na podporované SUSE Linux Enterprise Server a OpenSUSE distribuce/verze (64bitová verze):

**SUSE Linux Enterprise Server 13.2**

* .NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)
* .NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)
* .NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)

**openSUSE 24**

* .NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)
* .NET core SDK 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)

---

> [!IMPORTANT]
> Pokud máte potíže s instalací jádra .NET na podporované distribuce systému Linux nebo verzi, naleznete v následujících tématech nainstalovaných distribuce/verzí:
> * [.NET core 2.1 známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [Rozhraní .NET 2.0 základní známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [.NET core 1.1 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [.NET core 1.0 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0)
