---
title: 'Postupy: Vytvoření kompozitní kresby'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: 886956b03bd3e17360283cee1bc0e4db1d2a4731
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491412"
---
# <a name="how-to-create-a-composite-drawing"></a>Postupy: Vytvoření kompozitní kresby
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.DrawingGroup> k vytvoření složitých drawings kombinací několika <xref:System.Windows.Media.Drawing> objekty do jednoho kompozitní kresby.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.DrawingGroup> vytvoření složeného vykreslování ze <xref:System.Windows.Media.GeometryDrawing> a <xref:System.Windows.Media.ImageDrawing> objekty. Následující obrázek ukazuje výstup, který tento příklad vytvoří.  
  
 ![DrawingGroup – s použitím kreslení více](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
Který je vytvořen pomocí DrawingGroup kompozitní kresby  
  
 Všimněte si šedé ohraničení, která ukazuje rozsah výkresu.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Můžete použít <xref:System.Windows.Media.DrawingGroup> použít <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> nastavení <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, nebo <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> kreslení obsahuje. Protože <xref:System.Windows.Media.DrawingGroup> je také <xref:System.Windows.Media.Drawing>, mohou obsahovat jiné <xref:System.Windows.Media.DrawingGroup> objekty.  
  
 Následující příklad je podobný předchozí příklad, s tím rozdílem, že používá další <xref:System.Windows.Media.DrawingGroup> objektů použít některé z jeho drawings bitmapových efektů a masku neprůhlednosti. Následující obrázek ukazuje výstup, který tento příklad vytvoří.  
  
 ![DrawingGroup – s použitím kreslení více](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")  
Složené výkresu, který má více DrawingGroup – objekty  
  
 Všimněte si šedé ohraničení, která ukazuje rozsah výkresu.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>
- <xref:System.Windows.Media.DrawingGroup.Transform%2A>
- <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>
- <xref:System.Windows.Media.DrawingGroup.Opacity%2A>
- <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>
- <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>
- [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
