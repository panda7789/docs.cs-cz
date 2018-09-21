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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbbf7055a250ae7fa630097f3014a6420228fed3
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46538274"
---
# <a name="barrier"></a>Bariéra

A <xref:System.Threading.Barrier?displayProperty=nameWithType> je primitiv synchronizace, která umožňuje více vláken (označované jako *účastníci*) pracovat souběžně na algoritmus ve fázích. Každý účastník opakuje, dokud se nedosáhne barrier bod v kódu. Odbourejte překážky bránící představuje konec jednu fázi práce. Odbourejte překážky bránící dosáhne účastníka blokuje, dokud všichni účastníci dosáhnou této bariéry stejné. Jakmile všichni účastníci dosáhnou této bariéry, můžete volitelně vyvolat akce po fázi. Tuto fázi po akci můžete využívat k provádění akcí jedním vláknem a když jsou všechny ostatní vlákna budou i nadále zablokované. Po spuštění akce jsou všechny odblokované účastníci.  
  
 Následující fragment kódu ukazuje základní barrier vzor.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Kompletní příklad naleznete v tématu [postupy: synchronizace souběh operací pomocí bariéry](how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Přidávání a odebírání účastníků

 Když vytvoříte <xref:System.Threading.Barrier> instance, zadejte počet účastníků. Můžete také přidat nebo odebrat účastníci dynamicky kdykoli. Například, pokud jeden účastník řeší jeho část problému, můžete uložit výsledek, zastavit provádění na vlákno a volat <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> se sníží počet účastníků v odbourejte překážky bránící. Když přidáte účastníka voláním <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, návratová hodnota určuje číslo aktuální fázi, který může být užitečné, pokud chcete inicializovat pracovní nového účastníka.  
  
## <a name="broken-barriers"></a>Nefunkční překážek

 Zablokování může dojít, pokud jeden účastník nepodaří spojit odbourejte překážky bránící. Aby se zabránilo tyto zablokování, použijte přetížení <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> metoda zadat časový limit a token zrušení. Tato přetížení návratový logická hodnota, která každých účastníka můžete zkontrolovat dříve, než bude pokračovat do další fáze.  
  
## <a name="post-phase-exceptions"></a>Po fázi výjimky

 Pokud po fázi delegáta vyvolá výjimku, je obalen <xref:System.Threading.BarrierPostPhaseException> objekt, který je pak šířený do všichni účastníci.  
  
## <a name="barrier-versus-continuewhenall"></a>Barrier oproti ContinueWhenAll

 Vlákna provádění více fázích ve smyčkách jsou zvláště užitečné překážek. Pokud váš kód vyžaduje pouze jednu nebo dvě fáze práce, zvažte, jestli se má použít <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty s jakýmkoli implicitní spojení, včetně:  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 Další informace najdete v tématu [řetězení úloh pomocí úloh pokračování používání](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Viz také:

- [Práce s vlákny funkce a objekty](threading-objects-and-features.md)  
- [Postupy: synchronizace souběh operací pomocí bariéry](how-to-synchronize-concurrent-operations-with-a-barrier.md)
