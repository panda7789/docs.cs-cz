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
ms.openlocfilehash: 40b98e01d6c34fb01a1f508f2ea52309f2f7938b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45989518"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="d76c1-102">Postupy: Zpracování výjimek v dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="d76c1-102">How to: Handle Exceptions in a PLINQ Query</span></span>
<span data-ttu-id="d76c1-103">První příklad v tomto tématu ukazuje, jak zpracovat <xref:System.AggregateException?displayProperty=nameWithType> , které mohou být vyvolány z dotazu PLINQ při provádění.</span><span class="sxs-lookup"><span data-stu-id="d76c1-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="d76c1-104">Druhý příklad ukazuje, jak vložit bloků try-catch v rámci delegáty, co nejblíže k kde bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d76c1-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="d76c1-105">Tímto způsobem může zachytit je co nejdříve, dojde k a případně pokračovat provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="d76c1-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="d76c1-106">Pokud je výjimkám umožněn pokračovala zpět do spojovacího vlákna, pak je možné, že dotaz může pokračovat ve zpracování některých položek poté, co je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d76c1-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>  
  
 <span data-ttu-id="d76c1-107">V některých případech při PLINQ spadne zpět na sekvenční provádění a dojde k výjimce, výjimky může být rozšířena přímo a nejsou zabaleny v <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="d76c1-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="d76c1-108">Navíc <xref:System.Threading.ThreadAbortException>s nerozšíří vždy přímo.</span><span class="sxs-lookup"><span data-stu-id="d76c1-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d76c1-109">Pokud je povoleno "Jen můj kód", Visual Studio na řádce, která výjimku a zobrazí chybovou zprávu, že "výjimka není ošetřena v uživatelském kódu."</span><span class="sxs-lookup"><span data-stu-id="d76c1-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="d76c1-110">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="d76c1-110">This error is benign.</span></span> <span data-ttu-id="d76c1-111">Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, což je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="d76c1-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="d76c1-112">Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="d76c1-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="d76c1-113">V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům.</span><span class="sxs-lookup"><span data-stu-id="d76c1-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="d76c1-114">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="d76c1-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d76c1-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d76c1-115">Example</span></span>  
 <span data-ttu-id="d76c1-116">Tento příklad ukazuje, jak vložit bloků try-catch kolem kód, který provede daný dotaz k zachycení všech <xref:System.AggregateException?displayProperty=nameWithType>, které jsou vyvolány.</span><span class="sxs-lookup"><span data-stu-id="d76c1-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 <span data-ttu-id="d76c1-117">V tomto příkladu dotaz nemůže pokračovat po vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="d76c1-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="d76c1-118">Podle času kódu aplikace zachytí výjimku PLINQ již zastavil dotaz na všech vláknech.</span><span class="sxs-lookup"><span data-stu-id="d76c1-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d76c1-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="d76c1-119">Example</span></span>  
 <span data-ttu-id="d76c1-120">Následující příklad ukazuje, jak vložit blok try-catch v delegátovi, aby bylo možné zachytit výjimku a pokračujte v provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="d76c1-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d76c1-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d76c1-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d76c1-122">Kompilace a spuštění tyto příklady, zkopírujte je do příklad ukázková Data pro PLINQ a zavolejte metodu z hlavní.</span><span class="sxs-lookup"><span data-stu-id="d76c1-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d76c1-123">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d76c1-123">Robust Programming</span></span>  
 <span data-ttu-id="d76c1-124">Nezachycujte výjimky, pokud si nejste jisti, jak ji zpracovat tak, aby nedošlo k poškození stavu programu.</span><span class="sxs-lookup"><span data-stu-id="d76c1-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d76c1-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d76c1-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>  
- [<span data-ttu-id="d76c1-126">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d76c1-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
