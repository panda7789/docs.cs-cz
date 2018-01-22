---
title: "Návod: Vytvoření nového obsahu WPF ve Windows Forms během návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc357b8ad1ff450c699878dfffe1fbb6e2440f49
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="b5fb0-102">Návod: Vytvoření nového obsahu WPF ve Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="b5fb0-102">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="b5fb0-103">Toto téma ukazuje, jak vytvořit ovládací prvek Windows Presentation Foundation (WPF) pro použití v aplikacích Windows formulářů.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-103">This topic shows you how to create a Windows Presentation Foundation (WPF) control for use in your Windows Forms-based applications.</span></span>  
  
 <span data-ttu-id="b5fb0-104">V tomto návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="b5fb0-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="b5fb0-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-105">Create the project.</span></span>  
  
-   <span data-ttu-id="b5fb0-106">Vytvořte nový ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-106">Create a new WPF control.</span></span>  
  
-   <span data-ttu-id="b5fb0-107">Přidejte nové ovládací prvek WPF do formuláře systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-107">Add the new WPF control to a Windows Form.</span></span> <span data-ttu-id="b5fb0-108">Ovládací prvek WPF je hostován v <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-108">The WPF control is hosted in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5fb0-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b5fb0-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b5fb0-111">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="b5fb0-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b5fb0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5fb0-112">Prerequisites</span></span>  
 <span data-ttu-id="b5fb0-113">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="b5fb0-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="b5fb0-114">.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b5fb0-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="b5fb0-115">Creating the Project</span></span>  
 <span data-ttu-id="b5fb0-116">Prvním krokem je vytvoření projektu modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5fb0-117">Pokud hostování obsahu subsystému WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="b5fb0-118">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="b5fb0-118">To create the project</span></span>  
  
-   <span data-ttu-id="b5fb0-119">Vytvořte nový projekt aplikace Windows Forms v jazyce Visual Basic a Visual C# s názvem `HostingWpf`.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `HostingWpf`.</span></span>  
  
## <a name="creating-a-new-wpf-control"></a><span data-ttu-id="b5fb0-120">Vytvoření nové ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="b5fb0-120">Creating a New WPF Control</span></span>  
 <span data-ttu-id="b5fb0-121">Vytvoření nové ovládací prvek WPF a její přidání do projektu je stejně snadná jako přidávání dalších položek do projektu.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-121">Creating a new WPF control and adding it to your project is as easy as adding any other item to your project.</span></span> <span data-ttu-id="b5fb0-122">Návrhář formulářů Windows funguje s konkrétní typ ovládací prvek s názvem *složeného ovládacího prvku*, nebo *uživatelský ovládací prvek*.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-122">The Windows Forms Designer works with a particular kind of control named *composite control*, or *user control*.</span></span> <span data-ttu-id="b5fb0-123">Další informace o uživatelských ovládacích prvků WPF najdete v tématu <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-123">For more information about WPF user controls, see <xref:System.Windows.Controls.UserControl>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5fb0-124"><xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> Typ pro WPF se liší od typ ovládacího prvku uživatele poskytované Windows Forms, který je také název <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-124">The <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> type for WPF is distinct from the user control type provided by Windows Forms, which is also named <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span>  
  
#### <a name="to-create-a-new-wpf-control"></a><span data-ttu-id="b5fb0-125">Chcete-li vytvořit nový ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="b5fb0-125">To create a new WPF control</span></span>  
  
1.  <span data-ttu-id="b5fb0-126">V **Průzkumníku řešení**, přidejte nový **knihovny ovládací prvek WPF uživatelského** projektu k řešení.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-126">In **Solution Explorer**, add a new **WPF User Control Library** project to the solution.</span></span> <span data-ttu-id="b5fb0-127">Použít výchozí název pro knihovnu řízení `WpfControlLibrary1`.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-127">Use the default name for the control library, `WpfControlLibrary1`.</span></span> <span data-ttu-id="b5fb0-128">Výchozí název ovládacího prvku je `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-128">The default control name is `UserControl1.xaml`.</span></span>  
  
     <span data-ttu-id="b5fb0-129">Přidání nového ovládacího prvku má tyto důsledky.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-129">Adding the new control has the following effects.</span></span>  
  
    -   <span data-ttu-id="b5fb0-130">Soubor UserControl1.xaml je přidána.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-130">File UserControl1.xaml is added.</span></span>  
  
    -   <span data-ttu-id="b5fb0-131">Soubor UserControl1.xaml.cs nebo UserControl1.xaml.vb přidán.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-131">Either file UserControl1.xaml.cs or UserControl1.xaml.vb is added.</span></span> <span data-ttu-id="b5fb0-132">Tento soubor obsahuje kódu pro obslužné rutiny událostí a jiné implementace.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-132">This file contains the code-behind for event handlers and other implementation.</span></span>  
  
    -   <span data-ttu-id="b5fb0-133">Odkazy na sestavení WPF jsou přidány.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-133">References to WPF assemblies are added.</span></span>  
  
    -   <span data-ttu-id="b5fb0-134">UserControl1.xaml soubor se otevře v [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5fb0-134">File UserControl1.xaml opens in the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="b5fb0-135">V návrhovém zobrazení, ujistěte se, že `UserControl1` je vybrána.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-135">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="b5fb0-136">Další informace najdete v tématu [postup: vyberte a přesunout elementů na návrhovou plochu](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="b5fb0-136">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="b5fb0-137">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti, které chcete `200`.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-137">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="b5fb0-138">Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládacího prvku na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-138">From the **Toolbox**, drag a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control onto the design surface.</span></span>  
  
5.  <span data-ttu-id="b5fb0-139">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostované obsahu**.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-139">In the **Properties** window, set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5fb0-140">Obecně platí by měl hostitel sofistikovanější obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-140">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="b5fb0-141"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Řízení tady je použita pouze pro ilustraci.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-141">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
6.  <span data-ttu-id="b5fb0-142">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-142">Build the project.</span></span>  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="b5fb0-143">Přidání ovládacího prvku WPF na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="b5fb0-143">Adding a WPF Control to a Windows Form</span></span>  
 <span data-ttu-id="b5fb0-144">Nový ovládací prvek WPF je připravený k použití na formuláři.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-144">Your new WPF control is ready for use on the form.</span></span> <span data-ttu-id="b5fb0-145">Windows Forms používá <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek jako hostitele obsahu WPF</span><span class="sxs-lookup"><span data-stu-id="b5fb0-145">Windows Forms uses the <xref:System.Windows.Forms.Integration.ElementHost> control to host WPF content</span></span>  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a><span data-ttu-id="b5fb0-146">Přidání ovládacího prvku WPF do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="b5fb0-146">To add a WPF control to a Windows Form</span></span>  
  
1.  <span data-ttu-id="b5fb0-147">Otevřete `Form1` v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-147">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="b5fb0-148">V **sada nástrojů**, najít na kartě s názvem bez přípony **WPFUserControlLibrary WPF uživatelské ovládací prvky**.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-148">In the **Toolbox**, find the tab labeled **WPFUserControlLibrary WPF User Controls**.</span></span>  
  
3.  <span data-ttu-id="b5fb0-149">Přetáhněte instanci `UserControl1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-149">Drag an instance of `UserControl1` onto the form.</span></span>  
  
    -   <span data-ttu-id="b5fb0-150"><xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek je automaticky vytvořen ve formuláři pro hostování ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-150">An <xref:System.Windows.Forms.Integration.ElementHost> control is created automatically on the form to host the WPF control.</span></span>  
  
    -   <span data-ttu-id="b5fb0-151"><xref:System.Windows.Forms.Integration.ElementHost> Řízení jmenuje `elementHost1` a v **vlastnosti** okně uvidíte jeho <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na **UserControl1**.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-151">The <xref:System.Windows.Forms.Integration.ElementHost> control is named `elementHost1` and in the **Properties** window, you can see its <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl1**.</span></span>  
  
    -   <span data-ttu-id="b5fb0-152">Odkazy na sestavení WPF jsou přidány do projektu.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-152">References to WPF assemblies are added to the project.</span></span>  
  
    -   <span data-ttu-id="b5fb0-153">`elementHost1` Má ovládací prvek inteligentního panelu, které jsou uvedené dostupné možnosti hostování.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-153">The `elementHost1` control has a smart tag panel that shows the available hosting options.</span></span>  
  
4.  <span data-ttu-id="b5fb0-154">V **ElementHost úlohy** inteligentní panel, vyberte **ukotvení v nadřazený kontejner**.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-154">In the **ElementHost Tasks** smart tag panel, select **Dock in parent container**.</span></span>  
  
5.  <span data-ttu-id="b5fb0-155">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-155">Press F5 to build and run the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b5fb0-156">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b5fb0-156">Next Steps</span></span>  
 <span data-ttu-id="b5fb0-157">Windows Forms a WPF jsou různých technologií, ale jsou navrženy úzce spolupracovat.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-157">Windows Forms and WPF are different technologies, but they are designed to interoperate closely.</span></span> <span data-ttu-id="b5fb0-158">Pokud chcete zadat bohatší vzhled a chování v aplikacích, zkuste následující postup.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-158">To provide richer appearance and behavior in your applications, try the following.</span></span>  
  
-   <span data-ttu-id="b5fb0-159">Hostování ovládacího prvku Windows Forms na stránce WPF.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-159">Host a Windows Forms control in a WPF page.</span></span> <span data-ttu-id="b5fb0-160">Další informace najdete v tématu [návod: hostování ovládacího prvku Windows Forms v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="b5fb0-160">For more information, see [Walkthrough: Hosting a Windows Forms Control in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>  
  
-   <span data-ttu-id="b5fb0-161">Vizuální styly Windows Forms použijte k vašemu obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-161">Apply Windows Forms visual styles to your WPF content.</span></span> <span data-ttu-id="b5fb0-162">Další informace najdete v tématu [postupy: povolení vizuální styly v hybridní aplikace](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span><span class="sxs-lookup"><span data-stu-id="b5fb0-162">For more information, see [How to: Enable Visual Styles in a Hybrid Application](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).</span></span>  
  
-   <span data-ttu-id="b5fb0-163">Změna stylu obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="b5fb0-163">Change the style of your WPF content.</span></span> <span data-ttu-id="b5fb0-164">Další informace najdete v tématu [návod: určení stylu obsahu WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span><span class="sxs-lookup"><span data-stu-id="b5fb0-164">For more information, see [Walkthrough: Styling WPF Content](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5fb0-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5fb0-165">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="b5fb0-166">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="b5fb0-166">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="b5fb0-167">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="b5fb0-167">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="b5fb0-168">WPF Designer</span><span class="sxs-lookup"><span data-stu-id="b5fb0-168">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
