---
title: Předpoklady pro .NET Core v systému Linux
description: Podporované verze systému Linux a závislostí .NET Core k vývoji, nasazení a spouštění aplikací .NET Core na počítače se systémem Linux.
keywords: Debian, ubuntu Linux, .NET, .NET core RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 04/12/2018
ms.topic: conceptual
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload:
- dotnetcore
ms.openlocfilehash: 37dc4f25b6c4915971bc79931a105474fcd43670
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="d91ca-104">Předpoklady pro .NET Core v systému Linux</span><span class="sxs-lookup"><span data-stu-id="d91ca-104">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="d91ca-105">Tento článek ukazuje závislosti potřebné k vývoji aplikací .NET Core v systému Linux.</span><span class="sxs-lookup"><span data-stu-id="d91ca-105">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="d91ca-106">Podporované distribuce systému Linux nebo verze a závislosti, které platí na dva způsoby, jak vývoj aplikací .NET Core v systému Linux:</span><span class="sxs-lookup"><span data-stu-id="d91ca-106">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="d91ca-107">Příkazového řádku pomocí vašeho oblíbeného editoru</span><span class="sxs-lookup"><span data-stu-id="d91ca-107">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="d91ca-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d91ca-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="d91ca-109">Balíček .NET Core SDK není nutné pro produkční servery nebo prostředí.</span><span class="sxs-lookup"><span data-stu-id="d91ca-109">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="d91ca-110">Pouze balíček .NET Core runtime je potřeba pro aplikace nasazené do produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="d91ca-110">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="d91ca-111">Nasazení na .NET Core runtime s aplikacemi v rámci samostatná nasazení, ale musí být nasazený pro závislé na Framework nasazených aplikací samostatně.</span><span class="sxs-lookup"><span data-stu-id="d91ca-111">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="d91ca-112">Další informace o typech nasazení závislé na framework a nezávislý najdete v tématu [nasazení aplikace .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d91ca-112">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="d91ca-113">Viz také [aplikace Self-contained Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) konkrétní pokyny.</span><span class="sxs-lookup"><span data-stu-id="d91ca-113">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="d91ca-114">Podporované verze systému Linux</span><span class="sxs-lookup"><span data-stu-id="d91ca-114">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d91ca-115">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-115">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="d91ca-116">.NET core 2.x vyhodnotí jako jeden operační systém Linux.</span><span class="sxs-lookup"><span data-stu-id="d91ca-116">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="d91ca-117">Neexistuje jeden Linux sestavení (podle architektura procesoru) podporované distribuce systému Linux.</span><span class="sxs-lookup"><span data-stu-id="d91ca-117">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="d91ca-118">NET základní 2.x je podporovaný na následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce/verze:</span><span class="sxs-lookup"><span data-stu-id="d91ca-118">NET Core 2.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="d91ca-119">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="d91ca-119">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="d91ca-120">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d91ca-120">CentOS 7</span></span>
* <span data-ttu-id="d91ca-121">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="d91ca-121">Oracle Linux 7</span></span>
* <span data-ttu-id="d91ca-122">Fedora 27, 26</span><span class="sxs-lookup"><span data-stu-id="d91ca-122">Fedora 27, 26</span></span>
* <span data-ttu-id="d91ca-123">Debian 9 8.7 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="d91ca-123">Debian 9, 8.7 or later versions</span></span>
* <span data-ttu-id="d91ca-124">Ubuntu 17.10, 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="d91ca-124">Ubuntu 17.10, 16.04, 14.04</span></span>
* <span data-ttu-id="d91ca-125">Linux máta 18, 17</span><span class="sxs-lookup"><span data-stu-id="d91ca-125">Linux Mint 18, 17</span></span>
* <span data-ttu-id="d91ca-126">openSUSE 42.3 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="d91ca-126">openSUSE 42.3 or later versions</span></span>
* <span data-ttu-id="d91ca-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 nebo novější</span><span class="sxs-lookup"><span data-stu-id="d91ca-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later</span></span>

<span data-ttu-id="d91ca-128">V tématu [2.x .NET Core, podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, distribucí a verzí, nedostatek verze podporu operačního systému a odkazy na zásady životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="d91ca-128">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d91ca-129">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-129">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d91ca-130">.NET core 1.x je podporována v následujících Linux 64-bit (`x86_64` nebo `amd64`) distribuce/verze:</span><span class="sxs-lookup"><span data-stu-id="d91ca-130">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="d91ca-131">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="d91ca-131">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="d91ca-132">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="d91ca-132">CentOS 7</span></span>
* <span data-ttu-id="d91ca-133">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="d91ca-133">Oracle Linux 7</span></span>
* <span data-ttu-id="d91ca-134">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="d91ca-134">Fedora 26</span></span>
* <span data-ttu-id="d91ca-135">Debian 8.2 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="d91ca-135">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="d91ca-136">Ubuntu 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="d91ca-136">Ubuntu 16.04, 14.04</span></span>
* <span data-ttu-id="d91ca-137">Linux máta 18, 17</span><span class="sxs-lookup"><span data-stu-id="d91ca-137">Linux Mint 18, 17</span></span>
* <span data-ttu-id="d91ca-138">openSUSE 42.3 nebo novější verze (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="d91ca-138">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="d91ca-139">V tématu [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="d91ca-139">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="d91ca-140">Linux distribuční závislosti</span><span class="sxs-lookup"><span data-stu-id="d91ca-140">Linux distribution dependencies</span></span>

<span data-ttu-id="d91ca-141">Následující by měla být příklady.</span><span class="sxs-lookup"><span data-stu-id="d91ca-141">The following are intended to be examples.</span></span> <span data-ttu-id="d91ca-142">Přesné verze a názvy se mohou mírně lišit na Linux distribuční výběru.</span><span class="sxs-lookup"><span data-stu-id="d91ca-142">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="d91ca-143">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d91ca-143">Ubuntu</span></span>

<span data-ttu-id="d91ca-144">Ubuntu distribuce vyžadovat nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="d91ca-144">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="d91ca-145">libunwind8</span><span class="sxs-lookup"><span data-stu-id="d91ca-145">libunwind8</span></span>
* <span data-ttu-id="d91ca-146">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="d91ca-146">liblttng-ust0</span></span>
* <span data-ttu-id="d91ca-147">libcurl3</span><span class="sxs-lookup"><span data-stu-id="d91ca-147">libcurl3</span></span>
* <span data-ttu-id="d91ca-148">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="d91ca-148">libssl1.0.0</span></span>
* <span data-ttu-id="d91ca-149">libuuid1</span><span class="sxs-lookup"><span data-stu-id="d91ca-149">libuuid1</span></span>
* <span data-ttu-id="d91ca-150">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="d91ca-150">libkrb5-3</span></span>
* <span data-ttu-id="d91ca-151">zlib1g</span><span class="sxs-lookup"><span data-stu-id="d91ca-151">zlib1g</span></span>
* <span data-ttu-id="d91ca-152">libicu52 (pro 14.x)</span><span class="sxs-lookup"><span data-stu-id="d91ca-152">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="d91ca-153">libicu55 (pro 16.x)</span><span class="sxs-lookup"><span data-stu-id="d91ca-153">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="d91ca-154">libicu57 (pro 17.x)</span><span class="sxs-lookup"><span data-stu-id="d91ca-154">libicu57 (for 17.x)</span></span>

### <a name="centos"></a><span data-ttu-id="d91ca-155">CentOS</span><span class="sxs-lookup"><span data-stu-id="d91ca-155">CentOS</span></span>

<span data-ttu-id="d91ca-156">Distribuce centOS vyžadovat nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="d91ca-156">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="d91ca-157">libunwind</span><span class="sxs-lookup"><span data-stu-id="d91ca-157">libunwind</span></span>
* <span data-ttu-id="d91ca-158">Upravit lttng</span><span class="sxs-lookup"><span data-stu-id="d91ca-158">lttng-ust</span></span>
* <span data-ttu-id="d91ca-159">libcurl</span><span class="sxs-lookup"><span data-stu-id="d91ca-159">libcurl</span></span>
* <span data-ttu-id="d91ca-160">knihovny OpenSSL</span><span class="sxs-lookup"><span data-stu-id="d91ca-160">openssl-libs</span></span>
* <span data-ttu-id="d91ca-161">libuuid</span><span class="sxs-lookup"><span data-stu-id="d91ca-161">libuuid</span></span>
* <span data-ttu-id="d91ca-162">krb5 knihovny</span><span class="sxs-lookup"><span data-stu-id="d91ca-162">krb5-libs</span></span>
* <span data-ttu-id="d91ca-163">libicu</span><span class="sxs-lookup"><span data-stu-id="d91ca-163">libicu</span></span>
* <span data-ttu-id="d91ca-164">zlib</span><span class="sxs-lookup"><span data-stu-id="d91ca-164">zlib</span></span>

<span data-ttu-id="d91ca-165">Další informace o závislostech najdete v tématu [aplikace Self-contained Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="d91ca-165">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="d91ca-166">Instalování závislostí .NET Core s nativní instalační programy</span><span class="sxs-lookup"><span data-stu-id="d91ca-166">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="d91ca-167">.NET core, které jsou k dispozici pro nativní instalační programy podporované distribuce systému Linux nebo verze.</span><span class="sxs-lookup"><span data-stu-id="d91ca-167">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="d91ca-168">Nativní instalační programy vyžadují správce (sudo) přístup k serveru.</span><span class="sxs-lookup"><span data-stu-id="d91ca-168">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="d91ca-169">Výhodou použití nativní instalační program je, že jsou nainstalovány všechny závislosti nativní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d91ca-169">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="d91ca-170">Nativní instalační programy také nainstalovat celý systém .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d91ca-170">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="d91ca-171">V systému Linux existují dvě možnosti balíček Instalační služby:</span><span class="sxs-lookup"><span data-stu-id="d91ca-171">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="d91ca-172">Pomocí Správce balíčků na základě informačního kanálu, jako například výstižný get pro Ubuntu nebo yum pro CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="d91ca-172">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="d91ca-173">Použití balíčků, sami bázi DEB nebo ot. / min.</span><span class="sxs-lookup"><span data-stu-id="d91ca-173">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="d91ca-174">Skriptování nainstaluje s skript instalačního programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="d91ca-174">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="d91ca-175">[Skriptů instalace dotnet](./tools/dotnet-install-script.md) se používají k provedení instalace bez oprávnění správce nástrojů rozhraní příkazového řádku a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d91ca-175">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="d91ca-176">Si můžete stáhnout skript z [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).</span><span class="sxs-lookup"><span data-stu-id="d91ca-176">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="d91ca-177">Skript bash instalačního programu se používá v automatizace scénáře a instalace bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="d91ca-177">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="d91ca-178">Tento skript také přečte přepínače prostředí PowerShell, takže je můžete používat pomocí skriptu v systémech Linux nebo OS X.</span><span class="sxs-lookup"><span data-stu-id="d91ca-178">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a><span data-ttu-id="d91ca-179">Instalace .NET Core pro podporované verze systému Red Hat Enterprise Linux (RHEL)</span><span class="sxs-lookup"><span data-stu-id="d91ca-179">Install .NET Core for supported Red Hat Enterprise Linux (RHEL) versions</span></span>

<span data-ttu-id="d91ca-180">Instalace .NET Core na podporovaných verzích systému RHEL:</span><span class="sxs-lookup"><span data-stu-id="d91ca-180">To install .NET Core on supported RHEL versions:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d91ca-181">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-181">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="d91ca-182">Zajistěte, abyste měli nejnovější informace o instalaci, postupujte podle [pokyny 2.x SDK a instalační program modulu Runtime .NET Core](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current) pro podporované verze systému RHEL.</span><span class="sxs-lookup"><span data-stu-id="d91ca-182">To ensure you have the latest installation information, follow the [.NET Core 2.x SDK and Runtime Installer instructions](https://www.microsoft.com/net/download/linux-package-manager/rhel/sdk-current) for supported RHEL versions.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d91ca-183">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-183">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="d91ca-184">**.NET core 1.1**</span><span class="sxs-lookup"><span data-stu-id="d91ca-184">**.NET Core 1.1**</span></span>

1. <span data-ttu-id="d91ca-185">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-185">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2.  <span data-ttu-id="d91ca-186">Nejnovější 1.1 .NET Core na informace o instalaci Red Hat Enterprise Linux, najdete v části [.NET Core 1.1 Průvodce Začínáme](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)</span><span class="sxs-lookup"><span data-stu-id="d91ca-186">For the latest .NET Core 1.1 on Red Hat Enterprise Linux installation information, see [the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)</span></span>
     
<span data-ttu-id="d91ca-187">**.NET core 1.0**</span><span class="sxs-lookup"><span data-stu-id="d91ca-187">**.NET Core 1.0**</span></span>

1. <span data-ttu-id="d91ca-188">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-188">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2.  <span data-ttu-id="d91ca-189">Nejnovější 1.0 .NET Core na informace o instalaci Red Hat Enterprise Linux, najdete v části [.NET Core 1.0 Průvodce Začínáme](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)</span><span class="sxs-lookup"><span data-stu-id="d91ca-189">For the latest .NET Core 1.0 on Red Hat Enterprise Linux installation information, see [the .NET Core 1.0 Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)</span></span>

<span data-ttu-id="d91ca-190">Red Hat .NET kanál přístup registrace pomoc najdete v tématu [kapitoly 1 .NET Core 1.1 – Příručka Začínáme](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) v Red Hat.</span><span class="sxs-lookup"><span data-stu-id="d91ca-190">For Red Hat .NET channel access registration help, see [Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) at Red Hat.</span></span>

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a><span data-ttu-id="d91ca-191">Instalace .NET Core pro podporované Ubuntu Linux máta distribuce/verze a (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="d91ca-191">Install .NET Core for supported Ubuntu and Linux Mint distributions/versions (64 bit)</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d91ca-192">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-192">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="d91ca-193">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-193">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d91ca-194">Nainstalujte .NET Core 2.x na podporované Ubuntu a Linux máta distribuce/verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-194">Install .NET Core 2.x on supported Ubuntu and Linux Mint distributions/versions (64 bit):</span></span>

<span data-ttu-id="d91ca-195">**.NET core 2.0**</span><span class="sxs-lookup"><span data-stu-id="d91ca-195">**.NET Core 2.0**</span></span>

|<span data-ttu-id="d91ca-196">Moduly runtime nebo sady SDK</span><span class="sxs-lookup"><span data-stu-id="d91ca-196">Runtimes / SDKs</span></span>          |<span data-ttu-id="d91ca-197">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="d91ca-197">Ubuntu 17.10</span></span>  |<span data-ttu-id="d91ca-198">Ubuntu 16.04 / Linux máta 18</span><span class="sxs-lookup"><span data-stu-id="d91ca-198">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="d91ca-199">Ubuntu 14.04 / Linux máta 17</span><span class="sxs-lookup"><span data-stu-id="d91ca-199">Ubuntu 14.04 / Linux Mint 17</span></span>|
|-------------------------|--------------|----------------------------|----------------------------|
|<span data-ttu-id="d91ca-200">.NET core Runtime 2.0.6</span><span class="sxs-lookup"><span data-stu-id="d91ca-200">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="d91ca-201">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-201">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[<span data-ttu-id="d91ca-202">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-202">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[<span data-ttu-id="d91ca-203">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-203">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|<span data-ttu-id="d91ca-204">.NET core Runtime 2.0.5</span><span class="sxs-lookup"><span data-stu-id="d91ca-204">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="d91ca-205">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-205">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[<span data-ttu-id="d91ca-206">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-206">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[<span data-ttu-id="d91ca-207">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-207">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|<span data-ttu-id="d91ca-208">.NET core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="d91ca-208">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="d91ca-209">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-209">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[<span data-ttu-id="d91ca-210">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-210">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[<span data-ttu-id="d91ca-211">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-211">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|<span data-ttu-id="d91ca-212">.NET core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="d91ca-212">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="d91ca-213">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-213">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[<span data-ttu-id="d91ca-214">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-214">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[<span data-ttu-id="d91ca-215">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-215">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |

<span data-ttu-id="d91ca-216">**.NET core 2.1**</span><span class="sxs-lookup"><span data-stu-id="d91ca-216">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d91ca-217">Chcete-li použít pomocí sady Visual Studio .NET Core 2.1, je potřeba [instalaci Visual Studia 2017 15.7 Preview 1 nebo novější](https://www.visualstudio.com/vs/preview).</span><span class="sxs-lookup"><span data-stu-id="d91ca-217">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="d91ca-218">Moduly runtime nebo sady SDK</span><span class="sxs-lookup"><span data-stu-id="d91ca-218">Runtimes / SDKs</span></span>                  |<span data-ttu-id="d91ca-219">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="d91ca-219">Ubuntu 17.10</span></span>    |<span data-ttu-id="d91ca-220">Ubuntu 16.04 / Linux máta 18</span><span class="sxs-lookup"><span data-stu-id="d91ca-220">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="d91ca-221">Ubuntu 14.04 / Linux máta 17</span><span class="sxs-lookup"><span data-stu-id="d91ca-221">Ubuntu 14.04 / Linux Mint 17</span></span>|
|---------------------------------|----------------|----------------------------|----------------------------|
|<span data-ttu-id="d91ca-222">.NET core Runtime 2.1.0-preview1</span><span class="sxs-lookup"><span data-stu-id="d91ca-222">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="d91ca-223">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-223">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0-preview1)|[<span data-ttu-id="d91ca-224">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-224">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0-preview1)            |[<span data-ttu-id="d91ca-225">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-225">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0-preview1)            |
|<span data-ttu-id="d91ca-226">.NET core SDK 2.1.300-preview1</span><span class="sxs-lookup"><span data-stu-id="d91ca-226">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="d91ca-227">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-227">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300-preview1)|[<span data-ttu-id="d91ca-228">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-228">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300-preview1)            |[<span data-ttu-id="d91ca-229">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-229">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300-preview1)            |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d91ca-230">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-230">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="d91ca-231">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-231">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d91ca-232">Nainstalujte .NET Core 1.x na podporované Ubuntu a Linux máta distribuce/verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-232">Install .NET Core 1.x on supported Ubuntu and Linux Mint distributions/versions (64 bit):</span></span>

| <span data-ttu-id="d91ca-233">Moduly runtime nebo sady SDK</span><span class="sxs-lookup"><span data-stu-id="d91ca-233">Runtimes / SDKs</span></span>         |<span data-ttu-id="d91ca-234">Ubuntu 16.04 / Linux máta 18</span><span class="sxs-lookup"><span data-stu-id="d91ca-234">Ubuntu 16.04 / Linux Mint 18</span></span>|<span data-ttu-id="d91ca-235">Ubuntu 14.04 / Linux máta 17</span><span class="sxs-lookup"><span data-stu-id="d91ca-235">Ubuntu 14.04 / Linux Mint 17</span></span>|
|-------------------------|----------------------------|----------------------------|
|<span data-ttu-id="d91ca-236">.NET core Runtime 1.1.7</span><span class="sxs-lookup"><span data-stu-id="d91ca-236">.NET Core Runtime 1.1.7</span></span>  |[<span data-ttu-id="d91ca-237">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-237">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="d91ca-238">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-238">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="d91ca-239">.NET core Runtime 1.1.6</span><span class="sxs-lookup"><span data-stu-id="d91ca-239">.NET Core Runtime 1.1.6</span></span>  |[<span data-ttu-id="d91ca-240">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-240">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="d91ca-241">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-241">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="d91ca-242">.NET core Runtime 1.0.10</span><span class="sxs-lookup"><span data-stu-id="d91ca-242">.NET Core Runtime 1.0.10</span></span> |[<span data-ttu-id="d91ca-243">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-243">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="d91ca-244">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-244">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="d91ca-245">.NET core Runtime 1.0.9</span><span class="sxs-lookup"><span data-stu-id="d91ca-245">.NET Core Runtime 1.0.9</span></span>  |[<span data-ttu-id="d91ca-246">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-246">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="d91ca-247">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-247">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="d91ca-248">.NET core SDK bodem 1.1.8</span><span class="sxs-lookup"><span data-stu-id="d91ca-248">.NET Core SDK 1.1.8</span></span>      |[<span data-ttu-id="d91ca-249">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-249">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="d91ca-250">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-250">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="d91ca-251">.NET core SDK 1.1.7</span><span class="sxs-lookup"><span data-stu-id="d91ca-251">.NET Core SDK 1.1.7</span></span>      |[<span data-ttu-id="d91ca-252">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-252">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="d91ca-253">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-253">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="d91ca-254">.NET core SDK 1.0.4</span><span class="sxs-lookup"><span data-stu-id="d91ca-254">.NET Core SDK 1.0.4</span></span>      |[<span data-ttu-id="d91ca-255">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-255">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="d91ca-256">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-256">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|<span data-ttu-id="d91ca-257">.NET core SDK 1.0.1</span><span class="sxs-lookup"><span data-stu-id="d91ca-257">.NET Core SDK 1.0.1</span></span>      |[<span data-ttu-id="d91ca-258">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-258">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[<span data-ttu-id="d91ca-259">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-259">Install link</span></span>](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a><span data-ttu-id="d91ca-260">Instalace .NET Core pro podporované verze Debian (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="d91ca-260">Install .NET Core for supported Debian versions (64 bit)</span></span>

<span data-ttu-id="d91ca-261">Instalace .NET Core na podporované Debian verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-261">To install .NET Core on supported Debian versions (64 bit):</span></span>

> [!NOTE]
> <span data-ttu-id="d91ca-262">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="d91ca-262">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d91ca-263">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-263">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="d91ca-264">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-264">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d91ca-265">Nainstalujte .NET Core 2.x na podporované Debian verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-265">Install .NET Core 2.x on supported Debian versions (64 bit):</span></span>

<span data-ttu-id="d91ca-266">**.NET core 2.0**</span><span class="sxs-lookup"><span data-stu-id="d91ca-266">**.NET Core 2.0**</span></span>

|<span data-ttu-id="d91ca-267">Moduly runtime nebo sady SDK</span><span class="sxs-lookup"><span data-stu-id="d91ca-267">Runtimes / SDKs</span></span>          |<span data-ttu-id="d91ca-268">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d91ca-268">Debian 9</span></span>       |<span data-ttu-id="d91ca-269">Debian 8</span><span class="sxs-lookup"><span data-stu-id="d91ca-269">Debian 8</span></span>       |
|-------------------------|---------------|---------------|
|<span data-ttu-id="d91ca-270">.NET core Runtime 2.0.6</span><span class="sxs-lookup"><span data-stu-id="d91ca-270">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="d91ca-271">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-271">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[<span data-ttu-id="d91ca-272">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-272">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|<span data-ttu-id="d91ca-273">.NET core Runtime 2.0.5</span><span class="sxs-lookup"><span data-stu-id="d91ca-273">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="d91ca-274">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-274">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[<span data-ttu-id="d91ca-275">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-275">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|<span data-ttu-id="d91ca-276">.NET core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="d91ca-276">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="d91ca-277">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-277">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[<span data-ttu-id="d91ca-278">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-278">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|<span data-ttu-id="d91ca-279">.NET core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="d91ca-279">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="d91ca-280">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-280">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[<span data-ttu-id="d91ca-281">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-281">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |

<span data-ttu-id="d91ca-282">**.NET core 2.1**</span><span class="sxs-lookup"><span data-stu-id="d91ca-282">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d91ca-283">Chcete-li použít pomocí sady Visual Studio .NET Core 2.1, je potřeba [instalaci Visual Studia 2017 15.7 Preview 1 nebo novější](https://www.visualstudio.com/vs/preview).</span><span class="sxs-lookup"><span data-stu-id="d91ca-283">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="d91ca-284">Moduly runtime nebo sady SDK</span><span class="sxs-lookup"><span data-stu-id="d91ca-284">Runtimes / SDKs</span></span>                  |<span data-ttu-id="d91ca-285">Debian 9</span><span class="sxs-lookup"><span data-stu-id="d91ca-285">Debian 9</span></span>       |<span data-ttu-id="d91ca-286">Debian 8</span><span class="sxs-lookup"><span data-stu-id="d91ca-286">Debian 8</span></span>       |
|---------------------------------|---------------|---------------|
|<span data-ttu-id="d91ca-287">.NET core Runtime 2.1.0-preview1</span><span class="sxs-lookup"><span data-stu-id="d91ca-287">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="d91ca-288">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-288">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0-preview1)   |[<span data-ttu-id="d91ca-289">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-289">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0-preview1)   |
|<span data-ttu-id="d91ca-290">.NET core SDK 2.1.300-preview1</span><span class="sxs-lookup"><span data-stu-id="d91ca-290">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="d91ca-291">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-291">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300-preview1)   |[<span data-ttu-id="d91ca-292">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-292">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300-preview1)   |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d91ca-293">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-293">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="d91ca-294">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-294">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d91ca-295">Instalace rozhraní .NET základní 1.x na Debian 9 nebo Debian 8:</span><span class="sxs-lookup"><span data-stu-id="d91ca-295">Install .NET Core 1.x on Debian 9 or Debian 8:</span></span>

* <span data-ttu-id="d91ca-296">.NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-296">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-297">.NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-297">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-298">.NET core Runtime 1.0.10 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-298">.NET Core Runtime 1.0.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-299">.NET core Runtime 1.0.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-299">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-300">.NET core SDK bodem 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-300">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-301">.NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-301">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-302">.NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-302">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-303">.NET core SDK 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-303">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a><span data-ttu-id="d91ca-304">Instalace .NET Core pro podporované verze Fedora (64 bitů)</span><span class="sxs-lookup"><span data-stu-id="d91ca-304">Install .NET Core for supported Fedora versions (64 bit)</span></span>

<span data-ttu-id="d91ca-305">Instalace .NET Core na podporované verze Fedora:</span><span class="sxs-lookup"><span data-stu-id="d91ca-305">To install .NET Core on supported Fedora versions:</span></span>

> [!NOTE]
> <span data-ttu-id="d91ca-306">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="d91ca-306">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d91ca-307">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-307">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="d91ca-308">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-308">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d91ca-309">Nainstalujte .NET Core 2.x na podporované Fedora verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-309">Install .NET Core 2.x on supported Fedora versions (64 bit):</span></span>

<span data-ttu-id="d91ca-310">**.NET core 2.0**</span><span class="sxs-lookup"><span data-stu-id="d91ca-310">**.NET Core 2.0**</span></span>

|<span data-ttu-id="d91ca-311">Moduly runtime nebo sady SDK</span><span class="sxs-lookup"><span data-stu-id="d91ca-311">Runtimes / SDKs</span></span>          |<span data-ttu-id="d91ca-312">Fedora 26 nebo novější</span><span class="sxs-lookup"><span data-stu-id="d91ca-312">Fedora 26 or later</span></span> |<span data-ttu-id="d91ca-313">Fedora 25 nebo předchozí</span><span class="sxs-lookup"><span data-stu-id="d91ca-313">Fedora 25 or previous</span></span> |
|-------------------------|-------------------|----------------------|
|<span data-ttu-id="d91ca-314">.NET core Runtime 2.0.6</span><span class="sxs-lookup"><span data-stu-id="d91ca-314">.NET Core Runtime 2.0.6</span></span>  |[<span data-ttu-id="d91ca-315">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-315">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[<span data-ttu-id="d91ca-316">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-316">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|<span data-ttu-id="d91ca-317">.NET core Runtime 2.0.5</span><span class="sxs-lookup"><span data-stu-id="d91ca-317">.NET Core Runtime 2.0.5</span></span>  |[<span data-ttu-id="d91ca-318">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-318">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[<span data-ttu-id="d91ca-319">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-319">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|<span data-ttu-id="d91ca-320">.NET core SDK 2.1.103</span><span class="sxs-lookup"><span data-stu-id="d91ca-320">.NET Core SDK 2.1.103</span></span>    |[<span data-ttu-id="d91ca-321">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-321">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[<span data-ttu-id="d91ca-322">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-322">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|<span data-ttu-id="d91ca-323">.NET core SDK 2.0.3</span><span class="sxs-lookup"><span data-stu-id="d91ca-323">.NET Core SDK 2.0.3</span></span>      |[<span data-ttu-id="d91ca-324">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-324">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[<span data-ttu-id="d91ca-325">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-325">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

<span data-ttu-id="d91ca-326">**.NET core 2.1**</span><span class="sxs-lookup"><span data-stu-id="d91ca-326">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d91ca-327">Chcete-li použít pomocí sady Visual Studio .NET Core 2.1, je potřeba [instalaci Visual Studia 2017 15.7 Preview 1 nebo novější](https://www.visualstudio.com/vs/preview).</span><span class="sxs-lookup"><span data-stu-id="d91ca-327">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

|<span data-ttu-id="d91ca-328">Moduly runtime nebo sady SDK</span><span class="sxs-lookup"><span data-stu-id="d91ca-328">Runtimes / SDKs</span></span>                  |<span data-ttu-id="d91ca-329">Fedora 26 nebo novější</span><span class="sxs-lookup"><span data-stu-id="d91ca-329">Fedora 26 or later</span></span> |<span data-ttu-id="d91ca-330">Fedora 25 nebo předchozí</span><span class="sxs-lookup"><span data-stu-id="d91ca-330">Fedora 25 or previous</span></span> |
|---------------------------------|-------------------|----------------------|
|<span data-ttu-id="d91ca-331">.NET core Runtime 2.1.0-preview1</span><span class="sxs-lookup"><span data-stu-id="d91ca-331">.NET Core Runtime 2.1.0-preview1</span></span> |[<span data-ttu-id="d91ca-332">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-332">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.1.0-preview1)       |[<span data-ttu-id="d91ca-333">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-333">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.1.0-preview1)           |        |
|<span data-ttu-id="d91ca-334">.NET core SDK 2.1.300-preview1</span><span class="sxs-lookup"><span data-stu-id="d91ca-334">.NET Core SDK 2.1.300-preview1</span></span>   |[<span data-ttu-id="d91ca-335">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-335">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.300-preview1)       |[<span data-ttu-id="d91ca-336">Odkaz instalace</span><span class="sxs-lookup"><span data-stu-id="d91ca-336">Install link</span></span>](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.300-preview1)           |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d91ca-337">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-337">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="d91ca-338">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-338">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d91ca-339">Nainstalujte .NET Core 1.x podporované Fedora verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-339">Install .NET Core 1.x supported Fedora versions (64 bit):</span></span>

<span data-ttu-id="d91ca-340">**Fedora 24**</span><span class="sxs-lookup"><span data-stu-id="d91ca-340">**Fedora 24**</span></span>

* <span data-ttu-id="d91ca-341">.NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-341">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-342">.NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-342">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-343">.NET core SDK bodem 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-343">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-344">.NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-344">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-345">.NET core SDK 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-345">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)</span></span>

<span data-ttu-id="d91ca-346">**Fedora 23**</span><span class="sxs-lookup"><span data-stu-id="d91ca-346">**Fedora 23**</span></span>

* <span data-ttu-id="d91ca-347">.NET core Runtime 1.0.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-347">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-348">.NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-348">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-349">.NET core SDK 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-349">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a><span data-ttu-id="d91ca-350">Instalace .NET Core pro podporované CentOS a Oracle Linux distribuce/verze (64bitová verze)</span><span class="sxs-lookup"><span data-stu-id="d91ca-350">Install .NET Core for supported CentOS and Oracle Linux distributions/versions (64 bit)</span></span>

<span data-ttu-id="d91ca-351">Chcete-li nainstalovat rozhraní .NET základní pro podporované CentOS a Oracle Linux distribuce/verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-351">To install .NET Core for supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

> [!NOTE]
> <span data-ttu-id="d91ca-352">Adresář řízenou uživatele je vyžadována pro instalace z tar.gz systému Linux.</span><span class="sxs-lookup"><span data-stu-id="d91ca-352">A user-controlled directory is required for Linux system installs from tar.gz.</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d91ca-353">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-353">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="d91ca-354">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-354">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d91ca-355">Instalace .NET Core 2.x na podporované CentOS a Oracle Linux distribuce/verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-355">Install .NET Core 2.x on supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

<span data-ttu-id="d91ca-356">**.NET core 2.0**</span><span class="sxs-lookup"><span data-stu-id="d91ca-356">**.NET Core 2.0**</span></span>

* <span data-ttu-id="d91ca-357">.NET core Runtime 2.0.6 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)</span><span class="sxs-lookup"><span data-stu-id="d91ca-357">.NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)</span></span>
* <span data-ttu-id="d91ca-358">.NET core Runtime 2.0.5 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)</span><span class="sxs-lookup"><span data-stu-id="d91ca-358">.NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)</span></span>
* <span data-ttu-id="d91ca-359">.NET core SDK 2.1.103 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)</span><span class="sxs-lookup"><span data-stu-id="d91ca-359">.NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)</span></span>
* <span data-ttu-id="d91ca-360">.NET core SDK 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)</span><span class="sxs-lookup"><span data-stu-id="d91ca-360">.NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)</span></span>
 
<span data-ttu-id="d91ca-361">**.NET core 2.1**</span><span class="sxs-lookup"><span data-stu-id="d91ca-361">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d91ca-362">Chcete-li použít pomocí sady Visual Studio .NET Core 2.1, je potřeba [instalaci Visual Studia 2017 15.7 Preview 1 nebo novější](https://www.visualstudio.com/vs/preview/).</span><span class="sxs-lookup"><span data-stu-id="d91ca-362">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview/).</span></span>

* <span data-ttu-id="d91ca-363">.NET core Runtime 2.1.0-preview1 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview1)</span><span class="sxs-lookup"><span data-stu-id="d91ca-363">.NET Core Runtime 2.1.0-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0-preview1)</span></span>
* <span data-ttu-id="d91ca-364">.NET core SDK 2.1.300-preview1 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview1)</span><span class="sxs-lookup"><span data-stu-id="d91ca-364">.NET Core SDK 2.1.300-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300-preview1)</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d91ca-365">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-365">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="d91ca-366">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-366">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d91ca-367">Instalace .NET Core 1.x na podporované CentOS a Oracle Linux distribuce/verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-367">Install .NET Core 1.x on supported CentOS and Oracle Linux distributions/versions (64 bit):</span></span>

* <span data-ttu-id="d91ca-368">.NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-368">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-369">.NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-369">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-370">.NET core Runtime 1.0.10 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-370">.NET Core Runtime 1.0.10 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-371">.NET core Runtime 1.0.9 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-371">.NET Core Runtime 1.0.9 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-372">.NET core SDK bodem 1.1.8 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-372">.NET Core SDK 1.1.8 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-373">.NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-373">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-374">.NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-374">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-375">.NET core SDK 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-375">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)</span></span>

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a><span data-ttu-id="d91ca-376">Instalace .NET Core podporované SUSE Linux Enterprise Server a OpenSUSE distribuce/verze (64bitová verze)</span><span class="sxs-lookup"><span data-stu-id="d91ca-376">Install .NET Core for supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit)</span></span>

<span data-ttu-id="d91ca-377">K instalaci .NET Core 2.x pro podporované SUSE Linux Enterprise Server a OpenSUSE distribuce/verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-377">To install .NET Core 2.x for supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d91ca-378">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-378">.NET Core 2.x</span></span>](#tab/netcore2x)

1. <span data-ttu-id="d91ca-379">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-379">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d91ca-380">Nainstalujte .NET Core 2.x na podporované SUSE Linux Enterprise Server a OpenSUSE distribuce/verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-380">Install .NET Core 2.x on supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

<span data-ttu-id="d91ca-381">**.NET core 2.0**</span><span class="sxs-lookup"><span data-stu-id="d91ca-381">**.NET Core 2.0**</span></span>

* <span data-ttu-id="d91ca-382">.NET core Runtime 2.0.6 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)</span><span class="sxs-lookup"><span data-stu-id="d91ca-382">.NET Core Runtime 2.0.6 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)</span></span>
* <span data-ttu-id="d91ca-383">.NET core Runtime 2.0.5 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)</span><span class="sxs-lookup"><span data-stu-id="d91ca-383">.NET Core Runtime 2.0.5 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)</span></span>
* <span data-ttu-id="d91ca-384">.NET core SDK 2.1.103 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)</span><span class="sxs-lookup"><span data-stu-id="d91ca-384">.NET Core SDK 2.1.103 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)</span></span>
* <span data-ttu-id="d91ca-385">.NET core SDK 2.0.3 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)</span><span class="sxs-lookup"><span data-stu-id="d91ca-385">.NET Core SDK 2.0.3 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)</span></span>
 
<span data-ttu-id="d91ca-386">**.NET core 2.1**</span><span class="sxs-lookup"><span data-stu-id="d91ca-386">**.NET Core 2.1**</span></span>

>[!IMPORTANT]
> <span data-ttu-id="d91ca-387">Chcete-li použít pomocí sady Visual Studio .NET Core 2.1, je potřeba [instalaci Visual Studia 2017 15.7 Preview 1 nebo novější](https://www.visualstudio.com/vs/preview).</span><span class="sxs-lookup"><span data-stu-id="d91ca-387">To use .NET Core 2.1 with Visual Studio, you need to [install Visual Studio 2017 15.7 Preview 1 or newer](https://www.visualstudio.com/vs/preview).</span></span>

* <span data-ttu-id="d91ca-388">.NET core Runtime 2.1.0-preview1 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview1)</span><span class="sxs-lookup"><span data-stu-id="d91ca-388">.NET Core Runtime 2.1.0-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0-preview1)</span></span>
* <span data-ttu-id="d91ca-389">.NET core SDK 2.1.300-preview1 [odkaz instalace](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview1)</span><span class="sxs-lookup"><span data-stu-id="d91ca-389">.NET Core SDK 2.1.300-preview1 [install link](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300-preview1)</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d91ca-390">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="d91ca-390">.NET Core 1.x</span></span>](#tab/netcore1x)

1. <span data-ttu-id="d91ca-391">Odeberte parametr **předchozí preview** verze .NET Core z vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="d91ca-391">Remove any **previous preview** versions of .NET Core from your system.</span></span>

2. <span data-ttu-id="d91ca-392">Nainstalujte .NET Core 1.x na podporované SUSE Linux Enterprise Server a OpenSUSE distribuce/verze (64bitová verze):</span><span class="sxs-lookup"><span data-stu-id="d91ca-392">Install .NET Core 1.x on supported SUSE Linux Enterprise Server and OpenSUSE distributions/versions (64 bit):</span></span>

<span data-ttu-id="d91ca-393">**SUSE Linux Enterprise Server 13.2**</span><span class="sxs-lookup"><span data-stu-id="d91ca-393">**SUSE Linux Enterprise Server 13.2**</span></span>

* <span data-ttu-id="d91ca-394">.NET core Runtime 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-394">.NET Core Runtime 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-395">.NET core Runtime 1.1.6 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-395">.NET Core Runtime 1.1.6 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-396">.NET core SDK 1.1.7 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-396">.NET Core SDK 1.1.7 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)</span></span>

<span data-ttu-id="d91ca-397">**openSUSE 24**</span><span class="sxs-lookup"><span data-stu-id="d91ca-397">**openSUSE 24**</span></span>

* <span data-ttu-id="d91ca-398">.NET core SDK 1.0.4 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-398">.NET Core SDK 1.0.4 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-24-x64-binaries)</span></span>
* <span data-ttu-id="d91ca-399">.NET core SDK 1.0.1 [odkaz instalace](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)</span><span class="sxs-lookup"><span data-stu-id="d91ca-399">.NET Core SDK 1.0.1 [install link](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-24-x64-binaries)</span></span>

---

> [!IMPORTANT]
> <span data-ttu-id="d91ca-400">Pokud máte potíže s instalací jádra .NET na podporované distribuce systému Linux nebo verzi, naleznete v následujících tématech nainstalovaných distribuce/verzí:</span><span class="sxs-lookup"><span data-stu-id="d91ca-400">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>
> * [<span data-ttu-id="d91ca-401">.NET core 2.1 známé problémy</span><span class="sxs-lookup"><span data-stu-id="d91ca-401">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [<span data-ttu-id="d91ca-402">Rozhraní .NET 2.0 základní známé problémy</span><span class="sxs-lookup"><span data-stu-id="d91ca-402">.NET Core 2.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [<span data-ttu-id="d91ca-403">.NET core 1.1 známé problémy</span><span class="sxs-lookup"><span data-stu-id="d91ca-403">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [<span data-ttu-id="d91ca-404">.NET core 1.0 známé problémy</span><span class="sxs-lookup"><span data-stu-id="d91ca-404">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)