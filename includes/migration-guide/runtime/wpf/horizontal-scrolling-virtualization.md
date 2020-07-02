---
ms.openlocfilehash: 14585b6de3ce02884f8be789930fc8610f73ba7d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621112"
---
### <a name="horizontal-scrolling-and-virtualization"></a>Horizontální posouvání a virtualizace

#### <a name="details"></a>Podrobnosti

Tato změna se vztahuje na objekt <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> , který má vlastní virtualizaci ve směru kolmosti na hlavní směr posouvání (hlavní příklad je <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> s EnableColumnVirtualization = &quot; true &quot; ).  Výsledek některých operací horizontálního posouvání se změnil, aby vznikly intuitivnější a více podobných výsledkům srovnatelných vertikálních operací.<p/>Operace zahrnují &quot; posuňte se sem &quot; a &quot; pravé hrany &quot; , pokud chcete použít názvy z nabídky, které získáte kliknutím pravým tlačítkem myši na vodorovný posuvník.  Obě tyto výpočetní operace mají posun a volání <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)> .<p/>Po posunu na nový posun se může stát, že se vyvolala &quot; &quot; hodnota tohoto nebo &quot; pravého okraje, &quot; protože nově nevirtualizovaný obsah změnil hodnotu <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> .<p/>Před .NET Framework 4.6.2 operace Scroll jednoduše používá posun kandidáta, i když nemusí být &quot; zde &quot; nebo na &quot; pravém okraji &quot; .  Výsledkem je, že se jedná o efekty &quot; &quot; , jako je skákající posunutí posuvníku, nejlépe znázorněné v příkladu. Předpokládejme, že a <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> má ExtentWidth = 1000 a Width = 200.  Posun k &quot; pravé hraně &quot; používá kandidáta na posun 1000-200 = 800.  Při posouvání na tento posun jsou nové sloupce devirtualizované; Řekněme, že jsou moc velké, takže <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> změny se 2000.  Posuvník končí na HorizontalOffset = 800 a palec se &quot; &quot; vrátí k blízkosti středu scrollbar v 800/2000 = 40%.<p/>Změnou je přepočítat nový posun kandidáta, pokud dojde k této situaci, a akci opakujte. (To znamená, jak svislé posouvání funguje.) <p/>Tato změna vytvoří pro koncového uživatele více předvídatelného a intuitivního prostředí, ale může také ovlivnit jakoukoli aplikaci, která závisí na přesné hodnotě <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=fullName> po vodorovném posuvníku, ať už je vyvolána koncovým uživatelem nebo explicitním voláním metody <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)> .

#### <a name="suggestion"></a>Návrh

Aplikace, která používá předpovězenou hodnotu, <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=fullName> by měla být změněna tak, aby získala skutečnou hodnotu (a hodnotu <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> ) po jakémkoli vodorovném posuvníku, který se může změnit <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=fullName> z důvodu zrušení virtualizace.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|
