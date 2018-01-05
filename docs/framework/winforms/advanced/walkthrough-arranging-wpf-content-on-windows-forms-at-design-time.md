---
title: "Návod: Uspořádání obsahu WPF ve Windows Forms během návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c222e6f43bd595d264caeca2d9f79f7845f7f99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="c1bb8-102">Návod: Uspořádání obsahu WPF ve Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="c1bb8-102">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="c1bb8-103">Tento návod ukazuje, jak používat funkce rozložení Windows Forms, jako je například ukotvení a zarovnávací čáry, k uspořádání ovládacích prvků Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="c1bb8-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>  
  
 <span data-ttu-id="c1bb8-104">V tomto návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="c1bb8-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="c1bb8-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-105">Create the project.</span></span>  
  
-   <span data-ttu-id="c1bb8-106">Vytvoření ovládacího prvku WPF.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="c1bb8-107">Hostitelské ovládací prvky WPF panelu rozložení.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-107">Host WPF controls in a layout panel.</span></span>  
  
-   <span data-ttu-id="c1bb8-108">Zarovnávací čáry použijte k zarovnání ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-108">Use snaplines to align WPF controls.</span></span>  
  
-   <span data-ttu-id="c1bb8-109">Ukotvení a dokování ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-109">Anchor and dock WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1bb8-110">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c1bb8-111">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c1bb8-112">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c1bb8-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c1bb8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1bb8-113">Prerequisites</span></span>  
 <span data-ttu-id="c1bb8-114">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="c1bb8-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="c1bb8-115">.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="c1bb8-116">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c1bb8-116">Creating the Project</span></span>  
 <span data-ttu-id="c1bb8-117">Prvním krokem je vytvoření projektu modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-117">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1bb8-118">Pokud hostování obsahu subsystému WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-118">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="c1bb8-119">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c1bb8-119">To create the project</span></span>  
  
-   <span data-ttu-id="c1bb8-120">Vytvořte nový projekt aplikace Windows Forms v jazyce Visual Basic a Visual C# s názvem `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-120">Create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="c1bb8-121">Vytvoření ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="c1bb8-121">Creating the WPF Control</span></span>  
 <span data-ttu-id="c1bb8-122">Po přidání ovládací prvek WPF do projektu, můžete ho uspořádat na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-122">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="c1bb8-123">Chcete-li vytvořit ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c1bb8-123">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="c1bb8-124">Přidat nové WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-124">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="c1bb8-125">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-125">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="c1bb8-126">Další informace najdete v tématu [návod: vytvoření nové WPF obsahu v aplikaci Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c1bb8-126">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="c1bb8-127">V návrhovém zobrazení, ujistěte se, že `UserControl1` je vybrána.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-127">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="c1bb8-128">Další informace najdete v tématu [postup: vyberte a přesunout elementů na návrhovou plochu](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="c1bb8-128">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="c1bb8-129">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti, které chcete `200`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-129">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="c1bb8-130">Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-130">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
5.  <span data-ttu-id="c1bb8-131">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-131">Build the project.</span></span>  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="c1bb8-132">Hostování ovládacích prvků WPF panelu rozložení</span><span class="sxs-lookup"><span data-stu-id="c1bb8-132">Hosting WPF Controls in a Layout Panel</span></span>  
 <span data-ttu-id="c1bb8-133">Můžete v panelů rozložení ovládacích prvků WPF stejným způsobem, jakým používáte další ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-133">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="c1bb8-134">Na hostiteli ovládacích prvků WPF panelu rozložení</span><span class="sxs-lookup"><span data-stu-id="c1bb8-134">To host WPF controls in a layout panel</span></span>  
  
1.  <span data-ttu-id="c1bb8-135">Otevřete `Form1` v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-135">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="c1bb8-136">V **sada nástrojů**, přetáhněte ji <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-136">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>  
  
3.  <span data-ttu-id="c1bb8-137">Na <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku inteligentní panel, vyberte **odebere poslední řádek**.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-137">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>  
  
4.  <span data-ttu-id="c1bb8-138">Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> řízení větší šířku a výšku.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-138">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>  
  
5.  <span data-ttu-id="c1bb8-139">V **sada nástrojů**, dvakrát klikněte na `UserControl1` k vytvoření instance `UserControl1` v první buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-139">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="c1bb8-140">Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-140">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
6.  <span data-ttu-id="c1bb8-141">V **sada nástrojů**, dvakrát klikněte na `UserControl1` vytvořit jiná instance do druhé buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-141">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="c1bb8-142">V **Osnova dokumentu** vyberte `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-142">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="c1bb8-143">Další informace najdete v tématu [Osnova dokumentu – okno](http://msdn.microsoft.com/en-us/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span><span class="sxs-lookup"><span data-stu-id="c1bb8-143">For more information, see [Document Outline Window](http://msdn.microsoft.com/en-us/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span></span>  
  
8.  <span data-ttu-id="c1bb8-144">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Padding%2A> vlastnost `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-144">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>  
  
     <span data-ttu-id="c1bb8-145">Obě <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky jsou po změně velikosti a nevejde se do nové rozložení.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-145">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>  
  
## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="c1bb8-146">Chcete-li zarovnat ovládacích prvků WPF pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="c1bb8-146">Using Snaplines to Align WPF Controls</span></span>  
 <span data-ttu-id="c1bb8-147">Zarovnávací čáry povolit snadno zarovnání ovládacích prvků na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-147">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="c1bb8-148">Chcete-li zarovnat vaší ovládacích prvků WPF také můžete zarovnávací čáry.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-148">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="c1bb8-149">Další informace najdete v tématu [návod: uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="c1bb8-149">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="c1bb8-150">Zarovnat WPF pomocí zarovnávacích čar ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="c1bb8-150">To use snaplines to align WPF controls</span></span>  
  
1.  <span data-ttu-id="c1bb8-151">Z **sada nástrojů**, přetáhněte instanci `UserControl1` do formuláře a umístěte jej do prostoru pod <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-151">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="c1bb8-152">Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-152">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>  
  
2.  <span data-ttu-id="c1bb8-153">Pomocí zarovnávacích čar, Zarovnat je levý okraj `elementHost3` s levým okrajem <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-153">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="c1bb8-154">Pomocí zarovnávacích čar, velikost `elementHost3` stejné šířky, jako <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-154">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="c1bb8-155">Přesunout `elementHost3` směrem k <xref:System.Windows.Forms.TableLayoutPanel> řízení, dokud se nezobrazí center snapline mezi ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-155">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>  
  
5.  <span data-ttu-id="c1bb8-156">V **vlastnosti** okno, nastavte hodnotu vlastnosti okraj `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-156">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>  
  
6.  <span data-ttu-id="c1bb8-157">Přesunout `elementHost3` směrem od <xref:System.Windows.Forms.TableLayoutPanel> řízení dokud center snapline se znovu nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-157">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="c1bb8-158">Center snapline nyní označuje okraj 20.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-158">The center snapline now indicates a margin of 20.</span></span>  
  
7.  <span data-ttu-id="c1bb8-159">Přesunout `elementHost3` vpravo, dokud jeho levé hrany zarovnaná s levým okrajem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-159">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>  
  
8.  <span data-ttu-id="c1bb8-160">Umožňuje změnit šířku `elementHost3` dokud jeho pravé hrany zarovnán podle pravé hrany `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-160">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>  
  
## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="c1bb8-161">Ukotvení a dokování ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c1bb8-161">Anchoring and Docking WPF Controls</span></span>  
 <span data-ttu-id="c1bb8-162">Ovládací prvek WPF hostované ve formuláři má stejné ukotvení a dokování chování jako další ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-162">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="c1bb8-163">Chcete-li ukotvení a dokování ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c1bb8-163">To anchor and dock WPF controls</span></span>  
  
1.  <span data-ttu-id="c1bb8-164">Vyberte `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-164">Select `elementHost1`.</span></span>  
  
2.  <span data-ttu-id="c1bb8-165">V **vlastnosti** nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost **nahoru, dolů, doleva a doprava**.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-165">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>  
  
3.  <span data-ttu-id="c1bb8-166">Změnit velikost <xref:System.Windows.Forms.TableLayoutPanel> řízení větší velikost.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-166">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>  
  
     <span data-ttu-id="c1bb8-167">`elementHost1` Změní velikost vyplníte buňku řízení.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-167">The `elementHost1` control resizes to fill the cell.</span></span>  
  
4.  <span data-ttu-id="c1bb8-168">Vyberte `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-168">Select `elementHost2`.</span></span>  
  
5.  <span data-ttu-id="c1bb8-169">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-169">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="c1bb8-170">`elementHost2` Změní velikost vyplníte buňku řízení.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-170">The `elementHost2` control resizes to fill the cell.</span></span>  
  
6.  <span data-ttu-id="c1bb8-171">Vyberte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-171">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="c1bb8-172">Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-172">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>  
  
8.  <span data-ttu-id="c1bb8-173">Vyberte `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-173">Select `elementHost3`.</span></span>  
  
9. <span data-ttu-id="c1bb8-174">Nastavte hodnotu jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-174">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="c1bb8-175">`elementHost3` Řízení změní velikost k vyplnění zbývající místo na formuláři.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-175">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>  
  
10. <span data-ttu-id="c1bb8-176">Změnit velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-176">Resize the form.</span></span>  
  
     <span data-ttu-id="c1bb8-177">Všechny tři <xref:System.Windows.Forms.Integration.ElementHost> správně Změna velikosti ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="c1bb8-177">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>  
  
     <span data-ttu-id="c1bb8-178">Další informace najdete v tématu [postupy: ukotvení a ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="c1bb8-178">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1bb8-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1bb8-179">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="c1bb8-180">Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c1bb8-180">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="c1bb8-181">Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu</span><span class="sxs-lookup"><span data-stu-id="c1bb8-181">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="c1bb8-182">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="c1bb8-182">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="c1bb8-183">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="c1bb8-183">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="c1bb8-184">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="c1bb8-184">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="c1bb8-185">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="c1bb8-185">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
