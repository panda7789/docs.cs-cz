---
title: "Bariéra [.NET Framework]"
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
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 392e975f6bf566c2ba36290940eb0daee03f004f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="barrier-net-framework"></a>Bariéra [.NET Framework]
A *barrier* je uživatelem definované synchronizaci primitivní umožňující více vláken (označované jako *účastníky*) pro práci současně na algoritmus ve fázích. Každý účastník, provede, dokud nebude dosaženo bodem bariéry v kódu. Bariéry představuje konec jednou z fází práce. Když účastník dosáhne bariéry, zablokuje, dokud všichni účastníci dosáhli stejné bariéry. Po všichni účastníci dosáhli bariéry, můžete případně vyvolat po fáze akce. Tato fáze po akce slouží k provádění akcí podle jedním vláknem a při jiná vlákna jsou stále zablokované. Po provedení akce, jsou všechny odblokuje jednotlivými účastníky.  
  
 Následující fragment kódu ukazuje základní bariéry vzor.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Úplný příklad najdete v tématu [postupy: synchronizace souběh operací pomocí bariéry](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Přidávání a odebírání účastníky  
 Při vytváření <xref:System.Threading.Barrier>, zadejte počet účastníky. Můžete také přidat nebo odebrat účastníky dynamicky kdykoli. Například pokud jeden účastník řeší jeho součástí problém, můžete uložit výsledek zastavit provádění na vláken a volání <xref:System.Threading.Barrier.RemoveParticipant%2A> se sníží počet účastníků bariéry. Když přidáte účastník voláním <xref:System.Threading.Barrier.AddParticipant%2A>, návratová hodnota určuje číslo aktuální fáze, které můžou být užitečné, chcete-li inicializovat pracovní nového člena.  
  
## <a name="broken-barriers"></a>Přerušený překážek  
 Blokování může dojít, pokud jeden účastník nepodaří spojit bariéry. Abyste se vyhnuli tyto zablokování, použijte přetížení <xref:System.Threading.Barrier.SignalAndWait%2A> metoda a zadat časový limit a token zrušení. Tyto návratové přetížení logická hodnota, která každý účastník můžete zkontrolovat dříve, než se i nadále v další fázi.  
  
## <a name="post-phase-exceptions"></a>Po první fáze výjimky  
 Pokud po fáze delegát vyvolá výjimku, je uzavřen do <xref:System.Threading.BarrierPostPhaseException> objekt, který je pak se rozšíří všichni účastníci.  
  
## <a name="barrier-versus-continuewhenall"></a>Barrier Versus ContinueWhenAll  
 Překážek jsou zvláště užitečné, když vláken provádění více fáze v smyčky. Pokud váš kód vyžaduje pouze jednu nebo dvě fáze práce, zvažte použití <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty s jakýmkoli implicitní připojení, včetně:  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 Další informace najdete v tématu [řetězení úloh pomocí úloh pokračování pomocí](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Viz také  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Postupy: Synchronizace souběžných operací pomocí třídy Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
