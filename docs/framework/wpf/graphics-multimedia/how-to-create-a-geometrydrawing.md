---
title: 'Postupy: Vytvoření objektu GeometryDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: 6eb604a8446000ef308c2b5a99480fb6a476c949
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373813"
---
# <a name="how-to-create-a-geometrydrawing"></a>Postupy: Vytvoření objektu GeometryDrawing
Tento příklad ukazuje, jak vytvořit a zobrazit <xref:System.Windows.Media.GeometryDrawing>. A <xref:System.Windows.Media.GeometryDrawing> umožňuje vytvoření tvaru pomocí výplň a osnovy tím, že přidružíte <xref:System.Windows.Media.Pen> a <xref:System.Windows.Media.Brush> s <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Popisuje strukturu obrazce <xref:System.Windows.Media.GeometryDrawing.Brush%2A> popisuje vyplnění obrazce a <xref:System.Windows.Media.GeometryDrawing.Pen%2A> popisuje obrysu obrazce.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.GeometryDrawing> k vykreslení obrazce. Tvar je popsán <xref:System.Windows.Media.GeometryGroup> a dva <xref:System.Windows.Media.EllipseGeometry> objekty. Vnitřní obrazce vymalováním s <xref:System.Windows.Media.LinearGradientBrush> a obrysu je vykreslen pomocí <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>. <xref:System.Windows.Media.GeometryDrawing> Se zobrazí pomocí <xref:System.Windows.Media.ImageDrawing> a <xref:System.Windows.Controls.Image> elementu.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 Následující obrázek znázorňuje výsledný <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![GeometryDrawing dvě symbol tří teček](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 Chcete-li vytvořit složitější kreslení, můžete kombinovat více nakreslených objektů do jedné složeného kreslení pomocí <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.DrawingGroup>
- [Přehled nakreslených objektů](drawing-objects-overview.md)
- [Přehled geometrie](geometry-overview.md)
- [Vytvoření kompozitní kresby](how-to-create-a-composite-drawing.md)
