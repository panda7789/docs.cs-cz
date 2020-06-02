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
ms.openlocfilehash: 369631603791d90c51244c1dc9907b9d8ec17364
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291159"
---
# <a name="pausing-and-interrupting-threads"></a>Pozastavení a přerušení vláken

Nejběžnější způsob, jak synchronizovat aktivity vláken, je blokovat a vydávat vlákna nebo uzamknout objekty nebo oblasti kódu. Další informace o těchto mechanismech uzamykání a blokování najdete v tématu [Přehled primitiv synchronizace](overview-of-synchronization-primitives.md).  
  
 Vlákna je také možné umístit do režimu spánku. Pokud jsou vlákna blokována nebo v režimu spánku, můžete použít <xref:System.Threading.ThreadInterruptedException> k rozdělení do jejich čekacích stavů.  
  
## <a name="the-threadsleep-method"></a>Thread. Sleep – Metoda

 Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> metody způsobí, že aktuální vlákno okamžitě zablokuje počet milisekund nebo časový interval, který do metody předáte, a vyřadí zbytek časového řezu jinému vláknu. Po uplynutí tohoto intervalu pokračuje běh vlákna v režimu spánku.  
  
 Jedno vlákno nemůže volat <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> jiné vlákno.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>je statická metoda, která vždy způsobí, že aktuální vlákno bude v režimu spánku.  
  
 Volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> s hodnotou způsobí, že se <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> vlákno dokončí do spánku, dokud není přerušeno jiným vláknem, které volá <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metodu na pozastaveném vlákně, nebo dokud není ukončeno voláním <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody.  Následující příklad ilustruje obě metody přerušení spícího vlákna.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Přerušení vláken

 Můžete přerušit čekající vlákno voláním <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> metody v blokovaném vláknu a vyvolat výjimku <xref:System.Threading.ThreadInterruptedException> , která přeruší vlákno mimo blokující volání. Vlákno by mělo zachytit <xref:System.Threading.ThreadInterruptedException> a dělat vše, co je vhodné pro pokračování v práci. Pokud vlákno ignoruje výjimku, modul runtime zachytí výjimku a zastaví vlákno.  
  
> [!NOTE]
> Pokud cílové vlákno není blokováno při <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> volání, vlákno není přerušeno, dokud se neblokuje. Pokud vlákno nikdy není blokováno, může být dokončeno bez přerušení.  
  
 Pokud je čekání spravovaným čekáním, pak <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> obě vlákna okamžitě probudit. Pokud je čekání nespravovaným čekáním (například platforma vyvolá volání funkce Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) ), ani <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> nemůže převzít kontrolu nad vláknem, dokud se nevrátí do spravovaného kódu nebo do něj nevrátí volání. Ve spravovaném kódu je chování následující:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>probudí vlákno z jakéhokoli čekání, které může být v a způsobí, že bude <xref:System.Threading.ThreadInterruptedException> vyvoláno v cílovém vlákně.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>probudí vlákno z jakéhokoli čekání, které může být v a způsobí, že bude ve <xref:System.Threading.ThreadAbortException> vlákně vyvolána výjimka. Podrobnosti najdete v tématu [zničení vláken](destroying-threads.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [Dělení na vlákna](index.md)
- [Použití vláken a dělení na vlákna](using-threads-and-threading.md)
- [Přehled primitiv synchronizace](overview-of-synchronization-primitives.md)
