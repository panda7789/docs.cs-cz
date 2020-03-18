---
title: Pozastavení a přerušení vláken
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interrupting threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
ms.openlocfilehash: 3020694b93479d5f1d64d31c203f8fe033a10320
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128996"
---
# <a name="pausing-and-interrupting-threads"></a>Pozastavení a přerušení vláken

Nejběžnější způsoby synchronizace aktivit podprocesů jsou blokování a uvolnění podprocesů nebo uzamčení objektů nebo oblastí kódu. Další informace o těchto mechanismech uzamčení a blokování naleznete v [tématu Přehled primitivních synchronizačních modulů](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Můžete také mít vlákna dát sami spát. Když jsou vlákna blokována nebo <xref:System.Threading.ThreadInterruptedException> usnout, můžete je použít k jejich vylomení z jejich čekacích stavů.  
  
## <a name="the-threadsleep-method"></a>Metoda Thread.Sleep

 Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metody způsobí, že aktuální vlákno okamžitě blokovat pro počet milisekund nebo časový interval, který předáte metodě a výnosy zbytek jeho časový úsek do jiného vlákna. Po uplynutí tohoto intervalu podproces spánku obnoví provádění.  
  
 Jedno vlákno <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> nemůže volat na jiné vlákno.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>je statická metoda, která vždy způsobí, že aktuální vlákno do režimu spánku.  
  
 Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> s hodnotou <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> způsobí, že vlákno do režimu spánku, dokud je přerušeno jiným vláknem, které volá metodu <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> v podprocesu spánku, nebo dokud není ukončena voláním jeho <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody.  Následující příklad ilustruje obě metody přerušení podprocesu spánku.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Přerušení vláken

 Čekající vlákno můžete přerušit voláním metody na <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> blokovaném vlákně k vyvolání <xref:System.Threading.ThreadInterruptedException>, která přeruší vlákno z blokování volání. Vlákno by mělo <xref:System.Threading.ThreadInterruptedException> zachytit a dělat, co je vhodné pokračovat v práci. Pokud vlákno ignoruje výjimku, zachytí runtime výjimku a zastaví vlákno.  
  
> [!NOTE]
> Pokud cílové vlákno není <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> blokován, když je volána, vlákno není přerušeno, dokud se zablokuje. Pokud vlákno nikdy blokuje, mohlo by být dokončeno, aniž by bylo přerušeno.  
  
 Pokud wait je spravované čekání, pak <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> oba probudit vlákno okamžitě. Pokud wait je nespravované čekání (například platforma vyvolat volání Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) funkce), ani <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> převzít kontrolu podprocesu, dokud se vrátí nebo volání do spravovaného kódu. Ve spravovaném kódu je chování následující:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>probudí vlákno z jakékoli čekání může být v <xref:System.Threading.ThreadInterruptedException> a způsobí, že být vyvolána v cílovém vlákně.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>probudí vlákno z jakékoli čekání může být v <xref:System.Threading.ThreadAbortException> a způsobí, že být vyvolána na vlákno. Podrobnosti naleznete v [tématu Zničení vláken](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [Threading](../../../docs/standard/threading/index.md)
- [Použití vláken a zřetězení](../../../docs/standard/threading/using-threads-and-threading.md)
- [Přehled základních synchronizačních zařízení](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
