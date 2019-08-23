---
title: Štětce a vyplněné obrazce v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 45ef0b5920e43300e047d363149ea10a7833477b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912233"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="056db-102">Štětce a vyplněné obrazce v GDI+</span><span class="sxs-lookup"><span data-stu-id="056db-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="056db-103">Uzavřený tvar, jako je obdélník nebo elipsa, se skládá z obrysu a vnitřku.</span><span class="sxs-lookup"><span data-stu-id="056db-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="056db-104">Obrys se vykreslí perem a vnitřek se vyplní štětcem.</span><span class="sxs-lookup"><span data-stu-id="056db-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> <span data-ttu-id="056db-105">GDI+ poskytuje několik tříd štětců pro vyplňování vnitřních tvarů uzavřených obrazců: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>a <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="056db-105">GDI+ provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="056db-106">Všechny tyto třídy dědí z <xref:System.Drawing.Brush> třídy.</span><span class="sxs-lookup"><span data-stu-id="056db-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="056db-107">Následující obrázek znázorňuje obdélník vyplněný plným štětcem a elipsu vyplněnou tahem šrafování.</span><span class="sxs-lookup"><span data-stu-id="056db-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="056db-108">![Vyplněné obrazce](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="056db-108">![Filled Shapes](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="056db-109">Plné štětce</span><span class="sxs-lookup"><span data-stu-id="056db-109">Solid Brushes</span></span>  
 <span data-ttu-id="056db-110">Chcete-li vyplnit uzavřený tvar, potřebujete instanci <xref:System.Drawing.Graphics> třídy <xref:System.Drawing.Brush>a.</span><span class="sxs-lookup"><span data-stu-id="056db-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="056db-111">Instance <xref:System.Drawing.Graphics> třídy poskytuje metody, <xref:System.Drawing.Graphics.FillRectangle%2A> jako jsou a <xref:System.Drawing.Graphics.FillEllipse%2A>, a také <xref:System.Drawing.Brush> atributy obchodů výplně, jako je barva a vzor.</span><span class="sxs-lookup"><span data-stu-id="056db-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="056db-112"><xref:System.Drawing.Brush> Je předán jako jeden z argumentů metody Fill.</span><span class="sxs-lookup"><span data-stu-id="056db-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="056db-113">Následující příklad kódu ukazuje, jak vyplnit elipsu plnou červenou barvou.</span><span class="sxs-lookup"><span data-stu-id="056db-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
> <span data-ttu-id="056db-114">V předchozím příkladu je štětec typu <xref:System.Drawing.SolidBrush>, který dědí z. <xref:System.Drawing.Brush></span><span class="sxs-lookup"><span data-stu-id="056db-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="056db-115">Šrafované štětce</span><span class="sxs-lookup"><span data-stu-id="056db-115">Hatch Brushes</span></span>  
 <span data-ttu-id="056db-116">Při naplňování tvaru pomocí šrafování štětce určíte barvu popředí, barvu pozadí a styl šrafování.</span><span class="sxs-lookup"><span data-stu-id="056db-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="056db-117">Barva popředí je barva šrafování.</span><span class="sxs-lookup"><span data-stu-id="056db-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 <span data-ttu-id="056db-118">GDI+ poskytuje více než 50 stylů šrafování; tři styly zobrazené na následujícím obrázku jsou <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>a <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span><span class="sxs-lookup"><span data-stu-id="056db-118">GDI+ provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="056db-119">![Vyplněné obrazce](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="056db-119">![Filled Shapes](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="056db-120">Štětce textury</span><span class="sxs-lookup"><span data-stu-id="056db-120">Texture Brushes</span></span>  
 <span data-ttu-id="056db-121">Pomocí štětce textury můžete vyplnit tvar pomocí vzoru uloženého v bitmapě.</span><span class="sxs-lookup"><span data-stu-id="056db-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="056db-122">Předpokládejme například, že následující obrázek je uložený v souboru na disku s `MyTexture.bmp`názvem.</span><span class="sxs-lookup"><span data-stu-id="056db-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="056db-123">![Vyplněný tvar](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="056db-123">![Filled Shape](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="056db-124">Následující příklad kódu ukazuje, jak vyplnit elipsu opakováním obrázku uloženého v `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="056db-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="056db-125">Následující ilustrace znázorňuje Vyplněnou elipsu.</span><span class="sxs-lookup"><span data-stu-id="056db-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="056db-126">![Vyplněný tvar](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="056db-126">![Filled Shape](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="056db-127">Štětce přechodu</span><span class="sxs-lookup"><span data-stu-id="056db-127">Gradient Brushes</span></span>  
 <span data-ttu-id="056db-128">GDI+ nabízí dva druhy štětců přechodů: lineární a cesta.</span><span class="sxs-lookup"><span data-stu-id="056db-128">GDI+ provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="056db-129">Můžete použít štětec lineárního přechodu k vyplnění obrazce barvou, která se postupně mění při pohybu mezi tvary vodorovně, svisle nebo úhlopříčně.</span><span class="sxs-lookup"><span data-stu-id="056db-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="056db-130">Následující příklad kódu ukazuje, jak vyplnit elipsu vodorovným barevným štětcem, který se při přesunu od levého okraje elipsy do pravého okraje mění z modré na zelenou.</span><span class="sxs-lookup"><span data-stu-id="056db-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="056db-131">Následující ilustrace znázorňuje Vyplněnou elipsu.</span><span class="sxs-lookup"><span data-stu-id="056db-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="056db-132">![Vyplněný tvar](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="056db-132">![Filled Shape](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="056db-133">Štětec pro barevný přechod může být nakonfigurovaný tak, aby se změnila barva při přechodu od středu tvaru k okraji.</span><span class="sxs-lookup"><span data-stu-id="056db-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="056db-134">![Vyplněný tvar](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="056db-134">![Filled Shape](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="056db-135">Štětce přechodu cest jsou poměrně flexibilní.</span><span class="sxs-lookup"><span data-stu-id="056db-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="056db-136">Štětec přechodu použitý k vyplnění trojúhelníku v následujícím obrázku se postupně mění od červeného na všech třech různých barvách na vrcholech.</span><span class="sxs-lookup"><span data-stu-id="056db-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="056db-137">![Vyplněný tvar](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="056db-137">![Filled Shape](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="056db-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="056db-138">See also</span></span>

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [<span data-ttu-id="056db-139">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="056db-139">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="056db-140">Postupy: Nakreslit vyplněný obdélník na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="056db-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [<span data-ttu-id="056db-141">Postupy: Nakreslit Vyplněnou elipsu na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="056db-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
