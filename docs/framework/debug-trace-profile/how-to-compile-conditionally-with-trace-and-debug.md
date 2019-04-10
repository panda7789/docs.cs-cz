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
ms.openlocfilehash: a010b2ee1de17741b2d0bdd6e7c50d5f602256ac
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298575"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a>Postupy: Podmíněná kompilace pomocí atributu Trace a Debug
Při ladění aplikace během vývoje, přejděte do okna výstup v sadě Visual Studio vaší trasování a ladění výstupu. Ale musíte zahrnout funkce sledování nasazených aplikací, zkompilovat instrumentované aplikace s využitím **trasování** direktivy kompilátoru povolena. To umožňuje trasování kódu se zkompiluje do verze vaší aplikace. Pokud nepovolíte **trasování** direktiv, všechna trasování kódu je ignorována během kompilace a není součástí spustitelný kód, který nasadíte.  
  
 Trasování a ladění metody mají přiřazeny podmíněné atributy. Například pokud podmíněný atribut pro trasování je **true**, všechny příkazy trasování jsou zahrnuty v rámci sestavení (soubor zkompilovaný .exe nebo .dll); Pokud **trasování** atribut conditional je **false**, příkazů trasování nejsou zahrnuty.  
  
 Může mít buď **trasování** nebo **ladění** atribut conditional zapnuté pro sestavení, nebo obou nebo ani jeden. Proto existují čtyři typy sestavení: **Ladění**, **trasování**obou nebo ani jedna. Některé buildy vydaných verzí pro produkční nasazení mohou obsahovat ani; většinu ladicích sestavení obsahují.  
  
 Můžete zadat nastavení kompilátoru pro vaši aplikaci několika způsoby:  
  
-   Stránky vlastností  
  
-   Příkazový řádek  
  
-   **#CONST** (pro jazyk Visual Basic) a **#define** (pro C#)  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a>Chcete-li změnit nastavení kompilace z dialogového okna stránky vlastností  
  
1. Klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení**.  
  
2. Zvolte **vlastnosti** z místní nabídky.  
  
    -   V jazyce Visual Basic, klikněte na tlačítko **kompilace** kartu v levém podokně na stránce vlastností a pak klikněte na tlačítko **Upřesnit možnosti kompilace** tlačítka pro zobrazení **pokročilé nastavení kompilátoru**dialogové okno. Zaškrtněte políčka pro nastavení kompilátoru, které chcete povolit. Zrušte zaškrtnutí políček u nastavení, které chcete zakázat.  
  
    -   V C#, klikněte na tlačítko **sestavení** kartu v levém podokně na stránce vlastností a pak zaškrtněte políčka pro nastavení kompilátoru, které chcete povolit. Zrušte zaškrtnutí políček u nastavení, které chcete zakázat.  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a>Chcete-li zkompilovat instrumentované kódu pomocí příkazového řádku  
  
1. Nastavení přepínače podmíněné kompilátoru na příkazovém řádku. Kompilátor bude zahrnovat trasování nebo ladění kódu ve spustitelném souboru.  
  
     Například následující pokyn kompilátoru zadané na příkazovém řádku by zahrnout trasování kódu do zkompilovaného spustitelného souboru:  
  
     V jazyce Visual Basic: **Vbc –-r:System.dll -d: trasování = TRUE -d: DEBUG = FALSE MyApplication.vb**  
  
     Pro C#: **csc-r:System.dll -d: trasování -d: DEBUG = FALSE MyApplication.cs**  
  
    > [!TIP]
    >  Chcete-li zkompilovat více než jeden soubor aplikace, ponechte prázdné místo mezi názvy souborů, například **MyApplication1.vb MyApplication2.vb MyApplication3.vb** nebo **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.  
  
     Význam direktivy podmíněné kompilace použité v předchozích příkladech je následujícím způsobem:  
  
    |– Direktiva|Význam|  
    |---------------|-------------|  
    |`vbc`|Visual Basic – kompilátor|  
    |`csc`|C#Kompilátor|  
    |`-r:`|Odkazuje na externí sestavení (EXE nebo DLL)|  
    |`-d:`|Definuje symbol podmíněné kompilace|  
  
    > [!NOTE]
    >  Je nutné zadat trasování a ladění se velká písmena. Další informace o příkazech podmíněné kompilace, zadejte `vbc /?` (pro jazyk Visual Basic) nebo `csc /?` (pro C#) na příkazovém řádku. Další informace najdete v tématu [sestavení z příkazového řádku](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) nebo [volání kompilátoru příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a>K provedení podmíněné kompilace pomocí #CONST nebo #define  
  
1. Zadejte odpovídající příkaz pro svůj oblíbený programovací jazyk v horní části souboru se zdrojovým kódem.  
  
    |Jazyk|Příkaz|Výsledek|  
    |--------------|---------------|------------|  
    |**Visual Basic**|**#CONST trasování = true**|Umožňuje trasování|  
    ||**#CONST trasování = false**|Zakáže trasování|  
    ||**#CONST ladění = true**|Povolí ladění|  
    ||**#CONST ladění = false**|Zakáže ladění|  
    |**C#**|**#define trasování**|Umožňuje trasování|  
    ||**#undef trasování**|Zakáže trasování|  
    ||**#define ladění**|Povolí ladění|  
    ||**#undef ladění**|Zakáže ladění|  
  
### <a name="to-disable-tracing-or-debugging"></a>Chcete-li zakázat trasování a ladění  
  
Direktivy kompilátoru odstraňte ze zdrojového kódu.  
  
\- nebo –  
  
Okomentujte direktivy kompilátoru.  
  
> [!NOTE]
>  Až budete připravení ke kompilaci, můžete buď zvolit **sestavení** z **sestavení** nabídce nebo pomocí příkazového řádku, ale bez zadání **d:** k definování podmíněné symboly kompilace.  
  
## <a name="see-also"></a>Viz také:

- [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Postupy: Vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [Naslouchací procesy trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Postupy: Přidání příkazů trasování do kódu aplikace](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Postupy: Nastavení proměnných prostředí pro příkazový řádek Visual Studia](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [Postupy: Volání kompilátoru příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
