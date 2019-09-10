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
# <a name="prerequisites-for-net-core-on-macos"></a>Předpoklady pro .NET Core v macOS

V tomto článku se dozvíte o podporovaných verzích macOS a závislostech .NET Core, které potřebujete k vývoji, nasazování a spouštění aplikací .NET Core na počítačích s macOS. Podporované verze operačního systému a závislosti, které následují, se vztahují na tři způsoby vývoje aplikací .NET Core na Macu: prostřednictvím [příkazového řádku s oblíbeným editorem](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)a [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

## <a name="supported-macos-versions"></a>Podporované verze macOS

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Rozhraní .NET Core 2. x je podporované v následujících verzích macOS:

* macOS 10,12 "Sierra" a novější verze

Úplný seznam operačních systémů .NET Core 2,1 2,2 a .NET Core 2,2 s podporovanými operačními systémy, distribuce a verze, nepodporované verze operačního systému a zásady životního cyklu najdete v článku podporované verze operačního systému .NET [core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) a .net Core [](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) . odkazy.

Odkazy ke stažení a další informace najdete v tématu soubory ke stažení pro [.NET core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) nebo soubory ke stažení pro [.NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Rozhraní .NET Core 1. x je podporované v následujících verzích macOS:

* macOS 10.12 "Sierra"
* macOS 10,11 "El Capitan"

Úplný seznam operačních systémů .NET Core 1,1 1,0 a .NET Core 1,0 s podporovanými operačními systémy, distribuce a verze, nepodporované verze operačního systému a zásady životního cyklu najdete v článku podporované verze operačního systému .NET [core 1,1](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) a .net Core [](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) . odkazy.

Odkazy ke stažení a další informace najdete v tématu soubory ke stažení pro [.NET core 1,1](https://dotnet.microsoft.com/download/dotnet-core/1.1) nebo soubory ke stažení pro [.NET Core 1,0](https://dotnet.microsoft.com/download/dotnet-core/1.0).

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3,0 se podporuje v následujících verzích macOS:

* macOS 10,13 "High Sierra" a novější verze

Úplný 3,0 seznam podporovaných operačních systémů, distribucí a verzí operačního systému a odkazů na zásady životního cyklu najdete v tématu podporované verze operačního systému .NET [core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .

Odkazy ke stažení a další informace najdete v tématu [soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

---

## <a name="net-core-dependencies"></a>Závislosti .NET Core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro rozhraní .NET](https://dotnet.microsoft.com/download) . Pokud máte problémy s instalací na macOS, přečtěte si téma [známé problémy](https://github.com/dotnet/core/tree/master/release-notes/2.1) pro verzi, kterou jste nainstalovali.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

.NET Core 1. x vyžaduje OpenSSL při spuštění v macOS. Snadný způsob, jak získat OpenSSL, je použít Správce balíčků [homebrew ("Brew")](https://brew.sh/) pro MacOS. Po instalaci *Brew*nainstalujte OpenSSL spuštěním následujících příkazů na příkazovém řádku terminálu (Command):

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro rozhraní .NET](https://dotnet.microsoft.com/download) . Pokud máte problémy s instalací na macOS, Projděte si témata [známé problémy 1.0.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) a [1.0.1 známé problémy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) .

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Stáhněte a nainstalujte .NET Core SDK na stránce [soubory ke stažení pro rozhraní .NET](https://dotnet.microsoft.com/download) . Pokud máte problémy s instalací na macOS, přečtěte si téma [poznámky](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) k verzi pro verzi, kterou jste nainstalovali.

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>Zvýšit maximální počet otevřených souborů (verze .NET Core před .NET Core SDK 2.0.2)

Ve starších verzích .NET Core (před .NET Core SDK 2.0.2) nemusí být výchozí omezení pro otevření souborů macOS dostačující pro některé úlohy .NET Core, jako je například obnovování projektů nebo spouštění testů jednotek.

Tento limit můžete zvýšit pomocí následujících kroků:

1. Pomocí textového editoru vytvořte nový soubor _/Library/LaunchDaemons/limit.maxfiles.plist_a uložte tento soubor s tímto obsahem:

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

2. V okně terminálu spusťte následující příkaz:

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. Pokud chcete použít tato nastavení, restartujte počítač Mac.

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

K vývoji aplikací .NET Core pomocí .NET Core SDK můžete použít libovolný editor. Pokud ale chcete vyvíjet aplikace .NET Core na Macu v integrovaném vývojovém prostředí, můžete použít [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

Vývoj pro .NET Core v macOS s Visual Studio pro Mac vyžaduje:

* Podporovaná verze operačního systému macOS
* OpenSSL (pouze .NET Core 1. x; .NET Core 2. x používá služby zabezpečení dostupné nativně v macOS)
* .NET Core SDK pro Mac
* [Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
