---
title: 'Postupy: Řízení výplně složeného tvaru'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 89f69d392e8838af99538c759a2f06453e1bcd60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855910"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Postupy: Řízení výplně složeného tvaru

<xref:System.Windows.Media.GeometryGroup.FillRule%2A> Vlastnost nebo,<xref:System.Windows.Media.PathGeometry>určuje "pravidlo", které složený tvar používá k určení, zda je daný bod součástí geometrie. <xref:System.Windows.Media.GeometryGroup> Existují dvě možné hodnoty pro <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> a <xref:System.Windows.Media.FillRule.Nonzero>. Následující části popisují způsob použití těchto dvou pravidel.

**EvenOdd** Toto pravidlo určuje, jestli je bod v oblasti Fill, tak, že z něj sekreslíte od tohoto bodu do nekonečna v jakémkoli směru a napočítáte počet segmentů cesty v rámci daného tvaru, které daný paprskový protíná. Pokud je toto číslo liché, je bod uvnitř; Pokud je tento bod i mimo to, je tento bod mimo.

Například XAML níže vytvoří složený tvar, který se skládá z řady soustředných prstenců (cíle) s <xref:System.Windows.Media.GeometryGroup.FillRule%2A> nastavením na. <xref:System.Windows.Media.FillRule.EvenOdd>

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]

Následující ilustrace znázorňuje tvar vytvořený v předchozím příkladu.

![Kruh, který sestavil s soustřednými prstenci řady s střídavými barvami.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-property.png)

Na předchozím obrázku si všimněte, že se nesestavil střed a třetí prstenec. Důvodem je to, že paprsk nakreslený z libovolného bodu v jednom z těchto dvou kroužků projde sudým počtem segmentů. Podívejte se na následující obrázek:

![Diagram znázorňující paprsky EvenOdd vykreslené v kruhu](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-rays.png)

**Nenulovou** Toto pravidlo určuje, jestli je bod v oblasti výplně cesty, tak, že z něj nakreslíte prostor od tohoto bodu do nekonečna v jakémkoli směru a pak prozkoumáte místa, kde segment tvaru protíná ray. Počínaje nulovým počtem přidejte jednu pokaždé, když segment přejíždí z pole od zleva doprava, a odečte jeden z nich pokaždé, když segment cesty přechází z směru zprava doleva. Pokud je výsledek nula, je po počítání překročení bod mimo cestu. V opačném případě je uvnitř.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]

V předchozím příkladu hodnota <xref:System.Windows.Media.FillRule.Nonzero> pro <xref:System.Windows.Media.GeometryGroup.FillRule%2A> poskytuje následující ilustrace jako výsledek:

![Kruh, který sestavil s soustřednými prstenci řady, vyplněný stejnou barvou.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-nonzero.png)

Jak vidíte, všechny prstence jsou vyplněny. Důvodem je to, že všechny segmenty běží ve stejném směru, takže v jednom z nich se bude přecházet z jednoho nebo více segmentů a součet křížení se nerovná nule. Na následujícím obrázku například červené šipky představují směr vykreslování segmentů a bílá šipka představuje libovolný Ray běžící od bodu v nejvnitřnějším prstenci. Počínaje hodnotou nula se pro každý segment, který je paprskový, přidá hodnota jednoho, protože segment přechází z levého na pravé.

![Diagram znázorňující hodnotu vlastnosti FillRule, která se rovná nenule](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-equal-nonzero.png)

Aby lépe ukázal chování <xref:System.Windows.Media.FillRule.Nonzero> pravidla, složitější tvar se segmenty, které běží v různých směrech, je povinná. Níže uvedený kód XAML vytvoří podobný tvar jako předchozí příklad s tím rozdílem, že je vytvořen pomocí <xref:System.Windows.Media.PathGeometry> a místo toho <xref:System.Windows.Media.EllipseGeometry> vytvoří čtyři soustředné oblouky namísto pak plně uzavřené soustředné kroužky.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]

Následující ilustrace znázorňuje tvar vytvořený v předchozím příkladu.

![Kruh, který sestavil s soustřednými prstenci řady s střídajícími se barvami, které třetí oblouk nevyplní.](./media/how-to-control-the-fill-of-a-composite-shape/pathgeometry-concentric-arcs.png)

Všimněte si, že třetí oblouk ze středu není vyplněn. Na následujícím obrázku vidíte, proč je to. Na ilustraci červené šipky představují směr vykreslování segmentů. Dvě bílé šipky znázorňují dva libovolné paprsky, které přecházejí z bodu v oblasti "nevyplněné". Jak je vidět na ilustraci, součet hodnot z daného paprsku po segmentech v cestě je nula. Jak je definováno výše, součet nuly znamená, že bod není součástí geometrie (není součástí výplně), zatímco součet, který *není nula,* včetně záporné hodnoty, je součástí geometrie.

![Diagram znázorňující libovolné paprsky protínající segmenty](./media/how-to-control-the-fill-of-a-composite-shape/arbitrary-ray-cross-segment.png)

> [!NOTE]
> Pro účely <xref:System.Windows.Media.FillRule>se všechny tvary považují za uzavřené. V případě, že je v segmentu mezera, nakreslete imaginární čáru, aby se zavřela. V předchozím příkladu jsou k dispozici malé mezery v prstencích. V takovém případě může být očekáván prostor, který projde mezerou, aby pomohly jiný výsledek a pak bude pracovat v jiném směru. Níže je zvětšená ilustrace jednoho z těchto mezer a "imaginární segment" (segment, který je vykreslen pro účely použití <xref:System.Windows.Media.FillRule>), který ho zavírá.

![Diagram znázorňující FillRule segmenty, které jsou vždy uzavřeny.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-closed-segments.png)

## <a name="example"></a>Příklad

## <a name="see-also"></a>Viz také:

- [Vytvoření složeného tvaru](how-to-create-a-composite-shape.md)
- [Přehled geometrie](geometry-overview.md)
