---
title: 'Postupy: Vykreslení čáry'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: c11dfb9523834ec2e622cb2e62bd6982a1a78fd4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143517"
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="26032-102">Postupy: Vykreslení čáry</span><span class="sxs-lookup"><span data-stu-id="26032-102">How to: Draw a Line</span></span>
<span data-ttu-id="26032-103">Tento příklad ukazuje, jak s použitím kreslení čar <xref:System.Windows.Shapes.Line> elementu.</span><span class="sxs-lookup"><span data-stu-id="26032-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="26032-104">Chcete-li nakreslit čáru, vytvořte <xref:System.Windows.Shapes.Line> elementu.</span><span class="sxs-lookup"><span data-stu-id="26032-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="26032-105">Použijte jeho <xref:System.Windows.Shapes.Line.X1%2A> a <xref:System.Windows.Shapes.Line.Y1%2A> vlastnosti, které chcete nastavit jeho počáteční bod; a použít jeho <xref:System.Windows.Shapes.Line.X2%2A> a <xref:System.Windows.Shapes.Line.Y2%2A> vlastnosti a nastavte její koncový bod.</span><span class="sxs-lookup"><span data-stu-id="26032-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="26032-106">Nakonec nastavte svůj <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vzhledem k tomu, že je neviditelný řádek bez tah.</span><span class="sxs-lookup"><span data-stu-id="26032-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="26032-107">Nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> – element pro řádek nemá žádný účinek, protože nemá žádné vnitřní řádku.</span><span class="sxs-lookup"><span data-stu-id="26032-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="26032-108">Následující příklad nakreslí tři řádky uvnitř <xref:System.Windows.Controls.Canvas> elementu.</span><span class="sxs-lookup"><span data-stu-id="26032-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26032-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="26032-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="26032-110">V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="26032-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26032-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26032-111">See also</span></span>

- <xref:System.Windows.Shapes.Line>
- [<span data-ttu-id="26032-112">Ukázka elementy obrazce</span><span class="sxs-lookup"><span data-stu-id="26032-112">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
