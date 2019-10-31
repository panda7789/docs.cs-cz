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
ms.openlocfilehash: 272f25d62cb63c60209be3bc54dc5e76fb30df54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134234"
---
# <a name="how-to-cancel-a-plinq-query"></a>Postupy: Zrušení dotazu PLINQ
Následující příklady znázorňují dva způsoby, jak zrušit dotaz PLINQ. První příklad ukazuje, jak zrušit dotaz, který se skládá hlavně z procházení dat. Druhý příklad ukazuje, jak zrušit dotaz, který obsahuje uživatelskou funkci, která je výpočetně náročná.

> [!NOTE]
> Když je povolená možnost Pouze můj kód, Visual Studio se na řádku, který vyvolá výjimku, přeruší a zobrazí se chybová zpráva s informacemi o tom, že výjimka není zpracována uživatelským kódem. Tato chyba je neškodná. Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech. Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.
>
> Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Příklad

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

Rozhraní PLINQ nezahrnuje jeden <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> musí být zpracována v samostatném bloku catch. Pokud jeden nebo více delegátů uživatele vyvolá OperationCanceledException (externalCT) (pomocí externího <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ale žádná jiná výjimka a dotaz byl definován jako `AsParallel().WithCancellation(externalCT)`, pak PLINQ vydá jedinou <xref:System.OperationCanceledException> (externalCT) místo <xref:System.AggregateException?displayProperty=nameWithType>. Nicméně pokud jeden delegát uživatele vyvolá <xref:System.OperationCanceledException>a jiný delegát vyvolá jiný typ výjimky, pak obě výjimky budou zahrnuty do <xref:System.AggregateException>.

Obecné pokyny týkající se zrušení jsou následující:

1. Pokud provádíte zrušení delegáta uživatele, měli byste informovat o PLINQ <xref:System.Threading.CancellationToken> a vyvolat <xref:System.OperationCanceledException>(externalCT).

2. Pokud dojde k zrušení a nejsou vyvolány žádné další výjimky, měli byste zpracovat <xref:System.OperationCanceledException> místo <xref:System.AggregateException>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zpracovat zrušení, když máte výpočetní náročnou funkci v uživatelském kódu.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Při zpracování zrušení v uživatelském kódu není nutné používat <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> v definici dotazu. Nicméně doporučujeme, abyste to provedli, protože <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nemá žádný vliv na výkon dotazů a umožňuje, aby se zrušení zpracovalo pomocí operátorů dotazů a uživatelského kódu.

Aby se zajistila odezva systému, doporučujeme, abyste kontrolovali zrušení přibližně jednou za milisekundu. Nicméně jakékoli období až 10 milisekund se považuje za přijatelné. Tato frekvence by neměla mít negativní vliv na výkon vašeho kódu.

Když je vyjímka vyhozena, například když se kód rozdělí mimo smyčku foreach (for each in Visual Basic), která provádí iteraci přes výsledky dotazu, je dotaz zrušen, ale není vyvolána žádná výjimka.

## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
