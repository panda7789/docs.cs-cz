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
ms.openlocfilehash: b9f7c122ac8acf34f740aca5f0fafc162edcea82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127589"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor a SemaphoreSlim
Třída <xref:System.Threading.Semaphore?displayProperty=nameWithType> představuje pojmenovaný (systemwide) nebo místní semafor. Jedná se o tenký obal kolem objektu semaforu Win32. Semafory Win32 počítají semafory, které lze použít k řízení přístupu k fondu prostředků.  
  
 Třída <xref:System.Threading.SemaphoreSlim> představuje lehký, rychlý semafor, který lze použít pro čekání v rámci jednoho procesu, kdy se očekává, že čekací doby budou velmi krátké. <xref:System.Threading.SemaphoreSlim>závisí co nejvíce na synchronizaci primitiv poskytované modulu CLR (COMMON Language runtime). Poskytuje však také líně inicializované popisovače čekání založené na jádru podle potřeby pro podporu čekání na více semaforů. <xref:System.Threading.SemaphoreSlim>také podporuje použití tokenů zrušení, ale nepodporuje pojmenované semafory nebo použití popisovače čekání pro synchronizaci.  
  
## <a name="managing-a-limited-resource"></a>Správa omezeného zdroje  
 Vlákna zadejte semafor <xref:System.Threading.WaitHandle.WaitOne%2A> voláním metody, která <xref:System.Threading.WaitHandle> je zděděna <xref:System.Threading.Semaphore?displayProperty=nameWithType> z třídy, v případě objektu <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> nebo metody nebo v <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> případě objektu. <xref:System.Threading.SemaphoreSlim> Když volání vrátí, počet na semafor uschlovaný. Když vlákno požaduje zadání a počet je nula, vlákno blokuje. Jako vlákna uvolnit semafor <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> voláním nebo <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metoda, blokované vlákna mohou vstoupit. Neexistuje žádné zaručené pořadí, jako je například první vstup, první ven (FIFO) nebo poslední dovnitř, první ven (LIFO), pro blokované vlákna pro vstup do semaforu.  
  
 Vlákno může zadat semafor vícekrát <xref:System.Threading.Semaphore?displayProperty=nameWithType> voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metody objektu <xref:System.Threading.SemaphoreSlim> nebo <xref:System.Threading.SemaphoreSlim.Wait%2A> metody objektu opakovaně. Chcete-li uvolnit semafor, podproces <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> může buď volat přetížení metody nebo <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> stejný počet opakování, nebo volat přetížení metody nebo a zadat počet položek, které mají být uvolněny.  
  
### <a name="semaphores-and-thread-identity"></a>Semafory a identita vlákna  
 Dva typy semaforu nevynucují identitu <xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.SemaphoreSlim.Wait%2A>vlákna při volání metod , <xref:System.Threading.Semaphore.Release%2A>, a <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> metod. Například běžný scénář použití pro semafory zahrnuje vlákno výrobce a spotřebitelské vlákno, přičemž jedno vlákno vždy zintáží počet semaforů a druhé vždy snižuje jeho snížení.  
  
 Je odpovědností programátora zajistit, aby vlákno neuvolní semafor příliš mnohokrát. Předpokládejme například, že semafor má maximální počet dvou a že vlákno A a vlákno B vstupují do semaforu. Pokud chyba programování ve vlákně `Release` B způsobí, že volání dvakrát, obě volání úspěšné. Počet na semafor je plný a když vlákno `Release`A <xref:System.Threading.SemaphoreFullException> nakonec volá , je vyvolána.  
  
## <a name="named-semaphores"></a>Pojmenované semafory  
 Operační systém Windows umožňuje semafory mít názvy. Pojmenovaný semafor je celý systém. To znamená, že po vytvoření pojmenovanésem semaforu je viditelný pro všechna vlákna ve všech procesech. Pojmenovaný semafor lze tedy použít k synchronizaci aktivit procesů i vláken.  
  
 Můžete vytvořit <xref:System.Threading.Semaphore> objekt, který představuje pojmenovaný systém ový semafor pomocí jednoho z konstruktorů, který určuje název.  
  
> [!NOTE]
> Vzhledem k tomu, že pojmenované semafory <xref:System.Threading.Semaphore> jsou celého systému, je možné mít více objektů, které představují stejný pojmenovaný semafor. Pokaždé, když voláte konstruktor nebo <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> <xref:System.Threading.Semaphore> metodu, je vytvořen nový objekt. Zadáním stejného názvu opakovaně vytvoří více objektů, které představují stejný pojmenovaný semafor.  
  
 Při použití pojmenovaných semaforů buďte opatrní. Vzhledem k tomu, že jsou celého systému, jiný proces, který používá stejný název můžete zadat semafor neočekávaně. Škodlivý kód spuštěný ve stejném počítači by jej mohl použít jako základ útoku typu denial of service.  
  
 Zabezpečení řízení přístupu <xref:System.Threading.Semaphore> slouží k ochraně objektu, který představuje pojmenovaný semafor, nejlépe pomocí konstruktoru, <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> který určuje objekt. Můžete také použít zabezpečení řízení <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> přístupu pomocí metody, ale to ponechává okno chyby mezi čassem semafor je vytvořen a čas je chráněn. Ochrana semaforů se zabezpečením řízení přístupu pomáhá zabránit škodlivým útokům, ale neřeší problém neúmyslných kolizí názvů.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Semaphore>
- <xref:System.Threading.SemaphoreSlim>
- [Objekty a prvky zřetězení](../../../docs/standard/threading/threading-objects-and-features.md)
