---
title: Developer Command Prompt pro Visual Studio
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715853"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Developer Command Prompt pro Visual Studio

Developer Command Prompt pro Visual Studio vám umožní snadněji používat nástroje .NET Framework. Jedná se o příkazový řádek, který automaticky nastaví konkrétní proměnné prostředí. Po otevření Developer Command Prompt můžete zadat příkazy pro [.NET Framework nástroje](index.md) , jako je například `ildasm` nebo `clrver`.

## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Hledání příkazového řádku na svém počítači

V závislosti na verzi sady Visual Studio a všech dalších sadách SDK a úlohách, které jste nainstalovali, může být více příkazů. Pokud následující kroky nefungují, můžete zkusit [soubory vyhledat ručně na svém počítači](#manually-locate-the-files-on-your-machine) nebo [Spustit příkazový řádek v rámci sady Visual Studio](#start-the-command-prompt-from-inside-visual-studio).

### <a name="windows-10"></a>Windows 10

1. Na klávesnici vyberte **spustit** ![klávesu s logem Windows.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) a přejděte k písmenu **v**.

1. Rozbalte složku **Visual Studio 2019** .

1. Vyberte **Developer Command Prompt pro VS 2019** (nebo příkazový řádek, který chcete použít).

   Alternativně můžete spustit zadání názvu příkazového řádku do vyhledávacího pole na hlavním panelu a vybrat výsledek, který chcete zobrazit v seznamu výsledků hledání.

   ![Animovaný obrázek GIF znázorňující chování hledání ve Windows 10](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Na **úvodní** obrazovce stiskněte klávesu s logem Windows ![klávesu s logem Windows na klávesnici.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) například na klávesnici.

1. Na **úvodní** obrazovce stisknutím klávesy **CTRL**+**kartu** otevřete seznam **aplikace** a potom stiskněte klávesu **V**. Tím zobrazíte seznam, který obsahuje všechny nainstalované příkazy sady Visual Studio.

1. Vyberte **Developer Command Prompt pro VS 2019** (nebo příkazový řádek, který chcete použít).

### <a name="windows-7"></a>Windows 7

1. Zvolte **Start** a potom rozbalte **všechny programy**.

1. Vyberte možnost **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt pro vs 2019**nebo příkazový řádek, který chcete použít.

   ![Nabídka Start ve Windows 7 se zvýrazněným příkazovým řádkem](./media/developer-command-prompt-for-vs/windows7-menu.png)

Pokud máte nainstalované jiné sady SDK, jako je například [Sada Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), může se zobrazit další příkazová výzva. V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.

## <a name="manually-locate-the-files-on-your-machine"></a>Ručně vyhledat soubory na počítači

Zkratky pro příkazy, které jste nainstalovali, jsou obvykle umístěny ve složce **nabídky Start** pro aplikaci Visual Studio, například v *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019 \ Visual Studio Tools*. Ale pokud z nějakého důvodu hledání příkazového řádku nepřinese očekávané výsledky, můžete zkusit na svém počítači ručně najít zástupce. Zkuste vyhledat název souboru příkazového řádku, například *VsDevCmd. bat*, nebo přejít do složky Tools, například *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (cesta se mění podle vaší verze sady Visual Studio, edice a umístění instalace).

## <a name="start-the-command-prompt-from-inside-visual-studio"></a>Spuštění příkazového řádku v rámci sady Visual Studio

Pro snazší přístup můžete přidat Developer Command Prompt nebo jakýkoli jiný příkazový řádek do nabídky nástroje v aplikaci Visual Studio. Aby byl nástroj dostupný, přidejte ho do seznamu externích nástrojů. Postup je následující:

1. Otevřít Visual Studio.

1. V okně Start vyberte možnost **pokračovat bez kódu**.

1. Na panelu nabídek vyberte **nástroje** > **externích nástrojích**.

1. V dialogovém okně **externí nástroje** klikněte na tlačítko **Přidat** . Zobrazí se nová položka.

1. Zadejte **název** nové položky nabídky, například `Command Prompt`.

1. Do pole **příkaz** zadejte soubor, který chcete spustit, například `%comspec%` nebo `C:\Windows\System32\cmd.exe`.

1. V poli **argumenty** určete, kde se má najít konkrétní příkazový řádek, který chcete použít, například `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`. Tento příkaz spustí Developer Command Prompt, která je nainstalovaná se sadou Visual Studio 2019 Community. Změňte tuto hodnotu podle vaší verze, edice a umístění sady Visual Studio.

1. V poli **počáteční adresář** zadejte adresář, ve kterém se spustí příkazový řádek. Zvolte hodnotu jako **adresář projektu** výběrem šipky vedle pole.

1. Zvolte **OK** tlačítko.

   ![Dialog externích nástrojů s vyplněnými hodnotami pole](./media/developer-command-prompt-for-vs/add-external-tool.png)

   Nová položka nabídky se přidá a k příkazovému řádku můžete získat přístup z nabídky nástroje.

   ![Položka nabídky příkazového řádku v aplikaci Visual Studio](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a>Viz také:

- [Nástroje .NET Framework](index.md)
- [Správa externích nástrojů](/visualstudio/ide/managing-external-tools)
- [Použití sady nástrojů C++ Microsoft z příkazového řádku](/cpp/build/building-on-the-command-line)
