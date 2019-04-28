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
ms.openlocfilehash: 306c042fe432f0c087ceb1b5ff6b5aec0fe0bbc7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748249"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="78436-102">Návod: Uspořádání obsahu WPF v modelu Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="78436-102">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="78436-103">Tento návod ukazuje způsob použití funkcí rozložení Windows Forms, jako je například ukotvení a zarovnávacích čar, k uspořádání ovládacích prvků Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="78436-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

 <span data-ttu-id="78436-104">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="78436-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="78436-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="78436-105">Create the project.</span></span>

- <span data-ttu-id="78436-106">Vytvoření ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="78436-106">Create the WPF control.</span></span>

- <span data-ttu-id="78436-107">Hostitelské ovládací prvky WPF v panelu rozložení.</span><span class="sxs-lookup"><span data-stu-id="78436-107">Host WPF controls in a layout panel.</span></span>

- <span data-ttu-id="78436-108">Pomocí zarovnávacích čar Zarovnat ovládací prvky WPF.</span><span class="sxs-lookup"><span data-stu-id="78436-108">Use snaplines to align WPF controls.</span></span>

- <span data-ttu-id="78436-109">Ukotvení a ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="78436-109">Anchor and dock WPF controls.</span></span>

> [!NOTE]
>  <span data-ttu-id="78436-110">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="78436-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="78436-111">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="78436-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="78436-112">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="78436-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="78436-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78436-113">Prerequisites</span></span>  
 <span data-ttu-id="78436-114">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="78436-114">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="78436-115">Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="78436-115">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="78436-116">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="78436-116">Creating the Project</span></span>  
 <span data-ttu-id="78436-117">Prvním krokem je vytvoření projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="78436-117">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78436-118">Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="78436-118">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="78436-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="78436-119">To create the project</span></span>  
  
- <span data-ttu-id="78436-120">Vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="78436-120">Create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="78436-121">Vytvoření ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="78436-121">Creating the WPF Control</span></span>  
 <span data-ttu-id="78436-122">Po přidání ovládacího prvku WPF do projektu, můžete je nastavit na formuláři.</span><span class="sxs-lookup"><span data-stu-id="78436-122">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="78436-123">Chcete-li vytvořit ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="78436-123">To create WPF controls</span></span>  
  
1. <span data-ttu-id="78436-124">Přidat nový WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="78436-124">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="78436-125">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="78436-125">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="78436-126">Další informace najdete v tématu [názorný postup: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="78436-126">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2. <span data-ttu-id="78436-127">V návrhovém zobrazení, ujistěte se, že `UserControl1` zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="78436-127">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="78436-128">Další informace najdete v tématu [jak: Vyberte a přesuňte prvků na návrhové ploše](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="78436-128">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>  
  
3. <span data-ttu-id="78436-129">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastností `200`.</span><span class="sxs-lookup"><span data-stu-id="78436-129">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4. <span data-ttu-id="78436-130">Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.</span><span class="sxs-lookup"><span data-stu-id="78436-130">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
5. <span data-ttu-id="78436-131">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="78436-131">Build the project.</span></span>  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="78436-132">Hostování ovládacích prvků WPF na panelu rozložení</span><span class="sxs-lookup"><span data-stu-id="78436-132">Hosting WPF Controls in a Layout Panel</span></span>  
 <span data-ttu-id="78436-133">Ovládací prvky WPF v panely rozložení můžete použít stejným způsobem, jakým používáte další ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="78436-133">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="78436-134">Na hostitelských ovládacích prvků WPF na panelu rozložení</span><span class="sxs-lookup"><span data-stu-id="78436-134">To host WPF controls in a layout panel</span></span>  
  
1. <span data-ttu-id="78436-135">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="78436-135">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2. <span data-ttu-id="78436-136">V **nástrojů**, přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="78436-136">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>  
  
3. <span data-ttu-id="78436-137">Na <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku panelu inteligentních značek, vyberte **odebrat poslední řádek**.</span><span class="sxs-lookup"><span data-stu-id="78436-137">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>  
  
4. <span data-ttu-id="78436-138">Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na větší šířku a výšku.</span><span class="sxs-lookup"><span data-stu-id="78436-138">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>  
  
5. <span data-ttu-id="78436-139">V **nástrojů**, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` do první buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78436-139">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="78436-140">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="78436-140">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
6. <span data-ttu-id="78436-141">V **nástrojů**, dvakrát klikněte na panel `UserControl1` pro vytvoření další instance v druhé buňce <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78436-141">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7. <span data-ttu-id="78436-142">V **Osnova dokumentu** okně `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="78436-142">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="78436-143">Další informace najdete v tématu [Osnova dokumentu – okno](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span><span class="sxs-lookup"><span data-stu-id="78436-143">For more information, see [Document Outline Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span></span>  
  
8. <span data-ttu-id="78436-144">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Padding%2A> vlastnost `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="78436-144">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>  
  
     <span data-ttu-id="78436-145">Obě <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky se přizpůsobí do nového rozložení.</span><span class="sxs-lookup"><span data-stu-id="78436-145">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>  
  
## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="78436-146">Zarovnání ovládacích prvků WPF pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="78436-146">Using Snaplines to Align WPF Controls</span></span>  
 <span data-ttu-id="78436-147">Zarovnávacích čar bylo možné snadno zarovnání ovládacích prvků ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="78436-147">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="78436-148">Zarovnání ovládacích prvků WPF také můžete použít zarovnávacích čar.</span><span class="sxs-lookup"><span data-stu-id="78436-148">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="78436-149">Další informace najdete v tématu [názorný postup: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="78436-149">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="78436-150">Určuje zarovnání WPF pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="78436-150">To use snaplines to align WPF controls</span></span>  
  
1. <span data-ttu-id="78436-151">Z **nástrojů**, přetáhněte instance `UserControl1` do formuláře a umístěte ji v prostoru pod <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78436-151">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="78436-152">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="78436-152">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>  
  
2. <span data-ttu-id="78436-153">Pomocí zarovnávacích čar, zarovnání na levý okraj `elementHost3` s levým okrajem <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78436-153">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3. <span data-ttu-id="78436-154">Pomocí zarovnávacích čar, velikost `elementHost3` podle stejné šířky, jako <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78436-154">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4. <span data-ttu-id="78436-155">Přesunout `elementHost3` směrem k <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek, dokud se nezobrazí snapline – System center mezi ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="78436-155">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>  
  
5. <span data-ttu-id="78436-156">V **vlastnosti** okno, nastavte hodnotu vlastnosti okraj k `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="78436-156">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>  
  
6. <span data-ttu-id="78436-157">Přesunout `elementHost3` klávesou <xref:System.Windows.Forms.TableLayoutPanel> ovládací snapline – System center, zobrazí se znovu.</span><span class="sxs-lookup"><span data-stu-id="78436-157">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="78436-158">Snapline – System center teď uvádí rozpětí od 20.</span><span class="sxs-lookup"><span data-stu-id="78436-158">The center snapline now indicates a margin of 20.</span></span>  
  
7. <span data-ttu-id="78436-159">Přesunout `elementHost3` doprava, dokud jeho levé hrany v souladu s levým okrajem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="78436-159">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>  
  
8. <span data-ttu-id="78436-160">Umožňuje změnit šířku `elementHost3` až do jeho pravé hrany v souladu s pravým okrajem `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="78436-160">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>  
  
## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="78436-161">Ukotvení a dokování ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="78436-161">Anchoring and Docking WPF Controls</span></span>  
 <span data-ttu-id="78436-162">Ovládací prvek WPF hostované ve formuláři obsahuje stejné ukotvení a dokování chování jako ostatní ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="78436-162">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="78436-163">Ukotvení a ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="78436-163">To anchor and dock WPF controls</span></span>  
  
1. <span data-ttu-id="78436-164">Vyberte `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="78436-164">Select `elementHost1`.</span></span>  
  
2. <span data-ttu-id="78436-165">V **vlastnosti** okno, nastaveno <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost **nahoře, dole, vlevo, vpravo**.</span><span class="sxs-lookup"><span data-stu-id="78436-165">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>  
  
3. <span data-ttu-id="78436-166">Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na větší velikost.</span><span class="sxs-lookup"><span data-stu-id="78436-166">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>  
  
     <span data-ttu-id="78436-167">`elementHost1` Řídit změní tak, aby vyplnil buňku.</span><span class="sxs-lookup"><span data-stu-id="78436-167">The `elementHost1` control resizes to fill the cell.</span></span>  
  
4. <span data-ttu-id="78436-168">Vyberte `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="78436-168">Select `elementHost2`.</span></span>  
  
5. <span data-ttu-id="78436-169">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="78436-169">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="78436-170">`elementHost2` Řídit změní tak, aby vyplnil buňku.</span><span class="sxs-lookup"><span data-stu-id="78436-170">The `elementHost2` control resizes to fill the cell.</span></span>  
  
6. <span data-ttu-id="78436-171">Vyberte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="78436-171">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7. <span data-ttu-id="78436-172">Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="78436-172">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>  
  
8. <span data-ttu-id="78436-173">Vyberte `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="78436-173">Select `elementHost3`.</span></span>  
  
9. <span data-ttu-id="78436-174">Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="78436-174">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="78436-175">`elementHost3` Řídit změní tak, aby vyplnil zbývající místo na formuláři.</span><span class="sxs-lookup"><span data-stu-id="78436-175">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>  
  
10. <span data-ttu-id="78436-176">Změnit velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="78436-176">Resize the form.</span></span>  
  
     <span data-ttu-id="78436-177">Všechny tři <xref:System.Windows.Forms.Integration.ElementHost> odpovídajícím způsobem změňte velikost ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="78436-177">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>  
  
     <span data-ttu-id="78436-178">Další informace najdete v tématu [jak: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="78436-178">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78436-179">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78436-179">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="78436-180">Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="78436-180">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="78436-181">Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu</span><span class="sxs-lookup"><span data-stu-id="78436-181">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="78436-182">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="78436-182">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="78436-183">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="78436-183">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="78436-184">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="78436-184">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="78436-185">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="78436-185">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
