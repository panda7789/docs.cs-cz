---
title: "Návod: Hostování ovládacího prvku Windows Forms v objektu WPF použitím kódu XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5fe01b4ef9aebe697138e925935b73bd4770e86a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="b0528-102">Návod: Hostování ovládacího prvku Windows Forms v objektu WPF použitím kódu XAML</span><span class="sxs-lookup"><span data-stu-id="b0528-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="b0528-103">poskytuje mnoho ovládacích prvků bohaté sadě funkcí.</span><span class="sxs-lookup"><span data-stu-id="b0528-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="b0528-104">Ale v některých případech můžete použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky na vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="b0528-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="b0528-105">Například můžete mít významné investice v existující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, nebo může mít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který poskytuje jedinečné funkce.</span><span class="sxs-lookup"><span data-stu-id="b0528-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="b0528-106">Tento návod ukazuje, jak k hostování Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> řízení na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránku pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0528-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="b0528-107">Kompletní kód tak seznam úloh v tomto návodu najdete v tématu [hostování ovládacího prvku Windows Forms v grafickém subsystému WPF podle pomocí ukázkových XAML](http://go.microsoft.com/fwlink/?LinkID=160000).</span><span class="sxs-lookup"><span data-stu-id="b0528-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](http://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b0528-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0528-108">Prerequisites</span></span>  
 <span data-ttu-id="b0528-109">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="b0528-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="b0528-110">.</span><span class="sxs-lookup"><span data-stu-id="b0528-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="b0528-111">Hostování ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0528-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="b0528-112">K hostování MaskedTextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b0528-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="b0528-113">Vytvořte projekt aplikace WPF s názvem `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="b0528-113">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="b0528-114">Přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="b0528-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="b0528-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="b0528-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="b0528-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="b0528-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="b0528-117">Otevřete MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0528-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="b0528-118">V <xref:System.Windows.Window> elementu, přidejte následující mapování oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b0528-118">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="b0528-119">`wf` Mapování oboru názvů vytváří odkaz na sestavení, které obsahuje [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b0528-119">The `wf` namespace mapping establishes a reference to the assembly that contains the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="b0528-120">V <xref:System.Windows.Controls.Grid> element přidejte následující XAML.</span><span class="sxs-lookup"><span data-stu-id="b0528-120">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="b0528-121"><xref:System.Windows.Forms.MaskedTextBox> Ovládací prvek je vytvořen jako podřízený <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b0528-121">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="b0528-122">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0528-122">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0528-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0528-123">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="b0528-124">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="b0528-124">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="b0528-125">Postupy: Hostování ovládacího prvku Windows Forms v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="b0528-125">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="b0528-126">Postupy: Hostování ovládacího prvku Windows Forms složené v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="b0528-126">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="b0528-127">Postupy: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0528-127">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="b0528-128">Windows Forms a ovládacích prvků ekvivalentní WPF</span><span class="sxs-lookup"><span data-stu-id="b0528-128">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="b0528-129">Hostování ovládacího prvku Windows Forms v grafickém subsystému WPF pomocí ukázkových XAML</span><span class="sxs-lookup"><span data-stu-id="b0528-129">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160000)
