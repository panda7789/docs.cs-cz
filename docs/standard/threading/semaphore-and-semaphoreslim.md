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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127589"
---
# <a name="semaphore-and-semaphoreslim"></a>Semafor a SemaphoreSlim
Třída <xref:System.Threading.Semaphore?displayProperty=nameWithType> představuje pojmenovaný (systémové) nebo místní semafor. Je to tenké Obálka kolem objektu semaforu Win32. Semafory Win32 počítají semafory, které je možné použít k řízení přístupu k fondu prostředků.  
  
 Třída <xref:System.Threading.SemaphoreSlim> představuje lehký a rychlý semafor, který lze použít pro čekání v rámci jednoho procesu, pokud se očekává, že časy čekání budou velmi krátké. <xref:System.Threading.SemaphoreSlim> spoléhá co nejvíc na primitivy synchronizace poskytované modulem CLR (Common Language Runtime). Nicméně také poskytuje laxně vytvářená inicializovaných obslužných rutin na bázi jádra, které jsou potřeba pro podporu čekání na více semaforů. <xref:System.Threading.SemaphoreSlim> také podporuje použití tokenů zrušení, ale nepodporuje pojmenované semafory nebo použití popisovače čekání pro synchronizaci.  
  
## <a name="managing-a-limited-resource"></a>Správa omezeného prostředku  
 Vlákna vstupují semafor voláním metody <xref:System.Threading.WaitHandle.WaitOne%2A>, která je zděděna z třídy <xref:System.Threading.WaitHandle>, v případě <xref:System.Threading.Semaphore?displayProperty=nameWithType>ho objektu nebo metody <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> v případě objektu <xref:System.Threading.SemaphoreSlim>. Když se volání vrátí, bude snížen počet semaforu. V případě, že je položka žádosti o vlákno a počet rovna nule, vlákno blokuje. Jak vlákna vydávají semafor voláním metody <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType>, jsou povoleny blokované vlákna. Neexistuje žádné zaručené pořadí, například First-in, First-out (FIFO) nebo Last-in a First-out (LIFO) pro zablokované vlákno pro vstup do semaforu.  
  
 Vlákno může vstup semaforu víckrát zadat voláním metody <xref:System.Threading.WaitHandle.WaitOne%2A> objektu <xref:System.Threading.Semaphore?displayProperty=nameWithType> nebo opakovaného <xref:System.Threading.SemaphoreSlim.Wait%2A> metody objektu <xref:System.Threading.SemaphoreSlim>. Chcete-li uvolnit semafor, vlákno může buď volat <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> přetížení metody, nebo volat přetížení metody <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> nebo <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> a určit počet položek, které budou uvolněny.  
  
### <a name="semaphores-and-thread-identity"></a>Semafory a identita vlákna  
 Tyto dva typy semaforu vynutily identitu vlákna při volání metody <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.SemaphoreSlim.Wait%2A>, <xref:System.Threading.Semaphore.Release%2A>a <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType>. Například běžný scénář použití pro semafory zahrnuje vlákno producenta a uživatelské vlákno, přičemž jedno vlákno vždy zvyšuje počet semaforu a druhý vždy snižuje.  
  
 Je zodpovědností programátora, aby bylo zajištěno, že vlákno neuvolní semafor příliš mnohokrát. Předpokládejme například, že semafor má maximální počet dvou a že vlákno a a vlákno B zadávají semafor. Pokud chyba programátora v vlákně B způsobí, že by volání `Release` dvakrát, obě volání budou úspěšná. Počet v semaforu je plný a když vlákno A nakonec volá `Release`, je vyvolána <xref:System.Threading.SemaphoreFullException>.  
  
## <a name="named-semaphores"></a>Pojmenované semafory  
 Operační systém Windows umožňuje semaforům mít názvy. Pojmenovaný semafor je napříč systémem. To znamená, že jakmile je pojmenovaný semafor vytvořen, je viditelný pro všechna vlákna ve všech procesech. Pojmenovaný semafor se proto dá použít k synchronizaci aktivit procesů i vláken.  
  
 Můžete vytvořit objekt <xref:System.Threading.Semaphore>, který představuje pojmenovaný systémový semafor pomocí jednoho z konstruktorů, které určují název.  
  
> [!NOTE]
> Vzhledem k tomu, že pojmenované semafory jsou napříč systémem, je možné mít více <xref:System.Threading.Semaphore> objektů, které představují stejný pojmenovaný semafor. Pokaždé, když zavoláte konstruktor nebo metodu <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType>, vytvoří se nový objekt <xref:System.Threading.Semaphore>. Zadáním stejného názvu opakovaně vytvoříte více objektů, které reprezentují stejný pojmenovaný semafor.  
  
 Buďte opatrní při použití pojmenovaných semaforů. Vzhledem k tomu, že se jedná o systém, může váš semafor neočekávaně zadat jiný proces, který používá stejný název. Škodlivý kód spuštěný ve stejném počítači může použít tento způsob útoku DOS (Denial of Service).  
  
 Použijte zabezpečení řízení přístupu k ochraně objektu <xref:System.Threading.Semaphore>, který představuje pojmenovaný semafor, nejlépe pomocí konstruktoru, který určuje objekt <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType>. Můžete také použít zabezpečení řízení přístupu pomocí metody <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType>, ale toto nastavení zachová okno chyby zabezpečení mezi časem vytvoření semaforu a časem, který je chráněn. Ochrana semaforů pomocí zabezpečení řízení přístupu pomáhá zabránit škodlivým útokům, ale neřeší problém kolizí neúmyslného názvu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Semaphore>
- <xref:System.Threading.SemaphoreSlim>
- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
