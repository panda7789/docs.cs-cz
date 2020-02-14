---
title: dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: 4e7e858dfb85eeccbadb23da60d081d1407e89d8
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216675"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
Pokud je metoda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> volána v jiném vlákně, než je aktuální vlákno, je aktivována aplikace `dangerousThreadingAPI` Managed Debugging Assistant (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace nereaguje nebo nereaguje na neomezenou dobu. Data systému nebo aplikací mohou být ponechána v nepředvídatelném stavu dočasně nebo i po vypnutí aplikace. Některé operace nejsou dokončeny podle očekávání.  
  
 Příznaky se můžou výrazně lišit v důsledku náhodnosti podstaty problému.  
  
## <a name="cause"></a>Příčina  
 Vlákno je asynchronně pozastaveno jiným vláknem pomocí metody <xref:System.Threading.Thread.Suspend%2A>. Neexistuje žádný způsob, jak určit, kdy je bezpečné pozastavit jiné vlákno, které může být uprostřed operace. Pozastavení vlákna může mít za následek poškození dat nebo rozdělení invariant. Má-li být vlákno umístěno do pozastaveného stavu a nikdy se neobnovilo pomocí metody <xref:System.Threading.Thread.Resume%2A>, může aplikace zavěsit data aplikace bez omezení a pravděpodobně je poškodit. Tyto metody byly označeny jako zastaralé.  
  
 Pokud jsou prvky synchronizace uloženy cílovým vláknem, zůstanou při pozastavení uchovávány. To může vést k zablokování by mělo jiné vlákno, například vlákno, které provádí <xref:System.Threading.Thread.Suspend%2A>, pokus o získání zámku na primitivním rozhraní. V takové situaci se problém projeví jako zablokování.  
  
## <a name="resolution"></a>Řešení  
 Vyhněte se návrhům, které vyžadují použití <xref:System.Threading.Thread.Suspend%2A> a <xref:System.Threading.Thread.Resume%2A>. Pro spolupráci mezi vlákny použijte prvky synchronizace, například <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>nebo příkaz C# `lock`. Pokud je nutné použít tyto metody, omezte časový interval a minimalizujte množství kódu, který se spustí, když je vlákno v pozastaveném stavu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR. Oznamuje pouze data o nebezpečných operacích vláken.  
  
## <a name="output"></a>Výstup  
 MDA identifikuje nebezpečnou metodu vláken, která způsobila, že je aktivována.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje volání metody <xref:System.Threading.Thread.Suspend%2A>, která způsobuje aktivaci `dangerousThreadingAPI`.  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();   
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
- [lock – příkaz](../../csharp/language-reference/keywords/lock-statement.md)
