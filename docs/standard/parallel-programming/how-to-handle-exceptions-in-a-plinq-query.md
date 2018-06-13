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
ms.openlocfilehash: 162ef3849f025cae9196c2f595634f82cfc782df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580741"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="caf38-102">Postupy: Zpracování výjimek v dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="caf38-102">How to: Handle Exceptions in a PLINQ Query</span></span>
<span data-ttu-id="caf38-103">V prvním příkladu v tomto tématu ukazuje způsob zpracování <xref:System.AggregateException?displayProperty=nameWithType> , může být vyvolána z PLINQ dotazu, jakmile je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="caf38-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="caf38-104">Druhý příklad ukazuje, jak se umístí bloků try-catch v rámci delegátů, co nejblíže k kde bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="caf38-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="caf38-105">Tímto způsobem můžete zachytit je Jakmile k nim dojde a případně pokračovat v provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="caf38-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="caf38-106">Pokud je výjimky umožněno vyvolat zpět do spojovacího vlákna, je možné, že dotaz může pokračovat ve zpracování některé položky po je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="caf38-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>  
  
 <span data-ttu-id="caf38-107">V některých případech když PLINQ přejde zpět k sekvenční provádění, a dojde k výjimce, výjimka může být rozšířen přímo a není uzavřen do <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="caf38-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="caf38-108">Navíc <xref:System.Threading.ThreadAbortException>s rozšířeny vždy přímo.</span><span class="sxs-lookup"><span data-stu-id="caf38-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="caf38-109">Pokud je povoleno "Pouze můj kód", Visual Studio se rozdělit na řádku, která vyvolala výjimku a zobrazí chybovou zprávu, která říká "výjimka není zpracována uživatelského kódu."</span><span class="sxs-lookup"><span data-stu-id="caf38-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="caf38-110">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="caf38-110">This error is benign.</span></span> <span data-ttu-id="caf38-111">Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, která je znázorněna v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="caf38-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="caf38-112">Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="caf38-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="caf38-113">Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="caf38-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="caf38-114">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="caf38-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="caf38-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="caf38-115">Example</span></span>  
 <span data-ttu-id="caf38-116">Tento příklad ukazuje, jak umístit bloky try-catch – okolo kód, který provede daný dotaz k zachycení všech <xref:System.AggregateException?displayProperty=nameWithType>vyvolaných.</span><span class="sxs-lookup"><span data-stu-id="caf38-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 <span data-ttu-id="caf38-117">V tomto příkladu dotaz nemůže pokračovat po vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="caf38-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="caf38-118">Podle času kód aplikace zachytí výjimky PLINQ již zastavil dotaz na všechna vlákna.</span><span class="sxs-lookup"><span data-stu-id="caf38-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="caf38-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="caf38-119">Example</span></span>  
 <span data-ttu-id="caf38-120">Následující příklad ukazuje, jak se umístí blok try-catch – delegáta, aby bylo možné zachytit výjimku a pokračovat v provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="caf38-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="caf38-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="caf38-121">Compiling the Code</span></span>  
  
-   <span data-ttu-id="caf38-122">Pro zkompilování a spuštění těchto příkladech, zkopírujte je do příklad ukázková Data pro PLINQ a volat metodu z hlavní.</span><span class="sxs-lookup"><span data-stu-id="caf38-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="caf38-123">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="caf38-123">Robust Programming</span></span>  
 <span data-ttu-id="caf38-124">Pokud víte, jak ji zpracovat tak, aby nedošlo k poškození stavu vašeho programu není zachycení výjimek.</span><span class="sxs-lookup"><span data-stu-id="caf38-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf38-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="caf38-125">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="caf38-126">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="caf38-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
