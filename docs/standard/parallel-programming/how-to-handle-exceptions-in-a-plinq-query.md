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
ms.openlocfilehash: 5ccddfb01d6b173900dfffc465292c7812626ddc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587991"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="03df3-102">Postupy: Zpracování výjimek v dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="03df3-102">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="03df3-103">První příklad v tomto tématu <xref:System.AggregateException?displayProperty=nameWithType> ukazuje, jak zpracovat, které mohou být vyvolány z dotazu PLINQ při spuštění.</span><span class="sxs-lookup"><span data-stu-id="03df3-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="03df3-104">Druhý příklad ukazuje, jak umístit try-catch bloky v rámci delegátů, co nejblíže k kde bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="03df3-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="03df3-105">Tímto způsobem můžete zachytit, jakmile k nim dojde a případně pokračovat v provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="03df3-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="03df3-106">Pokud jsou povoleny výjimky bubliny zpět do spojovacího vlákna, pak je možné, že dotaz může pokračovat ve zpracování některých položek po vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="03df3-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="03df3-107">V některých případech, kdy PLINQ přejde zpět na sekvenční spuštění a dojde k výjimce, může být výjimka šířena přímo a není zabalena do . <xref:System.AggregateException></span><span class="sxs-lookup"><span data-stu-id="03df3-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="03df3-108">Také <xref:System.Threading.ThreadAbortException>s jsou vždy šířeny přímo.</span><span class="sxs-lookup"><span data-stu-id="03df3-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="03df3-109">Pokud je povolena možnost "Pouze můj kód", Visual Studio se přeruší na řádku, který vyvolá výjimku a zobrazí chybovou zprávu s textem "výjimka není zpracována uživatelským kódem".</span><span class="sxs-lookup"><span data-stu-id="03df3-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="03df3-110">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="03df3-110">This error is benign.</span></span> <span data-ttu-id="03df3-111">Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladech níže.</span><span class="sxs-lookup"><span data-stu-id="03df3-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="03df3-112">Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="03df3-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="03df3-113">Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="03df3-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="03df3-114">Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="03df3-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="03df3-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="03df3-115">Example</span></span>

<span data-ttu-id="03df3-116">Tento příklad ukazuje, jak umístit try-catch bloky kolem kódu, <xref:System.AggregateException?displayProperty=nameWithType>který spustí dotaz zachytit všechny s, které jsou vyvolány.</span><span class="sxs-lookup"><span data-stu-id="03df3-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="03df3-117">V tomto příkladu dotaz nemůže pokračovat po vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="03df3-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="03df3-118">V době, kdy kód aplikace zachytí výjimku, PLINQ již zastavil dotaz na všechna vlákna.</span><span class="sxs-lookup"><span data-stu-id="03df3-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="03df3-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="03df3-119">Example</span></span>

<span data-ttu-id="03df3-120">Následující příklad ukazuje, jak umístit blok try-catch v delegátovi, aby bylo možné zachytit výjimku a pokračovat v provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="03df3-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="03df3-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="03df3-121">Compiling the Code</span></span>

- <span data-ttu-id="03df3-122">Chcete-li zkompilovat a spustit tyto příklady, zkopírujte je do příkladu ukázky dat PLINQ a volání metody z Main.</span><span class="sxs-lookup"><span data-stu-id="03df3-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="03df3-123">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="03df3-123">Robust Programming</span></span>

<span data-ttu-id="03df3-124">Nezachycujte výjimku, pokud nevíte, jak ji zpracovat, abyste nepoškodili stav programu.</span><span class="sxs-lookup"><span data-stu-id="03df3-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="03df3-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="03df3-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="03df3-126">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="03df3-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
