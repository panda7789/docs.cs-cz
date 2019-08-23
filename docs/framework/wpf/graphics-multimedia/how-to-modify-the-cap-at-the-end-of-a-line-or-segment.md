---
title: 'Postupy: Změna zakončení na konci čáry nebo segmentu'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916136"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="e6b19-102">Postupy: Změna zakončení na konci čáry nebo segmentu</span><span class="sxs-lookup"><span data-stu-id="e6b19-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="e6b19-103">Tento příklad ukazuje, jak změnit tvar na začátku nebo konci otevřeného <xref:System.Windows.Shapes.Shape> elementu.</span><span class="sxs-lookup"><span data-stu-id="e6b19-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="e6b19-104">Chcete-li změnit zakončení na začátku otevřeného <xref:System.Windows.Shapes.Shape>objektu, použijte <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> jeho vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e6b19-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="e6b19-105">Chcete-li změnit zakončení na konci otevřeného <xref:System.Windows.Shapes.Shape>objektu, použijte <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> jeho vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e6b19-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="e6b19-106">Chcete-li zobrazit dostupná zakončení řádků, <xref:System.Windows.Media.PenLineCap> Podívejte se na výčet.</span><span class="sxs-lookup"><span data-stu-id="e6b19-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e6b19-107">Tato vlastnost má vliv pouze na otevřený tvar, jako <xref:System.Windows.Shapes.Line>je <xref:System.Windows.Shapes.Polyline>,, nebo otevřený <xref:System.Windows.Shapes.Path> element.</span><span class="sxs-lookup"><span data-stu-id="e6b19-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="e6b19-108">Následující příklad kreslí čtyři <xref:System.Windows.Shapes.Polyline> prvky a používá jinou sadu tvarů na koncích každého.</span><span class="sxs-lookup"><span data-stu-id="e6b19-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6b19-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6b19-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="e6b19-110">Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="e6b19-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b19-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6b19-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
