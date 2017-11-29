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
# <a name="prerequisites-for-net-core-on-macos"></a>Předpoklady pro .NET Core v systému macOS

Tento článek ukazuje systému macOS podporované verze a závislosti .NET Core, které potřebujete k vývoji, nasadit a spustit aplikace .NET Core v systému macOS počítače. Podporované verze operačního systému a závislosti, které následují použít na tři způsoby, jak vývoj aplikací .NET Core na Macu: prostřednictvím [příkazového řádku pomocí vašeho oblíbeného editoru](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)a [Visual Studio pro Mac](https://www.visualstudio.com/vs/visual-studio-mac/).

## <a name="supported-macos-versions"></a>Podporované systému macOS verze

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

.NET core 2.x je podporována v následujících verzích systému macOS:

* systému macOS 10.12 "Sierra" a novější verze

V tématu [2.x .NET Core, podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

.NET core 1.x je podporována v následujících verzích systému macOS:

* systému macOS 10.12 "Sierra"
* systému macOS 10.11 "El Capitan"

V tématu [podporované verze operačního systému aplikace .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pro úplný seznam .NET Core 1.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.

---

## <a name="net-core-dependencies"></a>.NET core závislosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

Stáhněte a nainstalujte rozhraní .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core). Pokud máte problémy s instalací v systému macOS, projděte si [známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.0) téma pro nainstalovanou verzi.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

**.NET pro základní 1.x**

.NET core 1.x vyžaduje OpenSSL spuštěnou v systému macOS. Snadný způsob, jak získat OpenSSL je pomocí [Homebrew ("brew")](https://brew.sh/) Správce balíčků pro systému macOS. Po instalaci *brew*, nainstalovat OpenSSL spuštěním následujících příkazů příkazového řádku Terminálové (příkaz):

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Stáhněte a nainstalujte rozhraní .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core). Pokud máte problémy s instalací v systému macOS, projděte si [1.0.0 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) témata.

---

## <a name="increase-the-maximum-open-file-limit"></a>Zvyšte limit maximální otevření souboru

Výchozí limit pro otevření souboru v systému macOS nemusí dostačovat pro některé úlohy .NET Core, jako je například obnovení projekty nebo spouštění testů jednotek.

Toto omezení můžete zvýšit pomocí následujících kroků:

1. Pomocí textového editoru, vytvořte nový soubor _/Library/LaunchDaemons/limit.maxfiles.plist_a uložte soubor tohoto obsahu:

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

K vývoji aplikací .NET Core pomocí sady .NET Core SDK můžete použít všechny editor. Ale pokud chcete k vývoji aplikací .NET Core v systému Mac v integrovaném vývojovém prostředí, můžete použít [Visual Studio pro Mac](https://www.visualstudio.com/vs/visual-studio-mac/). 

.NET core vývoj v systému macOS pomocí sady Visual Studio pro Mac vyžaduje:

* Podporované verze operačního systému macOS
* OpenSSL (.NET Core 1.x pouze; .NET Core 2.x používá zabezpečení služeb dostupných v systému macOS nativně)
* .NET core SDK pro systém Mac
* [Visual Studio pro Mac](https://www.visualstudio.com/vs/visual-studio-mac/)
