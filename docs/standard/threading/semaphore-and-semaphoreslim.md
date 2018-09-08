---
title: Semafor a SemaphoreSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- counting semaphores
- semaphores
- threading [.NET Framework], cross-process synchronization
- Semaphore class, about Semaphore class
- SemaphoreSlim class, about SemaphoreSlim class
- threading [.NET Framework], Semaphore class
ms.assetid: 7722a333-b974-47a2-a7c0-f09097fb644e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e98862aba937724c799adef597260a06ed495f6
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44199762"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor a SemaphoreSlim
<xref:System.Threading.Semaphore?displayProperty=nameWithType> Třída představuje pojmenované (systémové) nebo místní "Semaphore". Je dynamického zajišťování obálku kolem objektu semafor Win32. Win32 semafory jsou počítání semaforů, které je možné použít k řízení přístupu k fondu zdrojů.  
  
 <xref:System.Threading.SemaphoreSlim> Třída představuje semafor odlehčený, rychlý, který se dá použít pro čekání v rámci jednoho procesu při velmi krátké očekávané době čekání. <xref:System.Threading.SemaphoreSlim> spoléhá na synchronizací primitiv modulem common language runtime (CLR) k dispozici co nejvíc. Ale také poskytuje obslužné rutiny čekání laxně inicializovaný, na základě jádra podle potřeby pro podporu čekání na více semafory. <xref:System.Threading.SemaphoreSlim> také podporuje použití tokenů zrušení, ale nepodporuje s názvem semafory nebo použijte popisovač čekání synchronizace.  
  
## <a name="managing-a-limited-resource"></a>Správa prostředků omezené  
 Vlákna zadejte semafor voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metodu, která se dědí z <xref:System.Threading.WaitHandle> třídy, v případě <xref:System.Threading.Semaphore?displayProperty=nameWithType> objektu, nebo <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> metodu v případě <xref:System.Threading.SemaphoreSlim> objektu... Při volání se vrátí se odečte počet na semaforu. Když vlákno požádá o vstupu a počet je nula, vlákno blokováno. Jako vláken verzi semafor voláním <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metody blokovaná vlákna budou moci zadat. Blokovaná vlákna k zadání semafor je zaručeno pořadí, jako je například první dovnitř, první ven (FIFO) nebo poslední dovnitř, první ven (LIFO).  
  
 Vlákno můžete zadat semafor více než jednou voláním <xref:System.Threading.Semaphore?displayProperty=nameWithType> objektu <xref:System.Threading.WaitHandle.WaitOne%2A> metoda nebo <xref:System.Threading.SemaphoreSlim> objektu <xref:System.Threading.SemaphoreSlim.Wait%2A> metoda opakovaně. Vydat semafor vlákna můžete buď zavolat <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> metody přetížení stejný počet, kolikrát, nebo volání <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> metoda přetížení a zadat počet položek, které mají být všeobecně dostupné.  
  
### <a name="semaphores-and-thread-identity"></a>Semaforů a identitu vlákna  
 Semafor dva typy Nevynucovat identitu vlákna na volání <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A>, a <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metody. Například běžný scénář využití pro semafory zahrnuje vlákno výrobce a příjemce vlákna, s jedno vlákno vždy zvyšování počtu pro semafor a druhý vždy dekrementace ho.  
  
 Je programátorovi povinností ujistit se, že vlákno neuvolní semafor příliš mnohokrát. Například předpokládejme, že semafor má maximální počet dva a tohoto vlákna A a vlákna B obě zadejte semafor. Pokud k chybě programování ve vlákně B způsobí, že jej, aby volalo `Release` dvakrát, obě volání úspěšné. Počet na semaforu je plný a pokud vlákno A nakonec volá `Release`, <xref:System.Threading.SemaphoreFullException> je vyvolána výjimka.  
  
## <a name="named-semaphores"></a>Pojmenované semafory  
 Operační systém Windows umožňuje semafory mít názvy. Pojmenované semafor je v systému. To znamená že po vytvoření pojmenovaných semafor je viditelný na všechna vlákna ve všech procesech. Proto pojmenované semafor slouží k synchronizaci činností procesy a vlákna.  
  
 Můžete vytvořit <xref:System.Threading.Semaphore> objekt, který představuje semafor pojmenované systému pomocí jednoho z konstruktorů, které určuje název.  
  
> [!NOTE]
>  Vzhledem k tomu pojmenované semafory v systému, je možné mít více <xref:System.Threading.Semaphore> objekty, které představují stejný název pro spolupráci. Pokaždé, když volat konstruktor nebo <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> metodu, nové <xref:System.Threading.Semaphore> je vytvořen objekt. Zadání se stejným názvem opakovaně vytvoří více objektů, které představují stejné pojmenované semafor.  
  
 Buďte opatrní při použití pojmenované semafory. Protože jsou v systému, jiný proces, který používá stejný název můžete zadat vaše semafor neočekávaně. Škodlivý kód, spouští ve stejném počítači může použít jako základ útok s cílem odepření služby.  
  
 Použití řízení přístupu k ochraně <xref:System.Threading.Semaphore> objekt, který představuje pojmenované semafor nejlépe pomocí konstruktoru, který určuje <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> objektu. Můžete také použít pomocí zabezpečení řízení přístupu <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> metody, ale ponechá okno na ohrožení zabezpečení mezi časem semafor se vytvoří a čas, který je chráněn. Ochrana semafory pomocí řízení přístupu pomáhá zabránit útoky se zlými úmysly, ale problém kolize názvů neúmyslnému nevyřeší.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Semaphore>  
- <xref:System.Threading.SemaphoreSlim>  
- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
