---
title: 'Postupy: Nastavení velikosti dlaždice pro TileBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: e1ba1a25281ffdd1cc00e0bed0efe4f8508780be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467832"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Postupy: Nastavení velikosti dlaždice pro TileBrush
Tento příklad ukazuje, jak nastavení velikosti dlaždice pro <xref:System.Windows.Media.TileBrush>. Ve výchozím nastavení <xref:System.Windows.Media.TileBrush> vytváří jednu dlaždici, která úplně vyplňuje oblast, kterou vymalováváte. Toto chování můžete přepsat tak, že nastavíte <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnosti.  
  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Vlastnost určuje velikost dlaždice <xref:System.Windows.Media.TileBrush>. Výchozí hodnota <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost je relativní vzhledem k velikosti oblasti se překreslit. Chcete-li <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost určovat velikost absolutní dlaždice nastavit <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnost <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush>, typu <xref:System.Windows.Media.TileBrush>k vykreslení obdélníku s dlaždicemi. Příklad nastaví Každá dlaždice na 50 % 50 procent výstupní oblasti (obdélník). V důsledku toho obdélník vybarvené čtyři projekce bitové kopie.  
  
 Následující obrázek znázorňuje výstup v příkladu vytvoří.
  
 ![Příklad dělení do bloků s obrázkový štětec](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 Následující příklad vytvoří <xref:System.Windows.Media.ImageBrush>, nastaví jeho <xref:System.Windows.Media.TileBrush.Viewport%2A> k `0,0,25,25` a jeho <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> k <xref:System.Windows.Media.BrushMappingMode.Absolute>a použije ho k vykreslení jiného obdélník. V důsledku toho vytváří štětec, které mají šířku 25 pixelů a výšku v pixelech 25.  
  
 Následující obrázek znázorňuje výstup v příkladu vytvoří.  
  
 ![A vedle sebe TileBrush se oblast zobrazení 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 Předchozí příklady jsou součástí větší ukázky. Úplnou ukázku najdete v tématu [ImageBrush ukázka](https://go.microsoft.com/fwlink/?LinkID=160005).  
  
 I když v tomto příkladu <xref:System.Windows.Media.ImageBrush> třídy, <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnosti se chovají stejně jako pro ostatní <xref:System.Windows.Media.TileBrush> objekty, to znamená, pro <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>. Další informace o <xref:System.Windows.Media.ImageBrush> a druhý <xref:System.Windows.Media.TileBrush> objekty, najdete [Malování pomocí obrázků, kreseb a vizuálních](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.TileBrush>  
 [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Vytvoření jiných vzorů dlaždic pomocí prvku TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
