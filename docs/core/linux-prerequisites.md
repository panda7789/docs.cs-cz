---
title: Požadavky pro .NET Core v Linuxu
description: Podporované verze systému Linux a závislosti .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na počítačích s Linuxem.
author: thraka
ms.author: adegeo
ms.date: 12/03/2018
ms.openlocfilehash: e250158d10c6a03535f4e693e74954747f860a3c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148322"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="8163a-103">Požadavky pro .NET Core v Linuxu</span><span class="sxs-lookup"><span data-stu-id="8163a-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="8163a-104">Tento článek popisuje závislosti, které potřebujete pro vývoj aplikací .NET Core v Linuxu.</span><span class="sxs-lookup"><span data-stu-id="8163a-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="8163a-105">Podporované distribuce systému Linux/verze a závislosti, které následují platí na dva způsoby, jak vyvíjet aplikace .NET Core v Linuxu:</span><span class="sxs-lookup"><span data-stu-id="8163a-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="8163a-106">Pomocí oblíbeného editoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="8163a-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="8163a-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8163a-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="8163a-108">Balíček .NET Core SDK není potřeba pro produkční servery pro/prostředí.</span><span class="sxs-lookup"><span data-stu-id="8163a-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="8163a-109">Pro aplikace nasazené do produkčního prostředí se vyžaduje jenom balíček modulu runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8163a-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="8163a-110">Modul runtime .NET Core je nasazený s aplikacemi jako součást samostatná nasazení, ale se musí nasadit pro závisí na architektuře nasazené aplikace samostatně.</span><span class="sxs-lookup"><span data-stu-id="8163a-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="8163a-111">Další informace o typech nasazení závisí na architektuře a samostatná najdete v tématu [nasazení aplikace .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="8163a-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="8163a-112">Viz také [Self-contained Linuxové aplikace](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) konkrétní pokyny.</span><span class="sxs-lookup"><span data-stu-id="8163a-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="8163a-113">Podporované verze Linuxu</span><span class="sxs-lookup"><span data-stu-id="8163a-113">Supported Linux versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8163a-114">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="8163a-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="8163a-115">.NET core 2.x považuje Linux jako jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="8163a-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="8163a-116">Existuje jedno sestavení Linux (za architektura procesoru) podporované distribuce systému Linux.</span><span class="sxs-lookup"><span data-stu-id="8163a-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="8163a-117">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 2.2](https://www.microsoft.com/net/download/dotnet-core/2.2) nebo [soubory ke stažení rozhraní .NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="8163a-117">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="8163a-118">.NET core 2.x je podporovaný v následujících distribucích systému Linux/verzích:</span><span class="sxs-lookup"><span data-stu-id="8163a-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="8163a-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8163a-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8163a-120">CentOS 7 - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8163a-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="8163a-121">Oracle Linux 7 - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8163a-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="8163a-122">Fedora 28, 27 - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8163a-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="8163a-123">Debian 9 (64-bit, `arm32`), 8.7 nebo novější verze - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8163a-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8163a-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8163a-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8163a-125">Linux Mint 18, 17 – 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8163a-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8163a-126">openSUSE 42.3 nebo novější verze - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8163a-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8163a-127">SUSE Enterprise Linux (SLES) 12 aktualizace Service Pack 2 nebo novější - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8163a-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="8163a-128">Nástroj Alpine Linuxu 3.7 nebo novější verze - 64-bit (`x86_64` nebo `amd64`)</span><span class="sxs-lookup"><span data-stu-id="8163a-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="8163a-129">Zobrazit [podporované verze operačního systému .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) a [podporované verze operačního systému .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) úplný seznam .NET Core 2.1 a .NET Core 2.2 podporované operační systémy, distribuce a verze, z celkového počtu Podpora verze operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="8163a-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8163a-130">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="8163a-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8163a-131">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) nebo [.NET Core 1.0 stáhne](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="8163a-131">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="8163a-132">.NET core 1.x podporuje následující Linux 64-bit (`x86_64` nebo `amd64`) distribuce a verze:</span><span class="sxs-lookup"><span data-stu-id="8163a-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="8163a-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="8163a-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="8163a-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="8163a-134">CentOS 7</span></span>
* <span data-ttu-id="8163a-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="8163a-135">Oracle Linux 7</span></span>
* <span data-ttu-id="8163a-136">Fedora 28 (.NET Core 1.1), z 27.</span><span class="sxs-lookup"><span data-stu-id="8163a-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="8163a-137">Debian 8.2 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="8163a-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="8163a-138">18.04 (.NET Core 1.1), Ubuntu 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="8163a-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="8163a-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="8163a-139">Linux Mint 17</span></span>
* <span data-ttu-id="8163a-140">openSUSE 42.3 nebo novější verze (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="8163a-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="8163a-141">Zobrazit [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, z verze podporu operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="8163a-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="8163a-142">Závislosti distribuce Linuxu</span><span class="sxs-lookup"><span data-stu-id="8163a-142">Linux distribution dependencies</span></span>

<span data-ttu-id="8163a-143">Následující jsou určeny jako příklady.</span><span class="sxs-lookup"><span data-stu-id="8163a-143">The following are intended to be examples.</span></span> <span data-ttu-id="8163a-144">Přesné verze a názvy se mohou mírně lišit na vaší distribuci Linuxu podle výběru.</span><span class="sxs-lookup"><span data-stu-id="8163a-144">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="8163a-145">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8163a-145">Ubuntu</span></span>

<span data-ttu-id="8163a-146">Ubuntu distribuce vyžaduje nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="8163a-146">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="8163a-147">liblttng ust0</span><span class="sxs-lookup"><span data-stu-id="8163a-147">liblttng-ust0</span></span>
* <span data-ttu-id="8163a-148">libcurl3</span><span class="sxs-lookup"><span data-stu-id="8163a-148">libcurl3</span></span>
* <span data-ttu-id="8163a-149">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="8163a-149">libssl1.0.0</span></span>
* <span data-ttu-id="8163a-150">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="8163a-150">libkrb5-3</span></span>
* <span data-ttu-id="8163a-151">zlib1g</span><span class="sxs-lookup"><span data-stu-id="8163a-151">zlib1g</span></span>
* <span data-ttu-id="8163a-152">libicu52 (pro 14.x)</span><span class="sxs-lookup"><span data-stu-id="8163a-152">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="8163a-153">libicu55 (pro 16.x)</span><span class="sxs-lookup"><span data-stu-id="8163a-153">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="8163a-154">libicu57 (pro 17.x)</span><span class="sxs-lookup"><span data-stu-id="8163a-154">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="8163a-155">libicu60 (pro 18.x)</span><span class="sxs-lookup"><span data-stu-id="8163a-155">libicu60 (for 18.x)</span></span>

<span data-ttu-id="8163a-156">Pro verze starší než .NET Core 2.1 následující závislosti se rovněž vyžadují:</span><span class="sxs-lookup"><span data-stu-id="8163a-156">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="8163a-157">libunwind8</span><span class="sxs-lookup"><span data-stu-id="8163a-157">libunwind8</span></span>
* <span data-ttu-id="8163a-158">libuuid1</span><span class="sxs-lookup"><span data-stu-id="8163a-158">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="8163a-159">CentOS i Fedora</span><span class="sxs-lookup"><span data-stu-id="8163a-159">CentOS and Fedora</span></span>

<span data-ttu-id="8163a-160">CentOS distribuce vyžaduje nainstalované následující knihovny:</span><span class="sxs-lookup"><span data-stu-id="8163a-160">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="8163a-161">lttng tým ust</span><span class="sxs-lookup"><span data-stu-id="8163a-161">lttng-ust</span></span>
* <span data-ttu-id="8163a-162">libcurl</span><span class="sxs-lookup"><span data-stu-id="8163a-162">libcurl</span></span>
* <span data-ttu-id="8163a-163">knihovny OpenSSL</span><span class="sxs-lookup"><span data-stu-id="8163a-163">openssl-libs</span></span>
* <span data-ttu-id="8163a-164">krb5 knihovny</span><span class="sxs-lookup"><span data-stu-id="8163a-164">krb5-libs</span></span>
* <span data-ttu-id="8163a-165">libicu</span><span class="sxs-lookup"><span data-stu-id="8163a-165">libicu</span></span>
* <span data-ttu-id="8163a-166">zlib</span><span class="sxs-lookup"><span data-stu-id="8163a-166">zlib</span></span>

<span data-ttu-id="8163a-167">Uživatelé, fedora: Pokud vaše openssl verze > = 1.1, budete muset nainstalovat openssl10 kompatibility.</span><span class="sxs-lookup"><span data-stu-id="8163a-167">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="8163a-168">Pro verze starší než .NET Core 2.1 následující závislosti se rovněž vyžadují:</span><span class="sxs-lookup"><span data-stu-id="8163a-168">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="8163a-169">libunwind</span><span class="sxs-lookup"><span data-stu-id="8163a-169">libunwind</span></span>
* <span data-ttu-id="8163a-170">libuuid</span><span class="sxs-lookup"><span data-stu-id="8163a-170">libuuid</span></span>

<span data-ttu-id="8163a-171">Další informace o závislostech najdete v tématu [Self-contained Linuxové aplikace](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="8163a-171">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="8163a-172">Instalování závislostí pro .NET Core pomocí nativních instalačních programů</span><span class="sxs-lookup"><span data-stu-id="8163a-172">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="8163a-173">.NET core, které jsou k dispozici pro nativních instalačních programů podporované distribuce systému Linux/verze.</span><span class="sxs-lookup"><span data-stu-id="8163a-173">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="8163a-174">Nativních instalačních programů vyžadovat přístup správce (sudo) na server.</span><span class="sxs-lookup"><span data-stu-id="8163a-174">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="8163a-175">Výhodou použití nativní instalačního programu je, že jsou nainstalovány všechny závislosti nativní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8163a-175">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="8163a-176">Nativních instalačních programů nainstalovat také systémová sada .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8163a-176">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="8163a-177">V Linuxu existují dvě možnosti balíček instalačního programu:</span><span class="sxs-lookup"><span data-stu-id="8163a-177">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="8163a-178">Pomocí Správce balíčků založená na informační kanál, třeba apt-get pro Ubuntu nebo yumu pro CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="8163a-178">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="8163a-179">Použití balíčků, sami, DEB nebo ot. / min.</span><span class="sxs-lookup"><span data-stu-id="8163a-179">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="8163a-180">Skriptování nainstaluje s skript instalačního programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="8163a-180">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="8163a-181">[Dotnet instalačních skriptů](./tools/dotnet-install-script.md) umožňují provést instalaci bez oprávnění správce. Sada nástrojů rozhraní příkazového řádku a sdílený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="8163a-181">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="8163a-182">Můžete stáhnout skript z [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).</span><span class="sxs-lookup"><span data-stu-id="8163a-182">You can download the script from [https://dot.net/v1/dotnet-install.sh](https://dot.net/v1/dotnet-install.sh).</span></span>

<span data-ttu-id="8163a-183">Výchozí hodnoty skriptu k instalaci nejnovější verze "L", která je aktuálně .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="8163a-183">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="8163a-184">Pokud chcete nainstalovat rozhraní .NET Core 2.1, spusťte skript s přepínačem následující:</span><span class="sxs-lookup"><span data-stu-id="8163a-184">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="8163a-185">Skript bash instalačního programu se používá v scénáře automatizace a zařízení bez oprávnění správce.</span><span class="sxs-lookup"><span data-stu-id="8163a-185">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="8163a-186">Tento skript také přečte přepínače prostředí PowerShell, aby je bylo možné použít pomocí skriptu v systémech Linux nebo OS X.</span><span class="sxs-lookup"><span data-stu-id="8163a-186">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="8163a-187">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="8163a-187">Troubleshoot</span></span>

<span data-ttu-id="8163a-188">Pokud máte problémy s instalací rozhraní .NET Core na podporované distribuce systému Linux/version, najdete v následujících tématech nainstalovaných distribucí a verzí:</span><span class="sxs-lookup"><span data-stu-id="8163a-188">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="8163a-189">Známé problémy s .NET core 3.0</span><span class="sxs-lookup"><span data-stu-id="8163a-189">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="8163a-190">Známé problémy s .NET core 2.2</span><span class="sxs-lookup"><span data-stu-id="8163a-190">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="8163a-191">Známé problémy s .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="8163a-191">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="8163a-192">Známé problémy s .NET core 1.1</span><span class="sxs-lookup"><span data-stu-id="8163a-192">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="8163a-193">Známé problémy s .NET core 1.0</span><span class="sxs-lookup"><span data-stu-id="8163a-193">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
