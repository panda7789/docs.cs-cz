---
title: "Přehled masek krytí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [WPF], opacity masks
- masks [WPF], opacity
- opacity [WPF], masks
ms.assetid: 22367fab-5f59-4583-abfd-db2bf86eaef7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6cd077d1e24fa50dc42a2169b45fe38930cc76c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="opacity-masks-overview"></a>Přehled masek krytí
Masky krytí umožňují provést části elementu nebo visual průhledných nebo částečně transparentní. Chcete-li vytvořit masky krytí, je použít <xref:System.Windows.Media.Brush> k <xref:System.Windows.UIElement.OpacityMask%2A> vlastnost elementu nebo <xref:System.Windows.Media.Visual>.  Štětec se mapuje na element nebo visual a hodnota neprůhlednosti každého obrazového bodu štětce slouží k určení výsledného krytí jednotlivých odpovídající pixelů, elementu nebo visual.  
  
<a name="prereqs"></a>   
## <a name="prerequisites"></a>Požadavky  
 Tento přehled předpokládá, že jste obeznámeni s <xref:System.Windows.Media.Brush> objekty. Úvod do používání štětce, najdete v části [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Informace o <xref:System.Windows.Media.ImageBrush> a <xref:System.Windows.Media.DrawingBrush>, najdete v části [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="opacitymasks"></a>   
## <a name="creating-visual-effects-with-opacity-masks"></a>Vytváření vizuálních efektů pomocí masky krytí  
 Maska krytí funguje tak, že do elementu nebo visual mapování její obsah. Alfa kanálu jednotlivých pixelů štětce pak slouží k určení výsledného krytí element nebo na visual odpovídající pixelů; skutečné barvu štětce se ignoruje. Pokud je danou část stopy transparentní, odpovídající část elementu nebo visual viditelný. Pokud je danou část stopy neprůhledné, krytí odpovídající část elementu nebo visual se nezmění. Krytí určeného maska krytí spolu s nastavení krytí v prvku nebo visual. Například pokud je element 25 procent neprůhledných a masky krytí platí, která přejde z plně neprůhledného do zcela průhledné, výsledkem je element, který přechází z 25 procent krytí do zcela průhledná.  
  
> [!NOTE]
>  I když tento přehled příkladech masek krytí u elementů bitové kopie, masky krytí mohou být použity u libovolného elementu nebo <xref:System.Windows.Media.Visual>, včetně panelů a ovládací prvky.  
  
 Masky krytí slouží k vytváření zajímavé vizuální efekty, například vytvoření bitové kopie nebo tlačítka, která zmizí ze zobrazení, přidat textury na elementy nebo kombinovat přechody k vytvoření povrchy jako pohotovostní. Následující obrázek ukazuje použití masky krytí. Šachovnicová mřížka pozadí se používá k zobrazení části transparentní masky.  
  
 ![Objekt s maskou neprůhlednosti LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-opacitymask-imageexample.png "wcpsdk_graphicsmm_opacitymask_imageexample")  
Příklad maskování neprůhlednost.  
  
<a name="creatingopacitymasks"></a>   
## <a name="creating-an-opacity-mask"></a>Vytvoření masky krytí  
 Chcete-li vytvořit masky krytí, je vytvořit <xref:System.Windows.Media.Brush> a použijte ho k <xref:System.Windows.UIElement.OpacityMask%2A> vlastnosti element nebo visual. Můžete použít jakýkoli typ <xref:System.Windows.Media.Brush> jako masky krytí.  
  
-   <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>: Používají k vytvoření prvku nebo visual Objevování ze zobrazení.  
  
     Na následujícím obrázku <xref:System.Windows.Media.LinearGradientBrush> použít jako masky krytí.  
  
     ![Objekt s neprůhlednosti LinearGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-brushes-lineagradientopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_lineagradientopacitymasksingle")  
Příklad LinearGradientBrush krytí maskování  
  
-   <xref:System.Windows.Media.ImageBrush>: Použít k vytvoření texture a logicky nebo vytržená edge účinky.  
  
     Následující obrázek znázorňuje <xref:System.Windows.Media.ImageBrush> použít jako masky krytí.  
  
     ![Objekt, který má maskou neprůhlednosti ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-brushes-imageasopacitymasksingle.jpg "wcpsdk_graphicsmm_brushes_imageasopacitymasksingle")  
Příklad maskování krytí LinearGradientBrush  
  
-   <xref:System.Windows.Media.DrawingBrush>: Použít k vytvoření komplexní krytí masky od tvarů, bitové kopie a přechody.  
  
     Na následujícím obrázku <xref:System.Windows.Media.DrawingBrush> použít jako masky krytí.  
  
     ![Objekt s maskou neprůhlednosti DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-drawingbrushasopacitymask-single.jpg "wcpsdk_drawingbrushasopacitymask_single")  
Příklad maskování krytí DrawingBrush  
  
 Štětce přechodu (<xref:System.Windows.Media.LinearGradientBrush> a <xref:System.Windows.Media.RadialGradientBrush>) jsou zvlášť vhodné pro použití jako masky krytí. Protože <xref:System.Windows.Media.SolidColorBrush> výplněmi na oblast s jednotné barvy, provádění nízký krytí zakrývá; pomocí <xref:System.Windows.Media.SolidColorBrush> je ekvivalentní nastavení elementu nebo na visual <xref:System.Windows.UIElement.OpacityMask%2A> vlastnost.  
  
<a name="creatingopacitymaskswithgradients"></a>   
## <a name="using-a-gradient-as-an-opacity-mask"></a>Použití přechod jako masky krytí  
 K vytvoření přechodu výplně, zadejte dva nebo více Přechodové zarážky. Obsahuje každou Přechodové zarážky popisuje barvu a pozice (najdete v části [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) Další informace o vytváření a používání přechody). Proces je stejný při použití přechod jako masky krytí s tím rozdílem, že místo prolnutí barvy, přechodu maska krytí smíchá hodnoty alfa kanálu. Proto není důležité barvu skutečný obsah má barevný přechod; záleží jenom alfa kanálu, nebo krytí jednotlivých barev. Následuje příklad.  
  
 [!code-xaml[OpacityMasksSnippet#LinearGradientOpacityMaskonImage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#lineargradientopacitymaskonimage)]  
  
<a name="specifyinggradientcolors"></a>   
## <a name="specifying-gradient-stops-for-an-opacity-mask"></a>Určení ukončení přechodu pro masku krytí  
 V předchozím příkladu, barvu definovaná systémem <xref:System.Windows.Media.Colors.Black%2A> slouží jako počáteční barvu barevného přechodu. Protože všechny barvy v <xref:System.Windows.Media.Colors> třída, s výjimkou <xref:System.Windows.Media.Colors.Transparent%2A>, jsou plně neprůhledné, lze jednoduše zadat počáteční barvu pro masku krytí přechodu.  
  
 Pro další kontrolu nad hodnoty alfa při definování masky krytí, můžete zadat alfa kanálu pomocí barev [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] šestnáctkové soustavě v kódu nebo pomocí <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> metoda.  
  
<a name="argbsyntax"></a>   
### <a name="specifying-color-opacity-in-xaml"></a>Určení krytí barev v "XAML"  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], použijete [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] šestnáctkové soustavě k určení krytí jednotlivých barev. [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)]šestnáctkové soustavě používá následující syntaxe:  
  
 `#`**aa** *rrggbb*  
  
 *Aa* v předchozí řádek představuje letopočty šestnáctkové hodnoty slouží k zadání krytí barvy. *Rr*, *gg*, a *bb* každý představují dvoumístné šestnáctkové hodnoty používaný k zadání množství červená, zelená a modrá v barvu. Každý šestnáctková číslice může mít hodnotu od 0 – 9 nebo A-F. 0 je nejmenší hodnota a F je největší. Při použití hodnoty alfa 00 určuje barvu, která je zcela transparentní, zatímco při použití hodnoty alfa FF vytvoří barvu, která je plně neprůhledný.  V následujícím příkladu, hexadecimální [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] zápis slouží k určení dvě barvy. První je zcela neprůhledné, zatímco druhý je zcela transparentní.  
  
 [!code-xaml[OpacityMasksSnippet#AARRGGBBValueonOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/GradientBrushExample.xaml#aarrggbbvalueonopacitymask)]  
  
<a name="usingimageasopacitymask"></a>   
## <a name="using-an-image-as-an-opacity-mask"></a>Použití bitovou kopii jako masky krytí  
 Obrázky lze použít také jako masky krytí. Následující obrázek ukazuje příklad. Šachovnicová mřížka pozadí se používá k zobrazení části transparentní masky.  
  
 ![Objekt s maskou neprůhlednosti ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-imageasopacitymask.png "wcpsdk_graphicsmm_imageasopacitymask")  
Příklad maskování neprůhlednost.  
  
 Chcete-li použít bitovou kopii jako masky krytí, použijte <xref:System.Windows.Media.ImageBrush> tak, aby obsahovala bitovou kopii. Při vytváření obrázek, který se použije jako masky krytí, uložit obrázek ve formátu, který podporuje více úrovní transparentnosti, například [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]. Následující příklad ukazuje kód používaný k vytvoření na předchozím obrázku.  
  
 [!code-xaml[OpacityMasksSnippet#UIElementOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#uielementopacitymask)]  
  
<a name="tilingimageopacitymask"></a>   
### <a name="using-a-tiled-image-as-an-opacity-mask"></a>Pomocí obrázků vedle sebe jako masky krytí  
 V následujícím příkladu se používá stejnou bitovou kopii s jinou <xref:System.Windows.Media.ImageBrush>, ale funkce stopy dlaždice se používají k vytvoření dlaždice druhou mocninu image 50 pixelů.  
  
 [!code-xaml[OpacityMasksSnippet#TiledImageasOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/ImageBrushExample.xaml#tiledimageasopacitymask)]  
  
<a name="drawingbrushasopacitymask"></a>   
## <a name="creating-an-opacity-mask-from-a-drawing"></a>Vytváření masky krytí z výkresu  
 Kresby lze použít masky krytí. Obsažené v kreslení obrazce můžete sami vyplněn přechody plné barvy, Image nebo i další výkresy. Následující obrázek znázorňuje příklad výkresu použít jako masky krytí. Šachovnicová mřížka pozadí se používá k zobrazení části transparentní masky.  
  
 ![Objekt s maskou neprůhlednosti DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-drawingbrushasopacitymask.png "wcpsdk_drawingbrushasopacitymask")  
Příklad maskování krytí DrawingBrush  
  
 Pokud chcete použít jako masky krytí výkresu, použijte <xref:System.Windows.Media.DrawingBrush> tak, aby obsahovala kreslení. Následující příklad ukazuje kód používaný k vytvoření na předchozím obrázku:  
  
 [!code-xaml[OpacityMasksSnippet#OpacityMaskfromDrawing](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#opacitymaskfromdrawing)]  
  
<a name="tileddrawingbrush"></a>   
### <a name="using-a-tiled-drawing-as-an-opacity-mask"></a>Použití vedle sebe kreslení jako masky krytí  
 Podobně jako <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> můžete provedeny na dlaždici jeho kreslení. V následujícím příkladu se kreslení štětce používá k vytvoření masku krytí vedle sebe.  
  
 [!code-xaml[OpacityMasksSnippet#TiledDrawingasOpacityMask](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpacityMasksSnippet/CS/DrawingBrushExample.xaml#tileddrawingasopacitymask)]  
  
## <a name="see-also"></a>Viz také  
 [Malování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Malování s plnou barvy a přechody – přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
