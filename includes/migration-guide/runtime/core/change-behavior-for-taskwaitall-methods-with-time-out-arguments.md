---
ms.openlocfilehash: 52406f1e4ea4eda417909e52cf6529631cb0ae33
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619963"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>Změna chování pro metody Task. WaitAll s argumenty časového limitu

#### <a name="details"></a>Podrobnosti

<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>chování bylo v souladu s .NET Framework 4.5.In .NET Framework 4, tyto metody se chovají nekonzistentně. Po vypršení časového limitu, pokud před voláním metody byla dokončena nebo zrušena jedna nebo více úloh, metoda vyvolala <xref:System.AggregateException?displayProperty=fullName> výjimku. Po vypršení časového limitu, pokud nebyly dokončeny nebo zrušeny žádné úkoly před voláním metody, ale jedna nebo více úloh zadal tyto stavy po volání metody, metoda vrátila hodnotu false.<br/><br/>V .NET Framework 4,5 Tato přetížení metody nyní vrací hodnotu false, pokud některé úlohy stále běží, když vypršel časový limit, a vyvolávají <xref:System.AggregateException?displayProperty=fullName> výjimku pouze v případě, že vstupní úkol byl zrušen (bez ohledu na to, zda byl dříve nebo po volání metody) a zda stále nejsou spuštěny žádné další úlohy.

#### <a name="suggestion"></a>Návrh

Pokud <xref:System.AggregateException?displayProperty=fullName> byla zachycena jako způsob detekce úlohy, která byla zrušena před <xref:System.Threading.Tasks.Task.WaitAll%2A> vyvoláním volání, měl by tento kód místo toho provádět stejné zjišťování prostřednictvím <xref:System.Threading.Tasks.Task.IsCanceled%2A> vlastnosti (například:. Any (t = &gt; t. uncanceled)), protože .NET Framework 4,6 bude v takovém případě vyvolána pouze v případě, že všechny očekávané úkoly byly dokončeny před časovým limitem.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|
