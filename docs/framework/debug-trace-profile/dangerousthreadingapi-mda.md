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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d635100c4e8214a7a8659c2d3e4da61825cf243
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966308"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
Pokud je `dangerousThreadingAPI` metodavolánavjinémvlákněnežvaktuálnímvlákně,jeaktivovánapomocníkspravovanéholadění<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace nereaguje nebo nereaguje na neomezenou dobu. Data systému nebo aplikací mohou být ponechána v nepředvídatelném stavu dočasně nebo i po vypnutí aplikace. Některé operace nejsou dokončeny podle očekávání.  
  
 Příznaky se můžou výrazně lišit v důsledku náhodnosti podstaty problému.  
  
## <a name="cause"></a>příčina  
 Vlákno je asynchronně pozastaveno jiným vláknem pomocí <xref:System.Threading.Thread.Suspend%2A> metody. Neexistuje žádný způsob, jak určit, kdy je bezpečné pozastavit jiné vlákno, které může být uprostřed operace. Pozastavení vlákna může mít za následek poškození dat nebo rozdělení invariant. Pokud by vlákno bylo umístěno do pozastaveného stavu a nikdy se neobnovilo pomocí <xref:System.Threading.Thread.Resume%2A> metody, může aplikace zablokovat neomezenou dobu a může poškodit data aplikace. Tyto metody byly označeny jako zastaralé.  
  
 Pokud jsou prvky synchronizace uloženy cílovým vláknem, zůstanou při pozastavení uchovávány. To může vést k zablokování by mělo jiné vlákno, například vlákno provádí <xref:System.Threading.Thread.Suspend%2A>, pokus o získání zámku na primitivním rozhraní. V takové situaci se problém projeví jako zablokování.  
  
## <a name="resolution"></a>Řešení  
 Vyhněte se návrhům, které <xref:System.Threading.Thread.Suspend%2A> vyžadují <xref:System.Threading.Thread.Resume%2A>použití a. Pro spolupráci <xref:System.Threading.Monitor>mezi vlákny použijte prvky synchronizace <xref:System.Threading.Mutex>, jako je, <xref:System.Threading.ReaderWriterLock>, nebo C# `lock` příkaz. Pokud je nutné použít tyto metody, omezte časový interval a minimalizujte množství kódu, který se spustí, když je vlákno v pozastaveném stavu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Tento MDA nemá žádný vliv na CLR. Oznamuje pouze data o nebezpečných operacích vláken.  
  
## <a name="output"></a>Výstup  
 MDA identifikuje nebezpečnou metodu vláken, která způsobila, že je aktivována.  
  
## <a name="configuration"></a>Konfiguraci  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje volání <xref:System.Threading.Thread.Suspend%2A> metody, která způsobuje aktivaci. `dangerousThreadingAPI`  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [lock – příkaz](../../csharp/language-reference/keywords/lock-statement.md)
