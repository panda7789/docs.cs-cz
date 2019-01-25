---
title: -platform (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 4455167577871cc6251c248d20e32f04ce11410e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671587"
---
# <a name="-platform-visual-basic"></a>-platform (Visual Basic)
Určuje, jaké verze platformy common language runtime (CLR) můžete spustit výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`x86`|Kompiluje sestavení ke spuštění v 32 bitů, které je kompatibilní x86 CLR.|  
|`x64`|Kompiluje sestavení ke spuštění v 64bitovém modulu CLR na počítači, který podporuje AMD64 nebo EM64T instrukční sadu.|  
|`Itanium`|Kompiluje sestavení ke spuštění v 64bitovém modulu CLR na počítači s procesorem Itanium.|  
|`arm`|Kompiluje sestavení ke spuštění v počítači s procesorem ARM (Advanced RISC Machine).|  
|`anycpu`|Kompiluje sestavení pro spouštěn na libovolné platformě. Aplikace se spustí jako 32bitová aplikace ve 32bitové verze Windows a jako na 64bitovými verzemi Windows 64-bit aplikace. Výchozí hodnota je tento příznak.|  
|`anycpu32bitpreferred`|Kompiluje sestavení pro spouštěn na libovolné platformě. Aplikace poběží jako 32bitová aplikace ve 32bitové a 64bitové verze Windows. Tento příznak je platná pouze pro spustitelné soubory (. Soubor EXE) a vyžaduje [!INCLUDE[net_v45](~/includes/net-v45-md.md)].|  
  
## <a name="remarks"></a>Poznámky  
 Použití `-platform` možnost určit typ procesoru cílem výstupního souboru.  
  
 Sestavení rozhraní .NET Framework, které jsou napsané v jazyce Visual Basic, poběží stejný bez ohledu na platformu. Existují však případy, které se chovají jinak na různých platformách. Tyto běžné případy jsou:  
  
-   Struktury, které obsahují členy, které se mění velikost v závislosti na platformě, jako je například libovolný typ ukazatele.  
  
-   Aritmetika ukazatele, který obsahuje konstantní velikostí.  
  
-   Nesprávný platformu vyvolání nebo deklarace modelu COM, které používají `Integer` pro popisovače místo <xref:System.IntPtr>.  
  
-   Přetypování <xref:System.IntPtr> k `Integer`.  
  
-   Pomocí platformy vyvolat nebo komunikace s objekty COM s komponentami, které neexistují na všech platformách.  
  
 **-Platform** možnost zmírnit některé problémy, pokud víte, že jste provedli předpoklady o architektuře váš kód poběží. Konkrétně:  
  
-   Pokud se rozhodnete cílit na 64bitové platformě a v 32bitovém počítači při spuštění aplikace, chybová zpráva obsahuje mnohem dříve a více zaměřuje se na problému než chybu, která probíhá, aniž by tento přepínač.  
  
-   Pokud jste nastavili `x86` příznak na možnosti a následně při spuštění aplikace na 64bitovém počítači, bude aplikace spuštěna v subsystému WOW, místo spouštění nativně.  
  
 V operačním systému Windows 64-bit:  
  
-   Sestavení zkompilovaná `-platform:x86` se spustí na 32-bit CLR spuštěna v modulu WOW64.  
  
-   Spustitelné soubory zkompilovaná `-platform:anycpu` se spustí na 64bitový modul CLR.  
  
-   Knihovna DLL zkompilovaná `-platform:anycpu` se spustí na stejném modulu CLR jako proces, do kterého ji načíst.  
  
-   Spustitelné soubory, které jsou kompilovány pomocí `-platform:anycpu32bitpreferred` se spustí na 32-bit CLR.  
  
 Další informace o tom, jak vyvinout aplikaci v 64bitové verzi Windows, naleznete v tématu [64bitové aplikace](../../../framework/64-bit-apps.md).  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>Chcete-li nastavit - platform v integrovaném vývojovém prostředí sady Visual Studio  
  
1.  V **Průzkumníka řešení**, vyberte projekt, otevřete **projektu** nabídky a pak klikněte na tlačítko **vlastnosti**.  
  
2.  Na **kompilaci** kartu, zaškrtněte nebo zrušte zaškrtnutí **preferovat 32bitovou verzi** zaškrtávací políčko, nebo v **cílový procesor** , zvolte hodnotu.  
  
     Další informace najdete v tématu [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `-platform` – možnost kompilátoru.  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Viz také:
- [/ target (Visual Basic)](target.md)
- [Visual Basic Command-Line Compiler](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
