---
title: "Postupy: Vytváření jiných vzorů dlaždic pomocí TileBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6247f6a16cd8ab7be683d0d4d33aac021f3a2b32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>Postupy: Vytváření jiných vzorů dlaždic pomocí TileBrush
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost <xref:System.Windows.Media.TileBrush> vzorek.  
  
 <xref:System.Windows.Media.TileBrush.TileMode%2A> Vlastnost umožňuje určit jak obsah <xref:System.Windows.Media.TileBrush> se opakuje, který je, rozložen formou dlaždic k vyplnění oblast výstup. Pokud chcete vytvořit vzor, nastavíte <xref:System.Windows.Media.TileBrush.TileMode%2A> k <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, nebo <xref:System.Windows.Media.TileMode.FlipXY>. Je nutné také nastavit <xref:System.Windows.Media.TileBrush.Viewport%2A> z <xref:System.Windows.Media.TileBrush> tak, aby byla menší než k oblasti, která jste jsou vykreslování; jinak, pouze jedna dlaždice je vytvořené, bez ohledu na to který <xref:System.Windows.Media.TileBrush.TileMode%2A> nastavení, které používáte.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří pět <xref:System.Windows.Media.DrawingBrush> objekty, poskytne jim každý v jiné <xref:System.Windows.Media.TileBrush.TileMode%2A> nastavení a použije je k vyplnění pět obdélníky. I když tento příklad používá <xref:System.Windows.Media.DrawingBrush> třída k předvedení <xref:System.Windows.Media.TileBrush.TileMode%2A> chování, <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost funguje stejně jako u všech <xref:System.Windows.Media.TileBrush> objekty, který je pro <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, a <xref:System.Windows.Media.DrawingBrush>.  
  
 Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.  
  
 ![TileBrush dlaždice příklad výstupu](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
Vzory dlaždice, které jsou vytvořeny s vlastnosti TileMode objektu  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>Viz také  
 [Nastavení velikosti dlaždice pro objekt TileBrush](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [Malování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
