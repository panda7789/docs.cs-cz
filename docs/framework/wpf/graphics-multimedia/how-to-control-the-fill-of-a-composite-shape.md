---
title: 'Postupy: Řízení výplně složeného tvaru'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 0ba07d8979a2910ce4ec775493e38c714240f642
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997112"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Postupy: Řízení výplně složeného tvaru
<xref:System.Windows.Media.GeometryGroup.FillRule%2A> Vlastnost <xref:System.Windows.Media.GeometryGroup> nebo <xref:System.Windows.Media.PathGeometry>, určuje "pravidlo" který složeného tvaru používá k určení, zda daný bod je součástí geometrii. Existují dva možné hodnoty pro <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> a <xref:System.Windows.Media.FillRule.Nonzero>. V následujících částech se popisují, jak používat tyto dvě pravidla.  
  
 **EvenOdd:** Toto pravidlo určuje, zda bod v oblasti výplně kreslení ray od tohoto okamžiku do nekonečna vede libovolným směrem a počtu segmentů cesty v rámci daného tvaru protne. Pokud je toto číslo liché, bod nachází uvnitř; Pokud ještě, se bod nachází mimo.  
  
 Například následující XAML vytvoří složeného tvaru, který se skládá z řady instancí soustředných (cíl) s <xref:System.Windows.Media.GeometryGroup.FillRule%2A> nastavena na <xref:System.Windows.Media.FillRule.EvenOdd>.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![Kruh se skládá z řady soustředných aktualizační kanály s různými barvami.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-property.png)  
  
 Na předchozím obrázku Všimněte si, že nejsou vyplněné System center a třetí kanál. Je to proto ray z libovolného bodu v některé z těchto dvou okruhů prochází sudý počet segmentů. Viz následující obrázek:  
  
 ![Diagram znázorňující paprsky EvenOdd vykreslen v kruhu.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-rays.png)  
  
 **Nenulovou hodnotu:** Toto pravidlo určuje, zda bod v oblasti výplně cesty k vykreslení ray od tohoto okamžiku do nekonečna vede libovolným směrem a poté zkoumá místa, kde segment tvaru protne. Spuštění s počtem nula, přidejte každý čas Segment protne zleva doprava a odečítání každý čas cestu segmentu protne zprava doleva. Po počítání přechody, pokud je výsledek nula pak se bod nachází mimo cestu. V opačném případě se nachází uvnitř.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 Použijeme předchozí příklad hodnotu <xref:System.Windows.Media.FillRule.Nonzero> pro <xref:System.Windows.Media.GeometryGroup.FillRule%2A> poskytuje díky tomu na následujícím obrázku:  
  
 ![Tvořené řadu soustředných okruhy všechny se stejnou barvu kruhu.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-nonzero.png)  
  
 Jak vidíte, jsou vyplněny všechny aktualizační kanály. Toto je vzhledem k tomu, že všechny segmenty jsou spuštěny ve stejném směru a tak, aby ray z libovolného bodu bude mezi jeden nebo více segmentů a součet hodnot přechodech nesmí být roven nule. Například na následujícím obrázku, červenou šipky představují směr, ve kterém jsou vykreslovány segmenty a bílé šipka označuje libovolné ray spuštěná z bodu ve vnitřní prstenec. Spuštění s hodnotou nula, pro každý segment protne, je přidat o hodnotu jedna, protože segment protne zleva doprava.  
  
 ![Diagram znázorňující rovna Nonzero FillRule hodnotu vlastnosti.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-equal-nonzero.png)  
  
 Abychom lépe chování <xref:System.Windows.Media.FillRule.Nonzero> pravidlo složitější obrazec s segmenty spuštěné v různých pokynů je povinné. Následující kód XAML vytvoří obrazec podobné jako předchozí příklad s tím rozdílem, že je vytvořen s <xref:System.Windows.Media.PathGeometry> nikoli <xref:System.Windows.Media.EllipseGeometry> vytváří čtyři soustředných oblouky spíše plně zavřeny soustředných kruzích.  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 Následující obrázek znázorňuje tvar vytvořený v předchozím příkladu.  
  
 ![Kruh se skládá z řady soustředných aktualizační kanály s různými barvami s třetí oblouk není vyplněné.](./media/how-to-control-the-fill-of-a-composite-shape/pathgeometry-concentric-arcs.png)  
  
 Všimněte si, že není vyplněno třetí oblouk v centru. Následující ilustrace ukazuje, proč je to. Na obrázku red šipky představují směr, ve kterém jsou vykreslovány segmenty. Dvě šipky bílé představují dva libovolného paprsky, které přesunout ven z bodu v oblasti "nevyplněná". Jak je vidět z obrázku, aby součet hodnot z daného ray přecházení mezi segmenty v cestě je nula. Definované výše součet nula znamená, že bod není součástí Geometrie (není součástí výplně) při sum, která je *není* nula, včetně hodnota záporná, je součástí geometrii.  
  
 ![Diagram znázorňující libovolného paprsky hraničních segmenty.](./media/how-to-control-the-fill-of-a-composite-shape/arbitrary-ray-cross-segment.png)  
  
 **Poznámka:** Pro účely <xref:System.Windows.Media.FillRule>, všechny obrazce se považují za uzavřen. Pokud existuje mezera v segmentu, nakreslete imaginární řádku ho zavřít. V předchozím příkladu jsou malé mezery v kroužky. To směru, očekávat paprsku, který projde mezera poskytnout jiné výsledky pak ray systémem v jiném směru. Níže je zvětšeným ilustraci jednu z těchto mezer a "imaginární segmentu" (segment, který je vykreslen pro účely <xref:System.Windows.Media.FillRule>), která ukončí.  
  
 ![Diagram znázorňující FillRule segmenty, které jsou vždy uzavřen.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-closed-segments.png)  
  
## <a name="example"></a>Příklad  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření složeného tvaru](how-to-create-a-composite-shape.md)
- [Přehled geometrie](geometry-overview.md)
