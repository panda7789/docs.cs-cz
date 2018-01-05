---
title: "Postupy: Použití kresby jako zdroje obrázku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], drawings [WPF], as image sources
- image sources [WPF], drawings
- drawings [WPF], as image sources
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e0fe8f7d3633143348693c95d92dd2715bd0442
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
