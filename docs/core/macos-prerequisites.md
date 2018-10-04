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
# <a name="prerequisites-for-net-core-on-macos"></a>Předpoklady pro .NET Core v macOS

Tento článek popisuje podporované macOS verze a závislosti .NET Core, které potřebujete k vývoji, nasazování a spouštění aplikací .NET Core v počítačích s macOS. Podporované verze operačního systému a závislostech, které následují použít na tři způsoby, jak vyvíjet aplikace .NET Core na počítači Mac: prostřednictvím [příkazového řádku pomocí oblíbeného editoru](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)a [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).

## <a name="supported-macos-versions"></a>Podporované macOS verze

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

.NET core 2.x je podporována v následujících verzích systému macOS:

* macOS 10.12 "Sierra" a novější verze

Zobrazit [podporované verze operačního systému aplikace .NET Core 2.x](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, z verze podporu operačního systému a propojení zásad životního cyklu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

.NET core 1.x podporuje následující verze systému macOS:

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

Zobrazit [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, z verze podporu operačního systému a propojení zásad životního cyklu.

---

## <a name="net-core-dependencies"></a>.NET core závislosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

Stáhněte a nainstalujte .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core). Pokud máte problémy při instalaci v systému macOS, projděte si [známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.1) tématu pro nainstalovanou verzi.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**.NET core 1.x**

.NET core 1.x vyžaduje OpenSSL při spouštění v systému macOS. Snadný způsob, jak získat OpenSSL je použít [Homebrew ("brew")](https://brew.sh/) Správce balíčků pro macOS. Po instalaci *brew*, nainstalovat OpenSSL, spuštěním následujících příkazů v terminálu (příkaz) řádku:

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Stáhněte a nainstalujte .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core). Pokud máte problémy při instalaci v systému macOS, projděte si [1.0.0 známé problémy v sadě](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy v sadě](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) témata.

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>Zvyšte limit maximální otevření souboru (.NET Core verze starší než .NET Core SDK bodu 2.0.2) 

Ve starších verzích .NET Core (před .NET Core SDK bodu 2.0.2) nemusí být dostatečné pro některé úlohy .NET Core, jako je obnovení projektů nebo spouštění testů jednotek výchozí limit pro otevření souboru v systému macOS.

Tento limit můžete zvýšit pomocí následujících kroků:

1. Pomocí textového editoru vytvořte nový soubor _/Library/LaunchDaemons/limit.maxfiles.plist_a uložte soubor tohoto obsahu:

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

2. V okně terminálu spusťte následující příkaz:

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. Restartování počítače Mac, chcete-li použít tato nastavení.

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

Můžete použít libovolný editor k vývoji aplikací .NET Core pomocí sady .NET Core SDK. Nicméně, pokud chcete vyvíjet aplikace .NET Core na počítači Mac v integrovaném vývojovém prostředí, můžete použít [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/). 

Vývoj v .NET core v systému macOS pomocí sady Visual Studio pro Mac vyžaduje:

* Podporované verze operačního systému macOS
* OpenSSL (.NET Core 1.x pouze; služby zabezpečení používá .NET Core 2.x je k dispozici nativně v systému macOS)
* .NET core SDK pro Mac
* [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
