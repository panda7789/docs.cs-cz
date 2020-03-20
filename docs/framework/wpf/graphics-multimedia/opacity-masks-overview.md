---
title: Přehled masek krytí
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 0c859659c35e2a5806b8585214c87c18fbcb62d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187690"
---
# <a name="opacity-masks-overview"></a>Přehled masek krytí
Masky krytí umožňují vytvořit části prvku nebo vizuálu průhledné nebo částečně průhledné. Chcete-li vytvořit masku krytí, <xref:System.Windows.Media.Brush> aplikujte a <xref:System.Windows.UIElement.OpacityMask%2A> na <xref:System.Windows.Media.Visual>vlastnost prvku nebo .  Stopa je mapována na prvek nebo vizuál a hodnota krytí každého obrazového bodu stopy se používá k určení výsledného krytí každého odpovídajícího obrazového bodu prvku nebo vizuálu.  
  
<a name="prereqs"></a>
## <a name="prerequisites"></a>Požadavky  
 Tento přehled předpokládá, že <xref:System.Windows.Media.Brush> jste obeznámeni s objekty. Úvod k používání štětců najdete [v tématu Malování plnými barvami a přechody – přehled](painting-with-solid-colors-and-gradients-overview.md). Informace o <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.DrawingBrush>aplikaci a najdete v tématu [Malování obrázky, kresby a vizuály](painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>
## <a name="creating-visual-effects-with-opacity-masks"></a>Vytváření vizuálních efektů s maskami krytí  
 Maska krytí funguje tak, že mapuje její obsah na prvek nebo vizuál. Alfa kanál každého obrazového bodu stopy se pak používá k určení výsledného krytí prvku nebo odpovídajících obrazových bodů vizuálu; skutečná barva stopy je ignorována. Pokud je daná část stopy průhledná, odpovídající část prvku nebo vizuálu se stane průhlednou. Pokud je daná část stopy neprůhledná, krytí odpovídající části prvku nebo vizuálu se nezmění. Krytí určené maskou krytí je kombinováno s libovolnými nastaveními krytí, která se nacházejí v prvku nebo vizuálu. Pokud je například prvek 25 % neprůhledný a je použita maska krytí, která přechází z plně neprůhledného na plně průhledný, výsledkem je prvek, který přechází z krytí 25 procent na plně průhledný.  
  
> [!NOTE]
> Ačkoli příklady v tomto přehledu ukazují použití masek krytí na obrazové prvky, maska krytí může být použita na libovolný prvek nebo <xref:System.Windows.Media.Visual>, včetně panelů a ovládacích prvků.  
  
 Masky krytí se používají k vytváření zajímavých vizuálních efektů, jako je vytváření obrazů nebo tlačítek, které ze zobrazení blednou, pro přidání textur prvků nebo pro kombinování přechodů za účelem vytvoření skleněných povrchů. Následující obrázek znázorňuje použití masky krytí. Šachovna pozadí se používá k zobrazení průhledné části masky.  
  
 ![Objekt s maskou krytí LinearGradientBrush](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Příklad maskování krytí  
  
<a name="creatingopacitymasks"></a>
## <a name="creating-an-opacity-mask"></a>Vytvoření masky krytí  
 Chcete-li vytvořit masku krytí, <xref:System.Windows.Media.Brush> vytvořte a <xref:System.Windows.UIElement.OpacityMask%2A> aplikujte ji na vlastnost prvku nebo vizuálu. Jako masku krytí <xref:System.Windows.Media.Brush> můžete použít libovolný typ.  
  
- <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Používá se k tomu, aby prvek nebo vizuální zeslabení prvku ze zobrazení.  
  
     Následující obrázek <xref:System.Windows.Media.LinearGradientBrush> znázorňuje masku krytí.  
  
     ![Objekt s maskou krytí Krytí LinearGradientBrush](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Příklad maskování krytí pozadí lineargradientuštu  
  
- <xref:System.Windows.Media.ImageBrush>: Používá se k vytvoření textury a měkkých nebo roztržených okrajových efektů.  
  
     Následující obrázek <xref:System.Windows.Media.ImageBrush> znázorňuje masku krytí.  
  
     ![Objekt, který má masku krytí ImageBrush](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Příklad maskování krytí LinearGradientBrush  
  
- <xref:System.Windows.Media.DrawingBrush>: Slouží k vytvoření složitých masek krytí ze vzorků tvarů, obrazů a přechodů.  
  
     Následující obrázek <xref:System.Windows.Media.DrawingBrush> znázorňuje masku krytí.  
  
     ![Objekt s maskou krytí DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Příklad maskování krytí kreseb  
  
 Štětce<xref:System.Windows.Media.LinearGradientBrush> přechodu ( a <xref:System.Windows.Media.RadialGradientBrush>) jsou obzvláště vhodné pro použití jako maska krytí. Vzhledem <xref:System.Windows.Media.SolidColorBrush> k tomu, že vyplní oblast jednotnou barvou, vytvoří špatné masky krytí; pomocí <xref:System.Windows.Media.SolidColorBrush> je ekvivalentní nastavení <xref:System.Windows.UIElement.OpacityMask%2A> vlastnosti prvku nebo vizuálu.  
  
<a name="creatingopacitymaskswithgradients"></a>
## <a name="using-a-gradient-as-an-opacity-mask"></a>Použití přechodu jako masky krytí  
 Chcete-li vytvořit výplň přechodem, určete dvě nebo více zarážek přechodu. Každá zarážka přechodu obsahuje popis barvy a polohy (další informace o vytváření a používání přechodů viz [Malování plnými barvami a přechody Přehled).](painting-with-solid-colors-and-gradients-overview.md) Proces je stejný při použití přechodu jako masky krytí, s tím rozdílem, že místo prolnutí barev prolne přechod masky krytí hodnoty alfa kanálů. Takže skutečná barva obsahu gradientu nezáleží; záleží pouze na alfa kanálu nebo krytí každé barvy. Následuje příklad.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Určení zarážek přechodu pro masku krytí  
 V předchozím příkladu se systémem <xref:System.Windows.Media.Colors.Black%2A> definovaná barva používá jako počáteční barva přechodu. Vzhledem k tomu, <xref:System.Windows.Media.Colors> že <xref:System.Windows.Media.Colors.Transparent%2A>všechny barvy ve třídě, s výjimkou , jsou zcela neprůhledné, lze je jednoduše definovat počáteční barvu pro masku krytí přechodu.  
  
 Pro další kontrolu nad alfa hodnotami při definování masky krytí můžete určit alfa kanál barev pomocí hexadecimálního zápisu <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> ARGB ve značkách nebo pomocí metody.  
  
<a name="argbsyntax"></a>
### <a name="specifying-color-opacity-in-xaml"></a>Určení krytí barev v "XAML"  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]aplikace použijete šestnáctkový zápis ARGB k určení krytí jednotlivých barev. Hexadecimální zápis ARGB používá následující syntaxi:  
  
 `#`**aa** *rrggbb*  
  
 *Aa* v předchozím řádku představuje dvoumístnou šestnáctkovou hodnotu použitou k určení krytí barvy. *Rr*, *gg*a *bb* představují dvoumístnou šestnáctkovou hodnotu použitou k určení množství červené, zelené a modré barvy. Každá šestnáctková číslice může mít hodnotu od 0-9 nebo A-F. 0 je nejmenší hodnota a F je největší. Hodnota alfa 00 určuje barvu, která je zcela průhledná, zatímco alfa hodnota FF vytvoří barvu, která je zcela neprůhledná.  V následujícím příkladu šestnáctkové ARGB zápis se používá k určení dvou barev. První je zcela neprůhledná, zatímco druhá je zcela průhledná.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>
## <a name="using-an-image-as-an-opacity-mask"></a>Použití obrazu jako masky krytí  
 Obrazy lze také použít jako masku krytí. Příklad ukazuje následující obrázek. Šachovna pozadí se používá k zobrazení průhledné části masky.  
  
 ![Objekt s maskou krytí ImageBrush](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Příklad maskování krytí  
  
 Chcete-li použít obraz jako masku <xref:System.Windows.Media.ImageBrush> krytí, použijte k jeho zobrazení. Při vytváření obrazu, který má být použit jako maska krytí, uložte obraz ve formátu, který podporuje více úrovní průhlednosti, například portable network graphics (PNG). Následující příklad ukazuje kód použitý k vytvoření předchozí ilustrace.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Použití kachlového obrazu jako masky krytí  
 V následujícím příkladu se stejný obrázek používá s jiným <xref:System.Windows.Media.ImageBrush>obrázkem , ale prvky dlaždic stopy se používají k vytvoření dlaždic obrazu o rozloze 50 pixelů.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Vytvoření masky krytí z výkresu  
 Výkresy lze použít jako masku krytí. Tvary obsažené ve výkresu mohou být samy vyplněny přechody, plnými barvami, obrazy nebo dokonce jinými výkresy. Následující obrázek znázorňuje příklad výkresu použitého jako maska krytí. Šachovna pozadí se používá k zobrazení průhledné části masky.  
  
 ![Objekt s maskou krytí DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Příklad maskování krytí kreseb  
  
 Chcete-li použít výkres jako masku <xref:System.Windows.Media.DrawingBrush> krytí, použijte k jeho obsahujícímu výkresu. Následující příklad ukazuje kód použitý k vytvoření předchozíilustrace:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Použití kachlové kresby jako masky krytí  
 Stejně <xref:System.Windows.Media.ImageBrush>jako <xref:System.Windows.Media.DrawingBrush> , může být provedena dlaždice jeho výkresu. V následujícím příkladu se k vytvoření masky kachlového krytí používá stopa výkresu.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Viz také

- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
