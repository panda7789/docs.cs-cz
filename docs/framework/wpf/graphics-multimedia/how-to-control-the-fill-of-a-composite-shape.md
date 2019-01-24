---
title: 'Postupy: Řízení výplně složeného tvaru'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 18261b2f7a71822684707de7c8c6a37793a8a410
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574674"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Postupy: Řízení výplně složeného tvaru
<xref:System.Windows.Media.GeometryGroup.FillRule%2A> Vlastnost <xref:System.Windows.Media.GeometryGroup> nebo <xref:System.Windows.Media.PathGeometry>, určuje "pravidlo" který složeného tvaru používá k určení, zda daný bod je součástí geometrii. Existují dva možné hodnoty pro <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> a <xref:System.Windows.Media.FillRule.Nonzero>. V následujících částech se popisují, jak používat tyto dvě pravidla.  
  
 **EvenOdd:** Toto pravidlo určuje, zda bod v oblasti výplně kreslení ray od tohoto okamžiku do nekonečna vede libovolným směrem a počtu segmentů cesty v rámci daného tvaru protne. Pokud je toto číslo liché, bod nachází uvnitř; Pokud ještě, se bod nachází mimo.  
  
 Například následující XAML vytvoří složeného tvaru, který se skládá z řady instancí soustředných (cíl) s <xref:System.Windows.Media.GeometryGroup.FillRule%2A> nastavena na <xref:System.Windows.Media.FillRule.EvenOdd>.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![Snímek obrazovky: Vlastnost FillRule EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")  
  
 Na výše uvedeném obrázku Všimněte si, že nejsou vyplněné System center a 3. kanál. Je to proto ray z libovolného bodu v některé z těchto dvou okruhů prochází sudý počet segmentů. Viz následující obrázek:  
  
 ![Diagram: Hodnota vlastnosti FillRule EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenodd2.png "FillRuleEvenOdd2")  
  
 **Nenulovou hodnotu:** Toto pravidlo určuje, zda bod v oblasti výplně cesty k vykreslení ray od tohoto okamžiku do nekonečna vede libovolným směrem a poté zkoumá místa, kde segment tvaru protne. Spuštění s počtem nula, přidejte každý čas Segment protne zleva doprava a odečítání každý čas cestu segmentu protne zprava doleva. Po počítání přechody, pokud je výsledek nula pak se bod nachází mimo cestu. V opačném případě se nachází uvnitř.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 Použijeme příklad výše, hodnota <xref:System.Windows.Media.FillRule.Nonzero> pro <xref:System.Windows.Media.GeometryGroup.FillRule%2A> poskytuje díky tomu na následujícím obrázku:  
  
 ![Snímek obrazovky: Hodnota FillRule NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero1.png "FillRuleNonZero1")  
  
 Jak vidíte, jsou vyplněny všechny aktualizační kanály. Toto je vzhledem k tomu, že všechny segmenty jsou spuštěny ve stejném směru a tak, aby ray z libovolného bodu bude mezi jeden nebo více segmentů a součet hodnot přechodech nesmí být roven nule. Například na následující ilustraci red šipky představují směr, ve kterém jsou vykreslovány segmenty a bílé šipka označuje libovolné ray spuštěná z bodu ve vnitřní prstenec. Spuštění s hodnotou nula, pro každý segment protne, je přidat o hodnotu jedna, protože segment protne zleva doprava.  
  
 ![Diagram: Hodnota vlastnosti FillRule rovna NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero2.png "FillRuleNonZero2")  
  
 Abychom lépe chování <xref:System.Windows.Media.FillRule.Nonzero> pravidlo složitější obrazec s segmenty spuštěné v různých pokynů je povinné. Následující kód XAML vytvoří obrazec podobné jako předchozí příklad s tím rozdílem, že je vytvořen s <xref:System.Windows.Media.PathGeometry> nikoli <xref:System.Windows.Media.EllipseGeometry> vytváří čtyři soustředných oblouky spíše plně zavřeny soustředných kruzích.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![Snímek obrazovky: Hodnota vlastnosti FillRule NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero3.png "FillRuleNonZero3")  
  
 Všimněte si, že není vyplněno třetí oblouk v centru. Následující obrázek ukazuje, proč je to. Na obrázku red šipky představují směr, ve kterém jsou vykreslovány segmenty. Dvě šipky bílé představují dva libovolného paprsky, které přesunout ven z bodu v oblasti "nevyplněná". Jak je vidět z obrázku, aby součet hodnot z daného ray přecházení mezi segmenty v cestě je nula. Definované výše součet nula znamená, že bod není součástí Geometrie (není součástí výplně) při sum, která je *není* nula, včetně hodnota záporná, je součástí geometrii.  
  
 ![Diagram: Hodnota vlastnosti FillRule NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero4.png "FillRuleNonZero4")  
  
 **Poznámka:** Pro účely <xref:System.Windows.Media.FillRule>, všechny obrazce se považují za uzavřen. Pokud existuje mezera v segmentu, nakreslete imaginární řádku ho zavřít. V předchozím příkladu jsou malé mezery v kroužky. To směru, očekávat paprsku, který projde mezera poskytnout jiné výsledky pak ray systémem v jiném směru. Níže je zvětšeným ilustraci jednu z těchto mezer a "imaginární segmentu" (segment, který je vykreslen pro účely <xref:System.Windows.Media.FillRule>), která ukončí.  
  
 ![Diagram: Pro FillRule, jsou vždy uzavřen segmenty](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleclosedshapes.png "FillRuleClosedShapes")  
  
## <a name="example"></a>Příklad  
  
## <a name="see-also"></a>Viz také:
- [Vytvoření složeného tvaru](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)
- [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
