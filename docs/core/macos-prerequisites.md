---
title: Předpoklady pro .NET Core v počítačích Mac
description: Podporované verze macOS a .NET Core závislosti pro vývoj, nasazování a spouštění aplikací .NET Core v počítačích s macOS.
author: guardrex
ms.author: mairaw
ms.date: 10/03/2018
ms.openlocfilehash: b5b3c6ea90a2cc4487e849af468d324b645834af
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584075"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="88b45-103">Předpoklady pro .NET Core v macOS</span><span class="sxs-lookup"><span data-stu-id="88b45-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="88b45-104">Tento článek popisuje podporované macOS verze a závislosti .NET Core, které potřebujete k vývoji, nasazování a spouštění aplikací .NET Core v počítačích s macOS.</span><span class="sxs-lookup"><span data-stu-id="88b45-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="88b45-105">Podporované verze operačního systému a závislostech, které následují použít na tři způsoby, jak vyvíjet aplikace .NET Core na počítači Mac: prostřednictvím [příkazového řádku pomocí oblíbeného editoru](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)a [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="88b45-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="88b45-106">Podporované macOS verze</span><span class="sxs-lookup"><span data-stu-id="88b45-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="88b45-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="88b45-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="88b45-108">.NET core 2.x je podporována v následujících verzích systému macOS:</span><span class="sxs-lookup"><span data-stu-id="88b45-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="88b45-109">macOS 10.12 "Sierra" a novější verze</span><span class="sxs-lookup"><span data-stu-id="88b45-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="88b45-110">Zobrazit [podporované verze operačního systému aplikace .NET Core 2.x](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, z verze podporu operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="88b45-110">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="88b45-111">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="88b45-111">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="88b45-112">.NET core 1.x podporuje následující verze systému macOS:</span><span class="sxs-lookup"><span data-stu-id="88b45-112">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="88b45-113">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="88b45-113">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="88b45-114">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="88b45-114">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="88b45-115">Zobrazit [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, z verze podporu operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="88b45-115">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="88b45-116">.NET core závislosti</span><span class="sxs-lookup"><span data-stu-id="88b45-116">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="88b45-117">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="88b45-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="88b45-118">Stáhněte a nainstalujte .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="88b45-118">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="88b45-119">Pokud máte problémy při instalaci v systému macOS, projděte si [známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.1) tématu pro nainstalovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="88b45-119">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="88b45-120">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="88b45-120">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="88b45-121">**.NET core 1.x**</span><span class="sxs-lookup"><span data-stu-id="88b45-121">**.NET Core 1.x**</span></span>

<span data-ttu-id="88b45-122">.NET core 1.x vyžaduje OpenSSL při spouštění v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="88b45-122">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="88b45-123">Snadný způsob, jak získat OpenSSL je použít [Homebrew ("brew")](https://brew.sh/) Správce balíčků pro macOS.</span><span class="sxs-lookup"><span data-stu-id="88b45-123">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="88b45-124">Po instalaci *brew*, nainstalovat OpenSSL, spuštěním následujících příkazů v terminálu (příkaz) řádku:</span><span class="sxs-lookup"><span data-stu-id="88b45-124">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="88b45-125">Stáhněte a nainstalujte .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="88b45-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="88b45-126">Pokud máte problémy při instalaci v systému macOS, projděte si [1.0.0 známé problémy v sadě](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy v sadě](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) témata.</span><span class="sxs-lookup"><span data-stu-id="88b45-126">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="88b45-127">Zvyšte limit maximální otevření souboru (.NET Core verze starší než .NET Core SDK bodu 2.0.2)</span><span class="sxs-lookup"><span data-stu-id="88b45-127">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span> 

<span data-ttu-id="88b45-128">Ve starších verzích .NET Core (před .NET Core SDK bodu 2.0.2) nemusí být dostatečné pro některé úlohy .NET Core, jako je obnovení projektů nebo spouštění testů jednotek výchozí limit pro otevření souboru v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="88b45-128">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="88b45-129">Tento limit můžete zvýšit pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="88b45-129">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="88b45-130">Pomocí textového editoru vytvořte nový soubor _/Library/LaunchDaemons/limit.maxfiles.plist_a uložte soubor tohoto obsahu:</span><span class="sxs-lookup"><span data-stu-id="88b45-130">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>limit.maxfiles</string>
    <key>ProgramArguments</key>
    <array>
      <string>launchctl</string>
      <string>limit</string>
      <string>maxfiles</string>
      <string>2048</string>
      <string>4096</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>ServiceIPC</key>
    <false/>
  </dict>
</plist>
```

2. <span data-ttu-id="88b45-131">V okně terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="88b45-131">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="88b45-132">Restartování počítače Mac, chcete-li použít tato nastavení.</span><span class="sxs-lookup"><span data-stu-id="88b45-132">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="88b45-133">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="88b45-133">Visual Studio for Mac</span></span>

<span data-ttu-id="88b45-134">Můžete použít libovolný editor k vývoji aplikací .NET Core pomocí sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="88b45-134">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="88b45-135">Nicméně, pokud chcete vyvíjet aplikace .NET Core na počítači Mac v integrovaném vývojovém prostředí, můžete použít [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="88b45-135">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="88b45-136">Vývoj v .NET core v systému macOS pomocí sady Visual Studio pro Mac vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="88b45-136">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="88b45-137">Podporované verze operačního systému macOS</span><span class="sxs-lookup"><span data-stu-id="88b45-137">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="88b45-138">OpenSSL (.NET Core 1.x pouze; služby zabezpečení používá .NET Core 2.x je k dispozici nativně v systému macOS)</span><span class="sxs-lookup"><span data-stu-id="88b45-138">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="88b45-139">.NET core SDK pro Mac</span><span class="sxs-lookup"><span data-stu-id="88b45-139">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="88b45-140">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="88b45-140">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
