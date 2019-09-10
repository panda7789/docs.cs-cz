---
title: Předpoklady pro .NET Core na Macu
description: Podporované verze macOS a závislosti rozhraní .NET Core pro vývoj, nasazování a spouštění aplikací .NET Core na macOS počítačích.
author: mairaw
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 07/13/2019
ms.openlocfilehash: 4e0570beb0dd096d7d11cdcfb6a7ed20221c0386
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848951"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="39fb4-103">Předpoklady pro .NET Core v macOS</span><span class="sxs-lookup"><span data-stu-id="39fb4-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="39fb4-104">V tomto článku se dozvíte o podporovaných verzích macOS a závislostech .NET Core, které potřebujete k vývoji, nasazování a spouštění aplikací .NET Core na počítačích s macOS.</span><span class="sxs-lookup"><span data-stu-id="39fb4-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="39fb4-105">Podporované verze operačního systému a závislosti, které následují, se vztahují na tři způsoby vývoje aplikací .NET Core na Macu: prostřednictvím [příkazového řádku s oblíbeným editorem](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)a [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="39fb4-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="39fb4-106">Podporované verze macOS</span><span class="sxs-lookup"><span data-stu-id="39fb4-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="39fb4-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="39fb4-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="39fb4-108">Rozhraní .NET Core 2. x je podporované v následujících verzích macOS:</span><span class="sxs-lookup"><span data-stu-id="39fb4-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="39fb4-109">macOS 10,12 "Sierra" a novější verze</span><span class="sxs-lookup"><span data-stu-id="39fb4-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="39fb4-110">Úplný seznam operačních systémů .NET Core 2,1 2,2 a .NET Core 2,2 s podporovanými operačními systémy, distribuce a verze, nepodporované verze operačního systému a zásady životního cyklu najdete v článku podporované verze operačního systému .NET [core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) a .net Core [](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) . odkazy.</span><span class="sxs-lookup"><span data-stu-id="39fb4-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="39fb4-111">Odkazy ke stažení a další informace najdete v tématu soubory ke stažení pro [.NET core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) nebo soubory ke stažení pro [.NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="39fb4-111">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="39fb4-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="39fb4-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="39fb4-113">Rozhraní .NET Core 1. x je podporované v následujících verzích macOS:</span><span class="sxs-lookup"><span data-stu-id="39fb4-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="39fb4-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="39fb4-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="39fb4-115">macOS 10,11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="39fb4-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="39fb4-116">Úplný seznam operačních systémů .NET Core 1,1 1,0 a .NET Core 1,0 s podporovanými operačními systémy, distribuce a verze, nepodporované verze operačního systému a zásady životního cyklu najdete v článku podporované verze operačního systému .NET [core 1,1](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) a .net Core [](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) . odkazy.</span><span class="sxs-lookup"><span data-stu-id="39fb4-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="39fb4-117">Odkazy ke stažení a další informace najdete v tématu soubory ke stažení pro [.NET core 1,1](https://dotnet.microsoft.com/download/dotnet-core/1.1) nebo soubory ke stažení pro [.NET Core 1,0](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="39fb4-117">For download links and more information, see [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="39fb4-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="39fb4-118">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="39fb4-119">.NET Core 3,0 se podporuje v následujících verzích macOS:</span><span class="sxs-lookup"><span data-stu-id="39fb4-119">.NET Core 3.0 is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="39fb4-120">macOS 10,13 "High Sierra" a novější verze</span><span class="sxs-lookup"><span data-stu-id="39fb4-120">macOS 10.13 "High Sierra" and later versions</span></span>

<span data-ttu-id="39fb4-121">Úplný 3,0 seznam podporovaných operačních systémů, distribucí a verzí operačního systému a odkazů na zásady životního cyklu najdete v tématu podporované verze operačního systému .NET [core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .</span><span class="sxs-lookup"><span data-stu-id="39fb4-121">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="39fb4-122">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="39fb4-122">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="39fb4-123">Závislosti .NET Core</span><span class="sxs-lookup"><span data-stu-id="39fb4-123">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="39fb4-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="39fb4-124">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="39fb4-125">Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro rozhraní .NET](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="39fb4-125">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="39fb4-126">Pokud máte problémy s instalací na macOS, přečtěte si téma [známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.1) pro verzi, kterou jste nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="39fb4-126">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="39fb4-127">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="39fb4-127">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="39fb4-128">.NET Core 1. x vyžaduje OpenSSL při spuštění v macOS.</span><span class="sxs-lookup"><span data-stu-id="39fb4-128">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="39fb4-129">Snadný způsob, jak získat OpenSSL, je použít Správce balíčků [homebrew ("Brew")](https://brew.sh/) pro MacOS.</span><span class="sxs-lookup"><span data-stu-id="39fb4-129">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="39fb4-130">Po instalaci *Brew*nainstalujte OpenSSL spuštěním následujících příkazů na příkazovém řádku terminálu (Command):</span><span class="sxs-lookup"><span data-stu-id="39fb4-130">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="39fb4-131">Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro rozhraní .NET](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="39fb4-131">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="39fb4-132">Pokud máte problémy s instalací na macOS, Projděte si témata [známé problémy 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) .</span><span class="sxs-lookup"><span data-stu-id="39fb4-132">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="39fb4-133">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="39fb4-133">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="39fb4-134">Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro rozhraní .NET](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="39fb4-134">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="39fb4-135">Pokud máte problémy s instalací na macOS, přečtěte si téma [poznámky](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) k verzi pro verzi, kterou jste nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="39fb4-135">If you have problems with the installation on macOS, consult the [Release notes](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) topic for the version you have installed.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="39fb4-136">Zvýšit maximální počet otevřených souborů (verze .NET Core před .NET Core SDK 2.0.2)</span><span class="sxs-lookup"><span data-stu-id="39fb4-136">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span>

<span data-ttu-id="39fb4-137">Ve starších verzích .NET Core (před .NET Core SDK 2.0.2) nemusí být výchozí omezení pro otevření souborů macOS dostačující pro některé úlohy .NET Core, jako je například obnovování projektů nebo spouštění testů jednotek.</span><span class="sxs-lookup"><span data-stu-id="39fb4-137">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="39fb4-138">Tento limit můžete zvýšit pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="39fb4-138">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="39fb4-139">Pomocí textového editoru vytvořte nový soubor _/Library/LaunchDaemons/limit.maxfiles.plist_a uložte tento soubor s tímto obsahem:</span><span class="sxs-lookup"><span data-stu-id="39fb4-139">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
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

2. <span data-ttu-id="39fb4-140">V okně terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="39fb4-140">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="39fb4-141">Pokud chcete použít tato nastavení, restartujte počítač Mac.</span><span class="sxs-lookup"><span data-stu-id="39fb4-141">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="39fb4-142">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="39fb4-142">Visual Studio for Mac</span></span>

<span data-ttu-id="39fb4-143">K vývoji aplikací .NET Core pomocí .NET Core SDK můžete použít libovolný editor.</span><span class="sxs-lookup"><span data-stu-id="39fb4-143">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="39fb4-144">Pokud ale chcete vyvíjet aplikace .NET Core na Macu v integrovaném vývojovém prostředí, můžete použít [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="39fb4-144">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

<span data-ttu-id="39fb4-145">Vývoj pro .NET Core v macOS s Visual Studio pro Mac vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="39fb4-145">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="39fb4-146">Podporovaná verze operačního systému macOS</span><span class="sxs-lookup"><span data-stu-id="39fb4-146">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="39fb4-147">OpenSSL (pouze .NET Core 1. x; .NET Core 2. x používá služby zabezpečení dostupné nativně v macOS)</span><span class="sxs-lookup"><span data-stu-id="39fb4-147">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="39fb4-148">.NET Core SDK pro Mac</span><span class="sxs-lookup"><span data-stu-id="39fb4-148">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="39fb4-149">Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="39fb4-149">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
