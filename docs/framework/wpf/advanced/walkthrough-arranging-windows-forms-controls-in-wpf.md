---
title: 'Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 31afacd6bb387a4df9eb8d36d2dc224ead63cc68
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842434"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="ea88f-102">Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="ea88f-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>
<span data-ttu-id="ea88f-103">Tento návod ukazuje, jak používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcí rozložení uspořádat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků v hybridní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>  
  
 <span data-ttu-id="ea88f-104">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="ea88f-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="ea88f-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="ea88f-106">Pomocí výchozího nastavení rozložení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-106">Using default layout settings.</span></span>  
  
-   <span data-ttu-id="ea88f-107">Nastavení velikosti obsahu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-107">Sizing to content.</span></span>  
  
-   <span data-ttu-id="ea88f-108">Použití absolutní pozici.</span><span class="sxs-lookup"><span data-stu-id="ea88f-108">Using absolute positioning.</span></span>  
  
-   <span data-ttu-id="ea88f-109">Určení velikosti explicitně.</span><span class="sxs-lookup"><span data-stu-id="ea88f-109">Specifying size explicitly.</span></span>  
  
-   <span data-ttu-id="ea88f-110">Nastavení vlastnosti rozložení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-110">Setting layout properties.</span></span>  
  
-   <span data-ttu-id="ea88f-111">Principy omezení pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="ea88f-111">Understanding z-order limitations.</span></span>  
  
-   <span data-ttu-id="ea88f-112">Ukotvení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-112">Docking.</span></span>  
  
-   <span data-ttu-id="ea88f-113">Nastavení viditelnosti.</span><span class="sxs-lookup"><span data-stu-id="ea88f-113">Setting visibility.</span></span>  
  
-   <span data-ttu-id="ea88f-114">Hostování ovládacího prvku, který není stretch.</span><span class="sxs-lookup"><span data-stu-id="ea88f-114">Hosting a control that does not stretch.</span></span>  
  
-   <span data-ttu-id="ea88f-115">Škálování.</span><span class="sxs-lookup"><span data-stu-id="ea88f-115">Scaling.</span></span>  
  
-   <span data-ttu-id="ea88f-116">Otáčení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-116">Rotating.</span></span>  
  
-   <span data-ttu-id="ea88f-117">Nastavení odsazení a okraje.</span><span class="sxs-lookup"><span data-stu-id="ea88f-117">Setting padding and margins.</span></span>  
  
-   <span data-ttu-id="ea88f-118">Použití dynamického rozložení kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="ea88f-118">Using dynamic layout containers.</span></span>  
  
 <span data-ttu-id="ea88f-119">Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [uspořádání prvky Windows Forms v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="ea88f-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>  
  
 <span data-ttu-id="ea88f-120">Až budete hotovi, budete mít znalost [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozložení funkce v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na.</span><span class="sxs-lookup"><span data-stu-id="ea88f-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ea88f-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea88f-121">Prerequisites</span></span>  

<span data-ttu-id="ea88f-122">Visual Studio k dokončení tohoto návodu potřebujete.</span><span class="sxs-lookup"><span data-stu-id="ea88f-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="creating-the-project"></a><span data-ttu-id="ea88f-123">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="ea88f-123">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="ea88f-124">K vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="ea88f-124">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="ea88f-125">Vytvoření projektu aplikace WPF s názvem `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="ea88f-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>  
  
2.  <span data-ttu-id="ea88f-126">V Průzkumníku řešení přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-126">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="ea88f-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="ea88f-127">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="ea88f-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="ea88f-128">System.Windows.Forms</span></span>  
  
    -   <span data-ttu-id="ea88f-129">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="ea88f-129">System.Drawing</span></span>  
  
3.  <span data-ttu-id="ea88f-130">Poklikejte na soubor MainWindow.xaml a otevřete ho v XAML zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-130">Double-click MainWindow.xaml to open it in XAML view.</span></span>  
  
4.  <span data-ttu-id="ea88f-131">V <xref:System.Windows.Window> prvku, přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ea88f-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="ea88f-132">V <xref:System.Windows.Controls.Grid> set elementu <xref:System.Windows.Controls.Grid.ShowGridLines%2A> vlastnost `true` a definování pěti řádky a tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="ea88f-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a><span data-ttu-id="ea88f-133">Pomocí výchozího nastavení rozložení</span><span class="sxs-lookup"><span data-stu-id="ea88f-133">Using Default Layout Settings</span></span>  
 <span data-ttu-id="ea88f-134">Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> element zpracovává rozložení pro hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ea88f-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-use-default-layout-settings"></a><span data-ttu-id="ea88f-135">Chcete-li použít výchozí nastavení rozložení</span><span class="sxs-lookup"><span data-stu-id="ea88f-135">To use default layout settings</span></span>  
  
1.  <span data-ttu-id="ea88f-136">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  <span data-ttu-id="ea88f-137">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-137">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-138">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Ovládací prvek zobrazí <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="ea88f-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="ea88f-139">Hostovaného ovládacího prvku je velikost na základě jeho obsahu a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element je dimenzovány pro zvládnutí hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ea88f-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>  
  
## <a name="sizing-to-content"></a><span data-ttu-id="ea88f-140">Nastavení velikosti obsahu</span><span class="sxs-lookup"><span data-stu-id="ea88f-140">Sizing to Content</span></span>  
 <span data-ttu-id="ea88f-141"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek zajišťuje, že je správně zobrazit jeho obsah velikost hostované ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ea88f-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>  
  
#### <a name="to-size-to-content"></a><span data-ttu-id="ea88f-142">Pro nastavení velikosti obsahu</span><span class="sxs-lookup"><span data-stu-id="ea88f-142">To size to content</span></span>  
  
1.  <span data-ttu-id="ea88f-143">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  <span data-ttu-id="ea88f-144">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-144">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-145">Pro zobrazení delšího textový řetězec a větší velikost písma správně, je velikost dva nové ovládací prvky tlačítka a <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky jsou velikost hostované ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="ea88f-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>  
  
## <a name="using-absolute-positioning"></a><span data-ttu-id="ea88f-146">Použití absolutní pozici</span><span class="sxs-lookup"><span data-stu-id="ea88f-146">Using Absolute Positioning</span></span>  
 <span data-ttu-id="ea88f-147">Absolutní umístění můžete použít k umístění <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek kdekoli v uživatelském rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="ea88f-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>  
  
#### <a name="to-use-absolute-positioning"></a><span data-ttu-id="ea88f-148">Chcete-li použít absolutní pozici</span><span class="sxs-lookup"><span data-stu-id="ea88f-148">To use absolute positioning</span></span>  
  
1.  <span data-ttu-id="ea88f-149">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  <span data-ttu-id="ea88f-150">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-150">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-151"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element nachází 20 pixelů v horním rohu buňky mřížky a 20 pixelů od levého okraje.</span><span class="sxs-lookup"><span data-stu-id="ea88f-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>  
  
## <a name="specifying-size-explicitly"></a><span data-ttu-id="ea88f-152">Explicitní určení velikosti</span><span class="sxs-lookup"><span data-stu-id="ea88f-152">Specifying Size Explicitly</span></span>  
 <span data-ttu-id="ea88f-153">Můžete zadat velikost <xref:System.Windows.Forms.Integration.WindowsFormsHost> pomocí elementu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ea88f-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>  
  
#### <a name="to-specify-size-explicitly"></a><span data-ttu-id="ea88f-154">Chcete-li explicitně určit velikost</span><span class="sxs-lookup"><span data-stu-id="ea88f-154">To specify size explicitly</span></span>  
  
1.  <span data-ttu-id="ea88f-155">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  <span data-ttu-id="ea88f-156">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-156">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-157"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je nastaven na velikost 50 pixelů na šířku a 70 pixelů na výšku, které je menší než nastavení výchozí rozložení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="ea88f-158">Obsah [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek je odpovídajícím způsobem měnit.</span><span class="sxs-lookup"><span data-stu-id="ea88f-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>  
  
## <a name="setting-layout-properties"></a><span data-ttu-id="ea88f-159">Nastavení vlastnosti rozložení</span><span class="sxs-lookup"><span data-stu-id="ea88f-159">Setting Layout Properties</span></span>  
 <span data-ttu-id="ea88f-160">Vždy nastavit vlastnosti související s rozložením hostovaného ovládacího prvku pomocí vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="ea88f-161">Nastavení vlastností rozložení přímo na hostovaného ovládacího prvku poskytne neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="ea88f-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>  
  
 <span data-ttu-id="ea88f-162">Nastavení vlastností související s rozložením hostovaného ovládacího prvku v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="ea88f-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="ea88f-163">Abyste viděli efekt nastavování vlastností na hostovaného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ea88f-163">To see the effects of setting properties on the hosted control</span></span>  
  
1.  <span data-ttu-id="ea88f-164">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  <span data-ttu-id="ea88f-165">V Průzkumníku řešení poklikejte na soubor MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="ea88f-165">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="ea88f-166">vb nebo MainWindow.xaml.cs ho otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-166">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>  
  
3.  <span data-ttu-id="ea88f-167">Zkopírujte následující kód do `MainWindow` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="ea88f-167">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4.  <span data-ttu-id="ea88f-168">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-168">Press F5 to build and run the application.</span></span>

5.  <span data-ttu-id="ea88f-169">Klikněte na tlačítko **klikněte na mě** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ea88f-169">Click the **Click me** button.</span></span> <span data-ttu-id="ea88f-170">`button1_Click` Sady obslužné rutiny události <xref:System.Windows.Forms.Control.Top%2A> a <xref:System.Windows.Forms.Control.Left%2A> vlastnosti hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ea88f-170">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="ea88f-171">To způsobí, že hostovaný ovládací prvek změnit umístění v rámci <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-171">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="ea88f-172">Hostitel udržuje stejné oblasti obrazovky, ale oříznut hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ea88f-172">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="ea88f-173">Místo toho by měla vždy zaplnit hostovaného ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-173">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="ea88f-174">Principy omezení pořadí vykreslování</span><span class="sxs-lookup"><span data-stu-id="ea88f-174">Understanding Z-Order Limitations</span></span>
 <span data-ttu-id="ea88f-175">Viditelné <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky jsou vždy vykreslován nad další prvky WPF a jsou ovlivněny pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="ea88f-175">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="ea88f-176">Pokud chcete zobrazit toto chování pořadí vykreslování, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="ea88f-176">To see this z-order behavior, do the following:</span></span>

1.  <span data-ttu-id="ea88f-177">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-177">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2.  <span data-ttu-id="ea88f-178">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-178">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-179"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Nad prvkem popisek vymalovávání elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-179">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>


## <a name="docking"></a><span data-ttu-id="ea88f-180">Ukotvení</span><span class="sxs-lookup"><span data-stu-id="ea88f-180">Docking</span></span>
 <span data-ttu-id="ea88f-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> podporuje prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukotvení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="ea88f-182">Nastavit <xref:System.Windows.Controls.DockPanel.Dock%2A> přidružená vlastnost ukotvení hostované ovládacího prvku <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-182">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

#### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="ea88f-183">Chcete-li ukotvit hostovaného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ea88f-183">To dock a hosted control</span></span>

1.  <span data-ttu-id="ea88f-184">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-184">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2.  <span data-ttu-id="ea88f-185">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-185">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-186"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek ukotven k pravému okraji <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-186">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="ea88f-187">Nastavení viditelnosti</span><span class="sxs-lookup"><span data-stu-id="ea88f-187">Setting Visibility</span></span>
 <span data-ttu-id="ea88f-188">Můžete provést vaše [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řídit neviditelný nebo sbalit nastavením <xref:System.Windows.UIElement.Visibility%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-188">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="ea88f-189">Když je ovládací prvek neviditelné, se nezobrazí, ale zabírá místo rozložení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-189">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="ea88f-190">Když je sbalen ovládací prvek, se nezobrazí ani nemá zabírat místo rozložení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-190">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

#### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="ea88f-191">Chcete-li nastavit, zda se hostovaného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ea88f-191">To set the visibility of a hosted control</span></span>

1.  <span data-ttu-id="ea88f-192">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-192">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2.  <span data-ttu-id="ea88f-193">V souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs zkopírujte následující kód do definice třídy.</span><span class="sxs-lookup"><span data-stu-id="ea88f-193">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3.  <span data-ttu-id="ea88f-194">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-194">Press F5 to build and run the application.</span></span>

4.  <span data-ttu-id="ea88f-195">Klikněte na tlačítko **kliknutím skrytí** tlačítka <xref:System.Windows.Forms.Integration.WindowsFormsHost> element neviditelné.</span><span class="sxs-lookup"><span data-stu-id="ea88f-195">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5.  <span data-ttu-id="ea88f-196">Klikněte na tlačítko **kliknutím sbalte** tlačítko skrýt <xref:System.Windows.Forms.Integration.WindowsFormsHost> element z rozložení úplně.</span><span class="sxs-lookup"><span data-stu-id="ea88f-196">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="ea88f-197">Když [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] je sbalen ovládací prvek, okolního prvky jsou změnit jejich uspořádání tak, aby obsadily své místo.</span><span class="sxs-lookup"><span data-stu-id="ea88f-197">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="ea88f-198">Hostování ovládacího prvku, který není Stretch</span><span class="sxs-lookup"><span data-stu-id="ea88f-198">Hosting a Control That Does Not Stretch</span></span>
 <span data-ttu-id="ea88f-199">Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky mají pevnou velikost a ne roztáhnout tak, aby vyplnil dostupné místo v rozložení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-199">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="ea88f-200">Například <xref:System.Windows.Forms.MonthCalendar> ovládací prvek zobrazí v pevná mezera za měsíc.</span><span class="sxs-lookup"><span data-stu-id="ea88f-200">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

#### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="ea88f-201">K hostování ovládacího prvku, který není stretch</span><span class="sxs-lookup"><span data-stu-id="ea88f-201">To host a control that does not stretch</span></span>

1.  <span data-ttu-id="ea88f-202">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-202">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2.  <span data-ttu-id="ea88f-203">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-203">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-204"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je uprostřed řádku mřížky, ale ta není roztažená tak, aby vyplnil dostupné místo.</span><span class="sxs-lookup"><span data-stu-id="ea88f-204">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="ea88f-205">Pokud okna je příliš velká, může se zobrazit dvě nebo víc měsíců zobrazený hostovanou <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku, ale ty se na v řádku.</span><span class="sxs-lookup"><span data-stu-id="ea88f-205">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="ea88f-206">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Modul rozložení centra pro prvky, které nelze mít velikost tak, aby vyplnil dostupné místo.</span><span class="sxs-lookup"><span data-stu-id="ea88f-206">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="ea88f-207">Škálování</span><span class="sxs-lookup"><span data-stu-id="ea88f-207">Scaling</span></span>
 <span data-ttu-id="ea88f-208">Na rozdíl od prvků WPF nejsou průběžně škálovatelné většina ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ea88f-208">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="ea88f-209">Pokud chcete zadat vlastní škálování, přepíšete <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ea88f-209">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="ea88f-210">Škálování hostovaného ovládacího prvku s použitím výchozí chování</span><span class="sxs-lookup"><span data-stu-id="ea88f-210">To scale a hosted control by using the default behavior</span></span>

1.  <span data-ttu-id="ea88f-211">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-211">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2.  <span data-ttu-id="ea88f-212">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-212">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-213">Hostovaného ovládacího prvku a jeho okolního prvky jsou měřítkem řídit 0,5.</span><span class="sxs-lookup"><span data-stu-id="ea88f-213">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="ea88f-214">Však není škálovat písma hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ea88f-214">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="ea88f-215">Otáčení</span><span class="sxs-lookup"><span data-stu-id="ea88f-215">Rotating</span></span>
 <span data-ttu-id="ea88f-216">Na rozdíl od WPF elementů ovládacích prvků Windows Forms nepodporují otočení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-216">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="ea88f-217"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element není s jinými prvky WPF otočí, když je použita transformace otočení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-217">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="ea88f-218">Jakoukoli otočení jinou hodnotu než vyvolá 180stupňový rozsah s orientací <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> událostí.</span><span class="sxs-lookup"><span data-stu-id="ea88f-218">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="ea88f-219">A vidět její účinek otáčení v hybridní aplikaci</span><span class="sxs-lookup"><span data-stu-id="ea88f-219">To see the effect of rotation in a hybrid application</span></span>

1.  <span data-ttu-id="ea88f-220">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-220">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2.  <span data-ttu-id="ea88f-221">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-221">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-222">Otočen hostovaného ovládacího prvku, ale jeho okolního prvky jsou otočit o úhel 180 stupňů.</span><span class="sxs-lookup"><span data-stu-id="ea88f-222">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="ea88f-223">Budete muset změnit velikost okna zobrazení prvků.</span><span class="sxs-lookup"><span data-stu-id="ea88f-223">You may have to resize the window to see the elements.</span></span>


## <a name="setting-padding-and-margins"></a><span data-ttu-id="ea88f-224">Nastavení odsazení a okraje</span><span class="sxs-lookup"><span data-stu-id="ea88f-224">Setting Padding and Margins</span></span>
 <span data-ttu-id="ea88f-225">Odsazení a okrajů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení jsou podobné odsazení a okraje [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea88f-225">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="ea88f-226">Stačí nastavit <xref:System.Windows.Controls.Control.Padding%2A> a <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-226">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="ea88f-227">Nastavte odsazení a okrajů pro hostované ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ea88f-227">To set padding and margins for a hosted control</span></span>

1.  <span data-ttu-id="ea88f-228">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-228">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2.  <span data-ttu-id="ea88f-229">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-229">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-230">Použijí se nastavení odsazení a okraj na hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky stejně, jako by být použity v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea88f-230">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="ea88f-231">Pomocí kontejnerů dynamické rozložení</span><span class="sxs-lookup"><span data-stu-id="ea88f-231">Using Dynamic Layout Containers</span></span>
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <span data-ttu-id="ea88f-232">poskytuje dva kontejnery dynamického rozložení, <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="ea88f-232"> provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="ea88f-233">Můžete také použít tyto kontejnery v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení.</span><span class="sxs-lookup"><span data-stu-id="ea88f-233">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

#### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="ea88f-234">Použití kontejneru dynamické rozložení</span><span class="sxs-lookup"><span data-stu-id="ea88f-234">To use a dynamic layout container</span></span>

1.  <span data-ttu-id="ea88f-235">Zkopírujte následující XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="ea88f-235">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2.  <span data-ttu-id="ea88f-236">V souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs zkopírujte následující kód do definice třídy.</span><span class="sxs-lookup"><span data-stu-id="ea88f-236">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3.  <span data-ttu-id="ea88f-237">Přidejte volání `InitializeFlowLayoutPanel` metoda v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ea88f-237">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  <span data-ttu-id="ea88f-238">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea88f-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="ea88f-239"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek vyplní <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Forms.FlowLayoutPanel> uspořádá jeho podřízených ovládacích prvků ve výchozím <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="ea88f-239">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea88f-240">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea88f-240">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="ea88f-241">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ea88f-241">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [<span data-ttu-id="ea88f-242">Předpoklady rozložení pro element WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="ea88f-242">Layout Considerations for the WindowsFormsHost Element</span></span>](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [<span data-ttu-id="ea88f-243">Uspořádání Windows Forms ovládací prvky v ukázce WPF</span><span class="sxs-lookup"><span data-stu-id="ea88f-243">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)  
 [<span data-ttu-id="ea88f-244">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="ea88f-244">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="ea88f-245">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ea88f-245">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
