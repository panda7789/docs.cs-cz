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
ms.openlocfilehash: 484895db539b288bf388ff6c2ce3c29db55080b1
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197839"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="0880a-102">Návod: Uspořádání ovládacích prvků Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="0880a-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="0880a-103">V tomto návodu se dozvíte, jak používat funkce rozložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k uspořádání [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků v hybridní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="0880a-104">Úlohy, které jsou znázorněné v tomto návodu, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="0880a-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="0880a-105">Vytváří se projekt.</span><span class="sxs-lookup"><span data-stu-id="0880a-105">Creating the project.</span></span>
- <span data-ttu-id="0880a-106">Používá se výchozí nastavení rozložení.</span><span class="sxs-lookup"><span data-stu-id="0880a-106">Using default layout settings.</span></span>
- <span data-ttu-id="0880a-107">Změna velikosti obsahu.</span><span class="sxs-lookup"><span data-stu-id="0880a-107">Sizing to content.</span></span>
- <span data-ttu-id="0880a-108">Použití absolutního umístění.</span><span class="sxs-lookup"><span data-stu-id="0880a-108">Using absolute positioning.</span></span>
- <span data-ttu-id="0880a-109">Explicitní určení velikosti</span><span class="sxs-lookup"><span data-stu-id="0880a-109">Specifying size explicitly.</span></span>
- <span data-ttu-id="0880a-110">Nastavení vlastností rozložení.</span><span class="sxs-lookup"><span data-stu-id="0880a-110">Setting layout properties.</span></span>
- <span data-ttu-id="0880a-111">Porozumění omezením pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="0880a-111">Understanding z-order limitations.</span></span>
- <span data-ttu-id="0880a-112">Ukotvení.</span><span class="sxs-lookup"><span data-stu-id="0880a-112">Docking.</span></span>
- <span data-ttu-id="0880a-113">Nastavení viditelnosti.</span><span class="sxs-lookup"><span data-stu-id="0880a-113">Setting visibility.</span></span>
- <span data-ttu-id="0880a-114">Hostování ovládacího prvku, který se nepřizpůsobuje.</span><span class="sxs-lookup"><span data-stu-id="0880a-114">Hosting a control that does not stretch.</span></span>
- <span data-ttu-id="0880a-115">Změně.</span><span class="sxs-lookup"><span data-stu-id="0880a-115">Scaling.</span></span>
- <span data-ttu-id="0880a-116">Otočné.</span><span class="sxs-lookup"><span data-stu-id="0880a-116">Rotating.</span></span>
- <span data-ttu-id="0880a-117">Nastavení odsazení a okrajů</span><span class="sxs-lookup"><span data-stu-id="0880a-117">Setting padding and margins.</span></span>
- <span data-ttu-id="0880a-118">Použití kontejnerů dynamického rozložení.</span><span class="sxs-lookup"><span data-stu-id="0880a-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="0880a-119">Úplný výpis kódu úloh, které jsou znázorněny v tomto návodu, naleznete v tématu [uspořádání model Windows Formsch ovládacích prvků v UKÁZCE WPF](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="0880a-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="0880a-120">Až budete hotovi, budete obeznámeni s funkcemi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] rozložení v aplikacích založených na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0880a-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0880a-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0880a-121">Prerequisites</span></span>

<span data-ttu-id="0880a-122">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0880a-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="0880a-123">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="0880a-123">Creating the Project</span></span>

<span data-ttu-id="0880a-124">Chcete-li vytvořit a nastavit projekt, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="0880a-124">To create and set up the project, follow these steps:</span></span>

1. <span data-ttu-id="0880a-125">Vytvořte projekt aplikace WPF s názvem `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="0880a-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="0880a-126">V Průzkumník řešení přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="0880a-126">In Solution Explorer, add references to the following assemblies:</span></span>

    - <span data-ttu-id="0880a-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="0880a-127">WindowsFormsIntegration</span></span>
    - <span data-ttu-id="0880a-128">System. Windows. Forms</span><span class="sxs-lookup"><span data-stu-id="0880a-128">System.Windows.Forms</span></span>
    - <span data-ttu-id="0880a-129">System. Drawing</span><span class="sxs-lookup"><span data-stu-id="0880a-129">System.Drawing</span></span>

3. <span data-ttu-id="0880a-130">Poklikejte na *MainWindow. XAML* a otevře se v zobrazení XAML.</span><span class="sxs-lookup"><span data-stu-id="0880a-130">Double-click *MainWindow.xaml* to open it in XAML view.</span></span>

4. <span data-ttu-id="0880a-131">V elementu <xref:System.Windows.Window> přidejte následující mapování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0880a-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="0880a-132">V prvku <xref:System.Windows.Controls.Grid> nastavte vlastnost <xref:System.Windows.Controls.Grid.ShowGridLines%2A> na hodnotu `true` a definujte pět řádků a tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="0880a-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="0880a-133">Použití výchozího nastavení rozložení</span><span class="sxs-lookup"><span data-stu-id="0880a-133">Using Default Layout Settings</span></span>

<span data-ttu-id="0880a-134">Ve výchozím nastavení prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> zpracovává rozložení pro hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="0880a-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="0880a-135">Chcete-li použít výchozí nastavení rozložení, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="0880a-135">To use default layout settings, follow these steps:</span></span>

1. <span data-ttu-id="0880a-136">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="0880a-137">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-137">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-138">V <xref:System.Windows.Controls.Canvas>se zobrazí ovládací prvek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0880a-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="0880a-139">Hostovaný ovládací prvek má velikost na základě jeho obsahu a prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> má velikost pro přizpůsobení hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0880a-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="0880a-140">Změna velikosti obsahu</span><span class="sxs-lookup"><span data-stu-id="0880a-140">Sizing to Content</span></span>

<span data-ttu-id="0880a-141">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> zajišťuje, že hostovaný ovládací prvek má velikost pro správné zobrazení obsahu.</span><span class="sxs-lookup"><span data-stu-id="0880a-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

<span data-ttu-id="0880a-142">Chcete-li nastavit velikost obsahu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="0880a-142">To size to content, follow these steps:</span></span>

1. <span data-ttu-id="0880a-143">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="0880a-144">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-144">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-145">Dva nové ovládací prvky tlačítka mají velikost pro zobrazení delšího textového řetězce a větší velikosti písma a prvky <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou změněna tak, aby vyhovovaly hostovaným ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="0880a-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="0880a-146">Použití absolutního umístění</span><span class="sxs-lookup"><span data-stu-id="0880a-146">Using Absolute Positioning</span></span>

<span data-ttu-id="0880a-147">Absolutní umístění lze použít k umístění elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> kdekoli v uživatelském rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="0880a-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

<span data-ttu-id="0880a-148">Chcete-li použít absolutní umístění, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="0880a-148">To use absolute positioning, follow these steps:</span></span>

1. <span data-ttu-id="0880a-149">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="0880a-150">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-150">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-151">Prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je umístěn 20 pixelů od horní strany buňky mřížky a 20 pixelů vlevo.</span><span class="sxs-lookup"><span data-stu-id="0880a-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="0880a-152">Explicitní určení velikosti</span><span class="sxs-lookup"><span data-stu-id="0880a-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="0880a-153">Můžete určit velikost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu pomocí vlastností <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="0880a-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

<span data-ttu-id="0880a-154">Pokud chcete určit velikost explicitně, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="0880a-154">To specify size explicitly, follow these steps:</span></span>

1. <span data-ttu-id="0880a-155">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="0880a-156">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-156">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-157">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> je nastaven na velikost 50 pixelů v šířce až 70 pixelů vysoké, což je menší než výchozí nastavení rozložení.</span><span class="sxs-lookup"><span data-stu-id="0880a-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="0880a-158">Obsah ovládacího prvku [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] se odpovídajícím způsobem změní.</span><span class="sxs-lookup"><span data-stu-id="0880a-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="0880a-159">Nastavení vlastností rozložení</span><span class="sxs-lookup"><span data-stu-id="0880a-159">Setting Layout Properties</span></span>

<span data-ttu-id="0880a-160">V hostovaném ovládacím prvku vždy nastavte vlastnosti související s rozložením pomocí vlastností elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="0880a-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="0880a-161">Nastavení vlastností rozložení přímo v hostovaném ovládacím prvku bude vracet neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="0880a-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="0880a-162">Nastavení vlastností souvisejících s rozložením u hostovaného ovládacího prvku v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="0880a-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

<span data-ttu-id="0880a-163">Chcete-li zobrazit účinky nastavení vlastností u hostovaného ovládacího prvku, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="0880a-163">To see the effects of setting properties on the hosted control, follow these steps:</span></span>

1. <span data-ttu-id="0880a-164">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="0880a-165">V **Průzkumník řešení**poklikejte na *MainWindow. XAML. vb* nebo *MainWindow.XAML.cs* a otevře se v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="0880a-165">In **Solution Explorer**, double-click *MainWindow.xaml.vb* or *MainWindow.xaml.cs* to open it in the Code Editor.</span></span>

3. <span data-ttu-id="0880a-166">Zkopírujte následující kód do definice třídy `MainWindow`:</span><span class="sxs-lookup"><span data-stu-id="0880a-166">Copy the following code into the `MainWindow` class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="0880a-167">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-167">Press <kbd>F5</kbd> to build and run the application.</span></span>

5. <span data-ttu-id="0880a-168">Klikněte na tlačítko **klepnutím na tlačítko** .</span><span class="sxs-lookup"><span data-stu-id="0880a-168">Click the **Click me** button.</span></span> <span data-ttu-id="0880a-169">Obslužná rutina události `button1_Click` nastaví vlastnosti <xref:System.Windows.Forms.Control.Top%2A> a <xref:System.Windows.Forms.Control.Left%2A> v hostovaném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="0880a-169">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="0880a-170">Tím dojde k přemístění hostovaného ovládacího prvku v rámci elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="0880a-170">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="0880a-171">Hostitel udržuje stejnou oblast obrazovky, ale hostovaný ovládací prvek je oříznutý.</span><span class="sxs-lookup"><span data-stu-id="0880a-171">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="0880a-172">Místo toho by měl hostovaný ovládací prvek vždy vyplnit <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span><span class="sxs-lookup"><span data-stu-id="0880a-172">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="0880a-173">Porozumění omezením pořadí vykreslování</span><span class="sxs-lookup"><span data-stu-id="0880a-173">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="0880a-174">Viditelné prvky <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou vždy vykresleny nad ostatními prvky WPF a nejsou ovlivněny pořadím z.</span><span class="sxs-lookup"><span data-stu-id="0880a-174">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="0880a-175">Chcete-li zobrazit toto chování z pořadí vykreslování, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="0880a-175">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="0880a-176">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-176">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="0880a-177">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-177">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-178">Prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je vykreslen nad prvkem Label.</span><span class="sxs-lookup"><span data-stu-id="0880a-178">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="0880a-179">Ukotvení</span><span class="sxs-lookup"><span data-stu-id="0880a-179">Docking</span></span>

<span data-ttu-id="0880a-180">element <xref:System.Windows.Forms.Integration.WindowsFormsHost> podporuje ukotvení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0880a-180"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="0880a-181">Nastavte vlastnost <xref:System.Windows.Controls.DockPanel.Dock%2A> připojeno k ukotvení hostovaného ovládacího prvku v <xref:System.Windows.Controls.DockPanel> elementu.</span><span class="sxs-lookup"><span data-stu-id="0880a-181">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

<span data-ttu-id="0880a-182">Pro ukotvení hostovaného ovládacího prvku postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="0880a-182">To dock a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="0880a-183">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-183">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="0880a-184">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-184">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-185">Prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> je ukotven na pravé straně elementu <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="0880a-185">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="0880a-186">Nastavení viditelnosti</span><span class="sxs-lookup"><span data-stu-id="0880a-186">Setting Visibility</span></span>

<span data-ttu-id="0880a-187">Ovládací prvek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] můžete skrýt nebo ho sbalit nastavením vlastnosti <xref:System.Windows.UIElement.Visibility%2A> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="0880a-187">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="0880a-188">Když je ovládací prvek neviditelný, není zobrazený, ale zabírá prostor rozložení.</span><span class="sxs-lookup"><span data-stu-id="0880a-188">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="0880a-189">Když je ovládací prvek sbalen, není zobrazen, ani nevyužívá prostor rozložení.</span><span class="sxs-lookup"><span data-stu-id="0880a-189">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

<span data-ttu-id="0880a-190">Chcete-li nastavit viditelnost hostovaného ovládacího prvku, použijte následující postup:</span><span class="sxs-lookup"><span data-stu-id="0880a-190">To set the visibility of a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="0880a-191">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-191">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="0880a-192">V souboru *MainWindow. XAML. vb* nebo *MainWindow.XAML.cs*zkopírujte následující kód do definice třídy:</span><span class="sxs-lookup"><span data-stu-id="0880a-192">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="0880a-193">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-193">Press <kbd>F5</kbd> to build and run the application.</span></span>

4. <span data-ttu-id="0880a-194">Kliknutím na tlačítko **pro vytvoření neviditelného** tlačítka nastavíte prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> neviditelný.</span><span class="sxs-lookup"><span data-stu-id="0880a-194">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="0880a-195">Kliknutím na tlačítko **sbalit lze sbalit** skrýt prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> z rozložení zcela.</span><span class="sxs-lookup"><span data-stu-id="0880a-195">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="0880a-196">Když je ovládací prvek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sbalený, okolní prvky jsou přeuspořádány tak, aby zabíraly místo.</span><span class="sxs-lookup"><span data-stu-id="0880a-196">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="0880a-197">Hostování ovládacího prvku, který se roztáhne</span><span class="sxs-lookup"><span data-stu-id="0880a-197">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="0880a-198">Některé ovládací prvky [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mají pevnou velikost a nelze je roztáhnout, aby vyplnily dostupné místo v rozložení.</span><span class="sxs-lookup"><span data-stu-id="0880a-198">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="0880a-199">Například ovládací prvek <xref:System.Windows.Forms.MonthCalendar> zobrazuje měsíc v pevném prostoru.</span><span class="sxs-lookup"><span data-stu-id="0880a-199">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

<span data-ttu-id="0880a-200">Chcete-li hostovat ovládací prvek, který se nepřizpůsobuje, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="0880a-200">To host a control that does not stretch, follow these steps:</span></span>

1. <span data-ttu-id="0880a-201">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-201">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="0880a-202">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-202">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-203">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> je zarovnán na střed řádku gridu, ale není roztažen tak, aby vyplnil dostupné místo.</span><span class="sxs-lookup"><span data-stu-id="0880a-203">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="0880a-204">Pokud je okno dostatečně velké, může se zobrazit dva nebo více měsíců zobrazených v ovládacím prvku Hosted <xref:System.Windows.Forms.MonthCalendar>, ale jsou umístěny na střed na řádku.</span><span class="sxs-lookup"><span data-stu-id="0880a-204">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="0880a-205">Modul rozložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Centruje prvky, jejichž velikost nelze měnit, aby vyplnila dostupný prostor.</span><span class="sxs-lookup"><span data-stu-id="0880a-205">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="0880a-206">Změně</span><span class="sxs-lookup"><span data-stu-id="0880a-206">Scaling</span></span>

<span data-ttu-id="0880a-207">Na rozdíl od prvků WPF, většina model Windows Formsch ovládacích prvků není nepřetržitě škálovatelná.</span><span class="sxs-lookup"><span data-stu-id="0880a-207">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="0880a-208">Chcete-li zajistit vlastní škálování, přepište metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0880a-208">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0880a-209">Chcete-li škálovat hostovaný ovládací prvek pomocí výchozího chování, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="0880a-209">To scale a hosted control by using the default behavior, follow these steps:</span></span>

1. <span data-ttu-id="0880a-210">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-210">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="0880a-211">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-211">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-212">Hostovaný ovládací prvek a jeho okolní prvky se škálují podle faktoru 0,5.</span><span class="sxs-lookup"><span data-stu-id="0880a-212">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="0880a-213">Písmo hostovaného ovládacího prvku však není škálované.</span><span class="sxs-lookup"><span data-stu-id="0880a-213">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="0880a-214">Otočné</span><span class="sxs-lookup"><span data-stu-id="0880a-214">Rotating</span></span>

<span data-ttu-id="0880a-215">Na rozdíl od prvků WPF ovládací prvky model Windows Forms nepodporují otočení.</span><span class="sxs-lookup"><span data-stu-id="0880a-215">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="0880a-216">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> se při použití transformace rotace neotáčí s jinými prvky WPF.</span><span class="sxs-lookup"><span data-stu-id="0880a-216">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="0880a-217">Jakákoli hodnota rotace kromě 180 stupňů vyvolá událost <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.</span><span class="sxs-lookup"><span data-stu-id="0880a-217">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

<span data-ttu-id="0880a-218">Pokud chcete zobrazit efekt otočení v hybridní aplikaci, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="0880a-218">To see the effect of rotation in a hybrid application, follow these steps:</span></span>

1. <span data-ttu-id="0880a-219">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-219">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="0880a-220">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-220">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-221">Hostovaný ovládací prvek není otočen, ale jeho okolní prvky jsou otočeny o úhel 180 stupňů.</span><span class="sxs-lookup"><span data-stu-id="0880a-221">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="0880a-222">Možná budete muset změnit velikost okna, aby se zobrazily elementy.</span><span class="sxs-lookup"><span data-stu-id="0880a-222">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="0880a-223">Nastavení odsazení a okrajů</span><span class="sxs-lookup"><span data-stu-id="0880a-223">Setting Padding and Margins</span></span>

<span data-ttu-id="0880a-224">Odsazení a okraje v rozložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou podobné odsazení a okraje v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0880a-224">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="0880a-225">Jednoduše nastavte <xref:System.Windows.Controls.Control.Padding%2A> a vlastnosti <xref:System.Windows.FrameworkElement.Margin%2A> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="0880a-225">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

<span data-ttu-id="0880a-226">Chcete-li nastavit odsazení a okraje pro hostovaný ovládací prvek, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="0880a-226">To set padding and margins for a hosted control, follow these steps:</span></span>

1. <span data-ttu-id="0880a-227">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-227">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="0880a-228">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-228">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-229">Nastavení odsazení a okraj se aplikují na ovládací prvky hostovaného [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] stejným způsobem jako při použití v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0880a-229">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="0880a-230">Použití kontejnerů dynamického rozložení</span><span class="sxs-lookup"><span data-stu-id="0880a-230">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <span data-ttu-id="0880a-231">poskytuje dva kontejnery dynamického rozložení, <xref:System.Windows.Forms.FlowLayoutPanel> a <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="0880a-231">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="0880a-232">Tyto kontejnery můžete použít také v rozloženích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0880a-232">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

<span data-ttu-id="0880a-233">Chcete-li použít dynamický kontejner rozložení, použijte následující postup:</span><span class="sxs-lookup"><span data-stu-id="0880a-233">To use a dynamic layout container, follow these steps:</span></span>

1. <span data-ttu-id="0880a-234">Zkopírujte následující kód XAML do elementu <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="0880a-234">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element:</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="0880a-235">V souboru *MainWindow. XAML. vb* nebo *MainWindow.XAML.cs*zkopírujte následující kód do definice třídy:</span><span class="sxs-lookup"><span data-stu-id="0880a-235">In *MainWindow.xaml.vb* or *MainWindow.xaml.cs*, copy the following code into the class definition:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="0880a-236">Přidejte volání metody `InitializeFlowLayoutPanel` v konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="0880a-236">Add a call to the `InitializeFlowLayoutPanel` method in the constructor:</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="0880a-237">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0880a-237">Press <kbd>F5</kbd> to build and run the application.</span></span> <span data-ttu-id="0880a-238"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element vyplní <xref:System.Windows.Controls.DockPanel>a <xref:System.Windows.Forms.FlowLayoutPanel> uspořádá jeho podřízené ovládací prvky ve výchozím <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="0880a-238">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="0880a-239">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0880a-239">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="0880a-240">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0880a-240">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="0880a-241">Předpoklady rozložení pro element WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="0880a-241">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="0880a-242">Uspořádání ovládacích prvků model Windows Forms v ukázce WPF</span><span class="sxs-lookup"><span data-stu-id="0880a-242">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="0880a-243">Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="0880a-243">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="0880a-244">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0880a-244">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
