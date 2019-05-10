---
title: 'Návod: Uspořádání obsahu WPF v modelu Windows Forms během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
ms.openlocfilehash: a8f690438136450cb12dbcf5e17ddfcca617457e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211463"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="b3396-102">Návod: Uspořádání obsahu WPF ve Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="b3396-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="b3396-103">Tento návod ukazuje způsob použití funkcí rozložení Windows Forms, jako je například ukotvení a zarovnávacích čar, k uspořádání ovládacích prvků Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="b3396-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

<span data-ttu-id="b3396-104">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b3396-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="b3396-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="b3396-105">Create the project.</span></span>

- <span data-ttu-id="b3396-106">Vytvoření ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="b3396-106">Create the WPF control.</span></span>

- <span data-ttu-id="b3396-107">Hostitelské ovládací prvky WPF v panelu rozložení.</span><span class="sxs-lookup"><span data-stu-id="b3396-107">Host WPF controls in a layout panel.</span></span>

- <span data-ttu-id="b3396-108">Pomocí zarovnávacích čar Zarovnat ovládací prvky WPF.</span><span class="sxs-lookup"><span data-stu-id="b3396-108">Use snaplines to align WPF controls.</span></span>

- <span data-ttu-id="b3396-109">Ukotvení a ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="b3396-109">Anchor and dock WPF controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b3396-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3396-110">Prerequisites</span></span>

<span data-ttu-id="b3396-111">Visual Studio k dokončení tohoto návodu potřebujete.</span><span class="sxs-lookup"><span data-stu-id="b3396-111">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="b3396-112">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="b3396-112">Create the project</span></span>

<span data-ttu-id="b3396-113">Otevřít Visual Studio a vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="b3396-113">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="b3396-114">Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b3396-114">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="b3396-115">Vytvoření ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="b3396-115">Create the WPF control</span></span>

<span data-ttu-id="b3396-116">Po přidání ovládacího prvku WPF do projektu, můžete je nastavit na formuláři.</span><span class="sxs-lookup"><span data-stu-id="b3396-116">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="b3396-117">Přidat nový WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="b3396-117">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="b3396-118">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="b3396-118">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="b3396-119">Další informace najdete v tématu [názorný postup: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="b3396-119">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="b3396-120">V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="b3396-120">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="b3396-121">Další informace najdete v tématu [jak: Vyberte a přesuňte prvků na návrhové ploše](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b3396-121">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="b3396-122">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.</span><span class="sxs-lookup"><span data-stu-id="b3396-122">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="b3396-123">Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.</span><span class="sxs-lookup"><span data-stu-id="b3396-123">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>

5. <span data-ttu-id="b3396-124">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="b3396-124">Build the project.</span></span>

## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="b3396-125">Hostování ovládacích prvků WPF na panelu rozložení</span><span class="sxs-lookup"><span data-stu-id="b3396-125">Hosting WPF Controls in a Layout Panel</span></span>
 <span data-ttu-id="b3396-126">Ovládací prvky WPF v panely rozložení můžete použít stejným způsobem, jakým používáte další ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b3396-126">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="b3396-127">Na hostitelských ovládacích prvků WPF na panelu rozložení</span><span class="sxs-lookup"><span data-stu-id="b3396-127">To host WPF controls in a layout panel</span></span>

1. <span data-ttu-id="b3396-128">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="b3396-128">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="b3396-129">V **nástrojů**, přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="b3396-129">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="b3396-130">Na <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku panelu inteligentních značek, vyberte **odebrat poslední řádek**.</span><span class="sxs-lookup"><span data-stu-id="b3396-130">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="b3396-131">Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na větší šířku a výšku.</span><span class="sxs-lookup"><span data-stu-id="b3396-131">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="b3396-132">V **nástrojů**, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` do první buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b3396-132">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

     <span data-ttu-id="b3396-133">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="b3396-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="b3396-134">V **nástrojů**, dvakrát klikněte na panel `UserControl1` pro vytvoření další instance v druhé buňce <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b3396-134">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="b3396-135">V **Osnova dokumentu** okně `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="b3396-135">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="b3396-136">Další informace najdete v tématu [Osnova dokumentu – okno](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span><span class="sxs-lookup"><span data-stu-id="b3396-136">For more information, see [Document Outline Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span></span>

8. <span data-ttu-id="b3396-137">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Padding%2A> vlastnost `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="b3396-137">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>

     <span data-ttu-id="b3396-138">Obě <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky se přizpůsobí do nového rozložení.</span><span class="sxs-lookup"><span data-stu-id="b3396-138">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="b3396-139">Zarovnání ovládacích prvků WPF pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="b3396-139">Using Snaplines to Align WPF Controls</span></span>
 <span data-ttu-id="b3396-140">Zarovnávacích čar bylo možné snadno zarovnání ovládacích prvků ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="b3396-140">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="b3396-141">Zarovnání ovládacích prvků WPF také můžete použít zarovnávacích čar.</span><span class="sxs-lookup"><span data-stu-id="b3396-141">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="b3396-142">Další informace najdete v tématu [názorný postup: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="b3396-142">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="b3396-143">Určuje zarovnání WPF pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="b3396-143">To use snaplines to align WPF controls</span></span>

1. <span data-ttu-id="b3396-144">Z **nástrojů**, přetáhněte instance `UserControl1` do formuláře a umístěte ji v prostoru pod <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b3396-144">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

     <span data-ttu-id="b3396-145">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="b3396-145">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="b3396-146">Pomocí zarovnávacích čar, zarovnání na levý okraj `elementHost3` s levým okrajem <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b3396-146">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="b3396-147">Pomocí zarovnávacích čar, velikost `elementHost3` podle stejné šířky, jako <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b3396-147">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="b3396-148">Přesunout `elementHost3` směrem k <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek, dokud se nezobrazí snapline – System center mezi ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="b3396-148">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="b3396-149">V **vlastnosti** okno, nastavte hodnotu vlastnosti okraj k `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="b3396-149">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>

6. <span data-ttu-id="b3396-150">Přesunout `elementHost3` klávesou <xref:System.Windows.Forms.TableLayoutPanel> ovládací snapline – System center, zobrazí se znovu.</span><span class="sxs-lookup"><span data-stu-id="b3396-150">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="b3396-151">Snapline – System center teď uvádí rozpětí od 20.</span><span class="sxs-lookup"><span data-stu-id="b3396-151">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="b3396-152">Přesunout `elementHost3` doprava, dokud jeho levé hrany v souladu s levým okrajem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="b3396-152">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="b3396-153">Umožňuje změnit šířku `elementHost3` až do jeho pravé hrany v souladu s pravým okrajem `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="b3396-153">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="b3396-154">Ukotvení a dokování ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="b3396-154">Anchoring and Docking WPF Controls</span></span>
 <span data-ttu-id="b3396-155">Ovládací prvek WPF hostované ve formuláři obsahuje stejné ukotvení a dokování chování jako ostatní ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b3396-155">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="b3396-156">Ukotvení a ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="b3396-156">To anchor and dock WPF controls</span></span>

1. <span data-ttu-id="b3396-157">Vyberte `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="b3396-157">Select `elementHost1`.</span></span>

2. <span data-ttu-id="b3396-158">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost **nahoře, dole, vlevo, vpravo**.</span><span class="sxs-lookup"><span data-stu-id="b3396-158">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="b3396-159">Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na větší velikost.</span><span class="sxs-lookup"><span data-stu-id="b3396-159">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

     <span data-ttu-id="b3396-160">`elementHost1` Řídit změní tak, aby vyplnil buňku.</span><span class="sxs-lookup"><span data-stu-id="b3396-160">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="b3396-161">Vyberte `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="b3396-161">Select `elementHost2`.</span></span>

5. <span data-ttu-id="b3396-162">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="b3396-162">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

     <span data-ttu-id="b3396-163">`elementHost2` Řídit změní tak, aby vyplnil buňku.</span><span class="sxs-lookup"><span data-stu-id="b3396-163">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="b3396-164">Vyberte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b3396-164">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="b3396-165">Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="b3396-165">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="b3396-166">Vyberte `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="b3396-166">Select `elementHost3`.</span></span>

9. <span data-ttu-id="b3396-167">Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="b3396-167">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

     <span data-ttu-id="b3396-168">`elementHost3` Řídit změní tak, aby vyplnil zbývající místo na formuláři.</span><span class="sxs-lookup"><span data-stu-id="b3396-168">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="b3396-169">Změnit velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="b3396-169">Resize the form.</span></span>

     <span data-ttu-id="b3396-170">Všechny tři <xref:System.Windows.Forms.Integration.ElementHost> odpovídajícím způsobem změňte velikost ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="b3396-170">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

     <span data-ttu-id="b3396-171">Další informace najdete v tématu [jak: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="b3396-171">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3396-172">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3396-172">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="b3396-173">Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b3396-173">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="b3396-174">Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu</span><span class="sxs-lookup"><span data-stu-id="b3396-174">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="b3396-175">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="b3396-175">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="b3396-176">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="b3396-176">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="b3396-177">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="b3396-177">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="b3396-178">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b3396-178">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
