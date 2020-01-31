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
ms.openlocfilehash: dd52313e9100f9c6a1141b53ccc5a23a4b54410a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789923"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="fc595-102">Postupy: Povolení vizuálních stylů v hybridní aplikaci</span><span class="sxs-lookup"><span data-stu-id="fc595-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="fc595-103">Toto téma ukazuje, jak povolit vizuální styly v ovládacím prvku model Windows Forms hostovaném v aplikaci založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc595-103">This topic shows how to enable visual styles on a Windows Forms control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="fc595-104">Pokud vaše aplikace volá metodu <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>, většina ovládacích prvků model Windows Forms bude automaticky používat vizuální styly.</span><span class="sxs-lookup"><span data-stu-id="fc595-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your Windows Forms controls will automatically use visual styles.</span></span> <span data-ttu-id="fc595-105">Další informace naleznete v tématu [vykreslování ovládacích prvků pomocí vizuálních stylů](../../winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="fc595-105">For more information, see [Rendering Controls with Visual Styles](../../winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="fc595-106">Úplný výpis kódu úloh, které jsou znázorněny v tomto tématu, naleznete v tématu [Povolení vizuálních stylů v ukázce hybridní aplikace](https://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="fc595-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="fc595-107">Povolení model Windows Formsch vizuálních stylů</span><span class="sxs-lookup"><span data-stu-id="fc595-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="fc595-108">Povolení model Windows Formsch vizuálních stylů</span><span class="sxs-lookup"><span data-stu-id="fc595-108">To enable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="fc595-109">Vytvořte projekt aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s názvem `HostingWfWithVisualStyles`.</span><span class="sxs-lookup"><span data-stu-id="fc595-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2. <span data-ttu-id="fc595-110">V Průzkumník řešení přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="fc595-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="fc595-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="fc595-111">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="fc595-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="fc595-112">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="fc595-113">Na panelu nástrojů poklikejte na ikonu <xref:System.Windows.Controls.Grid> a umístěte <xref:System.Windows.Controls.Grid> prvek na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="fc595-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4. <span data-ttu-id="fc595-114">V okno Vlastnosti nastavte hodnoty vlastností <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> na **auto**.</span><span class="sxs-lookup"><span data-stu-id="fc595-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5. <span data-ttu-id="fc595-115">V zobrazení zobrazení Návrh nebo XAML vyberte <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="fc595-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6. <span data-ttu-id="fc595-116">V okno Vlastnosti klikněte na kartu **události** .</span><span class="sxs-lookup"><span data-stu-id="fc595-116">In the Properties window, click the **Events** tab.</span></span>  
  
7. <span data-ttu-id="fc595-117">Dvakrát klikněte na událost <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="fc595-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8. <span data-ttu-id="fc595-118">V souboru MainWindow. XAML. vb nebo MainWindow.xaml.cs vložte následující kód pro zpracování události <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="fc595-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="fc595-119">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fc595-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="fc595-120">Ovládací prvek model Windows Forms je vykreslen pomocí vizuálních stylů.</span><span class="sxs-lookup"><span data-stu-id="fc595-120">The Windows Forms control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="fc595-121">Zákaz model Windows Formsch vizuálních stylů</span><span class="sxs-lookup"><span data-stu-id="fc595-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="fc595-122">Chcete-li zakázat vizuální styly, jednoduše odeberte volání metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc595-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="fc595-123">Zakázání vizuálních stylů model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc595-123">To disable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="fc595-124">V editoru kódu otevřete MainWindow. XAML. vb nebo MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="fc595-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2. <span data-ttu-id="fc595-125">Odkomentujte volání metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc595-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3. <span data-ttu-id="fc595-126">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fc595-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="fc595-127">Ovládací prvek model Windows Forms je vykreslen s výchozím stylem systému.</span><span class="sxs-lookup"><span data-stu-id="fc595-127">The Windows Forms control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc595-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc595-128">See also</span></span>

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="fc595-129">Vykreslování ovládacích prvků s vizuálními styly</span><span class="sxs-lookup"><span data-stu-id="fc595-129">Rendering Controls with Visual Styles</span></span>](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [<span data-ttu-id="fc595-130">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="fc595-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
