---
title: "Postupy: Změna CAP na konci čáry nebo segmentu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e062b82e698a99705a2b06588aa9aae3a0c93157
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="8b3f7-102">Postupy: Změna CAP na konci čáry nebo segmentu</span><span class="sxs-lookup"><span data-stu-id="8b3f7-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="8b3f7-103">Tento příklad ukazuje, jak upravit tvaru na začátku nebo na konci otevřenou <xref:System.Windows.Shapes.Shape> elementu.</span><span class="sxs-lookup"><span data-stu-id="8b3f7-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="8b3f7-104">Chcete-li změnit zakončení na začátku otevřenou <xref:System.Windows.Shapes.Shape>, použijte jeho <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8b3f7-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="8b3f7-105">Chcete-li změnit zakončení na konci otevřenou <xref:System.Windows.Shapes.Shape>, použijte jeho <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8b3f7-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="8b3f7-106">Chcete-li zobrazit dostupné čar, najdete v článku <xref:System.Windows.Media.PenLineCap> výčtu.</span><span class="sxs-lookup"><span data-stu-id="8b3f7-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b3f7-107">Tato vlastnost ovlivňuje pouze otevřený tvar, například <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Polyline>, nebo otevřenou <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="8b3f7-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="8b3f7-108">Následující příklad nevykresluje čtyři <xref:System.Windows.Shapes.Polyline> elementy a používá jinou sadu tvarů na koncích jednotlivých.</span><span class="sxs-lookup"><span data-stu-id="8b3f7-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b3f7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b3f7-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="8b3f7-110">Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="8b3f7-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b3f7-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b3f7-111">See Also</span></span>  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
