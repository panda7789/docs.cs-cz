---
title: Semafor a SemaphoreSlim
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- counting semaphores
- semaphores
- threading [.NET Framework], cross-process synchronization
- Semaphore class, about Semaphore class
- SemaphoreSlim class, about SemaphoreSlim class
- threading [.NET Framework], Semaphore class
ms.assetid: 7722a333-b974-47a2-a7c0-f09097fb644e
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 039dee4df1a6d06fa1833eae077817ff5eca3ea3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor a SemaphoreSlim
<xref:System.Threading.Semaphore?displayProperty=nameWithType> Třída reprezentuje s názvem (systémové) nebo místní semafor. Je dynamické obálku kolem objekt semafor Win32. Win32 semaforů jsou počítání semaforů, které se dají použít k řízení přístupu k fondu zdrojů.  
  
 <xref:System.Threading.SemaphoreSlim> Třída reprezentuje lightweight rychlé semafor, který lze použít pro čekání na v rámci jednoho procesu, když očekávané velmi krátké době čekání. <xref:System.Threading.SemaphoreSlim>využívá co nejvíce na synchronizace primitiv poskytované common language runtime (CLR). Však poskytuje také obslužné rutiny čekání líné inicializovaného, na základě jádra podle potřeby pro podporu čekání na více semaforů. <xref:System.Threading.SemaphoreSlim>také podporuje použití tokenů zrušení, ale nepodporuje s názvem semaforů nebo použití popisovač čekání synchronizace.  
  
## <a name="managing-a-limited-resource"></a>Správa omezené prostředků  
 Vláken zadejte semaforu voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metodu, která je zděděn z <xref:System.Threading.WaitHandle> třídy, v případě <xref:System.Threading.Semaphore?displayProperty=nameWithType> objekt, nebo <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> metoda, v případě <xref:System.Threading.SemaphoreSlim> objektu... Když se volání vrátí, počet na semaforu se odečte. Když vlákno požadavky položky a počet rovná nule, bloky přístup z více vláken. Jako vláken verze semaforu voláním <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metody pozastavených vláken mohou zadat. Pozastavených vláken na vstup do semaforu neexistuje žádné zaručenou pořadí, jako je například first in, použity nebo last-in, první ven (LIFO).  
  
 Vlákno můžete zadat semaforu vícekrát voláním <xref:System.Threading.Semaphore?displayProperty=nameWithType> objektu <xref:System.Threading.WaitHandle.WaitOne%2A> metoda nebo <xref:System.Threading.SemaphoreSlim> objektu <xref:System.Threading.SemaphoreSlim.Wait%2A> metoda opakovaně. Chcete-li uvolnit semafor, vlákno můžete buď volání <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> metoda přetížení stejný počet pokusů, nebo volejte <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> metoda přetížení a zadat počet položek k uvolnění.  
  
### <a name="semaphores-and-thread-identity"></a>Semaforů a Identity přístup z více vláken  
 Semafor dva typy Nevynucovat identita přístup z více vláken na volání <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A>, a <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metody. Například běžný scénář použití pro semaforů zahrnuje vlákno výrobce a příjemce přístup z více vláken, s jedním vláknem vždy zvyšování počet semafor a dalších vždy dekrementace ho.  
  
 Je zodpovědností pro programátory zajistit, že vlákno neuvolní semaforu příliš mnohokrát. Například předpokládejme, že semafor má maximální počet dva a že vláken A a vlákno B obě zadejte semaforu. Pokud k chybě programování ve vláknu B způsobuje, že volání `Release` dvakrát obě volání úspěšné. Počet na semafor je plný a pokud vláken A nakonec volá `Release`, <xref:System.Threading.SemaphoreFullException> je vyvolána výjimka.  
  
## <a name="named-semaphores"></a>Pojmenované semaforů  
 Operační systém Windows umožňuje semaforů názvy. Pojmenované semafor je celého systému. To znamená že po vytvoření pojmenovaného semafor je viditelná pro všechny vláken ve všech procesů. Proto s názvem semafor slouží k synchronizaci aktivity procesy a také vláken.  
  
 Můžete vytvořit <xref:System.Threading.Semaphore> objekt, který reprezentuje semafor pojmenované systém pomocí jedné z konstruktorů, které určuje název.  
  
> [!NOTE]
>  Protože pojmenované semaforů celého systému, je možné, že více <xref:System.Threading.Semaphore> objekty, které představují stejné s názvem semafor. Pokaždé, když voláte konstruktor nebo <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> metoda, nový <xref:System.Threading.Semaphore> je vytvořen objekt. Zadat stejný název opakovaně vytvoří více objektů, které představují stejnou pojmenované semafor.  
  
 Při použití s názvem semaforů buďte opatrní. Protože jsou celého systému, jiný proces, který používá stejný název můžete zadat vaše semafor neočekávaně. Škodlivý kód provádění na stejném počítači může použít jako základ útoku denial of service.  
  
 Použít zabezpečení řízení přístupu k ochraně <xref:System.Threading.Semaphore> objekt, který představuje pojmenovanou semafor, ideálně s využitím konstruktor, který určuje <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> objektu. Můžete taky použít přístupu k řízení zabezpečení pomocí <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> metoda, ale ponechá okno ohrožení zabezpečení mezi časem semaforu je vytvořena a čas, který je chráněn. Ochrana semaforů s zabezpečení řízení přístupu pomáhá zabránit útoky se zlými úmysly, ale nebyl vyřešen problém kolize neúmyslnému názvů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Semaphore>  
 <xref:System.Threading.SemaphoreSlim>  
 [Dělení na vlákna objektů a funkcí](../../../docs/standard/threading/threading-objects-and-features.md)
