---
title: "Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF"
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
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67bfa913627d33238aea92acdd49b6d2ecfef2a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="46df1-102">Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="46df1-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="46df1-103">Tento postup vám ukáže, jak používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce rozložení uspořádat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků v hybridní aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="46df1-104">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="46df1-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="46df1-105">Vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="46df1-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="46df1-106">Pomocí výchozího nastavení rozložení.</span><span class="sxs-lookup"><span data-stu-id="46df1-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="46df1-107">Nastavení velikosti obsahu.</span><span class="sxs-lookup"><span data-stu-id="46df1-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="46df1-108">Pomocí absolutní umístění.</span><span class="sxs-lookup"><span data-stu-id="46df1-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="46df1-109">Určení velikosti explicitně.</span><span class="sxs-lookup"><span data-stu-id="46df1-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="46df1-110">Nastavení vlastností rozložení.</span><span class="sxs-lookup"><span data-stu-id="46df1-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="46df1-111">Principy pořadí z-order omezení.</span><span class="sxs-lookup"><span data-stu-id="46df1-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="46df1-112">Ukotvení.</span><span class="sxs-lookup"><span data-stu-id="46df1-112">Docking.</span></span>  
  
-   <span data-ttu-id="46df1-113">Nastavení viditelnosti.</span><span class="sxs-lookup"><span data-stu-id="46df1-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="46df1-114">Hostování ovládacího prvku, který není funkce stretch.</span><span class="sxs-lookup"><span data-stu-id="46df1-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="46df1-115">Škálování.</span><span class="sxs-lookup"><span data-stu-id="46df1-115">Scaling.</span></span>  
  
-   <span data-ttu-id="46df1-116">Otáčení.</span><span class="sxs-lookup"><span data-stu-id="46df1-116">Rotating.</span></span>  
  
-   <span data-ttu-id="46df1-117">Nastavení odsazení a okraje.</span><span class="sxs-lookup"><span data-stu-id="46df1-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="46df1-118">Použití dynamické rozložení kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="46df1-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="46df1-119">Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [uspořádání ovládacích prvků Windows Forms v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="46df1-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="46df1-120">Po dokončení bude mít k pochopení [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozložení funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikací.</span><span class="sxs-lookup"><span data-stu-id="46df1-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="46df1-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46df1-121">Prerequisites</span></span>  
 <span data-ttu-id="46df1-122">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="46df1-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="46df1-123">.</span><span class="sxs-lookup"><span data-stu-id="46df1-123">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="46df1-124">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="46df1-124">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="46df1-125">Vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="46df1-125">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="46df1-126">Vytvořte projekt aplikace WPF s názvem `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="46df1-126">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="46df1-127">V Průzkumníku řešení přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="46df1-127">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="46df1-128">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="46df1-128">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="46df1-129">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="46df1-129">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="46df1-130">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="46df1-130">System.Drawing</span></span>  
  
3.  <span data-ttu-id="46df1-131">Dvakrát klikněte na MainWindow.xaml a otevře se v zobrazení jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="46df1-131">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="46df1-132">V <xref:System.Windows.Window> elementu, přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="46df1-132">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="46df1-133">V <xref:System.Windows.Controls.Grid> element sadu <xref:System.Windows.Controls.Grid.ShowGridLines%2A> vlastnost `true` a definovat pět řádků a tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="46df1-133">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="46df1-134">Pomocí výchozího nastavení rozložení</span><span class="sxs-lookup"><span data-stu-id="46df1-134">Using Default Layout Settings</span></span>  
 <span data-ttu-id="46df1-135">Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element zpracovává rozložení pro hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="46df1-135">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="46df1-136">Chcete-li použít výchozí nastavení rozložení</span><span class="sxs-lookup"><span data-stu-id="46df1-136">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="46df1-137">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-137">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="46df1-138">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-138">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-139">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Zobrazí ovládací prvek v <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="46df1-139">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="46df1-140">Je velikost hostované ovládacího prvku, na základě jeho obsahu a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element je dimenzovány pro zvládnutí hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="46df1-140">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="46df1-141">Nastavení velikosti obsahu</span><span class="sxs-lookup"><span data-stu-id="46df1-141">Sizing to Content</span></span>  
 <span data-ttu-id="46df1-142"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek zajišťuje, že je správně zobrazit jeho obsah velikost hostované ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="46df1-142">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="46df1-143">Velikost obsahu</span><span class="sxs-lookup"><span data-stu-id="46df1-143">To size to content</span></span>  
  
1.  <span data-ttu-id="46df1-144">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-144">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="46df1-145">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-145">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-146">Jsou dvě nové ovládací prvky tlačítko dimenzované k zobrazení delší textového řetězce a zvětšení velikosti písma správně a <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou možnosti změnit velikost elementů zohlednit hostované ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="46df1-146">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="46df1-147">Pomocí absolutní umístění</span><span class="sxs-lookup"><span data-stu-id="46df1-147">Using Absolute Positioning</span></span>  
 <span data-ttu-id="46df1-148">Absolutní umístění můžete použít k umístění <xref:System.Windows.Forms.Integration.WindowsFormsHost> element kdekoli v uživatelském rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="46df1-148">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="46df1-149">Chcete-li použít absolutní umístění</span><span class="sxs-lookup"><span data-stu-id="46df1-149">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="46df1-150">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-150">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="46df1-151">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-151">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-152"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je umístěn 20 pixelů z na horní straně buňky mřížky a 20 pixelů od levého okraje.</span><span class="sxs-lookup"><span data-stu-id="46df1-152">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="46df1-153">Určení velikosti explicitně</span><span class="sxs-lookup"><span data-stu-id="46df1-153">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="46df1-154">Můžete zadat velikost <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pomocí <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="46df1-154">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="46df1-155">Chcete-li explicitně určit velikost</span><span class="sxs-lookup"><span data-stu-id="46df1-155">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="46df1-156">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-156">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="46df1-157">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-157">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-158"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je nastavena velikost 50 × široké 70 pixelů vysoké, což je menší než výchozí nastavení rozložení.</span><span class="sxs-lookup"><span data-stu-id="46df1-158">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="46df1-159">Obsah [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek je přeskupení odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="46df1-159">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="46df1-160">Nastavení vlastností rozložení</span><span class="sxs-lookup"><span data-stu-id="46df1-160">Setting Layout Properties</span></span>  
 <span data-ttu-id="46df1-161">Vždy nastavit vlastnosti související s rozložením na hostované ovládacího prvku pomocí vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-161">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="46df1-162">Nastavení vlastností rozložení přímo na hostované ovládací prvek předá neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="46df1-162">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="46df1-163">Nastavit vlastnosti související s rozložením hostované ovládacího prvku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="46df1-163">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="46df1-164">Chcete-li zobrazit důsledky nastavení vlastnosti na hostované ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="46df1-164">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="46df1-165">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-165">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="46df1-166">V Průzkumníku řešení klikněte dvakrát na MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="46df1-166">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="46df1-167">vb nebo MainWindow.xaml.cs a otevře se v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="46df1-167">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="46df1-168">Zkopírujte následující kód do `MainWindow` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="46df1-168">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  <span data-ttu-id="46df1-169">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-169">Press F5 to build and run the application.</span></span>  
  
5.  <span data-ttu-id="46df1-170">Klikněte **klikněte na tlačítko mi** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="46df1-170">Click the **Click me** button.</span></span> <span data-ttu-id="46df1-171">`button1_Click` Sady obslužné rutiny událostí <xref:System.Windows.Forms.Control.Top%2A> a <xref:System.Windows.Forms.Control.Left%2A> vlastností hostovaného prvku.</span><span class="sxs-lookup"><span data-stu-id="46df1-171">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="46df1-172">To způsobí, že hostovaný ovládací prvek změnit jejich umístění v rámci <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-172">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="46df1-173">Hostitel udržuje stejné oblasti obrazovky, ale je oříznut hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="46df1-173">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="46df1-174">Místo toho by měla vždycky vyplnění hostovaného ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-174">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="understanding-z-order-limitations"></a><span data-ttu-id="46df1-175">Seznámení s omezeními pořadí Z-Order</span><span class="sxs-lookup"><span data-stu-id="46df1-175">Understanding Z-Order Limitations</span></span>  
 <span data-ttu-id="46df1-176">Ve výchozím nastavení viditelné <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementy jsou vždy vykreslován nad dalších [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky a nejsou ovlivněny pořadí z-order.</span><span class="sxs-lookup"><span data-stu-id="46df1-176">By default, visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="46df1-177">Chcete-li povolit pořadí z-ordering, nastavte <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> na hodnotu true a <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> vlastnost <xref:System.Windows.Interop.CompositionMode.Full> nebo <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="46df1-177">To enable z-ordering, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-see-the-default-z-order-behavior"></a><span data-ttu-id="46df1-178">Chcete-li zobrazit výchozí chování pořadí z-order</span><span class="sxs-lookup"><span data-stu-id="46df1-178">To see the default z-order behavior</span></span>  
  
1.  <span data-ttu-id="46df1-179">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-179">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  <span data-ttu-id="46df1-180">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-180">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Vymalovávání elementu přes do elementu label.</span><span class="sxs-lookup"><span data-stu-id="46df1-181">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>  
  
#### <a name="to-see-the-z-order-behavior-when-isredirected-is-true"></a><span data-ttu-id="46df1-182">Chcete-li zobrazit pořadí z-order chování, pokud IsRedirected hodnotu true</span><span class="sxs-lookup"><span data-stu-id="46df1-182">To see the z-order behavior when IsRedirected is true</span></span>  
  
1.  <span data-ttu-id="46df1-183">Nahradí předchozí příklad pořadí z-order následující XAML.</span><span class="sxs-lookup"><span data-stu-id="46df1-183">Replace the previous z-order example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     <span data-ttu-id="46df1-184">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-184">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-185">Do elementu label se vykresluje přes <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-185">The label element is painted over the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
## <a name="docking"></a><span data-ttu-id="46df1-186">Ukotvení</span><span class="sxs-lookup"><span data-stu-id="46df1-186">Docking</span></span>  
 <span data-ttu-id="46df1-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost>element podporuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukotvení.</span><span class="sxs-lookup"><span data-stu-id="46df1-187"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="46df1-188">Nastavte <xref:System.Windows.Controls.DockPanel.Dock%2A> přidružená vlastnost chcete ukotvit hostované ovládacího prvku <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-188">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="46df1-189">Chcete-li ukotvit hostované ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="46df1-189">To dock a hosted control</span></span>  
  
1.  <span data-ttu-id="46df1-190">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-190">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  <span data-ttu-id="46df1-191">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-191">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-192"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element ukotven na pravé straně <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-192">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>  
  
## <a name="setting-visibility"></a><span data-ttu-id="46df1-193">Nastavení viditelnosti</span><span class="sxs-lookup"><span data-stu-id="46df1-193">Setting Visibility</span></span>  
 <span data-ttu-id="46df1-194">Můžete provést vaše [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení neviditelná nebo sbalit nastavením <xref:System.Windows.UIElement.Visibility%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-194">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="46df1-195">Když je ovládací prvek neviditelná, se nezobrazí, ale zabírá prostor rozložení.</span><span class="sxs-lookup"><span data-stu-id="46df1-195">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="46df1-196">Když ovládacího prvku sbalena, se nezobrazí, ani nemá zabírají prostor rozložení.</span><span class="sxs-lookup"><span data-stu-id="46df1-196">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="46df1-197">Chcete-li nastavit viditelnost hostované ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="46df1-197">To set the visibility of a hosted control</span></span>  
  
1.  <span data-ttu-id="46df1-198">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-198">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  <span data-ttu-id="46df1-199">MainWindow.xaml.vb nebo MainWindow.xaml.cs zkopírujte následující kód do definici třídy.</span><span class="sxs-lookup"><span data-stu-id="46df1-199">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  <span data-ttu-id="46df1-200">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-200">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="46df1-201">Klikněte na tlačítko **kliknutím na nastavit jako neviditelné** tlačítko, aby <xref:System.Windows.Forms.Integration.WindowsFormsHost> element neviditelná.</span><span class="sxs-lookup"><span data-stu-id="46df1-201">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>  
  
5.  <span data-ttu-id="46df1-202">Klikněte na tlačítko **kliknutím sbalit** tlačítko skrýt <xref:System.Windows.Forms.Integration.WindowsFormsHost> element z rozložení úplně.</span><span class="sxs-lookup"><span data-stu-id="46df1-202">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="46df1-203">Když [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení sbalena, okolního elementy jsou změněno tak, aby zabíral jeho místa.</span><span class="sxs-lookup"><span data-stu-id="46df1-203">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>  
  
## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="46df1-204">Hostování ovládacího prvku, který není funkce Stretch</span><span class="sxs-lookup"><span data-stu-id="46df1-204">Hosting a Control That Does Not Stretch</span></span>  
 <span data-ttu-id="46df1-205">Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky s pevnou velikostí mají a není roztáhnou tak, aby vyplnil celou dostupné místo v rozložení.</span><span class="sxs-lookup"><span data-stu-id="46df1-205">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="46df1-206">Například <xref:System.Windows.Forms.MonthCalendar> zobrazí měsíce v pevné mezery.</span><span class="sxs-lookup"><span data-stu-id="46df1-206">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="46df1-207">K hostování ovládacího prvku, který není funkce stretch</span><span class="sxs-lookup"><span data-stu-id="46df1-207">To host a control that does not stretch</span></span>  
  
1.  <span data-ttu-id="46df1-208">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-208">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  <span data-ttu-id="46df1-209">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-209">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-210"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je umístěn na střed v řádku mřížky, ale není roztažen tak, aby vyplňování dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="46df1-210">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="46df1-211">Pokud je okno dostatečně velké na to, uvidíte dvě nebo více měsíců zobrazuje hostované <xref:System.Windows.Forms.MonthCalendar> řízení, ale ty se na v řádku.</span><span class="sxs-lookup"><span data-stu-id="46df1-211">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="46df1-212">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Modul rozložení centra prvky, které nemůže být dimenzovány pro vyplňování dostupného místa.</span><span class="sxs-lookup"><span data-stu-id="46df1-212">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>  
  
## <a name="scaling"></a><span data-ttu-id="46df1-213">Změna měřítka</span><span class="sxs-lookup"><span data-stu-id="46df1-213">Scaling</span></span>  
 <span data-ttu-id="46df1-214">Na rozdíl od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy, většina [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nejsou nepřetržitě škálovatelné.</span><span class="sxs-lookup"><span data-stu-id="46df1-214">Unlike [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, most [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls are not continuously scalable.</span></span> <span data-ttu-id="46df1-215">Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element škáluje jeho hostované řízení, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="46df1-215">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element scales its hosted control when possible.</span></span>  <span data-ttu-id="46df1-216">Chcete-li povolit plnohodnotný škálování, nastavte <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> na hodnotu true a <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> vlastnost <xref:System.Windows.Interop.CompositionMode.Full> nebo <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="46df1-216">To enable full-fledged scaling, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="46df1-217">Škálování hostované ovládacího prvku pomocí výchozí chování</span><span class="sxs-lookup"><span data-stu-id="46df1-217">To scale a hosted control by using the default behavior</span></span>  
  
1.  <span data-ttu-id="46df1-218">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-218">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  <span data-ttu-id="46df1-219">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-219">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-220">Hostované ovládací prvek a jeho okolního elementy jsou škálovat faktorem 0,5.</span><span class="sxs-lookup"><span data-stu-id="46df1-220">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="46df1-221">Však není škálovat písma hostované ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="46df1-221">However, the hosted control's font is not scaled.</span></span>  
  
#### <a name="to-scale-a-hosted-control-by-setting-isredirected-to-true"></a><span data-ttu-id="46df1-222">Škálování ovládacího prvku hostované nastavením IsRedirected na hodnotu true</span><span class="sxs-lookup"><span data-stu-id="46df1-222">To scale a hosted control by setting IsRedirected to true</span></span>  
  
1.  <span data-ttu-id="46df1-223">Nahradí předchozí příklad škálování následující XAML.</span><span class="sxs-lookup"><span data-stu-id="46df1-223">Replace the previous scaling example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  <span data-ttu-id="46df1-224">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-224">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-225">Hostované řízení, jeho okolního elementy a hostované ovládacího prvku písma jsou škálovat faktorem 0,5.</span><span class="sxs-lookup"><span data-stu-id="46df1-225">The hosted control, its surrounding elements, and the hosted control's font are scaled by a factor of 0.5.</span></span>  
  
## <a name="rotating"></a><span data-ttu-id="46df1-226">Otáčení</span><span class="sxs-lookup"><span data-stu-id="46df1-226">Rotating</span></span>  
 <span data-ttu-id="46df1-227">Na rozdíl od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementů [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nepodporuje otočení.</span><span class="sxs-lookup"><span data-stu-id="46df1-227">Unlike [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls do not support rotation.</span></span> <span data-ttu-id="46df1-228">Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element není otočit s jinými [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvků při otočení transformací.</span><span class="sxs-lookup"><span data-stu-id="46df1-228">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements when a rotation transformation is applied.</span></span> <span data-ttu-id="46df1-229">Jakoukoli jinou hodnotu než 180 stupňů vyvolá otočení <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> událostí.</span><span class="sxs-lookup"><span data-stu-id="46df1-229">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>  <span data-ttu-id="46df1-230">Pokud chcete povolit, otáčení libovolném úhlu, nastavte <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> na hodnotu true a <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> vlastnost <xref:System.Windows.Interop.CompositionMode.Full> nebo <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span><span class="sxs-lookup"><span data-stu-id="46df1-230">To enable rotating to any angle, set the <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> property of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> to true and the <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> property to <xref:System.Windows.Interop.CompositionMode.Full> or <xref:System.Windows.Interop.CompositionMode.OutputOnly>.</span></span>  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="46df1-231">Pokud chcete vidět otočení v hybridní aplikace</span><span class="sxs-lookup"><span data-stu-id="46df1-231">To see the effect of rotation in a hybrid application</span></span>  
  
1.  <span data-ttu-id="46df1-232">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-232">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  <span data-ttu-id="46df1-233">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-233">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-234">Hostované ovládací prvek není otáčet, ale jeho elementy okolního jsou otáčet o úhel 180 stupňů.</span><span class="sxs-lookup"><span data-stu-id="46df1-234">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="46df1-235">Možná budete muset změnit velikost okna zobrazíte elementy.</span><span class="sxs-lookup"><span data-stu-id="46df1-235">You may have to resize the window to see the elements.</span></span>  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application-when-isredirected-is-true"></a><span data-ttu-id="46df1-236">Pokud chcete vidět otočení v hybridní aplikace, pokud IsRedirected hodnotu true</span><span class="sxs-lookup"><span data-stu-id="46df1-236">To see the effect of rotation in a hybrid application when IsRedirected is true</span></span>  
  
1.  <span data-ttu-id="46df1-237">Předchozí příklad otočení nahradí následující XAML.</span><span class="sxs-lookup"><span data-stu-id="46df1-237">Replace the previous rotation example with the following XAML.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  <span data-ttu-id="46df1-238">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-239">Hostované ovládacího prvku otočen.</span><span class="sxs-lookup"><span data-stu-id="46df1-239">The hosted control is rotated.</span></span>  <span data-ttu-id="46df1-240">Všimněte si, že <xref:System.Windows.Media.RotateTransform.Angle%2A> může být nastavena na jakoukoli hodnotu.</span><span class="sxs-lookup"><span data-stu-id="46df1-240">Note that the <xref:System.Windows.Media.RotateTransform.Angle%2A> property can be set to any value.</span></span> <span data-ttu-id="46df1-241">Možná budete muset změnit velikost okna zobrazíte elementy.</span><span class="sxs-lookup"><span data-stu-id="46df1-241">You may have to resize the window to see the elements.</span></span>  
  
## <a name="setting-padding-and-margins"></a><span data-ttu-id="46df1-242">Nastavení odsazení a okraje</span><span class="sxs-lookup"><span data-stu-id="46df1-242">Setting Padding and Margins</span></span>  
 <span data-ttu-id="46df1-243">Odsazení a okraje v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení jsou podobné odsazení a okraje v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46df1-243">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="46df1-244">Jednoduše nastavit <xref:System.Windows.Controls.Control.Padding%2A> a <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-244">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="46df1-245">Nastavení odsazení a okrajů pro hostované ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="46df1-245">To set padding and margins for a hosted control</span></span>  
  
1.  <span data-ttu-id="46df1-246">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-246">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  <span data-ttu-id="46df1-247">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-247">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-248">Nastavení odsazení a okrajů se použijí k hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky stejným způsobem, že by bylo možné provést v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46df1-248">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="46df1-249">Použití kontejnerů dynamické rozložení</span><span class="sxs-lookup"><span data-stu-id="46df1-249">Using Dynamic Layout Containers</span></span>  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="46df1-250">poskytuje dvě dynamické rozložení kontejnery <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="46df1-250"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="46df1-251">Můžete také použít tyto kontejnery v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení.</span><span class="sxs-lookup"><span data-stu-id="46df1-251">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>  
  
#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="46df1-252">Použít kontejner dynamické rozložení</span><span class="sxs-lookup"><span data-stu-id="46df1-252">To use a dynamic layout container</span></span>  
  
1.  <span data-ttu-id="46df1-253">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="46df1-253">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  <span data-ttu-id="46df1-254">MainWindow.xaml.vb nebo MainWindow.xaml.cs zkopírujte následující kód do definici třídy.</span><span class="sxs-lookup"><span data-stu-id="46df1-254">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  <span data-ttu-id="46df1-255">Přidejte volání `InitializeFlowLayoutPanel` metoda v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="46df1-255">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="46df1-256">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="46df1-256">Press F5 to build and run the application.</span></span> <span data-ttu-id="46df1-257"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element doplní <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Forms.FlowLayoutPanel> uspořádá jeho podřízených ovládacích prvků ve výchozí <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="46df1-257">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46df1-258">Viz také</span><span class="sxs-lookup"><span data-stu-id="46df1-258">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="46df1-259">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="46df1-259">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="46df1-260">Předpoklady rozložení pro element WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="46df1-260">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="46df1-261">Uspořádání Windows Forms – ovládací prvky v ukázce WPF</span><span class="sxs-lookup"><span data-stu-id="46df1-261">Arranging Windows Forms Controls in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="46df1-262">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="46df1-262">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="46df1-263">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46df1-263">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
