---
title: Otevřené a uzavřené křivky v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 33a8954296a7e63637ad5e210fb30fba1a3fdd53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165110"
---
# <a name="open-and-closed-curves-in-gdi"></a><span data-ttu-id="f8615-102">Otevřené a uzavřené křivky v GDI+</span><span class="sxs-lookup"><span data-stu-id="f8615-102">Open and Closed Curves in GDI+</span></span>
<span data-ttu-id="f8615-103">Následující obrázek znázorňuje dvě křivek: jeden otevřít a jeden zavřené.</span><span class="sxs-lookup"><span data-stu-id="f8615-103">The following illustration shows two curves: one open and one closed.</span></span>  
  
 <span data-ttu-id="f8615-104">![Otevřené a uzavřené křivky](./media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span><span class="sxs-lookup"><span data-stu-id="f8615-104">![Open & Closed curves](./media/aboutgdip02-art24.gif "Aboutgdip02_art24")</span></span>  
  
## <a name="managed-interface-for-curves"></a><span data-ttu-id="f8615-105">Použití spravovaného rozhraní křivky</span><span class="sxs-lookup"><span data-stu-id="f8615-105">Managed Interface for Curves</span></span>  
 <span data-ttu-id="f8615-106">Uzavřené křivky mají vnitřním a proto může být vyplněny štětce.</span><span class="sxs-lookup"><span data-stu-id="f8615-106">Closed curves have an interior and therefore can be filled with a brush.</span></span> <span data-ttu-id="f8615-107"><xref:System.Drawing.Graphics> Třídy v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje následující metody pro vyplnění uzavřených obrazců a křivek: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, a <xref:System.Drawing.Graphics.FillRegion%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8615-107">The <xref:System.Drawing.Graphics> class in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provides the following methods for filling closed shapes and curves: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, and <xref:System.Drawing.Graphics.FillRegion%2A>.</span></span> <span data-ttu-id="f8615-108">Pokaždé, když se bude volat jednu z těchto metod, je nutné předat jednoho z typů konkrétní štětce (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, nebo <xref:System.Drawing.Drawing2D.PathGradientBrush>) jako argument.</span><span class="sxs-lookup"><span data-stu-id="f8615-108">Whenever you call one of these methods, you must pass one of the specific brush types (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, or <xref:System.Drawing.Drawing2D.PathGradientBrush>) as an argument.</span></span>  
  
 <span data-ttu-id="f8615-109"><xref:System.Drawing.Graphics.FillPie%2A> Metody, který je k <xref:System.Drawing.Graphics.DrawArc%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f8615-109">The <xref:System.Drawing.Graphics.FillPie%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawArc%2A> method.</span></span> <span data-ttu-id="f8615-110">Stejně jako <xref:System.Drawing.Graphics.DrawArc%2A> metoda vykreslí část osnovy elipsy, <xref:System.Drawing.Graphics.FillPie%2A> metoda vyplní část vnitřní elipsu.</span><span class="sxs-lookup"><span data-stu-id="f8615-110">Just as the <xref:System.Drawing.Graphics.DrawArc%2A> method draws a portion of the outline of an ellipse, the <xref:System.Drawing.Graphics.FillPie%2A> method fills a portion of the interior of an ellipse.</span></span> <span data-ttu-id="f8615-111">V následujícím příkladu Nakreslí oblouk a vyplní odpovídající část vnitřní elipsy:</span><span class="sxs-lookup"><span data-stu-id="f8615-111">The following example draws an arc and fills the corresponding portion of the interior of the ellipse:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#21](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 <span data-ttu-id="f8615-112">Následující obrázek znázorňuje oblouk a plného výseče.</span><span class="sxs-lookup"><span data-stu-id="f8615-112">The following illustration shows the arc and the filled pie.</span></span>  
  
 <span data-ttu-id="f8615-113">![Otevřené a uzavřené křivky](./media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span><span class="sxs-lookup"><span data-stu-id="f8615-113">![Open & Closed curves](./media/aboutgdip02-art25.gif "Aboutgdip02_art25")</span></span>  
  
 <span data-ttu-id="f8615-114"><xref:System.Drawing.Graphics.FillClosedCurve%2A> Metody, který je k <xref:System.Drawing.Graphics.DrawClosedCurve%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f8615-114">The <xref:System.Drawing.Graphics.FillClosedCurve%2A> method is a companion to the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method.</span></span> <span data-ttu-id="f8615-115">Obě metody automaticky uzavřít křivka koncový bod připojení k výchozí bod.</span><span class="sxs-lookup"><span data-stu-id="f8615-115">Both methods automatically close the curve by connecting the ending point to the starting point.</span></span> <span data-ttu-id="f8615-116">Následující příklad nakreslí křivku, která prochází (0, 0), (60, 20) a (40, 50).</span><span class="sxs-lookup"><span data-stu-id="f8615-116">The following example draws a curve that passes through (0, 0), (60, 20), and (40, 50).</span></span> <span data-ttu-id="f8615-117">Pak se automaticky ukončí křivka připojením (40, 50) na počáteční bod (0, 0), a vnitřní je vyplněn plnou barvou.</span><span class="sxs-lookup"><span data-stu-id="f8615-117">Then, the curve is automatically closed by connecting (40, 50) to the starting point (0, 0), and the interior is filled with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#22](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <span data-ttu-id="f8615-118"><xref:System.Drawing.Graphics.FillPath%2A> Metoda vyplní vnitřek samostatné části cesty.</span><span class="sxs-lookup"><span data-stu-id="f8615-118">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the interiors of the separate pieces of a path.</span></span> <span data-ttu-id="f8615-119">Pokud není tvoří část cesty, uzavřené křivky a obrazce, <xref:System.Drawing.Graphics.FillPath%2A> metoda automaticky uzavře danou částí cesty než vyplnění.</span><span class="sxs-lookup"><span data-stu-id="f8615-119">If a piece of a path doesn't form a closed curve or shape, the <xref:System.Drawing.Graphics.FillPath%2A> method automatically closes that piece of the path before filling it.</span></span> <span data-ttu-id="f8615-120">V následujícím příkladu kreslení a vyplní cestu, která se skládá z oblouk, křivky mohutnosti, řetězce a výsečový:</span><span class="sxs-lookup"><span data-stu-id="f8615-120">The following example draws and fills a path that consists of an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#23](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 <span data-ttu-id="f8615-121">Následující obrázek znázorňuje cestu a nemusíte plné barvy.</span><span class="sxs-lookup"><span data-stu-id="f8615-121">The following illustration shows the path with and without the solid fill.</span></span> <span data-ttu-id="f8615-122">Všimněte si, že je text v řetězci uvedené, ale není vyplněné, tím <xref:System.Drawing.Graphics.DrawPath%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f8615-122">Note that the text in the string is outlined, but not filled, by the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="f8615-123">Je <xref:System.Drawing.Graphics.FillPath%2A> metodu, která se vybarví vnitřek znaků v řetězci.</span><span class="sxs-lookup"><span data-stu-id="f8615-123">It is the <xref:System.Drawing.Graphics.FillPath%2A> method that paints the interiors of the characters in the string.</span></span>  
  
 <span data-ttu-id="f8615-124">![Řetězec v cestě](./media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span><span class="sxs-lookup"><span data-stu-id="f8615-124">![String in a path](./media/aboutgdip02-art26.gif "Aboutgdip02_art26")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8615-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8615-125">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [<span data-ttu-id="f8615-126">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="f8615-126">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="f8615-127">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="f8615-127">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="f8615-128">Sestavování a kreslení cest</span><span class="sxs-lookup"><span data-stu-id="f8615-128">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
