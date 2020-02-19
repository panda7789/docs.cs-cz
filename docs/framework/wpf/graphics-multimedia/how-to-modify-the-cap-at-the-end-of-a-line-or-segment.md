---
title: 'Postupy: Změna CAP na konci čáry nebo segmentu'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 5f755d7b4d1682755ea461121f91c0666d450ad1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452776"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="a2eea-102">Postupy: Změna CAP na konci čáry nebo segmentu</span><span class="sxs-lookup"><span data-stu-id="a2eea-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="a2eea-103">Tento příklad ukazuje, jak změnit tvar na začátku nebo konci elementu Open <xref:System.Windows.Shapes.Shape>.</span><span class="sxs-lookup"><span data-stu-id="a2eea-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="a2eea-104">Chcete-li změnit zakončení na začátku otevřeného <xref:System.Windows.Shapes.Shape>, použijte jeho vlastnost <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2eea-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="a2eea-105">Chcete-li změnit zakončení na konci otevřeného <xref:System.Windows.Shapes.Shape>, použijte jeho vlastnost <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2eea-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="a2eea-106">Chcete-li zobrazit dostupná zakončení řádků, přečtěte si <xref:System.Windows.Media.PenLineCap> výčtu.</span><span class="sxs-lookup"><span data-stu-id="a2eea-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2eea-107">Tato vlastnost má vliv pouze na otevřený tvar, například <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Polyline>nebo element Open <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="a2eea-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="a2eea-108">Následující příklad kreslí čtyři prvky <xref:System.Windows.Shapes.Polyline> a používá jinou sadu tvarů na koncích každého.</span><span class="sxs-lookup"><span data-stu-id="a2eea-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2eea-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2eea-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="a2eea-110">Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="a2eea-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2eea-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2eea-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
