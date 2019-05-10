---
title: Předpoklady pro .NET Core v počítačích Mac
description: Podporované verze macOS a .NET Core závislosti pro vývoj, nasazování a spouštění aplikací .NET Core v počítačích s macOS.
author: guardrex
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 12/14/2018
ms.openlocfilehash: 3f5dce25ed03061d690432684975909d15bbad57
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64752962"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="f9f90-103">Předpoklady pro .NET Core v macOS</span><span class="sxs-lookup"><span data-stu-id="f9f90-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="f9f90-104">Tento článek popisuje podporované macOS verze a závislosti .NET Core, které potřebujete k vývoji, nasazování a spouštění aplikací .NET Core v počítačích s macOS.</span><span class="sxs-lookup"><span data-stu-id="f9f90-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="f9f90-105">Podporované verze operačního systému a závislostech, které následují použít na tři způsoby, jak vyvíjet aplikace .NET Core na počítači Mac: prostřednictvím [příkazového řádku pomocí oblíbeného editoru](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)a [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="f9f90-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="f9f90-106">Podporované macOS verze</span><span class="sxs-lookup"><span data-stu-id="f9f90-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f9f90-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f9f90-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="f9f90-108">.NET core 2.x je podporována v následujících verzích systému macOS:</span><span class="sxs-lookup"><span data-stu-id="f9f90-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="f9f90-109">macOS 10.12 "Sierra" a novější verze</span><span class="sxs-lookup"><span data-stu-id="f9f90-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="f9f90-110">Zobrazit [podporované verze operačního systému .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) a [podporované verze operačního systému .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) úplný seznam .NET Core 2.1 a .NET Core 2.2 podporované operační systémy, distribuce a verze, z celkového počtu Podpora verze operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="f9f90-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="f9f90-111">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 2.2](https://www.microsoft.com/net/download/dotnet-core/2.2) nebo [soubory ke stažení rozhraní .NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="f9f90-111">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f9f90-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f9f90-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f9f90-113">.NET core 1.x podporuje následující verze systému macOS:</span><span class="sxs-lookup"><span data-stu-id="f9f90-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="f9f90-114">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="f9f90-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="f9f90-115">macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="f9f90-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="f9f90-116">Zobrazit [podporované verze operačního systému .NET Core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) a [podporované verze operačního systému .NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) úplný seznam 1.1 rozhraní .NET Core a .NET Core 1.0 podporované operační systémy, distribuce a verze, z celkového počtu Podpora verze operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="f9f90-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="f9f90-117">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) nebo [.NET Core 1.0 stáhne](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="f9f90-117">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="f9f90-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f9f90-118">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="f9f90-119">.NET core 3.0 ve verzi Preview 3 je podporována v následujících verzích systému macOS:</span><span class="sxs-lookup"><span data-stu-id="f9f90-119">.NET Core 3.0 Preview 3 is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="f9f90-120">macOS 10.12 "Sierra" a novější verze</span><span class="sxs-lookup"><span data-stu-id="f9f90-120">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="f9f90-121">Zobrazit [podporované verze operačního systému .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pro .NET Core 3.0 na úplný seznam podporovaných operačních systémů, distribuce a verze z verze podporu operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="f9f90-121">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="f9f90-122">Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 3.0](https://www.microsoft.com/net/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="f9f90-122">For download links and more information, see [.NET Core 3.0 downloads](https://www.microsoft.com/net/download/dotnet-core/3.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="f9f90-123">.NET core závislosti</span><span class="sxs-lookup"><span data-stu-id="f9f90-123">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f9f90-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f9f90-124">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="f9f90-125">Stáhněte a nainstalujte .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="f9f90-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="f9f90-126">Pokud máte problémy při instalaci v systému macOS, projděte si [známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.1) tématu pro nainstalovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="f9f90-126">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f9f90-127">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f9f90-127">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f9f90-128">.NET core 1.x vyžaduje OpenSSL při spouštění v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="f9f90-128">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="f9f90-129">Snadný způsob, jak získat OpenSSL je použít [Homebrew ("brew")](https://brew.sh/) Správce balíčků pro macOS.</span><span class="sxs-lookup"><span data-stu-id="f9f90-129">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="f9f90-130">Po instalaci *brew*, nainstalovat OpenSSL, spuštěním následujících příkazů v terminálu (příkaz) řádku:</span><span class="sxs-lookup"><span data-stu-id="f9f90-130">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="f9f90-131">Stáhněte a nainstalujte .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="f9f90-131">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="f9f90-132">Pokud máte problémy při instalaci v systému macOS, projděte si [1.0.0 známé problémy v sadě](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy v sadě](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) témata.</span><span class="sxs-lookup"><span data-stu-id="f9f90-132">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="f9f90-133">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f9f90-133">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="f9f90-134">Stáhněte a nainstalujte .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="f9f90-134">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="f9f90-135">Pokud máte problémy při instalaci v systému macOS, projděte si [poznámky k verzi](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) tématu pro nainstalovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="f9f90-135">If you have problems with the installation on macOS, consult the [Release notes](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) topic for the version you have installed.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="f9f90-136">Zvyšte limit maximální otevření souboru (.NET Core verze starší než .NET Core SDK bodu 2.0.2)</span><span class="sxs-lookup"><span data-stu-id="f9f90-136">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span>

<span data-ttu-id="f9f90-137">Ve starších verzích .NET Core (před .NET Core SDK bodu 2.0.2) nemusí být dostatečné pro některé úlohy .NET Core, jako je obnovení projektů nebo spouštění testů jednotek výchozí limit pro otevření souboru v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="f9f90-137">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="f9f90-138">Tento limit můžete zvýšit pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="f9f90-138">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="f9f90-139">Pomocí textového editoru vytvořte nový soubor _/Library/LaunchDaemons/limit.maxfiles.plist_a uložte soubor tohoto obsahu:</span><span class="sxs-lookup"><span data-stu-id="f9f90-139">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="f9f90-140">V okně terminálu spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f9f90-140">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="f9f90-141">Restartování počítače Mac, chcete-li použít tato nastavení.</span><span class="sxs-lookup"><span data-stu-id="f9f90-141">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="f9f90-142">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="f9f90-142">Visual Studio for Mac</span></span>

<span data-ttu-id="f9f90-143">Můžete použít libovolný editor k vývoji aplikací .NET Core pomocí sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f9f90-143">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="f9f90-144">Nicméně, pokud chcete vyvíjet aplikace .NET Core na počítači Mac v integrovaném vývojovém prostředí, můžete použít [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="f9f90-144">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

<span data-ttu-id="f9f90-145">Vývoj v .NET core v systému macOS pomocí sady Visual Studio pro Mac vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f9f90-145">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="f9f90-146">Podporované verze operačního systému macOS</span><span class="sxs-lookup"><span data-stu-id="f9f90-146">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="f9f90-147">OpenSSL (.NET Core 1.x pouze; služby zabezpečení používá .NET Core 2.x je k dispozici nativně v systému macOS)</span><span class="sxs-lookup"><span data-stu-id="f9f90-147">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="f9f90-148">.NET core SDK pro Mac</span><span class="sxs-lookup"><span data-stu-id="f9f90-148">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="f9f90-149">Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="f9f90-149">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
