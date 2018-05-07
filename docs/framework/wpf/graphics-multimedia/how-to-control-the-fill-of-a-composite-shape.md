---
title: 'Postupy: Řízení výplně složeného tvaru'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: a9a17434f11f432f6446e09bd853ed0d2f23fbe8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Postupy: Řízení výplně složeného tvaru
<xref:System.Windows.Media.GeometryGroup.FillRule%2A> Vlastnost <xref:System.Windows.Media.GeometryGroup> nebo <xref:System.Windows.Media.PathGeometry>, určuje "pravidlo" používaný k určení, zda je k danému bodu součástí geometrie kompozitních tvaru. Existují dvě možné hodnoty pro <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> a <xref:System.Windows.Media.FillRule.Nonzero>. V následujících částech se popisují, jak používat tyto dvě pravidla.  
  
 **Hodnotou EvenOdd:** toto pravidlo určuje, zda bod je v oblasti výplně kreslení paprsek do nekonečna vede libovolným směrem od tohoto okamžiku a určovat počet segmentů cesty v rámci daného tvaru paprsek protne. Pokud je toto číslo liché, bod je uvnitř; Pokud i, se bod nachází mimo.  
  
 Například následující XAML vytvoří kompozitních tvaru skládá z řady instancí soustředných (cíl) s <xref:System.Windows.Media.GeometryGroup.FillRule%2A> nastavena na <xref:System.Windows.Media.FillRule.EvenOdd>.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![Snímek obrazovky: Vlastnost FillRule EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")  
  
 Ve výše uvedeném obrázku Všimněte si, že nejsou plná center a 3. prstenec. To je proto paprsek čerpají z libovolného bodu v rámci některý z těchto dvou okruhů projdou sudý počet segmentů. Viz obrázek níže:  
  
 ![Diagram: Hodnota vlastnosti FillRule EvenOdd](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleevenodd2.png "FillRuleEvenOdd2")  
  
 **NonZero:** toto pravidlo určuje, zda bod je v oblasti výplně cesty kreslení paprsek do nekonečna vede libovolným směrem od tohoto okamžiku a poté zkoumá místa, kde tento paprsek protne segment tvaru. Počínaje počet nula, přidejte po jedné čas paprsek protne Segment zleva doprava a jeden každý odečtena čas cestu tento paprsek protne segment zprava doleva. Po počítání provozovaných, pokud je výsledek nula. pak se bod nachází mimo cestu. Jinak je uvnitř.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 Použití v příkladu výše, hodnota <xref:System.Windows.Media.FillRule.Nonzero> pro <xref:System.Windows.Media.GeometryGroup.FillRule%2A> v důsledku dává na následujícím obrázku:  
  
 ![Snímek obrazovky: FillRule hodnotou NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero1.png "FillRuleNonZero1")  
  
 Jak vidíte, jsou vyplněny všechny kroužky. Toto je vzhledem k tomu, že všechny segmenty běží ve stejném směru a tak, aby paprsek čerpají z libovolného bodu bude křížové jeden nebo více segmenty a součet provozovaných nebude rovné nule. Například na následující ilustraci red šipky představují směr, ve kterém jsou vykreslovány segmentů a bílé šipku představuje libovolné ray spuštěna z bodu v nejvnitřnější prstenec. Počínaje hodnota nula, pro každý segment, který paprsek protne, je přidat na hodnotu jedna, protože tento paprsek protne segment zleva doprava.  
  
 ![Diagram: Hodnota vlastnosti FillRule rovna NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero2.png "FillRuleNonZero2")  
  
 K předvedení lépe chování <xref:System.Windows.Media.FillRule.Nonzero> je požadováno pravidlo složitější obrazce s segmenty spuštěné v různých pokynů. Následující kód XAML vytvoří podobné obrazce jako předchozí příklad, s tím rozdílem, že je vytvořen pomocí <xref:System.Windows.Media.PathGeometry> místo pak <xref:System.Windows.Media.EllipseGeometry> vytváří čtyři soustředných oblouky místo pak plně uzavřený soustředných kroužky.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![Snímek obrazovky: Hodnota vlastnosti FillRule NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero3.png "FillRuleNonZero3")  
  
 Všimněte si, že není vyplněna třetí oblouk z centra. Následující ilustrace zobrazuje, proč je to. Na obrázku red šipky představují směr, ve kterém jsou vykreslovány segmentů. Dva bílé šipky představují dva libovolný paprsky, které přepínají z bodu v oblasti "bez naplní". Jak je vidět z obrázku, aby součet hodnot z daného paprsek při překročení segmentů v cestě je nulová. Definuje výše, součet nula znamená, že bod se není součástí Geometrie (není součástí výplně) při sum, který je *není* nula, včetně záporná, je součástí geometrického útvaru.  
  
 ![Diagram: Hodnota vlastnosti FillRule NonZero](../../../../docs/framework/wpf/graphics-multimedia/media/fillrulenonzero4.png "FillRuleNonZero4")  
  
 **Poznámka:** pro účely <xref:System.Windows.Media.FillRule>, všechny obrazce jsou považovány za uzavřen. Pokud existuje mezera v segmentu, kreslení čárou a tím ho zavřete. V předchozím příkladu jsou malé mezery v kroužky. To zadána jeden můžou očekávat paprsek používající prostřednictvím mezera umožnit jiný výsledek pak paprsek systémem v jiném směru. Níže je ilustraci zvětšeným jednoho z těchto mezery a "pomyslná segmentu" (segment, který je vykreslen pro účely použití <xref:System.Windows.Media.FillRule>), se zavře.  
  
 ![Diagram: Pro vlastnost FillRule jsou segmenty vždy uzavřené](../../../../docs/framework/wpf/graphics-multimedia/media/fillruleclosedshapes.png "FillRuleClosedShapes")  
  
## <a name="example"></a>Příklad  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření složeného tvaru](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
