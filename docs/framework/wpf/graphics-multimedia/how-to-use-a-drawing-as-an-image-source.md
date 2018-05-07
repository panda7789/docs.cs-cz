---
title: 'Postupy: Použití kresby jako zdroje obrázku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: 7da8a2a594b0562667aaf417d736159d98818a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>Postupy: Použití kresby jako zdroje obrázku
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Drawing> jako <xref:System.Windows.Controls.Image.Source%2A> pro <xref:System.Windows.Controls.Image> ovládacího prvku. K zobrazení <xref:System.Windows.Media.Drawing> s <xref:System.Windows.Controls.Image> řídit, použijte <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> ovládacího prvku <xref:System.Windows.Controls.Image.Source%2A> a nastavte <xref:System.Windows.Media.DrawingImage> objektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> vlastnost kreslení chcete zobrazit.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.DrawingImage> a <xref:System.Windows.Controls.Image> ovládacího prvku pro zobrazení <xref:System.Windows.Media.GeometryDrawing>. Tento příklad vytvoří následující výstup:  
  
 ![Objekt GeometryDrawing sestávající ze dvou výpustky](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [Vykreslení obrázku pomocí ImageDrawing](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)  
 [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Přehled zablokovatelných objektů](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [PresentationOptions:Freeze – atribut](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
