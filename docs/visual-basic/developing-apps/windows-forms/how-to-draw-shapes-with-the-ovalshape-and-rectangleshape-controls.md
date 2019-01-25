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
ms.openlocfilehash: fe937236332591f6065e618c49ca5cf2c54b987c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701219"
---
# <a name="how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls-visual-studio"></a><span data-ttu-id="5fad6-102">Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5fad6-102">How to: Draw Shapes with the OvalShape and RectangleShape Controls (Visual Studio)</span></span>
<span data-ttu-id="5fad6-103">Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> ovládací prvek nakreslit kruhy nebo elipsy ve formuláři nebo kontejneru, v době návrhu i době běhu.</span><span class="sxs-lookup"><span data-stu-id="5fad6-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> control to draw circles or ovals on a form or container, both at design time and at run time.</span></span> <span data-ttu-id="5fad6-104">Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládací prvek nakreslit čtverce, obdélníku nebo obdélníky zaoblené rohy ve formuláři nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5fad6-104">You can use the <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control to draw squares, rectangles, or rectangles with rounded corners on a form or container.</span></span> <span data-ttu-id="5fad6-105">Tento ovládací prvek lze také použít pro kreslení tvarů v době návrhu i době běhu.</span><span class="sxs-lookup"><span data-stu-id="5fad6-105">You can also use this control to draw shapes both at design time and at run time.</span></span>  
  
 <span data-ttu-id="5fad6-106">Můžete přizpůsobit vzhled tvaru tak, že změníte šířku, barvu a styl ohraničení.</span><span class="sxs-lookup"><span data-stu-id="5fad6-106">You can customize the appearance of a shape by changing the width, color, and style of the border.</span></span> <span data-ttu-id="5fad6-107">Pozadí obrazec je transparentní ve výchozím nastavení; můžete přizpůsobit zobrazení plnou barvu, vzor, přechodovou výplní (přechod z jedné barvy k jinému) nebo obrázek na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5fad6-107">The background of a shape is transparent by default; you can customize the background to display a solid color, a pattern, a gradient fill (transitioning from one color to another), or an image.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-design-time"></a><span data-ttu-id="5fad6-108">Chcete-li nakreslit jednoduchý obrazec v době návrhu</span><span class="sxs-lookup"><span data-stu-id="5fad6-108">To draw a simple shape at design time</span></span>  
  
1.  <span data-ttu-id="5fad6-109">Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> nebo <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládacího prvku **sady Visual Basic PowerPack** kartu (instalaci najdete v tématu [ovládací prvky jazyka Visual Basic Power Pack](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)) v **nástrojů** do ovládacího prvku formulář nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5fad6-109">Drag the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> or <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> control from the **Visual Basic PowerPacks** tab (to install, see [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md))in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="5fad6-110">Přetažením úchytů a přesunout obslužné rutiny na velikost a umístění obrazce.</span><span class="sxs-lookup"><span data-stu-id="5fad6-110">Drag the sizing and move handles to size and position the shape.</span></span>  
  
     <span data-ttu-id="5fad6-111">Můžete také změnit velikost a umístění obrazce tak, že změníte `Size` a `Position` vlastnosti **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="5fad6-111">You can also size and position the shape by changing the `Size` and `Position` properties in the **Properties** window.</span></span>  
  
     <span data-ttu-id="5fad6-112">Chcete-li vytvořit obdélník zaoblené rohy, vyberte `CornerRadius` vlastnost v **vlastnosti** okno a nastavte ho na hodnotu, která je větší než 0.</span><span class="sxs-lookup"><span data-stu-id="5fad6-112">To create a rectangle with rounded corners, select the `CornerRadius` property in the **Properties** window and set it to a value that is greater than 0.</span></span>  
  
3.  <span data-ttu-id="5fad6-113">V **vlastnosti** okna, Volitelně můžete nastavit další vlastnosti ke změně vzhledu tvar.</span><span class="sxs-lookup"><span data-stu-id="5fad6-113">In the **Properties** window, optionally set additional properties to change the appearance of the shape.</span></span>  
  
### <a name="to-draw-a-simple-shape-at-run-time"></a><span data-ttu-id="5fad6-114">Chcete-li nakreslit jednoduchý obrazec za běhu</span><span class="sxs-lookup"><span data-stu-id="5fad6-114">To draw a simple shape at run time</span></span>  
  
1.  <span data-ttu-id="5fad6-115">Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="5fad6-115">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="5fad6-116">V **přidat odkaz** dialogu **Microsoft.VisualBasic.PowerPacks.VS**a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="5fad6-116">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="5fad6-117">V **Editor kódu**, přidejte `Imports` nebo `using` příkazu v horní části modulu:</span><span class="sxs-lookup"><span data-stu-id="5fad6-117">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="5fad6-118">Přidejte následující kód `Event` postup:</span><span class="sxs-lookup"><span data-stu-id="5fad6-118">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.cs)]
     [!code-vb[VbPowerpacksShape#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls_1.vb)]  
  
## <a name="customizing-shapes"></a><span data-ttu-id="5fad6-119">Přizpůsobení obrazce</span><span class="sxs-lookup"><span data-stu-id="5fad6-119">Customizing Shapes</span></span>  
 <span data-ttu-id="5fad6-120">Pokud použijete výchozí nastavení <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> a <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládací prvky jsou zobrazeny s plnou černým ohraničením, které je jeden pixel široké a průhledné pozadí.</span><span class="sxs-lookup"><span data-stu-id="5fad6-120">When you use the default settings, the <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> and <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls are displayed with a solid black border that is one pixel wide and a transparent background.</span></span> <span data-ttu-id="5fad6-121">Šířky, stylu a barvy ohraničení můžete změnit nastavením vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5fad6-121">You can change the width, style, and color of the border by setting properties.</span></span> <span data-ttu-id="5fad6-122">Další vlastnosti umožňují změnit na pozadí obrazce plnou barvu, vzor, přechod nebo image.</span><span class="sxs-lookup"><span data-stu-id="5fad6-122">Additional properties enable you to change the background of a shape to a solid color, a pattern, a gradient fill, or an image.</span></span>  
  
 <span data-ttu-id="5fad6-123">Než změníte na pozadí tvaru, byste měli znát několik vlastností interakci.</span><span class="sxs-lookup"><span data-stu-id="5fad6-123">Before you change the background of a shape, you should know how several of the properties interact.</span></span>  
  
-   <span data-ttu-id="5fad6-124"><xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> Nastavení vlastnost nemá žádný vliv, pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="5fad6-124">The <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A> property setting has no effect unless the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="5fad6-125">Pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> přepsání <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="5fad6-125">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid>, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A> overrides the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>.</span></span>  
  
-   <span data-ttu-id="5fad6-126">Pokud <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> je nastavena na hodnotu vzor jako <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> nebo <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, vzor se zobrazí v <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="5fad6-126">If the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property is set to a pattern value such as <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Horizontal> or <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Vertical>, the pattern will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillColor%2A>.</span></span> <span data-ttu-id="5fad6-127">Zobrazí se na pozadí v <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>za předpokladu, že <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> je nastavena na <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span><span class="sxs-lookup"><span data-stu-id="5fad6-127">The background will be displayed in the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackColor%2A>, provided that the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackStyle%2A> property is set to <xref:Microsoft.VisualBasic.PowerPacks.BackStyle.Opaque>.</span></span>  
  
-   <span data-ttu-id="5fad6-128">Aby bylo možné zobrazit přechodovou výplní <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> musí být vlastnost nastavena na <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> a <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> vlastnost musí být nastavena na hodnotu jiné než <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="5fad6-128">In order to display a gradient fill, the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillStyle%2A> property must be set to <xref:Microsoft.VisualBasic.PowerPacks.FillStyle.Solid> and the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.FillGradientStyle%2A> property must be set to a value other than <xref:Microsoft.VisualBasic.PowerPacks.FillGradientStyle.None>.</span></span>  
  
-   <span data-ttu-id="5fad6-129">Nastavení <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> vlastností pro bitovou kopii přepíše všechna ostatní nastavení na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5fad6-129">Setting the <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape.BackgroundImage%2A> property to an image overrides all other background settings.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-custom-border"></a><span data-ttu-id="5fad6-130">Chcete-li nakreslit kruh, který má vlastní ohraničení</span><span class="sxs-lookup"><span data-stu-id="5fad6-130">To draw a circle that has a custom border</span></span>  
  
1.  <span data-ttu-id="5fad6-131">Přetáhněte `OvalShape` ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5fad6-131">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="5fad6-132">V **vlastnosti** okno v `Size` , nastavit `Height` a `Width` na stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5fad6-132">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="5fad6-133">Nastavte `BorderColor` vlastnost na požadovanou barvu.</span><span class="sxs-lookup"><span data-stu-id="5fad6-133">Set the `BorderColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="5fad6-134">Nastavte `BorderStyle` vlastnost na libovolnou hodnotu jinou než `Solid`.</span><span class="sxs-lookup"><span data-stu-id="5fad6-134">Set the `BorderStyle` property to any value other than `Solid`.</span></span>  
  
5.  <span data-ttu-id="5fad6-135">Nastavte `BorderWidth` velikosti, který chcete v pixelech.</span><span class="sxs-lookup"><span data-stu-id="5fad6-135">Set the `BorderWidth` to the size that you want, in pixels.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-solid-fill"></a><span data-ttu-id="5fad6-136">Chcete-li nakreslit kruh, který má plné barvy</span><span class="sxs-lookup"><span data-stu-id="5fad6-136">To draw a circle that has a solid fill</span></span>  
  
1.  <span data-ttu-id="5fad6-137">Přetáhněte `OvalShape` ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5fad6-137">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="5fad6-138">V **vlastnosti** okno v `Size` , nastavit `Height` a `Width` na stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5fad6-138">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="5fad6-139">Nastavte `BackColor` vlastnost na požadovanou barvu.</span><span class="sxs-lookup"><span data-stu-id="5fad6-139">Set the `BackColor` property to the color that you want.</span></span>  
  
4.  <span data-ttu-id="5fad6-140">Nastavte `BackStyle` vlastnost `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="5fad6-140">Set the `BackStyle` property to `Opaque`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-patterned-fill"></a><span data-ttu-id="5fad6-141">Chcete-li nakreslit kruh, který má výplň vzorkem</span><span class="sxs-lookup"><span data-stu-id="5fad6-141">To draw a circle that has a patterned fill</span></span>  
  
1.  <span data-ttu-id="5fad6-142">Přetáhněte `OvalShape` ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5fad6-142">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="5fad6-143">V **vlastnosti** okno v `Size` , nastavit `Height` a `Width` na stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5fad6-143">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="5fad6-144">Nastavte `BackColor` vlastnost na požadovanou barvu má pozadí.</span><span class="sxs-lookup"><span data-stu-id="5fad6-144">Set the `BackColor` property to the color that you want for the background.</span></span>  
  
4.  <span data-ttu-id="5fad6-145">Nastavte `BackStyle` vlastnost `Opaque`.</span><span class="sxs-lookup"><span data-stu-id="5fad6-145">Set the `BackStyle` property to `Opaque`.</span></span>  
  
5.  <span data-ttu-id="5fad6-146">Nastavte `FillColor` nastavte barvu, která chcete použít pro vzorek.</span><span class="sxs-lookup"><span data-stu-id="5fad6-146">Set the `FillColor` property to the color that you want for the pattern.</span></span>  
  
6.  <span data-ttu-id="5fad6-147">Nastavte `FillStyle` vlastnost na libovolnou hodnotu jinou než `Transparent` nebo `Solid`.</span><span class="sxs-lookup"><span data-stu-id="5fad6-147">Set the `FillStyle` property to any value other than `Transparent` or `Solid`.</span></span>  
  
#### <a name="to-draw-a-circle-that-has-a-gradient-fill"></a><span data-ttu-id="5fad6-148">Chcete-li nakreslit kruh, který má přechodovou výplní</span><span class="sxs-lookup"><span data-stu-id="5fad6-148">To draw a circle that has a gradient fill</span></span>  
  
1.  <span data-ttu-id="5fad6-149">Přetáhněte `OvalShape` ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5fad6-149">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="5fad6-150">V **vlastnosti** okno v `Size` , nastavit `Height` a `Width` na stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5fad6-150">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="5fad6-151">Nastavte `FillColor` nastavte barvu, která chcete použít pro počáteční barvu.</span><span class="sxs-lookup"><span data-stu-id="5fad6-151">Set the `FillColor` property to the color that you want for the starting color.</span></span>  
  
4.  <span data-ttu-id="5fad6-152">Nastavte `FillGradientColor` nastavte barvu, která chcete použít pro koncovou barvu.</span><span class="sxs-lookup"><span data-stu-id="5fad6-152">Set the `FillGradientColor` property to the color that you want for the ending color.</span></span>  
  
5.  <span data-ttu-id="5fad6-153">Nastavte `FillGradientStyle` vlastnost na hodnotu jinou než `None`.</span><span class="sxs-lookup"><span data-stu-id="5fad6-153">Set the `FillGradientStyle` property to a value other than `None`.</span></span>  
  
#### <a name="to-draw-a-circle-that-is-filled-with-an-image"></a><span data-ttu-id="5fad6-154">Chcete-li nakreslit kruh, který je vyplněna bitovou kopii</span><span class="sxs-lookup"><span data-stu-id="5fad6-154">To draw a circle that is filled with an image</span></span>  
  
1.  <span data-ttu-id="5fad6-155">Přetáhněte `OvalShape` ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5fad6-155">Drag the `OvalShape` control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="5fad6-156">V **vlastnosti** okno v `Size` , nastavit `Height` a `Width` na stejné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5fad6-156">In the **Properties** window, in the `Size` property, set `Height` and `Width` to equal values.</span></span>  
  
3.  <span data-ttu-id="5fad6-157">Vyberte `BackgroundImage` vlastnosti a kliknutím **tlačítko se třemi tečkami** tlačítko (...).</span><span class="sxs-lookup"><span data-stu-id="5fad6-157">Select the `BackgroundImage` property and click the **ellipsis** button (...).</span></span>  
  
4.  <span data-ttu-id="5fad6-158">V **vybrat prostředek** dialogové okno, vyberte obrázek, který se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="5fad6-158">In the **Select Resource** dialog box, select an image to display.</span></span> <span data-ttu-id="5fad6-159">Pokud nejsou uvedeny žádné prostředky bitové kopie, klikněte na tlačítko **Import** a přejděte do umístění obrázku.</span><span class="sxs-lookup"><span data-stu-id="5fad6-159">If no image resources are listed, click **Import** to browse to the location of an image.</span></span>  
  
5.  <span data-ttu-id="5fad6-160">Klikněte na tlačítko **OK** vložit obrázek.</span><span class="sxs-lookup"><span data-stu-id="5fad6-160">Click **OK** to insert the image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fad6-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fad6-161">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>
- <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>
- [<span data-ttu-id="5fad6-162">Úvod k ovládacím prvkům Čára a Tvar</span><span class="sxs-lookup"><span data-stu-id="5fad6-162">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [<span data-ttu-id="5fad6-163">Postupy: Kreslení čar pomocí ovládacího prvku LineShape</span><span class="sxs-lookup"><span data-stu-id="5fad6-163">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)
