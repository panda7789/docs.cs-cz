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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305335"
---
# <a name="how-to-cancel-a-plinq-query"></a>Postupy: Zrušení dotazu PLINQ
Následující příklady ukazují dva způsoby, jak zrušení dotazu PLINQ. První příklad ukazuje, jak zrušit dotaz, který se skládá převážně procházení data. Druhý příklad ukazuje, jak zrušit dotaz, který obsahuje funkci uživatele, který je výpočetně náročná.  
  
> [!NOTE]
>  Pokud je povoleno "Jen můj kód", Visual Studio na řádce, která výjimku a zobrazí chybovou zprávu, že "výjimka není ošetřena v uživatelském kódu." Tato chyba je neškodná. Můžete stisknutím klávesy F5 pokračovat z něj a najdete v chování zpracování výjimek, což je znázorněno v následujících příkladech. Pokud chcete zabránit přerušení nebo první chybě sady Visual Studio, zrušte zaškrtnutí políčka "Jen můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
>   
>  V tomto příkladu je za cíl předvést využití a nemusí pracovat rychleji než ekvivalentní sekvenčních LINQ to Objects dotazům. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 Rozhraní PLINQ nevrátí jediného <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> musí být zpracovány v samostatném bloku catch. Pokud jeden nebo více uživatelských delegátech vyvolá výjimku OperationCanceledException(externalCT) (s použitím externí <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ale žádná výjimka a dotaz byl definován jako `AsParallel().WithCancellation(externalCT)`, pak PLINQ vydá jediného <xref:System.OperationCanceledException> (externalCT) spíše než výjimku <xref:System.AggregateException?displayProperty=nameWithType>. Nicméně, pokud jeden uživatelský delegát vyvolá <xref:System.OperationCanceledException>a jinou delegáta vyvolá jiný typ výjimky a pak obě výjimky budou vráceny do <xref:System.AggregateException>.  
  
 Obecné pokyny k zrušení vypadá takto:  
  
1. Pokud provádíte uživatelský delegát zrušení by měl PLINQ informovat o externí <xref:System.Threading.CancellationToken> a výjimku <xref:System.OperationCanceledException>(externalCT).  
  
2. Pokud dojde k zrušení a nejsou vyvolány žádné výjimky, pak můžete pracovat <xref:System.OperationCanceledException> spíše než výjimku <xref:System.AggregateException>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zpracovat zrušení, když máte výpočetně náročné funkce v uživatelském kódu.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 Při zpracování zrušení v uživatelském kódu, nemusíte používat <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> v definici dotazu. Doporučujeme však, že můžete udělat proto, že <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nemá žádný vliv na výkon dotazů a umožňuje zrušení zpracovávat operátorů pro dotazování a uživatelského kódu.  
  
 Aby bylo možné zajistit rychlost odezvy systému, doporučujeme zkontrolovat, zda zrušení přibližně jednou za milisekundu; období až do 10 milisekund je však považován za přijatelné. Četnost odesílání by neměla mít negativní dopad na výkon vašeho kódu.  
  
 Když enumerátor je odstraněn, třeba když kód přestane fungovat mimo smyčku foreach (pro každý v jazyce Visual Basic), která je iterování přes výsledky dotazu, pak dotazu bylo zrušeno, ale není vyvolána žádná výjimka.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq.ParallelEnumerable>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
