---
ms.openlocfilehash: fc6066fd0b23d299158114cb397934041b99ba47
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620097"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>WPF DispatcherSynchronizationContext. CreateCopy nyní vrátí novou kopii místo aktuální instance.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4 <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> vrátil odkaz na aktuální instanci, hlavně jako optimalizaci výkonu. V .NET Framework 4,5 vrátí novou instanci, která umožňuje, aby bylo možné poprvé uzavřít tyto stejné odkazy znamenají, že spuštěné vlákno je ve správném kontextu synchronizace.  Je pravděpodobné, že kód, který kontroluje identitu těchto odkazů, bude ovlivněn, ale kvůli změně by měl být kód, který volá, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> testován jako součást migrace na .NET Framework 4,5 nebo novější.

#### <a name="suggestion"></a>Návrh

Počítejte s tím, že <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> nyní vrátí nový <xref:System.Threading.SynchronizationContext?displayProperty=fullName> objekt. Dříve kód, který použil rovnocennost odkazů vygenerovaný tímto způsobem, nebyl ve skutečnosti zkontrolován, zda byl ve správném kontextu, ale v případě, že je sestaven proti .NET Framework 4,5 nebo novějším.  I když by nedošlo k potížím, by mělo být vhodné, aby při uplatnění ovlivněných cest kódu bylo možné zjistit, zda se jedná o problém.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
