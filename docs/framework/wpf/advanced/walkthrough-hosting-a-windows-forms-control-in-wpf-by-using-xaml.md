---
title: 'Návod: Hostování ovládacího prvku Windows Forms v objektu WPF použitím kódu XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 2f13689a15e91ee0f80c0d7b6bc71c5f973b8333
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43487127"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="22802-102">Návod: Hostování ovládacího prvku Windows Forms v objektu WPF použitím kódu XAML</span><span class="sxs-lookup"><span data-stu-id="22802-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="22802-103"> nabízí mnoho ovládacích prvků s bohatou sadou funkcí.</span><span class="sxs-lookup"><span data-stu-id="22802-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="22802-104">Však můžete někdy chtít použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky ve vašich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="22802-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="22802-105">Například můžete mít značné investice v existujícím [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, nebo můžete mít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který poskytuje jedinečné funkce.</span><span class="sxs-lookup"><span data-stu-id="22802-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="22802-106">Tento návod ukazuje, jak hostovat prvku Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> ovládání na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránku pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22802-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="22802-107">Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [hostování ovládacího prvku Windows Forms v subsystému WPF pomocí XAML vzorek](https://go.microsoft.com/fwlink/?LinkID=160000).</span><span class="sxs-lookup"><span data-stu-id="22802-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="22802-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22802-108">Prerequisites</span></span>  
 <span data-ttu-id="22802-109">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="22802-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="22802-110">.</span><span class="sxs-lookup"><span data-stu-id="22802-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="22802-111">Hostování ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22802-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="22802-112">K hostování ovládacím prvkem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="22802-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="22802-113">Vytvoření projektu aplikace WPF s názvem `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="22802-113">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="22802-114">Přidáte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="22802-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="22802-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="22802-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="22802-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="22802-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="22802-117">Otevřete soubor MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22802-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="22802-118">V <xref:System.Windows.Window> prvku, přidejte následující mapování oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="22802-118">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="22802-119">`wf` Mapování oboru názvů vytvoří odkaz na sestavení, která obsahuje ovládací prvek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="22802-119">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="22802-120">V <xref:System.Windows.Controls.Grid> prvek přidejte následující XAML.</span><span class="sxs-lookup"><span data-stu-id="22802-120">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="22802-121"><xref:System.Windows.Forms.MaskedTextBox> Ovládací prvek je vytvořen jako podřízený objekt <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="22802-121">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="22802-122">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="22802-122">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22802-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="22802-123">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="22802-124">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="22802-124">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [<span data-ttu-id="22802-125">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="22802-125">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="22802-126">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="22802-126">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="22802-127">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22802-127">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="22802-128">Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="22802-128">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="22802-129">Hostování ovládacího prvku Windows Forms v subsystému WPF pomocí ukázky XAML</span><span class="sxs-lookup"><span data-stu-id="22802-129">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
