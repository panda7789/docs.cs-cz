---
title: 'Postupy: Podmíněná kompilace pomocí atributu Trace a Debug'
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45e62fed53999636e23693ad7e61fedf21bc5423
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390572"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a>Postupy: Podmíněná kompilace pomocí atributu Trace a Debug
Při ladění aplikace během vývoje, vaše trasování a ladění výstupu přejít do okna výstupu v sadě Visual Studio. Zahrnout trasování funkce nasazené aplikace, musí však zkompilovat instrumentovaného aplikací s **trasování** kompilátoru direktiva povolena. To umožňuje trasování kódu ke kompilaci do verzi vaší aplikace. Pokud nepovolíte **trasování** direktivy, všechny trasování kódu se ignoruje při kompilaci a není součástí spustitelného kódu, kterou chcete nasadit.  
  
 Trasování a ladění metody přidruženy podmíněné atributy. Například pokud podmíněný atribut pro trasování je **true**, jsou součástí sestavení (Soubor kompilované .exe nebo .dll); všechny příkazy trasování, pokud **trasování** podmíněný atribut je **false**, nejsou zahrnuty trasovacích příkazů.  
  
 Může mít buď **trasování** nebo **ladění** podmíněný atribut zapnuli pro sestavení, nebo obojí nebo ani jeden z nich. Proto existují čtyři typy sestavení: **ladění**, **trasování**, oba, nebo žádný z nich. Některé verze sestavení pro produkční nasazení může obsahovat ani; Většina ladění sestavení obsahovat obě.  
  
 Můžete zadat nastavení kompilátoru pro vaši aplikaci několika způsoby:  
  
-   Stránky vlastností  
  
-   Příkazový řádek  
  
-   **#CONST** (pro Visual Basic) a **#define** (pro jazyk C#)  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a>Chcete-li změnit nastavení kompilace z dialogového okna Vlastnosti stránky  
  
1.  Klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení**.  
  
2.  Zvolte **vlastnosti** z místní nabídky.  
  
    -   V jazyce Visual Basic, klikněte na tlačítko **zkompilovat** v levém podokně na stránku vlastností a potom klikněte na tlačítko **Upřesnit možnosti kompilace** tlačítko pro zobrazení **Upřesnit nastavení kompilátoru**dialogové okno. Zaškrtněte políčka pro kompilátor – nastavení, které chcete povolit. Zrušte zaškrtnutí políčka pro nastavení, které chcete zakázat.  
  
    -   V jazyce C#, klikněte **sestavení** v levém podokně na stránku vlastností a potom zaškrtněte políčka pro kompilátor – nastavení, které chcete povolit. Zrušte zaškrtnutí políčka pro nastavení, které chcete zakázat.  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a>Ke kompilaci instrumentovány v kódu pomocí příkazového řádku  
  
1.  Nastavte podmíněný kompilátoru přepínač na příkazovém řádku. Kompilátor bude zahrnovat trasování nebo ladění kódu v spustitelný soubor.  
  
     Například následující pokyn kompilátoru zadat na příkazovém řádku bude zahrnovat trasování kódu v kompilovaném spustitelný soubor:  
  
     V jazyce Visual Basic: **Vbc –-r:System.dll -d: trasování = TRUE -d: ladění = FALSE MyApplication.vb**  
  
     Pro jazyk C#: **csc-r:System.dll -d: trasování -d: ladění = FALSE MyApplication.cs**  
  
    > [!TIP]
    >  Chcete-li kompilovat více než jeden soubor aplikace, ponechte prázdné místo mezi názvy souborů, například **MyApplication1.vb MyApplication2.vb MyApplication3.vb** nebo **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.  
  
     Význam direktivy podmíněné kompilace použít v uvedených příkladech je následující:  
  
    |– Direktiva|Význam|  
    |---------------|-------------|  
    |`vbc`|Visual Basic – kompilátor|  
    |`csc`|Kompilátor jazyka C#|  
    |`-r:`|Odkazuje na externí sestavení (EXE nebo DLL)|  
    |`-d:`|Definuje symbol Podmíněná kompilace|  
  
    > [!NOTE]
    >  Je nutné zadat trasování nebo ladění se velká písmena. Další informace o příkazech Podmíněná kompilace zadejte `vbc /?` (pro Visual Basic) nebo `csc /?` (pro jazyk C#) na příkazovém řádku. Další informace najdete v tématu [sestavení z příkazového řádku](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) nebo [volání kompilátoru příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a>K provedení Podmíněná kompilace pomocí #CONST nebo #define  
  
1.  Zadejte příkaz vhodné pro programovací jazyk v horní části souboru se zdrojovým kódem.  
  
    |Jazyk|Příkaz|Výsledek|  
    |--------------|---------------|------------|  
    |**Visual Basic**|**#CONST trasování = true**|Umožňuje trasování|  
    ||**#CONST trasování = false**|Zakáže trasování|  
    ||**#CONST ladění = true**|Povolí režim ladění|  
    ||**#CONST ladění = false**|Zakáže ladění|  
    |**C#**|**#define trasování**|Umožňuje trasování|  
    ||**#undef trasování**|Zakáže trasování|  
    ||**#define ladění**|Povolí režim ladění|  
    ||**#undef ladění**|Zakáže ladění|  
  
### <a name="to-disable-tracing-or-debugging"></a>Chcete-li zakázat trasování nebo ladění  
  
Direktivy kompilátoru odstraňte z vašeho zdrojového kódu.  
  
\- nebo –  
  
Komentář – direktiva kompilátoru.  
  
> [!NOTE]
>  Jakmile budete připraveni k sestavení, můžete buď zvolit **sestavení** z **sestavení** nabídky, nebo pomocí příkazového řádku, ale bez zadání **d:** k definování podmíněného kompilace symboly.  
  
## <a name="see-also"></a>Viz také  
 [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Postupy: Vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Postup: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [Postupy: Volání kompilátoru příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
