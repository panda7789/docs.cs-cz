---
title: Pera, čáry a obdélníky v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 84752773c0b56d9684dc31620d463d4ddccf9dad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078223"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a><span data-ttu-id="ef380-102">Pera, čáry a obdélníky v GDI+</span><span class="sxs-lookup"><span data-stu-id="ef380-102">Pens, Lines, and Rectangles in GDI+</span></span>
<span data-ttu-id="ef380-103">Kreslení čar pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je potřeba vytvořit <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef380-103">To draw lines with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you need to create a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="ef380-104"><xref:System.Drawing.Graphics> Objekt, který poskytuje metody, které se dělají kreslení, a <xref:System.Drawing.Pen> ukládá atributy, jako je barva čáry, šířku a stylu.</span><span class="sxs-lookup"><span data-stu-id="ef380-104">The <xref:System.Drawing.Graphics> object provides the methods that actually do the drawing, and the <xref:System.Drawing.Pen> object stores attributes, such as line color, width, and style.</span></span>  
  
## <a name="drawing-a-line"></a><span data-ttu-id="ef380-105">Vykreslení čáry</span><span class="sxs-lookup"><span data-stu-id="ef380-105">Drawing a Line</span></span>  
 <span data-ttu-id="ef380-106">Chcete-li nakreslit čáru, zavolejte <xref:System.Drawing.Graphics.DrawLine%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef380-106">To draw a line, call the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="ef380-107"><xref:System.Drawing.Pen> Objekt je předán jako argumenty, které mají <xref:System.Drawing.Graphics.DrawLine%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ef380-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method.</span></span> <span data-ttu-id="ef380-108">Následující příklad nakreslí čáru z bodu (4, 2) pro bod (12, 6):</span><span class="sxs-lookup"><span data-stu-id="ef380-108">The following example draws a line from the point (4, 2) to the point (12, 6):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <span data-ttu-id="ef380-109"><xref:System.Drawing.Graphics.DrawLine%2A> je přetížená metoda <xref:System.Drawing.Graphics> třídy, takže je můžete zadat s argumenty několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="ef380-109"><xref:System.Drawing.Graphics.DrawLine%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="ef380-110">Například můžete vytvořit dvě <xref:System.Drawing.Point> objekty a předejte jí <xref:System.Drawing.Point> objekty jako argumenty, které mají <xref:System.Drawing.Graphics.DrawLine%2A> metoda:</span><span class="sxs-lookup"><span data-stu-id="ef380-110">For example, you can construct two <xref:System.Drawing.Point> objects and pass the <xref:System.Drawing.Point> objects as arguments to the <xref:System.Drawing.Graphics.DrawLine%2A> method:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a><span data-ttu-id="ef380-111">Vytváření pera</span><span class="sxs-lookup"><span data-stu-id="ef380-111">Constructing a Pen</span></span>  
 <span data-ttu-id="ef380-112">Určité atributy můžete zadat při vytváření <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef380-112">You can specify certain attributes when you construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="ef380-113">Například jeden `Pen` konstruktor umožňuje zadat barvu a šířku.</span><span class="sxs-lookup"><span data-stu-id="ef380-113">For example, one `Pen` constructor allows you to specify color and width.</span></span> <span data-ttu-id="ef380-114">Následující příklad nakreslí modrá čára šířky 2 z (0, 0) na (60, 30):</span><span class="sxs-lookup"><span data-stu-id="ef380-114">The following example draws a blue line of width 2 from (0, 0) to (60, 30):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a><span data-ttu-id="ef380-115">Přerušované čáry a zakončení</span><span class="sxs-lookup"><span data-stu-id="ef380-115">Dashed Lines and Line Caps</span></span>  
 <span data-ttu-id="ef380-116"><xref:System.Drawing.Pen> Objekt také zpřístupní vlastnosti, jako například <xref:System.Drawing.Pen.DashStyle%2A>, že můžete použít k určení funkce na řádku.</span><span class="sxs-lookup"><span data-stu-id="ef380-116">The <xref:System.Drawing.Pen> object also exposes properties, such as <xref:System.Drawing.Pen.DashStyle%2A>, that you can use to specify features of the line.</span></span> <span data-ttu-id="ef380-117">Následující příklad kreslení na přerušovanou čáru z (100, 50) na (300, 80):</span><span class="sxs-lookup"><span data-stu-id="ef380-117">The following example draws a dashed line from (100, 50) to (300, 80):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 <span data-ttu-id="ef380-118">Můžete použít vlastnosti <xref:System.Drawing.Pen> nastavíte mnoho další atributy čáry.</span><span class="sxs-lookup"><span data-stu-id="ef380-118">You can use the properties of the <xref:System.Drawing.Pen> object to set many more attributes of the line.</span></span> <span data-ttu-id="ef380-119"><xref:System.Drawing.Pen.StartCap%2A> a <xref:System.Drawing.Pen.EndCap%2A> vlastnosti určují vzhled konce řádku; konců lze použít bez stromové struktury, čtvereček, zakulacený, trojúhelníkové, nebo vlastní obrazce.</span><span class="sxs-lookup"><span data-stu-id="ef380-119">The <xref:System.Drawing.Pen.StartCap%2A> and <xref:System.Drawing.Pen.EndCap%2A> properties specify the appearance of the ends of the line; the ends can be flat, square, rounded, triangular, or a custom shape.</span></span> <span data-ttu-id="ef380-120"><xref:System.Drawing.Pen.LineJoin%2A> Vlastnost umožňuje určit, zda spojené čáry jsou zkosené (připojené k doméně se sharp rohy), sený, zaokrouhleno nebo oříznut.</span><span class="sxs-lookup"><span data-stu-id="ef380-120">The <xref:System.Drawing.Pen.LineJoin%2A> property lets you specify whether connected lines are mitered (joined with sharp corners), beveled, rounded, or clipped.</span></span> <span data-ttu-id="ef380-121">Následující obrázek znázorňuje řádky s různými styly zakončení a spojení.</span><span class="sxs-lookup"><span data-stu-id="ef380-121">The following illustration shows lines with various cap and join styles.</span></span>  
  
 <span data-ttu-id="ef380-122">![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span><span class="sxs-lookup"><span data-stu-id="ef380-122">![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")</span></span>  
  
## <a name="drawing-a-rectangle"></a><span data-ttu-id="ef380-123">Vykreslení obdélníku</span><span class="sxs-lookup"><span data-stu-id="ef380-123">Drawing a Rectangle</span></span>  
 <span data-ttu-id="ef380-124">Kreslení obdélníků pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] je nějak nakreslení čáry.</span><span class="sxs-lookup"><span data-stu-id="ef380-124">Drawing rectangles with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is similar to drawing lines.</span></span> <span data-ttu-id="ef380-125">Chcete-li nakreslit obdélník, je nutné <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="ef380-125">To draw a rectangle, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="ef380-126"><xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.DrawRectangle%2A> metody a <xref:System.Drawing.Pen> ukládá atributy, jako je například šířku čáry a barvu.</span><span class="sxs-lookup"><span data-stu-id="ef380-126">The <xref:System.Drawing.Graphics> object provides a <xref:System.Drawing.Graphics.DrawRectangle%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as line width and color.</span></span> <span data-ttu-id="ef380-127"><xref:System.Drawing.Pen> Objekt je předán jako argumenty, které mají <xref:System.Drawing.Graphics.DrawRectangle%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ef380-127">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method.</span></span> <span data-ttu-id="ef380-128">Kreslení obdélníku s jeho levého horního rohu v následujícím příkladu (100, 50), 80 šířku a výšku 40:</span><span class="sxs-lookup"><span data-stu-id="ef380-128">The following example draws a rectangle with its upper-left corner at (100, 50), a width of 80, and a height of 40:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <span data-ttu-id="ef380-129"><xref:System.Drawing.Graphics.DrawRectangle%2A> je přetížená metoda <xref:System.Drawing.Graphics> třídy, takže je můžete zadat s argumenty několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="ef380-129"><xref:System.Drawing.Graphics.DrawRectangle%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="ef380-130">Například můžete vytvořit <xref:System.Drawing.Rectangle> objektu a předejte <xref:System.Drawing.Rectangle> objektu <xref:System.Drawing.Graphics.DrawRectangle%2A> metody jako argument:</span><span class="sxs-lookup"><span data-stu-id="ef380-130">For example, you can construct a <xref:System.Drawing.Rectangle> object and pass the <xref:System.Drawing.Rectangle> object to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 <span data-ttu-id="ef380-131">A <xref:System.Drawing.Rectangle> objekt má metody a vlastnosti zpracování a shromažďují se informace o obdélníku.</span><span class="sxs-lookup"><span data-stu-id="ef380-131">A <xref:System.Drawing.Rectangle> object has methods and properties for manipulating and gathering information about the rectangle.</span></span> <span data-ttu-id="ef380-132">Například <xref:System.Drawing.Rectangle.Inflate%2A> a <xref:System.Drawing.Rectangle.Offset%2A> metody měnit velikost a umístění obdélníku.</span><span class="sxs-lookup"><span data-stu-id="ef380-132">For example, the <xref:System.Drawing.Rectangle.Inflate%2A> and <xref:System.Drawing.Rectangle.Offset%2A> methods change the size and position of the rectangle.</span></span> <span data-ttu-id="ef380-133"><xref:System.Drawing.Rectangle.IntersectsWith%2A> Metoda zjistíte, zda obdélník protíná jiné zadané obdélníku a <xref:System.Drawing.Rectangle.Contains%2A> metoda zjistíte, jestli je daný bod v obdélníku.</span><span class="sxs-lookup"><span data-stu-id="ef380-133">The <xref:System.Drawing.Rectangle.IntersectsWith%2A> method tells you whether the rectangle intersects another given rectangle, and the <xref:System.Drawing.Rectangle.Contains%2A> method tells you whether a given point is inside the rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef380-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef380-134">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [<span data-ttu-id="ef380-135">Postupy: Vytvoření pera</span><span class="sxs-lookup"><span data-stu-id="ef380-135">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="ef380-136">Postupy: Nakreslit čáru na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="ef380-136">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)
- [<span data-ttu-id="ef380-137">Postupy: Kreslení obrazce s obrysem</span><span class="sxs-lookup"><span data-stu-id="ef380-137">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)
