---
title: 'Návod: Hostování ovládacího prvku ActiveX ve WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: a84363221ee216aade041adb65cce5f092ad3ae5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130128"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="60fbd-102">Návod: Hostování ovládacího prvku ActiveX ve WPF</span><span class="sxs-lookup"><span data-stu-id="60fbd-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="60fbd-103">Povolit Vylepšený interakce s prohlížeči, můžete použít [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] ovládacích prvků v vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na.</span><span class="sxs-lookup"><span data-stu-id="60fbd-103">To enable improved interaction with browsers, you can use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="60fbd-104">Tento návod ukazuje, jak můžete hostovat [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] jako ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="60fbd-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="60fbd-105">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="60fbd-105">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="60fbd-106">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="60fbd-106">Creating the project.</span></span>

-   <span data-ttu-id="60fbd-107">Vytvoření ovládacího prvku ActiveX.</span><span class="sxs-lookup"><span data-stu-id="60fbd-107">Creating the ActiveX control.</span></span>

-   <span data-ttu-id="60fbd-108">Hostování ovládacího prvku ActiveX na stránce WPF.</span><span class="sxs-lookup"><span data-stu-id="60fbd-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="60fbd-109">Po dokončení tohoto návodu budete rozumět použití [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] ovládacích prvků v vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na.</span><span class="sxs-lookup"><span data-stu-id="60fbd-109">When you have completed this walkthrough, you will understand how to use [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="60fbd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60fbd-110">Prerequisites</span></span>
 <span data-ttu-id="60fbd-111">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="60fbd-111">You need the following components to complete this walkthrough:</span></span>

-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] <span data-ttu-id="60fbd-112">nainstalované v počítači nainstalovanou aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="60fbd-112">installed on the computer where Visual Studio is installed.</span></span>

-   <span data-ttu-id="60fbd-113">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="60fbd-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="60fbd-114">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="60fbd-114">Creating the Project</span></span>

#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="60fbd-115">K vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="60fbd-115">To create and set up the project</span></span>

1.  <span data-ttu-id="60fbd-116">Vytvoření projektu aplikace WPF s názvem `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="60fbd-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2.  <span data-ttu-id="60fbd-117">Přidat do řešení projekt Knihovna ovládacích prvků Windows Forms a pojmenujte projekt `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="60fbd-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3.  <span data-ttu-id="60fbd-118">V projektu WmpAxLib přidejte odkaz na sestavení programu Windows Media Player, který se nazývá wmp.dll.</span><span class="sxs-lookup"><span data-stu-id="60fbd-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4.  <span data-ttu-id="60fbd-119">Otevřít **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="60fbd-119">Open the **Toolbox**.</span></span>

5.  <span data-ttu-id="60fbd-120">Klikněte pravým tlačítkem **nástrojů**a potom klikněte na tlačítko **zvolit položky**.</span><span class="sxs-lookup"><span data-stu-id="60fbd-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6.  <span data-ttu-id="60fbd-121">Klikněte na tlačítko **komponenty modelu COM** kartu, vyberte **Windows Media Player** ovládací prvek a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="60fbd-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="60fbd-122">Ovládací prvek programu Windows Media Player je přidán do **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="60fbd-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7.  <span data-ttu-id="60fbd-123">V Průzkumníku řešení klikněte pravým tlačítkem myši **UserControl1** souboru a pak klikněte na tlačítko **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="60fbd-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8.  <span data-ttu-id="60fbd-124">Změňte název na `WmpAxControl.vb` nebo `WmpAxControl.cs`, v závislosti na jazyku.</span><span class="sxs-lookup"><span data-stu-id="60fbd-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="60fbd-125">Pokud se zobrazí výzva k přejmenování všech odkazů, klikněte na tlačítko **Ano**.</span><span class="sxs-lookup"><span data-stu-id="60fbd-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="60fbd-126">Vytvoření ovládacího prvku ActiveX</span><span class="sxs-lookup"><span data-stu-id="60fbd-126">Creating the ActiveX Control</span></span>
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] <span data-ttu-id="60fbd-127">automaticky generuje <xref:System.Windows.Forms.AxHost> obálkovou třídu pro [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] řídit, kdy je ovládací prvek přidán na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="60fbd-127">automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] control when the control is added to a design surface.</span></span> <span data-ttu-id="60fbd-128">Následujícím postupem vytvoříte spravované sestavení s názvem AxInterop.WMPLib.dll.</span><span class="sxs-lookup"><span data-stu-id="60fbd-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

#### <a name="to-create-the-activex-control"></a><span data-ttu-id="60fbd-129">Vytvoření ovládacího prvku ActiveX</span><span class="sxs-lookup"><span data-stu-id="60fbd-129">To create the ActiveX control</span></span>

1.  <span data-ttu-id="60fbd-130">Otevřete WmpAxControl.vb nebo WmpAxControl.cs v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="60fbd-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2.  <span data-ttu-id="60fbd-131">Z **nástrojů**, přidejte ovládací prvek programu Windows Media Player na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="60fbd-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3.  <span data-ttu-id="60fbd-132">V okně Vlastnosti nastavte hodnotu ovládacího prvku programu Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="60fbd-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4.  <span data-ttu-id="60fbd-133">Vytvoření projektu knihovny ovládacích prvků WmpAxLib.</span><span class="sxs-lookup"><span data-stu-id="60fbd-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="60fbd-134">Hostování ovládacího prvku ActiveX na stránce WPF</span><span class="sxs-lookup"><span data-stu-id="60fbd-134">Hosting the ActiveX Control on a WPF Page</span></span>

#### <a name="to-host-the-activex-control"></a><span data-ttu-id="60fbd-135">K hostování ovládacího prvku ActiveX</span><span class="sxs-lookup"><span data-stu-id="60fbd-135">To host the ActiveX control</span></span>

1.  <span data-ttu-id="60fbd-136">HostingAxInWpf projektu přidejte odkaz na generované [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] sestavení vzájemná funkční spolupráce.</span><span class="sxs-lookup"><span data-stu-id="60fbd-136">In the HostingAxInWpf project, add a reference to the generated [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperability assembly.</span></span>

     <span data-ttu-id="60fbd-137">Toto sestavení je s názvem AxInterop.WMPLib.dll a byl přidán do složky ladění projektu WmpAxLib při importu ovládací prvek programu Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="60fbd-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2.  <span data-ttu-id="60fbd-138">Přidáte odkaz na sestavení WindowsFormsIntegration, který se nazývá WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="60fbd-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3.  <span data-ttu-id="60fbd-139">Přidejte odkaz na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sestavení, který se nazývá System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="60fbd-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4.  <span data-ttu-id="60fbd-140">Otevřete soubor MainWindow.xaml v návrháři pro WPF.</span><span class="sxs-lookup"><span data-stu-id="60fbd-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5.  <span data-ttu-id="60fbd-141">Název <xref:System.Windows.Controls.Grid> element `grid1`.</span><span class="sxs-lookup"><span data-stu-id="60fbd-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6.  <span data-ttu-id="60fbd-142">V zobrazení návrhu nebo v XAML zobrazení, vyberte <xref:System.Windows.Window> elementu.</span><span class="sxs-lookup"><span data-stu-id="60fbd-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7.  <span data-ttu-id="60fbd-143">V okně Vlastnosti klikněte na tlačítko **události** kartu.</span><span class="sxs-lookup"><span data-stu-id="60fbd-143">In the Properties window, click the **Events** tab.</span></span>

8.  <span data-ttu-id="60fbd-144">Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="60fbd-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="60fbd-145">Vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="60fbd-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="60fbd-146">Tento kód vytvoří instanci <xref:System.Windows.Forms.Integration.WindowsFormsHost> řídit a přidá instanci `AxWindowsMediaPlayer` ovládací prvek jako jeho podřízených.</span><span class="sxs-lookup"><span data-stu-id="60fbd-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="60fbd-147">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="60fbd-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60fbd-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60fbd-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="60fbd-149">Návrh XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="60fbd-149">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="60fbd-150">Návod: Hostování složeného ovládacího prvku Windows Forms ve WPF</span><span class="sxs-lookup"><span data-stu-id="60fbd-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="60fbd-151">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="60fbd-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
