---
title: Příkazový řádek vývojáře pro sadu Visual Studio
ms.date: 03/30/2017
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
ms.openlocfilehash: d3ff897e37e3fa2f7202a54c05c8093ba05282c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402025"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Příkazový řádek vývojáře pro sadu Visual Studio
Příkazový řádek vývojáře pro sadu Visual Studio automaticky nastaví proměnné prostředí, které vám umožní snadno používat nástroje rozhraní .NET Framework. Do příkazového řádku vývojáře se instaluje s plná nebo komunity edice sady Visual Studio. Není nainstalovaná verze Express sady Visual Studio.  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a>Hledání příkazového řádku na počítači  
 Může se zobrazit více příkazového řádku, v závislosti na verzi sady Visual Studio a všechny další sady SDK jste nainstalovali. Například 64bitové verze sady Visual Studio poskytují 32bitové a 64bitové verze příkazového řádku. (32bitové a 64bitové verze jsou u většiny nástrojů stejné, u několika nástrojů se však 32bitové a 64bitové prostředí liší.) Pokud nejsou k dispozici níže uvedené kroky, můžete zkusit [ručně vyhledávání souborů v počítači](#alternative) nebo [spuštěním příkazu příkazový řádek v sadě Visual Studio](#visualstudio).  
  
 **Ve Windows 10**  
  
1.  Otevřete **spustit** nabídky, stisknutím klávesy s logem Windows ![s logem Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici, např.  
  
2.  Na **spustit** nabídky, zadejte `dev`. Otevře se seznam nainstalovaných aplikací, které odpovídají parametry vyhledávání. Pokud hledáte jiný příkazový řádek, zkuste zadat jiný hledaný termín, jako `prompt`.  
  
3.  Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).  
  
 **Ve Windows 8.1**  
  
1.  Přejděte na **spustit** obrazovky, stisknutím klávesy s logem Windows ![s logem Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici, např.  
  
2.  Na **spustit** obrazovky, stiskněte `CTRL + TAB` otevřete **aplikace** seznamu a pak zadejte `V`. Otevře se seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazového řádku.  
  
3.  Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).  
  
 **Ve Windows 8**  
  
1.  Přejděte na **spustit** obrazovky, stisknutím klávesy s logem Windows ![s logem Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici, např.  
  
2.  Na **spustit** obrazovky, stiskněte klávesu s logem Windows ![s logem Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.  
  
3.  Vyberte **zobrazení aplikace** ikona v dolní části obrazovky a pak zadejte `V`. Otevře se seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazového řádku.  
  
4.  Vyberte **příkazový řádek vývojáře** (nebo na příkazovém řádku, kterou chcete použít).  
  
 **Ve Windows 7**  
  
1.  Zvolte **spustit**, rozbalte položku **všechny programy**a potom rozbalte **Microsoft Visual Studio**.  
  
2.  V závislosti na verzi sady Visual Studio, které jste nainstalovali, zvolte **nástroje sady Visual Studio**, **Visual Studio – příkazový řádek**, nebo na příkazovém řádku, kterou chcete použít.  
  
 Pokud máte [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) nebo [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) nainstalován, mohou se zobrazit další příkaz vyzve k zadání ARM, x 86 nebo x64 architektury. V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a>Ručně vyhledávání souborů v počítači  
  Obvykle bude provedeno zástupce pro vás příkaz požádá jste nainstalovali na **nabídce Start** složku pro sadu Visual Studio, například C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Nástroje.    Ale pokud z nějakého důvodu není vyhledávání pro příkazový řádek yield očekávané výsledky, můžete zkusit ruční nalezení zástupce na počítači-li ji používat.   Zkuste vyhledat název souboru příkazového řádku, jako je například VsDevCmd.bat nebo přejděte do složky nástroje, jako je například C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\Tools (cesta se změní podle umístění instalace a verzi vaší aplikace Visual Studio).  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a>Spuštění příkazu příkazový řádek v sadě Visual Studio  
 Pro snadnější přístup můžete přidat příkazového řádku vývojáře Visual Studio nebo jiné příkazového řádku nabídky Nástroje v sadě Visual Studio, přidáním do seznamu externí nástroje. Toto je, jak můžete provést, který:  
  
1.  Otevřete Visual Studio.  
  
2.  Vyberte **nástroje** nabídky a zvolte **externích nástrojů...** .  
  
3.  Na **externích nástrojů** dialogovém okně vyberte **přidat** tlačítko. Nová položka  
  
4.  Zadejte **název** pro novou položku nabídky jako `Command Prompt`.  
  
5.  V **příkaz** pole, zadejte soubor, který chcete spustit jako `%comspec%` nebo `C:\Windows\System32\cmd.exe` .  
  
6.  V **argumenty** pole, zadejte, kam chcete najít konkrétní příkazového řádku, kterou chcete použít jako `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (tím se spustí příkazový řádek vývojáře nainstalované s [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]). Tato hodnota je potřeba změnit podle vašeho umístění instalace a verzi sady Visual Studio.  
  
7.  Vyberte hodnotu pro **directory počáteční** pole, jako **adresáři projektu** .  
  
8.  Vyberte **OK** tlačítko.  
  
 Poté při přidání nové položky nabídky a dostanete příkazového řádku **nástroje** nabídky.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Správa externích nástrojů](/visualstudio/ide/managing-external-tools)
