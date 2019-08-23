---
title: 'Postupy: Vykreslení lomené čáry pomocí elementu lomené čáry'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934960"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Postupy: Vykreslení lomené čáry pomocí elementu lomené čáry
Tento příklad ukazuje, jak vykreslit lomenou čáru, což je řada propojených řádků pomocí <xref:System.Windows.Shapes.Polyline> elementu.  
  
 Chcete-li nakreslit lomenou <xref:System.Windows.Shapes.Polyline> čáru, vytvořte element <xref:System.Windows.Shapes.Polyline.Points%2A> a použijte jeho vlastnost k určení vrcholů tvaru. Nakonec pomocí <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastností a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> popište obrys lomené čáry, protože čára bez tahu není viditelná.  
  
> [!NOTE]
> Vzhledem k <xref:System.Windows.Shapes.Polyline> tomu, že element není uzavřený obrazec <xref:System.Windows.Shapes.Shape.Fill%2A> , vlastnost nemá žádný vliv, i když záměrně uzavřete obrys tvaru. Chcete-li vytvořit uzavřený obrazec <xref:System.Windows.Shapes.Shape.Fill%2A>pomocí, <xref:System.Windows.Shapes.Polygon> použijte element.  
  
 Následující příklad kreslí dva <xref:System.Windows.Shapes.Polyline> prvky <xref:System.Windows.Controls.Canvas>uvnitř.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]nástroji je platná syntaxe pro body oddělená mezerami oddělenými čárkami oddělené páry x-a y-souřadnic.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 I když tento příklad používá <xref:System.Windows.Controls.Canvas> a obsahuje lomené čáry, můžete použít prvky lomené čáry (a všechny ostatní prvky obrazce) s jakýmkoli <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje obsah, který není textový.  
  
 Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [Prvky tvaru – ukázka](https://go.microsoft.com/fwlink/?LinkID=160037)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
