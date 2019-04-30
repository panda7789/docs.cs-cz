---
ms.openlocfilehash: 8e75c60126abc2670053eba2c01e1fb36d1a93e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762552"
---
### <a name="wpf-appdomain-shutdown-handling-may-now-call-dispatcherinvoke-in-cleanup-of-weak-events"></a>Zpracování ukončení domény aplikace WPF může nyní volat Dispatcher.Invoke v vyčištění slabé událostí

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.1 a starší verze WPF potenciálně vytváří <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> na finalizační podproces .NET během vypínání domény aplikace.  Byl opraven v rozhraní .NET Framework 4.7.2 a novějších verzích tím, že vyčištění slabé události s ohledem na vlákno.  Z toho důvodu může volat WPF <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> dokončete proces vyčištění. V některých aplikacích tato změna finalizační metodu časování potenciálně způsobit výjimky během AppDomain nebo zpracovat vypnutí.  To je obvykle vidět v aplikacích, které nevypínejte správně dispečerů běžící na pracovních vláken před procesu nebo ukončení domény aplikace.  Tyto aplikace byste měli věnovat pozornost ke správě životnosti dispečerů.|
|Doporučení|Vývojáři v rozhraní .NET Framework 4.7.2 a novějších verzích, můžete zakázat tuto opravu mohla pomoci zmírnění (ale ne eliminovat) problémy načasování, které mohou nastat z důvodu změny vyčištění. Zakázat změnu v hodnotě vyčištění, použijte následující AppContext příznak.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotInvokeInWeakEventTableShutdownListener=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7.2|
|Type|Změna cílení|
