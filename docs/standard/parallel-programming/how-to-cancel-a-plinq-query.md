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
ms.openlocfilehash: 09405a8a9f5d96d80454bcc98cbf29db54df6725
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288209"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="7d128-102">Postupy: Zrušení dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="7d128-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="7d128-103">Následující příklady znázorňují dva způsoby, jak zrušit dotaz PLINQ.</span><span class="sxs-lookup"><span data-stu-id="7d128-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="7d128-104">První příklad ukazuje, jak zrušit dotaz, který se skládá hlavně z procházení dat.</span><span class="sxs-lookup"><span data-stu-id="7d128-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="7d128-105">Druhý příklad ukazuje, jak zrušit dotaz, který obsahuje uživatelskou funkci, která je výpočetně náročná.</span><span class="sxs-lookup"><span data-stu-id="7d128-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>

> [!NOTE]
> <span data-ttu-id="7d128-106">Když je povolená možnost Pouze můj kód, Visual Studio se na řádku, který vyvolá výjimku, přeruší a zobrazí se chybová zpráva s informacemi o tom, že výjimka není zpracována uživatelským kódem.</span><span class="sxs-lookup"><span data-stu-id="7d128-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="7d128-107">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="7d128-107">This error is benign.</span></span> <span data-ttu-id="7d128-108">Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech.</span><span class="sxs-lookup"><span data-stu-id="7d128-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="7d128-109">Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="7d128-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="7d128-110">Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz.</span><span class="sxs-lookup"><span data-stu-id="7d128-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="7d128-111">Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="7d128-111">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="7d128-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d128-112">Example</span></span>

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

<span data-ttu-id="7d128-113">Rozhraní PLINQ nezahrnuje jednu hodnotu <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType> . <xref:System.OperationCanceledException> musí být zpracována v samostatném bloku catch.</span><span class="sxs-lookup"><span data-stu-id="7d128-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="7d128-114">Pokud jeden nebo více delegátů uživatele vyvolá OperationCanceledException (externalCT) (pomocí externí <xref:System.Threading.CancellationToken?displayProperty=nameWithType> ), ale bez jiné výjimky a dotaz byl definován jako `AsParallel().WithCancellation(externalCT)` , pak PLINQ vydá jednu <xref:System.OperationCanceledException> (externalCT), nikoli <xref:System.AggregateException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7d128-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7d128-115">Nicméně pokud jeden uživatelský delegát vyvolá výjimku <xref:System.OperationCanceledException> a jiný delegát vyvolá jiný typ výjimky, pak obě výjimky budou zahrnuty do <xref:System.AggregateException> .</span><span class="sxs-lookup"><span data-stu-id="7d128-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>

<span data-ttu-id="7d128-116">Obecné pokyny týkající se zrušení jsou následující:</span><span class="sxs-lookup"><span data-stu-id="7d128-116">The general guidance on cancellation is as follows:</span></span>

1. <span data-ttu-id="7d128-117">Pokud provádíte zrušení uživatelem delegáta, měli byste informovat o externích <xref:System.Threading.CancellationToken> událostech a vyvolat výjimku <xref:System.OperationCanceledException> (externalCT).</span><span class="sxs-lookup"><span data-stu-id="7d128-117">If you perform user-delegate cancellation, you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>

2. <span data-ttu-id="7d128-118">Pokud dojde k zrušení a nejsou vyvolány žádné další výjimky, pak je zpracována <xref:System.OperationCanceledException> místo <xref:System.AggregateException> .</span><span class="sxs-lookup"><span data-stu-id="7d128-118">If cancellation occurs and no other exceptions are thrown, then handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>

## <a name="example"></a><span data-ttu-id="7d128-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d128-119">Example</span></span>

<span data-ttu-id="7d128-120">Následující příklad ukazuje, jak zpracovat zrušení, když máte výpočetní náročnou funkci v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="7d128-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

<span data-ttu-id="7d128-121">Při zpracování zrušení v uživatelském kódu není nutné používat <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> v definici dotazu.</span><span class="sxs-lookup"><span data-stu-id="7d128-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="7d128-122">Doporučujeme však použít <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> , protože <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nemá žádný vliv na výkon dotazů a umožňuje zrušení zpracování pomocí operátorů dotazů a uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="7d128-122">However, we recommended that you do use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>, because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>

<span data-ttu-id="7d128-123">Aby se zajistila odezva systému, doporučujeme, abyste kontrolovali zrušení přibližně jednou za milisekundu. Nicméně jakékoli období až 10 milisekund se považuje za přijatelné.</span><span class="sxs-lookup"><span data-stu-id="7d128-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="7d128-124">Tato frekvence by neměla mít negativní vliv na výkon vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="7d128-124">This frequency should not have a negative impact on your code's performance.</span></span>

<span data-ttu-id="7d128-125">Když je vyjímka vyhozena, například když se kód rozdělí mimo smyčku foreach (for each in Visual Basic), která provádí iteraci nad výsledky dotazu, je dotaz zrušen, ale není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="7d128-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is canceled, but no exception is thrown.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d128-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d128-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="7d128-127">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="7d128-127">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
- [<span data-ttu-id="7d128-128">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="7d128-128">Cancellation in Managed Threads</span></span>](../threading/cancellation-in-managed-threads.md)
