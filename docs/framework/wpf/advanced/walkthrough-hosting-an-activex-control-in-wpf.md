---
title: Hostování ovládacího prvku ActiveX v subsystému WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: f2d9345eaaba7b85a217e6b230ae202f27ad3af8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742622"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="02fbb-102">Návod: Hostování ovládacího prvku ActiveX v objektu WPF</span><span class="sxs-lookup"><span data-stu-id="02fbb-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="02fbb-103">Chcete-li povolit vylepšenou interakci s prohlížeči, můžete v aplikaci založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]použít ovládací prvky Microsoft ActiveX.</span><span class="sxs-lookup"><span data-stu-id="02fbb-103">To enable improved interaction with browsers, you can use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="02fbb-104">Tento návod ukazuje, jak můžete hostovat Microsoft Windows Media Player jako ovládací prvek na stránce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02fbb-104">This walkthrough demonstrates how you can host the Microsoft Windows Media Player as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="02fbb-105">Úlohy, které jsou znázorněné v tomto návodu, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="02fbb-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="02fbb-106">Vytváří se projekt.</span><span class="sxs-lookup"><span data-stu-id="02fbb-106">Creating the project.</span></span>

- <span data-ttu-id="02fbb-107">Vytvoření ovládacího prvku ActiveX.</span><span class="sxs-lookup"><span data-stu-id="02fbb-107">Creating the ActiveX control.</span></span>

- <span data-ttu-id="02fbb-108">Hostování ovládacího prvku ActiveX na stránce WPF.</span><span class="sxs-lookup"><span data-stu-id="02fbb-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="02fbb-109">Po dokončení tohoto návodu budete pochopit, jak používat ovládací prvky Microsoft ActiveX ve vaší aplikaci založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02fbb-109">When you have completed this walkthrough, you will understand how to use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="02fbb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02fbb-110">Prerequisites</span></span>
 <span data-ttu-id="02fbb-111">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="02fbb-111">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="02fbb-112">V počítači, kde je nainstalována aplikace Visual Studio, je nainstalována aplikace Microsoft Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="02fbb-112">Microsoft Windows Media Player installed on the computer where Visual Studio is installed.</span></span>

- <span data-ttu-id="02fbb-113">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="02fbb-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="02fbb-114">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="02fbb-114">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="02fbb-115">Vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="02fbb-115">To create and set up the project</span></span>

1. <span data-ttu-id="02fbb-116">Vytvořte projekt aplikace WPF s názvem `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="02fbb-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2. <span data-ttu-id="02fbb-117">Přidejte do řešení projekt knihovny ovládacích prvků model Windows Forms a pojmenujte projekt `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="02fbb-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3. <span data-ttu-id="02fbb-118">V projektu WmpAxLib přidejte odkaz na sestavení Windows Media Player, které je pojmenované WMP. dll.</span><span class="sxs-lookup"><span data-stu-id="02fbb-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4. <span data-ttu-id="02fbb-119">Otevřete **sadu nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="02fbb-119">Open the **Toolbox**.</span></span>

5. <span data-ttu-id="02fbb-120">Klikněte pravým tlačítkem myši na **panel nástrojů**a potom klikněte na příkaz **zvolit položky**.</span><span class="sxs-lookup"><span data-stu-id="02fbb-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6. <span data-ttu-id="02fbb-121">Klikněte na kartu **komponenty modelu COM** , vyberte ovládací prvek **Windows Media Player** a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="02fbb-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="02fbb-122">Do **sady nástrojů**se přidá ovládací prvek Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="02fbb-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7. <span data-ttu-id="02fbb-123">V Průzkumník řešení klikněte pravým tlačítkem na soubor **UserControl1** a pak klikněte na **Přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="02fbb-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8. <span data-ttu-id="02fbb-124">Změňte název na `WmpAxControl.vb` nebo `WmpAxControl.cs`v závislosti na jazyku.</span><span class="sxs-lookup"><span data-stu-id="02fbb-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="02fbb-125">Pokud se zobrazí výzva k přejmenování všech odkazů, klikněte na **Ano**.</span><span class="sxs-lookup"><span data-stu-id="02fbb-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="02fbb-126">Vytvoření ovládacího prvku ActiveX</span><span class="sxs-lookup"><span data-stu-id="02fbb-126">Creating the ActiveX Control</span></span>
<span data-ttu-id="02fbb-127">Když je ovládací prvek přidán na návrhovou plochu, Visual Studio automaticky vygeneruje <xref:System.Windows.Forms.AxHost> obálkovou třídu pro ovládací prvek Microsoft ActiveX.</span><span class="sxs-lookup"><span data-stu-id="02fbb-127">Visual Studio automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a Microsoft ActiveX control when the control is added to a design surface.</span></span> <span data-ttu-id="02fbb-128">Následující postup vytvoří spravované sestavení s názvem AxInterop. WMPLib. dll.</span><span class="sxs-lookup"><span data-stu-id="02fbb-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

### <a name="to-create-the-activex-control"></a><span data-ttu-id="02fbb-129">Vytvoření ovládacího prvku ActiveX</span><span class="sxs-lookup"><span data-stu-id="02fbb-129">To create the ActiveX control</span></span>

1. <span data-ttu-id="02fbb-130">Otevřete WmpAxControl. vb nebo WmpAxControl.cs v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="02fbb-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="02fbb-131">Z **panelu nástrojů**přidejte ovládací prvek Windows Media Player na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="02fbb-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3. <span data-ttu-id="02fbb-132">V okno Vlastnosti nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> ovládacího prvku Windows Media Player na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="02fbb-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4. <span data-ttu-id="02fbb-133">Sestavte projekt knihovny ovládacích prvků WmpAxLib.</span><span class="sxs-lookup"><span data-stu-id="02fbb-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="02fbb-134">Hostování ovládacího prvku ActiveX na stránce WPF</span><span class="sxs-lookup"><span data-stu-id="02fbb-134">Hosting the ActiveX Control on a WPF Page</span></span>

### <a name="to-host-the-activex-control"></a><span data-ttu-id="02fbb-135">Hostování ovládacího prvku ActiveX</span><span class="sxs-lookup"><span data-stu-id="02fbb-135">To host the ActiveX control</span></span>

1. <span data-ttu-id="02fbb-136">V projektu HostingAxInWpf přidejte odkaz na vygenerované sestavení interoperability ActiveX.</span><span class="sxs-lookup"><span data-stu-id="02fbb-136">In the HostingAxInWpf project, add a reference to the generated ActiveX interoperability assembly.</span></span>

     <span data-ttu-id="02fbb-137">Toto sestavení má název AxInterop. WMPLib. dll a bylo přidáno do složky ladění projektu WmpAxLib při importu ovládacího prvku Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="02fbb-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2. <span data-ttu-id="02fbb-138">Přidejte odkaz na sestavení WindowsFormsIntegration, které má název WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="02fbb-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="02fbb-139">Přidejte odkaz na sestavení [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], které má název System. Windows. Forms. dll.</span><span class="sxs-lookup"><span data-stu-id="02fbb-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4. <span data-ttu-id="02fbb-140">Otevřete MainWindow. XAML v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="02fbb-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5. <span data-ttu-id="02fbb-141">Pojmenujte <xref:System.Windows.Controls.Grid> element `grid1`.</span><span class="sxs-lookup"><span data-stu-id="02fbb-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. <span data-ttu-id="02fbb-142">V zobrazení zobrazení Návrh nebo XAML vyberte prvek <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="02fbb-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7. <span data-ttu-id="02fbb-143">V okno Vlastnosti klikněte na kartu **události** .</span><span class="sxs-lookup"><span data-stu-id="02fbb-143">In the Properties window, click the **Events** tab.</span></span>

8. <span data-ttu-id="02fbb-144">Dvakrát klikněte na událost <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="02fbb-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="02fbb-145">Vložte následující kód pro zpracování události <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="02fbb-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="02fbb-146">Tento kód vytvoří instanci ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> a přidá instanci ovládacího prvku `AxWindowsMediaPlayer` jako jeho podřízenou položku.</span><span class="sxs-lookup"><span data-stu-id="02fbb-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="02fbb-147">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="02fbb-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02fbb-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02fbb-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="02fbb-149">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="02fbb-149">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="02fbb-150">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="02fbb-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="02fbb-151">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02fbb-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
