---
title: 'Postupy: Vykreslení čáry'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a803c1be01086ca8911ef4cc33bd67697239e2c0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452945"
---
# <a name="how-to-draw-a-line"></a>Postupy: Vykreslení čáry
Tento příklad ukazuje, jak kreslit čáry pomocí elementu <xref:System.Windows.Shapes.Line>.  
  
 Chcete-li nakreslit čáru, vytvořte <xref:System.Windows.Shapes.Line> element. Pro nastavení počátečního bodu použijte jeho <xref:System.Windows.Shapes.Line.X1%2A> a vlastnosti <xref:System.Windows.Shapes.Line.Y1%2A>. a k nastavení jeho koncového bodu použijte jeho <xref:System.Windows.Shapes.Line.X2%2A> a vlastnosti <xref:System.Windows.Shapes.Line.Y2%2A>. Nakonec nastavte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>, protože čára bez tahu není viditelná.  
  
 Nastavení elementu <xref:System.Windows.Shapes.Shape.Fill%2A> pro řádek nemá žádný účinek, protože řádek nemá žádnou vnitřní hodnotu.  
  
 Následující příklad kreslí tři čáry uvnitř prvku <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Shapes.Line>
- [Prvky tvaru – ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
