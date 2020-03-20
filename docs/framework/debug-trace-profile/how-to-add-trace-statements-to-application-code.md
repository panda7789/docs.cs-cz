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
ms.openlocfilehash: 9903a0357d1d8ceade21b590fd54c8cab517f134
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174742"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Postupy: Přidání příkazů trasování do kódu aplikace
Nejčastěji používané metody pro trasování jsou metody pro zápis výstupu do posluchačů: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**a **Fail**. Tyto metody lze rozdělit do dvou kategorií: **Write**, **WriteLine**a **Fail** všechny vyzařovat výstup bezpodmínečně, zatímco **WriteIf**, **WriteLineIf**a **Assert** test boolean podmínku a zápis nebo nezapisovat na základě hodnoty podmínky. **WriteIf** a **WriteLineIf** emitovat `true`výstup, pokud je podmínka , `false`a **Assert** vyzařuje výstup, pokud je podmínka .  
  
 Při navrhování strategie trasování a ladění byste měli přemýšlet o tom, jak má výstup vypadat. Více **Write** příkazy vyplněné nesouvisející informace vytvoří protokol, který je obtížné číst. Na druhou stranu pomocí **WriteLine** umístit související příkazy na samostatné řádky může být obtížné rozlišit, jaké informace patří dohromady. Obecně použijte více **Příkazů Zápisu,** pokud chcete kombinovat informace z více zdrojů k vytvoření jedné informativní zprávy a použijte příkaz **WriteLine,** pokud chcete vytvořit jednu úplnou zprávu.  
  
### <a name="to-write-a-complete-line"></a>Napsání úplného řádku  
  
1. Volání <xref:System.Diagnostics.Trace.WriteLine%2A> nebo <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.  
  
     Návrat řádku je připojen na konec zprávy tato metoda vrátí tak, aby další zpráva vrácena **Write**, **WriteIf**, **WriteLine**, nebo **WriteLineIf** začne na následujícím řádku:  
  
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
  
     Další zpráva vyznaná **Write**, **WriteIf**, **WriteLine**nebo **WriteLineIf** začne na stejném řádku jako zpráva vyznaná příkazem **Write** nebo **WriteIf:**  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Ověření, zda existují určité podmínky před nebo po provedení metody  
  
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
    > Assert můžete **použít** s trasování a ladění. Tento příklad výstupy zásobníku volání na všechny naslouchací proces v **listeners** kolekce. Další informace naleznete [v tématu Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [Trasování a instrumentace aplikací](tracing-and-instrumenting-applications.md)
- [Postupy: Vytváření, inicializace a konfigurace přepínačů trasování](how-to-create-initialize-and-configure-trace-switches.md)
- [Přepínače trasování](trace-switches.md)
- [Moduly naslouchání trasování](trace-listeners.md)
