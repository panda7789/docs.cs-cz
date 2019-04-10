---
title: Developer Command Prompt for Visual Studio
ms.date: 08/14/2018
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
ms.openlocfilehash: cc88106a54a00b4b12e5043da7961791a98102c0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344361"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Developer Command Prompt for Visual Studio

Developer Command Prompt pro sadu Visual Studio umožňuje snadno používat nástroje rozhraní .NET Framework. Je příkazový řádek, který automaticky nastavuje určité proměnné prostředí.

> [!div class="button"]
> [Stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Hledat příkazový řádek na svém počítači

Můžete mít více příkazových řádků, v závislosti na verzi sady Visual Studio a všech dodatečných sad SDK si nainstalujete. Například 64bitové verze sady Visual Studio poskytují 32bitové a 64bitové verze příkazového řádku. (32bitové a 64bitové verze Většina nástrojů jsou stejné, ale u několika nástrojů měnit konkrétní 32bitové a 64bitové prostředí) Pokud tyto kroky nefungují, můžete zkusit [ručně vyhledat soubory na svém počítači](#manually-locate-the-files-on-your-machine) nebo [spustit z příkazového řádku v sadě Visual Studio](#run-the-command-prompt-from-inside-visual-studio).

### <a name="in-windows-10"></a>In Windows 10

1. Do vyhledávacího pole na hlavním panelu, začněte psát název nástroje, jako například `dev` nebo `developer command prompt`. Tím se zobrazí seznam nainstalovaných aplikací, které odpovídají vaší vyhledávací vzory. Pokud hledáte různých příkazového řádku, zkuste zadat jinou hledaný termín, jako `prompt`.

2. Zvolte **Developer Command Prompt pro sadu Visual Studio** (nebo příkazový řádek, který chcete použít).

### <a name="in-windows-81"></a>Ve Windows 8.1

1. Přejděte na **Start** obrazovku stisknutím klávesy s logem Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici pro příklad.

2. Na **Start** obrazovky, stiskněte klávesu **Ctrl**+**kartu** otevřít **aplikace** seznamu a pak zadejte `V`. Zobrazí seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazové řádky.

3. Zvolte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).

### <a name="in-windows-8"></a>V systému Windows 8

1. Přejděte na **Start** obrazovku stisknutím klávesy s logem Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") na klávesnici pro příklad.

2. Na **Start** obrazovky, stiskněte klávesu s logem Windows ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.

3. Zvolte **aplikace zobrazit** ikony v dolní části obrazovky a pak zadejte `V`. Zobrazí seznam, který zahrnuje všechny nainstalované sady Visual Studio příkazové řádky.

4. Zvolte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).

### <a name="in-windows-7"></a>Ve Windows 7

1. Zvolte **Start**, rozbalte **všechny programy**a potom rozbalte **sady Microsoft Visual Studio**.

2. V závislosti na verzi sady Visual Studio jste nainstalovali, zvolte **Visual Studio Tools**, **příkazový řádek sady Visual Studio**, nebo na příkazovém řádku, který chcete použít.

Pokud máte jiné sady SDK nainstalované, jako [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), mohou vidět další příkazové řádky pro ARM, x 86 nebo x64 architektury. V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.

## <a name="manually-locate-the-files-on-your-machine"></a>Ruční nalezení souborů v počítači

Obvykle, klávesové zkratky pro příkaz vyzve k instalaci jsou umístěny na **nabídky Start** složka pro sadu Visual Studio, jako je například nástroje Studio 2017\Visual C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio. Ale pokud z nějakého důvodu není vyhledávání pro příkazový řádek přinést očekávané výsledky, můžete zkusit ruční nalezení klávesovou zkratku na svém počítači. Zkuste vyhledat název souboru příkazového řádku, jako například *VsDevCmd.bat*, nebo přejděte do složky nástrojů, jako je například C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (cesta změny podle vašeho Vizuálu Umístění sady Studio verze, vydání a instalace).

## <a name="run-the-command-prompt-from-inside-visual-studio"></a>Spusťte z příkazového řádku v sadě Visual Studio

Pro snadnější přístup, můžete přidat příkazový řádek sady Visual Studio pro vývojáře, nebo jiné příkazového řádku **nástroje** nabídky v sadě Visual Studio. Zpřístupnění nástroje, přidejte ho do seznam externích nástrojů. Postup je následující:

1. Otevřít Visual Studio.

2. Vyberte **nástroje** nabídky a klikněte na tlačítko **externích nástrojů**.

3. Na **externích nástrojů** dialogového okna zvolte **přidat** tlačítko. Zobrazí se nová položka.

4. Zadejte **Title** pro novou položku nabídky, jako `Command Prompt`.

5. V **příkaz** zadejte soubor, který chcete spustit, jako například `%comspec%` nebo `C:\Windows\System32\cmd.exe`.

6. V **argumenty** pole, zadejte, kam chcete najít konkrétní příkazového řádku, který chcete použít jako `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Tento příkaz spustí příkazový řádek vývojáře, který je nainstalován se sadou Visual Studio 2017 Enterprise). Změňte tuto hodnotu podle umístěním verze, vydání a instalace sady Visual Studio.

7. Zvolte hodnotu **výchozí adresář** pole, jako například **adresáře projektu**.

8. Zvolte **OK** tlačítko.

   Přidat novou položku nabídky, a dostanete příkazový řádek z **nástroje** nabídky.

   ![Položka nabídky příkazového řádku v sadě Visual Studio](media/command-prompt-vs-menu.png)

## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Správa externích nástrojů](/visualstudio/ide/managing-external-tools)
