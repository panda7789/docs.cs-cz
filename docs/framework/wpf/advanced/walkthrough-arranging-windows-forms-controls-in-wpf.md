---
title: 'Návod: Uspořádání ovládacích prvků Windows Forms ve WPF'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972308"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a><span data-ttu-id="3b1a0-102">Návod: Uspořádání ovládacích prvků Windows Forms ve WPF</span><span class="sxs-lookup"><span data-stu-id="3b1a0-102">Walkthrough: Arranging Windows Forms Controls in WPF</span></span>

<span data-ttu-id="3b1a0-103">V tomto návodu se dozvíte, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jak používat funkce rozložení [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] k uspořádání ovládacích prvků v hybridní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-103">This walkthrough shows you how to use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout features to arrange [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in a hybrid application.</span></span>

<span data-ttu-id="3b1a0-104">Úlohy, které jsou znázorněné v tomto návodu, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="3b1a0-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="3b1a0-105">Vytváří se projekt.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-105">Creating the project.</span></span>

- <span data-ttu-id="3b1a0-106">Používá se výchozí nastavení rozložení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-106">Using default layout settings.</span></span>

- <span data-ttu-id="3b1a0-107">Změna velikosti obsahu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-107">Sizing to content.</span></span>

- <span data-ttu-id="3b1a0-108">Použití absolutního umístění.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-108">Using absolute positioning.</span></span>

- <span data-ttu-id="3b1a0-109">Explicitní určení velikosti</span><span class="sxs-lookup"><span data-stu-id="3b1a0-109">Specifying size explicitly.</span></span>

- <span data-ttu-id="3b1a0-110">Nastavení vlastností rozložení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-110">Setting layout properties.</span></span>

- <span data-ttu-id="3b1a0-111">Porozumění omezením pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-111">Understanding z-order limitations.</span></span>

- <span data-ttu-id="3b1a0-112">Ukotvení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-112">Docking.</span></span>

- <span data-ttu-id="3b1a0-113">Nastavení viditelnosti.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-113">Setting visibility.</span></span>

- <span data-ttu-id="3b1a0-114">Hostování ovládacího prvku, který se nepřizpůsobuje.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-114">Hosting a control that does not stretch.</span></span>

- <span data-ttu-id="3b1a0-115">Změně.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-115">Scaling.</span></span>

- <span data-ttu-id="3b1a0-116">Otočné.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-116">Rotating.</span></span>

- <span data-ttu-id="3b1a0-117">Nastavení odsazení a okrajů</span><span class="sxs-lookup"><span data-stu-id="3b1a0-117">Setting padding and margins.</span></span>

- <span data-ttu-id="3b1a0-118">Použití kontejnerů dynamického rozložení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-118">Using dynamic layout containers.</span></span>

<span data-ttu-id="3b1a0-119">Úplný výpis kódu úloh, které jsou znázorněny v tomto návodu, naleznete v tématu [uspořádání model Windows Formsch ovládacích prvků v UKÁZCE WPF](https://go.microsoft.com/fwlink/?LinkID=159971).</span><span class="sxs-lookup"><span data-stu-id="3b1a0-119">For a complete code listing of the tasks illustrated in this walkthrough, see [Arranging Windows Forms Controls in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159971).</span></span>

<span data-ttu-id="3b1a0-120">Až budete hotovi, budete mít přehled o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] funkcích rozložení v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacích založených na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-120">When you are finished, you will have an understanding of [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] layout features in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3b1a0-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b1a0-121">Prerequisites</span></span>

<span data-ttu-id="3b1a0-122">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-122">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="3b1a0-123">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="3b1a0-123">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="3b1a0-124">Vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="3b1a0-124">To create and set up the project</span></span>

1. <span data-ttu-id="3b1a0-125">Vytvořte projekt aplikace WPF s názvem `WpfLayoutHostingWf`.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-125">Create a WPF Application project named `WpfLayoutHostingWf`.</span></span>

2. <span data-ttu-id="3b1a0-126">V Průzkumník řešení přidejte odkazy na následující sestavení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-126">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="3b1a0-127">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="3b1a0-127">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="3b1a0-128">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="3b1a0-128">System.Windows.Forms</span></span>

    - <span data-ttu-id="3b1a0-129">System. Drawing</span><span class="sxs-lookup"><span data-stu-id="3b1a0-129">System.Drawing</span></span>

3. <span data-ttu-id="3b1a0-130">Poklikejte na MainWindow. XAML a otevře se v zobrazení XAML.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-130">Double-click MainWindow.xaml to open it in XAML view.</span></span>

4. <span data-ttu-id="3b1a0-131">V elementu přidejte následující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mapování oboru názvů. <xref:System.Windows.Window></span><span class="sxs-lookup"><span data-stu-id="3b1a0-131">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespace mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="3b1a0-132">V elementu nastavte vlastnost na `true` a definujte pět řádků a tři sloupce. <xref:System.Windows.Controls.Grid.ShowGridLines%2A> <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="3b1a0-132">In the <xref:System.Windows.Controls.Grid> element set the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property to `true` and define five rows and three columns.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a><span data-ttu-id="3b1a0-133">Použití výchozího nastavení rozložení</span><span class="sxs-lookup"><span data-stu-id="3b1a0-133">Using Default Layout Settings</span></span>

<span data-ttu-id="3b1a0-134">Ve výchozím nastavení <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek zpracovává rozložení pro hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-134">By default, the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element handles the layout for the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-use-default-layout-settings"></a><span data-ttu-id="3b1a0-135">Použití výchozího nastavení rozložení</span><span class="sxs-lookup"><span data-stu-id="3b1a0-135">To use default layout settings</span></span>

1. <span data-ttu-id="3b1a0-136">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-136">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. <span data-ttu-id="3b1a0-137">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-137">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-138">Ovládací prvek se zobrazí v <xref:System.Windows.Controls.Canvas>. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3b1a0-138">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Button?displayProperty=nameWithType> control appears in the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="3b1a0-139">Hostovaný ovládací prvek má velikost na základě jeho obsahu a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element má velikost pro přizpůsobení hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-139">The hosted control is sized based on its content, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is sized to accommodate the hosted control.</span></span>

## <a name="sizing-to-content"></a><span data-ttu-id="3b1a0-140">Změna velikosti obsahu</span><span class="sxs-lookup"><span data-stu-id="3b1a0-140">Sizing to Content</span></span>

<span data-ttu-id="3b1a0-141"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek zajistí, že hostovaný ovládací prvek má velikost pro správné zobrazení obsahu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-141">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element ensures that the hosted control is sized to display its content properly.</span></span>

### <a name="to-size-to-content"></a><span data-ttu-id="3b1a0-142">Chcete-li nastavit velikost obsahu</span><span class="sxs-lookup"><span data-stu-id="3b1a0-142">To size to content</span></span>

1. <span data-ttu-id="3b1a0-143">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-143">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. <span data-ttu-id="3b1a0-144">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-144">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-145">Dva nové ovládací prvky tlačítka mají velikost pro zobrazení delšího textového řetězce a větší velikosti písma a <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky jsou změněna tak, aby vyhovovaly hostovaným ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-145">The two new button controls are sized to display the longer text string and larger font size properly, and the <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are resized to accommodate the hosted controls.</span></span>

## <a name="using-absolute-positioning"></a><span data-ttu-id="3b1a0-146">Použití absolutního umístění</span><span class="sxs-lookup"><span data-stu-id="3b1a0-146">Using Absolute Positioning</span></span>

<span data-ttu-id="3b1a0-147">Absolutní umístění lze použít k umístění <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu kdekoli v uživatelském rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="3b1a0-147">You can use absolute positioning to place the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element anywhere in the user interface (UI).</span></span>

### <a name="to-use-absolute-positioning"></a><span data-ttu-id="3b1a0-148">Použití absolutního umístění</span><span class="sxs-lookup"><span data-stu-id="3b1a0-148">To use absolute positioning</span></span>

1. <span data-ttu-id="3b1a0-149">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-149">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. <span data-ttu-id="3b1a0-150">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-150">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-151"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je umístěn 20 pixelů od horní strany buňky mřížky a 20 pixelů zleva.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-151">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is placed 20 pixels from the top side of the grid cell and 20 pixels from the left.</span></span>

## <a name="specifying-size-explicitly"></a><span data-ttu-id="3b1a0-152">Explicitní určení velikosti</span><span class="sxs-lookup"><span data-stu-id="3b1a0-152">Specifying Size Explicitly</span></span>

<span data-ttu-id="3b1a0-153">Můžete určit velikost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.FrameworkElement.Width%2A> pomocí vlastností a <xref:System.Windows.FrameworkElement.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="3b1a0-153">You can specify the size of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element using the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span>

### <a name="to-specify-size-explicitly"></a><span data-ttu-id="3b1a0-154">Explicitní určení velikosti</span><span class="sxs-lookup"><span data-stu-id="3b1a0-154">To specify size explicitly</span></span>

1. <span data-ttu-id="3b1a0-155">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-155">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. <span data-ttu-id="3b1a0-156">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-156">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-157"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je nastaven na velikost 50 pixelů v šířce až 70 pixelů vysoké, což je menší než výchozí nastavení rozložení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-157">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is set to a size of 50 pixels wide by 70 pixels high, which is smaller than the default layout settings.</span></span> <span data-ttu-id="3b1a0-158">Obsah [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku se odpovídajícím způsobem změní.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-158">The content of the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is rearranged accordingly.</span></span>

## <a name="setting-layout-properties"></a><span data-ttu-id="3b1a0-159">Nastavení vlastností rozložení</span><span class="sxs-lookup"><span data-stu-id="3b1a0-159">Setting Layout Properties</span></span>

<span data-ttu-id="3b1a0-160">V hostovaném ovládacím prvku vždy nastavte vlastnosti související s rozložením pomocí vlastností <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-160">Always set layout-related properties on the hosted control by using the properties of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="3b1a0-161">Nastavení vlastností rozložení přímo v hostovaném ovládacím prvku bude vracet neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-161">Setting layout properties directly on the hosted control will yield unintended results.</span></span>

 <span data-ttu-id="3b1a0-162">Nastavení vlastností souvisejících s rozložením v hostovaném ovládacím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvku v nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-162">Setting layout-related properties on the hosted control in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] has no effect.</span></span>

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a><span data-ttu-id="3b1a0-163">Postup zobrazení efektů nastavení vlastností u hostovaného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="3b1a0-163">To see the effects of setting properties on the hosted control</span></span>

1. <span data-ttu-id="3b1a0-164">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-164">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. <span data-ttu-id="3b1a0-165">V Průzkumník řešení dvakrát klikněte na MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-165">In Solution Explorer, double-click MainWindow.xaml.</span></span> <span data-ttu-id="3b1a0-166">vb nebo MainWindow.xaml.cs jej otevřete v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-166">vb or MainWindow.xaml.cs to open it in the Code Editor.</span></span>

3. <span data-ttu-id="3b1a0-167">Zkopírujte následující kód do `MainWindow` definice třídy.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-167">Copy the following code into the `MainWindow` class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. <span data-ttu-id="3b1a0-168">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-168">Press F5 to build and run the application.</span></span>

5. <span data-ttu-id="3b1a0-169">Klikněte na tlačítko **klepnutím na tlačítko** .</span><span class="sxs-lookup"><span data-stu-id="3b1a0-169">Click the **Click me** button.</span></span> <span data-ttu-id="3b1a0-170">Obslužná rutina <xref:System.Windows.Forms.Control.Top%2A>událostinastaví vlastnosti <xref:System.Windows.Forms.Control.Left%2A> a u hostovaného ovládacího prvku. `button1_Click`</span><span class="sxs-lookup"><span data-stu-id="3b1a0-170">The `button1_Click` event handler sets the <xref:System.Windows.Forms.Control.Top%2A> and <xref:System.Windows.Forms.Control.Left%2A> properties on the hosted control.</span></span> <span data-ttu-id="3b1a0-171">Tím dojde k přemístění hostovaného ovládacího prvku v rámci <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-171">This causes the hosted control to be repositioned within the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="3b1a0-172">Hostitel udržuje stejnou oblast obrazovky, ale hostovaný ovládací prvek je oříznutý.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-172">The host maintains the same screen area, but the hosted control is clipped.</span></span> <span data-ttu-id="3b1a0-173">Místo toho by měl hostovaný ovládací prvek vždy vyplnit <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-173">Instead, the hosted control should always fill the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

## <a name="understanding-z-order-limitations"></a><span data-ttu-id="3b1a0-174">Porozumění omezením pořadí vykreslování</span><span class="sxs-lookup"><span data-stu-id="3b1a0-174">Understanding Z-Order Limitations</span></span>

<span data-ttu-id="3b1a0-175">Viditelné <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvky jsou vždy vykresleny nad ostatními prvky WPF a nejsou ovlivněny pořadím z.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-175">Visible <xref:System.Windows.Forms.Integration.WindowsFormsHost> elements are always drawn on top of other WPF elements, and they are unaffected by z-order.</span></span> <span data-ttu-id="3b1a0-176">Chcete-li zobrazit toto chování z pořadí vykreslování, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="3b1a0-176">To see this z-order behavior, do the following:</span></span>

1. <span data-ttu-id="3b1a0-177">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-177">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. <span data-ttu-id="3b1a0-178">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-178">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-179"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Prvek je vykreslen nad prvkem popisku.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-179">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is painted over the label element.</span></span>

## <a name="docking"></a><span data-ttu-id="3b1a0-180">Ukotvení</span><span class="sxs-lookup"><span data-stu-id="3b1a0-180">Docking</span></span>

<span data-ttu-id="3b1a0-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost>prvek podporuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ukotvení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-181"><xref:System.Windows.Forms.Integration.WindowsFormsHost> element supports [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] docking.</span></span> <span data-ttu-id="3b1a0-182">Nastavte připojenou vlastnost pro ukotvení hostovaného ovládacího prvku <xref:System.Windows.Controls.DockPanel> v elementu. <xref:System.Windows.Controls.DockPanel.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="3b1a0-182">Set the <xref:System.Windows.Controls.DockPanel.Dock%2A> attached property to dock the hosted control in a <xref:System.Windows.Controls.DockPanel> element.</span></span>

### <a name="to-dock-a-hosted-control"></a><span data-ttu-id="3b1a0-183">Ukotvení hostovaného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="3b1a0-183">To dock a hosted control</span></span>

1. <span data-ttu-id="3b1a0-184">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-184">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. <span data-ttu-id="3b1a0-185">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-185">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-186">Prvek je ukotven na pravé straně <xref:System.Windows.Controls.DockPanel> elementu. <xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="3b1a0-186">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is docked to the right side of the <xref:System.Windows.Controls.DockPanel> element.</span></span>

## <a name="setting-visibility"></a><span data-ttu-id="3b1a0-187">Nastavení viditelnosti</span><span class="sxs-lookup"><span data-stu-id="3b1a0-187">Setting Visibility</span></span>

<span data-ttu-id="3b1a0-188">Můžete nastavit, aby [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] byl ovládací prvek neviditelný nebo sbalen, <xref:System.Windows.UIElement.Visibility%2A> nastavením vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvku.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-188">You can make your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control invisible or collapse it by setting the <xref:System.Windows.UIElement.Visibility%2A> property on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span> <span data-ttu-id="3b1a0-189">Když je ovládací prvek neviditelný, není zobrazený, ale zabírá prostor rozložení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-189">When a control is invisible, it is not displayed, but it occupies layout space.</span></span> <span data-ttu-id="3b1a0-190">Když je ovládací prvek sbalen, není zobrazen, ani nevyužívá prostor rozložení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-190">When a control is collapsed, it is not displayed, nor does it occupy layout space.</span></span>

### <a name="to-set-the-visibility-of-a-hosted-control"></a><span data-ttu-id="3b1a0-191">Nastavení viditelnosti hostovaného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="3b1a0-191">To set the visibility of a hosted control</span></span>

1. <span data-ttu-id="3b1a0-192">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-192">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. <span data-ttu-id="3b1a0-193">V souboru MainWindow. XAML. vb nebo MainWindow.xaml.cs zkopírujte následující kód do definice třídy.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-193">In MainWindow.xaml.vb or MainWindow.xaml.cs, copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. <span data-ttu-id="3b1a0-194">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-194">Press F5 to build and run the application.</span></span>

4. <span data-ttu-id="3b1a0-195">Klikněte na tlačítko **kliknutím a vytvořte neviditelné** tlačítko, <xref:System.Windows.Forms.Integration.WindowsFormsHost> aby se element neviditelní.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-195">Click the **Click to make invisible** button to make the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element invisible.</span></span>

5. <span data-ttu-id="3b1a0-196">Kliknutím na tlačítko **sbalit pro sbalení** zcela skryjete <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek z rozložení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-196">Click the **Click to collapse** button to hide the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element from the layout entirely.</span></span> <span data-ttu-id="3b1a0-197">Když je [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek sbalen, okolní prvky jsou přeuspořádány tak, aby zabíraly místo.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-197">When the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is collapsed, the surrounding elements are rearranged to occupy its space.</span></span>

## <a name="hosting-a-control-that-does-not-stretch"></a><span data-ttu-id="3b1a0-198">Hostování ovládacího prvku, který se roztáhne</span><span class="sxs-lookup"><span data-stu-id="3b1a0-198">Hosting a Control That Does Not Stretch</span></span>

<span data-ttu-id="3b1a0-199">Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky mají pevnou velikost a nelze je roztáhnout, aby vyplnily dostupné místo v rozložení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-199">Some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have a fixed size and do not stretch to fill available space in the layout.</span></span> <span data-ttu-id="3b1a0-200">Například <xref:System.Windows.Forms.MonthCalendar> ovládací prvek zobrazuje měsíc v pevném prostoru.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-200">For example, the <xref:System.Windows.Forms.MonthCalendar> control displays a month in a fixed space.</span></span>

### <a name="to-host-a-control-that-does-not-stretch"></a><span data-ttu-id="3b1a0-201">Hostování ovládacího prvku, který se roztáhne</span><span class="sxs-lookup"><span data-stu-id="3b1a0-201">To host a control that does not stretch</span></span>

1. <span data-ttu-id="3b1a0-202">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-202">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. <span data-ttu-id="3b1a0-203">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-203">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-204"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element je zarovnán na střed řádku mřížky, ale není roztažen tak, aby vyplnil dostupné místo.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-204">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element is centered in the grid row, but it is not stretched to fill the available space.</span></span> <span data-ttu-id="3b1a0-205">Pokud je okno dostatečně velké, může se zobrazit dva nebo více měsíců zobrazených v hostovaném <xref:System.Windows.Forms.MonthCalendar> ovládacím prvku, ale tyto řádky jsou zarovnány na střed.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-205">If the window is large enough, you may see two or more months displayed by the hosted <xref:System.Windows.Forms.MonthCalendar> control, but these are centered in the row.</span></span> <span data-ttu-id="3b1a0-206">Modul [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení vycentruje prvky, jejichž velikost nelze měnit, aby vyplnila dostupný prostor.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-206">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout engine centers elements that cannot be sized to fill the available space.</span></span>

## <a name="scaling"></a><span data-ttu-id="3b1a0-207">Škálování</span><span class="sxs-lookup"><span data-stu-id="3b1a0-207">Scaling</span></span>

<span data-ttu-id="3b1a0-208">Na rozdíl od prvků WPF, většina model Windows Formsch ovládacích prvků není nepřetržitě škálovatelná.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-208">Unlike WPF elements, most Windows Forms controls are not continuously scalable.</span></span> <span data-ttu-id="3b1a0-209">Chcete-li zajistit vlastní škálování, přepište <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-209">To provide custom scaling, you override the <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> method.</span></span>

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a><span data-ttu-id="3b1a0-210">Škálování hostovaného ovládacího prvku pomocí výchozího chování</span><span class="sxs-lookup"><span data-stu-id="3b1a0-210">To scale a hosted control by using the default behavior</span></span>

1. <span data-ttu-id="3b1a0-211">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-211">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. <span data-ttu-id="3b1a0-212">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-212">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-213">Hostovaný ovládací prvek a jeho okolní prvky se škálují podle faktoru 0,5.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-213">The hosted control and its surrounding elements are scaled by a factor of 0.5.</span></span> <span data-ttu-id="3b1a0-214">Písmo hostovaného ovládacího prvku však není škálované.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-214">However, the hosted control's font is not scaled.</span></span>

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a><span data-ttu-id="3b1a0-215">Otočné</span><span class="sxs-lookup"><span data-stu-id="3b1a0-215">Rotating</span></span>

<span data-ttu-id="3b1a0-216">Na rozdíl od prvků WPF ovládací prvky model Windows Forms nepodporují otočení.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-216">Unlike WPF elements, Windows Forms controls do not support rotation.</span></span> <span data-ttu-id="3b1a0-217"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element se při použití transformace rotace neotáčí s jinými prvky WPF.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-217">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element does not rotate with other WPF elements when a rotation transformation is applied.</span></span> <span data-ttu-id="3b1a0-218">Jakákoli hodnota rotace s <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> výjimkou 180 stupňů vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-218">Any rotation value other than 180 degrees raises the <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> event.</span></span>

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a><span data-ttu-id="3b1a0-219">Zobrazení efektu rotace v hybridní aplikaci</span><span class="sxs-lookup"><span data-stu-id="3b1a0-219">To see the effect of rotation in a hybrid application</span></span>

1. <span data-ttu-id="3b1a0-220">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-220">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. <span data-ttu-id="3b1a0-221">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-221">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-222">Hostovaný ovládací prvek není otočen, ale jeho okolní prvky jsou otočeny o úhel 180 stupňů.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-222">The hosted control is not rotated, but its surrounding elements are rotated by an angle of 180 degrees.</span></span> <span data-ttu-id="3b1a0-223">Možná budete muset změnit velikost okna, aby se zobrazily elementy.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-223">You may have to resize the window to see the elements.</span></span>

## <a name="setting-padding-and-margins"></a><span data-ttu-id="3b1a0-224">Nastavení odsazení a okrajů</span><span class="sxs-lookup"><span data-stu-id="3b1a0-224">Setting Padding and Margins</span></span>

<span data-ttu-id="3b1a0-225">Odsazení a okraje v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení se podobají odsazení a okrajům v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b1a0-225">Padding and margins in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout are similar to padding and margins in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="3b1a0-226">Jednoduše nastavte <xref:System.Windows.Controls.Control.Padding%2A> vlastnosti a <xref:System.Windows.FrameworkElement.Margin%2A> u <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvku.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-226">Simply set the <xref:System.Windows.Controls.Control.Padding%2A> and <xref:System.Windows.FrameworkElement.Margin%2A> properties on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element.</span></span>

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a><span data-ttu-id="3b1a0-227">Nastavení odsazení a okrajů pro hostovaný ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="3b1a0-227">To set padding and margins for a hosted control</span></span>

1. <span data-ttu-id="3b1a0-228">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-228">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. <span data-ttu-id="3b1a0-229">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-229">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-230">Nastavení odsazení a okraj se aplikují na hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky stejným způsobem jako při použití v. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b1a0-230">The padding and margin settings are applied to the hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls in the same way they would be applied in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

## <a name="using-dynamic-layout-containers"></a><span data-ttu-id="3b1a0-231">Použití kontejnerů dynamického rozložení</span><span class="sxs-lookup"><span data-stu-id="3b1a0-231">Using Dynamic Layout Containers</span></span>

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<span data-ttu-id="3b1a0-232">poskytuje dva kontejnery <xref:System.Windows.Forms.FlowLayoutPanel> dynamického rozložení a <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-232">provides two dynamic layout containers, <xref:System.Windows.Forms.FlowLayoutPanel> and <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="3b1a0-233">Tyto kontejnery můžete také použít v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozloženích.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-233">You can also use these containers in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layouts.</span></span>

### <a name="to-use-a-dynamic-layout-container"></a><span data-ttu-id="3b1a0-234">Použití dynamického kontejneru rozložení</span><span class="sxs-lookup"><span data-stu-id="3b1a0-234">To use a dynamic layout container</span></span>

1. <span data-ttu-id="3b1a0-235">Zkopírujte následující kód XAML do <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-235">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element.</span></span>

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. <span data-ttu-id="3b1a0-236">V souboru MainWindow. XAML. vb nebo MainWindow.xaml.cs zkopírujte následující kód do definice třídy.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-236">In MainWindow.xaml.vb or MainWindow.xaml.cs copy the following code into the class definition.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. <span data-ttu-id="3b1a0-237">Přidejte volání `InitializeFlowLayoutPanel` metody v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-237">Add a call to the `InitializeFlowLayoutPanel` method in the constructor.</span></span>

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. <span data-ttu-id="3b1a0-238">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b1a0-238">Press F5 to build and run the application.</span></span> <span data-ttu-id="3b1a0-239">Element vyplní a uspořádá<xref:System.Windows.Forms.FlowLayoutPanel> své podřízené ovládací prvky ve výchozím nastavení <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>. <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Controls.DockPanel></span><span class="sxs-lookup"><span data-stu-id="3b1a0-239">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element fills the <xref:System.Windows.Controls.DockPanel>, and <xref:System.Windows.Forms.FlowLayoutPanel> arranges its child controls in the default <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b1a0-240">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b1a0-240">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="3b1a0-241">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b1a0-241">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="3b1a0-242">Předpoklady rozložení pro element WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="3b1a0-242">Layout Considerations for the WindowsFormsHost Element</span></span>](layout-considerations-for-the-windowsformshost-element.md)
- [<span data-ttu-id="3b1a0-243">Uspořádání ovládacích prvků model Windows Forms v ukázce WPF</span><span class="sxs-lookup"><span data-stu-id="3b1a0-243">Arranging Windows Forms Controls in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159971)
- [<span data-ttu-id="3b1a0-244">Návod: Hostování model Windows Forms složeného ovládacího prvku v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="3b1a0-244">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="3b1a0-245">Návod: Hostování složeného ovládacího prvku WPF v model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b1a0-245">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
