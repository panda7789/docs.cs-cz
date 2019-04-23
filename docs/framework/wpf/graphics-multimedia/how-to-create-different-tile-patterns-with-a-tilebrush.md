---
title: 'Postupy: Vytvoření jiných vzorů dlaždic pomocí prvku TileBrush'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
ms.openlocfilehash: c1051b234961eee9ae740af2abac3d64c523656c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227402"
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>Postupy: Vytvoření jiných vzorů dlaždic pomocí prvku TileBrush
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost <xref:System.Windows.Media.TileBrush> k vytvoření vzorku.  
  
 <xref:System.Windows.Media.TileBrush.TileMode%2A> Vlastnost umožňuje určit způsob, jak obsah <xref:System.Windows.Media.TileBrush> se opakuje, to znamená, vedle sebe k zaplnění výstupní oblasti. K vytvoření vzorku, nastavíte <xref:System.Windows.Media.TileBrush.TileMode%2A> k <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, nebo <xref:System.Windows.Media.TileMode.FlipXY>. Musíte taky nastavit <xref:System.Windows.Media.TileBrush.Viewport%2A> z <xref:System.Windows.Media.TileBrush> tak, aby je menší než oblasti, kterou vymalováváte; v opačném případě pouze jednu dlaždici je vyprodukované, bez ohledu na to což <xref:System.Windows.Media.TileBrush.TileMode%2A> nastavení používáte.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří pět <xref:System.Windows.Media.DrawingBrush> objekty, poskytuje jim každý jiný <xref:System.Windows.Media.TileBrush.TileMode%2A> nastavení a použije je k vykreslení obdélníků pět. I když v tomto příkladu <xref:System.Windows.Media.DrawingBrush> třídy k předvedení <xref:System.Windows.Media.TileBrush.TileMode%2A> chování, <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnost funguje stejně jako u všech <xref:System.Windows.Media.TileBrush> objekty, to znamená, pro <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, a <xref:System.Windows.Media.DrawingBrush>.  
  
 Následující obrázek ukazuje výstup, který tento příklad vytvoří.  
  
 ![TileBrush – dlaždice příklad výstupu](./media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
Vytvořen s vlastností vlastnosti TileMode objektu vzorů dlaždic  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>Viz také:

- [Nastavení velikosti dlaždice pro TileBrush](how-to-set-the-tile-size-for-a-tilebrush.md)
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
