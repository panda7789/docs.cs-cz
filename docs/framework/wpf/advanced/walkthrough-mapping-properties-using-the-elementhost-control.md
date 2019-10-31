---
title: 'Návod: Mapování vlastností použitím ovládacího prvku ElementHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 7d1cf353f7e6c4b87c13598e7e6029960cd0f715
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197812"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="7ed49-102">Návod: Mapování vlastností použitím ovládacího prvku ElementHost</span><span class="sxs-lookup"><span data-stu-id="7ed49-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>

<span data-ttu-id="7ed49-103">V tomto návodu se dozvíte, jak použít vlastnost <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> k mapování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastností na odpovídající vlastnosti u hostovaného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="7ed49-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>

<span data-ttu-id="7ed49-104">Úlohy, které jsou znázorněné v tomto návodu, zahrnují:</span><span class="sxs-lookup"><span data-stu-id="7ed49-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="7ed49-105">Vytváří se projekt.</span><span class="sxs-lookup"><span data-stu-id="7ed49-105">Creating the project.</span></span>

- <span data-ttu-id="7ed49-106">Definování nového mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="7ed49-106">Defining a new property mapping.</span></span>

- <span data-ttu-id="7ed49-107">Odebírá se výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="7ed49-107">Removing a default property mapping.</span></span>

- <span data-ttu-id="7ed49-108">Rozšíření výchozího mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="7ed49-108">Extending a default property mapping.</span></span>

<span data-ttu-id="7ed49-109">Úplný výpis kódu úloh, které jsou znázorněny v tomto návodu, najdete v tématu [mapování vlastností pomocí ukázky ovládacího prvku ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="7ed49-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](https://go.microsoft.com/fwlink/?LinkID=160018).</span></span>

<span data-ttu-id="7ed49-110">Až budete hotovi, budete moci mapovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti na odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti v hostovaném elementu.</span><span class="sxs-lookup"><span data-stu-id="7ed49-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7ed49-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ed49-111">Prerequisites</span></span>

<span data-ttu-id="7ed49-112">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="7ed49-112">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="7ed49-113">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7ed49-113">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="7ed49-114">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="7ed49-114">Creating the Project</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="7ed49-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="7ed49-115">To create the project</span></span>

1. <span data-ttu-id="7ed49-116">Vytvořte projekt **aplikace model Windows Forms** s názvem `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="7ed49-116">Create a **Windows Forms App** project named `PropertyMappingWithElementHost`.</span></span>

2. <span data-ttu-id="7ed49-117">V **Průzkumník řešení**přidejte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="7ed49-117">In **Solution Explorer**, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>

    - <span data-ttu-id="7ed49-118">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="7ed49-118">PresentationCore</span></span>

    - <span data-ttu-id="7ed49-119">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="7ed49-119">PresentationFramework</span></span>

    - <span data-ttu-id="7ed49-120">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="7ed49-120">WindowsBase</span></span>

    - <span data-ttu-id="7ed49-121">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="7ed49-121">WindowsFormsIntegration</span></span>

3. <span data-ttu-id="7ed49-122">Zkopírujte následující kód do horní části souboru kódu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7ed49-122">Copy the following code into the top of the `Form1` code file.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. <span data-ttu-id="7ed49-123">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="7ed49-123">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="7ed49-124">Dvakrát klikněte na formulář a přidejte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Form.Load>.</span><span class="sxs-lookup"><span data-stu-id="7ed49-124">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>

5. <span data-ttu-id="7ed49-125">Vraťte se do Návrhář formulářů a přidejte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Resize> formuláře.</span><span class="sxs-lookup"><span data-stu-id="7ed49-125">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="7ed49-126">Další informace naleznete v tématu [Postupy: vytváření obslužných rutin událostí pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7ed49-126">For more information, see [How to: Create Event Handlers Using the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).</span></span>

6. <span data-ttu-id="7ed49-127">Deklaruje pole <xref:System.Windows.Forms.Integration.ElementHost> ve třídě `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7ed49-127">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a><span data-ttu-id="7ed49-128">Definování nových mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="7ed49-128">Defining New Property Mappings</span></span>

<span data-ttu-id="7ed49-129">Ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> poskytuje několik výchozích mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="7ed49-129">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="7ed49-130">Přidáte nové mapování vlastností voláním metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="7ed49-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-define-new-property-mappings"></a><span data-ttu-id="7ed49-131">Definování nových mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="7ed49-131">To define new property mappings</span></span>

1. <span data-ttu-id="7ed49-132">Zkopírujte následující kód do definice pro třídu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7ed49-132">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     <span data-ttu-id="7ed49-133">Metoda `AddMarginMapping` přidá nové mapování pro vlastnost <xref:System.Windows.Forms.Control.Margin%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ed49-133">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>

     <span data-ttu-id="7ed49-134">Metoda `OnMarginChange` překládá vlastnost <xref:System.Windows.Forms.Control.Margin%2A> na vlastnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ed49-134">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>

2. <span data-ttu-id="7ed49-135">Zkopírujte následující kód do definice pro třídu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7ed49-135">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     <span data-ttu-id="7ed49-136">Metoda `AddRegionMapping` přidá nové mapování pro vlastnost <xref:System.Windows.Forms.Control.Region%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ed49-136">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="7ed49-137">Metoda `OnRegionChange` překládá vlastnost <xref:System.Windows.Forms.Control.Region%2A> na vlastnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ed49-137">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="7ed49-138">Metoda `Form1_Resize` zpracovává událost <xref:System.Windows.Forms.Control.Resize> formuláře a velikost oblasti oříznutí tak, aby odpovídala hostovanému elementu.</span><span class="sxs-lookup"><span data-stu-id="7ed49-138">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="7ed49-139">Odebírá se výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="7ed49-139">Removing a Default Property Mapping</span></span>

<span data-ttu-id="7ed49-140">Odeberte výchozí mapování vlastností voláním metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="7ed49-140">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="7ed49-141">Odebrání výchozího mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="7ed49-141">To remove a default property mapping</span></span>

- <span data-ttu-id="7ed49-142">Zkopírujte následující kód do definice pro třídu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7ed49-142">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     <span data-ttu-id="7ed49-143">Metoda `RemoveCursorMapping` odstraní výchozí mapování pro vlastnost <xref:System.Windows.Forms.Control.Cursor%2A>.</span><span class="sxs-lookup"><span data-stu-id="7ed49-143">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="7ed49-144">Rozšíření výchozího mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="7ed49-144">Extending a Default Property Mapping</span></span>

<span data-ttu-id="7ed49-145">Můžete použít výchozí mapování vlastností a také ho roztáhnout s vlastním mapováním.</span><span class="sxs-lookup"><span data-stu-id="7ed49-145">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="7ed49-146">Postup při rozšiřování výchozího mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="7ed49-146">To extend a default property mapping</span></span>

- <span data-ttu-id="7ed49-147">Zkopírujte následující kód do definice pro třídu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7ed49-147">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     <span data-ttu-id="7ed49-148">Metoda `ExtendBackColorMapping` přidá do existujícího mapování vlastností <xref:System.Windows.Forms.Control.BackColor%2A> překladatele vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7ed49-148">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>

     <span data-ttu-id="7ed49-149">Metoda `OnBackColorChange` přiřadí konkrétní obrázek k vlastnosti <xref:System.Windows.Controls.Control.Background%2A> hostovaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7ed49-149">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="7ed49-150">Metoda `OnBackColorChange` je volána poté, co je použito výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="7ed49-150">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>

## <a name="initialize-your-property-mappings"></a><span data-ttu-id="7ed49-151">Inicializace mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="7ed49-151">Initialize your property mappings</span></span>

1. <span data-ttu-id="7ed49-152">Zkopírujte následující kód do definice pro třídu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7ed49-152">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     <span data-ttu-id="7ed49-153">Metoda `Form1_Load` zpracovává událost <xref:System.Windows.Forms.Form.Load> a provádí následující inicializaci.</span><span class="sxs-lookup"><span data-stu-id="7ed49-153">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>

    - <span data-ttu-id="7ed49-154">Vytvoří prvek <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ed49-154">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>

    - <span data-ttu-id="7ed49-155">Volá metody, které jste definovali dříve v návodu, aby se nastavilo mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="7ed49-155">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    - <span data-ttu-id="7ed49-156">Přiřadí počáteční hodnoty k mapovaným vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="7ed49-156">Assigns initial values to the mapped properties.</span></span>

2. <span data-ttu-id="7ed49-157">Stisknutím klávesy F5 Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7ed49-157">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ed49-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ed49-158">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="7ed49-159">Mapování vlastnosti Windows Forms a WPF</span><span class="sxs-lookup"><span data-stu-id="7ed49-159">Windows Forms and WPF Property Mapping</span></span>](windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="7ed49-160">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7ed49-160">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="7ed49-161">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ed49-161">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
