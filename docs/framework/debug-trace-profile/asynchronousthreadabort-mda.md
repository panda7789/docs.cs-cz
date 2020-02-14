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
ms.openlocfilehash: d0c78e6d52ae4a5b3a24e0bb4278b2e8a1b98751
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217581"
---
# <a name="asynchronousthreadabort-mda"></a>asynchronousThreadAbort – pomocník spravovaného ladění (MDA)
Pokud se vlákno pokusí o zavedení asynchronního přerušení do jiného vlákna, aktivuje se Pomocník s `asynchronousThreadAbort`em spravovaného ladění (MDA). Synchronní přerušení vlákna neaktivují `asynchronousThreadAbort` MDA.

## <a name="symptoms"></a>Příznaky
 Aplikace selže s neošetřenou <xref:System.Threading.ThreadAbortException>, když je hlavní vlákno aplikace přerušeno. Pokud by aplikace pokračovala v provádění, může to být horší než selhání aplikace, což může vést k dalšímu poškození dat.

 Operace, které mají být atomické, byly pravděpodobně přerušeny po částečném dokončení a data aplikace budou ponechána v nepředvídatelném stavu. <xref:System.Threading.ThreadAbortException> lze vygenerovat z zdánlivě náhodných bodů při provádění kódu, často v místech, ze kterých se neočekává, že vzniká výjimka. Kód nemusí být schopen zpracovat takovou výjimku, což vede k poškozenému stavu.

 Příznaky se můžou výrazně lišit v důsledku náhodnosti podstaty problému.

## <a name="cause"></a>Příčina
 Kód v jednom vlákně s názvem <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodou v cílovém vlákně pro zavedení asynchronního přerušení vlákna. Přerušení vlákna je asynchronní, protože kód, který volá <xref:System.Threading.Thread.Abort%2A>, je spuštěn v jiném vlákně než cíl operace Abort. Synchronní přerušení vlákna by neměla způsobovat problém, protože vlákno, které provádí <xref:System.Threading.Thread.Abort%2A>, by mělo být provedeno pouze v bezpečném kontrolním bodu, kde je stav aplikace konzistentní.

 Asynchronní vlákno přerušuje problém, protože jsou zpracovávány v nepředvídatelných bodech v provádění cílového vlákna. Aby k tomu nedocházelo, kód napsaný pro spuštění ve vlákně, který může být přerušen tímto způsobem, by musel zpracovat <xref:System.Threading.ThreadAbortException> v téměř každém řádku kódu a přitom zajistit, aby se data aplikace vrátila do konzistentního stavu. Nejedná se o realistickou situaci, kdy očekáváte, že se kód bude zapisovat s tímto problémem, nebo jestli chcete napsat kód, který chrání před všemi možnými okolnostmi.

 Volání do nespravovaného kódu a `finally` bloky nebudou asynchronně přerušeny, ale okamžitě po ukončení jedné z těchto kategorií.

 Příčina může být obtížné určit z důvodu náhodnosti podstaty problému.

## <a name="resolution"></a>Řešení
 Vyhněte se návrhu kódu, který vyžaduje použití asynchronního přerušení vlákna. Existuje několik přístupů, které jsou vhodnější pro přerušení cílového vlákna, které nevyžadují volání <xref:System.Threading.Thread.Abort%2A>. Nejbezpečnější je zavedení mechanismu, jako je například společná vlastnost, která signalizuje cílovému vláknu, aby požadoval přerušení. Cílové vlákno kontroluje signál u určitých bezpečných kontrolních bodů. Pokud si vyžádá, že bylo vyžadováno přerušení, může se řádně vypnout.

## <a name="effect-on-the-runtime"></a>Vliv na modul runtime
 Tento MDA nemá žádný vliv na CLR. Pouze hlásí data o přerušení asynchronního vlákna.

## <a name="output"></a>Výstup
 MDA hlásí ID vlákna, které provádí přerušení, a ID vlákna, které je cílem přerušení. Nebudou nikdy stejné, protože to je omezeno na asynchronní přerušení.

## <a name="configuration"></a>Konfigurace

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a>Příklad
 Aktivace `asynchronousThreadAbort` MDA vyžaduje pouze volání <xref:System.Threading.Thread.Abort%2A> na samostatném běžícím vlákně. Zvažte důsledky, pokud je obsah funkce spuštění vlákna množinou složitějších operací, které mohou být přerušeny v libovolném okamžiku přerušení.

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

- <xref:System.Threading.Thread>
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
