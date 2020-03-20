---
title: 'Postupy: Nastavení velikosti dlaždice pro TileBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186839"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Postupy: Nastavení velikosti dlaždice pro TileBrush

Tento příklad ukazuje, jak nastavit <xref:System.Windows.Media.TileBrush>velikost dlaždice pro . Ve výchozím <xref:System.Windows.Media.TileBrush> nastavení vytvoří jedna dlaždice, která zcela vyplní oblast, kterou malujete. Toto chování můžete přepsat <xref:System.Windows.Media.TileBrush.Viewport%2A> nastavením vlastností a. <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>

Vlastnost <xref:System.Windows.Media.TileBrush.Viewport%2A> určuje velikost dlaždice pro <xref:System.Windows.Media.TileBrush>. Ve výchozím nastavení je <xref:System.Windows.Media.TileBrush.Viewport%2A> hodnota vlastnosti relativní k velikosti oblasti, která je vybarvena. Chcete-li, <xref:System.Windows.Media.TileBrush.Viewport%2A> aby vlastnost určovat <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> absolutní <xref:System.Windows.Media.BrushMappingMode.Absolute>velikost dlaždice, nastavte vlastnost na .

## <a name="example"></a>Příklad

Následující příklad používá <xref:System.Windows.Media.ImageBrush>, typ <xref:System.Windows.Media.TileBrush>, malovat obdélník s dlaždicemi. Příklad nastaví každou dlaždici na 50 procent o 50 procent výstupní oblasti (obdélník). V důsledku toho je obdélník vymalován čtyřmi projekcemi obrazu.

Následující obrázek znázorňuje výstup, který v příkladu vytváří:

![Obdélník se čtyřmi třešněmi demonstrujícími obklady s obrazovým štětcem.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

Další příklad vytvoří <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.TileBrush.Viewport%2A> nastaví <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> jeho <xref:System.Windows.Media.BrushMappingMode.Absolute>a `0,0,25,25` jeho na , a používá jej k malování jiného obdélníku. V důsledku toho stopa vytváří dlaždice, které mají šířku 25 pixelů a výšku 25 pixelů .

Následující obrázek znázorňuje výstup, který v příkladu vytváří:

![Obdélník s čtyřicet osm třešní demonstrovat kachlová TileBrush s výřez.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

Předchozí příklady jsou součástí větší ukázky. Kompletní ukázku naleznete v tématu [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).

Ačkoli tento příklad <xref:System.Windows.Media.ImageBrush> používá <xref:System.Windows.Media.TileBrush.Viewport%2A> třídu, vlastnosti <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> a <xref:System.Windows.Media.TileBrush> se chovají stejně <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>pro ostatní objekty, to znamená pro a . Další informace <xref:System.Windows.Media.ImageBrush> o ostatních <xref:System.Windows.Media.TileBrush> objektech naleznete v [tématu Malování obrázky, kresbami a vizuály](painting-with-images-drawings-and-visuals.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.TileBrush>
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
- [Vytvoření jiných vzorů dlaždic pomocí prvku TileBrush](how-to-create-different-tile-patterns-with-a-tilebrush.md)
