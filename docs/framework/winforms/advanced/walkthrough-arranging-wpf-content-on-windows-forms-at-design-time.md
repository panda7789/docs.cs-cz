---
title: 'Návod: Uspořádání obsahu WPF ve Windows Forms během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9db49ae299870479a5cfa6372c25d793a92ff8f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460682"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="20e2b-102">Návod: uspořádání obsahu WPF v model Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="20e2b-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="20e2b-103">V tomto článku se dozvíte, jak používat funkce model Windows Forms rozložení, jako je například ukotvení a zarovnávacím čárám, k uspořádání ovládacích prvků Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="20e2b-103">This article shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="20e2b-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20e2b-104">Prerequisites</span></span>

<span data-ttu-id="20e2b-105">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20e2b-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="20e2b-106">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="20e2b-106">Create the project</span></span>

<span data-ttu-id="20e2b-107">Otevřete Visual Studio a vytvořte nový projekt aplikace model Windows Forms v Visual Basic nebo vizuálu C# s názvem `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="20e2b-108">Při hostování obsahu WPF jsou podporovány C# pouze projekty a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="20e2b-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="20e2b-109">Vytvoření ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="20e2b-109">Create the WPF control</span></span>

<span data-ttu-id="20e2b-110">Po přidání ovládacího prvku WPF do projektu jej můžete uspořádat na formuláři.</span><span class="sxs-lookup"><span data-stu-id="20e2b-110">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="20e2b-111">Přidejte do projektu novou <xref:System.Windows.Controls.UserControl> WPF.</span><span class="sxs-lookup"><span data-stu-id="20e2b-111">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="20e2b-112">Použijte výchozí název pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="20e2b-113">Další informace najdete v tématu [Návod: vytvoření nového obsahu WPF na model Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="20e2b-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="20e2b-114">V zobrazení Návrh se ujistěte, že je vybrána možnost `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="20e2b-115">V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="20e2b-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="20e2b-116">Nastavte hodnotu vlastnosti <xref:System.Windows.Controls.Control.Background%2A> na **modrou**.</span><span class="sxs-lookup"><span data-stu-id="20e2b-116">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

5. <span data-ttu-id="20e2b-117">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="20e2b-117">Build the project.</span></span>

## <a name="host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="20e2b-118">Hostování ovládacích prvků WPF na panelu rozložení</span><span class="sxs-lookup"><span data-stu-id="20e2b-118">Host WPF controls in a layout panel</span></span>

<span data-ttu-id="20e2b-119">Ovládací prvky WPF lze v panelech rozložení použít stejným způsobem jako jiné ovládací prvky model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="20e2b-119">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

1. <span data-ttu-id="20e2b-120">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="20e2b-120">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="20e2b-121">V **sadě nástrojů**přetáhněte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="20e2b-121">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="20e2b-122">Na panelu inteligentních značek ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> vyberte **Odebrat poslední řádek**.</span><span class="sxs-lookup"><span data-stu-id="20e2b-122">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="20e2b-123">Změňte velikost ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> na větší šířku a výšku.</span><span class="sxs-lookup"><span data-stu-id="20e2b-123">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="20e2b-124">V sadě **nástrojů**poklikejte na `UserControl1` pro vytvoření instance `UserControl1` v první buňce ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="20e2b-124">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="20e2b-125">Instance `UserControl1` je hostována v novém ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-125">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="20e2b-126">V **sadě nástrojů**poklikejte na `UserControl1` pro vytvoření další instance v druhé buňce ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="20e2b-126">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="20e2b-127">V okně **Osnova dokumentu** vyberte `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-127">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span>

8. <span data-ttu-id="20e2b-128">V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> na **10, 10, 10, 10**.</span><span class="sxs-lookup"><span data-stu-id="20e2b-128">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to **10, 10, 10, 10**.</span></span>

   <span data-ttu-id="20e2b-129">Velikost obou <xref:System.Windows.Forms.Integration.ElementHost>ch ovládacích prvků se přizpůsobí novému rozložení.</span><span class="sxs-lookup"><span data-stu-id="20e2b-129">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="20e2b-130">Použití zarovnávacím čárám k zarovnání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="20e2b-130">Use snaplines to align WPF controls</span></span>

<span data-ttu-id="20e2b-131">Zarovnávacím čárám umožňuje snadné zarovnání ovládacích prvků na formuláři.</span><span class="sxs-lookup"><span data-stu-id="20e2b-131">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="20e2b-132">Zarovnávacím čárám můžete použít i k zarovnání ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="20e2b-132">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="20e2b-133">Další informace najdete v tématu [Návod: uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="20e2b-133">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

1. <span data-ttu-id="20e2b-134">Z **panelu nástrojů**přetáhněte instanci `UserControl1` do formuláře a umístěte ji do prostoru pod ovládacím prvkem <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="20e2b-134">From the **Toolbox**, drag an instance of `UserControl1` onto the form, and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="20e2b-135">Instance `UserControl1` je hostována v novém ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> s názvem `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-135">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="20e2b-136">Pomocí zarovnávacím čárám zarovnejte levý okraj `elementHost3` s levým okrajem ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="20e2b-136">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="20e2b-137">Pomocí zarovnávacím čárám velikost `elementHost3` se stejnou šířkou jako <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="20e2b-137">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="20e2b-138">Přesuňte `elementHost3` směrem k ovládacímu prvku <xref:System.Windows.Forms.TableLayoutPanel> dokud se mezi ovládacími prvky snapline střed.</span><span class="sxs-lookup"><span data-stu-id="20e2b-138">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="20e2b-139">V okně **vlastnosti** nastavte hodnotu vlastnosti okraj na **20, 20, 20, 20**.</span><span class="sxs-lookup"><span data-stu-id="20e2b-139">In the **Properties** window, set the value of the Margin property to **20, 20, 20, 20**.</span></span>

6. <span data-ttu-id="20e2b-140">Přesuňte `elementHost3` pryč od ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel>, dokud se znovu neobjeví snapline Center.</span><span class="sxs-lookup"><span data-stu-id="20e2b-140">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="20e2b-141">Centrum snapline nyní indikuje okraj 20.</span><span class="sxs-lookup"><span data-stu-id="20e2b-141">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="20e2b-142">Přesune `elementHost3` doprava, dokud její levý okraj není zarovnán s levým okrajem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-142">Move `elementHost3` to the right until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="20e2b-143">Změní šířku `elementHost3`, dokud její pravý okraj není zarovnán s pravým okrajem `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-143">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchor-and-dock-wpf-controls"></a><span data-ttu-id="20e2b-144">Ukotvení a ukotvení ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="20e2b-144">Anchor and dock WPF controls</span></span>

<span data-ttu-id="20e2b-145">Ovládací prvek WPF hostovaný na formuláři má stejné chování při ukotvení a ukotvení jako jiné ovládací prvky model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="20e2b-145">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

1. <span data-ttu-id="20e2b-146">Vyberte `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-146">Select `elementHost1`.</span></span>

2. <span data-ttu-id="20e2b-147">V okně **vlastnosti** nastavte vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> na **nahoře, dole, vlevo, vpravo**.</span><span class="sxs-lookup"><span data-stu-id="20e2b-147">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="20e2b-148">Změňte velikost ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> na větší velikost.</span><span class="sxs-lookup"><span data-stu-id="20e2b-148">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

   <span data-ttu-id="20e2b-149">Ovládací prvek `elementHost1` mění velikost pro vyplnění buňky.</span><span class="sxs-lookup"><span data-stu-id="20e2b-149">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="20e2b-150">Vyberte `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-150">Select `elementHost2`.</span></span>

5. <span data-ttu-id="20e2b-151">V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="20e2b-151">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="20e2b-152">Ovládací prvek `elementHost2` mění velikost pro vyplnění buňky.</span><span class="sxs-lookup"><span data-stu-id="20e2b-152">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="20e2b-153">Vyberte ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="20e2b-153">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="20e2b-154">Nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="20e2b-154">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="20e2b-155">Vyberte `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="20e2b-155">Select `elementHost3`.</span></span>

9. <span data-ttu-id="20e2b-156">Nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="20e2b-156">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="20e2b-157">Ovládací prvek `elementHost3` mění velikost, aby vyplnil zbývající místo ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="20e2b-157">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="20e2b-158">Změňte velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="20e2b-158">Resize the form.</span></span>

    <span data-ttu-id="20e2b-159">Všechny tři <xref:System.Windows.Forms.Integration.ElementHost> řídí správné přizpůsobení velikosti.</span><span class="sxs-lookup"><span data-stu-id="20e2b-159">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

    <span data-ttu-id="20e2b-160">Další informace naleznete v tématu [Postupy: ukotvení a ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="20e2b-160">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="20e2b-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20e2b-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="20e2b-162">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="20e2b-162">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="20e2b-163">Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu</span><span class="sxs-lookup"><span data-stu-id="20e2b-163">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="20e2b-164">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="20e2b-164">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="20e2b-165">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="20e2b-165">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="20e2b-166">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="20e2b-166">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="20e2b-167">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="20e2b-167">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
