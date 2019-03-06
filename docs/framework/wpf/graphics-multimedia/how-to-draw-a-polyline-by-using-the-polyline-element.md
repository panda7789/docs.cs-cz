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
ms.openlocfilehash: 35981f6d5a47ea5d5e024efe714b52103938eddf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378175"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Postupy: Vykreslení lomené čáry použitím elementu lomené čáry
Tento příklad ukazuje způsob vykreslení lomené čáry, která je řada spojené čáry pomocí <xref:System.Windows.Shapes.Polyline> elementu.  
  
 Vykreslení lomené čáry, vytvořit <xref:System.Windows.Shapes.Polyline> elementu a použijte jeho <xref:System.Windows.Shapes.Polyline.Points%2A> vlastnosti a určit tak vrcholů obrazce. Nakonec použijte <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastností, které popisují lomenou čáru popisují, protože je neviditelný řádek bez tah.  
  
> [!NOTE]
>  Protože <xref:System.Windows.Shapes.Polyline> element není uzavřený obrazec <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost nemá žádný účinek, i když záměrně zavřete Obrys obrazce. K vytvoření zavřeného tvaru pomocí <xref:System.Windows.Shapes.Shape.Fill%2A>, použijte <xref:System.Windows.Shapes.Polygon> elementu.  
  
 Následující příklad nakreslí dva <xref:System.Windows.Shapes.Polyline> elementů v rámci <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], platnou syntaxi pro body je mezerami oddělený seznam párů oddělených čárkou x a y souřadnice.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala čáru lomených, můžete použít prvky lomenou čáru (a všechny ostatní prvky tvar) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje netextový obsah.  
  
 V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Ukázka elementy obrazce](https://go.microsoft.com/fwlink/?LinkID=160037)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
