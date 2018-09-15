---
title: Bariéra [.NET Framework]
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 385e370f205851630f809b285a93c2609220efeb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647548"
---
# <a name="barrier-net-framework"></a>Bariéra [.NET Framework]
A *bariéry* je uživatelem definovaný primitiv synchronizace, která umožňuje více vláken (označované jako *účastníci*) pracovat souběžně na algoritmus ve fázích. Každý účastník opakuje, dokud se nedosáhne barrier bod v kódu. Odbourejte překážky bránící představuje konec jednu fázi práce. Odbourejte překážky bránící dosáhne účastníka blokuje, dokud všichni účastníci dosáhnou této bariéry stejné. Jakmile všichni účastníci dosáhnou této bariéry, můžete volitelně vyvolat akce po fázi. Tuto fázi po akci můžete využívat k provádění akcí jedním vláknem a když jsou všechny ostatní vlákna budou i nadále zablokované. Po spuštění akce jsou všechny odblokované účastníci.  
  
 Následující fragment kódu ukazuje základní barrier vzor.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Kompletní příklad naleznete v tématu [postupy: synchronizace souběžných operací pomocí bariéry](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Přidávání a odebírání účastníků  
 Když vytvoříte <xref:System.Threading.Barrier>, zadejte počet účastníků. Můžete také přidat nebo odebrat účastníci dynamicky kdykoli. Například, pokud jeden účastník řeší jeho část problému, můžete uložit výsledek, zastavit provádění na vlákno a volat <xref:System.Threading.Barrier.RemoveParticipant%2A> se sníží počet účastníků v odbourejte překážky bránící. Když přidáte účastníka voláním <xref:System.Threading.Barrier.AddParticipant%2A>, návratová hodnota určuje číslo aktuální fázi, který může být užitečné, pokud chcete inicializovat pracovní nového účastníka.  
  
## <a name="broken-barriers"></a>Nefunkční překážek  
 Zablokování může dojít, pokud jeden účastník nepodaří spojit odbourejte překážky bránící. Aby se zabránilo tyto zablokování, použijte přetížení <xref:System.Threading.Barrier.SignalAndWait%2A> metoda zadat časový limit a token zrušení. Tato přetížení návratový logická hodnota, která každých účastníka můžete zkontrolovat dříve, než bude pokračovat do další fáze.  
  
## <a name="post-phase-exceptions"></a>Po fázi výjimky  
 Pokud po fázi delegáta vyvolá výjimku, je obalen <xref:System.Threading.BarrierPostPhaseException> objekt, který je pak šířený do všichni účastníci.  
  
## <a name="barrier-versus-continuewhenall"></a>Barrier oproti ContinueWhenAll  
 Vlákna provádění více fázích ve smyčkách jsou zvláště užitečné překážek. Pokud váš kód vyžaduje pouze jednu nebo dvě fáze práce, zvažte, jestli se má použít <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty s jakýmkoli implicitní spojení, včetně:  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 Další informace najdete v tématu [řetězení úloh pomocí úloh pokračování používání](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Viz také:

- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
- [Postupy: Synchronizace souběžných operací pomocí třídy Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
