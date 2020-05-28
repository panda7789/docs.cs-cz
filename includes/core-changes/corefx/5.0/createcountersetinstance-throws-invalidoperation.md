---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144475"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>Sada CounterSet. provedení operace CreateCounterSetInstance nyní vyvolá chybu InvalidOperationException, pokud již instance existuje.

Počínaje platformou .NET 5,0 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> vyvolá výjimku <xref:System.InvalidOperationException> místo, <xref:System.ArgumentException> Pokud sada čítačů již existuje.

#### <a name="change-description"></a>Popis změny

V .NET Framework a .NET Core 1,0 až 3,1 můžete vytvořit instanci sady čítačů voláním <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> . Nicméně pokud sada čítačů již existuje, metoda vyvolá <xref:System.ArgumentException> výjimku.

V rozhraní .NET 5,0 a novějších verzích, pokud zavoláte <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> a sadu čítačů existují, <xref:System.InvalidOperationException> je vyvolána výjimka.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 5

#### <a name="recommended-action"></a>Doporučená akce

Pokud zachytíte <xref:System.ArgumentException> výjimky v aplikaci při volání <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> , zvažte také zachycení <xref:System.InvalidOperationException> výjimek.

> [!NOTE]
> Nedoporučuje <xref:System.ArgumentException> se zachytávání výjimek.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
