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
ms.openlocfilehash: b39646655c175497533aa6dc358c6966acc27344
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754531"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Postupy: Přidání příkazů trasování do kódu aplikace
Nejčastěji používá pro trasování metody jsou metody pro zápis výstupu do naslouchacích procesů: **Zápis**, **writeif –**, **WriteLine**, **writelineif –**, **vyhodnocení**, a **selhání**. Tyto metody je možné rozdělit do dvou kategorií: **Zápis**, **WriteLine**, a **selhání** všechny bezpodmínečně, vygeneruje výstup vzhledem k tomu **writeif –**, **writelineif –** a  **Assert –** testu je logická podmínka a zapisovat nebo Nezapisovat závislosti na hodnotě podmínky. **Writeif –** a **writelineif –** vygeneruje výstup, pokud je podmínka `true`, a **Assert** generuje výstup, pokud je podmínka `false`.  
  
 Při navrhování vaší trasování a ladění strategie, byste uvažovat o tom, jak chcete výstup vás pod rouškou. Více **zápisu** příkazy vyplněna informacemi nesouvisejících vytvoří protokol, který je obtížné číst. Na druhé straně pomocí **WriteLine** umístění související příkazy na samostatných řádcích může být obtížné k rozlišení, jaké informace patří k sobě. Obecně platí, použijte více **zápisu** příkazy, pokud chcete kombinovat informace z různých zdrojů k vytvoření jedné informativní zprávy a použití **WriteLine** příkazu, pokud chcete vytvořit jediné, dokončení zprávy.  
  
### <a name="to-write-a-complete-line"></a>Napsat úplný řádek  
  
1. Volání <xref:System.Diagnostics.Trace.WriteLine%2A> nebo <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.  
  
     Zalomení řádku je připojen na konec zprávy návratu tato metoda tak, aby další zprávy vrácené **zápisu**, **writeif –**, **WriteLine**, nebo  **Writelineif –** začne na následující řádek:  
  
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
  
### <a name="to-write-a-partial-line"></a>Zápis částečný řádek  
  
1. Volání <xref:System.Diagnostics.Trace.Write%2A> nebo <xref:System.Diagnostics.Trace.WriteIf%2A> metody.  
  
     Další zprávu vložit navýšení kapacity **zápisu**, **writeif –**, **WriteLine**, nebo **writelineif –** začne na stejném řádku jako zprávu vložit navýšení kapacity **zápisu** nebo **writeif –** – příkaz:  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Chcete-li ověřit určitých podmínek před nebo po provedení metody  
  
1. Volání <xref:System.Diagnostics.Trace.Assert%2A> metody.  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  Můžete použít **Assert** pomocí trasování a ladění. Zásobník volání pro všechny posluchače v tomto příkladu je výstupem **naslouchacích procesů** kolekce. Další informace najdete v tématu [kontrolní výrazy ve spravovaného kódu](/visualstudio/debugger/assertions-in-managed-code) a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Postupy: Vytváření, inicializace a konfigurace přepínačů trasování](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [Přepínače trasování](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [Moduly naslouchání trasování](../../../docs/framework/debug-trace-profile/trace-listeners.md)
