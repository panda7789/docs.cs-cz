---
ms.openlocfilehash: 2cd107dc92fd0fae89717c38840ce7ea44f3ac9a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233947"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>Změna primárního klíče při zobrazování dat ADO v případě záznamů Master/Detail v WPF

|   |   |
|---|---|
|Podrobnosti|Předpokládejme, že máte kolekci ADO položky typu <code>Order</code>, s relation s názvem &quot;OrderDetails&quot; týkající se kolekce položek typu <code>Detail</code> přes primární klíč &quot;OrderID&quot;. V aplikaci WPF může vytvoření vazby ovládacího prvku seznam v podrobnostech uvedeném pořadí:<pre><code class="lang-xml">&lt;ListBox ItemsSource=&quot;{Binding Path=OrderDetails}&quot; &gt;&#13;&#10;</code></pre>kde je DataContext <code>Order</code>. WPF získá hodnotu <code>OrderDetails</code> vlastnost – shromažďování D všech <code>Detail</code> položky, jejichž <code>OrderID</code> odpovídá <code>OrderID</code> hlavní položky. Změna chování nastane při změně primárního klíče <code>OrderID</code> hlavní položky. ADO automaticky změní <code>OrderID</code> každé příslušné záznamy v kolekci podrobností (konkrétně těm, které jsou zkopírovány do kolekce D).  Ale co se stane D?<ul><li>Staré chování:   Shromažďování D je zrušeno.   Hlavní položky nemá <em>není</em> vyvolat oznámení o změně pro vlastnost <code>OrderDetails</code>.  Objekt ListBox i nadále používat shromažďování D, která je teď prázdný.</li><li>Nové chování:  Shromažďování D je beze změny.   Každá z jeho položek vyvolá oznámení o změně pro <code>OrderID</code> vlastnost.  Objekt ListBox dál používat shromažďování D a zobrazí podrobnosti o s novými <code>OrderID</code>.</li></ul>WPF implementuje nové chování tak, že vytvoříte kolekci D jiným způsobem: zavoláním metody ADO <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> s <code>followParent</code> argument nastaven na <code>true</code>.|
|Doporučení|Aplikace získá pomocí následující přepínač AppContext nové chování.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;&#13;&#10;</code></pre>Výchozí hodnota přepínače <code>true</code> (staré chování) pro aplikace, které cílí na .NET 4.7.1 nebo dolů a <code>false</code> (nové chování) pro aplikace, které cílí na .NET 4.7.2 nebo vyšší.|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Type|Změna cílení|
