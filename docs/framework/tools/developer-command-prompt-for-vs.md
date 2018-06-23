---
title: Příkazový řádek vývojáře pro sadu Visual Studio
ms.date: 06/18/2018
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e64facffd4face929b28d660ffd5210f127c3bd
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315222"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Příkazový řádek vývojáře pro sadu Visual Studio

Příkazový řádek vývojáře pro sadu Visual Studio automaticky nastaví proměnné prostředí, které vám umožní snadno používat nástroje rozhraní .NET Framework. Do příkazového řádku vývojáře se instaluje s plná nebo komunity edice sady Visual Studio. Není nainstalovaná verze Express sady Visual Studio.

> [!div class="button"]
[Stáhněte si Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

## <a name="searching-for-the-command-prompt-on-your-machine"></a>Hledání příkazového řádku na počítači

Může se zobrazit mnoho okna příkazového řádku, v závislosti na verzi sady Visual Studio a všechny další sady SDK jste nainstalovali. Například 64bitové verze sady Visual Studio poskytují 32bitové a 64bitové verze příkazového řádku. (32bitové a 64bitové verze Většina nástrojů jsou stejné, ale několik nástrojů změnit konkrétní prostředí 32bitové a 64bitové verze.) Pokud tyto kroky nefungují, můžete zkusit [ručně vyhledávání souborů v počítači](#manually-locating-the-files-on-your-machine) nebo [spuštěním příkazu příkazový řádek v sadě Visual Studio](#running-command-prompt-from-inside-visual-studio).

### <a name="in-windows-10"></a>Ve Windows 10

1. Do vyhledávacího pole na hlavním panelu, začněte psát název nástroje, jako například `dev` nebo `developer command prompt`. Tím zobrazíte seznam nainstalovaných aplikací, které odpovídají parametry vyhledávání. Pokud hledáte jiný příkazový řádek, zkuste zadat jiný hledaný termín, jako `prompt`.

2. Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).

### <a name="in-windows-81"></a>Ve Windows 8.1

1. Přejděte na **spustit** obrazovky, stisknutím klávesy s logem Windows ![s logem Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici, např.

2. Na **spustit** obrazovky, stiskněte `CTRL + TAB` otevřete **aplikace** seznamu a pak zadejte `V`. Tím zobrazíte seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazového řádku.

3. Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).

### <a name="in-windows-8"></a>Ve Windows 8

1. Přejděte na **spustit** obrazovky, stisknutím klávesy s logem Windows ![s logem Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici, např.

2. Na **spustit** obrazovky, stiskněte klávesu s logem Windows ![s logem Windows](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.

3. Vyberte **zobrazení aplikace** ikona v dolní části obrazovky a pak zadejte `V`. Tím zobrazíte seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazového řádku.

4. Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).

### <a name="in-windows-7"></a>Ve Windows 7

1. Zvolte **spustit**, rozbalte položku **všechny programy**a potom rozbalte **Microsoft Visual Studio**.

2. V závislosti na verzi sady Visual Studio, které jste nainstalovali, zvolte **nástroje sady Visual Studio**, **Visual Studio – příkazový řádek**, nebo na příkazovém řádku, kterou chcete použít.

Pokud máte dalších sadách SDK nainstalovat, jako [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive) nainstalován, mohou se zobrazit další příkaz vyzve k zadání ARM, x 86 nebo x64 architektury. V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.

## <a name="manually-locating-the-files-on-your-machine"></a>Ručně vyhledávání souborů v počítači

Obvykle jsou umístěny zástupce pro vás příkaz požádá jste nainstalovali na **nabídce Start** složku pro sadu Visual Studio, například v nástroji Studio 2017\Visual C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio. Ale pokud z nějakého důvodu není vyhledávání pro příkazový řádek přineste očekávané výsledky, můžete zkusit ruční nalezení zástupce na váš počítač. Zkuste vyhledat název souboru příkazového řádku, jako například *VsDevCmd.bat*, nebo přejděte do složky nástroje, například C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (cesta změny podle vaší Visual Studio verze, vydání a instalace umístění).

## <a name="running-command-prompt-from-inside-visual-studio"></a>Spuštění příkazu příkazový řádek v sadě Visual Studio

Pro snadnější přístup můžete přidat příkazového řádku vývojáře Visual Studio nebo jiné příkazového řádku nabídky Nástroje v sadě Visual Studio, přidáním do seznamu externí nástroje. Toto je, jak můžete provést, který:

1. Otevřete Visual Studio.

2. Vyberte **nástroje** nabídky a zvolte **externích nástrojů**.

3. Na **externích nástrojů** dialogovém okně vyberte **přidat** tlačítko. Nová položka.

4. Zadejte **název** pro novou položku nabídky jako `Command Prompt`.

5. V **příkaz** pole, zadejte soubor, který chcete spustit jako `%comspec%` nebo `C:\Windows\System32\cmd.exe`.

6. V **argumenty** pole, zadejte, kam chcete najít konkrétní příkazového řádku, kterou chcete použít jako `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Tento příkaz spustí příkazový řádek vývojáře, který je nainstalován pomocí Visual Studio 2017 Enterprise). Změňte tuto hodnotu podle vašeho umístění verze, vydání a instalace sady Visual Studio.

7. Vyberte hodnotu pro **directory počáteční** pole, jako **adresáři projektu**.

8. Vyberte **OK** tlačítko.

Poté při přidání nové položky nabídky a dostanete příkazového řádku **nástroje** nabídky.

## <a name="see-also"></a>Viz také:

 [Nástroje](../../../docs/framework/tools/index.md)  
 [Správa externích nástrojů](/visualstudio/ide/managing-external-tools)  
