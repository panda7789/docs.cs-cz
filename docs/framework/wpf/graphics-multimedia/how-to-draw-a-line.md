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
ms.openlocfilehash: 4911aea91416fb84e9a18d54c145b494737ef9dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="00ee4-102">Postupy: Vykreslení čáry</span><span class="sxs-lookup"><span data-stu-id="00ee4-102">How to: Draw a Line</span></span>
<span data-ttu-id="00ee4-103">Tento příklad ukazuje, jak kreslení čar pomocí <xref:System.Windows.Shapes.Line> elementu.</span><span class="sxs-lookup"><span data-stu-id="00ee4-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="00ee4-104">Kreslení čáry, vytvořte <xref:System.Windows.Shapes.Line> elementu.</span><span class="sxs-lookup"><span data-stu-id="00ee4-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="00ee4-105">Použijte jeho <xref:System.Windows.Shapes.Line.X1%2A> a <xref:System.Windows.Shapes.Line.Y1%2A> vlastnosti, které chcete nastavit svůj počáteční bod; a použít jeho <xref:System.Windows.Shapes.Line.X2%2A> a <xref:System.Windows.Shapes.Line.Y2%2A> vlastnosti, které chcete nastavit svůj koncový bod.</span><span class="sxs-lookup"><span data-stu-id="00ee4-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="00ee4-106">Nakonec nastavte svůj <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> protože řádek bez tahu neviditelná.</span><span class="sxs-lookup"><span data-stu-id="00ee4-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="00ee4-107">Nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> element pro řádek nemá žádný vliv, protože má řádek bez vnitřek.</span><span class="sxs-lookup"><span data-stu-id="00ee4-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="00ee4-108">Následující příklad nevykresluje tři řádky uvnitř <xref:System.Windows.Controls.Canvas> elementu.</span><span class="sxs-lookup"><span data-stu-id="00ee4-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00ee4-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="00ee4-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="00ee4-110">Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="00ee4-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ee4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="00ee4-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Line>  
 [<span data-ttu-id="00ee4-112">Ukázka elementy obrazce</span><span class="sxs-lookup"><span data-stu-id="00ee4-112">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)
