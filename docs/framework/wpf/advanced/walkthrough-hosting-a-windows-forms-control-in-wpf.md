---
title: "Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38b50c90f653238d44401bac917645cd7f293681
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="c7d2b-102">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="c7d2b-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="c7d2b-103">poskytuje mnoho ovládacích prvků bohaté sadě funkcí.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="c7d2b-104">Ale v některých případech můžete použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky na vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="c7d2b-105">Například můžete mít významné investice v existující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, nebo může mít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který poskytuje jedinečné funkce.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="c7d2b-106">Tento návod ukazuje, jak hostovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> řízení na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-106">This walkthrough shows you how to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>  
  
 <span data-ttu-id="c7d2b-107">Kompletní kód tak seznam úloh v tomto návodu najdete v tématu [hostování ovládacího prvku Windows Forms v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=160057).</span><span class="sxs-lookup"><span data-stu-id="c7d2b-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=160057).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c7d2b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7d2b-108">Prerequisites</span></span>  
 <span data-ttu-id="c7d2b-109">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="c7d2b-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="c7d2b-110">.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="c7d2b-111">Hostování ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7d2b-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="c7d2b-112">K hostování MaskedTextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="c7d2b-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="c7d2b-113">Vytvořte projekt aplikace WPF s názvem `HostingWfInWpf`.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>  
  
2.  <span data-ttu-id="c7d2b-114">Přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="c7d2b-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="c7d2b-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="c7d2b-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="c7d2b-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="c7d2b-117">Otevřete MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7d2b-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="c7d2b-118">Název <xref:System.Windows.Controls.Grid> element `grid1`.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  <span data-ttu-id="c7d2b-119">V návrhovém zobrazení nebo zobrazení jazyka XAML, vyberte <xref:System.Windows.Window> elementu.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="c7d2b-120">V okně vlastností klikněte **události** kartě.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-120">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="c7d2b-121">Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="c7d2b-122">Vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. <span data-ttu-id="c7d2b-123">Na začátek souboru přidejte následující `Imports` nebo `using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. <span data-ttu-id="c7d2b-124">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7d2b-124">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d2b-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7d2b-125">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="c7d2b-126">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="c7d2b-126">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="c7d2b-127">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF pomocí kódu XAML</span><span class="sxs-lookup"><span data-stu-id="c7d2b-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [<span data-ttu-id="c7d2b-128">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="c7d2b-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="c7d2b-129">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7d2b-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="c7d2b-130">Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="c7d2b-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="c7d2b-131">Hostování ovládacího prvku Windows Forms v ukázce WPF</span><span class="sxs-lookup"><span data-stu-id="c7d2b-131">Hosting a Windows Forms Control in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160057)
