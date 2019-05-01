---
title: InstalaceF#
description: Zjistěte, jak nainstalovat F# podle vašeho prostředí.
ms.date: 08/28/2018
ms.openlocfilehash: 792c61c0522cd4d0c68a64572f2892ce33f71ea6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017017"
---
# <a name="install-f"></a>Instalaci F\#

Můžete nainstalovat F# několika různými způsoby v závislosti na vašem prostředí.

## <a name="install-f-with-visual-studio"></a>Nainstalujte F# pomocí sady Visual Studio

Pokud stahujete [sady Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) poprvé, bude nejprve nainstalovat Instalační program sady Visual Studio. Instalace odpovídající SKU sady Visual Studio pomocí instalačního programu. Pokud už máte nainstalovaný, klikněte na tlačítko **změnit**.

Dále uvidíte seznam úloh. Vyberte **vývoj pro ASP.NET a web** instalace F# podpory a .NET Core, podporu pro projekty ASP.NET Core.

Klepnutím na tlačítko **změnit** v dolní pravé straně.  Tím se nainstaluje všechno, co jste vybrali. Pak můžete otevřít Visual Studio 2017 s F# jazykovou podporu kliknutím **spuštění**.

## <a name="install-f-with-visual-studio-for-mac"></a>Nainstalujte F# pomocí sady Visual Studio pro Mac

F#je nainstalovaný ve výchozím nastavení v [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), bez ohledu na to, konfiguraci, kterou zvolíte.

Po dokončení instalace zvolte možnost "Spustit Visual Studio". Také ho můžete spustit v systému macOS prostřednictvím hledání.

## <a name="install-f-with-visual-studio-code"></a>Nainstalujte F# ve Visual Studiu Code

Musíte mít [nainstalovaný git](https://git-scm.com/download) a dostupný na vaší cesty pomocí šablon projektu. Můžete ověřit, jestli je správně nainstalovaný zadáním `git --version` na příkazovém řádku a stisknutím klávesy **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

[Mono](https://www.mono-project.com) se používá pro [ F# interaktivní](../tutorials/fsharp-interactive/index.md) podporovat. Pomocí Homebrew je nejjednodušší způsob, jak nainstalovat Mono v systému macOS. Jednoduše do svého terminálu zadejte následující příkaz:

```console
brew install mono
```

Nainstalovat také [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

[Mono](https://www.mono-project.com) se používá pro [ F# interaktivní](../tutorials/fsharp-interactive/index.md) podporovat. Pokud jste v systému Debian nebo Ubuntu, můžete použít následující:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Nainstalovat také [.NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Nainstalujte [Visual Studio s F# podporují](#install-f-with-visual-studio). Tím se nainstaluje všechny komponenty potřebné k zápisu, kompilaci a spouštění F# kódu.

Nainstalovat také [.NET Core SDK](https://www.microsoft.com/net/download/).

---

Bude nutné [Visual Studio Code](https://code.visualstudio.com) nainstalované.

Dále klikněte na ikonu rozšíření a vyhledejte položku "Ionide":

Pouze požadované pro modul plug-in F# podpora ve Visual Studio Code je [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Ale můžete také nainstalovat [Ionide PHISHING](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) zobrazíte [FALEŠNÉ](https://fsharp.github.io/FAKE/) podporu a [Ionide Stáhnout](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) zobrazíte [Stáhnout](https://fsprojects.github.io/Paket/) podporovat. FALEŠNÉ a stáhnout jsou další F# komunitní nástroje pro vytváření projektů a správu závislostí, v uvedeném pořadí.
