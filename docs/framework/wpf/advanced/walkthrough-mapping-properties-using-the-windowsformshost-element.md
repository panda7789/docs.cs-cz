---
title: 'Návod: Mapování vlastností použitím elementu WindowsFormsHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: edd9d6f698ba27cacb5e9a5eecab43f58d47b8e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007113"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="20689-102">Návod: Mapování vlastností použitím elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="20689-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>

<span data-ttu-id="20689-103">Tento návod ukazuje, jak používat <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> vlastnost mapovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti odpovídající vlastnosti na hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="20689-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

<span data-ttu-id="20689-104">Úlohy v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="20689-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="20689-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="20689-105">Creating the project.</span></span>

- <span data-ttu-id="20689-106">Definování rozložení aplikace.</span><span class="sxs-lookup"><span data-stu-id="20689-106">Defining the application layout.</span></span>

- <span data-ttu-id="20689-107">Definování nového mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="20689-107">Defining a new property mapping.</span></span>

- <span data-ttu-id="20689-108">Odebrání výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="20689-108">Removing a default property mapping.</span></span>

- <span data-ttu-id="20689-109">Nahraďte výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="20689-109">Replacing a default property mapping.</span></span>

- <span data-ttu-id="20689-110">Rozšíření výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="20689-110">Extending a default property mapping.</span></span>

<span data-ttu-id="20689-111">Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [mapování vlastností použitím ukázka elementu WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="20689-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](https://go.microsoft.com/fwlink/?LinkID=160019).</span></span>

<span data-ttu-id="20689-112">Až budete hotovi, budete moci mapovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti odpovídající vlastnosti na hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="20689-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="20689-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20689-113">Prerequisites</span></span>

<span data-ttu-id="20689-114">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="20689-114">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="20689-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="20689-115">Visual Studio 2017</span></span>

## <a name="create-and-set-up-the-project"></a><span data-ttu-id="20689-116">Vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="20689-116">Create and set up the project</span></span>

1. <span data-ttu-id="20689-117">Vytvoření **aplikace WPF** projekt s názvem `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="20689-117">Create a **WPF App** project named `PropertyMappingWithWfhSample`.</span></span>

2. <span data-ttu-id="20689-118">V **Průzkumníka řešení**, přidejte odkaz na sestavení WindowsFormsIntegration, který se nazývá WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="20689-118">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="20689-119">V **Průzkumníka řešení**, přidejte odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="20689-119">In **Solution Explorer**, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="defining-the-application-layout"></a><span data-ttu-id="20689-120">Definování rozložení aplikace</span><span class="sxs-lookup"><span data-stu-id="20689-120">Defining the Application Layout</span></span>

<span data-ttu-id="20689-121">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– Na základě aplikace používá <xref:System.Windows.Forms.Integration.WindowsFormsHost> element na hostitele [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="20689-121">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-define-the-application-layout"></a><span data-ttu-id="20689-122">Pokud chcete definovat rozložení aplikace</span><span class="sxs-lookup"><span data-stu-id="20689-122">To define the application layout</span></span>

1. <span data-ttu-id="20689-123">Otevřete Window1.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20689-123">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

2. <span data-ttu-id="20689-124">Nahraďte stávající kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="20689-124">Replace the existing code with the following code.</span></span>

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. <span data-ttu-id="20689-125">Otevřete Window1.xaml.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="20689-125">Open Window1.xaml.cs in the Code Editor.</span></span>

4. <span data-ttu-id="20689-126">V horní části souboru importujte následující obory názvů.</span><span class="sxs-lookup"><span data-stu-id="20689-126">At the top of the file, import the following namespaces.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="20689-127">Definování nového mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="20689-127">Defining a New Property Mapping</span></span>

<span data-ttu-id="20689-128"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element poskytuje několik výchozích mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="20689-128">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="20689-129">Přidat nové mapování vlastností pomocí volání <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="20689-129">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="20689-130">Chcete-li definovat nové mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="20689-130">To define a new property mapping</span></span>

- <span data-ttu-id="20689-131">Zkopírujte následující kód do definice pro `Window1` třídy.</span><span class="sxs-lookup"><span data-stu-id="20689-131">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     <span data-ttu-id="20689-132">`AddClipMapping` Metoda přidá nové mapování <xref:System.Windows.UIElement.Clip%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="20689-132">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="20689-133">`OnClipChange` Metoda překládá <xref:System.Windows.UIElement.Clip%2A> vlastnost [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="20689-133">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="20689-134">`Window1_SizeChanged` Obsluhovala v okně <xref:System.Windows.FrameworkElement.SizeChanged> události a velikosti oblast ořezu podle okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="20689-134">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="20689-135">Odebrání výchozí mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="20689-135">Removing a Default Property Mapping</span></span>

<span data-ttu-id="20689-136">Odebrání výchozí mapování vlastností pomocí volání <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodu na <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="20689-136">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="20689-137">Chcete-li odebrat výchozí mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="20689-137">To remove a default property mapping</span></span>

- <span data-ttu-id="20689-138">Zkopírujte následující kód do definice pro `Window1` třídy.</span><span class="sxs-lookup"><span data-stu-id="20689-138">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     <span data-ttu-id="20689-139">`RemoveCursorMapping` Metoda odstraní výchozí mapování <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="20689-139">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>

## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="20689-140">Nahraďte výchozí mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="20689-140">Replacing a Default Property Mapping</span></span>

<span data-ttu-id="20689-141">Nahraďte výchozí mapování vlastnosti tak, že odeberete výchozí mapování a volání <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="20689-141">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="20689-142">Chcete-li nahradit výchozí mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="20689-142">To replace a default property mapping</span></span>

- <span data-ttu-id="20689-143">Zkopírujte následující kód do definice pro `Window1` třídy.</span><span class="sxs-lookup"><span data-stu-id="20689-143">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     <span data-ttu-id="20689-144">`ReplaceFlowDirectionMapping` Metoda nahradí výchozí mapování <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="20689-144">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>

     <span data-ttu-id="20689-145">`OnFlowDirectionChange` Metoda překládá <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="20689-145">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>

     <span data-ttu-id="20689-146">`cb_CheckedChanged` Metoda obslužné rutiny <xref:System.Windows.Forms.CheckBox.CheckedChanged> událostí na <xref:System.Windows.Forms.CheckBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="20689-146">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="20689-147">Přiřazuje <xref:System.Windows.FrameworkElement.FlowDirection%2A> nastavenou na hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnost</span><span class="sxs-lookup"><span data-stu-id="20689-147">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="20689-148">Rozšíření výchozí mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="20689-148">Extending a Default Property Mapping</span></span>

<span data-ttu-id="20689-149">Můžete použít výchozí mapování vlastností a také rozšířit o vlastní mapování.</span><span class="sxs-lookup"><span data-stu-id="20689-149">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="20689-150">Chcete-li rozšířit výchozí mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="20689-150">To extend a default property mapping</span></span>

- <span data-ttu-id="20689-151">Zkopírujte následující kód do definice pro `Window1` třídy.</span><span class="sxs-lookup"><span data-stu-id="20689-151">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     <span data-ttu-id="20689-152">`ExtendBackgroundMapping` Metoda přidá převaděče vlastní vlastnost do existující <xref:System.Windows.Controls.Control.Background%2A> mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="20689-152">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>

     <span data-ttu-id="20689-153">`OnBackgroundChange` Metoda přiřadí hostovaného ovládacího prvku konkrétní image <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="20689-153">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="20689-154">`OnBackgroundChange` Metoda se volá, když se použije výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="20689-154">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>

## <a name="initializing-your-property-mappings"></a><span data-ttu-id="20689-155">Inicializuje se mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="20689-155">Initializing Your Property Mappings</span></span>

<span data-ttu-id="20689-156">Nastavení mapování vlastností pomocí volání metody bylo popsáno dříve <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="20689-156">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="20689-157">Inicializace mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="20689-157">To initialize your property mappings</span></span>

1. <span data-ttu-id="20689-158">Zkopírujte následující kód do definice pro `Window1` třídy.</span><span class="sxs-lookup"><span data-stu-id="20689-158">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     <span data-ttu-id="20689-159">`WindowLoaded` Metoda obslužné rutiny <xref:System.Windows.FrameworkElement.Loaded> událostí a provádí následující inicializace.</span><span class="sxs-lookup"><span data-stu-id="20689-159">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>

    - <span data-ttu-id="20689-160">Vytvoří [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="20689-160">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>

    - <span data-ttu-id="20689-161">Volá metody, které jste definovali dříve v návodu k nastavení mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="20689-161">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="20689-162">Přiřadí počáteční hodnoty pro mapovanou vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="20689-162">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="20689-163">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="20689-163">Press **F5** to build and run the application.</span></span> <span data-ttu-id="20689-164">Klikněte na zaškrtávací políčko na vliv <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapování.</span><span class="sxs-lookup"><span data-stu-id="20689-164">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="20689-165">Po kliknutí na zaškrtávací políčko obrátí rozložení zleva doprava orientace.</span><span class="sxs-lookup"><span data-stu-id="20689-165">When you click the check box, the layout reverses its left-right orientation.</span></span>

## <a name="see-also"></a><span data-ttu-id="20689-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20689-166">See also</span></span>

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="20689-167">Mapování vlastnosti Windows Forms a WPF</span><span class="sxs-lookup"><span data-stu-id="20689-167">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="20689-168">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="20689-168">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="20689-169">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="20689-169">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)