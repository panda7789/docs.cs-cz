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
ms.openlocfilehash: 21df0e8129505e50e6b7f29c4f4f5aea94f380e3
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217471"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Postupy: Přidání příkazů trasování do kódu aplikace
Metody používané nejčastěji pro trasování jsou metody pro zápis výstupu do naslouchacího procesu: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**a **selžou**. Tyto metody lze rozdělit do dvou kategorií: **Write**, **WriteLine**a **selhat** výstup vysílat nepodmíněně, zatímco **WriteIf**, **WriteLineIf**a **Assert** otestujete logickou podmínku a nezapisujete nebo nepřepíšete na základě hodnoty podmínky. **WriteIf** a **WriteLineIf** vygenerují výstup, pokud je podmínka `true`, **a vygeneruje výstup, pokud** je podmínka `false`.  
  
 Při navrhování strategie trasování a ladění byste měli myslet na to, jak chcete, aby výstup vypadal. Vícenásobné příkazy **zápisu** vyplněné nesouvisejícími informacemi vytvoří protokol, který se obtížně přečte. Na druhé straně použití příkazu **WriteLine** k vložení souvisejících příkazů na samostatné řádky může být obtížné odlišit informace, které patří dohromady. Obecně platí, že pokud chcete kombinovat informace z více zdrojů k vytvoření jedné informativní zprávy, **použijte příkaz** WriteLine a použijte příkaz **WriteLine** , pokud chcete vytvořit jednu, úplnou zprávu.  
  
### <a name="to-write-a-complete-line"></a>Zápis kompletního řádku  
  
1. Volání <xref:System.Diagnostics.Trace.WriteLine%2A> nebo <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.  
  
     Znak návratu na začátek řádku je připojen ke konci zprávy, který tato metoda vrátí, takže další zpráva vrácená funkcí **Write**, **WriteIf**, **WriteLine**nebo **WriteLineIf** zahájí následující řádek:  
  
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
  
### <a name="to-write-a-partial-line"></a>Zápis částečného řádku  
  
1. Volání <xref:System.Diagnostics.Trace.Write%2A> nebo <xref:System.Diagnostics.Trace.WriteIf%2A> metody.  
  
     Další zpráva vydaná **zápisem**, **WriteIf**, **WriteLine**nebo **WriteLineIf** začne na stejném řádku jako zpráva vložená příkazem **Write** nebo **WriteIf** :  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Ověření, že některé podmínky existují buď před, nebo po provedení metody  
  
1. Zavolejte metodu <xref:System.Diagnostics.Trace.Assert%2A>.  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > Můžete použít **Assert** jak pro trasování, tak pro ladění. Tento příklad vypíše zásobník volání do libovolného naslouchacího procesu v kolekci **posluchačů** . Další informace naleznete v tématu [kontrolní výrazy ve spravovaném kódu](/visualstudio/debugger/assertions-in-managed-code) a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)
- [Postupy: Vytváření, inicializace a konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md)
- [Přepínače trasování](trace-switches.md)
- [Moduly naslouchání trasování](trace-listeners.md)
