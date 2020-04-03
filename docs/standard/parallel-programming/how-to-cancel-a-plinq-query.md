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
ms.openlocfilehash: 312c71b787ac7b4aa092f1517d2ed5af314a22e4
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635883"
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="c30d7-102">Postupy: Zrušení dotazu PLINQ</span><span class="sxs-lookup"><span data-stu-id="c30d7-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="c30d7-103">Následující příklady ukazují dva způsoby zrušení dotazu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c30d7-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="c30d7-104">První příklad ukazuje, jak zrušit dotaz, který se skládá převážně z průchodu dat.</span><span class="sxs-lookup"><span data-stu-id="c30d7-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="c30d7-105">Druhý příklad ukazuje, jak zrušit dotaz, který obsahuje uživatelskou funkci, která je výpočtově nákladné.</span><span class="sxs-lookup"><span data-stu-id="c30d7-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>

> [!NOTE]
> <span data-ttu-id="c30d7-106">Pokud je povolena možnost "Pouze můj kód", Visual Studio se přeruší na řádku, který vyvolá výjimku a zobrazí chybovou zprávu s textem "výjimka není zpracována uživatelským kódem".</span><span class="sxs-lookup"><span data-stu-id="c30d7-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="c30d7-107">Tato chyba je neškodná.</span><span class="sxs-lookup"><span data-stu-id="c30d7-107">This error is benign.</span></span> <span data-ttu-id="c30d7-108">Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladech níže.</span><span class="sxs-lookup"><span data-stu-id="c30d7-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="c30d7-109">Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.</span><span class="sxs-lookup"><span data-stu-id="c30d7-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="c30d7-110">Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="c30d7-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="c30d7-111">Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="c30d7-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="c30d7-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c30d7-112">Example</span></span>

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

<span data-ttu-id="c30d7-113">Rámec PLINQ nepřevádí jeden <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; s <xref:System.OperationCanceledException> blokem úlovku se musí zacházet v samostatném bloku odlovu.</span><span class="sxs-lookup"><span data-stu-id="c30d7-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="c30d7-114">Pokud jeden nebo více delegátů uživatele vyvolá OperationCanceledException(externalCT) <xref:System.Threading.CancellationToken?displayProperty=nameWithType>(pomocí externí) ale žádná jiná `AsParallel().WithCancellation(externalCT)`výjimka a dotaz byl <xref:System.OperationCanceledException> definován jako , <xref:System.AggregateException?displayProperty=nameWithType>pak PLINQ vydá jeden (externalCT) spíše než .</span><span class="sxs-lookup"><span data-stu-id="c30d7-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c30d7-115">Pokud však jeden delegát <xref:System.OperationCanceledException>uživatele vyvolá a jiný delegát vyvolá jiný typ výjimky, <xref:System.AggregateException>budou obě výjimky vráceny do .</span><span class="sxs-lookup"><span data-stu-id="c30d7-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>

<span data-ttu-id="c30d7-116">Obecné pokyny ke zrušení jsou následující:</span><span class="sxs-lookup"><span data-stu-id="c30d7-116">The general guidance on cancellation is as follows:</span></span>

1. <span data-ttu-id="c30d7-117">Pokud provedete zrušení delegáta uživatele, měli byste <xref:System.Threading.CancellationToken> informovat PLINQ o externí a vyvolat <xref:System.OperationCanceledException>(externalCT).</span><span class="sxs-lookup"><span data-stu-id="c30d7-117">If you perform user-delegate cancellation, you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>

2. <span data-ttu-id="c30d7-118">Pokud dojde ke zrušení a nejsou vyvolány žádné <xref:System.OperationCanceledException> další <xref:System.AggregateException>výjimky, pak zpracovat spíše než .</span><span class="sxs-lookup"><span data-stu-id="c30d7-118">If cancellation occurs and no other exceptions are thrown, then handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>

## <a name="example"></a><span data-ttu-id="c30d7-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="c30d7-119">Example</span></span>

<span data-ttu-id="c30d7-120">Následující příklad ukazuje, jak zpracovat zrušení, pokud máte výpočtově nákladné funkce v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="c30d7-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

<span data-ttu-id="c30d7-121">Při zpracování zrušení v uživatelském kódu, není <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> třeba použít v definici dotazu.</span><span class="sxs-lookup"><span data-stu-id="c30d7-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="c30d7-122">Doporučujeme však použít <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>, <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> protože nemá žádný vliv na výkon dotazu a umožňuje zrušení, které mají být zpracovány operátory dotazu a váš uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="c30d7-122">However, we recommended that you do use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>, because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>

<span data-ttu-id="c30d7-123">Chcete-li zajistit odezvu systému, doporučujeme zkontrolovat zrušení přibližně jednou za milisekundu; však jakékoli období až do 10 milisekund je považováno za přijatelné.</span><span class="sxs-lookup"><span data-stu-id="c30d7-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="c30d7-124">Tato frekvence by neměla mít negativní dopad na výkon kódu.</span><span class="sxs-lookup"><span data-stu-id="c30d7-124">This frequency should not have a negative impact on your code's performance.</span></span>

<span data-ttu-id="c30d7-125">Při uvolnění čítače výčtu, například když kód rozdělí foreach (pro každý v jazyce Visual Basic) smyčky, která je iterace přes výsledky dotazu, pak dotaz je zrušena, ale není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="c30d7-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is canceled, but no exception is thrown.</span></span>

## <a name="see-also"></a><span data-ttu-id="c30d7-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c30d7-126">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="c30d7-127">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="c30d7-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="c30d7-128">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="c30d7-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
