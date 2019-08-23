---
title: Přehled masek krytí
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: d0fea1aac4efb17811404ce45769615bb2e7234f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929661"
---
# <a name="opacity-masks-overview"></a>Přehled masek krytí
Masky neprůhlednosti umožňují nastavit části prvku nebo vizuálu buď transparentní, nebo částečně transparentní. Chcete-li vytvořit masku neprůhlednosti, <xref:System.Windows.Media.Brush> použijte <xref:System.Windows.UIElement.OpacityMask%2A> pro vlastnost elementu nebo <xref:System.Windows.Media.Visual>.  Štětec je namapován na prvek nebo vizuál a hodnota neprůhlednosti každého obrazového bodu štětce se používá k určení výsledné neprůhlednosti každého odpovídajícího pixelu prvku nebo vizuálu.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Požadavky  
 Tento přehled předpokládá, že máte zkušenosti s <xref:System.Windows.Media.Brush> objekty. Úvod k používání štětců naleznete v tématu [malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md). Informace o <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.DrawingBrush>najdete v tématu [malování pomocí obrázků, kreseb a vizuálů](painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Vytváření vizuálních efektů s maskami neprůhlednosti  
 Maska neprůhlednosti funguje tak, že mapuje její obsah na prvek nebo vizuál. Alfa kanál každého z obrazových bodů štětce se pak použije k určení výsledné neprůhlednosti prvku nebo odpovídajících obrazových bodů vizuálu; skutečná barva štětce je ignorována. Pokud je předaná část štětce průhledná, odpovídající část prvku nebo vizuálu se změní na transparentní. Pokud je daná část štětce neprůhledná, nezůstane průhlednost odpovídající části prvku nebo vizuálu beze změny. Krytí určené maskou neprůhlednosti je kombinováno s jakýmkoli nastavením neprůhlednosti, které je přítomno v prvku nebo vizuálu. Například pokud je prvek 25 procent neprůhledný a je použita maska neprůhlednosti, která přechází z zcela neprůhledných na plně transparentní, výsledkem je prvek, který přechází z neprůhlednosti 25 procent na plně transparentní.  
  
> [!NOTE]
> I když příklady v tomto přehledu ukazují použití masek neprůhlednosti pro prvky obrázku, může být použita maska neprůhlednosti pro libovolný prvek <xref:System.Windows.Media.Visual>nebo, včetně panelů a ovládacích prvků.  
  
 Masky neprůhlednosti slouží k vytváření zajímavých vizuálních efektů, jako je například vytváření obrázků nebo tlačítek, které se zobrazují v zobrazení, přidávání textur k prvkům nebo kombinování přechodů za účelem vytvoření povrchů podobných skleněným. Následující obrázek ukazuje použití masky krytí. K zobrazení průhledných částí masky se používá šachovnicové pozadí.  
  
 ![Objekt s maskou neprůhlednosti LinearGradientBrush](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Příklad maskování neprůhlednosti  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Vytvoření masky krytí  
 Chcete-li vytvořit masku krytí, <xref:System.Windows.Media.Brush> vytvoříte a použijte ji <xref:System.Windows.UIElement.OpacityMask%2A> pro vlastnost elementu nebo vizuálu. Můžete použít libovolný typ <xref:System.Windows.Media.Brush> jako masku krytí.  
  
- <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Slouží k nastavení zobrazení prvku nebo vizuálu.  
  
     Následující obrázek ukazuje <xref:System.Windows.Media.LinearGradientBrush> použití jako masky krytí.  
  
     ![Objekt s maskou neprůhlednosti LinearGradientBrush](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Příklad maskování neprůhlednosti LinearGradientBrush  
  
- <xref:System.Windows.Media.ImageBrush>: Slouží k vytváření textur a měkkých nebo odtrhanécích efektů Edge.  
  
     Následující obrázek ukazuje <xref:System.Windows.Media.ImageBrush> použití jako masky krytí.  
  
     ![Objekt, který má masku neprůhlednosti ImageBrush](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Příklad maskování neprůhlednosti LinearGradientBrush  
  
- <xref:System.Windows.Media.DrawingBrush>: Slouží k vytvoření složitých masek neprůhledností ze vzorů tvarů, obrázků a přechodů.  
  
     Následující obrázek ukazuje <xref:System.Windows.Media.DrawingBrush> použití jako masky krytí.  
  
     ![Objekt s maskou neprůhlednosti prostředek DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Příklad maskování neprůhlednosti prostředek DrawingBrush  
  
 Štětce přechodu (<xref:System.Windows.Media.LinearGradientBrush> a <xref:System.Windows.Media.RadialGradientBrush>) jsou zvláště vhodné pro použití jako masky krytí. Vzhledem k tomu, že <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.UIElement.OpacityMask%2A> vyplníoblaststejnoubarvou,majíšpatnémaskyneprůhlednosti;použitíprvkujeekvivalentemnastavenívlastnosti<xref:System.Windows.Media.SolidColorBrush> prvku nebo vizuálu.  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Použití přechodu jako masky krytí  
 Chcete-li vytvořit přechodovou výplň, zadejte dvě nebo více zarážek přechodu. Každé přechodové zarážky obsahuje popis barvy a pozice (viz [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md) , kde najdete další informace o vytváření a používání přechodů). Tento proces je stejný při použití přechodu jako masky krytí, s tím rozdílem, že místo barev prolnutí barvy neprůhlednosti prochází hodnoty alfa kanálu. Takže skutečná barva obsahu přechodu nezáleží na tom; pouze alfa kanál (nebo neprůhlednost) jednotlivých aspektů barev. Následuje příklad.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Určení zastavení přechodu pro masku krytí  
 V předchozím příkladu je jako počáteční barva přechodu použita barva <xref:System.Windows.Media.Colors.Black%2A> definovaná systémem. Vzhledem k tomu, že všechny barvy <xref:System.Windows.Media.Colors> ve třídě, <xref:System.Windows.Media.Colors.Transparent%2A>s výjimkou, jsou zcela neprůhledné, lze použít k definování počáteční barvy masky krytí přechodu.  
  
 Pro lepší kontrolu nad hodnotami alfa při definování masky krytí můžete určit alfa kanál barev pomocí ARGB hexadecimálního zápisu v kódu nebo pomocí <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> metody.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Určení neprůhlednosti barev v jazyce XAML  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]nástroji použijete ARGB hexadecimální zápis k určení neprůhlednosti jednotlivých barev. ARGB hexadecimální zápis používá následující syntaxi:  
  
 `#` **aa** *rrggbb*  
  
 *AA* na předchozím řádku představuje hexadecimální hodnotu se dvěma číslicemi, která se používá k určení neprůhlednosti barvy. Každý *záznam RR*, *GG*a *BB* představuje dvě číslice šestnáctkové hodnoty, které se používají k určení množství červené, zelené a modré barvy. Každé hexadecimální číslo může mít hodnotu od 0-9 nebo A-F. 0 je nejmenší hodnota a F je největší. Hodnota alfa 00 určuje barvu, která je zcela průhledná, zatímco alfa hodnota FF vytvoří barvu, která je zcela neprůhledná.  V následujícím příkladu je použit hexadecimální zápis ARGB pro zadání dvou barev. První je plně neprůhledný, zatímco druhá je zcela transparentní.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Použití obrázku jako masky krytí  
 Obrázky lze také použít jako masku krytí. Příklad ukazuje následující obrázek. K zobrazení průhledných částí masky se používá šachovnicové pozadí.  
  
 ![Objekt s maskou neprůhlednosti ImageBrush](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Příklad maskování neprůhlednosti  
  
 Chcete-li použít obrázek jako masku krytí, použijte <xref:System.Windows.Media.ImageBrush> k zahrnutí obrázku. Když vytváříte obrázek, který se má použít jako maska neprůhlednosti, uložte obrázek ve formátu, který podporuje více úrovní průhlednosti, jako je například Portable Network Graphics (PNG). Následující příklad ukazuje kód použitý k vytvoření předchozího obrázku.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Použití obrázku vedle sebe jako masky krytí  
 V následujícím příkladu je stejný obrázek použit s jiným <xref:System.Windows.Media.ImageBrush>, ale funkce dlaždic štětce jsou použity k vytváření dlaždic z čtverce obrázku 50 pixelů.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Vytvoření masky krytí z kresby  
 Pro kresby se dá použít maska neprůhlednosti. Tvary obsažené v kresbě lze sami vyplnit pomocí přechodů, plných barev, obrázků nebo dokonce i jiných kreseb. Následující obrázek ukazuje příklad kresby používané jako masky krytí. K zobrazení průhledných částí masky se používá šachovnicové pozadí.  
  
 ![Objekt s maskou neprůhlednosti prostředek DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Příklad maskování neprůhlednosti prostředek DrawingBrush  
  
 Chcete-li použít výkres jako masku krytí, použijte <xref:System.Windows.Media.DrawingBrush> k zahrnutí kresby. Následující příklad ukazuje kód použitý k vytvoření předchozího obrázku:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Použití dlaždicového vykreslování jako masky krytí  
 Podobně jako <xref:System.Windows.Media.ImageBrush>je <xref:System.Windows.Media.DrawingBrush> možné vytvořit dlaždici své kresby. V následujícím příkladu se k vytvoření dlaždicové masky krytí používá kreslicí štětec.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Viz také:

- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
