---
title: "Předpoklady pro .NET Core v systému Mac"
description: "Podporované verze systému macOS a .NET Core závislosti k vývoji, nasadit a spustit aplikace .NET Core v systému macOS počítače."
keywords: "Rozhraní .NET, .NET core systému macOS, Mac"
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.openlocfilehash: 16f3cfd482bddfff1b9ad56e7ffe58ae2aed4980
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="951d1-104">Předpoklady pro .NET Core v systému macOS</span><span class="sxs-lookup"><span data-stu-id="951d1-104">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="951d1-105">Tento článek ukazuje systému macOS podporované verze a závislosti .NET Core, které potřebujete k vývoji, nasadit a spustit aplikace .NET Core v systému macOS počítače.</span><span class="sxs-lookup"><span data-stu-id="951d1-105">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="951d1-106">Podporované verze operačního systému a závislosti, které následují použít na tři způsoby, jak vývoj aplikací .NET Core na Macu: prostřednictvím [příkazového řádku pomocí vašeho oblíbeného editoru](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)a [Visual Studio pro Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="951d1-106">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="951d1-107">Podporované systému macOS verze</span><span class="sxs-lookup"><span data-stu-id="951d1-107">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="951d1-108">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="951d1-108">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="951d1-109">.NET core 2.x je podporována v následujících verzích systému macOS:</span><span class="sxs-lookup"><span data-stu-id="951d1-109">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="951d1-110">systému macOS 10.12 "Sierra" a novější verze</span><span class="sxs-lookup"><span data-stu-id="951d1-110">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="951d1-111">V tématu [2.x .NET Core, podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="951d1-111">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="951d1-112">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="951d1-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="951d1-113">.NET core 1.x je podporována v následujících verzích systému macOS:</span><span class="sxs-lookup"><span data-stu-id="951d1-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="951d1-114">systému macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="951d1-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="951d1-115">systému macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="951d1-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="951d1-116">V tématu [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="951d1-116">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="951d1-117">.NET core závislosti</span><span class="sxs-lookup"><span data-stu-id="951d1-117">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="951d1-118">.NET pro základní 2.x</span><span class="sxs-lookup"><span data-stu-id="951d1-118">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="951d1-119">Stáhněte a nainstalujte rozhraní .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="951d1-119">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="951d1-120">Pokud máte problémy s instalací v systému macOS, projděte si [známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.0) téma pro nainstalovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="951d1-120">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="951d1-121">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="951d1-121">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="951d1-122">**.NET pro základní 1.x**</span><span class="sxs-lookup"><span data-stu-id="951d1-122">**.NET Core 1.x**</span></span>

<span data-ttu-id="951d1-123">.NET core 1.x vyžaduje OpenSSL spuštěnou v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="951d1-123">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="951d1-124">Snadný způsob, jak získat OpenSSL je pomocí [Homebrew ("brew")](https://brew.sh/) Správce balíčků pro systému macOS.</span><span class="sxs-lookup"><span data-stu-id="951d1-124">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="951d1-125">Po instalaci *brew*, nainstalovat OpenSSL spuštěním následujících příkazů příkazového řádku Terminálové (příkaz):</span><span class="sxs-lookup"><span data-stu-id="951d1-125">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="951d1-126">Stáhněte a nainstalujte rozhraní .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="951d1-126">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="951d1-127">Pokud máte problémy s instalací v systému macOS, projděte si [1.0.0 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) témata.</span><span class="sxs-lookup"><span data-stu-id="951d1-127">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit"></a><span data-ttu-id="951d1-128">Zvyšte limit maximální otevření souboru</span><span class="sxs-lookup"><span data-stu-id="951d1-128">Increase the maximum open file limit</span></span>

<span data-ttu-id="951d1-129">Výchozí limit pro otevření souboru v systému macOS nemusí dostačovat pro některé úlohy .NET Core, jako je například obnovení projekty nebo spouštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="951d1-129">The default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="951d1-130">Toto omezení můžete zvýšit pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="951d1-130">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="951d1-131">Pomocí textového editoru, vytvořte nový soubor _/Library/LaunchDaemons/limit.maxfiles.plist_a uložte soubor tohoto obsahu:</span><span class="sxs-lookup"><span data-stu-id="951d1-131">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="951d1-132">V okně terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="951d1-132">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="951d1-133">Restartování počítače Mac, chcete-li použít tato nastavení.</span><span class="sxs-lookup"><span data-stu-id="951d1-133">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="951d1-134">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="951d1-134">Visual Studio for Mac</span></span>

<span data-ttu-id="951d1-135">K vývoji aplikací .NET Core pomocí sady .NET Core SDK můžete použít všechny editor.</span><span class="sxs-lookup"><span data-stu-id="951d1-135">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="951d1-136">Ale pokud chcete k vývoji aplikací .NET Core v systému Mac v integrovaném vývojovém prostředí, můžete použít [Visual Studio pro Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="951d1-136">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="951d1-137">.NET core vývoj v systému macOS pomocí sady Visual Studio pro Mac vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="951d1-137">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="951d1-138">Podporované verze operačního systému macOS</span><span class="sxs-lookup"><span data-stu-id="951d1-138">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="951d1-139">OpenSSL (.NET Core 1.x pouze; .NET Core 2.x používá zabezpečení služeb dostupných v systému macOS nativně)</span><span class="sxs-lookup"><span data-stu-id="951d1-139">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="951d1-140">.NET core SDK pro systém Mac</span><span class="sxs-lookup"><span data-stu-id="951d1-140">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="951d1-141">Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="951d1-141">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)
