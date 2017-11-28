---
title: "Postupy: Zrušení dotazu PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8031758462df45c030b8b75a3507f1bfb44bfd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-plinq-query"></a>Postupy: Zrušení dotazu PLINQ
Následující příklady ukazují dva způsoby, jak zrušit PLINQ dotazu. V prvním příkladu ukazuje, jak zrušit dotaz, který se skládá z průchodu dat. nejčastěji. Druhý příklad ukazuje, jak zrušit dotaz, který obsahuje funkci uživatele, která náročné.  
  
> [!NOTE]
>  Pokud je povoleno "Pouze můj kód", Visual Studio se rozdělit na řádku, která vyvolala výjimku a zobrazí chybovou zprávu, která říká "výjimka není zpracována uživatelského kódu." Tato chyba je neškodná. Můžete stisknutím klávesy F5 lze pokračovat a jejich chování zpracování výjimek, která je znázorněna v následujících příkladech. Abyste zabránili zastavení při první chybě Visual Studio, stačí zrušit zaškrtnutí políčka "Pouze můj kód" v části **nástroje, možnosti, ladění, Obecné**.  
>   
>  Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 Rozhraní framework PLINQ není vrácení jedné <xref:System.OperationCanceledException> do <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> musí být zpracována v samostatném bloku catch. Pokud jeden nebo více uživatelských delegátů vyvolá výjimku OperationCanceledException(externalCT) (pomocí externího <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), ale žádná jiná výjimka a dotaz byl definován jako `AsParallel().WithCancellation(externalCT)`, pak PLINQ vyvolá jedné <xref:System.OperationCanceledException> (externalCT) místo <xref:System.AggregateException?displayProperty=nameWithType>. Ale pokud jeden uživatel delegovat vyvolá <xref:System.OperationCanceledException>a jiný delegát vyvolá výjimku jiného typu, pak oba výjimky budou vráceny do <xref:System.AggregateException>.  
  
 Obecné pokyny pro zrušení vypadá takto:  
  
1.  Pokud provádíte zrušení uživatelského delegáta PLINQ měli informovat o externí <xref:System.Threading.CancellationToken> a výjimku <xref:System.OperationCanceledException>(externalCT).  
  
2.  Pokud dojde k zrušení a nejsou žádné další výjimky vyvolány, pak by měl zpracována <xref:System.OperationCanceledException> místo <xref:System.AggregateException>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob zpracování zrušení, když máte výpočetně náročná funkce v uživatelském kódu.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 Pokud zpracováváte zrušení v uživatelském kódu, není nutné používat <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> v definici dotazu. Ale doporučujeme, abyste to provedli protože <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> nemá žádný vliv na výkon dotazů a umožňuje zrušení zpracovávat operátory dotazu a uživatelského kódu.  
  
 Aby se zajistilo systému odezvy, doporučujeme, aby kontrolovat zrušení přibližně jednou za milisekundu; jakákoli hodnota do 10 milisekund však za přijatelnou. Tato četnost by neměla mít negativní dopad na výkon vašeho kódu.  
  
 Při uvolnění má enumerátor, například když kód ukončí smyčku foreach (pro každou v jazyce Visual Basic), který je iterování přes výsledky dotazu, pak dotazu bylo zrušeno, ale nedojde k výjimce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.ParallelEnumerable>  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md)
