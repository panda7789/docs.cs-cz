---
title: dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Dangerousthreadingapi – (MDA), který se aktivuje při volání Thread. Suspend v jiném vlákně, než je aktuální vlákno.
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
ms.openlocfilehash: 9069ccb6f106c83db94f88bc464bc0888d28586c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416002"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
`dangerousThreadingAPI`Pokud <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> je metoda volána v jiném vlákně než v aktuálním vlákně, je aktivována pomocník spravovaného ladění (MDA).  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace nereaguje nebo nereaguje na neomezenou dobu. Data systému nebo aplikací mohou být ponechána v nepředvídatelném stavu dočasně nebo i po vypnutí aplikace. Některé operace nejsou dokončeny podle očekávání.  
  
 Příznaky se můžou výrazně lišit v důsledku náhodnosti podstaty problému.  
  
## <a name="cause"></a>Příčina  
 Vlákno je asynchronně pozastaveno jiným vláknem pomocí <xref:System.Threading.Thread.Suspend%2A> metody. Neexistuje žádný způsob, jak určit, kdy je bezpečné pozastavit jiné vlákno, které může být uprostřed operace. Pozastavení vlákna může mít za následek poškození dat nebo rozdělení invariant. Pokud by vlákno bylo umístěno do pozastaveného stavu a nikdy se neobnovilo pomocí <xref:System.Threading.Thread.Resume%2A> metody, může aplikace zablokovat neomezenou dobu a může poškodit data aplikace. Tyto metody byly označeny jako zastaralé.  
  
 Pokud jsou prvky synchronizace uloženy cílovým vláknem, zůstanou při pozastavení uchovávány. To může vést k zablokování by mělo jiné vlákno, například vlákno provádí <xref:System.Threading.Thread.Suspend%2A> , pokus o získání zámku na primitivním rozhraní. V takové situaci se problém projeví jako zablokování.  
  
## <a name="resolution"></a>Řešení  
 Vyhněte se návrhům, které vyžadují použití <xref:System.Threading.Thread.Suspend%2A> a <xref:System.Threading.Thread.Resume%2A> . Pro spolupráci mezi vlákny použijte prvky synchronizace <xref:System.Threading.Monitor> , jako je, <xref:System.Threading.ReaderWriterLock> , <xref:System.Threading.Mutex> nebo příkaz jazyka C# `lock` . Pokud je nutné použít tyto metody, omezte časový interval a minimalizujte množství kódu, který se spustí, když je vlákno v pozastaveném stavu.  
  
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
 Následující příklad kódu ukazuje volání <xref:System.Threading.Thread.Suspend%2A> metody, která způsobuje aktivaci `dangerousThreadingAPI` .  
  
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
