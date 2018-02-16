---
title: "Předpoklady pro .NET Core v systému Linux"
description: "Podporované verze systému Linux a závislostí .NET Core k vývoji, nasazení a spouštění aplikací .NET Core na počítače se systémem Linux."
keywords: Debian, ubuntu Linux, .NET, .NET core RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 12/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload:
- dotnetcore
ms.openlocfilehash: 913d3869559b10af508e695a06d06021f8f90175
ms.sourcegitcommit: adcf9bdafeaa6bc243af7bf70b45f3df954f256a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="207f1-104">Předpoklady pro .NET Core v systému Linux</span><span class="sxs-lookup"><span data-stu-id="207f1-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="207f1-105">Tento článek ukazuje závislosti potřebné k vývoji aplikací .NET Core v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="207f1-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="207f1-106">Podporované distribuce systému Linux nebo verze a závislosti, které platí na dva způsoby, jak vývoj aplikací .NET Core v systému Linux:</span><span class="sxs-lookup"><span data-stu-id="207f1-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="207f1-107">Příkazového řádku pomocí vašeho oblíbeného editoru</span><span class="sxs-lookup"><span data-stu-id="207f1-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="207f1-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="207f1-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="207f1-109">Podporované verze systému Linux</span><span class="sxs-lookup"><span data-stu-id="207f1-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="207f1-110">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="207f1-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="207f1-111">Rozhraní .NET 2.0 základní považuje za jeden operační systém Linux.</span><span class="sxs-lookup"><span data-stu-id="207f1-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="207f1-112">Neexistuje jeden Linux sestavení (podle architektura procesoru) pro podporovaných distribucích systému Linux.</span><span class="sxs-lookup"><span data-stu-id="207f1-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="207f1-113">NET základní 2.x je podporovaný na následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce/verze:</span><span class="sxs-lookup"><span data-stu-id="207f1-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="207f1-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="207f1-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="207f1-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="207f1-115">CentOS 7</span></span>
 * <span data-ttu-id="207f1-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="207f1-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="207f1-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="207f1-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="207f1-118">Debian 8.7 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="207f1-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="207f1-119">Ubuntu č. 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="207f1-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="207f1-120">Linux máta 18, máta Linux 17</span><span class="sxs-lookup"><span data-stu-id="207f1-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="207f1-121">openSUSE 42.2 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="207f1-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="207f1-122">SUSE Enterprise Linux (SLES) 12 SP2 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="207f1-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="207f1-123">V tématu [2.x .NET Core, podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="207f1-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="207f1-124">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="207f1-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="207f1-125">.NET core 1.x je podporována v následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce/verze:</span><span class="sxs-lookup"><span data-stu-id="207f1-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="207f1-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="207f1-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="207f1-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="207f1-127">CentOS 7</span></span>
* <span data-ttu-id="207f1-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="207f1-128">Oracle Linux 7</span></span>
* <span data-ttu-id="207f1-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="207f1-129">Fedora 24</span></span>
* <span data-ttu-id="207f1-130">Debian 8.2 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="207f1-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="207f1-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="207f1-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="207f1-132">Ubuntu 16.10 podporuje nejnovější verze opravy .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="207f1-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="207f1-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="207f1-133">Linux Mint 17</span></span>
* <span data-ttu-id="207f1-134">openSUSE 42,1 nebo novější verze (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="207f1-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="207f1-135">V tématu [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="207f1-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="207f1-136">Linux distribuční závislosti</span><span class="sxs-lookup"><span data-stu-id="207f1-136">Linux distribution dependencies</span></span>

<span data-ttu-id="207f1-137">Následující by měla být příklady.</span><span class="sxs-lookup"><span data-stu-id="207f1-137">The following are intended to be examples.</span></span> <span data-ttu-id="207f1-138">Přesné verze a názvy se mohou mírně lišit na Linux distribuční výběru.</span><span class="sxs-lookup"><span data-stu-id="207f1-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="207f1-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="207f1-139">Ubuntu</span></span>

<span data-ttu-id="207f1-140">Ubuntu distribuce vyžadovat nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="207f1-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="207f1-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="207f1-141">libunwind8</span></span>
* <span data-ttu-id="207f1-142">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="207f1-142">liblttng-ust0</span></span>
* <span data-ttu-id="207f1-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="207f1-143">libcurl3</span></span>
* <span data-ttu-id="207f1-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="207f1-144">libssl1.0.0</span></span>
* <span data-ttu-id="207f1-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="207f1-145">libuuid1</span></span>
* <span data-ttu-id="207f1-146">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="207f1-146">libkrb5-3</span></span>
* <span data-ttu-id="207f1-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="207f1-147">zlib1g</span></span>
* <span data-ttu-id="207f1-148">libicu52 (pro 14.X)</span><span class="sxs-lookup"><span data-stu-id="207f1-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="207f1-149">libicu55 (pro 16.X)</span><span class="sxs-lookup"><span data-stu-id="207f1-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="207f1-150">libicu57 (pro 17.X)</span><span class="sxs-lookup"><span data-stu-id="207f1-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="207f1-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="207f1-151">CentOS</span></span>

<span data-ttu-id="207f1-152">Distribuce centOS vyžadovat nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="207f1-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="207f1-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="207f1-153">libunwind</span></span>
* <span data-ttu-id="207f1-154">Upravit lttng</span><span class="sxs-lookup"><span data-stu-id="207f1-154">lttng-ust</span></span>
* <span data-ttu-id="207f1-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="207f1-155">libcurl</span></span>
* <span data-ttu-id="207f1-156">knihovny OpenSSL</span><span class="sxs-lookup"><span data-stu-id="207f1-156">openssl-libs</span></span>
* <span data-ttu-id="207f1-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="207f1-157">libuuid</span></span>
* <span data-ttu-id="207f1-158">krb5 knihovny</span><span class="sxs-lookup"><span data-stu-id="207f1-158">krb5-libs</span></span>
* <span data-ttu-id="207f1-159">libicu</span><span class="sxs-lookup"><span data-stu-id="207f1-159">libicu</span></span>
* <span data-ttu-id="207f1-160">zlib</span><span class="sxs-lookup"><span data-stu-id="207f1-160">zlib</span></span>

<span data-ttu-id="207f1-161">Další informace o závislostech najdete v tématu [aplikace Self-contained Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="207f1-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="207f1-162">Instalování závislostí .NET Core s nativní instalační programy</span><span class="sxs-lookup"><span data-stu-id="207f1-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="207f1-163">.NET core, které jsou k dispozici pro nativní instalační programy podporované distribuce systému Linux nebo verze.</span><span class="sxs-lookup"><span data-stu-id="207f1-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="207f1-164">Nativní instalační programy vyžadují správce (sudo) přístup k serveru.</span><span class="sxs-lookup"><span data-stu-id="207f1-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="207f1-165">Výhodou použití nativní instalační program je, že jsou nainstalovány všechny závislosti nativní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="207f1-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="207f1-166">Nativní instalační programy také nainstalovat celý systém .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="207f1-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="207f1-167">V systému Linux existují dvě možnosti balíček Instalační služby:</span><span class="sxs-lookup"><span data-stu-id="207f1-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="207f1-168">Pomocí Správce balíčků na základě informačního kanálu, jako například výstižný get pro Ubuntu nebo yum pro CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="207f1-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="207f1-169">Použití balíčků, sami bázi DEB nebo ot. / min.</span><span class="sxs-lookup"><span data-stu-id="207f1-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="207f1-170">Skriptování nainstaluje s skript instalačního programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="207f1-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="207f1-171">`dotnet-install` Skripty se používají k provedení instalace bez oprávnění správce nástrojů rozhraní příkazového řádku a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="207f1-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="207f1-172">Si můžete stáhnout skript z: https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="207f1-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="207f1-173">Skript bash instalačního programu se používá v automatizace scénáře a instalace bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="207f1-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="207f1-174">Tento skript také přečte přepínače prostředí PowerShell, takže je můžete používat pomocí skriptu v systémech Linux nebo OS X.</span><span class="sxs-lookup"><span data-stu-id="207f1-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="207f1-175">Před spuštěním skriptu nainstalujte požadované [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="207f1-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="207f1-176">Instalace .NET Core pro Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="207f1-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="207f1-177">Instalace .NET Core na RHEL 7:</span><span class="sxs-lookup"><span data-stu-id="207f1-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="207f1-178">Povolte kanál Red Hat .NET, který je k dispozici v rámci svého předplatného RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="207f1-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="207f1-179">Red Hat Enterprise 7 Server použijte:</span><span class="sxs-lookup"><span data-stu-id="207f1-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="207f1-180">Red Hat Enterprise 7 pracovní stanice použijte:</span><span class="sxs-lookup"><span data-stu-id="207f1-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="207f1-181">Red Hat Enterprise 7 HPC výpočetní uzel použijte:</span><span class="sxs-lookup"><span data-stu-id="207f1-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="207f1-182">Nainstalujte nástroj scl.</span><span class="sxs-lookup"><span data-stu-id="207f1-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="207f1-183">Instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="207f1-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="207f1-184">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="207f1-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="207f1-185">Nainstalujte základní rozhraní .NET 2.0 SDK a modulu Runtime:</span><span class="sxs-lookup"><span data-stu-id="207f1-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="207f1-186">Povolte .NET Core SDK nebo modul Runtime 2.0 pro vaše prostředí:</span><span class="sxs-lookup"><span data-stu-id="207f1-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="207f1-187">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="207f1-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="207f1-188">**.NET core 1.1**</span><span class="sxs-lookup"><span data-stu-id="207f1-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="207f1-189">Instalace .NET Core 1.1 SDK a modulu Runtime:</span><span class="sxs-lookup"><span data-stu-id="207f1-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="207f1-190">Povolte .NET Core 1.1 SDK a modulu Runtime pro vaše prostředí:</span><span class="sxs-lookup"><span data-stu-id="207f1-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="207f1-191">**.NET core 1.0**</span><span class="sxs-lookup"><span data-stu-id="207f1-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="207f1-192">Instalace rozhraní .NET základní 1.0 SDK a modulu Runtime:</span><span class="sxs-lookup"><span data-stu-id="207f1-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="207f1-193">Povolte .NET Core 1.0 SDK a modulu Runtime pro vaše prostředí:</span><span class="sxs-lookup"><span data-stu-id="207f1-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="207f1-194">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="207f1-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="207f1-195">Red Hat .NET kanál přístup registrace pomoc najdete v tématu [kapitoly 1 .NET Core 1.1 – Příručka Začínáme](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) v Red Hat.</span><span class="sxs-lookup"><span data-stu-id="207f1-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="207f1-196">Instalace .NET Core pro Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 a Linux máta 17 18 máta Linux (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="207f1-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="207f1-197">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="207f1-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="207f1-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="207f1-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="207f1-199">Registrovat Microsoft Product key jako důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="207f1-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="207f1-200">Nastavte balíček hostitele požadovanou verzi kanálu.</span><span class="sxs-lookup"><span data-stu-id="207f1-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="207f1-201">**Ubuntu 17.10**</span><span class="sxs-lookup"><span data-stu-id="207f1-201">**Ubuntu 17.10**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod artful main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```
   <span data-ttu-id="207f1-202">Ubuntu č. 17.04</span><span class="sxs-lookup"><span data-stu-id="207f1-202">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="207f1-203">**Ubuntu 16.04 / Linux máta 18**</span><span class="sxs-lookup"><span data-stu-id="207f1-203">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="207f1-204">**Ubuntu 14.04 / Linux máta 17**</span><span class="sxs-lookup"><span data-stu-id="207f1-204">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="207f1-205">Nainstalujte .NET Core.</span><span class="sxs-lookup"><span data-stu-id="207f1-205">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.1.4
   ```

4. <span data-ttu-id="207f1-206">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="207f1-206">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="207f1-207">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="207f1-207">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="207f1-208">Nastavte balíček hostitele požadovanou verzi kanálu.</span><span class="sxs-lookup"><span data-stu-id="207f1-208">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="207f1-209">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="207f1-209">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="207f1-210">**Ubuntu 16.04 / Linux máta 18**</span><span class="sxs-lookup"><span data-stu-id="207f1-210">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="207f1-211">**Ubuntu 14.04 / Linux máta 17**</span><span class="sxs-lookup"><span data-stu-id="207f1-211">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="207f1-212">Instalace rozhraní .NET základní 1.x na Ubuntu nebo máta Linux:</span><span class="sxs-lookup"><span data-stu-id="207f1-212">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="207f1-213">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="207f1-213">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="207f1-214">Instalace .NET Core pro Debian 8 nebo Debian 9 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="207f1-214">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="207f1-215">Instalace .NET Core na Debian 8 nebo Debian 9 (64 bitů):</span><span class="sxs-lookup"><span data-stu-id="207f1-215">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="207f1-216">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="207f1-216">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="207f1-217">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="207f1-217">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="207f1-218">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="207f1-218">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="207f1-219">Instalace komponent systému.</span><span class="sxs-lookup"><span data-stu-id="207f1-219">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="207f1-220">Zaregistrujte důvěryhodné Microsoft Product key.</span><span class="sxs-lookup"><span data-stu-id="207f1-220">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="207f1-221">Zaregistrujte Product Microsoft informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="207f1-221">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="207f1-222">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="207f1-222">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="207f1-223">Debian 8 (Klára)</span><span class="sxs-lookup"><span data-stu-id="207f1-223">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="207f1-224">Nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="207f1-224">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="207f1-225">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="207f1-225">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="207f1-226">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="207f1-226">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="207f1-227">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="207f1-227">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="207f1-228">Získáte požadované součásti.</span><span class="sxs-lookup"><span data-stu-id="207f1-228">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="207f1-229">Stáhněte si .NET Core SDK binárních souborů (tarball).</span><span class="sxs-lookup"><span data-stu-id="207f1-229">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="207f1-230">Rozbalte binární soubory .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="207f1-230">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="207f1-231">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="207f1-231">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="207f1-232">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="207f1-232">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="207f1-233">Instalace .NET Core pro Fedora 24, Fedora 25 nebo Fedora 26 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="207f1-233">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="207f1-234">Chcete-li nainstalovat .NET Core 2.x na Fedora 26 nebo Fedora 25 nebo .NET Core 1.x na Fedora 24:</span><span class="sxs-lookup"><span data-stu-id="207f1-234">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="207f1-235">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="207f1-235">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="207f1-236">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="207f1-236">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="207f1-237">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="207f1-237">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="207f1-238">**Fedora 26 nebo Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="207f1-238">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="207f1-239">Zaregistrujte klíč podpisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="207f1-239">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="207f1-240">Přidání produktu dotnet informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="207f1-240">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="207f1-241">Nainstalujte základní rozhraní .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="207f1-241">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="207f1-242">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="207f1-242">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="207f1-243">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="207f1-243">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="207f1-244">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="207f1-244">**Fedora 24**</span></span>

2. <span data-ttu-id="207f1-245">Získáte požadované součásti.</span><span class="sxs-lookup"><span data-stu-id="207f1-245">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="207f1-246">Stáhněte si .NET Core SDK binárního souboru (tarball).</span><span class="sxs-lookup"><span data-stu-id="207f1-246">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="207f1-247">Rozbalte binární soubory .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="207f1-247">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="207f1-248">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="207f1-248">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="207f1-249">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="207f1-249">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="207f1-250">Instalace .NET Core pro CentOS 7.1 (64 bitů) a Oracle Linux 7.1 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="207f1-250">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="207f1-251">Chcete-li nainstalovat .NET Core pro CentOS 7.1 (64 bitů) a Oracle Linux 7.1 (64 bitů):</span><span class="sxs-lookup"><span data-stu-id="207f1-251">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="207f1-252">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="207f1-252">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="207f1-253">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="207f1-253">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="207f1-254">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="207f1-254">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="207f1-255">Zaregistrujte klíč podpisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="207f1-255">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="207f1-256">Přidejte Product Microsoft informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="207f1-256">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="207f1-257">Nainstalujte základní rozhraní .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="207f1-257">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="207f1-258">Přidejte do své CESTĚ dotnet.</span><span class="sxs-lookup"><span data-stu-id="207f1-258">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="207f1-259">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="207f1-259">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="207f1-260">Získáte požadované součásti.</span><span class="sxs-lookup"><span data-stu-id="207f1-260">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="207f1-261">Stáhněte si .NET Core SDK binárního souboru (tarball).</span><span class="sxs-lookup"><span data-stu-id="207f1-261">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="207f1-262">Rozbalte binární soubory .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="207f1-262">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="207f1-263">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="207f1-263">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="207f1-264">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="207f1-264">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="207f1-265">Instalace .NET Core pro SUSE Linux Enterprise Server (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="207f1-265">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="207f1-266">Chcete-li nainstalovat .NET Core 2.x pro SUSE Linux Enterprise Server (SLES) 12 SP2 (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="207f1-266">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="207f1-267">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="207f1-267">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="207f1-268">Přidání produktu dotnet informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="207f1-268">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="207f1-269">Nainstalujte základní rozhraní .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="207f1-269">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="207f1-270">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="207f1-270">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="207f1-271">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="207f1-271">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="207f1-272">Instalace .NET Core pro openSUSE (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="207f1-272">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="207f1-273">Chcete-li nainstalovat .NET Core 2.x openSUSE nebo .NET Core 1.x pro openSUSE (64 bitů):</span><span class="sxs-lookup"><span data-stu-id="207f1-273">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="207f1-274">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="207f1-274">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="207f1-275">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="207f1-275">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="207f1-276">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="207f1-276">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="207f1-277">Zaregistrujte klíč podpisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="207f1-277">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="207f1-278">Přidání produktu dotnet informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="207f1-278">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="207f1-279">Nainstalujte základní rozhraní .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="207f1-279">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="207f1-280">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="207f1-280">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="207f1-281">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="207f1-281">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="207f1-282">Získáte požadované součásti.</span><span class="sxs-lookup"><span data-stu-id="207f1-282">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="207f1-283">Stáhněte si .NET Core SDK binárního souboru (tarball).</span><span class="sxs-lookup"><span data-stu-id="207f1-283">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="207f1-284">Rozbalte binární soubory .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="207f1-284">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="207f1-285">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="207f1-285">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="207f1-286">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="207f1-286">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="207f1-287">Pokud máte potíže s instalací 2.x .NET Core na podporované distribuce systému Linux nebo verzi, naleznete [2.0 – známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.0) tématu nainstalovaných distribuce/verzí.</span><span class="sxs-lookup"><span data-stu-id="207f1-287">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="207f1-288">Pokud máte potíže s instalací 1.x .NET Core na podporované distribuce systému Linux nebo verzi, naleznete [1.0.0 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) témata pro vaše nainstalovaná distribuce / verze.</span><span class="sxs-lookup"><span data-stu-id="207f1-288">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
