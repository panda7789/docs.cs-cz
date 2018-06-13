---
title: 'Postupy: Vytvoření objektu GeometryDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: 713cecd10bfa62494c50c96cb8cbece69f7e5660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560657"
---
# <a name="how-to-create-a-geometrydrawing"></a>Postupy: Vytvoření objektu GeometryDrawing
Tento příklad ukazuje, jak vytvořit a zobrazit <xref:System.Windows.Media.GeometryDrawing>. A <xref:System.Windows.Media.GeometryDrawing> umožňuje vytvářet obrazce s výplň a tou druhou je tím, že přidružíte <xref:System.Windows.Media.Pen> a <xref:System.Windows.Media.Brush> s <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Popisuje strukturu tvaru, <xref:System.Windows.Media.GeometryDrawing.Brush%2A> popisuje výplň obrazce a <xref:System.Windows.Media.GeometryDrawing.Pen%2A> popisuje obrysu obrazce.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.GeometryDrawing> k vykreslení obrazce. Tvar, který je popsán <xref:System.Windows.Media.GeometryGroup> a dvě <xref:System.Windows.Media.EllipseGeometry> objekty. Vykreslení vnitřního tvaru s <xref:System.Windows.Media.LinearGradientBrush> a jeho obrys vykreslením s <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>. <xref:System.Windows.Media.GeometryDrawing> Se zobrazí pomocí <xref:System.Windows.Media.ImageDrawing> a <xref:System.Windows.Controls.Image> elementu.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 Následující obrázek znázorňuje výsledná <xref:System.Windows.Media.GeometryDrawing>.  
  
 ![Objekt GeometryDrawing sestávající ze dvou výpustky](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 Chcete-li vytvořit složitější kresby, můžete kombinovat více kreslení objektů do jedné složené kreslení pomocí <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.DrawingGroup>  
 [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Vytvoření kompozitní kresby](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
