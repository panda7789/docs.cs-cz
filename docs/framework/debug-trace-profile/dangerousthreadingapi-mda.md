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
ms.openlocfilehash: 1bfc3aa2bb7d1819f5f6221154ba1d276e0c202c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149364"
---
# <a name="dangerousthreadingapi-mda"></a>dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
`dangerousThreadingAPI` Pomocníka spravovaného ladění (MDA) se aktivuje při <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> metoda je volána ve vlákně než aktuální vlákno.  
  
## <a name="symptoms"></a>Příznaky  
 Aplikace nereaguje nebo se zablokuje po neomezenou dobu. Systém nebo aplikace, data můžou zůstat v nepředvídatelném stavu dočasně, nebo i po aplikace se ukončila. Některé operace nejsou dokončení podle očekávání.  
  
 Příznaky můžou výrazně lišit kvůli náhodnost přináší problém.  
  
## <a name="cause"></a>příčina  
 Vlákno je pozastaveno asynchronně pomocí jiného vlákna <xref:System.Threading.Thread.Suspend%2A> metody. Neexistuje žádný způsob, jak určit, kdy je bezpečné pozastavit jiným vláknem, jež může být provádí operaci. Pozastavení vlákno může způsobit poškození dat nebo zásadní výstupních podmínek. Vlákno umístit do pozastaveného stavu a nikdy obnovenou pomocí <xref:System.Threading.Thread.Resume%2A> metodu, aplikace může neomezenou dobu zaseknout a případně poškodit data aplikací. Tyto metody jsou označené jako zastaralé.  
  
 Pokud cílové vlákno drží synchronizací primitiv, zůstanou vlastněnou během pozastavení. To může vést k zablokování by měl jiného vlákna, třeba vlákno provádění <xref:System.Threading.Thread.Suspend%2A>, pokus o získání zámku na primitivní vlastnost. V takovém případě problém projevuje jako zablokování.  
  
## <a name="resolution"></a>Rozlišení  
 Vyhněte se návrhům, které vyžadují použití <xref:System.Threading.Thread.Suspend%2A> a <xref:System.Threading.Thread.Resume%2A>. Spolupráce mezi vlákny pomocí synchronizace primitiv <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, nebo C# `lock` příkazu. Pokud je nutné použít tyto metody, snížit časové okno a minimalizovat množství kódu, který se spustí během zobrazení vlákna v pozastaveném stavu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR. Sestavy pouze data o nebezpečné operace vláken.  
  
## <a name="output"></a>Výstup  
 MDA identifikuje nebezpečné vláken metodu, která způsobila jeho aktivaci.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje volání <xref:System.Threading.Thread.Suspend%2A> metodu, která způsobí aktivaci `dangerousThreadingAPI`.  
  
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
 <xref:System.Threading.Thread>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [lock – příkaz](~/docs/csharp/language-reference/keywords/lock-statement.md)
