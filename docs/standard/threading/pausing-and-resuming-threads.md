---
title: "Pozastavování a obnovování vláken"
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
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b146987d2491f044e1f5794eba17d02d8f5e478c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pausing-and-resuming-threads"></a>Pozastavování a obnovování vláken
Nejběžnější způsoby pro synchronizaci aktivity vláken jsou bloku a verzi vlákna nebo objekty uzamčení nebo oblastech kódu. Další informace o těchto zamykání a blokování mechanismy najdete v tématu [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Můžete taky nechat vláken put sami do režimu spánku. Když jsou zablokované podprocesy nebo režimu spánku, můžete použít <xref:System.Threading.ThreadInterruptedException> pro přerušení je mimo stavy jejich čekání.  
  
## <a name="the-threadsleep-method"></a>Metoda Thread.Sleep  
 Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metoda způsobí, že aktuální vlákno okamžitě blokování pro počet milisekund nebo časový interval, předáte metodě a vypočítá zbytek jeho časovém intervalu na jiné vlákno. Po uplynutí této interval obnoví spící vláken provádění.  
  
 Nelze volat jedno vlákno <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> na jiné vlákno.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>je statická metoda, která způsobí, že vždy aktuální vlákno do režimu spánku.  
  
 Volání metody <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> s hodnotou <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> způsobí, že vlákno do režimu spánku, dokud bude přerušen přívod jiné vlákno, která volá <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metoda ve vlákně, v režimu spánku, nebo dokud není ukončen voláním jeho <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metoda.  Následující příklad ilustruje obě metody přerušení spící vlákna.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Přerušení vláken  
 Čekání na vlákno může přerušit voláním <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> blokované vlákno vyvolá metodu <xref:System.Threading.ThreadInterruptedException>, která dělí vlákna mimo blokování volání. Vlákno by měl catch <xref:System.Threading.ThreadInterruptedException> a jakékoli je vhodné pokračovat v práci. Pokud vlákno ignoruje výjimka, modul runtime zachytí výjimky a zastaví vlákno.  
  
> [!NOTE]
>  Pokud cílový vlákno není blokované při <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> je volána, vlákno proces se nepřerušil dokud bloky. Pokud vlákno nikdy blokuje, mohli dokončit bez někdy přerušena.  
  
 Pokud čekání je spravovaný čekání, pak <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> obě vlákno probuzení okamžitě. Pokud čekání nespravované čekání (například platformu vyvolat volání Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) funkce), ani <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ani <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> může převzít kontrolu nad vlákno, dokud vrátí nebo volá do spravovaného kódu. Ve spravovaném kódu chování je následující:  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>vlákna mimo žádné čekání to může být v a způsobí, že se probudí <xref:System.Threading.ThreadInterruptedException> vyvolání ve vlákně na cílový.  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>vlákna mimo žádné čekání to může být v a způsobí, že se probudí <xref:System.Threading.ThreadAbortException> vyvolání na vlákno. Podrobnosti najdete v tématu [zničení vláken](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
