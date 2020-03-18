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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138153"
---
# <a name="barrier"></a>Bariéra

A <xref:System.Threading.Barrier?displayProperty=nameWithType> je synchronizace primitivní, který umožňuje více podprocesů (označované jako *účastníci*) pracovat současně na algoritmu ve fázích. Každý účastník provede, dokud nedosáhne bodu bariéry v kódu. Bariéra představuje konec jedné fáze práce. Když účastník dosáhne bariéry, blokuje, dokud všichni účastníci nedosáhnou stejné bariéry. Poté, co všichni účastníci dosáhli bariéry, můžete volitelně vyvolat akci po fázi. Tuto akci po fázi lze použít k provádění akcí jedním vláknem, zatímco všechna ostatní vlákna jsou stále blokována. Po provedení akce jsou všichni účastníci odblokováni.  
  
 Následující fragment kódu zobrazuje základní bariérový vzor.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Úplný příklad naleznete v [tématu Jak: synchronizovat souběžné operace s Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Přidání a odebrání účastníků

 Při vytváření <xref:System.Threading.Barrier> instance zadejte počet účastníků. Účastníky můžete také kdykoli dynamicky přidávat nebo odebírat. Například pokud jeden účastník řeší jeho část problému, můžete uložit výsledek, zastavit provádění <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> v tomto vlákně a volání snížení počtu účastníků v bariéry. Přidáte-li účastníka <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>voláním , vrátí hodnota určuje aktuální číslo fáze, které může být užitečné pro inicializaci práce nového účastníka.  
  
## <a name="broken-barriers"></a>Rozbité bariéry

 Zablokování může dojít, pokud jeden účastník nedosáhne bariéry. Chcete-li se vyhnout těmto zablokování, <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> použijte přetížení metody k určení časového období a token zrušení. Tato přetížení vrátí logickou hodnotu, kterou může každý účastník zkontrolovat, než bude pokračovat do další fáze.  
  
## <a name="post-phase-exceptions"></a>Výjimky po fázi

 Pokud delegát po fázi vyvolá výjimku, je zabalen <xref:System.Threading.BarrierPostPhaseException> do objektu, který je pak rozšířen všem účastníkům.  
  
## <a name="barrier-versus-continuewhenall"></a>Bariéra versus ContinueWhenAll

 Bariéry jsou zvláště užitečné, když vlákna provádějí více fází ve smyčkách. Pokud váš kód vyžaduje pouze jednu nebo dvě <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> fáze práce, zvažte, zda použít objekty s libovolným druhem implicitního spojení, včetně:  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 Další informace naleznete v [tématu Chaining Tasks pomocí pokračování úlohy](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Viz také

- [Dělení objektů a funkcí na vlákna](threading-objects-and-features.md)
- [Postup: synchronizace souběžných operací s bariérou](how-to-synchronize-concurrent-operations-with-a-barrier.md)
