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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134234"
---
# <a name="how-to-cancel-a-plinq-query"></a>Postupy: Zrušení dotazu PLINQ
Následující příklady ukazují dva způsoby zrušení dotazu PLINQ. První příklad ukazuje, jak zrušit dotaz, který se skládá převážně z průchodu dat. Druhý příklad ukazuje, jak zrušit dotaz, který obsahuje uživatelskou funkci, která je výpočtově nákladné.

> [!NOTE]
> Pokud je povolena možnost "Pouze můj kód", Visual Studio se přeruší na řádku, který vyvolá výjimku a zobrazí chybovou zprávu s textem "výjimka není zpracována uživatelským kódem". Tato chyba je neškodná. Můžete stisknout Klávesu F5 pokračovat z něj a zobrazit chování zpracování výjimek, která je znázorněna v příkladech níže. Chcete-li zabránit visual studio z rozdělení na první chybu, stačí zrušit zaškrtnutí políčka "Jen můj kód" zaškrtněte políčko "Jen můj kód" v části **Nástroje, možnosti, ladění, obecné**.
>
> Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu. Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Příklad

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

Rámec PLINQ nepřevádí jeden <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; s <xref:System.OperationCanceledException> blokem úlovku se musí zacházet v samostatném bloku odlovu. Pokud jeden nebo více delegátů uživatele vyvolá OperationCanceledException(externalCT) <xref:System.Threading.CancellationToken?displayProperty=nameWithType>(pomocí externí) ale žádná jiná `AsParallel().WithCancellation(externalCT)`výjimka a dotaz byl <xref:System.OperationCanceledException> definován jako , <xref:System.AggregateException?displayProperty=nameWithType>pak PLINQ vydá jeden (externalCT) spíše než . Pokud však jeden delegát <xref:System.OperationCanceledException>uživatele vyvolá a jiný delegát vyvolá jiný typ výjimky, <xref:System.AggregateException>budou obě výjimky vráceny do .

Obecné pokyny ke zrušení jsou následující:

1. Pokud provedete zrušení delegáta uživatele, měli byste <xref:System.Threading.CancellationToken> informovat <xref:System.OperationCanceledException>PLINQ o externí a vyvolat (externalCT).

2. Pokud dojde ke zrušení a nejsou vyvolány žádné další <xref:System.OperationCanceledException> výjimky, měli byste zpracovat spíše než <xref:System.AggregateException>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak zpracovat zrušení, pokud máte výpočtově nákladné funkce v uživatelském kódu.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Při zpracování zrušení v uživatelském kódu, není <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> třeba použít v definici dotazu. Doporučujeme to však provést, protože <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nemá žádný vliv na výkon dotazu a umožňuje zrušení, které mají být zpracovány operátory dotazu a váš uživatelský kód.

Chcete-li zajistit odezvu systému, doporučujeme zkontrolovat zrušení přibližně jednou za milisekundu; však jakékoli období až do 10 milisekund je považováno za přijatelné. Tato frekvence by neměla mít negativní dopad na výkon kódu.

Při uvolnění čítače výčtu, například když kód rozdělí foreach (pro každý v jazyce Visual Basic) smyčky, která je iterace přes výsledky dotazu, pak je dotaz zrušen, ale není vyvolána žádná výjimka.

## <a name="see-also"></a>Viz také

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
