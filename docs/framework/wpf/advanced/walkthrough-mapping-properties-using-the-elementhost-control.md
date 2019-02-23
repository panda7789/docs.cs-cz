---
title: 'Průvodce: Mapování vlastností použitím ovládacího prvku ElementHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 29356f171506ece0fe35418f682681b19830d71c
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746335"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="5f27d-102">Průvodce: Mapování vlastností použitím ovládacího prvku ElementHost</span><span class="sxs-lookup"><span data-stu-id="5f27d-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>

<span data-ttu-id="5f27d-103">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> vlastnost mapovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti odpovídající vlastnosti na hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="5f27d-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>

<span data-ttu-id="5f27d-104">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="5f27d-104">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="5f27d-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="5f27d-105">Creating the project.</span></span>

-   <span data-ttu-id="5f27d-106">Definování nového mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="5f27d-106">Defining a new property mapping.</span></span>

-   <span data-ttu-id="5f27d-107">Odebrání výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="5f27d-107">Removing a default property mapping.</span></span>

-   <span data-ttu-id="5f27d-108">Rozšíření výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="5f27d-108">Extending a default property mapping.</span></span>

<span data-ttu-id="5f27d-109">Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [mapování vlastností použitím Ukázka ovládacího prvku ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="5f27d-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](https://go.microsoft.com/fwlink/?LinkID=160018).</span></span>

<span data-ttu-id="5f27d-110">Až budete hotovi, budete moci mapovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti k odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností hostované elementu.</span><span class="sxs-lookup"><span data-stu-id="5f27d-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5f27d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f27d-111">Prerequisites</span></span>

<span data-ttu-id="5f27d-112">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="5f27d-112">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="5f27d-113">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5f27d-113">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="5f27d-114">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="5f27d-114">Creating the Project</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="5f27d-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="5f27d-115">To create the project</span></span>

1.  <span data-ttu-id="5f27d-116">Vytvoření **aplikace Windows Forms** projekt s názvem `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="5f27d-116">Create a **Windows Forms App** project named `PropertyMappingWithElementHost`.</span></span>

2.  <span data-ttu-id="5f27d-117">V **Průzkumníka řešení**, přidejte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="5f27d-117">In **Solution Explorer**, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>

    -   <span data-ttu-id="5f27d-118">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="5f27d-118">PresentationCore</span></span>

    -   <span data-ttu-id="5f27d-119">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="5f27d-119">PresentationFramework</span></span>

    -   <span data-ttu-id="5f27d-120">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="5f27d-120">WindowsBase</span></span>

    -   <span data-ttu-id="5f27d-121">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="5f27d-121">WindowsFormsIntegration</span></span>

3.  <span data-ttu-id="5f27d-122">Zkopírujte následující kód do horní části `Form1` soubor kódu.</span><span class="sxs-lookup"><span data-stu-id="5f27d-122">Copy the following code into the top of the `Form1` code file.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4.  <span data-ttu-id="5f27d-123">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="5f27d-123">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="5f27d-124">Klikněte dvakrát na formuláři pro přidání obslužné rutiny události <xref:System.Windows.Forms.Form.Load> událostí.</span><span class="sxs-lookup"><span data-stu-id="5f27d-124">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>

5.  <span data-ttu-id="5f27d-125">Vraťte se do Návrháře formulářů Windows a přidejte obslužnou rutinu události pro daný formulář <xref:System.Windows.Forms.Control.Resize> událostí.</span><span class="sxs-lookup"><span data-stu-id="5f27d-125">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="5f27d-126">Další informace najdete v tématu [jak: Vytváření obslužných rutin událostí pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5f27d-126">For more information, see [How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span></span>

6.  <span data-ttu-id="5f27d-127">Deklarovat <xref:System.Windows.Forms.Integration.ElementHost> pole `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="5f27d-127">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a><span data-ttu-id="5f27d-128">Definování nového mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="5f27d-128">Defining New Property Mappings</span></span>

<span data-ttu-id="5f27d-129"><xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek obsahuje několik výchozích mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="5f27d-129">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="5f27d-130">Přidat nové mapování vlastností pomocí volání <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f27d-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-define-new-property-mappings"></a><span data-ttu-id="5f27d-131">Chcete-li definovat nové mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="5f27d-131">To define new property mappings</span></span>

1.  <span data-ttu-id="5f27d-132">Zkopírujte následující kód do definice pro `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="5f27d-132">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     <span data-ttu-id="5f27d-133">`AddMarginMapping` Metoda přidá nové mapování <xref:System.Windows.Forms.Control.Margin%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5f27d-133">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>

     <span data-ttu-id="5f27d-134">`OnMarginChange` Metoda překládá <xref:System.Windows.Forms.Control.Margin%2A> vlastnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5f27d-134">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>

2.  <span data-ttu-id="5f27d-135">Zkopírujte následující kód do definice pro `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="5f27d-135">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     <span data-ttu-id="5f27d-136">`AddRegionMapping` Metoda přidá nové mapování <xref:System.Windows.Forms.Control.Region%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5f27d-136">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="5f27d-137">`OnRegionChange` Metoda překládá <xref:System.Windows.Forms.Control.Region%2A> vlastnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5f27d-137">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="5f27d-138">`Form1_Resize` Obsluhovala formuláře <xref:System.Windows.Forms.Control.Resize> události a velikosti oblast ořezu podle hostovaný prvek.</span><span class="sxs-lookup"><span data-stu-id="5f27d-138">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="5f27d-139">Odebrání výchozí mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="5f27d-139">Removing a Default Property Mapping</span></span>

<span data-ttu-id="5f27d-140">Odeberte výchozí mapování vlastností pomocí volání <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodu <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f27d-140">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="5f27d-141">Chcete-li odebrat výchozí mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="5f27d-141">To remove a default property mapping</span></span>

-   <span data-ttu-id="5f27d-142">Zkopírujte následující kód do definice pro `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="5f27d-142">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     <span data-ttu-id="5f27d-143">`RemoveCursorMapping` Metoda odstraní výchozí mapování <xref:System.Windows.Forms.Control.Cursor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5f27d-143">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="5f27d-144">Rozšíření výchozí mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="5f27d-144">Extending a Default Property Mapping</span></span>

<span data-ttu-id="5f27d-145">Můžete použít výchozí mapování vlastností a také rozšířit o vlastní mapování.</span><span class="sxs-lookup"><span data-stu-id="5f27d-145">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="5f27d-146">Chcete-li rozšířit výchozí mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="5f27d-146">To extend a default property mapping</span></span>

-   <span data-ttu-id="5f27d-147">Zkopírujte následující kód do definice pro `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="5f27d-147">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     <span data-ttu-id="5f27d-148">`ExtendBackColorMapping` Metoda přidá převaděče vlastní vlastnost do existující <xref:System.Windows.Forms.Control.BackColor%2A> mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="5f27d-148">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>

     <span data-ttu-id="5f27d-149">`OnBackColorChange` Metoda přiřadí hostovaného ovládacího prvku konkrétní image <xref:System.Windows.Controls.Control.Background%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5f27d-149">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="5f27d-150">`OnBackColorChange` Metoda se volá, když se použije výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="5f27d-150">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>

## <a name="initialize-your-property-mappings"></a><span data-ttu-id="5f27d-151">Inicializovat mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="5f27d-151">Initialize your property mappings</span></span>

1.  <span data-ttu-id="5f27d-152">Zkopírujte následující kód do definice pro `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="5f27d-152">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     <span data-ttu-id="5f27d-153">`Form1_Load` Metoda obslužné rutiny <xref:System.Windows.Forms.Form.Load> událostí a provádí následující inicializace.</span><span class="sxs-lookup"><span data-stu-id="5f27d-153">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>

    -   <span data-ttu-id="5f27d-154">Vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> elementu.</span><span class="sxs-lookup"><span data-stu-id="5f27d-154">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>

    -   <span data-ttu-id="5f27d-155">Volá metody, které jste definovali dříve v návodu k nastavení mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="5f27d-155">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    -   <span data-ttu-id="5f27d-156">Přiřadí počáteční hodnoty pro mapovanou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5f27d-156">Assigns initial values to the mapped properties.</span></span>

2.  <span data-ttu-id="5f27d-157">Stisknutím klávesy F5 sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5f27d-157">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f27d-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f27d-158">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="5f27d-159">Mapování vlastnosti Windows Forms a WPF</span><span class="sxs-lookup"><span data-stu-id="5f27d-159">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="5f27d-160">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5f27d-160">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="5f27d-161">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5f27d-161">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)