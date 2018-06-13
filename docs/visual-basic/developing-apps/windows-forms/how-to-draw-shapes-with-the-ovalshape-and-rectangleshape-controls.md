---
title: 'Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OvalShape control [Visual Basic]
- shapes, drawing
- RectangleShape control [Visual Basic]
ms.assetid: 0275b4c6-7a13-46c8-90f3-61db308c6b5d
ms.openlocfilehash: f87865ba3aebe5739b87d6ae6bfeaa957af726d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592272"
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a><span data-ttu-id="6fdfd-102">Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="6fdfd-102">How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio)</span></span>
<span data-ttu-id="6fdfd-103">Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> řízení k vykreslení kroužky nebo elips ve formuláři nebo kontejneru, v době návrhu i v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> control to draw circles or ovals on a form or container, both at design time and at run time.</span></span> <span data-ttu-id="6fdfd-104">Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> řízení k vykreslení čtverce, obdélníku nebo obdélníků se zaoblenými hranami ve formuláři nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-104">You can use the <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control to draw squares, rectangles, or rectangles with rounded corners on a form or container.</span></span> <span data-ttu-id="6fdfd-105">Také můžete tento ovládací prvek pro kreslení tvarů v době návrhu i v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-105">You can also use this control to draw shapes both at design time and at run time.</span></span>  
  
 <span data-ttu-id="6fdfd-106">Vzhled obrazce můžete přizpůsobit tak, že změníte šířku, barvu a styl ohraničení.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-106">You can customize the appearance of a shape by changing the width, color, and style of the border.</span></span> <span data-ttu-id="6fdfd-107">Na pozadí obrazce je transparentní ve výchozím nastavení; můžete přizpůsobit na pozadí na plnou barvou, vzor, výplň přechodem (přechod z jedné barvy do jiného) nebo bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-107">The background of a shape is transparent by default; you can customize the background to display a solid color, a pattern, a gradient fill (transitioning from one color to another), or an image.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a><span data-ttu-id="6fdfd-108">Kreslení jednoduchý obrazec v době návrhu</span><span class="sxs-lookup"><span data-stu-id="6fdfd-108">To draw a simple shape at design time</span></span>  
  
1.  <span data-ttu-id="6fdfd-109">Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> nebo <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> řídit z **PowerPacks jazyka Visual Basic** karta (instalaci naleznete v tématu [ovládací prvky jazyka Visual Basic Power Pack](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) v **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-109">Drag the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> or <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control from the **Visual Basic PowerPacks** tab (to install, see [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md))in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6fdfd-110">Přetáhněte velikost a přesuňte velikost a umístění tvaru.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-110">Drag the sizing and move handles to size and position the shape.</span></span>  
  
     <span data-ttu-id="6fdfd-111">Můžete také upravit velikost a umístění tvaru změnou `Size` a `Position` vlastnosti v **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-111">You can also size and position the shape by changing the `Size` and `Position` properties in the **Properties** window.</span></span>  
  
     <span data-ttu-id="6fdfd-112">Chcete-li vytvořit obdélník se zaoblenými hranami, vyberte `CornerRadius` vlastnost v **vlastnosti** okno a nastavte ji na hodnotu, která je větší než 0.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-112">To create a rectangle with rounded corners, select the `CornerRadius` property in the **Properties** window and set it to a value that is greater than 0.</span></span>  
  
3.  <span data-ttu-id="6fdfd-113">V **vlastnosti** okno, Volitelně můžete nastavit další vlastnosti změnit vzhled tvaru.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-113">In the **Properties** window, optionally set additional properties to change the appearance of the shape.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a><span data-ttu-id="6fdfd-114">Kreslení obrazce jednoduché za běhu</span><span class="sxs-lookup"><span data-stu-id="6fdfd-114">To draw a simple shape at run time</span></span>  
  
1.  <span data-ttu-id="6fdfd-115">Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-115">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="6fdfd-116">V **přidat odkaz na** dialogové okno, vyberte **Microsoft.VisualBasic.PowerPacks.VS**a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-116">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6fdfd-117">V **Editor kódu**, přidejte `Imports` nebo `using` příkaz v horní části modulu:</span><span class="sxs-lookup"><span data-stu-id="6fdfd-117">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="6fdfd-118">Přidejte následující kód v `Event` postup:</span><span class="sxs-lookup"><span data-stu-id="6fdfd-118">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a><span data-ttu-id="6fdfd-119">Přizpůsobení tvarů</span><span class="sxs-lookup"><span data-stu-id="6fdfd-119">Customizing Shapes</span></span>  
 <span data-ttu-id="6fdfd-120">Pokud použijete výchozí nastavení <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> a <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládací prvky jsou zobrazeny s plnou černé ohraničení, které je jeden pixel široká a průhledné pozadí.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-120">When you use the default settings, the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> and <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls are displayed with a solid black border that is one pixel wide and a transparent background.</span></span> <span data-ttu-id="6fdfd-121">Šířky, stylu a barvy ohraničení můžete změnit nastavením vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-121">You can change the width, style, and color of the border by setting properties.</span></span> <span data-ttu-id="6fdfd-122">Další vlastnosti umožňují změnit pozadí obrazce plnou barvou, vzor, přechod nebo bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-122">Additional properties enable you to change the background of a shape to a solid color, a pattern, a gradient fill, or an image.</span></span>  
  
 <span data-ttu-id="6fdfd-123">Než změníte na pozadí obrazce, byste měli vědět, jak několik vlastností komunikovat.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-123">Before you change the background of a shape, you should know how several of the properties interact.</span></span>  
  
-   <span data-ttu-id="6fdfd-124"><xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Nastavení vlastnost nemá žádný vliv, pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-124">The <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> property setting has no effect unless the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="6fdfd-125">Pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> přepsání <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-125">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> overrides the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span></span>  
  
-   <span data-ttu-id="6fdfd-126">Pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> vlastnost nastavena na hodnotu vzor, jako <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> nebo <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, vzoru se zobrazí v <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-126">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to a pattern value such as <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> or <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, the pattern will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span></span> <span data-ttu-id="6fdfd-127">Zobrazí se na pozadí v <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, za předpokladu, že <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-127">The background will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, provided that the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="6fdfd-128">Aby bylo možné zobrazit výplň přechodem <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> musí být nastavena na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> a <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> vlastnost musí být nastavena na hodnotu než <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-128">In order to display a gradient fill, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property must be set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> and the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> property must be set to a value other than <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span></span>  
  
-   <span data-ttu-id="6fdfd-129">Nastavení <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> vlastnost pro bitovou kopii přepíše všechna ostatní nastavení pozadí.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-129">Setting the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> property to an image overrides all other background settings.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a><span data-ttu-id="6fdfd-130">Kreslení kruh, který má vlastní ohraničení</span><span class="sxs-lookup"><span data-stu-id="6fdfd-130">To draw a circle that has a custom border</span></span>  
  
1.  <span data-ttu-id="6fdfd-131">Přetáhněte `OvalShape` řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-131">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6fdfd-132">V **vlastnosti** okno v `Size` vlastnost, nastavte `Height` a `Width` na stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-132">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="6fdfd-133">Nastavte `BorderColor` vlastnost na požadovanou barvu.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-133">Set the `BorderColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="6fdfd-134">Nastavte `BorderStyle` vlastnost na jakoukoli jinou hodnotu než `Solid`.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-134">Set the `BorderStyle` property to any value other than `Solid`.</span></span>  
  
5.  <span data-ttu-id="6fdfd-135">Nastavte `BorderWidth` na velikost, které chcete v pixelech.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-135">Set the `BorderWidth` to the size that you want, in pixels.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a><span data-ttu-id="6fdfd-136">Kreslení kruh, který má plnou výplň</span><span class="sxs-lookup"><span data-stu-id="6fdfd-136">To draw a circle that has a solid fill</span></span>  
  
1.  <span data-ttu-id="6fdfd-137">Přetáhněte `OvalShape` řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-137">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6fdfd-138">V **vlastnosti** okno v `Size` vlastnost, nastavte `Height` a `Width` na stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-138">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="6fdfd-139">Nastavte `BackColor` vlastnost na požadovanou barvu.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-139">Set the `BackColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="6fdfd-140">Nastavte `BackStyle` vlastnost `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-140">Set the `BackStyle` property to `Opaque`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a><span data-ttu-id="6fdfd-141">Kreslení kruh, který má výplň vzorkem</span><span class="sxs-lookup"><span data-stu-id="6fdfd-141">To draw a circle that has a patterned fill</span></span>  
  
1.  <span data-ttu-id="6fdfd-142">Přetáhněte `OvalShape` řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-142">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6fdfd-143">V **vlastnosti** okno v `Size` vlastnost, nastavte `Height` a `Width` na stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-143">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="6fdfd-144">Nastavte `BackColor` vlastnost na barvu, která chcete použít pro na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-144">Set the `BackColor` property to the color that you want for the background.</span></span>  
  
4.  <span data-ttu-id="6fdfd-145">Nastavte `BackStyle` vlastnost `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-145">Set the `BackStyle` property to `Opaque`.</span></span>  
  
5.  <span data-ttu-id="6fdfd-146">Nastavte `FillColor` vlastnost na barvu, která chcete použít pro vzoru.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-146">Set the `FillColor` property to the color that you want for the pattern.</span></span>  
  
6.  <span data-ttu-id="6fdfd-147">Nastavte `FillStyle` vlastnost na jakoukoli jinou hodnotu než `Transparent` nebo `Solid`.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-147">Set the `FillStyle` property to any value other than `Transparent` or `Solid`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a><span data-ttu-id="6fdfd-148">Kreslení kruh, který má výplň přechodem</span><span class="sxs-lookup"><span data-stu-id="6fdfd-148">To draw a circle that has a gradient fill</span></span>  
  
1.  <span data-ttu-id="6fdfd-149">Přetáhněte `OvalShape` řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-149">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6fdfd-150">V **vlastnosti** okno v `Size` vlastnost, nastavte `Height` a `Width` na stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-150">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="6fdfd-151">Nastavte `FillColor` vlastnost na barvu, která chcete použít pro počáteční barvu.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-151">Set the `FillColor` property to the color that you want for the starting color.</span></span>  
  
4.  <span data-ttu-id="6fdfd-152">Nastavte `FillGradientColor` vlastnost na barvu, která chcete použít pro koncovou barvu.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-152">Set the `FillGradientColor` property to the color that you want for the ending color.</span></span>  
  
5.  <span data-ttu-id="6fdfd-153">Nastavte `FillGradientStyle` vlastnost na hodnotu jinou než `None`.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-153">Set the `FillGradientStyle` property to a value other than `None`.</span></span>  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a><span data-ttu-id="6fdfd-154">Kreslení kruh, který je vyplněn bitovou kopii</span><span class="sxs-lookup"><span data-stu-id="6fdfd-154">To draw a circle that is filled with an image</span></span>  
  
1.  <span data-ttu-id="6fdfd-155">Přetáhněte `OvalShape` řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-155">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="6fdfd-156">V **vlastnosti** okno v `Size` vlastnost, nastavte `Height` a `Width` na stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-156">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="6fdfd-157">Vyberte `BackgroundImage` vlastnost a klikněte na **třemi tečkami** tlačítko (...).</span><span class="sxs-lookup"><span data-stu-id="6fdfd-157">Select the `BackgroundImage` property and click the **ellipsis** button (...).</span></span>  
  
4.  <span data-ttu-id="6fdfd-158">V **vyberte prostředek** dialogové okno, vyberte bitovou kopii k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-158">In the **Select Resource** dialog box, select an image to display.</span></span> <span data-ttu-id="6fdfd-159">Pokud nejsou uvedeny žádné prostředky obrázků, klikněte na tlačítko **Import** a přejděte do umístění bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-159">If no image resources are listed, click **Import** to browse to the location of an image.</span></span>  
  
5.  <span data-ttu-id="6fdfd-160">Klikněte na tlačítko **OK** vložit bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="6fdfd-160">Click **OK** to insert the image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fdfd-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fdfd-161">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>  
 <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>  
 [<span data-ttu-id="6fdfd-162">Úvod k ovládacím prvkům Čára a Tvar</span><span class="sxs-lookup"><span data-stu-id="6fdfd-162">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="6fdfd-163">Postupy: Kreslení čar pomocí ovládacího prvku LineShape</span><span class="sxs-lookup"><span data-stu-id="6fdfd-163">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
