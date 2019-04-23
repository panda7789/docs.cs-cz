---
title: 'Návod: Hostování ovládacího prvku Windows Forms ve WPF pomocí XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 10554145de9725bb4cfc655ed88195dce28d739c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321611"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="f59dd-102">Návod: Hostování ovládacího prvku Windows Forms ve WPF pomocí XAML</span><span class="sxs-lookup"><span data-stu-id="f59dd-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="f59dd-103">nabízí mnoho ovládacích prvků s bohatou sadou funkcí.</span><span class="sxs-lookup"><span data-stu-id="f59dd-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="f59dd-104">Však můžete někdy chtít použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky ve vašich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="f59dd-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="f59dd-105">Například můžete mít značné investice v existujícím [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, nebo můžete mít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který poskytuje jedinečné funkce.</span><span class="sxs-lookup"><span data-stu-id="f59dd-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="f59dd-106">Tento návod ukazuje, jak hostovat prvku Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> ovládání na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránku pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f59dd-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="f59dd-107">Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [hostování ovládacího prvku Windows Forms v subsystému WPF pomocí XAML vzorek](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span><span class="sxs-lookup"><span data-stu-id="f59dd-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="f59dd-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f59dd-108">Prerequisites</span></span>  

<span data-ttu-id="f59dd-109">Visual Studio k dokončení tohoto návodu potřebujete.</span><span class="sxs-lookup"><span data-stu-id="f59dd-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="f59dd-110">Hostování ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f59dd-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="f59dd-111">K hostování ovládacím prvkem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="f59dd-111">To host the MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="f59dd-112">Vytvoření projektu aplikace WPF s názvem `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="f59dd-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2. <span data-ttu-id="f59dd-113">Přidáte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="f59dd-113">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="f59dd-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="f59dd-114">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="f59dd-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="f59dd-115">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="f59dd-116">Otevřete soubor MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f59dd-116">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4. <span data-ttu-id="f59dd-117">V <xref:System.Windows.Window> prvku, přidejte následující mapování oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f59dd-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="f59dd-118">`wf` Mapování oboru názvů vytvoří odkaz na sestavení, která obsahuje ovládací prvek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f59dd-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <span data-ttu-id="f59dd-119">V <xref:System.Windows.Controls.Grid> prvek přidejte následující XAML.</span><span class="sxs-lookup"><span data-stu-id="f59dd-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="f59dd-120"><xref:System.Windows.Forms.MaskedTextBox> Ovládací prvek je vytvořen jako podřízený objekt <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f59dd-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. <span data-ttu-id="f59dd-121">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f59dd-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f59dd-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f59dd-122">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="f59dd-123">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f59dd-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="f59dd-124">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="f59dd-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="f59dd-125">Návod: Hostování složeného ovládacího Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="f59dd-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="f59dd-126">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f59dd-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="f59dd-127">Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="f59dd-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="f59dd-128">Hostování ovládacího prvku Windows Forms v subsystému WPF pomocí ukázky XAML</span><span class="sxs-lookup"><span data-stu-id="f59dd-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
