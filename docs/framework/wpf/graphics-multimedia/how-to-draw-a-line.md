---
title: "Postupy: Vykreslení čáry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88d667e8654f72226dc609a14aec650effe2d5c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="14055-102">Postupy: Vykreslení čáry</span><span class="sxs-lookup"><span data-stu-id="14055-102">How to: Draw a Line</span></span>
<span data-ttu-id="14055-103">Tento příklad ukazuje, jak kreslení čar pomocí <xref:System.Windows.Shapes.Line> elementu.</span><span class="sxs-lookup"><span data-stu-id="14055-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="14055-104">Kreslení čáry, vytvořte <xref:System.Windows.Shapes.Line> elementu.</span><span class="sxs-lookup"><span data-stu-id="14055-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="14055-105">Použijte jeho <xref:System.Windows.Shapes.Line.X1%2A> a <xref:System.Windows.Shapes.Line.Y1%2A> vlastnosti, které chcete nastavit svůj počáteční bod; a použít jeho <xref:System.Windows.Shapes.Line.X2%2A> a <xref:System.Windows.Shapes.Line.Y2%2A> vlastnosti, které chcete nastavit svůj koncový bod.</span><span class="sxs-lookup"><span data-stu-id="14055-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="14055-106">Nakonec nastavte svůj <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> protože řádek bez tahu neviditelná.</span><span class="sxs-lookup"><span data-stu-id="14055-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="14055-107">Nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> element pro řádek nemá žádný vliv, protože má řádek bez vnitřek.</span><span class="sxs-lookup"><span data-stu-id="14055-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="14055-108">Následující příklad nevykresluje tři řádky uvnitř <xref:System.Windows.Controls.Canvas> elementu.</span><span class="sxs-lookup"><span data-stu-id="14055-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14055-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="14055-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="14055-110">Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="14055-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14055-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="14055-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Line>  
 [<span data-ttu-id="14055-112">Ukázka elementy obrazce</span><span class="sxs-lookup"><span data-stu-id="14055-112">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)
