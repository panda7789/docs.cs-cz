---
title: Elipsy a oblouky v rozhraní GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 8bbc2eda6450128eac55576259880e83f07099ab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117453"
---
# <a name="ellipses-and-arcs-in-gdi"></a><span data-ttu-id="a85e2-102">Elipsy a oblouky v rozhraní GDI+</span><span class="sxs-lookup"><span data-stu-id="a85e2-102">Ellipses and Arcs in GDI+</span></span>
<span data-ttu-id="a85e2-103">Můžete snadno kreslení elipsy a oblouky pomocí <xref:System.Drawing.Graphics.DrawEllipse%2A> a <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="a85e2-103">You can easily draw ellipses and arcs using the <xref:System.Drawing.Graphics.DrawEllipse%2A> and <xref:System.Drawing.Graphics.DrawArc%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="drawing-an-ellipse"></a><span data-ttu-id="a85e2-104">Kreslení elipsy</span><span class="sxs-lookup"><span data-stu-id="a85e2-104">Drawing an Ellipse</span></span>  
 <span data-ttu-id="a85e2-105">Chcete-li nakreslit elipsu, je nutné <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="a85e2-105">To draw an ellipse, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="a85e2-106"><xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.DrawEllipse%2A> metody a <xref:System.Drawing.Pen> ukládá atributy, například šířku a barvu čáry použité k vykreslení elipsy.</span><span class="sxs-lookup"><span data-stu-id="a85e2-106">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the ellipse.</span></span> <span data-ttu-id="a85e2-107"><xref:System.Drawing.Pen> Objekt je předán jako argumenty, které mají <xref:System.Drawing.Graphics.DrawEllipse%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a85e2-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="a85e2-108">Zbývající argumenty předané <xref:System.Drawing.Graphics.DrawEllipse%2A> metody zadejte ohraničující obdélník elipsy.</span><span class="sxs-lookup"><span data-stu-id="a85e2-108">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method specify the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="a85e2-109">Následující obrázek znázorňuje elipsa spolu s jeho ohraničující obdélník.</span><span class="sxs-lookup"><span data-stu-id="a85e2-109">The following illustration shows an ellipse along with its bounding rectangle.</span></span>  
  
 <span data-ttu-id="a85e2-110">![Elipsy a oblouky](./media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span><span class="sxs-lookup"><span data-stu-id="a85e2-110">![Ellipses and arcs](./media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span></span>  
  
 <span data-ttu-id="a85e2-111">Následující příklad kreslení plné elipsy; ohraničující obdélník má šířku 80, výška 40 a levého horního rohu (100, 50):</span><span class="sxs-lookup"><span data-stu-id="a85e2-111">The following example draws an ellipse; the bounding rectangle has a width of 80, a height of 40, and an upper-left corner of (100, 50):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#51](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <span data-ttu-id="a85e2-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> je přetížená metoda <xref:System.Drawing.Graphics> třídy, takže je můžete zadat s argumenty několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="a85e2-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="a85e2-113">Například můžete vytvořit <xref:System.Drawing.Rectangle> a předejte mu <xref:System.Drawing.Rectangle> k <xref:System.Drawing.Graphics.DrawEllipse%2A> metody jako argument:</span><span class="sxs-lookup"><span data-stu-id="a85e2-113">For example, you can construct a <xref:System.Drawing.Rectangle> and pass the <xref:System.Drawing.Rectangle> to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#52](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a><span data-ttu-id="a85e2-114">Kreslení oblouk</span><span class="sxs-lookup"><span data-stu-id="a85e2-114">Drawing an Arc</span></span>  
 <span data-ttu-id="a85e2-115">Oblouku je část elipsu.</span><span class="sxs-lookup"><span data-stu-id="a85e2-115">An arc is a portion of an ellipse.</span></span> <span data-ttu-id="a85e2-116">Chcete-li nakreslit oblouk, zavolejte <xref:System.Drawing.Graphics.DrawArc%2A> metodu <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="a85e2-116">To draw an arc, you call the <xref:System.Drawing.Graphics.DrawArc%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="a85e2-117">Parametry <xref:System.Drawing.Graphics.DrawArc%2A> metody jsou stejné jako parametry <xref:System.Drawing.Graphics.DrawEllipse%2A> metody, s výjimkou, že <xref:System.Drawing.Graphics.DrawArc%2A> vyžaduje počáteční úhel a úhel oblouku.</span><span class="sxs-lookup"><span data-stu-id="a85e2-117">The parameters of the <xref:System.Drawing.Graphics.DrawArc%2A> method are the same as the parameters of the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, except that <xref:System.Drawing.Graphics.DrawArc%2A> requires a starting angle and sweep angle.</span></span> <span data-ttu-id="a85e2-118">Následující příklad nakreslí oblouk s počáteční úhel ze stupňů 30 a úhel oblouku 180 stupňů:</span><span class="sxs-lookup"><span data-stu-id="a85e2-118">The following example draws an arc with a starting angle of 30 degrees and a sweep angle of 180 degrees:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#53](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 <span data-ttu-id="a85e2-119">Následující obrázek znázorňuje oblouku elipsy a ohraničující obdélník.</span><span class="sxs-lookup"><span data-stu-id="a85e2-119">The following illustration shows the arc, the ellipse, and the bounding rectangle.</span></span>  
  
 <span data-ttu-id="a85e2-120">![Elipsy a oblouky](./media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span><span class="sxs-lookup"><span data-stu-id="a85e2-120">![Ellipses and arcs](./media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85e2-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a85e2-121">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="a85e2-122">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="a85e2-122">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="a85e2-123">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="a85e2-123">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="a85e2-124">Postupy: Vytvoření pera</span><span class="sxs-lookup"><span data-stu-id="a85e2-124">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="a85e2-125">Postupy: Kreslení obrazce s obrysem</span><span class="sxs-lookup"><span data-stu-id="a85e2-125">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)
