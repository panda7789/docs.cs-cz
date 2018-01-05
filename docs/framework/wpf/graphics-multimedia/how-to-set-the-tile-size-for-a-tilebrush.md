---
title: "Postupy: Nastavení velikosti dlaždice pro TileBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e9b746fe66635054dbd35463f727d28a8abd3d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>Postupy: Nastavení velikosti dlaždice pro TileBrush
Tento příklad ukazuje, jak nastavit velikost dlaždice pro <xref:System.Windows.Media.TileBrush>. Ve výchozím nastavení <xref:System.Windows.Media.TileBrush> vytvoří jedna dlaždice, který kompletně vyplní celé oblasti, která jsou vykreslování. Toto chování můžete přepsat pomocí nastavení <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnosti.  
  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> Vlastnost určuje velikost dlaždice <xref:System.Windows.Media.TileBrush>. Výchozí hodnota <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost je relativní vzhledem k velikosti oblasti se vykresluje. Chcete-li <xref:System.Windows.Media.TileBrush.Viewport%2A> vlastnost stanovit velikost absolutní dlaždice, nastavit <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnost <xref:System.Windows.Media.BrushMappingMode.Absolute>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush>, typ <xref:System.Windows.Media.TileBrush>, k vyplnění obdélníku s dlaždice. V příkladu nastaví každou dlaždici na 50 procent o 50 procent výstupní oblasti (rámeček). V důsledku toho rámeček vykreslením s čtyři projekce bitové kopie.  
  
 Následující obrázek znázorňuje výstupu, který vytváří v příkladu.
  
 ![Příklad dlaždice s štětce image](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 Další příklad vytvoří <xref:System.Windows.Media.ImageBrush>, nastaví její <xref:System.Windows.Media.TileBrush.Viewport%2A> k `0,0,25,25` a jeho <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> k <xref:System.Windows.Media.BrushMappingMode.Absolute>a používá ho k vyplnění jiné obdélníku. V důsledku toho stopy vytvoří dlaždice, které mají 25 pixelů šířka a výška 25 pixelů.  
  
 Následující obrázek znázorňuje výstupu, který vytváří v příkladu.  
  
 ![A na dlaždicích TileBrush se zobrazení 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 V předchozích příkladech jsou součástí větší ukázky. Kompletní příklad, najdete v části [Objekt ImageBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
 I když tento příklad používá <xref:System.Windows.Media.ImageBrush> třídy, <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> vlastnosti chovají stejně jako pro druhý <xref:System.Windows.Media.TileBrush> objekty, který je pro <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>. Další informace o <xref:System.Windows.Media.ImageBrush> a dalších <xref:System.Windows.Media.TileBrush> objekty, najdete v části [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.TileBrush>  
 [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [Vytvoření jiných vzorů dlaždic pomocí prvku TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
