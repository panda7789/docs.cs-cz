---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614574"
---
### <a name="wpf-pointer-based-touch-stack"></a>Dotykové skládání na základě ukazatele WPF

#### <a name="details"></a>Podrobnosti

Tato změna přičítá možnost Povolit volitelnou sadu funkcí WPF Touch/Stylus založenou na WM_POINTER.  Vývojáři, kteří to explicitně nepovolují, by se neměli měnit v chování WPF Touch/Stylus. Aktuální známé problémy s volitelnou WM_POINTERou dotykovou a stylusovou vrstvou:

- Žádná podpora pro psaní rukou v reálném čase.
- I když budou rukopisné a StylusPlugIns – i nadále fungovat, budou zpracovány ve vlákně uživatelského rozhraní, což může vést k špatnému výkonu.
- Změny chování kvůli změnám v povýšení událostí dotykového/stylusu na události myši
- Manipulace se může chovat jinak.
- Přetažením nebudete mít k dispozici odpovídající zpětnou vazbu k dotykovému vstupu.
- To nemá vliv na vstup stylusu.
- Přetažení už nejde iniciovat na událostech dotyku nebo stylusu.
- To může potenciálně zablokovat aplikaci, dokud se nezjistí vstup z myši.
- Místo toho by vývojáři měli zahájit přetahování z událostí myši.

#### <a name="suggestion"></a>Návrh

Vývojáři, kteří chtějí tuto sadu povolit, můžou do souboru App.config aplikace přidat nebo sloučit následující:

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Odebráním tohoto nastavení nebo nastavením hodnoty na hodnotu false dojde k vypnutí tohoto volitelného zásobníku. Všimněte si, že tento zásobník je dostupný jenom pro Windows 10 Creators Update a novější.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4,7         |
| Typ    | Změna cílení |
