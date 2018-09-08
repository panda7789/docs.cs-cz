---
title: Pozastavení a přerušení vlákna
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b66881a8a42c0c34b5c2119f7404fe7787c8f3f2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137522"
---
# <a name="pausing-and-interrupting-threads"></a>Pozastavení a přerušení vlákna

Nejběžnější způsoby pro synchronizaci činností vlákna jsou bloku a verzi vlákna, nebo uzamčení objektů nebo oblasti kódu. Další informace o těchto zamykání a blokování mechanismy, naleznete v tématu [přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Je také možné vlákna vložit samotné do režimu spánku. Když jsou zablokované podprocesy nebo režimu spánku, můžete použít <xref:System.Threading.ThreadInterruptedException> přerušení mimo jejich stavů čekání.  
  
## <a name="the-threadsleep-method"></a>Thread.Sleep – metoda

 Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metoda způsobí, že aktuální vlákno, okamžitě zablokovat pro počet milisekund nebo časový interval předat metodě a vrací zbytek jeho časovém intervalu do jiného vlákna. Po uplynutí tohoto intervalu spící vlákno pokračuje v provádění.  
  
 Jedno vlákno nemůže volat <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> v jiném vlákně.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> je statická metoda, která způsobí, že vždy aktuální vlákno do režimu spánku.  
  
 Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> s hodnotou <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> způsobí, že vlákno do režimu spánku, dokud je přerušeno jiným vláknem, která volá <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metodu v režimu spánku vlákno nebo dokud nebude ukončen voláním jeho <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metoda.  Následující příklad znázorňuje oba způsoby by bylo třeba přerušit vlákno režimu spánku.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Přerušení vlákna

 Voláním můžete přerušit vlákno čeká <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metodu na blokovaná vlákna vyvolání <xref:System.Threading.ThreadInterruptedException>, který přeruší vlákna mimo blokovacího hovoru. Vlákno byste zachytit <xref:System.Threading.ThreadInterruptedException> a dělat všechno, co je třeba pokračovat v práci. Pokud vlákno ignoruje výjimka, modul runtime zachytí výjimku a přestane vlákno.  
  
> [!NOTE]
>  Pokud je cílové vlákno blokované, kdy <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> je volána, vlákno proces se nepřerušil dokud bloky. Pokud se nikdy blokuje vlákno, se stihlo dokončit bez nikdy přerušen.  
  
 Pokud čekání se spravované Počkejte, potom <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> obě funkce vlákno okamžitě. Při čekání na nespravované čekání (například voláním rozhraní Win32 vyvolání platformy [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) funkce), ani <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ani <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> může převzít kontrolu nad vlákno, dokud se vrátí do nebo volá do spravovaného kódu. Chování ve spravovaném kódu vypadá takto:  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> vlákna mimo všechny čekání, je možné a způsobí, že se probudí <xref:System.Threading.ThreadInterruptedException> vyvolání v cílové vlákno.  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> vlákna mimo všechny čekání, je možné a způsobí, že se probudí <xref:System.Threading.ThreadAbortException> vyvolání ve vlákně. Podrobnosti najdete v tématu [ničení vlákna](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadInterruptedException>  
- <xref:System.Threading.ThreadAbortException>  
- [Dělení na vlákna](../../../docs/standard/threading/index.md)  
- [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)  
- [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
