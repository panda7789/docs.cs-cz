---
title: 'Postupy: Vytvoření kompozitní kresby'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: bb222fff11c81b491c0413f174539ff0005d11b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-composite-drawing"></a>Postupy: Vytvoření kompozitní kresby
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.DrawingGroup> vytvořit komplexní výkresy kombinací více <xref:System.Windows.Media.Drawing> objektů do jedné složené kreslení.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.DrawingGroup> vytvořit složené z <xref:System.Windows.Media.GeometryDrawing> a <xref:System.Windows.Media.ImageDrawing> objekty. Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.  
  
 ![Objekt DrawingGroup s více výkresů](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")  
Složené kreslení, která je vytvořená pomocí DrawingGroup  
  
 Všimněte si šedého ohraničení, které znázorňuje hranice kreslení.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 Můžete použít <xref:System.Windows.Media.DrawingGroup> pro použití <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> nastavení, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, nebo <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> výkresů obsahuje. Protože <xref:System.Windows.Media.DrawingGroup> je také <xref:System.Windows.Media.Drawing>, může obsahovat jiné <xref:System.Windows.Media.DrawingGroup> objekty.  
  
 V následujícím příkladu je podobně jako v předchozím příkladu, s tím rozdílem, že používá další <xref:System.Windows.Media.DrawingGroup> objekty, které chcete použít dopady rastrového obrázku a masku krytí k některým z jeho kresby. Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.  
  
 ![Objekt DrawingGroup s více výkresů](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")  
Složené kreslení, který má více objektů DrawingGroup  
  
 Všimněte si šedého ohraničení, které znázorňuje hranice kreslení.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 Další informace o <xref:System.Windows.Media.Drawing> objekty, najdete v části [kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>  
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>  
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>  
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>  
 [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
