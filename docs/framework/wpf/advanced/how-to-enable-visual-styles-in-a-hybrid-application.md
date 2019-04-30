---
title: 'Postupy: Povolení vizuálních stylů v hybridní aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 7aa5208a4f378408a01a08a2f4c9dbf2edfa5243
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776139"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="77d78-102">Postupy: Povolení vizuálních stylů v hybridní aplikaci</span><span class="sxs-lookup"><span data-stu-id="77d78-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="77d78-103">Toto téma ukazuje, jak povolit [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] styly vizuál na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] konání ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na.</span><span class="sxs-lookup"><span data-stu-id="77d78-103">This topic shows how to enable [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="77d78-104">Pokud vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda, většina vašich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky budou automaticky používat vizuální styly, když vaše aplikace běží na [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77d78-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles when your application is run on [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span></span> <span data-ttu-id="77d78-105">Další informace najdete v tématu [vykreslování ovládacích prvků s vizuálními styly](../../winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="77d78-105">For more information, see [Rendering Controls with Visual Styles](../../winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="77d78-106">Výpis úplného kódu úkoly uvedené v tomto tématu, naleznete v tématu [povolení vizuálních stylů v hybridní aplikace ukázku](https://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="77d78-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="77d78-107">Povolení Windows Forms vizuální styly</span><span class="sxs-lookup"><span data-stu-id="77d78-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="77d78-108">K povolení vizuálních stylů Windows Forms</span><span class="sxs-lookup"><span data-stu-id="77d78-108">To enable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="77d78-109">Vytvoření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt aplikace s názvem `HostingWfWithVisualStyles`.</span><span class="sxs-lookup"><span data-stu-id="77d78-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2. <span data-ttu-id="77d78-110">V Průzkumníku řešení přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="77d78-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="77d78-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="77d78-111">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="77d78-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="77d78-112">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="77d78-113">V sadě nástrojů klikněte dvakrát na <xref:System.Windows.Controls.Grid> ikonu umístit <xref:System.Windows.Controls.Grid> prvek na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="77d78-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4. <span data-ttu-id="77d78-114">V okně Vlastnosti nastavte hodnoty <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastností **automaticky**.</span><span class="sxs-lookup"><span data-stu-id="77d78-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5. <span data-ttu-id="77d78-115">V zobrazení návrhu nebo v XAML zobrazení, vyberte <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="77d78-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6. <span data-ttu-id="77d78-116">V okně Vlastnosti klikněte na tlačítko **události** kartu.</span><span class="sxs-lookup"><span data-stu-id="77d78-116">In the Properties window, click the **Events** tab.</span></span>  
  
7. <span data-ttu-id="77d78-117">Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="77d78-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8. <span data-ttu-id="77d78-118">V souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs, vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.</span><span class="sxs-lookup"><span data-stu-id="77d78-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="77d78-119">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="77d78-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="77d78-120">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Vymalování s vizuálními styly ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77d78-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="77d78-121">Zakázání Windows Forms vizuální styly</span><span class="sxs-lookup"><span data-stu-id="77d78-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="77d78-122">Zakázat vizuálních stylů, jednoduše odeberte volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="77d78-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="77d78-123">Chcete-li zakázat vizuálních stylů Windows Forms</span><span class="sxs-lookup"><span data-stu-id="77d78-123">To disable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="77d78-124">Otevřete soubor MainWindow.xaml.vb nebo MainWindow.xaml.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="77d78-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2. <span data-ttu-id="77d78-125">Odkomentujte volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="77d78-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3. <span data-ttu-id="77d78-126">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="77d78-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="77d78-127">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Vymalování ovládací prvek se stylem systému výchozí.</span><span class="sxs-lookup"><span data-stu-id="77d78-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d78-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77d78-128">See also</span></span>

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="77d78-129">Vykreslování ovládacích prvků s vizuálními styly</span><span class="sxs-lookup"><span data-stu-id="77d78-129">Rendering Controls with Visual Styles</span></span>](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [<span data-ttu-id="77d78-130">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="77d78-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
