---
title: "Mnohoúhelníky v GDI+"
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
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 740a454873976e407843c417a7b09e5a5218398d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="polygons-in-gdi"></a><span data-ttu-id="87cfa-102">Mnohoúhelníky v GDI+</span><span class="sxs-lookup"><span data-stu-id="87cfa-102">Polygons in GDI+</span></span>
<span data-ttu-id="87cfa-103">Mnohoúhelníku je uzavřený obrazec s tři nebo více rovné strany.</span><span class="sxs-lookup"><span data-stu-id="87cfa-103">A polygon is a closed shape with three or more straight sides.</span></span> <span data-ttu-id="87cfa-104">Například trojúhelníček je mnohoúhelník s tři strany, obdélníku je mnohoúhelník s čtyři strany a pětiúhelník je mnohoúhelník s pěti stranách.</span><span class="sxs-lookup"><span data-stu-id="87cfa-104">For example, a triangle is a polygon with three sides, a rectangle is a polygon with four sides, and a pentagon is a polygon with five sides.</span></span> <span data-ttu-id="87cfa-105">Následující obrázek znázorňuje několik mnohoúhelníky.</span><span class="sxs-lookup"><span data-stu-id="87cfa-105">The following illustration shows several polygons.</span></span>  
  
 <span data-ttu-id="87cfa-106">![Mnohoúhelníky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span><span class="sxs-lookup"><span data-stu-id="87cfa-106">![Polygons](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")</span></span>  
  
## <a name="drawing-a-polygon"></a><span data-ttu-id="87cfa-107">Kreslení mnohoúhelníku</span><span class="sxs-lookup"><span data-stu-id="87cfa-107">Drawing a Polygon</span></span>  
 <span data-ttu-id="87cfa-108">Kreslení mnohoúhelníku, musíte <xref:System.Drawing.Graphics> objekt, <xref:System.Drawing.Pen> objekt a pole <xref:System.Drawing.Point> (nebo <xref:System.Drawing.PointF>) objekty.</span><span class="sxs-lookup"><span data-stu-id="87cfa-108">To draw a polygon, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and an array of <xref:System.Drawing.Point> (or <xref:System.Drawing.PointF>) objects.</span></span> <span data-ttu-id="87cfa-109"><xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.DrawPolygon%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="87cfa-109">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="87cfa-110"><xref:System.Drawing.Pen> Objekt ukládá atributy, jako například šířku a barvu čáry použité k vykreslení mnohoúhelníku a pole <xref:System.Drawing.Point> objekty ukládá body připojí pomocí přímých řádky.</span><span class="sxs-lookup"><span data-stu-id="87cfa-110">The <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the polygon, and the array of <xref:System.Drawing.Point> objects stores the points to be connected by straight lines.</span></span> <span data-ttu-id="87cfa-111"><xref:System.Drawing.Pen> Objekt a pole <xref:System.Drawing.Point> jako argumenty pro předávání objektů <xref:System.Drawing.Graphics.DrawPolygon%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="87cfa-111">The <xref:System.Drawing.Pen> object and the array of <xref:System.Drawing.Point> objects are passed as arguments to the <xref:System.Drawing.Graphics.DrawPolygon%2A> method.</span></span> <span data-ttu-id="87cfa-112">Následující příklad nevykresluje zachytávání tři mnohoúhelníku.</span><span class="sxs-lookup"><span data-stu-id="87cfa-112">The following example draws a three-sided polygon.</span></span> <span data-ttu-id="87cfa-113">Všimněte si, že jsou jenom tři body v `myPointArray`: (0, 0), (50, 30) a (30, 60).</span><span class="sxs-lookup"><span data-stu-id="87cfa-113">Note that there are only three points in `myPointArray`: (0, 0), (50, 30), and (30, 60).</span></span> <span data-ttu-id="87cfa-114"><xref:System.Drawing.Graphics.DrawPolygon%2A> Metoda automaticky zavře mnohoúhelníku ve kreslení řádek ze (30, 60) zpět na výchozí bod (0, 0).</span><span class="sxs-lookup"><span data-stu-id="87cfa-114">The <xref:System.Drawing.Graphics.DrawPolygon%2A> method automatically closes the polygon by drawing a line from (30, 60) back to the starting point (0, 0).</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 <span data-ttu-id="87cfa-115">Následující obrázek znázorňuje mnohoúhelníku.</span><span class="sxs-lookup"><span data-stu-id="87cfa-115">The following illustration shows the polygon.</span></span>  
  
 <span data-ttu-id="87cfa-116">![Mnohoúhelníku](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span><span class="sxs-lookup"><span data-stu-id="87cfa-116">![Polygon](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87cfa-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="87cfa-117">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="87cfa-118">Čar, křivek a obrazců</span><span class="sxs-lookup"><span data-stu-id="87cfa-118">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="87cfa-119">Postupy: vytvoření pera</span><span class="sxs-lookup"><span data-stu-id="87cfa-119">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
