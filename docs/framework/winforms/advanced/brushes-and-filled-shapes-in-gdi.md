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
ms.openlocfilehash: 9475518a5f0422e0eac1ec521088071bb4d1c885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518991"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a><span data-ttu-id="87e1e-102">Štětce a vyplněné obrazce v GDI+</span><span class="sxs-lookup"><span data-stu-id="87e1e-102">Brushes and Filled Shapes in GDI+</span></span>
<span data-ttu-id="87e1e-103">Uzavřený obrazec, jako je například obdélníku nebo elipsy, se skládá z přehledu a vnitřním.</span><span class="sxs-lookup"><span data-stu-id="87e1e-103">A closed shape, such as a rectangle or an ellipse, consists of an outline and an interior.</span></span> <span data-ttu-id="87e1e-104">Obrys vykreslením pomocí pera a vnitřní je vyplněn štětce.</span><span class="sxs-lookup"><span data-stu-id="87e1e-104">The outline is drawn with a pen and the interior is filled with a brush.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="87e1e-105"> poskytuje několik štětce třídy pro naplnění vnitřek uzavřené obrazce: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, a <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="87e1e-105"> provides several brush classes for filling the interiors of closed shapes: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, and <xref:System.Drawing.Drawing2D.PathGradientBrush>.</span></span> <span data-ttu-id="87e1e-106">Všechny tyto třídy dědí <xref:System.Drawing.Brush> třídy.</span><span class="sxs-lookup"><span data-stu-id="87e1e-106">All of these classes inherit from the <xref:System.Drawing.Brush> class.</span></span> <span data-ttu-id="87e1e-107">Následující obrázek znázorňuje obdélníku, naplní se plného štětce a elipsy plná štětce šrafování.</span><span class="sxs-lookup"><span data-stu-id="87e1e-107">The following illustration shows a rectangle filled with a solid brush and an ellipse filled with a hatch brush.</span></span>  
  
 <span data-ttu-id="87e1e-108">![Vyplněné tvary](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span><span class="sxs-lookup"><span data-stu-id="87e1e-108">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")</span></span>  
  
## <a name="solid-brushes"></a><span data-ttu-id="87e1e-109">Plného štětce</span><span class="sxs-lookup"><span data-stu-id="87e1e-109">Solid Brushes</span></span>  
 <span data-ttu-id="87e1e-110">K vyplnění uzavřený obrazec, je třeba instanci <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="87e1e-110">To fill a closed shape, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Brush>.</span></span> <span data-ttu-id="87e1e-111">Instance <xref:System.Drawing.Graphics> třída poskytuje metody, jako například <xref:System.Drawing.Graphics.FillRectangle%2A> a <xref:System.Drawing.Graphics.FillEllipse%2A>a <xref:System.Drawing.Brush> uloží atributy výplně, jako je například barvy a vzorku.</span><span class="sxs-lookup"><span data-stu-id="87e1e-111">The instance of the <xref:System.Drawing.Graphics> class provides methods, such as <xref:System.Drawing.Graphics.FillRectangle%2A> and <xref:System.Drawing.Graphics.FillEllipse%2A>, and the <xref:System.Drawing.Brush> stores attributes of the fill, such as color and pattern.</span></span> <span data-ttu-id="87e1e-112"><xref:System.Drawing.Brush> Jako jednoho z argumentů předaný metodě výplně.</span><span class="sxs-lookup"><span data-stu-id="87e1e-112">The <xref:System.Drawing.Brush> is passed as one of the arguments to the fill method.</span></span> <span data-ttu-id="87e1e-113">Následující příklad kódu ukazuje, jak k vyplnění elipsy s plnou červenou barvu.</span><span class="sxs-lookup"><span data-stu-id="87e1e-113">The following code example shows how to fill an ellipse with a solid red color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  <span data-ttu-id="87e1e-114">V předchozím příkladu stopy je typu <xref:System.Drawing.SolidBrush>, který dědí z <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="87e1e-114">In the preceding example, the brush is of type <xref:System.Drawing.SolidBrush>, which inherits from <xref:System.Drawing.Brush>.</span></span>  
  
## <a name="hatch-brushes"></a><span data-ttu-id="87e1e-115">Nesouvislých štětců</span><span class="sxs-lookup"><span data-stu-id="87e1e-115">Hatch Brushes</span></span>  
 <span data-ttu-id="87e1e-116">Po vyplnění obrazce štětcem šrafování, je třeba zadat barvu popředí, barva pozadí a styl šrafování.</span><span class="sxs-lookup"><span data-stu-id="87e1e-116">When you fill a shape with a hatch brush, you specify a foreground color, a background color, and a hatch style.</span></span> <span data-ttu-id="87e1e-117">Barvu popředí je barva šrafování.</span><span class="sxs-lookup"><span data-stu-id="87e1e-117">The foreground color is the color of the hatching.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="87e1e-118"> poskytuje více než 50 šrafování styly; tři styly vidět na následujícím obrázku jsou <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, a <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span><span class="sxs-lookup"><span data-stu-id="87e1e-118"> provides more than 50 hatch styles; the three styles shown in the following illustration are <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, and <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.</span></span>  
  
 <span data-ttu-id="87e1e-119">![Vyplněné tvary](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span><span class="sxs-lookup"><span data-stu-id="87e1e-119">![Filled Shapes](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")</span></span>  
  
## <a name="texture-brushes"></a><span data-ttu-id="87e1e-120">Texturované štětce</span><span class="sxs-lookup"><span data-stu-id="87e1e-120">Texture Brushes</span></span>  
 <span data-ttu-id="87e1e-121">Štětcem texture můžete vyplnění obrazce pomocí vzoru uložené v rastrový obrázek.</span><span class="sxs-lookup"><span data-stu-id="87e1e-121">With a texture brush, you can fill a shape with a pattern stored in a bitmap.</span></span> <span data-ttu-id="87e1e-122">Předpokládejme například, že na následujícím obrázku je uložený v souboru na disku s názvem `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="87e1e-122">For example, suppose the following picture is stored in a disk file named `MyTexture.bmp`.</span></span>  
  
 <span data-ttu-id="87e1e-123">![Vyplněné obrazce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span><span class="sxs-lookup"><span data-stu-id="87e1e-123">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")</span></span>  
  
 <span data-ttu-id="87e1e-124">Následující příklad kódu ukazuje, jak k vyplnění elipsy opakováním obrázek uložený v `MyTexture.bmp`.</span><span class="sxs-lookup"><span data-stu-id="87e1e-124">The following code example shows how to fill an ellipse by repeating the picture stored in `MyTexture.bmp`.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 <span data-ttu-id="87e1e-125">Následující obrázek znázorňuje plné elipsy.</span><span class="sxs-lookup"><span data-stu-id="87e1e-125">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="87e1e-126">![Vyplněné obrazce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span><span class="sxs-lookup"><span data-stu-id="87e1e-126">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")</span></span>  
  
## <a name="gradient-brushes"></a><span data-ttu-id="87e1e-127">Štětce přechodu</span><span class="sxs-lookup"><span data-stu-id="87e1e-127">Gradient Brushes</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="87e1e-128"> nabízí dva typy štětce přechodu: lineární a cestu.</span><span class="sxs-lookup"><span data-stu-id="87e1e-128"> provides two kinds of gradient brushes: linear and path.</span></span> <span data-ttu-id="87e1e-129">Můžete lineární štětce přechodu k vyplnění obrazce s barvu, která změní postupně přesouvat mezi tvaru vodorovně, svisle nebo šikmo.</span><span class="sxs-lookup"><span data-stu-id="87e1e-129">You can use a linear gradient brush to fill a shape with color that changes gradually as you move across the shape horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="87e1e-130">Následující příklad kódu ukazuje, jak vyplníte elipsy vodorovné štětce přechodu, který změní z modré zelený, když jste odpojili od levého okraje se třemi tečkami na pravý okraj.</span><span class="sxs-lookup"><span data-stu-id="87e1e-130">The following code example shows how to fill an ellipse with a horizontal gradient brush that changes from blue to green as you move from the left edge of the ellipse to the right edge.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 <span data-ttu-id="87e1e-131">Následující obrázek znázorňuje plné elipsy.</span><span class="sxs-lookup"><span data-stu-id="87e1e-131">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="87e1e-132">![Vyplněné obrazce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span><span class="sxs-lookup"><span data-stu-id="87e1e-132">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")</span></span>  
  
 <span data-ttu-id="87e1e-133">Štětce přechodu cesty může být nakonfigurován pro změnit barvu, jako jste odpojili od středu tvaru směrem od okraje.</span><span class="sxs-lookup"><span data-stu-id="87e1e-133">A path gradient brush can be configured to change color as you move from the center of a shape toward the edge.</span></span>  
  
 <span data-ttu-id="87e1e-134">![Vyplněné obrazce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span><span class="sxs-lookup"><span data-stu-id="87e1e-134">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")</span></span>  
  
 <span data-ttu-id="87e1e-135">Štětce přechodu cesty jsou velmi flexibilní.</span><span class="sxs-lookup"><span data-stu-id="87e1e-135">Path gradient brushes are quite flexible.</span></span> <span data-ttu-id="87e1e-136">Štětce přechodu použitou k vyplnění trojúhelníček následujícím změnám obrázek postupně z červené v Centru pro každé ze tří různých barev na vrcholy.</span><span class="sxs-lookup"><span data-stu-id="87e1e-136">The gradient brush used to fill the triangle in the following illustration changes gradually from red at the center to each of three different colors at the vertices.</span></span>  
  
 <span data-ttu-id="87e1e-137">![Vyplněné obrazce](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span><span class="sxs-lookup"><span data-stu-id="87e1e-137">![Filled Shape](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e1e-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="87e1e-138">See Also</span></span>  
 <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 [<span data-ttu-id="87e1e-139">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="87e1e-139">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="87e1e-140">Postupy: Kreslení plného obdélníku ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="87e1e-140">How to: Draw a Filled Rectangle on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)  
 [<span data-ttu-id="87e1e-141">Postupy: Kreslení plné elipsy ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="87e1e-141">How to: Draw a Filled Ellipse on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
