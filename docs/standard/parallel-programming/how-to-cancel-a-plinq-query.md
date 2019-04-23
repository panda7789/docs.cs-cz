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
ms.openlocfilehash: 80dc5f72bac436d4935c1697347d588b1a302f86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305335"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="da0c6-102">Postupy: Zrušení dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="da0c6-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="da0c6-103">Následující příklady ukazují dva způsoby, jak zrušení dotazu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="da0c6-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="da0c6-104">První příklad ukazuje, jak zrušit dotaz, který se skládá převážně procházení data.</span><span class="sxs-lookup"><span data-stu-id="da0c6-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="da0c6-105">Druhý příklad ukazuje, jak zrušit dotaz, který obsahuje funkci uživatele, který je výpočetně náročná.</span><span class="sxs-lookup"><span data-stu-id="da0c6-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da0c6-106">Pokud je povoleno "Jen můj kód", Visual Studio na řádce, která výjimku a zobrazí chybovou zprávu, že "výjimka není ošetřena v uživatelském kódu."</span><span class="sxs-lookup"><span data-stu-id="da0c6-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="da0c6-107">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="da0c6-107">This error is benign.</span></span> <span data-ttu-id="da0c6-108">Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, což je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="da0c6-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="da0c6-109">Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.</span><span class="sxs-lookup"><span data-stu-id="da0c6-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="da0c6-110">V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům.</span><span class="sxs-lookup"><span data-stu-id="da0c6-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="da0c6-111">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="da0c6-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da0c6-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="da0c6-112">Example</span></span>  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 <span data-ttu-id="da0c6-113">Rozhraní PLINQ nevrátí jediného <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> musí být zpracovány v samostatném bloku catch.</span><span class="sxs-lookup"><span data-stu-id="da0c6-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="da0c6-114">Pokud jeden nebo více uživatelských delegátech vyvolá výjimku OperationCanceledException(externalCT) (s použitím externí <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ale žádná výjimka a dotaz byl definován jako `AsParallel().WithCancellation(externalCT)`, pak PLINQ vydá jediného <xref:System.OperationCanceledException> (externalCT) spíše než výjimku <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da0c6-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="da0c6-115">Nicméně, pokud jeden uživatelský delegát vyvolá <xref:System.OperationCanceledException>a jinou delegáta vyvolá jiný typ výjimky a pak obě výjimky budou vráceny do <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="da0c6-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>  
  
 <span data-ttu-id="da0c6-116">Obecné pokyny k zrušení vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="da0c6-116">The general guidance on cancellation is as follows:</span></span>  
  
1. <span data-ttu-id="da0c6-117">Pokud provádíte uživatelský delegát zrušení by měl PLINQ informovat o externí <xref:System.Threading.CancellationToken> a výjimku <xref:System.OperationCanceledException>(externalCT).</span><span class="sxs-lookup"><span data-stu-id="da0c6-117">If you perform user-delegate cancellation you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>  
  
2. <span data-ttu-id="da0c6-118">Pokud dojde k zrušení a nejsou vyvolány žádné výjimky, pak můžete pracovat <xref:System.OperationCanceledException> spíše než výjimku <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="da0c6-118">If cancellation occurs and no other exceptions are thrown, then you should handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da0c6-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="da0c6-119">Example</span></span>  
 <span data-ttu-id="da0c6-120">Následující příklad ukazuje, jak zpracovat zrušení, když máte výpočetně náročné funkce v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="da0c6-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 <span data-ttu-id="da0c6-121">Při zpracování zrušení v uživatelském kódu, nemusíte používat <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> v definici dotazu.</span><span class="sxs-lookup"><span data-stu-id="da0c6-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="da0c6-122">Doporučujeme však, že můžete udělat proto, že <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nemá žádný vliv na výkon dotazů a umožňuje zrušení zpracovávat operátorů pro dotazování a uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="da0c6-122">However, we recommended that you do this because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>  
  
 <span data-ttu-id="da0c6-123">Aby bylo možné zajistit rychlost odezvy systému, doporučujeme zkontrolovat, zda zrušení přibližně jednou za milisekundu; období až do 10 milisekund je však považován za přijatelné.</span><span class="sxs-lookup"><span data-stu-id="da0c6-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="da0c6-124">Četnost odesílání by neměla mít negativní dopad na výkon vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="da0c6-124">This frequency should not have a negative impact on your code's performance.</span></span>  
  
 <span data-ttu-id="da0c6-125">Když enumerátor je odstraněn, třeba když kód přestane fungovat mimo smyčku foreach (pro každý v jazyce Visual Basic), která je iterování přes výsledky dotazu, pak dotazu bylo zrušeno, ale není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="da0c6-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is cancelled, but no exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da0c6-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da0c6-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="da0c6-127">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="da0c6-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="da0c6-128">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="da0c6-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
