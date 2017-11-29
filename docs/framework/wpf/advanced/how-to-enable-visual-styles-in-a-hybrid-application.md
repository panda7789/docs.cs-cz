---
title: "Postupy: Povolení vizuálních stylů v hybridní aplikaci"
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
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e628835f0e5fb315f15b9e9946c48f7017092bae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="e5207-102">Postupy: Povolení vizuálních stylů v hybridní aplikaci</span><span class="sxs-lookup"><span data-stu-id="e5207-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="e5207-103">Toto téma ukazuje, jak povolit [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styly na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení hostované v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5207-103">This topic shows how to enable [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="e5207-104">Pokud aplikace zavolá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda, většina vaše [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky automaticky použije vizuální styly, když aplikace běží na [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5207-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles when your application is run on [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span></span> <span data-ttu-id="e5207-105">Další informace najdete v tématu [vykreslování ovládacích prvků s vizuálními styly](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="e5207-105">For more information, see [Rendering Controls with Visual Styles](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="e5207-106">Seznam dokončení kódu úkoly popsané v tomto tématu najdete v tématu [povolení vizuální styly v ukázku hybridní aplikace](http://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="e5207-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](http://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="e5207-107">Povolení Windows Forms vizuální styly</span><span class="sxs-lookup"><span data-stu-id="e5207-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="e5207-108">Chcete-li povolit vizuální styly Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5207-108">To enable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="e5207-109">Vytvoření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt aplikace s názvem `HostingWfWithVisualStyles`.</span><span class="sxs-lookup"><span data-stu-id="e5207-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2.  <span data-ttu-id="e5207-110">V Průzkumníku řešení přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="e5207-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="e5207-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="e5207-111">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="e5207-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="e5207-112">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="e5207-113">V sadě nástrojů, dvakrát klikněte <xref:System.Windows.Controls.Grid> ikonu umístit <xref:System.Windows.Controls.Grid> elementu na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="e5207-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4.  <span data-ttu-id="e5207-114">V okně vlastností nastavte hodnoty <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti, které chcete **automaticky**.</span><span class="sxs-lookup"><span data-stu-id="e5207-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5.  <span data-ttu-id="e5207-115">V návrhovém zobrazení nebo zobrazení jazyka XAML, vyberte <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="e5207-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6.  <span data-ttu-id="e5207-116">V okně vlastností klikněte **události** kartě.</span><span class="sxs-lookup"><span data-stu-id="e5207-116">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="e5207-117">Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="e5207-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8.  <span data-ttu-id="e5207-118">V MainWindow.xaml.vb nebo MainWindow.xaml.cs, vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="e5207-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="e5207-119">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5207-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="e5207-120">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Vykreslení ovládacího prvku s vizuálními styly.</span><span class="sxs-lookup"><span data-stu-id="e5207-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="e5207-121">Zakázání Windows Forms vizuální styly</span><span class="sxs-lookup"><span data-stu-id="e5207-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="e5207-122">Zakázání stylů, stačí odstranit volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e5207-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="e5207-123">Zakázání Windows Forms stylů</span><span class="sxs-lookup"><span data-stu-id="e5207-123">To disable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="e5207-124">Otevřete MainWindow.xaml.vb nebo MainWindow.xaml.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="e5207-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="e5207-125">Komentář volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e5207-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3.  <span data-ttu-id="e5207-126">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5207-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="e5207-127">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Vykreslení ovládacího prvku s výchozí styl systému.</span><span class="sxs-lookup"><span data-stu-id="e5207-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5207-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5207-128">See Also</span></span>  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="e5207-129">Vykreslení ovládacích prvků s vizuálními styly</span><span class="sxs-lookup"><span data-stu-id="e5207-129">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [<span data-ttu-id="e5207-130">Postupy: Hostování ovládacího prvku Windows Forms v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="e5207-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
