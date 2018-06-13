---
title: -platform (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec3a7e01e62b60688080fee95cf70e0ed38917f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656175"
---
# <a name="-platform-visual-basic"></a>-platform (Visual Basic)
Určuje, která verze modul common language runtime (CLR) platforma můžete spustit výstupní soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`x86`|Zkompiluje vaše sestavení ke spuštění x86 kompatibilní, 32bitová verze modulu CLR.|  
|`x64`|Zkompiluje vaše sestavení pro 64bitové verze CLR spustit na počítači, který podporuje AMD64 nebo EM64T sada instrukcí.|  
|`Itanium`|Zkompiluje vaše sestavení pro 64bitové verze CLR spustit na počítači s procesorem Itanium.|  
|`arm`|Zkompiluje vaše sestavení pro spouštění na počítači s procesorem ARM (Advanced RISC Machine).|  
|`anycpu`|Zkompiluje vaše sestavení pro spouštěn na libovolné platformě. Aplikace se spustí jako 32bitová aplikace na 32bitové verze systému Windows a jako 64bitové aplikaci v 64bitových verzích systému Windows. Tento příznak je výchozí hodnota.|  
|`anycpu32bitpreferred`|Zkompiluje vaše sestavení pro spouštěn na libovolné platformě. Aplikace se spustí jako 32bitová aplikace na 32bitové a 64bitové verze systému Windows. Tento příznak je platná pouze pro spustitelné soubory (. Soubor EXE) a vyžaduje [!INCLUDE[net_v45](~/includes/net-v45-md.md)].|  
  
## <a name="remarks"></a>Poznámky  
 Použití `-platform` můžete určit typ procesoru cílem výstupní soubor.  
  
 Obecně platí sestavení rozhraní .NET Framework, které jsou napsané v jazyce Visual Basic se spustí stejný bez ohledu na platformu. Existují však někdy s odlišným na různých platformách. Jsou tyto běžné případy:  
  
-   Struktury, které obsahují členy, kteří změnit velikost v závislosti na platformě, jako je například libovolného typu ukazatele.  
  
-   Aritmetika ukazatele, který zahrnuje konstantní velikosti.  
  
-   Nesprávný platformy vyvolání nebo COM deklarace, které používají `Integer` pro obslužné rutiny místo <xref:System.IntPtr>.  
  
-   Přetypování <xref:System.IntPtr> k `Integer`.  
  
-   Pomocí platformy vyvolání nebo zprostředkovatel komunikace s objekty COM s součásti, které nejsou k dispozici na všech platformách.  
  
 **-Platformy** možnost bude zmírnit některé problémy, pokud víte, že jste provedli předpoklady o architektuře kódu se spustí na. Konkrétně:  
  
-   Pokud se rozhodnete platformu 64-bit a spuštění aplikace na počítač s 32bitovou, chybová zpráva obsahuje mnohem dříve a více cíleně problém než chybu, která nastane bez použití tohoto přepínače.  
  
-   Pokud nastavíte `x86` příznak na možnosti a následné spuštění aplikace na počítači 64-bit, bude aplikace spuštěna v subsystému WOW namísto spuštění nativně.  
  
 64bitová verze operačního systému Windows:  
  
-   Sestavení kompilovat s `-platform:x86` se spustí na 32bitová verze modulu CLR spuštěna pod WOW64.  
  
-   Spustitelné soubory kompilovat s `-platform:anycpu` se spustí na 64-bit CLR.  
  
-   Knihovny DLL kompilovat s `-platform:anycpu` se spustí na stejném modulu CLR jako proces, do kterého jej načíst.  
  
-   Spustitelné soubory, které jsou kompilovat s `-platform:anycpu32bitpreferred` se spustí na 32bitová verze modulu CLR.  
  
 Další informace o tom, jak vyvíjet aplikaci spustit v 64bitové verzi systému Windows najdete v tématu [64bitové aplikace](../../../framework/64-bit-apps.md).  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>Chcete-li nastavit - platformy v integrovaném vývojovém prostředí sady Visual Studio  
  
1.  V **Průzkumníku řešení**, zvolte projekt, otevřete **projektu** nabídce a pak klikněte na tlačítko **vlastnosti**.  
  
2.  Na **zkompilovat** kartě, zaškrtněte nebo zrušte **raději 32bitové** zaškrtávací políčko, nebo v **cílový procesor** seznamu, vyberte hodnotu.  
  
     Další informace najdete v tématu [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `-platform` – možnost kompilátoru.  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [/ target (Visual Basic)](target.md)  
 [Visual Basic – kompilátor příkazového řádku](index.md)  
 [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
