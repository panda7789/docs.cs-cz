---
title: 'Postupy: Volání kompilátoru příkazového řádku (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 0b835bb5654574a5aa6f32eede1e942b11e7dcb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656215"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Postupy: Volání kompilátoru příkazového řádku (Visual Basic)
Kompilátor příkazového řádku můžete vyvolat zadáním názvu jeho spustitelného souboru do příkazového řádku, také známé jako v systému MS-DOS. Pokud kompilujete z výchozího příkazového řádku systému Windows, musíte zadat plně kvalifikovanou cestu ke spustitelnému souboru. Pokud chcete přepsat toto výchozí chování, můžete buď použít příkazový řádek sady Visual Studio nebo změnit proměnné prostředí PATH. Oba umožňují zkompilovat z libovolného adresáře jednoduše zadáním názvu kompilátoru.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a>K volání kompilátoru pomocí příkazového řádku Visual Studio  
  
1.  Otevřete složku programu nástroje sady Visual Studio v rámci skupiny pro program Microsoft Visual Studio.  
  
2.  Příkazový řádek sady Visual Studio pro přístup k kompilátor z libovolného adresáře na počítači, můžete použít, pokud je nainstalovaná sada Visual Studio.  
  
3.  Vyvolání příkazového řádku Visual Studia.  
  
4.  Na příkazovém řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.  
  
     Například, pokud jste uložili vašeho zdrojového kódu v adresář s názvem `SourceFiles`, by otevřete příkazový řádek a zadejte `cd SourceFiles` tohoto adresáře. Pokud adresář obsahoval zdrojový soubor s názvem `Source.vb`, může ho zkompilovat zadáním `vbc.exe Source.vb`.  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Chcete-li nastavit proměnné prostředí PATH kompilátoru příkazového řádku pro Windows  
  
1.  Pomocí funkce Windows Search najít Vbc.exe na váš místní disk.  
  
     Přesný název adresáře, kde je umístěný kompilátor závisí na umístění adresáře systému Windows a verzi "Instalace rozhraní .NET Framework". Pokud máte více než jedna verze "nainstalováno rozhraní .NET Framework", musíte určit, kterou verzi má použít (obvykle nejnovější verzi).  
  
2.  Z vaší **spustit** nabídky, klikněte pravým tlačítkem na **Můj počítač**a potom klikněte na **vlastnosti** z místní nabídky.  
  
3.  Klikněte **Upřesnit** a pak klikněte **proměnné prostředí**.  
  
4.  V **systému** proměnné podokně, vyberte **cesta** ze seznamu a klikněte na tlačítko **upravit**.  
  
5.  V **upravit systému** proměnné dialogu, přesuňte kurzor na konec řetězec v **hodnota proměnné** pole a zadejte středníkem (;) a název úplné directory nalezen v kroku 1.  
  
6.  Klikněte na tlačítko **OK** potvrďte provedené úpravy a zavřete dialogová okna.  
  
     Po provedení změny proměnné prostředí PATH, můžete spustit kompilátoru jazyka Visual Basic v příkazovém řádku Windows z libovolného adresáře v počítači.  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>K volání kompilátoru pomocí příkazového řádku systému Windows  
  
1.  Z **spustit** nabídky, klikněte na **Příslušenství** složku a potom otevřete **příkazového řádku Windows**.  
  
2.  Na příkazovém řádku zadejte `vbc.exe` *sourceFileName* a stiskněte klávesu ENTER.  
  
     Například, pokud jste uložili vašeho zdrojového kódu v adresář s názvem `SourceFiles`, by otevřete příkazový řádek a zadejte `cd SourceFiles` tohoto adresáře. Pokud adresář obsahoval zdrojový soubor s názvem `Source.vb`, může ho zkompilovat zadáním `vbc.exe Source.vb`.  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
