---
title: 'Návod: Hostování ovládacího prvku ActiveX v objektu WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: c8cbc2cb60e4afce4bcb35cf1fe645068a452b1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547209"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="345ad-102">Návod: Hostování ovládacího prvku ActiveX v objektu WPF</span><span class="sxs-lookup"><span data-stu-id="345ad-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="345ad-103">Chcete-li umožnit lepší interakci s prohlížeči, můžete použít [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] ovládacích prvků do vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikace.</span><span class="sxs-lookup"><span data-stu-id="345ad-103">To enable improved interaction with browsers, you can use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="345ad-104">Tento návod ukazuje, jak můžete hostovat [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] jako ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="345ad-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>  
  
 <span data-ttu-id="345ad-105">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="345ad-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="345ad-106">Vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="345ad-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="345ad-107">Vytvoření ovládacího prvku ActiveX.</span><span class="sxs-lookup"><span data-stu-id="345ad-107">Creating the ActiveX control.</span></span>  
  
-   <span data-ttu-id="345ad-108">Hostování ovládacího prvku ActiveX na stránce WPF.</span><span class="sxs-lookup"><span data-stu-id="345ad-108">Hosting the ActiveX control on a WPF Page.</span></span>  
  
 <span data-ttu-id="345ad-109">Po dokončení tohoto průvodce můžete bude pochopit, jak používat [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] ovládacích prvků do vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikace.</span><span class="sxs-lookup"><span data-stu-id="345ad-109">When you have completed this walkthrough, you will understand how to use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="345ad-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="345ad-110">Prerequisites</span></span>  
 <span data-ttu-id="345ad-111">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="345ad-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]<span data-ttu-id="345ad-112"> v počítači, kde je nainstalována sada Visual Studio nainstalována.</span><span class="sxs-lookup"><span data-stu-id="345ad-112"> installed on the computer where Visual Studio is installed.</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="345ad-113">.</span><span class="sxs-lookup"><span data-stu-id="345ad-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="345ad-114">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="345ad-114">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="345ad-115">Vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="345ad-115">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="345ad-116">Vytvořte projekt aplikace WPF s názvem `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="345ad-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>  
  
2.  <span data-ttu-id="345ad-117">Přidejte projektu knihovny ovládacích prvků Windows Forms k řešení a název projektu `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="345ad-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>  
  
3.  <span data-ttu-id="345ad-118">V projektu WmpAxLib přidáte odkaz na sestavení program Windows Media Player, která se nazývá wmp.dll.</span><span class="sxs-lookup"><span data-stu-id="345ad-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>  
  
4.  <span data-ttu-id="345ad-119">Otevřete **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="345ad-119">Open the **Toolbox**.</span></span>  
  
5.  <span data-ttu-id="345ad-120">Klikněte pravým tlačítkem myši **sada nástrojů**a potom klikněte na **zvolit položky**.</span><span class="sxs-lookup"><span data-stu-id="345ad-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>  
  
6.  <span data-ttu-id="345ad-121">Klikněte na tlačítko **COM – součásti** vyberte **program Windows Media Player** řízení a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="345ad-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>  
  
     <span data-ttu-id="345ad-122">Ovládací prvek Windows Media Player je přidán do **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="345ad-122">The Windows Media Player control is added to the **Toolbox**.</span></span>  
  
7.  <span data-ttu-id="345ad-123">V Průzkumníku řešení klikněte pravým tlačítkem myši **UserControl1** souboru a potom klikněte na **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="345ad-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>  
  
8.  <span data-ttu-id="345ad-124">Změňte název `WmpAxControl.vb` nebo `WmpAxControl.cs`, v závislosti na jazyce.</span><span class="sxs-lookup"><span data-stu-id="345ad-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>  
  
9. <span data-ttu-id="345ad-125">Pokud se zobrazí výzva k přejmenování všech odkazů, klikněte na tlačítko **Ano**.</span><span class="sxs-lookup"><span data-stu-id="345ad-125">If you are prompted to rename all references, click **Yes**.</span></span>  
  
## <a name="creating-the-activex-control"></a><span data-ttu-id="345ad-126">Vytvoření ovládacího prvku ActiveX</span><span class="sxs-lookup"><span data-stu-id="345ad-126">Creating the ActiveX Control</span></span>  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]<span data-ttu-id="345ad-127"> automaticky generuje <xref:System.Windows.Forms.AxHost> obálkovou třídu pro [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] řízení, když je ovládací prvek přidán na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="345ad-127"> automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] control when the control is added to a design surface.</span></span> <span data-ttu-id="345ad-128">Následující postup vytvoří spravované sestavení s názvem AxInterop.WMPLib.dll.</span><span class="sxs-lookup"><span data-stu-id="345ad-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>  
  
#### <a name="to-create-the-activex-control"></a><span data-ttu-id="345ad-129">Vytvoření ovládacího prvku ActiveX</span><span class="sxs-lookup"><span data-stu-id="345ad-129">To create the ActiveX control</span></span>  
  
1.  <span data-ttu-id="345ad-130">Otevřete WmpAxControl.vb nebo WmpAxControl.cs v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="345ad-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="345ad-131">Z **sada nástrojů**, přidání ovládacího prvku Windows Media Player na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="345ad-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>  
  
3.  <span data-ttu-id="345ad-132">V okně vlastnosti nastavit hodnotu ovládacího prvku Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="345ad-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
4.  <span data-ttu-id="345ad-133">Sestavení projektu knihovny WmpAxLib ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="345ad-133">Build the WmpAxLib control library project.</span></span>  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="345ad-134">Hostování ovládacího prvku ActiveX na stránce WPF</span><span class="sxs-lookup"><span data-stu-id="345ad-134">Hosting the ActiveX Control on a WPF Page</span></span>  
  
#### <a name="to-host-the-activex-control"></a><span data-ttu-id="345ad-135">K hostování ovládacího prvku ActiveX</span><span class="sxs-lookup"><span data-stu-id="345ad-135">To host the ActiveX control</span></span>  
  
1.  <span data-ttu-id="345ad-136">V projektu HostingAxInWpf přidat odkaz na vygenerovaného [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperabilita sestavení.</span><span class="sxs-lookup"><span data-stu-id="345ad-136">In the HostingAxInWpf project, add a reference to the generated [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperability assembly.</span></span>  
  
     <span data-ttu-id="345ad-137">Toto sestavení jmenuje AxInterop.WMPLib.dll a byla přidána do složky ladění projektu WmpAxLib při importu ovládacího prvku Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="345ad-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>  
  
2.  <span data-ttu-id="345ad-138">Přidáte odkaz na sestavení WindowsFormsIntegration, která se nazývá WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="345ad-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="345ad-139">Přidat odkaz na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sestavení, která se nazývá System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="345ad-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>  
  
4.  <span data-ttu-id="345ad-140">Otevřete MainWindow.xaml v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="345ad-140">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
5.  <span data-ttu-id="345ad-141">Název <xref:System.Windows.Controls.Grid> element `grid1`.</span><span class="sxs-lookup"><span data-stu-id="345ad-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  <span data-ttu-id="345ad-142">V návrhovém zobrazení nebo zobrazení jazyka XAML, vyberte <xref:System.Windows.Window> elementu.</span><span class="sxs-lookup"><span data-stu-id="345ad-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
7.  <span data-ttu-id="345ad-143">V okně vlastností klikněte **události** kartě.</span><span class="sxs-lookup"><span data-stu-id="345ad-143">In the Properties window, click the **Events** tab.</span></span>  
  
8.  <span data-ttu-id="345ad-144">Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="345ad-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
9. <span data-ttu-id="345ad-145">Vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="345ad-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     <span data-ttu-id="345ad-146">Tento kód vytvoří instanci <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení a přidá instanci `AxWindowsMediaPlayer` ovládací prvek, jeho dceřiný.</span><span class="sxs-lookup"><span data-stu-id="345ad-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="345ad-147">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="345ad-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="345ad-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="345ad-148">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="345ad-149">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="345ad-149">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="345ad-150">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="345ad-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="345ad-151">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="345ad-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
