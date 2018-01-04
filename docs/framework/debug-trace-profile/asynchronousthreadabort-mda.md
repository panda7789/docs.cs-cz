---
title: "asynchronousThreadAbort – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecd99b098a619d4ad132432f4fd163d32598c2ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort – pomocník spravovaného ladění (MDA)
`asynchronousThreadAbort` Pomocník spravovaného ladění (MDA) se aktivuje, když se pokusí vlákna zavést asynchronní přerušení do jiné vlákno. Synchronní vlákno přerušení Neaktivujte `asynchronousThreadAbort` (mda).

## <a name="symptoms"></a>Příznaky
 Aplikace, dojde k chybě s neošetřenou <xref:System.Threading.ThreadAbortException> když byl přerušen hlavní vlákno aplikace. Pokud aplikace provést i nadále, může být zhoršení než aplikace chybám, což může způsobit další poškození dat důsledky.

 Operace, měl by být atomic mít byla přerušena pravděpodobně po dokončení částečné ponechat data aplikací v nepředvídatelném stavu. A <xref:System.Threading.ThreadAbortException> z zdánlivě náhodné body v provádění kódu, často v místech, ze kterých výjimku neočekává se, že jsou vyvolány lze vytvořit. Kód nemusí být schopen zpracování takové výjimky, což je v poškozeném stavu.

 Příznaky může odlišovat kvůli náhodnost vyplývajících tento problém.

## <a name="cause"></a>příčina
 Kód v názvem jedno vlákno <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metoda ve vlákně cíl zavádět přerušení asynchronní vlákno. Zrušení vláken je asynchronní, protože kód, který zpřístupňuje volání <xref:System.Threading.Thread.Abort%2A> běží v jiném podprocesu než cíl operace zrušení. Synchronní vlákno přerušení by nemělo způsobit problém, protože provádí přístup z více vláken <xref:System.Threading.Thread.Abort%2A> by mít provedena, protože pouze bezpečné kontrolního bodu, kde je konzistentní stav aplikace.

 Asynchronní vlákno přerušení představovat problém vzhledem k tomu, že jsou zpracovávány v nepředvídatelným body v cílové vláken provádění. Abyste tomu předešli, kód napsaný ke spuštění na vlákno, které může být tímto způsobem přerušena potřebovat pro zpracování <xref:System.Threading.ThreadAbortException> na téměř každý jednotlivý řádek kódu, aby byl vrátit data aplikací zpět do konzistentního stavu. Není reálné očekávat kódu k zapsání pomocí tohoto problému v paměti nebo napsat kód, který chrání před všechny možné okolnosti.

 Volání nespravovaného kódu a `finally` bloky nebude přerušena asynchronně ale ihned po ukončení z jedné z těchto kategorií.

 Příčinou může být obtížné určit, z důvodu náhodnost vyplývajících tento problém.

## <a name="resolution"></a>Rozlišení
 Vyhněte se návrh kód, který vyžaduje použití asynchronní vlákno přerušení. Existuje několik přístupů vhodnější pro přerušení cíl vlákno, které nevyžadují volání <xref:System.Threading.Thread.Abort%2A>. Nejbezpečnější je zavedení mechanismus, jako jsou běžnou vlastností, která signalizuje vlákno cíl požádat o přerušení. Cíl vlákno kontroluje signál v určitých bezpečné kontrolní body. Pokud je oznámení, že bylo vyzváno přerušení, ho můžete řádné ukončení.

## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime
 Tato MDA nemá žádný vliv na modulu CLR. Pouze sestavy data o přerušení asynchronní vlákno.

## <a name="output"></a>Výstup
 MDA hlásí ID vlákna provádění přerušení a ID vlákna, která je cílem přerušení. Tyto nebude nikdy ve stejné vzhledem k tomu, že toto je omezený na asynchronní přerušení.

## <a name="configuration"></a>Konfigurace

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Příklad
 Aktivace `asynchronousThreadAbort` MDA vyžaduje pouze volání <xref:System.Threading.Thread.Abort%2A> na samostatné spuštěných vláken. Je-li obsah vlákno spuštění funkce byly sadu složitějších operací, které může dojít k přerušení libovolný kdykoli podle přerušení, zvažte důsledky.

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a>Viz také
 <xref:System.Threading.Thread>[Diagnostikování chyb pomocí Pomocníci spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
