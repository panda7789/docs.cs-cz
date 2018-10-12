---
title: 'Instalaci F #'
description: 'Informace o instalaci F # založeny na vašem prostředí.'
ms.date: 08/28/2018
ms.openlocfilehash: 909e1c07ff7f6d52db77a987639d1c749146fdca
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120931"
---
# <a name="install-f"></a>Instalaci F # #

Můžete nainstalovat F # několika různými způsoby v závislosti na vašem prostředí.

## <a name="install-f-with-visual-studio"></a>Instalaci F # pomocí sady Visual Studio

Pokud stahujete [sady Visual Studio](https://visualstudio.microsoft.com/) poprvé, bude nejprve nainstalovat Instalační program sady Visual Studio. Instalace odpovídající SKU sady Visual Studio pomocí instalačního programu. Pokud už máte nainstalovaný, klikněte na tlačítko **změnit**.

Dále uvidíte seznam úloh. Vyberte **vývoj pro ASP.NET a web** instalace podporu F # a .NET Core pro projekty ASP.NET Core.

Klepnutím na tlačítko **změnit** v dolní pravé straně.  Tím se nainstaluje všechno, co jste vybrali. Pak můžete otevřít Visual Studio 2017 s podporou jazyka F # kliknutím **spuštění**.

## <a name="install-f-with-visual-studio-for-mac"></a>Instalaci F # pomocí sady Visual Studio pro Mac

F # je nainstalovaný ve výchozím nastavení v [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/), bez ohledu na to, konfiguraci, kterou zvolíte.

Po dokončení instalace zvolte možnost "Spustit Visual Studio". Také ho můžete spustit v systému macOS prostřednictvím hledání.

## <a name="install-f-with-visual-studio-code"></a>Instalaci F # ve Visual Studiu Code

Musíte mít [nainstalovaný git](https://git-scm.com/download) a dostupný na vaší cesty pomocí šablon projektu. Můžete ověřit, jestli je správně nainstalovaný zadáním `git --version` na příkazovém řádku a stisknutím klávesy **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](http://www.mono-project.com) se používá pro [F # Interactive](../tutorials/fsharp-interactive/index.md) podporovat. Pomocí Homebrew je nejjednodušší způsob, jak nainstalovat Mono v systému macOS. Jednoduše do svého terminálu zadejte následující příkaz:

```console
brew install mono
```

Nainstalovat také [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com) se používá pro [F # Interactive](../tutorials/fsharp-interactive/index.md) podporovat. Pokud jste v systému Debian nebo Ubuntu, můžete použít následující:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Nainstalovat také [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Nainstalujte [Visual Studio s podporou F #](#install-f-with-visual-studio). Tím se nainstaluje všechny komponenty potřebné k zápisu, kompilaci a spouštění kódu jazyka F #.

Nainstalovat také [.NET Core SDK](https://www.microsoft.com/net/download/).

---

Bude nutné [Visual Studio Code](https://code.visualstudio.com) nainstalované.

Dále klikněte na ikonu rozšíření a vyhledejte položku "Ionide":

Pouze modul plug-in, které jsou potřebné pro podporu F # v aplikaci Visual Studio Code je [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Ale můžete také nainstalovat [Ionide PHISHING](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) zobrazíte [FALEŠNÉ](https://fsharp.github.io/FAKE/) podporu a [Ionide Stáhnout](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) zobrazíte [Stáhnout](https://fsprojects.github.io/Paket/) podporovat. FALEŠNÉ a stáhnout jsou další F # komunitní nástroje pro vytváření projektů a správu závislostí, v uvedeném pořadí.
