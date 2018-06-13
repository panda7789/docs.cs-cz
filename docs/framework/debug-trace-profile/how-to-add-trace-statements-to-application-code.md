---
title: 'Postupy: Přidání příkazů trasování do kódu aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ed85c73182da5d911c6cc84fba26c658412ac158
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391365"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Postupy: Přidání příkazů trasování do kódu aplikace
Metody nejčastěji používají pro trasování jsou metody pro zápis výstupu do naslouchací procesy: **zápisu**, **writeif –**, **WriteLine**, **writelineif –**, **Assert**, a **nezdaří**. Tyto metody lze rozdělit do dvou kategorií: **zápisu**, **WriteLine**, a **nezdaří** všechny bezpodmínečně, emitování výstup zatímco **writeif –**, **Writelineif –**, a **Assert** testů podmínce logické a zápisu nebo Nezapisovat závislosti na hodnotě podmínky. **Writeif –** a **writelineif –** emitování výstupu, pokud je podmínka vyhodnocena `true`, a **Assert** vysílá výstupu, pokud je podmínka vyhodnocena `false`.  
  
 Při navrhování vaší trasování a ladění strategie, musí si myslíte o tom, jak chcete výstup k vypadat. Více **zápisu** příkazy, naplní se nesouvisejícími informace vytvoří protokolu, které je obtížné číst. Na druhé straně pomocí **WriteLine** uvést související příkazy samostatné řádky může být obtížné rozlišit, jaké informace patří společně. Obecně použít více **zápisu** příkazy, pokud chcete kombinovat informace z více zdrojů k vytvoření jedné informativní zprávy a použít **WriteLine** příkaz, pokud chcete vytvořit jeden, dokončení zpráva.  
  
### <a name="to-write-a-complete-line"></a>K zápisu dokončení řádku  
  
1.  Volání <xref:System.Diagnostics.Trace.WriteLine%2A> nebo <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.  
  
     Návrat je připojen na konec zprávy, tato metoda vrátí hodnotu, tak, aby na další zprávu vrácený **zápisu**, **writeif –**, **WriteLine**, nebo  **Writelineif –** zahájíte na následující řádek:  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,   
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a>K zápisu částečné řádku  
  
1.  Volání <xref:System.Diagnostics.Trace.Write%2A> nebo <xref:System.Diagnostics.Trace.WriteIf%2A> metody.  
  
     Na další zprávu put **zápisu**, **writeif –**, **WriteLine**, nebo **writelineif –** zahájíte na stejném řádku jako zprávu, která umístí **zápisu** nebo **writeif –** příkaz:  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,   
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Chcete-li ověřit to existují před i po provedení metody  
  
1.  Volání <xref:System.Diagnostics.Trace.Assert%2A> metoda.  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  Můžete použít **Assert** s trasování a ladění. Tento příklad výstupu pro všechny naslouchací proces v zásobníku volání **naslouchací procesy** kolekce. Další informace najdete v tématu [kontrolní výrazy ve spravovaného kódu](/visualstudio/debugger/assertions-in-managed-code) a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>  
 [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Postupy: Vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)
