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
# <a name="how-to-cancel-a-plinq-query"></a>Postupy: Zrušení dotazu PLINQ
Následující příklady znázorňují dva způsoby, jak zrušit dotaz PLINQ. První příklad ukazuje, jak zrušit dotaz, který se skládá hlavně z procházení dat. Druhý příklad ukazuje, jak zrušit dotaz, který obsahuje uživatelskou funkci, která je výpočetně náročná.

> [!NOTE]
> Když je povolená možnost Pouze můj kód, Visual Studio se na řádku, který vyvolá výjimku, přeruší a zobrazí se chybová zpráva s informacemi o tom, že výjimka není zpracována uživatelským kódem. Tato chyba je neškodná. Stiskem klávesy F5 můžete pokračovat a zobrazit chování zpracování výjimek, které je znázorněno v níže uvedených příkladech. Chcete-li aplikaci Visual Studio zabránit v přerušení první chyby, zrušte zaškrtnutí políčka Pouze můj kód v části **nástroje, možnosti, ladění, obecné**.
>
> Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).

## <a name="example"></a>Příklad

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

Rozhraní PLINQ nezahrnuje jednu hodnotu <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType> . <xref:System.OperationCanceledException> musí být zpracována v samostatném bloku catch. Pokud jeden nebo více delegátů uživatele vyvolá OperationCanceledException (externalCT) (pomocí externí <xref:System.Threading.CancellationToken?displayProperty=nameWithType> ), ale bez jiné výjimky a dotaz byl definován jako `AsParallel().WithCancellation(externalCT)` , pak PLINQ vydá jednu <xref:System.OperationCanceledException> (externalCT), nikoli <xref:System.AggregateException?displayProperty=nameWithType> . Nicméně pokud jeden uživatelský delegát vyvolá výjimku <xref:System.OperationCanceledException> a jiný delegát vyvolá jiný typ výjimky, pak obě výjimky budou zahrnuty do <xref:System.AggregateException> .

Obecné pokyny týkající se zrušení jsou následující:

1. Pokud provádíte zrušení uživatelem delegáta, měli byste informovat o externích <xref:System.Threading.CancellationToken> událostech a vyvolat výjimku <xref:System.OperationCanceledException> (externalCT).

2. Pokud dojde k zrušení a nejsou vyvolány žádné další výjimky, pak je zpracována <xref:System.OperationCanceledException> místo <xref:System.AggregateException> .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zpracovat zrušení, když máte výpočetní náročnou funkci v uživatelském kódu.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Při zpracování zrušení v uživatelském kódu není nutné používat <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> v definici dotazu. Doporučujeme však použít <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> , protože <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nemá žádný vliv na výkon dotazů a umožňuje zrušení zpracování pomocí operátorů dotazů a uživatelského kódu.

Aby se zajistila odezva systému, doporučujeme, abyste kontrolovali zrušení přibližně jednou za milisekundu. Nicméně jakékoli období až 10 milisekund se považuje za přijatelné. Tato frekvence by neměla mít negativní vliv na výkon vašeho kódu.

Když je vyjímka vyhozena, například když se kód rozdělí mimo smyčku foreach (for each in Visual Basic), která provádí iteraci nad výsledky dotazu, je dotaz zrušen, ale není vyvolána žádná výjimka.

## <a name="see-also"></a>Viz také

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)
- [Zrušení ve spravovaných vláknech](../threading/cancellation-in-managed-threads.md)
