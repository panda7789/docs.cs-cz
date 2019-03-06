---
title: 'Postupy: Použití kresby jako zdroje obrázku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
ms.openlocfilehash: 07659463a3fec9b962f7b4bb255ed065d544d954
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351733"
---
# <a name="how-to-use-a-drawing-as-an-image-source"></a>Postupy: Použití kresby jako zdroje obrázku
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Drawing> jako <xref:System.Windows.Controls.Image.Source%2A> pro <xref:System.Windows.Controls.Image> ovládacího prvku. K zobrazení <xref:System.Windows.Media.Drawing> s <xref:System.Windows.Controls.Image> řídit, použijte <xref:System.Windows.Media.DrawingImage> jako <xref:System.Windows.Controls.Image> ovládacího prvku <xref:System.Windows.Controls.Image.Source%2A> a nastavit <xref:System.Windows.Media.DrawingImage> objektu <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=nameWithType> vlastnost výkresu, které chcete zobrazit.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.DrawingImage> a <xref:System.Windows.Controls.Image> ovládací prvek pro zobrazení <xref:System.Windows.Media.GeometryDrawing>. Tento příklad vytvoří následující výstup:  
  
 ![GeometryDrawing dvě symbol tří teček](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Freezable.Freeze%2A>
- [Vykreslení obrázku pomocí ImageDrawing](how-to-draw-an-image-using-imagedrawing.md)
- [Přehled nakreslených objektů](drawing-objects-overview.md)
- [Přehled zablokovatelných objektů](../advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze – atribut](../advanced/presentationoptions-freeze-attribute.md)
