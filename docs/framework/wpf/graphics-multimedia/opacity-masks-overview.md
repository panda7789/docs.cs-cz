---
title: Přehled masek krytí
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
ms.openlocfilehash: 7b6afebbf6ac2dda0f8eb9932630da9a273f972e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376803"
---
# <a name="opacity-masks-overview"></a>Přehled masek krytí
Masky krytí umožňují vytvářet elementu nebo vizuální části transparentní nebo částečně transparentní. Vytvoření masky krytí, můžete použít <xref:System.Windows.Media.Brush> k <xref:System.Windows.UIElement.OpacityMask%2A> vlastnost elementu nebo <xref:System.Windows.Media.Visual>.  Štětec mapován na prvek nebo vizuální a hodnotu neprůhlednosti každý pixel štětce se používá k určení výsledného krytí pixel odpovídající element nebo visual.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Požadavky  
 Tento přehled předpokládá, že máte zkušenosti s <xref:System.Windows.Media.Brush> objekty. Úvod do používání štětce, naleznete v tématu [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md). Informace o <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.DrawingBrush>, naleznete v tématu [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Vytváření vizuálních efektů pomocí masky krytí  
 Masky krytí funguje tak, že do elementu nebo visual mapování jeho obsah. Alfa kanál jednotlivých pixelů na stopu se následně použijí k určení výsledného krytí elementu nebo pixelech odpovídající vizuálu; vlastní Barva štětce se ignoruje. Pokud danou část štětec je transparentní, odpovídající část element nebo vizuál viditelný. Pokud danou část štětec je neprůhledný, krytí elementu nebo vizuál odpovídající část je beze změny. Neprůhlednost určené masky krytí číslo zkombinuje s krytí nastavení k dispozici v elementu nebo visual. Například pokud prvek je neprůhledný 25 procent a masku neprůhlednosti se použije, která přejde z úplně neprůhledná do zcela transparentní, výsledkem je element, který změní z 25 procent krytí na zcela průhledná.  
  
> [!NOTE]
>  I když se v příkladech v tomto přehledu ukazují použití masky krytí v prvcích obrázek, masky krytí může použít u libovolného elementu nebo <xref:System.Windows.Media.Visual>, včetně panely a ovládací prvky.  
  
 Masky krytí umožňují vytvářet zajímavé vizuální efekty, jako například vytvoření imagí nebo tlačítka, která má vyblednout ze zobrazení, přidat textury na elementy nebo kombinovat přechody k vytvoření povrchy skla jako. Následující obrázek znázorňuje použití masku neprůhlednosti. Šachovnicová mřížka na pozadí se používá k zobrazení transparentní části masky.  
  
 ![Objekt s maskou neprůhlednosti LinearGradientBrush](./media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Příklad masky krytí  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Vytvoření masky krytí  
 Vytvoření masky krytí, vytvoříte <xref:System.Windows.Media.Brush> a použít ji k <xref:System.Windows.UIElement.OpacityMask%2A> vlastnost elementu nebo vizuál. Můžete použít libovolný typ <xref:System.Windows.Media.Brush> jako masku neprůhlednosti.  
  
-   <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Použít k vytvoření elementu nebo visual fade ze zobrazení.  
  
     Následující obrázek znázorňuje <xref:System.Windows.Media.LinearGradientBrush> použít jako masku neprůhlednosti.  
  
     ![Objekt s neprůhlednosti LinearGradientBrush](./media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Příklad maskování LinearGradientBrush krytí  
  
-   <xref:System.Windows.Media.ImageBrush>: Použít k vytvoření textury a obnovitelně nebo vytržená edge účinky.  
  
     Následující obrázek znázorňuje <xref:System.Windows.Media.ImageBrush> použít jako masku neprůhlednosti.  
  
     ![Objekt, který má masky krytí ImageBrush](./media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Příklad maskování LinearGradientBrush krytí  
  
-   <xref:System.Windows.Media.DrawingBrush>: Použitý k vytvoření masky krytí komplexní na vzory tvarů, obrázky a přechody.  
  
     Následující obrázek znázorňuje <xref:System.Windows.Media.DrawingBrush> použít jako masku neprůhlednosti.  
  
     ![Objekt s masky krytí DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Příklad maskování neprůhlednosti objektu DrawingBrush  
  
 Štětce přechodu (<xref:System.Windows.Media.LinearGradientBrush> a <xref:System.Windows.Media.RadialGradientBrush>) je zvlášť vhodné pro použití jako masku neprůhlednosti. Protože <xref:System.Windows.Media.SolidColorBrush> výplně některou oblast s jednotné barvy, získávají nízký krytí zakrývá; pomocí <xref:System.Windows.Media.SolidColorBrush> je ekvivalentní nastavení prvku nebo vizuálu <xref:System.Windows.UIElement.OpacityMask%2A> vlastnost.  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Použití přechod jako masky krytí  
 K vytvoření přechodu výplně, zadejte dva nebo více Přechodové zarážky. Obsahuje každou přechodové popisuje barvy a pozice (naleznete v tématu [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md) Další informace o vytváření a používání přechody). Proces je stejný při použití přechod jako masky krytí s tím rozdílem, že místo prolnutí barvy, přechod masky krytí prolnutí alfa kanál hodnoty. Vlastní barva přechod na obsah, proto není důležitá; pouze alfa kanálu, a krytí každá barva záleží. Následuje příklad.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Zadání masky krytí Přechodové zarážky  
 V předchozím příkladu se barva definovaných systémem <xref:System.Windows.Media.Colors.Black%2A> slouží jako počáteční barva přechodu. Protože všechny barvy v <xref:System.Windows.Media.Colors> třídy, s výjimkou <xref:System.Windows.Media.Colors.Transparent%2A>, jsou zcela neprůhledný, lze jednoduše definovat počáteční barvu barevného přechodu neprůhlednosti masky.  
  
 Pro větší kontrolu nad hodnoty alfa při definování masky krytí, můžete zadat alfa kanál barvy s použitím [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] šestnáctkové soustavě v kódu nebo použití <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> metody.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Určení barvy krytí v "XAML"  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], použijete [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] šestnáctkové soustavě k určení krytí jednotlivé barvy. [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] šestnáctkové soustavě používá následující syntaxi:  
  
 `#` **aa** *rrggbb*  
  
 *Aa* v předchozí řádek představuje dvěma číslicemi šestnáctková hodnota používá k určení krytí barvu. *Rr*, *gg*, a *bb* každý představují dvě číslice šestnáctková hodnota používá k určení množství červené, zelené a modré v barvu. Každý šestnáctková číslice může mít hodnotu od 0 – 9 nebo A – F. nejmenší hodnota je 0 a F je nejvyšší. Alfa hodnotu 00 určuje barvu, která je zcela transparentní, zatímco alfa hodnotu FF vytvoří barvu, která je úplně neprůhledná.  V následujícím příkladu, hexadecimální [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] zápisu se používá k určení dvěma barvami. První je úplně neprůhledná, zatímco druhá je dokonale transparentní.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Pomocí Image jako masky krytí  
 Image můžete použít také jako masky krytí. Příklad ukazuje následující obrázek. Šachovnicová mřížka na pozadí se používá k zobrazení transparentní části masky.  
  
 ![Objekt s masky krytí ImageBrush](./media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Příklad masky krytí  
  
 Chcete-li použít obraz jako masky krytí, použijte <xref:System.Windows.Media.ImageBrush> obsahovat obrázek. Při vytváření image se použije jako masky krytí, uložit obrázek ve formátu, který podporuje více úrovní průhlednosti, jako například [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]. Následující příklad ukazuje kód používaný k vytvoření na předchozím obrázku.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Pomocí bitové kopie vedle sebe jako masky krytí  
 V následujícím příkladu se používá stejná image s jiným <xref:System.Windows.Media.ImageBrush>, ale funkce dělení do bloků na stopu se používají k vytvoření dlaždice čtverec image 50 pixelů.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Vytvoření masky krytí z kresby  
 Čára lze použít masku neprůhlednosti. Obsažené v kreslení tvarů můžete sami zaplněny přechody, plnými barvami, Image nebo dokonce i v dalších kreslení. Následující obrázek ukazuje příklad vykreslování používá jako masku neprůhlednosti. Šachovnicová mřížka na pozadí se používá k zobrazení transparentní části masky.  
  
 ![Objekt s masky krytí DrawingBrush](./media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Příklad maskování neprůhlednosti objektu DrawingBrush  
  
 Použití kresby jako masky krytí, použijte <xref:System.Windows.Media.DrawingBrush> tak, aby obsahovala výkresu. Následující příklad ukazuje kód používaný k vytvoření na předchozím obrázku:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Použití kresby vedle sebe jako masky krytí  
 Podobně jako <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> můžete provést na dlaždici jeho vykreslování. V následujícím příkladu kreslicího štětce slouží k vytvoření masky krytí vedle sebe.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](~/samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Viz také:
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
