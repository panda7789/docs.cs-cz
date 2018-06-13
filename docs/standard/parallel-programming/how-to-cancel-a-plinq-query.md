---
title: 'Postupy: Zrušení dotazu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 074371a929d5dd2cf0efb763ec45395a8dfd0432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584276"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="105c7-102">Postupy: Zrušení dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="105c7-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="105c7-103">Následující příklady ukazují dva způsoby, jak zrušit PLINQ dotazu.</span><span class="sxs-lookup"><span data-stu-id="105c7-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="105c7-104">V prvním příkladu ukazuje, jak zrušit dotaz, který se skládá z průchodu dat. nejčastěji.</span><span class="sxs-lookup"><span data-stu-id="105c7-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="105c7-105">Druhý příklad ukazuje, jak zrušit dotaz, který obsahuje funkci uživatele, která náročné.</span><span class="sxs-lookup"><span data-stu-id="105c7-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="105c7-106">Pokud je povoleno "Pouze můj kód", Visual Studio se rozdělit na řádku, která vyvolala výjimku a zobrazí chybovou zprávu, která říká "výjimka není zpracována uživatelského kódu."</span><span class="sxs-lookup"><span data-stu-id="105c7-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="105c7-107">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="105c7-107">This error is benign.</span></span> <span data-ttu-id="105c7-108">Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, která je znázorněna v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="105c7-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="105c7-109">Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="105c7-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="105c7-110">Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="105c7-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="105c7-111">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="105c7-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="105c7-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="105c7-112">Example</span></span>  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 <span data-ttu-id="105c7-113">Rozhraní framework PLINQ není vrácení jedné <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> musí být zpracována v samostatném bloku catch.</span><span class="sxs-lookup"><span data-stu-id="105c7-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="105c7-114">Pokud jeden nebo více uživatelských delegátů vyvolá výjimku OperationCanceledException(externalCT) (pomocí externího <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ale žádná jiná výjimka a dotaz byl definován jako `AsParallel().WithCancellation(externalCT)`, pak PLINQ vyvolá jedné <xref:System.OperationCanceledException> (externalCT) místo <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="105c7-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="105c7-115">Ale pokud jeden uživatel delegovat vyvolá <xref:System.OperationCanceledException>a jiný delegát vyvolá výjimku jiného typu, pak oba výjimky budou vráceny do <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="105c7-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>  
  
 <span data-ttu-id="105c7-116">Obecné pokyny pro zrušení vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="105c7-116">The general guidance on cancellation is as follows:</span></span>  
  
1.  <span data-ttu-id="105c7-117">Pokud provádíte zrušení uživatelského delegáta PLINQ měli informovat o externí <xref:System.Threading.CancellationToken> a výjimku <xref:System.OperationCanceledException>(externalCT).</span><span class="sxs-lookup"><span data-stu-id="105c7-117">If you perform user-delegate cancellation you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>  
  
2.  <span data-ttu-id="105c7-118">Pokud dojde k zrušení a nejsou žádné další výjimky vyvolány, pak by měl zpracována <xref:System.OperationCanceledException> místo <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="105c7-118">If cancellation occurs and no other exceptions are thrown, then you should handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="105c7-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="105c7-119">Example</span></span>  
 <span data-ttu-id="105c7-120">Následující příklad ukazuje způsob zpracování zrušení, když máte výpočetně náročná funkce v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="105c7-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 <span data-ttu-id="105c7-121">Pokud zpracováváte zrušení v uživatelském kódu, není nutné používat <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> v definici dotazu.</span><span class="sxs-lookup"><span data-stu-id="105c7-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="105c7-122">Ale doporučujeme, abyste to provedli protože <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nemá žádný vliv na výkon dotazů a umožňuje zrušení zpracovávat operátory dotazu a uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="105c7-122">However, we recommended that you do this because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>  
  
 <span data-ttu-id="105c7-123">Aby se zajistilo systému odezvy, doporučujeme, aby kontrolovat zrušení přibližně jednou za milisekundu; jakákoli hodnota do 10 milisekund však za přijatelnou.</span><span class="sxs-lookup"><span data-stu-id="105c7-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="105c7-124">Tato četnost by neměla mít negativní dopad na výkon vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="105c7-124">This frequency should not have a negative impact on your code's performance.</span></span>  
  
 <span data-ttu-id="105c7-125">Při uvolnění má enumerátor, například když kód ukončí smyčku foreach (pro každou v jazyce Visual Basic), který je iterování přes výsledky dotazu, pak dotazu bylo zrušeno, ale nedojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="105c7-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is cancelled, but no exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105c7-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="105c7-126">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="105c7-127">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="105c7-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="105c7-128">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="105c7-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
