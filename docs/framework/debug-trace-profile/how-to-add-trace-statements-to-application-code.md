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
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="17e70-102">Postupy: Přidání příkazů trasování do kódu aplikace</span><span class="sxs-lookup"><span data-stu-id="17e70-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="17e70-103">Nejčastěji používané metody pro trasování jsou metody pro zápis výstupu do posluchačů: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**a **Fail**.</span><span class="sxs-lookup"><span data-stu-id="17e70-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="17e70-104">Tyto metody lze rozdělit do dvou kategorií: **Write**, **WriteLine**a **Fail** všechny vyzařovat výstup bezpodmínečně, zatímco **WriteIf**, **WriteLineIf**a **Assert** test boolean podmínku a zápis nebo nezapisovat na základě hodnoty podmínky.</span><span class="sxs-lookup"><span data-stu-id="17e70-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="17e70-105">**WriteIf** a **WriteLineIf** emitovat `true`výstup, pokud je podmínka , `false`a **Assert** vyzařuje výstup, pokud je podmínka .</span><span class="sxs-lookup"><span data-stu-id="17e70-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="17e70-106">Při navrhování strategie trasování a ladění byste měli přemýšlet o tom, jak má výstup vypadat.</span><span class="sxs-lookup"><span data-stu-id="17e70-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="17e70-107">Více **Write** příkazy vyplněné nesouvisející informace vytvoří protokol, který je obtížné číst.</span><span class="sxs-lookup"><span data-stu-id="17e70-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="17e70-108">Na druhou stranu pomocí **WriteLine** umístit související příkazy na samostatné řádky může být obtížné rozlišit, jaké informace patří dohromady.</span><span class="sxs-lookup"><span data-stu-id="17e70-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="17e70-109">Obecně použijte více **Příkazů Zápisu,** pokud chcete kombinovat informace z více zdrojů k vytvoření jedné informativní zprávy a použijte příkaz **WriteLine,** pokud chcete vytvořit jednu úplnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="17e70-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="17e70-110">Napsání úplného řádku</span><span class="sxs-lookup"><span data-stu-id="17e70-110">To write a complete line</span></span>  
  
1. <span data-ttu-id="17e70-111">Volání <xref:System.Diagnostics.Trace.WriteLine%2A> nebo <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="17e70-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="17e70-112">Návrat řádku je připojen na konec zprávy tato metoda vrátí tak, aby další zpráva vrácena **Write**, **WriteIf**, **WriteLine**, nebo **WriteLineIf** začne na následujícím řádku:</span><span class="sxs-lookup"><span data-stu-id="17e70-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
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
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="17e70-113">Zápis částečného řádku</span><span class="sxs-lookup"><span data-stu-id="17e70-113">To write a partial line</span></span>  
  
1. <span data-ttu-id="17e70-114">Volání <xref:System.Diagnostics.Trace.Write%2A> nebo <xref:System.Diagnostics.Trace.WriteIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="17e70-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="17e70-115">Další zpráva vyznaná **Write**, **WriteIf**, **WriteLine**nebo **WriteLineIf** začne na stejném řádku jako zpráva vyznaná příkazem **Write** nebo **WriteIf:**</span><span class="sxs-lookup"><span data-stu-id="17e70-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="17e70-116">Ověření, zda existují určité podmínky před nebo po provedení metody</span><span class="sxs-lookup"><span data-stu-id="17e70-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="17e70-117">Volání <xref:System.Diagnostics.Trace.Assert%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="17e70-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="17e70-118">Assert můžete **použít** s trasování a ladění.</span><span class="sxs-lookup"><span data-stu-id="17e70-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="17e70-119">Tento příklad výstupy zásobníku volání na všechny naslouchací proces v **listeners** kolekce.</span><span class="sxs-lookup"><span data-stu-id="17e70-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="17e70-120">Další informace naleznete [v tématu Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="17e70-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e70-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="17e70-121">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="17e70-122">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="17e70-122">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="17e70-123">Postupy: Vytváření, inicializace a konfigurace přepínačů trasování</span><span class="sxs-lookup"><span data-stu-id="17e70-123">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="17e70-124">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="17e70-124">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="17e70-125">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="17e70-125">Trace Listeners</span></span>](trace-listeners.md)
