---
ms.openlocfilehash: 3463b6c45952aab0023e40921739e84eb51ca001
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803683"
---
### <a name="wpf-pointer-based-touch-stack"></a>WPF Touch založené na ukazatel zásobníku

|   |   |
|---|---|
|Podrobnosti|Tato změna přidává možnost povolit volitelné WM_POINTER založený na zásobníku touch/stylus WPF.  Vývojáři, kteří nepovolujte explicitně to měli vidět žádné změny v chování touch/stylus WPF. Aktuální známé problémy s volitelné WM_POINTER na základě touch/stylus zásobníku:<ul><li>Žádná podpora pro rukopis v reálném čase.</li><li>Při rukopis a stylusplugins – budou i nadále fungovat, zpracuje na vlákně uživatelského rozhraní, což může vést k nižšímu výkonu.</li><li>Chování změny z důvodu změn v podpoře z dotykového ovládání/stylus událostí na události myši</li><li>Manipulace s může chovat jinak</li><li>Přetažení nezobrazí odpovídající zpětné vazby pro dotykové ovládání</li><li>To nemá vliv na vstup pomocí pera</li><li>Přetažení nepůjdou už pro dotykové ovládání/stylus události</li><li>Aplikace to můžete zablokování potenciálně, dokud je zjištěna vstup z myši.</li><li>Vývojáři by místo toho zahájit přetáhněte a vyřadit z události myši.</li></ul>|
|Doporučení|Vývojáři, kteří si přejete povolit tento zásobník můžete přidat/merge následujícího souboru App.config jejich aplikace:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>To odebírá nebo nastavením této hodnoty na false se vypne této volitelné zásobníku. Všimněte si, že tento zásobník je dostupná jenom ve Windows 10 Creators Update a vyšší.|
|Rozsah|Edge|
|Version|4.7|
|Type|Změna cílení|
