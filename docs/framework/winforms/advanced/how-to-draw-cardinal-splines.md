---
title: 'Postupy: Kreslení základních křivek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 2f03177bf97936a2ca9558972d4d82fa3e07463c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204949"
---
# <a name="how-to-draw-cardinal-splines"></a><span data-ttu-id="dcfcf-102">Postupy: Kreslení základních křivek</span><span class="sxs-lookup"><span data-stu-id="dcfcf-102">How to: Draw Cardinal Splines</span></span>
<span data-ttu-id="dcfcf-103">Křivky mohutnosti je křivku plynule prochází danou sadu body.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-103">A cardinal spline is a curve that passes smoothly through a given set of points.</span></span> <span data-ttu-id="dcfcf-104">K nakreslení křivky mohutnosti, vytvořit <xref:System.Drawing.Graphics> objektu a předat adresu pole odkazuje na <xref:System.Drawing.Graphics.DrawCurve%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-104">To draw a cardinal spline, create a <xref:System.Drawing.Graphics> object and pass the address of an array of points to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span>  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a><span data-ttu-id="dcfcf-105">Kreslení ve tvaru zvonu křivky mohutnosti</span><span class="sxs-lookup"><span data-stu-id="dcfcf-105">Drawing a Bell-Shaped Cardinal Spline</span></span>  
  
-   <span data-ttu-id="dcfcf-106">Následující příklad kreslení ve tvaru zvonu základní křivka vyhlazení, který prochází pět bodů určené.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-106">The following example draws a bell-shaped cardinal spline that passes through five designated points.</span></span> <span data-ttu-id="dcfcf-107">Následující obrázek znázorňuje křivky a pět bodů.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-107">The following illustration shows the curve and five points.</span></span>  
  
     ![Diagram zobrazující průběh křivky mohutnosti ve tvaru zvonu.](./media/how-to-draw-cardinal-splines/bell-shaped-cardinal-spline.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a><span data-ttu-id="dcfcf-109">Kreslení uzavřené křivky mohutnosti</span><span class="sxs-lookup"><span data-stu-id="dcfcf-109">Drawing a Closed Cardinal Spline</span></span>  
  
-   <span data-ttu-id="dcfcf-110">Použití <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metodu <xref:System.Drawing.Graphics> třídy kreslení uzavřené křivky mohutnosti.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-110">Use the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method of the <xref:System.Drawing.Graphics> class to draw a closed cardinal spline.</span></span> <span data-ttu-id="dcfcf-111">V uzavřené křivky mohutnosti křivka pokračuje přes poslední bod v poli a připojí se s prvním bodem v poli.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-111">In a closed cardinal spline, the curve continues through the last point in the array and connects with the first point in the array.</span></span> <span data-ttu-id="dcfcf-112">Následující příklad kreslení uzavřené vyhlazení, který prochází šest určené body.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-112">The following example draws a closed cardinal spline that passes through six designated points.</span></span> <span data-ttu-id="dcfcf-113">Následující obrázek znázorňuje uzavřené křivky spolu s šest bodů:</span><span class="sxs-lookup"><span data-stu-id="dcfcf-113">The following illustration shows the closed spline along with the six points:</span></span>  
  
 ![Diagram zobrazující průběh uzavřené křivky mohutnosti.](./media/how-to-draw-cardinal-splines/closed-cardinal-spine.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a><span data-ttu-id="dcfcf-115">Změna ohyb křivky mohutnosti</span><span class="sxs-lookup"><span data-stu-id="dcfcf-115">Changing the Bend of a Cardinal Spline</span></span>  
  
-   <span data-ttu-id="dcfcf-116">Změnit způsob předáním napětí argument zatáčkách křivky mohutnosti <xref:System.Drawing.Graphics.DrawCurve%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-116">Change the way a cardinal spline bends by passing a tension argument to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span> <span data-ttu-id="dcfcf-117">Následující příklad kreslení tři křivky mohutnosti, které prochází stejnou sadu body.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-117">The following example draws three cardinal splines that pass through the same set of points.</span></span> <span data-ttu-id="dcfcf-118">Následující obrázek znázorňuje tři křivky spolu s příslušnými hodnotami napětí.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-118">The following illustration shows the three splines along with their tension values.</span></span> <span data-ttu-id="dcfcf-119">Všimněte si, že 0 po hodnotu napětí body jsou spojeny čarami přímo.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-119">Note that when the tension is 0, the points are connected by straight lines.</span></span>  
  
 ![Diagram znázorňující tři křivky mohutnosti.](./media/how-to-draw-cardinal-splines/three-cardinal-splines.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dcfcf-121">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="dcfcf-121">Compiling the Code</span></span>  
 <span data-ttu-id="dcfcf-122">Předchozí příklady jsou určeny k použití pomocí Windows Forms a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="dcfcf-122">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcfcf-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcfcf-123">See also</span></span>

- [<span data-ttu-id="dcfcf-124">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="dcfcf-124">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="dcfcf-125">Sestavování a kreslení křivek</span><span class="sxs-lookup"><span data-stu-id="dcfcf-125">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
