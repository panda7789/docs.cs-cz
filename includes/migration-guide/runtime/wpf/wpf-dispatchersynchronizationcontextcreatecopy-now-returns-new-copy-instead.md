---
ms.openlocfilehash: ff4d67a1c821fc96130c4efbd88eb5c56766da06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379587"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>WPF DispatcherSynchronizationContext.CreateCopy nyní vrací novou kopii namísto aktuální instance

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4 <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> vrátí odkaz na aktuální instanci především jako optimalizaci výkonu. V rozhraní .NET Framework 4.5 vrátí novou instanci díky tomu je možné poprvé k závěru, že stejné odkazy znamenají, že spuštěné vlákno je v rámci synchronizace správné.  Není pravděpodobné, že bude mít vliv na kód, který ověří identitu tyto odkazy, ale z důvodu této změny se kód, který volá <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> by měl být testován jako součást migrace na rozhraní .NET Framework 4.5 nebo novější.|
|Doporučení|Mějte na paměti, která <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> nyní vrátí novou <xref:System.Threading.SynchronizationContext?displayProperty=name> objektu. Kód, který používá rovnocennosti odkazy generované tímto způsobem dříve, se ve skutečnosti kontroluje se, zda byla ve správném kontextu, ale nemá po sestavení pro rozhraní .NET Framework 4.5 nebo novější.  Zatímco pravděpodobně nezpůsobí problémy, práv vyplývajících z cesty ovlivněné kódu by vám měly dostatečně k určení, pokud to ale představuje jakýkoli problém.|
|Scope|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
