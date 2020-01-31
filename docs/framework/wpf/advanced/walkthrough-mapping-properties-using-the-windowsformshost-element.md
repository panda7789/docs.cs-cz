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
ms.openlocfilehash: c076937d6431adf1750793d47ece88dc82edf95c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794105"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="ae83b-102">Návod: Mapování vlastností použitím elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="ae83b-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>

<span data-ttu-id="ae83b-103">Tento návod ukazuje, jak použít vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> k mapování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností na odpovídající vlastnosti v hostovaném ovládacím prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ae83b-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted Windows Forms control.</span></span>

<span data-ttu-id="ae83b-104">Úlohy, které jsou znázorněné v tomto návodu, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="ae83b-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="ae83b-105">Vytváří se projekt.</span><span class="sxs-lookup"><span data-stu-id="ae83b-105">Creating the project.</span></span>

- <span data-ttu-id="ae83b-106">Definování rozložení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae83b-106">Defining the application layout.</span></span>

- <span data-ttu-id="ae83b-107">Definování nového mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="ae83b-107">Defining a new property mapping.</span></span>

- <span data-ttu-id="ae83b-108">Odebírá se výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="ae83b-108">Removing a default property mapping.</span></span>

- <span data-ttu-id="ae83b-109">Nahrazuje se výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="ae83b-109">Replacing a default property mapping.</span></span>

- <span data-ttu-id="ae83b-110">Rozšíření výchozího mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="ae83b-110">Extending a default property mapping.</span></span>

<span data-ttu-id="ae83b-111">Úplný výpis kódu úloh, které jsou znázorněny v tomto návodu, najdete v tématu [mapování vlastností pomocí ukázky elementu WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="ae83b-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](https://go.microsoft.com/fwlink/?LinkID=160019).</span></span>

<span data-ttu-id="ae83b-112">Až budete hotovi, budete moci mapovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti na odpovídající vlastnosti v hostovaném ovládacím prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ae83b-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted Windows Forms control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ae83b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae83b-113">Prerequisites</span></span>

<span data-ttu-id="ae83b-114">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="ae83b-114">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="ae83b-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ae83b-115">Visual Studio 2017</span></span>

## <a name="create-and-set-up-the-project"></a><span data-ttu-id="ae83b-116">Vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="ae83b-116">Create and set up the project</span></span>

1. <span data-ttu-id="ae83b-117">Vytvořte projekt **aplikace WPF** s názvem `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="ae83b-117">Create a **WPF App** project named `PropertyMappingWithWfhSample`.</span></span>

2. <span data-ttu-id="ae83b-118">V **Průzkumník řešení**přidejte odkaz na sestavení WindowsFormsIntegration, které má název WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="ae83b-118">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="ae83b-119">V **Průzkumník řešení**přidejte odkazy na sestavení System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="ae83b-119">In **Solution Explorer**, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="defining-the-application-layout"></a><span data-ttu-id="ae83b-120">Definování rozložení aplikace</span><span class="sxs-lookup"><span data-stu-id="ae83b-120">Defining the Application Layout</span></span>

<span data-ttu-id="ae83b-121">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace používá <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek pro hostování ovládacího prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ae83b-121">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a Windows Forms control.</span></span>

### <a name="to-define-the-application-layout"></a><span data-ttu-id="ae83b-122">Definování rozložení aplikace</span><span class="sxs-lookup"><span data-stu-id="ae83b-122">To define the application layout</span></span>

1. <span data-ttu-id="ae83b-123">Otevřete Window1. XAML v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="ae83b-123">Open Window1.xaml in the WPF Designer.</span></span>

2. <span data-ttu-id="ae83b-124">Nahraďte existující kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="ae83b-124">Replace the existing code with the following code.</span></span>

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. <span data-ttu-id="ae83b-125">Otevřete Window1.xaml.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="ae83b-125">Open Window1.xaml.cs in the Code Editor.</span></span>

4. <span data-ttu-id="ae83b-126">V horní části souboru importujte následující obory názvů.</span><span class="sxs-lookup"><span data-stu-id="ae83b-126">At the top of the file, import the following namespaces.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="ae83b-127">Definování nového mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="ae83b-127">Defining a New Property Mapping</span></span>

<span data-ttu-id="ae83b-128">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> poskytuje několik výchozích mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="ae83b-128">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="ae83b-129">Přidáte nové mapování vlastností voláním metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-129">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="ae83b-130">Definování nového mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="ae83b-130">To define a new property mapping</span></span>

- <span data-ttu-id="ae83b-131">Zkopírujte následující kód do definice pro třídu `Window1`.</span><span class="sxs-lookup"><span data-stu-id="ae83b-131">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     <span data-ttu-id="ae83b-132">Metoda `AddClipMapping` přidá nové mapování pro vlastnost <xref:System.Windows.UIElement.Clip%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-132">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="ae83b-133">Metoda `OnClipChange` překládá vlastnost <xref:System.Windows.UIElement.Clip%2A> na vlastnost model Windows Forms<xref:System.Windows.Forms.Control.Region%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-133">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the Windows Forms<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="ae83b-134">Metoda `Window1_SizeChanged` zpracovává událost <xref:System.Windows.FrameworkElement.SizeChanged> okna a velikost oblasti oříznutí tak, aby odpovídala oknu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae83b-134">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="ae83b-135">Odebírá se výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="ae83b-135">Removing a Default Property Mapping</span></span>

<span data-ttu-id="ae83b-136">Odeberte výchozí mapování vlastností voláním metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-136">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="ae83b-137">Odebrání výchozího mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="ae83b-137">To remove a default property mapping</span></span>

- <span data-ttu-id="ae83b-138">Zkopírujte následující kód do definice pro třídu `Window1`.</span><span class="sxs-lookup"><span data-stu-id="ae83b-138">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     <span data-ttu-id="ae83b-139">Metoda `RemoveCursorMapping` odstraní výchozí mapování pro vlastnost <xref:System.Windows.FrameworkElement.Cursor%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-139">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>

## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="ae83b-140">Nahrazení výchozího mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="ae83b-140">Replacing a Default Property Mapping</span></span>

<span data-ttu-id="ae83b-141">Nahraďte výchozí mapování vlastností odebráním výchozího mapování a voláním metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-141">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>

### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="ae83b-142">Nahrazení výchozího mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="ae83b-142">To replace a default property mapping</span></span>

- <span data-ttu-id="ae83b-143">Zkopírujte následující kód do definice pro třídu `Window1`.</span><span class="sxs-lookup"><span data-stu-id="ae83b-143">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     <span data-ttu-id="ae83b-144">Metoda `ReplaceFlowDirectionMapping` nahrazuje výchozí mapování pro vlastnost <xref:System.Windows.FrameworkElement.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-144">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>

     <span data-ttu-id="ae83b-145">Metoda `OnFlowDirectionChange` překládá vlastnost <xref:System.Windows.FrameworkElement.FlowDirection%2A> na vlastnost model Windows Forms<xref:System.Windows.Forms.Control.RightToLeft%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-145">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the Windows Forms<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>

     <span data-ttu-id="ae83b-146">Metoda `cb_CheckedChanged` zpracovává událost <xref:System.Windows.Forms.CheckBox.CheckedChanged> v ovládacím prvku <xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-146">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="ae83b-147">Přiřadí vlastnost <xref:System.Windows.FrameworkElement.FlowDirection%2A> na základě hodnoty vlastnosti <xref:System.Windows.Forms.CheckBox.CheckState%2A></span><span class="sxs-lookup"><span data-stu-id="ae83b-147">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="ae83b-148">Rozšíření výchozího mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="ae83b-148">Extending a Default Property Mapping</span></span>

<span data-ttu-id="ae83b-149">Můžete použít výchozí mapování vlastností a také ho roztáhnout s vlastním mapováním.</span><span class="sxs-lookup"><span data-stu-id="ae83b-149">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="ae83b-150">Postup při rozšiřování výchozího mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="ae83b-150">To extend a default property mapping</span></span>

- <span data-ttu-id="ae83b-151">Zkopírujte následující kód do definice pro třídu `Window1`.</span><span class="sxs-lookup"><span data-stu-id="ae83b-151">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     <span data-ttu-id="ae83b-152">Metoda `ExtendBackgroundMapping` přidá do existujícího mapování vlastností <xref:System.Windows.Controls.Control.Background%2A> překladatele vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ae83b-152">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>

     <span data-ttu-id="ae83b-153">Metoda `OnBackgroundChange` přiřadí konkrétní obrázek k vlastnosti <xref:System.Windows.Forms.Control.BackgroundImage%2A> hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ae83b-153">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="ae83b-154">Metoda `OnBackgroundChange` je volána poté, co je použito výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="ae83b-154">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>

## <a name="initializing-your-property-mappings"></a><span data-ttu-id="ae83b-155">Inicializuje se mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="ae83b-155">Initializing Your Property Mappings</span></span>

<span data-ttu-id="ae83b-156">Nastavte mapování vlastností voláním dříve popsaných metod v obslužné rutině události <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-156">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="ae83b-157">Inicializace mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="ae83b-157">To initialize your property mappings</span></span>

1. <span data-ttu-id="ae83b-158">Zkopírujte následující kód do definice pro třídu `Window1`.</span><span class="sxs-lookup"><span data-stu-id="ae83b-158">Copy the following code into the definition for the `Window1` class.</span></span>

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     <span data-ttu-id="ae83b-159">Metoda `WindowLoaded` zpracovává událost <xref:System.Windows.FrameworkElement.Loaded> a provádí následující inicializaci.</span><span class="sxs-lookup"><span data-stu-id="ae83b-159">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>

    - <span data-ttu-id="ae83b-160">Vytvoří ovládací prvek model Windows Forms<xref:System.Windows.Forms.CheckBox>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-160">Creates a Windows Forms<xref:System.Windows.Forms.CheckBox> control.</span></span>

    - <span data-ttu-id="ae83b-161">Volá metody, které jste definovali dříve v návodu, aby se nastavilo mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="ae83b-161">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="ae83b-162">Přiřadí počáteční hodnoty k mapovaným vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="ae83b-162">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="ae83b-163">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ae83b-163">Press **F5** to build and run the application.</span></span> <span data-ttu-id="ae83b-164">Kliknutím na zaškrtávací políčko zobrazíte efekt mapování <xref:System.Windows.FrameworkElement.FlowDirection%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae83b-164">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="ae83b-165">Když kliknete na zaškrtávací políčko, rozložení obrátí svou orientaci zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="ae83b-165">When you click the check box, the layout reverses its left-right orientation.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae83b-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae83b-166">See also</span></span>

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="ae83b-167">Mapování vlastnosti Windows Forms a WPF</span><span class="sxs-lookup"><span data-stu-id="ae83b-167">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="ae83b-168">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ae83b-168">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="ae83b-169">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="ae83b-169">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
