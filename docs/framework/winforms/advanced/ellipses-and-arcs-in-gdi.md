---
title: "Elipsy a oblouky v rozhraní GDI+"
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
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ebeae1d076a0ebcf36d52dee1af0c0ad5f04fdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ellipses-and-arcs-in-gdi"></a><span data-ttu-id="6faac-102">Elipsy a oblouky v rozhraní GDI+</span><span class="sxs-lookup"><span data-stu-id="6faac-102">Ellipses and Arcs in GDI+</span></span>
<span data-ttu-id="6faac-103">Můžete snadno kreslení elipsy a oblouky pomocí <xref:System.Drawing.Graphics.DrawEllipse%2A> a <xref:System.Drawing.Graphics.DrawArc%2A> metody <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="6faac-103">You can easily draw ellipses and arcs using the <xref:System.Drawing.Graphics.DrawEllipse%2A> and <xref:System.Drawing.Graphics.DrawArc%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="drawing-an-ellipse"></a><span data-ttu-id="6faac-104">Kreslení elipsy</span><span class="sxs-lookup"><span data-stu-id="6faac-104">Drawing an Ellipse</span></span>  
 <span data-ttu-id="6faac-105">Kreslení elipsy, musíte <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="6faac-105">To draw an ellipse, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="6faac-106"><xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.DrawEllipse%2A> metody a <xref:System.Drawing.Pen> objekt ukládá atributy, jako například šířku a barvu čáry použité k vykreslení se třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="6faac-106">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the ellipse.</span></span> <span data-ttu-id="6faac-107"><xref:System.Drawing.Pen> Objekt je předán jako jeden z argumenty, které mají <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="6faac-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="6faac-108">Zbývající argumenty předaný <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda zadejte ohraničující obdélník pro se třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="6faac-108">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method specify the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="6faac-109">Následující obrázek znázorňuje elipsy společně s jeho ohraničující obdélník.</span><span class="sxs-lookup"><span data-stu-id="6faac-109">The following illustration shows an ellipse along with its bounding rectangle.</span></span>  
  
 <span data-ttu-id="6faac-110">![Elipsy a oblouky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span><span class="sxs-lookup"><span data-stu-id="6faac-110">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span></span>  
  
 <span data-ttu-id="6faac-111">Následující příklad nevykresluje elipsy; ohraničující obdélník má šířku 80, výška 40 a levého horního rohu (100, 50):</span><span class="sxs-lookup"><span data-stu-id="6faac-111">The following example draws an ellipse; the bounding rectangle has a width of 80, a height of 40, and an upper-left corner of (100, 50):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <span data-ttu-id="6faac-112"><xref:System.Drawing.Graphics.DrawEllipse%2A>je přetížené metodu <xref:System.Drawing.Graphics> třídy, takže je můžete zadat s argumenty několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="6faac-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="6faac-113">Například můžete vytvořit <xref:System.Drawing.Rectangle> a předat <xref:System.Drawing.Rectangle> k <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda jako argument:</span><span class="sxs-lookup"><span data-stu-id="6faac-113">For example, you can construct a <xref:System.Drawing.Rectangle> and pass the <xref:System.Drawing.Rectangle> to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a><span data-ttu-id="6faac-114">Kreslení oblouk</span><span class="sxs-lookup"><span data-stu-id="6faac-114">Drawing an Arc</span></span>  
 <span data-ttu-id="6faac-115">Oblouk je část elipsy.</span><span class="sxs-lookup"><span data-stu-id="6faac-115">An arc is a portion of an ellipse.</span></span> <span data-ttu-id="6faac-116">Chcete-li nakreslit oblouk, zavolejte <xref:System.Drawing.Graphics.DrawArc%2A> metodu <xref:System.Drawing.Graphics> – třída.</span><span class="sxs-lookup"><span data-stu-id="6faac-116">To draw an arc, you call the <xref:System.Drawing.Graphics.DrawArc%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="6faac-117">Parametry <xref:System.Drawing.Graphics.DrawArc%2A> metody jsou stejné jako parametry <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda, vyjma toho, že <xref:System.Drawing.Graphics.DrawArc%2A> vyžaduje počáteční úhel a úhel oblouku.</span><span class="sxs-lookup"><span data-stu-id="6faac-117">The parameters of the <xref:System.Drawing.Graphics.DrawArc%2A> method are the same as the parameters of the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, except that <xref:System.Drawing.Graphics.DrawArc%2A> requires a starting angle and sweep angle.</span></span> <span data-ttu-id="6faac-118">Následující příklad nakreslí oblouk s počáteční úhel 30 stupňů a úhel oblouku 180 stupňů:</span><span class="sxs-lookup"><span data-stu-id="6faac-118">The following example draws an arc with a starting angle of 30 degrees and a sweep angle of 180 degrees:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 <span data-ttu-id="6faac-119">Následující obrázek znázorňuje oblouk, se třemi tečkami a ohraničující obdélník.</span><span class="sxs-lookup"><span data-stu-id="6faac-119">The following illustration shows the arc, the ellipse, and the bounding rectangle.</span></span>  
  
 <span data-ttu-id="6faac-120">![Elipsy a oblouky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span><span class="sxs-lookup"><span data-stu-id="6faac-120">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6faac-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6faac-121">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="6faac-122">Čar, křivek a obrazců</span><span class="sxs-lookup"><span data-stu-id="6faac-122">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="6faac-123">Postupy: vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="6faac-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="6faac-124">Postupy: vytvoření pera</span><span class="sxs-lookup"><span data-stu-id="6faac-124">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="6faac-125">Postupy: kreslení obrazce s obrysem</span><span class="sxs-lookup"><span data-stu-id="6faac-125">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
