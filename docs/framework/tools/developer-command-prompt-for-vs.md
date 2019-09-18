---
title: Developer Command Prompt pro Visual Studio
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
ms.openlocfilehash: 59af252967a18eca858035fb0a3465d909734ddf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044731"
---
# <a name="developer-command-prompt-for-visual-studio"></a>Developer Command Prompt pro Visual Studio

Developer Command Prompt pro Visual Studio vám umožní snadněji používat nástroje .NET Framework. Jedná se o příkazový řádek, který automaticky nastaví konkrétní proměnné prostředí.

> [!div class="button"]
> [Stáhnout Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a>Hledání příkazového řádku na svém počítači

V závislosti na verzi sady Visual Studio a všech dalších sadách SDK, které jste nainstalovali, můžete mít více příkazových výzev. Například 64bitové verze sady Visual Studio poskytují 32bitové a 64bitové verze příkazového řádku. (32 a 64 verze většiny nástrojů jsou stejné, ale některé nástroje mění konkrétní možnosti pro 32-bitové 64 a 16bitové prostředí.) Pokud následující postup nefunguje, můžete zkusit [soubory ručně vyhledat na](#manually-locate-the-files-on-your-machine) počítači nebo [Spustit příkazový řádek z aplikace Visual Studio](#run-the-command-prompt-from-inside-visual-studio).

### <a name="in-windows-10"></a>Ve Windows 10

1. Do vyhledávacího pole na hlavním panelu začněte psát název nástroje, například `dev` nebo. `developer command prompt` Tím se zobrazí seznam nainstalovaných aplikací, které odpovídají vašemu vzoru hledání. Pokud hledáte jiný příkazový řádek, zkuste zadat jiný hledaný výraz, jako je například `prompt`.

2. Vyberte **Developer Command Prompt pro Visual Studio** (nebo příkazový řádek, který chcete použít).

### <a name="in-windows-81"></a>V Windows 8.1

1. Kliknutím![na klávesu s logem Windows na klávesnici na obrazovce Start přejdete na **úvodní** obrazovku.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) například na klávesnici.

2. Na obrazovce **Start** **stiskněte klávesu** **CTRL**+a otevřete seznam **aplikace** a pak zadejte `V`. Tím se zobrazí seznam, který obsahuje všechny nainstalované příkazy sady Visual Studio.

3. Vyberte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).

### <a name="in-windows-8"></a>V systému Windows 8

1. Kliknutím![na klávesu s logem Windows na klávesnici na obrazovce Start přejdete na **úvodní** obrazovku.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) například na klávesnici.

2. Na obrazovce **Start** stiskněte klávesu s ![logem Windows na klávesu s logem Windows na klávesnici.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) `+ Z`.

3. V dolní části obrazovky zvolte ikonu **zobrazení aplikace** a pak zadejte `V`. Tím se zobrazí seznam, který obsahuje všechny nainstalované příkazy sady Visual Studio.

4. Vyberte **Developer Command Prompt** (nebo příkazový řádek, který chcete použít).

### <a name="in-windows-7"></a>V systému Windows 7

1. Klikněte na tlačítko **Start**, rozbalte položku **všechny programy**a poté rozbalte položku **Microsoft Visual Studio**.

2. V závislosti na verzi sady Visual Studio, kterou jste nainstalovali, vyberte možnost **Visual Studio Tools**, **příkazový řádek sady Visual Studio**nebo příkazový řádek, který chcete použít.

Pokud máte nainstalované jiné sady SDK, jako je například [Sada Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), může se zobrazit další příkazová výzva pro architektury ARM, x86 nebo x64. V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.

## <a name="manually-locate-the-files-on-your-machine"></a>Ručně vyhledat soubory na počítači

Zkratky pro příkazy, které jste nainstalovali, se obvykle nacházejí ve složce **nabídky Start** pro Visual Studio, například v C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017 \ Visual Studio Tools. Ale z nějakého důvodu hledání příkazového řádku nepřinese očekávané výsledky, můžete zkusit zástupce na svém počítači najít ručně. Zkuste vyhledat název souboru příkazového řádku, například *VsDevCmd. bat*, nebo přejít do složky Tools, jako je C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\Tools (cesta se mění podle verze sady Visual Studio, edice). a umístění instalace).

## <a name="run-the-command-prompt-from-inside-visual-studio"></a>Spuštění příkazového řádku v rámci sady Visual Studio

Pro snazší přístup můžete přidat Developer Command Prompt sady Visual Studio nebo jakýkoli jiný příkazový řádek do nabídky **nástroje** v aplikaci Visual Studio. Aby byl nástroj dostupný, přidejte ho do seznamu externích nástrojů. Postup je následující:

1. Otevřít Visual Studio.

2. Vyberte nabídku **nástroje** a pak zvolte **externí nástroje**.

3. V dialogovém okně **externí nástroje** klikněte na tlačítko **Přidat** . Zobrazí se nová položka.

4. Zadejte **název** nové položky nabídky, například `Command Prompt`.

5. Do pole **příkaz** zadejte soubor, který chcete spustit, například `%comspec%` nebo. `C:\Windows\System32\cmd.exe`

6. V poli **argumenty** určete, kde se má najít konkrétní příkazový řádek, který chcete použít `/k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\Tools\VsDevCmd.bat"` (Tento příkaz spustí Developer Command Prompt, který je nainstalován se sadou Visual Studio 2017 Enterprise). Změňte tuto hodnotu podle vaší verze, edice a umístění sady Visual Studio.

7. Vyberte hodnotu pro počáteční pole **adresáře** , jako je například **adresář projektu**.

8. Zvolte **OK** tlačítko.

   Nová položka nabídky se přidá a k příkazovému řádku můžete získat přístup z nabídky **nástroje** .

   ![Položka nabídky příkazového řádku v aplikaci Visual Studio](./media/command-prompt-vs-menu.png)

## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Správa externích nástrojů](/visualstudio/ide/managing-external-tools)
