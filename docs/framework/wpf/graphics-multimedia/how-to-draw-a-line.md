---
title: 'Postupy: Vykreslení čáry'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: 1093e754912cd3ee3b8474ed7d190913079a9f9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-line"></a>Postupy: Vykreslení čáry
Tento příklad ukazuje, jak kreslení čar pomocí <xref:System.Windows.Shapes.Line> elementu.  
  
 Kreslení čáry, vytvořte <xref:System.Windows.Shapes.Line> elementu. Použijte jeho <xref:System.Windows.Shapes.Line.X1%2A> a <xref:System.Windows.Shapes.Line.Y1%2A> vlastnosti, které chcete nastavit svůj počáteční bod; a použít jeho <xref:System.Windows.Shapes.Line.X2%2A> a <xref:System.Windows.Shapes.Line.Y2%2A> vlastnosti, které chcete nastavit svůj koncový bod. Nakonec nastavte svůj <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> protože řádek bez tahu neviditelná.  
  
 Nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> element pro řádek nemá žádný vliv, protože má řádek bez vnitřek.  
  
 Následující příklad nevykresluje tři řádky uvnitř <xref:System.Windows.Controls.Canvas> elementu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Shapes.Line>  
 [Ukázka elementy obrazce](http://go.microsoft.com/fwlink/?LinkID=160037)
