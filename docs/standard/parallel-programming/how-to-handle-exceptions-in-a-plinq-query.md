---
title: 'Postupy: Zpracování výjimek v dotazu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9b5dce796e546bf041c28864c8bf66b5f51965e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046628"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="9f093-102">Postupy: Zpracování výjimek v dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="9f093-102">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="9f093-103">První příklad v tomto tématu ukazuje <xref:System.AggregateException?displayProperty=nameWithType> , jak zpracovat, která může být vyvolána z dotazu PLINQ při jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="9f093-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="9f093-104">Druhý příklad ukazuje, jak umístit bloky try-catch v rámci delegátů co nejblíže k, kde bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9f093-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="9f093-105">Tímto způsobem je můžete zachytit ihned po jejich výskytu a případně pokračovat v provádění dotazů.</span><span class="sxs-lookup"><span data-stu-id="9f093-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="9f093-106">Pokud jsou výjimky povoleny k bublinám zpět do spojovacího vlákna, pak je možné, že dotaz může pokračovat ve zpracování některých položek poté, co je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9f093-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="9f093-107">V některých případech, pokud se PLINQ vrátí zpět k sekvenčnímu provedení a dojde k výjimce, výjimka může být šířena přímo a není zabalena <xref:System.AggregateException>do.</span><span class="sxs-lookup"><span data-stu-id="9f093-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="9f093-108"><xref:System.Threading.ThreadAbortException>Navíc se vždy šíří přímo.</span><span class="sxs-lookup"><span data-stu-id="9f093-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="9f093-109">Když je povolená možnost Pouze můj kód, Visual Studio se na řádku, který vyvolá výjimku, přeruší a zobrazí se chybová zpráva s informacemi o tom, že výjimka není zpracována uživatelským kódem.</span><span class="sxs-lookup"><span data-stu-id="9f093-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="9f093-110">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="9f093-110">This error is benign.</span></span> <span data-ttu-id="9f093-111">Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech.</span><span class="sxs-lookup"><span data-stu-id="9f093-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="9f093-112">Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="9f093-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="9f093-113">Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz.</span><span class="sxs-lookup"><span data-stu-id="9f093-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="9f093-114">Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="9f093-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="9f093-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f093-115">Example</span></span>

<span data-ttu-id="9f093-116">Tento příklad ukazuje, jak umístit bloky try-catch kolem kódu, který spouští dotaz k zachycení všech <xref:System.AggregateException?displayProperty=nameWithType>vyvolaných s.</span><span class="sxs-lookup"><span data-stu-id="9f093-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="9f093-117">V tomto příkladu nemůže dotaz pokračovat, i když je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9f093-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="9f093-118">V době, kdy kód aplikace zachytí výjimku, PLINQ již zastavil dotaz na všech vláknech.</span><span class="sxs-lookup"><span data-stu-id="9f093-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="9f093-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f093-119">Example</span></span>

<span data-ttu-id="9f093-120">Následující příklad ukazuje, jak umístit blok try-catch do delegáta pro zajištění, že je možné zachytit výjimku a pokračovat v provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="9f093-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="9f093-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9f093-121">Compiling the Code</span></span>

- <span data-ttu-id="9f093-122">Chcete-li tyto příklady zkompilovat a spustit, zkopírujte je do ukázkového příkladu dat PLINQ a zavolejte metodu z Main.</span><span class="sxs-lookup"><span data-stu-id="9f093-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="9f093-123">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="9f093-123">Robust Programming</span></span>

<span data-ttu-id="9f093-124">Nezachyťte výjimku, Pokud nevíte, jak ji zpracovat, abyste nepoškodili stav programu.</span><span class="sxs-lookup"><span data-stu-id="9f093-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f093-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f093-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="9f093-126">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9f093-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
