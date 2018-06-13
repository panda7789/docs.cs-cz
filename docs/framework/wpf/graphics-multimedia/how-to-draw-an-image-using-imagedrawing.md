---
title: 'Postupy: Vykreslení obrázku pomocí ImageDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: 2c7771f841fb3b600d4790eb4d484b0a09c45dd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559876"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>Postupy: Vykreslení obrázku pomocí ImageDrawing
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.ImageDrawing> kreslení obrázku. <xref:System.Windows.Media.ImageDrawing> Umožňuje můžete zobrazit <xref:System.Windows.Media.ImageSource> s <xref:System.Windows.Media.DrawingBrush>, <xref:System.Windows.Media.DrawingImage>, nebo <xref:System.Windows.Media.Visual>. Kreslení obrázku, vytvoříte <xref:System.Windows.Media.ImageDrawing> a nastavit jeho <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> a <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> vlastnosti. <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType> Vlastnost určuje bitovou kopii k vykreslení a <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType> vlastnost určuje umístění a velikost každé bitové kopie.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří složené kreslení pomocí čtyři <xref:System.Windows.Media.ImageDrawing> objekty. Tento příklad vytvoří na následujícím obrázku:  
  
 ![Několik objektů DrawingImage](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
Čtyři ImageDrawing objekty  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 Příklad zobrazuje jednoduchý způsob, jak zobrazit obrázek bez použití <xref:System.Windows.Media.ImageDrawing>, najdete v části [pomocí bitové kopie elementu](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Freezable.Freeze%2A>  
 <xref:System.Windows.Controls.Image>  
 [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [PresentationOptions:Freeze – atribut](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
