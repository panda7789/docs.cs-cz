---
title: 'Postupy: Vykreslení lomené čáry použitím elementu lomené čáry'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 2abfa29f7aca4bfc8c5f91e36fd974093a98a9e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561758"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Postupy: Vykreslení lomené čáry použitím elementu lomené čáry
Tento příklad ukazuje, jak k vykreslení čar, což je pomocí řady připojené řádky, <xref:System.Windows.Shapes.Polyline> elementu.  
  
 Kreslení čar, vytvořit <xref:System.Windows.Shapes.Polyline> elementu a použít jeho <xref:System.Windows.Shapes.Polyline.Points%2A> vlastnosti k určení vrcholy obrazce. Nakonec použijte <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti k popisu lomenou čáru popisují, protože řádek bez tahu neviditelná.  
  
> [!NOTE]
>  Protože <xref:System.Windows.Shapes.Polyline> element není uzavřený obrazec <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost nemá žádný vliv, i když úmyslně zavřete obrys tvaru. K vytvoření uzavřený obrazec s <xref:System.Windows.Shapes.Shape.Fill%2A>, používat <xref:System.Windows.Shapes.Polygon> elementu.  
  
 Následující příklad nevykresluje dva <xref:System.Windows.Shapes.Polyline> elementy uvnitř <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], platná syntaxe pro body je mezerami oddělený seznam párů textový soubor s oddělovači x - a -souřadnici y.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 I když tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala čáru lomených, můžete použít prvky lomenou čáru (a všechny ostatní elementy obrazce) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> bez textového obsahu, která podporuje.  
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Shapes.Polygon>  
 <xref:System.Windows.Shapes.Shape>  
 [Ukázka elementy obrazce](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [Přehled objektů Shape a základního kreslení ve WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
