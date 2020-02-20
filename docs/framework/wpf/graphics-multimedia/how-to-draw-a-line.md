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
# <a name="how-to-draw-a-line"></a><span data-ttu-id="9408b-102">Postupy: Vykreslení čáry</span><span class="sxs-lookup"><span data-stu-id="9408b-102">How to: Draw a Line</span></span>
<span data-ttu-id="9408b-103">Tento příklad ukazuje, jak kreslit čáry pomocí elementu <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="9408b-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="9408b-104">Chcete-li nakreslit čáru, vytvořte <xref:System.Windows.Shapes.Line> element.</span><span class="sxs-lookup"><span data-stu-id="9408b-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="9408b-105">Pro nastavení počátečního bodu použijte jeho <xref:System.Windows.Shapes.Line.X1%2A> a vlastnosti <xref:System.Windows.Shapes.Line.Y1%2A>. a k nastavení jeho koncového bodu použijte jeho <xref:System.Windows.Shapes.Line.X2%2A> a vlastnosti <xref:System.Windows.Shapes.Line.Y2%2A>.</span><span class="sxs-lookup"><span data-stu-id="9408b-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="9408b-106">Nakonec nastavte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>, protože čára bez tahu není viditelná.</span><span class="sxs-lookup"><span data-stu-id="9408b-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="9408b-107">Nastavení elementu <xref:System.Windows.Shapes.Shape.Fill%2A> pro řádek nemá žádný účinek, protože řádek nemá žádnou vnitřní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9408b-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="9408b-108">Následující příklad kreslí tři čáry uvnitř prvku <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="9408b-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9408b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="9408b-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="9408b-110">Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="9408b-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9408b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="9408b-111">See also</span></span>

- <xref:System.Windows.Shapes.Line>
- [<span data-ttu-id="9408b-112">Prvky tvaru – ukázka</span><span class="sxs-lookup"><span data-stu-id="9408b-112">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
