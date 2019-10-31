---
title: Bariéra
ms.date: 09/14/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
ms.openlocfilehash: 5aa34f7f39f4b9b626bea29372cf984f3cefb361
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138153"
---
# <a name="barrier"></a>Bariéra

<xref:System.Threading.Barrier?displayProperty=nameWithType> je prostředí pro synchronizaci, které umožňuje více vláknům (známým jako *účastníkům*) pracovat souběžně na algoritmu ve fázích. Každý účastník provede, dokud nedosáhne bodu bariéry v kódu. Bariéra představuje konec jedné fáze práce. Když účastník dosáhne bariéry, blokuje, dokud všichni účastníci nedosáhnou stejné bariéry. Až všichni účastníci dosáhnou bariéry, můžete volitelně vyvolat akci po fázi. Tato akce po fázi se dá použít k provedení akcí v jednom vlákně, zatímco všechna ostatní vlákna jsou pořád blokovaná. Po provedení akce se všechny účastníky odblokují.  
  
 Následující fragment kódu ukazuje základní vzorek bariéry.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Úplný příklad naleznete v tématu [How to: Synchronize souběžných operací s bariérou](how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Přidávání a odebírání účastníků

 Při vytváření instance <xref:System.Threading.Barrier> určete počet účastníků. Kdykoli můžete kdykoli přidat nebo odebrat účastníky. Například pokud jeden účastník vyřeší svou součást problému, můžete uložit výsledek, zastavit provádění tohoto vlákna a volat <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> pro snížení počtu účastníků v bariérě. Když přidáte účastníka voláním <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, vrácená hodnota určuje aktuální číslo fáze, které může být užitečné k inicializaci práce nového účastníka.  
  
## <a name="broken-barriers"></a>Přerušené bariéry

 Pokud se jednomu účastníku nepovede spojit s bariérou, může dojít k zablokování. Chcete-li se tomuto zablokování vyhnout, použijte přetížení metody <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> a určete časový limit a token zrušení. Tato přetížení vrátí logickou hodnotu, kterou každý účastník může před pokračováním do další fáze ověřit.  
  
## <a name="post-phase-exceptions"></a>Výjimky po fázi

 Pokud delegát po fázi vyvolá výjimku, je zabalena do objektu <xref:System.Threading.BarrierPostPhaseException>, který je poté šířen do všech účastníků.  
  
## <a name="barrier-versus-continuewhenall"></a>Bariéra versus ContinueWhenAll

 Bariéry jsou obzvláště užitečné, pokud vlákna provádějí více fází ve smyčce. Pokud váš kód vyžaduje jenom jednu nebo dvě fáze práce, zvažte, jestli použít <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty s libovolným typem implicitního spojení, včetně:  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 Další informace najdete v tématu [zřetězení úloh pomocí úloh pokračování](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Viz také:

- [Dělení objektů a funkcí](threading-objects-and-features.md)
- [Postupy: synchronizace souběžných operací s bariérou](how-to-synchronize-concurrent-operations-with-a-barrier.md)
