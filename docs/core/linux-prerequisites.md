---
title: "Předpoklady pro .NET Core v systému Linux"
description: "Podporované verze systému Linux a závislostí .NET Core k vývoji, nasazení a spouštění aplikací .NET Core na počítače se systémem Linux."
keywords: Debian, ubuntu Linux, .NET, .NET core RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: ec08d9fa3ad672400b61c269da0c6a70ed9ef2f5
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a>Předpoklady pro .NET Core v systému Linux

Tento článek ukazuje závislosti potřebné k vývoji aplikací .NET Core v systému Linux. Podporované distribuce systému Linux nebo verze a závislosti, které platí na dva způsoby, jak vývoj aplikací .NET Core v systému Linux:

* [Příkazového řádku pomocí vašeho oblíbeného editoru](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a>Podporované verze systému Linux

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

Rozhraní .NET 2.0 základní považuje za jeden operační systém Linux. Neexistuje jeden Linux sestavení (podle architektura procesoru) pro podporovaných distribucích systému Linux.

NET základní 2.x je podporovaný na následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce/verze:

 * Red Hat Enterprise Linux 7
 * CentOS 7
 * Oracle Linux 7
 * Fedora 25, Fedora 26
 * Debian 8.7 nebo novější verze 
 * Ubuntu č. 17.04, Ubuntu 16.04, Ubuntu 14.04
 * Linux máta 18, máta Linux 17
 * openSUSE 42.2 nebo novější verze
 * SUSE Enterprise Linux (SLES) 12 SP2 nebo novější verze

V tématu [2.x .NET Core, podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

.NET core 1.x je podporována v následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce/verze:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 24
* Debian 8.2 nebo novější verze
* Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*
 * Ubuntu 16.10 podporuje nejnovější verze opravy .NET Core 1.1
* Linux Mint 17
* openSUSE 42,1 nebo novější verze (.NET Core 1.1)

V tématu [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.

---

## <a name="linux-distribution-dependencies"></a>Linux distribuční závislosti

Následující by měla být příklady. Přesné verze a názvy se mohou mírně lišit na Linux distribuční výběru.

### <a name="ubuntu"></a>Ubuntu

Ubuntu distribuce vyžadovat nainstalované následující knihovny:

* libunwind8
* liblttng ust0
* libcurl3
* libssl1.0.0
* libuuid1
* libkrb5
* zlib1g
* libicu52 (pro 14.X)
* libicu55 (pro 16.X)
* libicu57 (pro 17.X)

### <a name="centos"></a>CentOS

Distribuce centOS vyžadovat nainstalované následující knihovny:

* libunwind
* Upravit lttng
* libcurl
* knihovny OpenSSL
* libuuid
* krb5 knihovny
* libicu
* zlib

Další informace o závislostech najdete v tématu [aplikace Self-contained Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Instalování závislostí .NET Core s nativní instalační programy

.NET core, které jsou k dispozici pro nativní instalační programy podporované distribuce systému Linux nebo verze. Nativní instalační programy vyžadují správce (sudo) přístup k serveru. Výhodou použití nativní instalační program je, že jsou nainstalovány všechny závislosti nativní .NET Core. Nativní instalační programy také nainstalovat celý systém .NET Core SDK.

V systému Linux existují dvě možnosti balíček Instalační služby:

* Pomocí Správce balíčků na základě informačního kanálu, jako například výstižný get pro Ubuntu nebo yum pro CentOS/RHEL.
* Použití balíčků, sami bázi DEB nebo ot. / min.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>Skriptování nainstaluje s skript instalačního programu .NET Core

`dotnet-install` Skripty se používají k provedení instalace bez oprávnění správce nástrojů rozhraní příkazového řádku a sdílený modul runtime. Si můžete stáhnout skript z: https://dot.net/v1/dotnet-install.sh

Skript bash instalačního programu se používá v automatizace scénáře a instalace bez oprávnění správce. Tento skript také přečte přepínače prostředí PowerShell, takže je můžete používat pomocí skriptu v systémech Linux nebo OS X.

> [!IMPORTANT]
> Před spuštěním skriptu nainstalujte požadované [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a>Instalace .NET Core pro Red Hat Enterprise Linux (RHEL) 7

Instalace .NET Core na RHEL 7:

1. Povolte kanál Red Hat .NET, který je k dispozici v rámci svého předplatného RHEL 7.
    * Red Hat Enterprise 7 Server použijte:
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * Red Hat Enterprise 7 pracovní stanice použijte:
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * Red Hat Enterprise 7 HPC výpočetní uzel použijte:
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. Nainstalujte nástroj scl.

    ```bash
    yum install scl-utils
    ```
    
3. Instalace .NET Core

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

Nainstalujte základní rozhraní .NET 2.0 SDK a modulu Runtime:

   ```bash
   yum install rh-dotnet20
   ```

Povolte .NET Core SDK nebo modul Runtime 2.0 pro vaše prostředí:

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

**.NET core 1.1**

Instalace .NET Core 1.1 SDK a modulu Runtime:

   ```bash
   yum install rh-dotnetcore11
   ```

Povolte .NET Core 1.1 SDK a modulu Runtime pro vaše prostředí:

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

**.NET core 1.0**

Instalace rozhraní .NET základní 1.0 SDK a modulu Runtime:

   ```bash
   yum install rh-dotnetcore10
   ```

Povolte .NET Core 1.0 SDK a modulu Runtime pro vaše prostředí:

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.

     ```bash
     dotnet --version
     ```

Red Hat .NET kanál přístup registrace pomoc najdete v tématu [kapitoly 1 .NET Core 1.1 – Příručka Začínáme](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) v Red Hat.

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a>Instalace .NET Core pro Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 a Linux máta 17 18 máta Linux (64 bitů)

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

2. Registrovat Microsoft Product key jako důvěryhodné.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. Nastavte balíček hostitele požadovanou verzi kanálu.

   **Ubuntu 17.10**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod artful main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```
   **Ubuntu č. 17.04**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 16.04 / Linux máta 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 14.04 / Linux máta 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. Nainstalujte .NET Core.

   ```bash
   sudo apt-get install dotnet-sdk-2.1.3
   ```

4. Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

2. Nastavte balíček hostitele požadovanou verzi kanálu.

   **Ubuntu 16.10**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  **Ubuntu 16.04 / Linux máta 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   **Ubuntu 14.04 / Linux máta 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. Instalace rozhraní .NET základní 1.x na Ubuntu nebo máta Linux:

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a>Instalace .NET Core pro Debian 8 nebo Debian 9 (64 bitů)

Instalace .NET Core na Debian 8 nebo Debian 9 (64 bitů):

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

> [!NOTE]
> Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

2. Instalace komponent systému.

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. Zaregistrujte důvěryhodné Microsoft Product key.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. Zaregistrujte Product Microsoft informačního kanálu.

   **Debian 9 (Stretch)**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   **Debian 8 (Klára)**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. Nainstalujte .NET Core SDK.

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. Přidejte CESTU k dotnet.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

2. Získáte požadované součásti.

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. Stáhněte si .NET Core SDK binárních souborů (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. Rozbalte binární soubory .NET Core SDK.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Přidejte CESTU k dotnet.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a>Instalace .NET Core pro Fedora 24, Fedora 25 nebo Fedora 26 (64 bitů)

Chcete-li nainstalovat .NET Core 2.x na Fedora 26 nebo Fedora 25 nebo .NET Core 1.x na Fedora 24:

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

> [!NOTE]
> Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

**Fedora 26 nebo Fedora 25**

2. Zaregistrujte klíč podpisu společnosti Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Přidání produktu dotnet informačního kanálu.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. Nainstalujte základní rozhraní .NET SDK.

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. Přidejte CESTU k dotnet.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

**Fedora 24**

2. Získáte požadované součásti.

   ```bash
   sudo dnf install libunwind libicu
   ```

3. Stáhněte si .NET Core SDK binárního souboru (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. Rozbalte binární soubory .NET Core SDK.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Přidejte CESTU k dotnet.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a>Instalace .NET Core pro CentOS 7.1 (64 bitů) a Oracle Linux 7.1 (64 bitů)

Chcete-li nainstalovat .NET Core pro CentOS 7.1 (64 bitů) a Oracle Linux 7.1 (64 bitů):

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

> [!NOTE]
> Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

2. Zaregistrujte klíč podpisu společnosti Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Přidejte Product Microsoft informačního kanálu.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. Nainstalujte základní rozhraní .NET SDK.

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. Přidejte do své CESTĚ dotnet.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

2. Získáte požadované součásti.

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. Stáhněte si .NET Core SDK binárního souboru (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. Rozbalte binární soubory .NET Core SDK.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Přidejte CESTU k dotnet.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a>Instalace .NET Core pro SUSE Linux Enterprise Server (64 bitů)

Chcete-li nainstalovat .NET Core 2.x pro SUSE Linux Enterprise Server (SLES) 12 SP2 (64bitová verze):

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

2. Přidání produktu dotnet informačního kanálu.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. Nainstalujte základní rozhraní .NET SDK.

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. Přidejte CESTU k dotnet.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a>Instalace .NET Core pro openSUSE (64 bitů)

Chcete-li nainstalovat .NET Core 2.x openSUSE nebo .NET Core 1.x pro openSUSE (64 bitů):

1. Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.

> [!NOTE]
> Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

2. Zaregistrujte klíč podpisu společnosti Microsoft.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Přidání produktu dotnet informačního kanálu.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. Nainstalujte základní rozhraní .NET SDK.

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. Přidejte CESTU k dotnet.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

2. Získáte požadované součásti.

   ```bash
   sudo zypper install libunwind libicu
   ```

3. Stáhněte si .NET Core SDK binárního souboru (tarball).

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. Rozbalte binární soubory .NET Core SDK.
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. Přidejte CESTU k dotnet.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> Pokud máte potíže s instalací 2.x .NET Core na podporované distribuce systému Linux nebo verzi, naleznete [2.0 – známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.0) tématu nainstalovaných distribuce/verzí. 
>
> Pokud máte potíže s instalací 1.x .NET Core na podporované distribuce systému Linux nebo verzi, naleznete [1.0.0 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) témata pro vaše nainstalovaná distribuce / verze.
