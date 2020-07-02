---
ms.openlocfilehash: 8b804d23247b95381f3ff83bc12c32215a420fb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614612"
---
### <a name="wpf-appdomain-shutdown-handling-may-now-call-dispatcherinvoke-in-cleanup-of-weak-events"></a>Zpracování vypnutí aplikace WPF AppDomain teď může volat dispečera. Invoke při čištění slabých událostí.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.7.1 a starších verzích WPF potenciálně <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> při vypnutí domény AppDomain vytvoří v vlákně finalizační metody rozhraní .NET.  Tato verze byla opravena v .NET Framework 4.7.2 a novějších verzích tím, že provádí vyčištění slabých událostí pracujících s vlákny.  Z tohoto důvodu může WPF volat <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> k dokončení procesu čištění. V některých aplikacích Tato změna v finalizaci časování může potenciálně způsobit výjimky během procesu AppDomain nebo vypnutí procesu.  Tato operace se obecně zobrazuje v aplikacích, které nespustily správně pracovní vlákna spuštěné v pracovních vláknech před vypnutím nebo ukončováním domény aplikace.  Takové aplikace by se měly postarat o správné řízení životnosti expedičních zásilek.

#### <a name="suggestion"></a>Návrh

V .NET Framework 4.7.2 a novějších verzích můžou vývojáři tuto opravu zakázat, aby bylo možné zmírnit (ale ne eliminovat) problémy časování, ke kterým může dojít z důvodu změny vyčištění. Pokud chcete zakázat změnu v čištění, použijte následující příznak AppContext.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotInvokeInWeakEventTableShutdownListener=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.2       |
| Typ    | Změna cílení |
