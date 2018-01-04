---
title: "Postupy: Kreslení základních čar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64661bbdcb267e2f2ce33b8a8db2ab2aac9a86f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-cardinal-splines"></a><span data-ttu-id="cb9e5-102">Postupy: Kreslení základních čar</span><span class="sxs-lookup"><span data-stu-id="cb9e5-102">How to: Draw Cardinal Splines</span></span>
<span data-ttu-id="cb9e5-103">Spojnice křivky je křivky, které procházejí danou sadu body bez problémů.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-103">A cardinal spline is a curve that passes smoothly through a given set of points.</span></span> <span data-ttu-id="cb9e5-104">Kreslení křivky mohutnosti, vytvořit <xref:System.Drawing.Graphics> objektu a předejte adresu v poli body <xref:System.Drawing.Graphics.DrawCurve%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-104">To draw a cardinal spline, create a <xref:System.Drawing.Graphics> object and pass the address of an array of points to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span>  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a><span data-ttu-id="cb9e5-105">Kreslení základních křivky ve tvaru zvonu</span><span class="sxs-lookup"><span data-stu-id="cb9e5-105">Drawing a Bell-Shaped Cardinal Spline</span></span>  
  
-   <span data-ttu-id="cb9e5-106">Následující příklad nevykresluje mohutnosti křivkový se ve tvaru zvonu, které procházejí pět určené body.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-106">The following example draws a bell-shaped cardinal spline that passes through five designated points.</span></span> <span data-ttu-id="cb9e5-107">Následující obrázek znázorňuje křivku a pět bodů.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-107">The following illustration shows the curve and five points.</span></span>  
  
     <span data-ttu-id="cb9e5-108">![Křivkový základních](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")</span><span class="sxs-lookup"><span data-stu-id="cb9e5-108">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a><span data-ttu-id="cb9e5-109">Kreslení uzavřené křivky základních</span><span class="sxs-lookup"><span data-stu-id="cb9e5-109">Drawing a Closed Cardinal Spline</span></span>  
  
-   <span data-ttu-id="cb9e5-110">Použití <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metodu <xref:System.Drawing.Graphics> třída k vykreslení uzavřené křivky mohutnosti.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-110">Use the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method of the <xref:System.Drawing.Graphics> class to draw a closed cardinal spline.</span></span> <span data-ttu-id="cb9e5-111">V uzavřené křivky mohutnosti křivku pokračuje pomocí posledního bodu v poli a připojí s prvním bodem v poli.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-111">In a closed cardinal spline, the curve continues through the last point in the array and connects with the first point in the array.</span></span> <span data-ttu-id="cb9e5-112">Následující příklad nevykresluje uzavřené křivku mohutnosti, která předá prostřednictvím šesti určené bodů.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-112">The following example draws a closed cardinal spline that passes through six designated points.</span></span> <span data-ttu-id="cb9e5-113">Následující obrázek znázorňuje uzavřené křivky společně s šest bodů.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-113">The following illustration shows the closed spline along with the six points.</span></span>  
  
 <span data-ttu-id="cb9e5-114">![Křivkový základních](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")</span><span class="sxs-lookup"><span data-stu-id="cb9e5-114">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a><span data-ttu-id="cb9e5-115">Změna ohybem základní křivky</span><span class="sxs-lookup"><span data-stu-id="cb9e5-115">Changing the Bend of a Cardinal Spline</span></span>  
  
-   <span data-ttu-id="cb9e5-116">Změnit způsob křivky mohutnosti zatáčkách předáním pnutí argument <xref:System.Drawing.Graphics.DrawCurve%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-116">Change the way a cardinal spline bends by passing a tension argument to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span> <span data-ttu-id="cb9e5-117">Následující příklad nevykresluje tři základní křivky vyhlazení, které procházejí stejnou sadu body.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-117">The following example draws three cardinal splines that pass through the same set of points.</span></span> <span data-ttu-id="cb9e5-118">Následující obrázek znázorňuje tři křivky spolu s příslušnými hodnotami pnutí.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-118">The following illustration shows the three splines along with their tension values.</span></span> <span data-ttu-id="cb9e5-119">Všimněte si, že 0 po hodnotu napětí body jsou připojena linkami přímých.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-119">Note that when the tension is 0, the points are connected by straight lines.</span></span>  
  
 <span data-ttu-id="cb9e5-120">![Křivkový základních](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")</span><span class="sxs-lookup"><span data-stu-id="cb9e5-120">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb9e5-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cb9e5-121">Compiling the Code</span></span>  
 <span data-ttu-id="cb9e5-122">V předchozích příkladech jsou navrženy pro používání s formuláři Windows a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-122">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9e5-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb9e5-123">See Also</span></span>  
 [<span data-ttu-id="cb9e5-124">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="cb9e5-124">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="cb9e5-125">Sestavování a kreslení křivek</span><span class="sxs-lookup"><span data-stu-id="cb9e5-125">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
