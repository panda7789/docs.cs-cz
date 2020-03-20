---
title: Příkazový řádek pro vývojáře pro Visual Studio
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: f028281d477284acf3ac4dac63f5ddbbd79f5259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715853"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Příkazový řádek pro vývojáře pro Visual Studio

Příkazový řádek pro vývojáře pro visual studio umožňuje snadněji používat nástroje rozhraní .NET Framework. Jedná se o příkazový řádek, který automaticky nastaví specifické proměnné prostředí. Po otevření příkazového řádku pro vývojáře můžete zadat příkazy `clrver`pro nástroje rozhraní [.NET Framework,](index.md) například `ildasm` nebo .

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Hledání příkazového řádku v počítači

V závislosti na verzi sady Visual Studio a dalších nainstalovaných sadách SDK a úlohách můžete mít k dispozici více příkazů. Pokud následující kroky nefungují, můžete zkusit [ručně vyhledat soubory v počítači](#manually-locate-the-files-on-your-machine) nebo spustit [příkazový řádek z aplikace Visual Studio](#start-the-command-prompt-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1. Na klávesnici vyberte **Spustit** ![klávesu s logem Windows.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) a přejděte na písmeno **V**.

1. Rozbalte složku **Visual Studio 2019.**

1. Zvolte **Příkazový řádek pro vývojáře pro VS 2019** (nebo příkazový řádek, který chcete použít).

   Případně můžete začít psát název příkazového řádku do vyhledávacího pole na hlavním panelu a vybrat požadovaný výsledek, protože seznam výsledků začne zobrazovat shody hledání.

   ![Animovaný gif zobrazující chování vyhledávání ve Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Přejděte na **úvodní** obrazovku stisknutím klávesy ![s logem Windows windows na klávesnici.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) na klávesnici.

1. Na **úvodní** obrazovce otevřete stisknutím **klávesy Ctrl**+**kartu** **a** stiskněte **klávesu V**. Tím se zobrazí seznam, který obsahuje všechny nainstalované příkazové příkazy sady Visual Studio.

1. Zvolte **Příkazový řádek pro vývojáře pro VS 2019** (nebo příkazový řádek, který chcete použít).

### <a name="windows-7"></a>Windows 7

1. Zvolte **Spustit** a potom rozbalte **položku Všechny programy**.

1. Zvolte **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt pro VS 2019**nebo příkazový řádek, který chcete použít.

   ![Nabídka Start systému Windows 7 se zvýrazněným příkazovým řádekm](./media/developer-command-prompt-for-vs/windows7-menu.png)

Pokud máte nainstalované jiné sady SDK, například [sady Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), mohou se zobrazit další příkazové příkazové příkazy. V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.

## <a name="manually-locate-the-files-on-your-machine"></a>Ruční vyhledání souborů v počítači

Zástupci nainstalovaných příkazových příkazů jsou obvykle umístěny ve složce **Nabídka Start** pro sadu Visual Studio, například v *%ProgramData%\Microsoft\Windows\Nabídka Start\Programy\Visual Studio 2019\Visual Studio Tools*. Pokud však hledání příkazového řádku z nějakého důvodu nevede k očekávaným výsledkům, můžete se pokusit zástupce v počítači vyhledat ručně. Zkuste vyhledat název souboru příkazového řádku, například *VsDevCmd.bat*, nebo přejděte do složky Nástroje, například *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (změna cesty podle verze, edice a umístění instalace sady Visual Studio).

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>Spuštění příkazového řádku z aplikace Visual Studio

Pro snadnější přístup můžete přidat příkazový řádek pro vývojáře nebo jakýkoli jiný příkazový řádek do nabídky Nástroje v sadě Visual Studio. Chcete-li nástroj zpřístupnit, přidejte jej do seznamu externích nástrojů. Postup je následující:

1. Otevřete sadu Visual Studio.

1. V počátečním okně zvolte **Pokračovat bez kódu**.

1. Na řádku nabídek zvolte **Nástroje externínástroje** > **External Tools**.

1. V dialogovém okně **Externí nástroje** zvolte tlačítko **Přidat.** Zobrazí se nová položka.

1. Zadejte **název** nové položky `Command Prompt`nabídky, například .

1. V poli **Příkaz** zadejte soubor, který chcete `%comspec%` `C:\Windows\System32\cmd.exe`spustit, například nebo .

1. V poli **Argumenty** určete, kde najít konkrétní příkazový řádek, který chcete použít, například `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`. Tento příkaz spustí příkazový řádek pro vývojáře, který je nainstalovaný v komunitě Visual Studio 2019. Změňte tuto hodnotu podle verze, edice a umístění instalace sady Visual Studio.

1. V poli **Počáteční adresář** zadejte adresář, ve kterém bude příkazový řádek spouštěn. Zvolte hodnotu, například **Adresář projektu,** výběrem šipky vedle pole.

1. Zvolte tlačítko **OK.**

   ![Dialogové okno Externí nástroje s vyplněnými hodnotami polí.](./media/developer-command-prompt-for-vs/add-external-tool.png)

   Nová položka nabídky je přidána a přístup k příkazovému řádku můžete získat z nabídky Nástroje.

   ![Položka nabídky příkazového řádku v sadě Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>Viz také

- [.NET Framework – nástroje](index.md)
- [Správa externích nástrojů](/visualstudio/ide/managing-external-tools)
- [Použití sady nástrojů Microsoft C++ z příkazového řádku](/cpp/build/building-on-the-command-line)
