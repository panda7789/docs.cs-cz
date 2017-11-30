---
title: "Otevřené a uzavřené křivky v GDI+"
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
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 14da32848978299a0d0651596bbfbfe17c2e0d53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="open-and-closed-curves-in-gdi"></a><span data-ttu-id="0e0cd-102">Otevřené a uzavřené křivky v GDI+</span><span class="sxs-lookup"><span data-stu-id="0e0cd-102">Open and Closed Curves in GDI+</span></span>
<span data-ttu-id="0e0cd-103">Následující obrázek znázorňuje dvě: jeden otevřete a jeden zavřené.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-103">The following illustration shows two curves: one open and one closed.</span></span>  
  
 <span data-ttu-id="0e0cd-104">![Otevřené a uzavřené křivky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span><span class="sxs-lookup"><span data-stu-id="0e0cd-104">![Open & Closed curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span></span>  
  
## <a name="managed-interface-for-curves"></a><span data-ttu-id="0e0cd-105">Spravovaná rozhraní pro křivek</span><span class="sxs-lookup"><span data-stu-id="0e0cd-105">Managed Interface for Curves</span></span>  
 <span data-ttu-id="0e0cd-106">Uzavřené křivky mít vnitřním a proto může být vyplněna štětcem.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-106">Closed curves have an interior and therefore can be filled with a brush.</span></span> <span data-ttu-id="0e0cd-107"><xref:System.Drawing.Graphics> Třídy v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje následující metody pro naplnění uzavřené tvarů a křivek: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, a <xref:System.Drawing.Graphics.FillRegion%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-107">The <xref:System.Drawing.Graphics> class in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the following methods for filling closed shapes and curves: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, and <xref:System.Drawing.Graphics.FillRegion%2A>.</span></span> <span data-ttu-id="0e0cd-108">Při každém volání jednoho z těchto metod, je nutné předat jeden z typů konkrétní štětce (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, nebo <xref:System.Drawing.Drawing2D.PathGradientBrush>) jako argument.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-108">Whenever you call one of these methods, you must pass one of the specific brush types (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, or <xref:System.Drawing.Drawing2D.PathGradientBrush>) as an argument.</span></span>  
  
 <span data-ttu-id="0e0cd-109"><xref:System.Drawing.Graphics.FillPie%2A> Metoda je Pomocníka pro <xref:System.Drawing.Graphics.DrawArc%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-109">The <xref:System.Drawing.Graphics.FillPie%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawArc%2A> method.</span></span> <span data-ttu-id="0e0cd-110">Stejně jako <xref:System.Drawing.Graphics.DrawArc%2A> metoda vykreslí část obrys elipsy, <xref:System.Drawing.Graphics.FillPie%2A> metoda doplní část vnitřek elipsy.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-110">Just as the <xref:System.Drawing.Graphics.DrawArc%2A> method draws a portion of the outline of an ellipse, the <xref:System.Drawing.Graphics.FillPie%2A> method fills a portion of the interior of an ellipse.</span></span> <span data-ttu-id="0e0cd-111">Následující příklad nakreslí oblouk a výplní odpovídající část vnitřek se třemi tečkami:</span><span class="sxs-lookup"><span data-stu-id="0e0cd-111">The following example draws an arc and fills the corresponding portion of the interior of the ellipse:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 <span data-ttu-id="0e0cd-112">Následující obrázek znázorňuje oblouk a vyplněné výseč.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-112">The following illustration shows the arc and the filled pie.</span></span>  
  
 <span data-ttu-id="0e0cd-113">![Otevřené a uzavřené křivky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span><span class="sxs-lookup"><span data-stu-id="0e0cd-113">![Open & Closed curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span></span>  
  
 <span data-ttu-id="0e0cd-114"><xref:System.Drawing.Graphics.FillClosedCurve%2A> Metoda je Pomocníka pro <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-114">The <xref:System.Drawing.Graphics.FillClosedCurve%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method.</span></span> <span data-ttu-id="0e0cd-115">Obě metody automaticky uzavřít křivku připojením koncový bod se počáteční bod.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-115">Both methods automatically close the curve by connecting the ending point to the starting point.</span></span> <span data-ttu-id="0e0cd-116">Následující příklad nakreslí křivku, které procházejí (0, 0), (60, 20) a (40, 50).</span><span class="sxs-lookup"><span data-stu-id="0e0cd-116">The following example draws a curve that passes through (0, 0), (60, 20), and (40, 50).</span></span> <span data-ttu-id="0e0cd-117">Potom automaticky zavře křivku připojením (40, 50) do výchozího bodu (0, 0), a vnitřní je vyplněn plnou barvou.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-117">Then, the curve is automatically closed by connecting (40, 50) to the starting point (0, 0), and the interior is filled with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <span data-ttu-id="0e0cd-118"><xref:System.Drawing.Graphics.FillPath%2A> Metoda doplní vnitřek samostatné části cesty.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-118">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the interiors of the separate pieces of a path.</span></span> <span data-ttu-id="0e0cd-119">Pokud není část cesty formuláři uzavřené křivky nebo tvaru, <xref:System.Drawing.Graphics.FillPath%2A> metody se automaticky zavře tuto část cesty před jeho naplnění.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-119">If a piece of a path doesn't form a closed curve or shape, the <xref:System.Drawing.Graphics.FillPath%2A> method automatically closes that piece of the path before filling it.</span></span> <span data-ttu-id="0e0cd-120">Následující příklad nevykresluje a výplní cestu, která se skládá z oblouk, křivky mohutnosti, řetězec a výsečový:</span><span class="sxs-lookup"><span data-stu-id="0e0cd-120">The following example draws and fills a path that consists of an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 <span data-ttu-id="0e0cd-121">Následující obrázek ukazuje cestu s i bez plné výplně.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-121">The following illustration shows the path with and without the solid fill.</span></span> <span data-ttu-id="0e0cd-122">Všimněte si, že je text v řetězci uvedené, ale není vyplněno, pomocí <xref:System.Drawing.Graphics.DrawPath%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-122">Note that the text in the string is outlined, but not filled, by the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="0e0cd-123">Je <xref:System.Drawing.Graphics.FillPath%2A> metoda, která vybarví vnitřek znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="0e0cd-123">It is the <xref:System.Drawing.Graphics.FillPath%2A> method that paints the interiors of the characters in the string.</span></span>  
  
 <span data-ttu-id="0e0cd-124">![Řetězec cesty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span><span class="sxs-lookup"><span data-stu-id="0e0cd-124">![String in a path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e0cd-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e0cd-125">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [<span data-ttu-id="0e0cd-126">Čar, křivek a obrazců</span><span class="sxs-lookup"><span data-stu-id="0e0cd-126">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="0e0cd-127">Postupy: vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="0e0cd-127">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="0e0cd-128">Sestavování a kreslení cest</span><span class="sxs-lookup"><span data-stu-id="0e0cd-128">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
