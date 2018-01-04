---
title: "Postupy: Vytvoření lineárního přechodu"
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
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33979decf37e9adb29d94a6602a43f992d93aaa1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-linear-gradient"></a><span data-ttu-id="654ac-102">Postupy: Vytvoření lineárního přechodu</span><span class="sxs-lookup"><span data-stu-id="654ac-102">How to: Create a Linear Gradient</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="654ac-103">poskytuje vodorovné, svislé a diagonálních lineární přechody.</span><span class="sxs-lookup"><span data-stu-id="654ac-103"> provides horizontal, vertical, and diagonal linear gradients.</span></span> <span data-ttu-id="654ac-104">Ve výchozím nastavení změní barvu v lineárního přechodu jednotně.</span><span class="sxs-lookup"><span data-stu-id="654ac-104">By default, the color in a linear gradient changes uniformly.</span></span> <span data-ttu-id="654ac-105">Lineárního přechodu však můžete přizpůsobit tak, že změní barvu způsobem neuniformní.</span><span class="sxs-lookup"><span data-stu-id="654ac-105">However, you can customize a linear gradient so that the color changes in a non-uniform fashion.</span></span>  
  
 <span data-ttu-id="654ac-106">Následující příklad doplní řádku, třemi tečkami a obdélníku štětcem vodorovné lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="654ac-106">The following example fills a line, an ellipse, and a rectangle with a horizontal linear gradient brush.</span></span>  
  
 <span data-ttu-id="654ac-107"><xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Konstruktor přijímá čtyři argumenty: dva body a dvě barvy.</span><span class="sxs-lookup"><span data-stu-id="654ac-107">The <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor receives four arguments: two points and two colors.</span></span> <span data-ttu-id="654ac-108">První bod (0, 10) je přidružen první barvy (červená) a druhý bod (200, 10) souvisí s druhou barvu (modrá).</span><span class="sxs-lookup"><span data-stu-id="654ac-108">The first point (0, 10) is associated with the first color (red), and the second point (200, 10) is associated with the second color (blue).</span></span> <span data-ttu-id="654ac-109">Jak by jste očekávali, řádku čerpají z (0, 10) na (200, 10) se změní z červené na modrou postupně.</span><span class="sxs-lookup"><span data-stu-id="654ac-109">As you would expect, the line drawn from (0, 10) to (200, 10) changes gradually from red to blue.</span></span>  
  
 <span data-ttu-id="654ac-110">10s v bodech (50, 10) a (200, 10) nejsou důležité.</span><span class="sxs-lookup"><span data-stu-id="654ac-110">The 10s in the points (50, 10) and (200, 10) are not important.</span></span> <span data-ttu-id="654ac-111">Důležité je, že dva body mají stejné souřadnice druhý – řádek jejich připojením je vodorovné.</span><span class="sxs-lookup"><span data-stu-id="654ac-111">What is important is that the two points have the same second coordinate — the line connecting them is horizontal.</span></span> <span data-ttu-id="654ac-112">Se třemi tečkami a rámeček také změnit postupně z červené na modrou jako souřadnici vodorovné přejde od 0 do 200.</span><span class="sxs-lookup"><span data-stu-id="654ac-112">The ellipse and the rectangle also change gradually from red to blue as the horizontal coordinate goes from 0 to 200.</span></span>  
  
 <span data-ttu-id="654ac-113">Následující obrázek znázorňuje řádek se třemi tečkami a rámeček.</span><span class="sxs-lookup"><span data-stu-id="654ac-113">The following illustration shows the line, the ellipse, and the rectangle.</span></span> <span data-ttu-id="654ac-114">Všimněte si, že barvy opakuje jako souřadnici vodorovné zvýší nad 200.</span><span class="sxs-lookup"><span data-stu-id="654ac-114">Note that the color gradient repeats itself as the horizontal coordinate increases beyond 200.</span></span>  
  
 <span data-ttu-id="654ac-115">![Lineárního přechodu](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")</span><span class="sxs-lookup"><span data-stu-id="654ac-115">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")</span></span>  
  
### <a name="to-use-horizontal-linear-gradients"></a><span data-ttu-id="654ac-116">Chcete-li použít vodorovné lineární přechody</span><span class="sxs-lookup"><span data-stu-id="654ac-116">To use horizontal linear gradients</span></span>  
  
-   <span data-ttu-id="654ac-117">Předejte modře neprůhledného červené a neprůhledného jako třetí a čtvrtý argument, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="654ac-117">Pass in the opaque red and opaque blue as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 <span data-ttu-id="654ac-118">V předchozím příkladu komponenty barvu změnit lineárně jako přesunout z vodorovné souřadnice 0 vodorovné souřadnice 200.</span><span class="sxs-lookup"><span data-stu-id="654ac-118">In the preceding example, the color components change linearly as you move from a horizontal coordinate of 0 to a horizontal coordinate of 200.</span></span> <span data-ttu-id="654ac-119">Například bod, jehož první souřadnice je uprostřed mezi 0 a 200 bude mít blue komponenty, která je uprostřed mezi 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="654ac-119">For example, a point whose first coordinate is halfway between 0 and 200 will have a blue component that is halfway between 0 and 255.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="654ac-120">Umožňuje upravit způsob, jakým barvu, která se liší od jeden okraj přechodu na druhý.</span><span class="sxs-lookup"><span data-stu-id="654ac-120"> allows you to adjust the way a color varies from one edge of a gradient to the other.</span></span> <span data-ttu-id="654ac-121">Předpokládejme, že chcete vytvořit štětce přechodu, který změní z černé na červený podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="654ac-121">Suppose you want to create a gradient brush that changes from black to red according to the following table.</span></span>  
  
|<span data-ttu-id="654ac-122">Vodorovné souřadnice</span><span class="sxs-lookup"><span data-stu-id="654ac-122">Horizontal coordinate</span></span>|<span data-ttu-id="654ac-123">RGB součásti</span><span class="sxs-lookup"><span data-stu-id="654ac-123">RGB components</span></span>|  
|---------------------------|--------------------|  
|<span data-ttu-id="654ac-124">0</span><span class="sxs-lookup"><span data-stu-id="654ac-124">0</span></span>|<span data-ttu-id="654ac-125">(0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="654ac-125">(0, 0, 0)</span></span>|  
|<span data-ttu-id="654ac-126">40</span><span class="sxs-lookup"><span data-stu-id="654ac-126">40</span></span>|<span data-ttu-id="654ac-127">(128, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="654ac-127">(128, 0, 0)</span></span>|  
|<span data-ttu-id="654ac-128">200</span><span class="sxs-lookup"><span data-stu-id="654ac-128">200</span></span>|<span data-ttu-id="654ac-129">(255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="654ac-129">(255, 0, 0)</span></span>|  
  
 <span data-ttu-id="654ac-130">Upozorňujeme, že komponentu red se poloviční intenzitou jenom 20 procent způsob 200 od 0 po vodorovné souřadnice.</span><span class="sxs-lookup"><span data-stu-id="654ac-130">Note that the red component is at half intensity when the horizontal coordinate is only 20 percent of the way from 0 to 200.</span></span>  
  
 <span data-ttu-id="654ac-131">Následující příklad nastavuje <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> vlastnost <xref:System.Drawing.Drawing2D.LinearGradientBrush> objekt, který chcete přidružit tři relativní intenzity tři relativní umístění.</span><span class="sxs-lookup"><span data-stu-id="654ac-131">The following example sets the <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> property of a <xref:System.Drawing.Drawing2D.LinearGradientBrush> object to associate three relative intensities with three relative positions.</span></span> <span data-ttu-id="654ac-132">Jako v předchozí tabulce je spojeno s relativní pozici 0,2 relativní intenzitou 0,5.</span><span class="sxs-lookup"><span data-stu-id="654ac-132">As in the preceding table, a relative intensity of 0.5 is associated with a relative position of 0.2.</span></span> <span data-ttu-id="654ac-133">Kód doplní elipsy a obdélníku s štětce přechodu.</span><span class="sxs-lookup"><span data-stu-id="654ac-133">The code fills an ellipse and a rectangle with the gradient brush.</span></span>  
  
 <span data-ttu-id="654ac-134">Následující obrázek znázorňuje výsledné elipsy a obdélník.</span><span class="sxs-lookup"><span data-stu-id="654ac-134">The following illustration shows the resulting ellipse and rectangle.</span></span>  
  
 <span data-ttu-id="654ac-135">![Lineárního přechodu](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")</span><span class="sxs-lookup"><span data-stu-id="654ac-135">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")</span></span>  
  
### <a name="to-customize-linear-gradients"></a><span data-ttu-id="654ac-136">Chcete-li přizpůsobit lineární přechody</span><span class="sxs-lookup"><span data-stu-id="654ac-136">To customize linear gradients</span></span>  
  
-   <span data-ttu-id="654ac-137">Předejte červeně neprůhledného černé a neprůhledného jako třetí a čtvrtý argument, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="654ac-137">Pass in the opaque black and opaque red as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 <span data-ttu-id="654ac-138">Přechody v předchozích ukázkách byly vodorovné; To znamená barva změní postupně jako přesunout společně žádné vodorovném řádku.</span><span class="sxs-lookup"><span data-stu-id="654ac-138">The gradients in the preceding examples have been horizontal; that is, the color changes gradually as you move along any horizontal line.</span></span> <span data-ttu-id="654ac-139">Můžete také definovat přechody vertikální a diagonálních přechody.</span><span class="sxs-lookup"><span data-stu-id="654ac-139">You can also define vertical gradients and diagonal gradients.</span></span>  
  
 <span data-ttu-id="654ac-140">Následující příklad předá body (0, 0) a (200, 100) <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="654ac-140">The following example passes the points (0, 0) and (200, 100) to a <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="654ac-141">Je přidružen modrou barvu (0, 0), a je přidružen zelenou barvu (200, 100).</span><span class="sxs-lookup"><span data-stu-id="654ac-141">The color blue is associated with (0, 0), and the color green is associated with (200, 100).</span></span> <span data-ttu-id="654ac-142">Řádek (s pera šířka 10) a elipsy jsou vyplněny lineární štětce přechodu.</span><span class="sxs-lookup"><span data-stu-id="654ac-142">A line (with pen width 10) and an ellipse are filled with the linear gradient brush.</span></span>  
  
 <span data-ttu-id="654ac-143">Následující obrázek znázorňuje řádku a se třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="654ac-143">The following illustration shows the line and the ellipse.</span></span> <span data-ttu-id="654ac-144">Všimněte si, že barvu v změny elipsy postupně jako přesunout společně žádné řádku, je paralelní na řádek prošla (0, 0) a (200, 100).</span><span class="sxs-lookup"><span data-stu-id="654ac-144">Note that the color in the ellipse changes gradually as you move along any line that is parallel to the line passing through (0, 0) and (200, 100).</span></span>  
  
 <span data-ttu-id="654ac-145">![Lineárního přechodu](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")</span><span class="sxs-lookup"><span data-stu-id="654ac-145">![Linear Gradient](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")</span></span>  
  
### <a name="to-create-diagonal-linear-gradients"></a><span data-ttu-id="654ac-146">Chcete-li vytvořit diagonálních lineární přechody</span><span class="sxs-lookup"><span data-stu-id="654ac-146">To create diagonal linear gradients</span></span>  
  
-   <span data-ttu-id="654ac-147">Předejte zeleně neprůhledného modré a neprůhledného jako třetí a čtvrtý argument, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="654ac-147">Pass in the opaque blue and opaque green as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="654ac-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="654ac-148">See Also</span></span>  
 [<span data-ttu-id="654ac-149">Použití štětce přechodu k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="654ac-149">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 [<span data-ttu-id="654ac-150">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="654ac-150">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
