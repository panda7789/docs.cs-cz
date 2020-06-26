---
title: 'Postupy: Přidání příkazů trasování do kódu aplikace'
description: Naučte se přidávat příkazy trasování do kódu aplikace v .NET. Metody používané nejčastěji pro trasování jsou metody pro zápis výstupu do posluchačů.
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
ms.openlocfilehash: 0c75a8775649aabe73b02187c4604d2eb3a8435b
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415885"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="0be1e-104">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="0be1e-104">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="0be1e-105">Metody používané nejčastěji pro trasování jsou metody pro zápis výstupu do naslouchacího procesu: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**a **selžou**.</span><span class="sxs-lookup"><span data-stu-id="0be1e-105">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="0be1e-106">Tyto metody lze rozdělit do dvou kategorií: **Write**, **WriteLine**a **selhat** výstup vysílat nepodmíněně, zatímco **WriteIf**, **WriteLineIf**a **Assert** otestujete logickou podmínku a nezapisujete nebo nepřepíšete na základě hodnoty podmínky.</span><span class="sxs-lookup"><span data-stu-id="0be1e-106">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="0be1e-107">**WriteIf** a **WriteLineIf** vygenerují výstup, pokud je podmínka `true` , a **Assert** vygeneruje výstup, pokud je podmínka `false` .</span><span class="sxs-lookup"><span data-stu-id="0be1e-107">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="0be1e-108">Při navrhování strategie trasování a ladění byste měli myslet na to, jak chcete, aby výstup vypadal.</span><span class="sxs-lookup"><span data-stu-id="0be1e-108">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="0be1e-109">Vícenásobné příkazy **zápisu** vyplněné nesouvisejícími informacemi vytvoří protokol, který se obtížně přečte.</span><span class="sxs-lookup"><span data-stu-id="0be1e-109">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="0be1e-110">Na druhé straně použití příkazu **WriteLine** k vložení souvisejících příkazů na samostatné řádky může být obtížné odlišit informace, které patří dohromady.</span><span class="sxs-lookup"><span data-stu-id="0be1e-110">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="0be1e-111">Obecně platí, že pokud chcete kombinovat informace z více zdrojů k vytvoření jedné informativní zprávy, **použijte příkaz** WriteLine a použijte příkaz **WriteLine** , pokud chcete vytvořit jednu, úplnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="0be1e-111">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="0be1e-112">Zápis kompletního řádku</span><span class="sxs-lookup"><span data-stu-id="0be1e-112">To write a complete line</span></span>  
  
1. <span data-ttu-id="0be1e-113">Volání <xref:System.Diagnostics.Trace.WriteLine%2A> nebo <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0be1e-113">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="0be1e-114">Znak návratu na začátek řádku je připojen ke konci zprávy, který tato metoda vrátí, takže další zpráva vrácená funkcí **Write**, **WriteIf**, **WriteLine**nebo **WriteLineIf** zahájí následující řádek:</span><span class="sxs-lookup"><span data-stu-id="0be1e-114">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
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
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="0be1e-115">Zápis částečného řádku</span><span class="sxs-lookup"><span data-stu-id="0be1e-115">To write a partial line</span></span>  
  
1. <span data-ttu-id="0be1e-116">Volání <xref:System.Diagnostics.Trace.Write%2A> nebo <xref:System.Diagnostics.Trace.WriteIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0be1e-116">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="0be1e-117">Další zpráva vydaná **zápisem**, **WriteIf**, **WriteLine**nebo **WriteLineIf** začne na stejném řádku jako zpráva vložená příkazem **Write** nebo **WriteIf** :</span><span class="sxs-lookup"><span data-stu-id="0be1e-117">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="0be1e-118">Ověření, že některé podmínky existují buď před, nebo po provedení metody</span><span class="sxs-lookup"><span data-stu-id="0be1e-118">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="0be1e-119">Zavolejte <xref:System.Diagnostics.Trace.Assert%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="0be1e-119">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="0be1e-120">Můžete použít **Assert** jak pro trasování, tak pro ladění.</span><span class="sxs-lookup"><span data-stu-id="0be1e-120">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="0be1e-121">Tento příklad vypíše zásobník volání do libovolného naslouchacího procesu v kolekci **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="0be1e-121">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="0be1e-122">Další informace naleznete v tématu [kontrolní výrazy ve spravovaném kódu](/visualstudio/debugger/assertions-in-managed-code) a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0be1e-122">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0be1e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="0be1e-123">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0be1e-124">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="0be1e-124">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="0be1e-125">Postupy: Vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="0be1e-125">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="0be1e-126">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="0be1e-126">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="0be1e-127">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="0be1e-127">Trace Listeners</span></span>](trace-listeners.md)
