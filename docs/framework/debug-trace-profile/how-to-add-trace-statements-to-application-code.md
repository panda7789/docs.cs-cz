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
ms.openlocfilehash: 1f45259623d4a481e635ac1b54ecb9a17497ab5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204091"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="1a5de-102">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="1a5de-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="1a5de-103">Nejčastěji používá pro trasování metody jsou metody pro zápis výstupu do naslouchacích procesů: **Zápis**, **writeif –**, **WriteLine**, **writelineif –**, **vyhodnocení**, a **selhání**.</span><span class="sxs-lookup"><span data-stu-id="1a5de-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="1a5de-104">Tyto metody je možné rozdělit do dvou kategorií: **Zápis**, **WriteLine**, a **selhání** všechny bezpodmínečně, vygeneruje výstup vzhledem k tomu **writeif –**, **writelineif –** a  **Assert –** testu je logická podmínka a zapisovat nebo Nezapisovat závislosti na hodnotě podmínky.</span><span class="sxs-lookup"><span data-stu-id="1a5de-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="1a5de-105">**Writeif –** a **writelineif –** vygeneruje výstup, pokud je podmínka `true`, a **Assert** generuje výstup, pokud je podmínka `false`.</span><span class="sxs-lookup"><span data-stu-id="1a5de-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="1a5de-106">Při navrhování vaší trasování a ladění strategie, byste uvažovat o tom, jak chcete výstup vás pod rouškou.</span><span class="sxs-lookup"><span data-stu-id="1a5de-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="1a5de-107">Více **zápisu** příkazy vyplněna informacemi nesouvisejících vytvoří protokol, který je obtížné číst.</span><span class="sxs-lookup"><span data-stu-id="1a5de-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="1a5de-108">Na druhé straně pomocí **WriteLine** umístění související příkazy na samostatných řádcích může být obtížné k rozlišení, jaké informace patří k sobě.</span><span class="sxs-lookup"><span data-stu-id="1a5de-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="1a5de-109">Obecně platí, použijte více **zápisu** příkazy, pokud chcete kombinovat informace z různých zdrojů k vytvoření jedné informativní zprávy a použití **WriteLine** příkazu, pokud chcete vytvořit jediné, dokončení zprávy.</span><span class="sxs-lookup"><span data-stu-id="1a5de-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="1a5de-110">Napsat úplný řádek</span><span class="sxs-lookup"><span data-stu-id="1a5de-110">To write a complete line</span></span>  
  
1.  <span data-ttu-id="1a5de-111">Volání <xref:System.Diagnostics.Trace.WriteLine%2A> nebo <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1a5de-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="1a5de-112">Zalomení řádku je připojen na konec zprávy návratu tato metoda tak, aby další zprávy vrácené **zápisu**, **writeif –**, **WriteLine**, nebo  **Writelineif –** začne na následující řádek:</span><span class="sxs-lookup"><span data-stu-id="1a5de-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
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
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="1a5de-113">Zápis částečný řádek</span><span class="sxs-lookup"><span data-stu-id="1a5de-113">To write a partial line</span></span>  
  
1.  <span data-ttu-id="1a5de-114">Volání <xref:System.Diagnostics.Trace.Write%2A> nebo <xref:System.Diagnostics.Trace.WriteIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1a5de-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="1a5de-115">Další zprávu vložit navýšení kapacity **zápisu**, **writeif –**, **WriteLine**, nebo **writelineif –** začne na stejném řádku jako zprávu vložit navýšení kapacity **zápisu** nebo **writeif –** – příkaz:</span><span class="sxs-lookup"><span data-stu-id="1a5de-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="1a5de-116">Chcete-li ověřit určitých podmínek před nebo po provedení metody</span><span class="sxs-lookup"><span data-stu-id="1a5de-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1.  <span data-ttu-id="1a5de-117">Volání <xref:System.Diagnostics.Trace.Assert%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1a5de-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1a5de-118">Můžete použít **Assert** pomocí trasování a ladění.</span><span class="sxs-lookup"><span data-stu-id="1a5de-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="1a5de-119">Zásobník volání pro všechny posluchače v tomto příkladu je výstupem **naslouchacích procesů** kolekce.</span><span class="sxs-lookup"><span data-stu-id="1a5de-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="1a5de-120">Další informace najdete v tématu [kontrolní výrazy ve spravovaného kódu](/visualstudio/debugger/assertions-in-managed-code) a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1a5de-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5de-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a5de-121">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1a5de-122">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="1a5de-122">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="1a5de-123">Postupy: Vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="1a5de-123">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="1a5de-124">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="1a5de-124">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="1a5de-125">Naslouchací procesy trasování</span><span class="sxs-lookup"><span data-stu-id="1a5de-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
