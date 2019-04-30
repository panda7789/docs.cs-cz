---
title: asynchronousThreadAbort – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08f67ad363d0bd3efcc7a1eeedd1f48d3bae9407
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875703"
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort – pomocník spravovaného ladění (MDA)
`asynchronousThreadAbort` Pomocníka spravovaného ladění (MDA) se aktivuje, když vlákno pokusí zavést asynchronnímu přerušení do jiného vlákna. Synchronní vlákno přeruší neaktivovat `asynchronousThreadAbort` MDA.

## <a name="symptoms"></a>Příznaky
 Dojde k chybě aplikace s neošetřenou <xref:System.Threading.ThreadAbortException> při hlavního vlákna aplikace je přerušeno. Pokud aplikace i nadále provádí, může být horší, než aplikace k chybám, což může způsobit poškození dat další důsledky.

 Má být atomické operace mají byla přerušena pravděpodobně po dokončení částečně, ponechání dat aplikace v nepředvídatelném stavu. A <xref:System.Threading.ThreadAbortException> se dá vygenerovat na zdánlivě náhodných intervalech v provádění kódu, často v místech, ze kterých se neočekává vzniknout výjimky. Kód nemusí být schopna zpracovávat takové výjimky, což v poškozeném stavu.

 Příznaky můžou výrazně lišit kvůli náhodnost přináší problém.

## <a name="cause"></a>Příčina
 Kód v jednom vlákně volána <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodu na zavést přerušení asynchronní vlákno s cílovým vláknem. Přerušení vlákna je asynchronní, protože kód, který provádí volání do <xref:System.Threading.Thread.Abort%2A> běží na jiném vlákně než cílová operaci zrušení udělat. Synchronní vlákno přeruší by neměly způsobit potíže, protože vlákno provádění <xref:System.Threading.Thread.Abort%2A> by mělo mít provedeno pouze na bezpečné kontrolní bod, ve kterém je konzistentní stav aplikace.

 Asynchronní vlákno přeruší představovat problém, protože jsou zpracovávány v nepředvídatelné body v cílové vlákno provádění. Abyste tomu předešli, by kód napsaný pro spuštění na vlákno, které může být přerušeno tímto způsobem potřeba zpracovat <xref:System.Threading.ThreadAbortException> v téměř každý jednotlivý řádek kódu, nezapomeňte vrátit data aplikací do konzistentního stavu. Není reálné očekávat kódu má být zapsán s tímto problémem v paměti nebo napsat kód, který chrání před všechny možné okolnosti.

 Volání nespravovaného kódu a `finally` bloky nebude přerušena asynchronně, ale hned po ukončení z jedné z těchto kategorií.

 Důvodem může být obtížné určit z důvodu náhodnost přináší problém.

## <a name="resolution"></a>Řešení
 Vyhněte se návrh kódu, který vyžaduje použití asynchronního podprocesu přeruší. Existuje několik přístupů vhodnější pro přerušení s cílovým vláknem, které nevyžadují volání <xref:System.Threading.Thread.Abort%2A>. Nejbezpečnější je zavést mechanismus, jako je například běžné vlastnosti, která signalizuje cílové vlákno požádat o přerušení. Cílové vlákno kontroluje signál v určitých bezpečné kontrolní body. Zjistí-li to požádal přerušení, ho můžete vypnout bez výpadku.

## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime
 Toto MDA nemá žádný vliv na CLR. Sestavy pouze data o přerušení asynchronní vlákna.

## <a name="output"></a>Výstup
 MDA sestavy ID vlákna provádění přerušení a ID vlákna, která je cílem přerušení. Nikdy budou stejné vzhledem k tomu, že tento požadavek omezuje na asynchronní přerušení.

## <a name="configuration"></a>Konfigurace

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Příklad
 Aktivace `asynchronousThreadAbort` MDA vyžaduje pouze volání <xref:System.Threading.Thread.Abort%2A> na samostatném vlákně spuštěné. Pokud obsah vlákno spustit funkci, byly sady složitějších operací, které může dojít k přerušení libovolného kdykoli podle abort vezměte v úvahu důsledky.

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

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
