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
ms.openlocfilehash: 04fdf26e150e6d489c0641588563f69f24835615
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="712be-104">Předpoklady pro .NET Core v systému Linux</span><span class="sxs-lookup"><span data-stu-id="712be-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="712be-105">Tento článek ukazuje závislosti potřebné k vývoji aplikací .NET Core v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="712be-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="712be-106">Podporované distribuce systému Linux nebo verze a závislosti, které platí na dva způsoby, jak vývoj aplikací .NET Core v systému Linux:</span><span class="sxs-lookup"><span data-stu-id="712be-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="712be-107">Příkazového řádku pomocí vašeho oblíbeného editoru</span><span class="sxs-lookup"><span data-stu-id="712be-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="712be-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="712be-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a><span data-ttu-id="712be-109">Podporované verze systému Linux</span><span class="sxs-lookup"><span data-stu-id="712be-109">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="712be-110">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="712be-110">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="712be-111">Rozhraní .NET 2.0 základní považuje za jeden operační systém Linux.</span><span class="sxs-lookup"><span data-stu-id="712be-111">.NET Core 2.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="712be-112">Neexistuje jeden Linux sestavení (podle architektura procesoru) pro podporovaných distribucích systému Linux.</span><span class="sxs-lookup"><span data-stu-id="712be-112">There is a single Linux build (per chip architecture) for supported Linux distros.</span></span>

<span data-ttu-id="712be-113">NET základní 2.x je podporovaný na následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce/verze:</span><span class="sxs-lookup"><span data-stu-id="712be-113">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

 * <span data-ttu-id="712be-114">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="712be-114">Red Hat Enterprise Linux 7</span></span>
 * <span data-ttu-id="712be-115">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="712be-115">CentOS 7</span></span>
 * <span data-ttu-id="712be-116">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="712be-116">Oracle Linux 7</span></span>
 * <span data-ttu-id="712be-117">Fedora 25, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="712be-117">Fedora 25, Fedora 26</span></span>
 * <span data-ttu-id="712be-118">Debian 8.7 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="712be-118">Debian 8.7 or later versions</span></span> 
 * <span data-ttu-id="712be-119">Ubuntu č. 17.04, Ubuntu 16.04, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="712be-119">Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04</span></span>
 * <span data-ttu-id="712be-120">Linux máta 18, máta Linux 17</span><span class="sxs-lookup"><span data-stu-id="712be-120">Linux Mint 18, Linux Mint 17</span></span>
 * <span data-ttu-id="712be-121">openSUSE 42.2 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="712be-121">openSUSE 42.2 or later versions</span></span>
 * <span data-ttu-id="712be-122">SUSE Enterprise Linux (SLES) 12 SP2 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="712be-122">SUSE Enterprise Linux (SLES) 12 SP2 or later versions</span></span>

<span data-ttu-id="712be-123">V tématu [2.x .NET Core, podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="712be-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="712be-124">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="712be-124">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="712be-125">.NET core 1.x je podporována v následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce/verze:</span><span class="sxs-lookup"><span data-stu-id="712be-125">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="712be-126">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="712be-126">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="712be-127">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="712be-127">CentOS 7</span></span>
* <span data-ttu-id="712be-128">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="712be-128">Oracle Linux 7</span></span>
* <span data-ttu-id="712be-129">Fedora 24</span><span class="sxs-lookup"><span data-stu-id="712be-129">Fedora 24</span></span>
* <span data-ttu-id="712be-130">Debian 8.2 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="712be-130">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="712be-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span><span class="sxs-lookup"><span data-stu-id="712be-131">Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*</span></span>
 * <span data-ttu-id="712be-132">Ubuntu 16.10 podporuje nejnovější verze opravy .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="712be-132">Ubuntu 16.10 is supported by the latest patch release of .NET Core 1.1</span></span>
* <span data-ttu-id="712be-133">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="712be-133">Linux Mint 17</span></span>
* <span data-ttu-id="712be-134">openSUSE 42,1 nebo novější verze (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="712be-134">openSUSE 42.1 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="712be-135">V tématu [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="712be-135">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="712be-136">Linux distribuční závislosti</span><span class="sxs-lookup"><span data-stu-id="712be-136">Linux distribution dependencies</span></span>

<span data-ttu-id="712be-137">Následující by měla být příklady.</span><span class="sxs-lookup"><span data-stu-id="712be-137">The following are intended to be examples.</span></span> <span data-ttu-id="712be-138">Přesné verze a názvy se mohou mírně lišit na Linux distribuční výběru.</span><span class="sxs-lookup"><span data-stu-id="712be-138">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="712be-139">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="712be-139">Ubuntu</span></span>

<span data-ttu-id="712be-140">Ubuntu distribuce vyžadovat nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="712be-140">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="712be-141">libunwind8</span><span class="sxs-lookup"><span data-stu-id="712be-141">libunwind8</span></span>
* <span data-ttu-id="712be-142">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="712be-142">liblttng-ust0</span></span>
* <span data-ttu-id="712be-143">libcurl3</span><span class="sxs-lookup"><span data-stu-id="712be-143">libcurl3</span></span>
* <span data-ttu-id="712be-144">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="712be-144">libssl1.0.0</span></span>
* <span data-ttu-id="712be-145">libuuid1</span><span class="sxs-lookup"><span data-stu-id="712be-145">libuuid1</span></span>
* <span data-ttu-id="712be-146">libkrb5</span><span class="sxs-lookup"><span data-stu-id="712be-146">libkrb5</span></span>
* <span data-ttu-id="712be-147">zlib1g</span><span class="sxs-lookup"><span data-stu-id="712be-147">zlib1g</span></span>
* <span data-ttu-id="712be-148">libicu52 (pro 14.X)</span><span class="sxs-lookup"><span data-stu-id="712be-148">libicu52 (for 14.X)</span></span>
* <span data-ttu-id="712be-149">libicu55 (pro 16.X)</span><span class="sxs-lookup"><span data-stu-id="712be-149">libicu55 (for 16.X)</span></span>
* <span data-ttu-id="712be-150">libicu57 (pro 17.X)</span><span class="sxs-lookup"><span data-stu-id="712be-150">libicu57 (for 17.X)</span></span>

### <a name="centos"></a><span data-ttu-id="712be-151">CentOS</span><span class="sxs-lookup"><span data-stu-id="712be-151">CentOS</span></span>

<span data-ttu-id="712be-152">Distribuce centOS vyžadovat nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="712be-152">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="712be-153">libunwind</span><span class="sxs-lookup"><span data-stu-id="712be-153">libunwind</span></span>
* <span data-ttu-id="712be-154">Upravit lttng</span><span class="sxs-lookup"><span data-stu-id="712be-154">lttng-ust</span></span>
* <span data-ttu-id="712be-155">libcurl</span><span class="sxs-lookup"><span data-stu-id="712be-155">libcurl</span></span>
* <span data-ttu-id="712be-156">knihovny OpenSSL</span><span class="sxs-lookup"><span data-stu-id="712be-156">openssl-libs</span></span>
* <span data-ttu-id="712be-157">libuuid</span><span class="sxs-lookup"><span data-stu-id="712be-157">libuuid</span></span>
* <span data-ttu-id="712be-158">krb5 knihovny</span><span class="sxs-lookup"><span data-stu-id="712be-158">krb5-libs</span></span>
* <span data-ttu-id="712be-159">libicu</span><span class="sxs-lookup"><span data-stu-id="712be-159">libicu</span></span>
* <span data-ttu-id="712be-160">zlib</span><span class="sxs-lookup"><span data-stu-id="712be-160">zlib</span></span>

<span data-ttu-id="712be-161">Další informace o závislostech najdete v tématu [aplikace Self-contained Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="712be-161">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="712be-162">Instalování závislostí .NET Core s nativní instalační programy</span><span class="sxs-lookup"><span data-stu-id="712be-162">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="712be-163">.NET core, které jsou k dispozici pro nativní instalační programy podporované distribuce systému Linux nebo verze.</span><span class="sxs-lookup"><span data-stu-id="712be-163">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="712be-164">Nativní instalační programy vyžadují správce (sudo) přístup k serveru.</span><span class="sxs-lookup"><span data-stu-id="712be-164">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="712be-165">Výhodou použití nativní instalační program je, že jsou nainstalovány všechny závislosti nativní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="712be-165">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="712be-166">Nativní instalační programy také nainstalovat celý systém .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="712be-166">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="712be-167">V systému Linux existují dvě možnosti balíček Instalační služby:</span><span class="sxs-lookup"><span data-stu-id="712be-167">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="712be-168">Pomocí Správce balíčků na základě informačního kanálu, jako například výstižný get pro Ubuntu nebo yum pro CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="712be-168">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="712be-169">Použití balíčků, sami bázi DEB nebo ot. / min.</span><span class="sxs-lookup"><span data-stu-id="712be-169">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="712be-170">Skriptování nainstaluje s skript instalačního programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="712be-170">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="712be-171">`dotnet-install` Skripty se používají k provedení instalace bez oprávnění správce nástrojů rozhraní příkazového řádku a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="712be-171">The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="712be-172">Si můžete stáhnout skript z: https://dot.net/v1/dotnet-install.sh</span><span class="sxs-lookup"><span data-stu-id="712be-172">You can download the script from: https://dot.net/v1/dotnet-install.sh</span></span>

<span data-ttu-id="712be-173">Skript bash instalačního programu se používá v automatizace scénáře a instalace bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="712be-173">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="712be-174">Tento skript také přečte přepínače prostředí PowerShell, takže je můžete používat pomocí skriptu v systémech Linux nebo OS X.</span><span class="sxs-lookup"><span data-stu-id="712be-174">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="712be-175">Před spuštěním skriptu nainstalujte požadované [závislosti](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="712be-175">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="712be-176">Instalace .NET Core pro Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="712be-176">Install .NET Core for Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="712be-177">Instalace .NET Core na RHEL 7:</span><span class="sxs-lookup"><span data-stu-id="712be-177">To install .NET Core on RHEL 7:</span></span>

1. <span data-ttu-id="712be-178">Povolte kanál Red Hat .NET, který je k dispozici v rámci svého předplatného RHEL 7.</span><span class="sxs-lookup"><span data-stu-id="712be-178">Enable the Red Hat .NET channel, available under your RHEL 7 subscription.</span></span>
    * <span data-ttu-id="712be-179">Red Hat Enterprise 7 Server použijte:</span><span class="sxs-lookup"><span data-stu-id="712be-179">For Red Hat Enterprise 7 Server, use:</span></span>
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * <span data-ttu-id="712be-180">Red Hat Enterprise 7 pracovní stanice použijte:</span><span class="sxs-lookup"><span data-stu-id="712be-180">For Red Hat Enterprise 7 Workstation, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * <span data-ttu-id="712be-181">Red Hat Enterprise 7 HPC výpočetní uzel použijte:</span><span class="sxs-lookup"><span data-stu-id="712be-181">For Red Hat Enterprise 7 HPC Compute Node, use:</span></span>
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. <span data-ttu-id="712be-182">Nainstalujte nástroj scl.</span><span class="sxs-lookup"><span data-stu-id="712be-182">Install the scl tool.</span></span>

    ```bash
    yum install scl-utils
    ```
    
3. <span data-ttu-id="712be-183">Instalace .NET Core</span><span class="sxs-lookup"><span data-stu-id="712be-183">Install .NET Core</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="712be-184">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="712be-184">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="712be-185">Nainstalujte základní rozhraní .NET 2.0 SDK a modulu Runtime:</span><span class="sxs-lookup"><span data-stu-id="712be-185">Install .NET Core 2.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnet20
   ```

<span data-ttu-id="712be-186">Povolte .NET Core SDK nebo modul Runtime 2.0 pro vaše prostředí:</span><span class="sxs-lookup"><span data-stu-id="712be-186">Enable .NET Core 2.0 SDK/Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="712be-187">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="712be-187">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="712be-188">**.NET core 1.1**</span><span class="sxs-lookup"><span data-stu-id="712be-188">**.NET Core 1.1**</span></span>

<span data-ttu-id="712be-189">Instalace .NET Core 1.1 SDK a modulu Runtime:</span><span class="sxs-lookup"><span data-stu-id="712be-189">Install .NET Core 1.1 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore11
   ```

<span data-ttu-id="712be-190">Povolte .NET Core 1.1 SDK a modulu Runtime pro vaše prostředí:</span><span class="sxs-lookup"><span data-stu-id="712be-190">Enable .NET Core 1.1 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

<span data-ttu-id="712be-191">**.NET core 1.0**</span><span class="sxs-lookup"><span data-stu-id="712be-191">**.NET Core 1.0**</span></span>

<span data-ttu-id="712be-192">Instalace rozhraní .NET základní 1.0 SDK a modulu Runtime:</span><span class="sxs-lookup"><span data-stu-id="712be-192">Install .NET Core 1.0 SDK and Runtime:</span></span>

   ```bash
   yum install rh-dotnetcore10
   ```

<span data-ttu-id="712be-193">Povolte .NET Core 1.0 SDK a modulu Runtime pro vaše prostředí:</span><span class="sxs-lookup"><span data-stu-id="712be-193">Enable .NET Core 1.0 SDK and Runtime for your environment:</span></span>

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. <span data-ttu-id="712be-194">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="712be-194">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

     ```bash
     dotnet --version
     ```

<span data-ttu-id="712be-195">Red Hat .NET kanál přístup registrace pomoc najdete v tématu [kapitoly 1 .NET Core 1.1 – Příručka Začínáme](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) v Red Hat.</span><span class="sxs-lookup"><span data-stu-id="712be-195">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a><span data-ttu-id="712be-196">Instalace .NET Core pro Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 a Linux máta 17 18 máta Linux (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="712be-196">Install .NET Core for Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 & Linux Mint 17, Linux Mint 18 (64 bit)</span></span>

1. <span data-ttu-id="712be-197">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="712be-197">Remove any **previous preview** versions of .NET Core from your system.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="712be-198">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="712be-198">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="712be-199">Registrovat Microsoft Product key jako důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="712be-199">Register the Microsoft Product key as trusted.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. <span data-ttu-id="712be-200">Nastavte balíček hostitele požadovanou verzi kanálu.</span><span class="sxs-lookup"><span data-stu-id="712be-200">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="712be-201">**Ubuntu č. 17.04**</span><span class="sxs-lookup"><span data-stu-id="712be-201">**Ubuntu 17.04**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="712be-202">**Ubuntu 16.04 / Linux máta 18**</span><span class="sxs-lookup"><span data-stu-id="712be-202">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   <span data-ttu-id="712be-203">**Ubuntu 14.04 / Linux máta 17**</span><span class="sxs-lookup"><span data-stu-id="712be-203">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. <span data-ttu-id="712be-204">Nainstalujte .NET Core.</span><span class="sxs-lookup"><span data-stu-id="712be-204">Install .NET Core.</span></span>

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="712be-205">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="712be-205">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="712be-206">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="712be-206">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="712be-207">Nastavte balíček hostitele požadovanou verzi kanálu.</span><span class="sxs-lookup"><span data-stu-id="712be-207">Set up the desired version host package feed.</span></span>

   <span data-ttu-id="712be-208">**Ubuntu 16.10**</span><span class="sxs-lookup"><span data-stu-id="712be-208">**Ubuntu 16.10**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  <span data-ttu-id="712be-209">**Ubuntu 16.04 / Linux máta 18**</span><span class="sxs-lookup"><span data-stu-id="712be-209">**Ubuntu 16.04 / Linux Mint 18**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   <span data-ttu-id="712be-210">**Ubuntu 14.04 / Linux máta 17**</span><span class="sxs-lookup"><span data-stu-id="712be-210">**Ubuntu 14.04 / Linux Mint 17**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. <span data-ttu-id="712be-211">Instalace rozhraní .NET základní 1.x na Ubuntu nebo máta Linux:</span><span class="sxs-lookup"><span data-stu-id="712be-211">Install .NET Core 1.x on Ubuntu or Linux Mint:</span></span>

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. <span data-ttu-id="712be-212">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="712be-212">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a><span data-ttu-id="712be-213">Instalace .NET Core pro Debian 8 nebo Debian 9 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="712be-213">Install .NET Core for Debian 8 or Debian 9 (64 bit)</span></span>

<span data-ttu-id="712be-214">Instalace .NET Core na Debian 8 nebo Debian 9 (64 bitů):</span><span class="sxs-lookup"><span data-stu-id="712be-214">To install .NET Core on Debian 8 or Debian 9 (64 bit):</span></span>

1. <span data-ttu-id="712be-215">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="712be-215">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="712be-216">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="712be-216">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="712be-217">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="712be-217">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="712be-218">Instalace komponent systému.</span><span class="sxs-lookup"><span data-stu-id="712be-218">Install system components.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. <span data-ttu-id="712be-219">Zaregistrujte důvěryhodné Microsoft Product key.</span><span class="sxs-lookup"><span data-stu-id="712be-219">Register the trusted Microsoft Product key.</span></span>

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. <span data-ttu-id="712be-220">Zaregistrujte Product Microsoft informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="712be-220">Register the Microsoft Product feed.</span></span>

   <span data-ttu-id="712be-221">**Debian 9 (Stretch)**</span><span class="sxs-lookup"><span data-stu-id="712be-221">**Debian 9 (Stretch)**</span></span>

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   <span data-ttu-id="712be-222">**Debian 8 (Klára)**</span><span class="sxs-lookup"><span data-stu-id="712be-222">**Debian 8 (Jessie)**</span></span>
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. <span data-ttu-id="712be-223">Nainstalujte .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="712be-223">Install .NET Core SDK.</span></span>

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. <span data-ttu-id="712be-224">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="712be-224">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. <span data-ttu-id="712be-225">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="712be-225">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="712be-226">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="712be-226">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="712be-227">Získáte požadované součásti.</span><span class="sxs-lookup"><span data-stu-id="712be-227">Get the prerequisites.</span></span>

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. <span data-ttu-id="712be-228">Stáhněte si .NET Core SDK binárních souborů (tarball).</span><span class="sxs-lookup"><span data-stu-id="712be-228">Download the .NET Core SDK binaries (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. <span data-ttu-id="712be-229">Rozbalte binární soubory .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="712be-229">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="712be-230">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="712be-230">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. <span data-ttu-id="712be-231">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="712be-231">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a><span data-ttu-id="712be-232">Instalace .NET Core pro Fedora 24, Fedora 25 nebo Fedora 26 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="712be-232">Install .NET Core for Fedora 24, Fedora 25, or Fedora 26 (64 bit)</span></span>

<span data-ttu-id="712be-233">Chcete-li nainstalovat .NET Core 2.x na Fedora 26 nebo Fedora 25 nebo .NET Core 1.x na Fedora 24:</span><span class="sxs-lookup"><span data-stu-id="712be-233">To install .NET Core 2.x on Fedora 26 or Fedora 25, or .NET Core 1.x on Fedora 24:</span></span>

1. <span data-ttu-id="712be-234">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="712be-234">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="712be-235">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="712be-235">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="712be-236">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="712be-236">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="712be-237">**Fedora 26 nebo Fedora 25**</span><span class="sxs-lookup"><span data-stu-id="712be-237">**Fedora 26 or Fedora 25**</span></span>

2. <span data-ttu-id="712be-238">Zaregistrujte klíč podpisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="712be-238">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="712be-239">Přidání produktu dotnet informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="712be-239">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="712be-240">Nainstalujte základní rozhraní .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="712be-240">Install the .NET Core SDK.</span></span>

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="712be-241">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="712be-241">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="712be-242">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="712be-242">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="712be-243">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="712be-243">**Fedora 24**</span></span>

2. <span data-ttu-id="712be-244">Získáte požadované součásti.</span><span class="sxs-lookup"><span data-stu-id="712be-244">Get the prerequisites.</span></span>

   ```bash
   sudo dnf install libunwind libicu
   ```

3. <span data-ttu-id="712be-245">Stáhněte si .NET Core SDK binárního souboru (tarball).</span><span class="sxs-lookup"><span data-stu-id="712be-245">Download the .NET Core SDK binary  (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. <span data-ttu-id="712be-246">Rozbalte binární soubory .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="712be-246">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="712be-247">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="712be-247">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="712be-248">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="712be-248">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a><span data-ttu-id="712be-249">Instalace .NET Core pro CentOS 7.1 (64 bitů) a Oracle Linux 7.1 (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="712be-249">Install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit)</span></span>

<span data-ttu-id="712be-250">Chcete-li nainstalovat .NET Core pro CentOS 7.1 (64 bitů) a Oracle Linux 7.1 (64 bitů):</span><span class="sxs-lookup"><span data-stu-id="712be-250">To install .NET Core for CentOS 7.1 (64 bit) & Oracle Linux 7.1 (64 bit):</span></span>

1. <span data-ttu-id="712be-251">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="712be-251">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="712be-252">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="712be-252">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="712be-253">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="712be-253">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="712be-254">Zaregistrujte klíč podpisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="712be-254">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="712be-255">Přidejte Product Microsoft informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="712be-255">Add the Microsoft Product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. <span data-ttu-id="712be-256">Nainstalujte základní rozhraní .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="712be-256">Install the .NET Core SDK.</span></span>

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="712be-257">Přidejte do své CESTĚ dotnet.</span><span class="sxs-lookup"><span data-stu-id="712be-257">Add dotnet to your PATH</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="712be-258">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="712be-258">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="712be-259">Získáte požadované součásti.</span><span class="sxs-lookup"><span data-stu-id="712be-259">Get the prerequisites.</span></span>

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. <span data-ttu-id="712be-260">Stáhněte si .NET Core SDK binárního souboru (tarball).</span><span class="sxs-lookup"><span data-stu-id="712be-260">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. <span data-ttu-id="712be-261">Rozbalte binární soubory .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="712be-261">Extract the .NET Core SDK binaries.</span></span>

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="712be-262">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="712be-262">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. <span data-ttu-id="712be-263">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="712be-263">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a><span data-ttu-id="712be-264">Instalace .NET Core pro SUSE Linux Enterprise Server (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="712be-264">Install .NET Core for SUSE Linux Enterprise Server (64 bit)</span></span>

<span data-ttu-id="712be-265">Chcete-li nainstalovat .NET Core 2.x pro SUSE Linux Enterprise Server (SLES) 12 SP2 (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="712be-265">To install .NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):</span></span>

1. <span data-ttu-id="712be-266">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="712be-266">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="712be-267">Přidání produktu dotnet informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="712be-267">Add the dotnet product feed.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. <span data-ttu-id="712be-268">Nainstalujte základní rozhraní .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="712be-268">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. <span data-ttu-id="712be-269">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="712be-269">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. <span data-ttu-id="712be-270">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="712be-270">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a><span data-ttu-id="712be-271">Instalace .NET Core pro openSUSE (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="712be-271">Install .NET Core for openSUSE (64 bit)</span></span>

<span data-ttu-id="712be-272">Chcete-li nainstalovat .NET Core 2.x openSUSE nebo .NET Core 1.x pro openSUSE (64 bitů):</span><span class="sxs-lookup"><span data-stu-id="712be-272">To install .NET Core 2.x for openSUSE or .NET Core 1.x for openSUSE (64 bit):</span></span>

1. <span data-ttu-id="712be-273">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="712be-273">Remove any **previous preview** versions of .NET Core from your system.</span></span>

> [!NOTE]
> <span data-ttu-id="712be-274">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="712be-274">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="712be-275">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="712be-275">.NET Core 2.x</span></span>](#tab/netcore2x)

2. <span data-ttu-id="712be-276">Zaregistrujte klíč podpisu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="712be-276">Register the Microsoft signature key.</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="712be-277">Přidání produktu dotnet informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="712be-277">Add the dotnet product feed.</span></span>

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. <span data-ttu-id="712be-278">Nainstalujte základní rozhraní .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="712be-278">Install the .NET Core SDK.</span></span>

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. <span data-ttu-id="712be-279">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="712be-279">Add dotnet to your PATH.</span></span>

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="712be-280">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="712be-280">.NET Core 1.x</span></span>](#tab/netcore1x)

2. <span data-ttu-id="712be-281">Získáte požadované součásti.</span><span class="sxs-lookup"><span data-stu-id="712be-281">Get the prerequisites.</span></span>

   ```bash
   sudo zypper install libunwind libicu
   ```

3. <span data-ttu-id="712be-282">Stáhněte si .NET Core SDK binárního souboru (tarball).</span><span class="sxs-lookup"><span data-stu-id="712be-282">Download the .NET Core SDK binary (tarball).</span></span>

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. <span data-ttu-id="712be-283">Rozbalte binární soubory .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="712be-283">Extract the .NET Core SDK binaries.</span></span>
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. <span data-ttu-id="712be-284">Přidejte CESTU k dotnet.</span><span class="sxs-lookup"><span data-stu-id="712be-284">Add dotnet to your PATH.</span></span>

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. <span data-ttu-id="712be-285">Spustit `dotnet --version` příkaz k prokázání instalace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="712be-285">Run the `dotnet --version` command to prove the installation succeeded.</span></span>

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> <span data-ttu-id="712be-286">Pokud máte potíže s instalací 2.x .NET Core na podporované distribuce systému Linux nebo verzi, naleznete [2.0 – známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.0) tématu nainstalovaných distribuce/verzí.</span><span class="sxs-lookup"><span data-stu-id="712be-286">If you have problems with the .NET Core 2.x installation on a supported Linux distribution/version, consult the [2.0 Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for your installed distributions/versions.</span></span> 
>
> <span data-ttu-id="712be-287">Pokud máte potíže s instalací 1.x .NET Core na podporované distribuce systému Linux nebo verzi, naleznete [1.0.0 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) témata pro vaše nainstalovaná distribuce / verze.</span><span class="sxs-lookup"><span data-stu-id="712be-287">If you have problems with the .NET Core 1.x installation on a supported Linux distribution/version, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics for your installed distributions/versions.</span></span>
