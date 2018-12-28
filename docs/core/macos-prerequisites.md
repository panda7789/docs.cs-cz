---
title: Předpoklady pro .NET Core v počítačích Mac
description: Podporované verze macOS a .NET Core závislosti pro vývoj, nasazování a spouštění aplikací .NET Core v počítačích s macOS.
author: guardrex
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: bc6e0b20c61c474c7069b757528dbc1ea38354e3
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656307"
---
# <a name="prerequisites-for-net-core-on-macos"></a>Předpoklady pro .NET Core v macOS

Tento článek popisuje podporované macOS verze a závislosti .NET Core, které potřebujete k vývoji, nasazování a spouštění aplikací .NET Core v počítačích s macOS. Podporované verze operačního systému a závislostech, které následují použít na tři způsoby, jak vyvíjet aplikace .NET Core na počítači Mac: prostřednictvím [příkazového řádku pomocí oblíbeného editoru](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)a [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).

## <a name="supported-macos-versions"></a>Podporované macOS verze

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

.NET core 2.x je podporována v následujících verzích systému macOS:

* macOS 10.12 "Sierra" a novější verze

Zobrazit [podporované verze operačního systému .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) a [podporované verze operačního systému .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) úplný seznam .NET Core 2.1 a .NET Core 2.2 podporované operační systémy, distribuce a verze, z celkového počtu Podpora verze operačního systému a propojení zásad životního cyklu.

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 2.2](https://www.microsoft.com/net/download/dotnet-core/2.2) nebo [soubory ke stažení rozhraní .NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1).


# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

.NET core 1.x podporuje následující verze systému macOS:

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

Zobrazit [podporované verze operačního systému .NET Core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) a [podporované verze operačního systému .NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) úplný seznam 1.1 rozhraní .NET Core a .NET Core 1.0 podporované operační systémy, distribuce a verze, z celkového počtu Podpora verze operačního systému a propojení zásad životního cyklu.

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) nebo [.NET Core 1.0 stáhne](https://www.microsoft.com/net/download/dotnet-core/1.0).

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET core 3.0 ve verzi Preview 1](#tab/netcore30)

.NET core 3.0 ve verzi Preview 1 se podporuje v následujících verzích systému macOS:

* macOS 10.12 "Sierra" a novější verze

Zobrazit [podporované verze operačního systému .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pro .NET Core 3.0 na úplný seznam podporovaných operačních systémů, distribuce a verze z verze podporu operačního systému a propojení zásad životního cyklu.

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení rozhraní .NET Core 3.0](https://www.microsoft.com/net/download/dotnet-core/3.0).

---

## <a name="net-core-dependencies"></a>.NET core závislosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

Stáhněte a nainstalujte .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core). Pokud máte problémy při instalaci v systému macOS, projděte si [známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.1) tématu pro nainstalovanou verzi.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

.NET core 1.x vyžaduje OpenSSL při spouštění v systému macOS. Snadný způsob, jak získat OpenSSL je použít [Homebrew ("brew")](https://brew.sh/) Správce balíčků pro macOS. Po instalaci *brew*, nainstalovat OpenSSL, spuštěním následujících příkazů v terminálu (příkaz) řádku:

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Stáhněte a nainstalujte .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core). Pokud máte problémy při instalaci v systému macOS, projděte si [1.0.0 známé problémy v sadě](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy v sadě](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) témata.

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET core 3.0 ve verzi Preview 1](#tab/netcore30)

Stáhněte a nainstalujte .NET Core SDK z [.NET stáhne](https://www.microsoft.com/net/download/core). Pokud máte problémy při instalaci v systému macOS, projděte si [poznámky k verzi](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) tématu pro nainstalovanou verzi.

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
