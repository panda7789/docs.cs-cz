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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3dcee9c45cdbf029ccba90a963c9cea0a9c7ad4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963568"
---
# <a name="pausing-and-interrupting-threads"></a>Pozastavení a přerušení vláken

Nejběžnější způsob, jak synchronizovat aktivity vláken, je blokovat a vydávat vlákna nebo uzamknout objekty nebo oblasti kódu. Další informace o těchto mechanismech uzamykání a blokování najdete v tématu [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Vlákna je také možné umístit do režimu spánku. Pokud jsou vlákna blokována nebo v režimu spánku, můžete <xref:System.Threading.ThreadInterruptedException> použít k rozdělení do jejich čekacích stavů.  
  
## <a name="the-threadsleep-method"></a>Thread. Sleep – Metoda

 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> Volání metody způsobí, že aktuální vlákno okamžitě zablokuje počet milisekund nebo časový interval, který do metody předáte, a vyřadí zbytek časového řezu jinému vláknu. Po uplynutí tohoto intervalu pokračuje běh vlákna v režimu spánku.  
  
 Jedno vlákno nemůže volat <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> jiné vlákno.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>je statická metoda, která vždy způsobí, že aktuální vlákno bude v režimu spánku.  
  
 Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> s <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> hodnotou způsobí, že se vlákno dokončí do spánku, dokud není přerušeno jiným vláknem, které volá metodu na pozastaveném vlákně, nebo dokud není ukončeno voláním metody. <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType>  Následující příklad ilustruje obě metody přerušení spícího vlákna.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Přerušení vláken

 Můžete přerušit čekající vlákno voláním <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody v blokovaném vláknu a <xref:System.Threading.ThreadInterruptedException>vyvolat výjimku, která přeruší vlákno mimo blokující volání. Vlákno by mělo zachytit <xref:System.Threading.ThreadInterruptedException> a dělat vše, co je vhodné pro pokračování v práci. Pokud vlákno ignoruje výjimku, modul runtime zachytí výjimku a zastaví vlákno.  
  
> [!NOTE]
> Pokud cílové vlákno není blokováno při <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> volání, vlákno není přerušeno, dokud se neblokuje. Pokud vlákno nikdy není blokováno, může být dokončeno bez přerušení.  
  
 Pokud je čekání spravovaným čekáním, pak <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> obě vlákna okamžitě probudit. Pokud je čekání nespravovaným čekáním (například platforma vyvolá volání funkce Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) ), ani <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> nemůže převzít kontrolu nad vláknem, dokud se nevrátí do spravovaného kódu nebo do něj nevrátí volání. Ve spravovaném kódu je chování následující:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>probudí vlákno z jakéhokoli čekání, <xref:System.Threading.ThreadInterruptedException> které může být v a způsobí, že bude vyvoláno v cílovém vlákně.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>probudí vlákno z jakéhokoli čekání, <xref:System.Threading.ThreadAbortException> které může být v a způsobí, že bude ve vlákně vyvolána výjimka. Podrobnosti najdete v tématu [zničení vláken](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [Dělení na vlákna](../../../docs/standard/threading/index.md)
- [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)
- [Přehled primitiv synchronizace](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
