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
ms.openlocfilehash: 1692b93e09ec972e537e4a375774eeeb865bd58c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043432"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a>Postupy: Podmíněná kompilace pomocí atributu Trace a Debug
Při ladění aplikace během vývoje přejde výstup trasování i ladění do okna výstup v aplikaci Visual Studio. Chcete-li však do nasazené aplikace zahrnout funkce trasování, je nutné zkompilovat vaše instrumentované aplikace s povolenou direktivou překladače **trasování** . To umožňuje zkompilovat kód pro vydanou verzi aplikace. Pokud nepovolíte direktivu **Trace** , veškerý trasovací kód se během kompilace ignoruje a není zahrnutý do spustitelného kódu, který nasadíte.  
  
 Metody trasování i ladění mají přidružené podmíněné atributy. Například pokud má podmíněný atribut pro trasování **hodnotu true**, všechny příkazy trasování jsou zahrnuty v rámci sestavení (zkompilovaného souboru. exe nebo. dll); Pokud má atribut **Trace** podmíněný **hodnotu false**, nejsou k dispozici příkazy TRACE.  
  
 Můžete mít pro sestavení zapnutý podmíněný atribut **trasování** nebo **ladění** , nebo ani jeden z nich. Proto existují čtyři typy sestavení: **Ladění**, **trasování**, obojí nebo ani jeden z nich. Některá sestavení vydaných verzí pro produkční nasazení mohou obsahovat ani jednu z těchto možností: Většina sestavení ladění obsahuje obě.  
  
 Nastavení kompilátoru pro aplikaci můžete zadat několika způsoby:  
  
- Stránky vlastností  
  
- Příkazový řádek  
  
- **#CONST** (pro Visual Basic) a **#define** (pro C#)  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a>Změna nastavení kompilace z dialogového okna stránky vlastností  
  
1. Klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení**.  
  
2. V místní nabídce vyberte možnost **vlastnosti** .  
  
    - V Visual Basic klikněte v levém podokně stránky vlastností na kartu **kompilovat** a pak klikněte na tlačítko **Upřesnit možnosti kompilace** . zobrazí se dialogové okno **Upřesnit nastavení kompilátoru** . Zaškrtněte políčka pro nastavení kompilátoru, které chcete povolit. Zrušte zaškrtnutí políček u nastavení, které chcete zakázat.  
  
    - V C#klikněte na kartu **sestavení** v levém podokně stránky vlastností a zaškrtněte políčka pro nastavení kompilátoru, která chcete povolit. Zrušte zaškrtnutí políček u nastavení, které chcete zakázat.  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a>Kompilace instrumentované kódu pomocí příkazového řádku  
  
1. Nastavte podmíněný přepínač kompilátoru na příkazovém řádku. Kompilátor bude obsahovat kód trasování nebo ladění ve spustitelném souboru.  
  
     Například následující instrukce kompilátoru, která je zadána v příkazovém řádku, by zahrnovala váš kód trasování ve zkompilovaném spustitelném souboru:  
  
     Pro Visual Basic: **Vbc-r:System.dll-d:TRACE = True-d:Debug = false MyApplication. vb**  
  
     Pro C#: **CSC-r:System.dll-d:Trace-d:Debug = false MyApplication.cs**  
  
    > [!TIP]
    > Chcete-li zkompilovat více než jeden soubor aplikace, ponechte prázdné místo mezi názvy souborů, například **MyApplication1. vb MyApplication2. vb MyApplication3. vb** nebo **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.  
  
     Význam direktiv podmíněné kompilace použitých ve výše uvedených příkladech je následující:  
  
    |– Direktiva|Význam|  
    |---------------|-------------|  
    |`vbc`|Visual Basic – kompilátor|  
    |`csc`|C#přepínač|  
    |`-r:`|Odkazuje na externí sestavení (EXE nebo DLL).|  
    |`-d:`|Definuje symbol podmíněné kompilace.|  
  
    > [!NOTE]
    > Je nutné provést trasování nebo ladění velkými písmeny. Další informace o příkazech podmíněné kompilace získáte zadáním `vbc /?` příkazu (pro Visual Basic) `csc /?` nebo ( C#pro) v příkazovém řádku. Další informace naleznete v tématu [sestavování z příkazového řádku](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) nebo [vyvolání kompilátoru příkazového řádku](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a>Provedení podmíněné kompilace pomocí #CONST nebo #define  
  
1. Zadejte odpovídající příkaz pro programovací jazyk v horní části souboru zdrojového kódu.  
  
    |Jazyk|Příkaz|Výsledek|  
    |--------------|---------------|------------|  
    |**Visual Basic**|**#CONST TRACE = True**|Povolí trasování|  
    ||**#CONST TRACE = false**|Zakáže trasování|  
    ||**#CONST DEBUG = true**|Povolí ladění|  
    ||**#CONST DEBUG = false**|Zakáže ladění.|  
    |**C#**|**TRASOVÁNÍ #define**|Povolí trasování|  
    ||**TRASOVÁNÍ #undef**|Zakáže trasování|  
    ||**#define ladění**|Povolí ladění|  
    ||**#undef ladění**|Zakáže ladění.|  
  
### <a name="to-disable-tracing-or-debugging"></a>Zakázání trasování nebo ladění  
  
Odstraní direktivu kompilátoru ze zdrojového kódu.  
  
\- nebo –  
  
Odkomentujte direktivu kompilátoru.  
  
> [!NOTE]
> Až budete připraveni kompilovat, můžete buď zvolit možnost **sestavit** z nabídky **sestavení** , nebo použít metodu příkazového řádku, ale bez zadání **d:** pro definování symbolů podmíněné kompilace.  
  
## <a name="see-also"></a>Viz také:

- [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Postupy: Vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Postupy: Nastavení proměnných prostředí pro příkazový řádek sady Visual Studio](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [Postupy: Volání kompilátoru příkazového řádku](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
