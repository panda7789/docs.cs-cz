---
title: 'Postupy: Volání kompilátoru příkazového řádku (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: d2d193f8c3d483ff87fe719919982e8c3473ec0b
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221840"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Postupy: Volání kompilátoru příkazového řádku (Visual Basic)
Kompilátor příkazového řádku můžete vyvolat zadáním názvu jeho spustitelného souboru do příkazového řádku, označované také jako příkazový. Pokud kompilujete z výchozího příkazového řádku Windows, je nutné zadat úplnou cestu ke spustitelnému souboru. Chcete-li přepsat toto výchozí chování, můžete použít příkazový řádek pro vývojáře pro sadu Visual Studio nebo upravit proměnné prostředí PATH. Umožňují z libovolného adresáře kompilovat pouze zadáním názvu kompilátoru.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>K vyvolání kompilátoru pomocí příkazového řádku pro vývojáře pro sadu Visual Studio  
  
1.  Otevřete složku program Visual Studio Tools v rámci skupiny pro program Microsoft Visual Studio.  
  
2.  Developer Command Prompt pro sadu Visual Studio můžete použít pro přístup k kompilátor z libovolného adresáře v počítači, pokud je nainstalována aplikace Visual Studio.  
  
3.  Vyvolání Developer Command Prompt pro sadu Visual Studio.  
  
4.  Na příkazovém řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.  
  
     Například, pokud váš zdrojový kód jste uložili v adresáři s názvem `SourceFiles`, by otevřete příkazový řádek a zadejte `cd SourceFiles` pro přechod do této složky. Pokud adresář obsahuje zdrojový soubor s názvem `Source.vb`, může zkompilovat jej tak, že zadáte `vbc.exe Source.vb`.  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Chcete-li nastavit proměnné prostředí PATH v kompilátoru pro příkazový řádek Windows  
  
1.  Pomocí funkce Windows Search hledání Vbc.exe na místním disku.  
  
     Přesný název adresáře, kde je umístěn kompilátor závisí na umístění adresáře Windows a verzí "nainstalováno rozhraní .NET Framework". Pokud máte více než jednu verzi "Instalace rozhraní .NET Framework", musíte určit, která verze se má použít (obvykle na nejnovější verzi).  
  
2.  Z vaší **Start** nabídky, klikněte pravým tlačítkem na **tento počítač**a potom klikněte na tlačítko **vlastnosti** z místní nabídky.  
  
3.  Klikněte na tlačítko **Upřesnit** kartu a potom klikněte na tlačítko **proměnné prostředí**.  
  
4.  V **systému** podokno proměnných, vyberte **cesta** ze seznamu a klikněte na tlačítko **upravit**.  
  
5.  V **upravit systému** proměnné dialogové okno, přesuňte kurzor na konec řetězce **hodnotu proměnné** pole a zadejte středníkem (;) za nímž následuje název úplné adresáře v kroku 1.  
  
6.  Klikněte na tlačítko **OK** potvrzení úprav a zavřete dialogová okna.  
  
     Po změně proměnné prostředí PATH, můžete spustit kompilátor jazyka Visual Basic v příkazovém řádku Windows z libovolného adresáře v počítači.  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>K volání kompilátoru příkazového řádku Windows  
  
1.  Z **Start** nabídky, klikněte na **Příslušenství** složku a pak otevřete **příkazový řádek Windows**.  
  
2.  Na příkazovém řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.  
  
     Například, pokud váš zdrojový kód jste uložili v adresáři s názvem `SourceFiles`, by otevřete příkazový řádek a zadejte `cd SourceFiles` pro přechod do této složky. Pokud adresář obsahuje zdrojový soubor s názvem `Source.vb`, může zkompilovat jej tak, že zadáte `vbc.exe Source.vb`.  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
