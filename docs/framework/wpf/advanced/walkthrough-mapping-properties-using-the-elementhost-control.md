---
title: 'Návod: Mapování vlastností použitím ovládacího prvku ElementHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: b5af1f45a0d01761358e83c890544ec1a11836e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549188"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="dc1f0-102">Návod: Mapování vlastností použitím ovládacího prvku ElementHost</span><span class="sxs-lookup"><span data-stu-id="dc1f0-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>
<span data-ttu-id="dc1f0-103">Tento postup vám ukáže, jak používat <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> vlastnost mapovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti na odpovídající vlastnosti na hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>  
  
 <span data-ttu-id="dc1f0-104">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="dc1f0-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="dc1f0-105">Vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="dc1f0-106">Definování nového mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-106">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="dc1f0-107">Odebrání výchozí vlastnost mapování.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-107">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="dc1f0-108">Rozšíření výchozí vlastnost mapování.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-108">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="dc1f0-109">Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [mapování vlastností pomocí Ukázka ovládacího prvku ElementHost](http://go.microsoft.com/fwlink/?LinkID=160018).</span><span class="sxs-lookup"><span data-stu-id="dc1f0-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](http://go.microsoft.com/fwlink/?LinkID=160018).</span></span>  
  
 <span data-ttu-id="dc1f0-110">Po dokončení bude možné mapovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti k odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti hostované elementu.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dc1f0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc1f0-111">Prerequisites</span></span>  
 <span data-ttu-id="dc1f0-112">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="dc1f0-112">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="dc1f0-113">.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-113">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="dc1f0-114">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="dc1f0-114">Creating the Project</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="dc1f0-115">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="dc1f0-115">To create the project</span></span>  
  
1.  <span data-ttu-id="dc1f0-116">Vytvoření [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projekt aplikace s názvem `PropertyMappingWithElementHost`.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-116">Create a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project named `PropertyMappingWithElementHost`.</span></span> <span data-ttu-id="dc1f0-117">Další informace najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="dc1f0-117">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="dc1f0-118">V Průzkumníku řešení přidáte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-118">In Solution Explorer, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>  
  
    -   <span data-ttu-id="dc1f0-119">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="dc1f0-119">PresentationCore</span></span>  
  
    -   <span data-ttu-id="dc1f0-120">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="dc1f0-120">PresentationFramework</span></span>  
  
    -   <span data-ttu-id="dc1f0-121">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="dc1f0-121">WindowsBase</span></span>  
  
    -   <span data-ttu-id="dc1f0-122">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="dc1f0-122">WindowsFormsIntegration</span></span>  
  
3.  <span data-ttu-id="dc1f0-123">Zkopírujte následující kód do horní části `Form1` souboru kódu.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-123">Copy the following code into the top of the `Form1` code file.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  <span data-ttu-id="dc1f0-124">Otevřete `Form1` v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-124">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="dc1f0-125">Klikněte dvakrát na formuláři pro přidání obslužné rutiny události pro <xref:System.Windows.Forms.Form.Load> událostí.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-125">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
5.  <span data-ttu-id="dc1f0-126">Vraťte se na správce systému Windows Forms a přidání obslužné rutiny události pro daný formulář <xref:System.Windows.Forms.Control.Resize> události.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-126">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="dc1f0-127">Další informace najdete v tématu [postupy: vytvoření události obslužné rutiny pomocí návrháře](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span><span class="sxs-lookup"><span data-stu-id="dc1f0-127">For more information, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>  
  
6.  <span data-ttu-id="dc1f0-128">Deklarace <xref:System.Windows.Forms.Integration.ElementHost> pole `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-128">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a><span data-ttu-id="dc1f0-129">Definování nového mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="dc1f0-129">Defining New Property Mappings</span></span>  
 <span data-ttu-id="dc1f0-130"><xref:System.Windows.Forms.Integration.ElementHost> Řízení poskytuje několik výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-130">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="dc1f0-131">Přidat nové mapování vlastností voláním <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-131">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-new-property-mappings"></a><span data-ttu-id="dc1f0-132">Chcete-li definovat nové mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="dc1f0-132">To define new property mappings</span></span>  
  
1.  <span data-ttu-id="dc1f0-133">Zkopírujte následující kód do definice pro `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-133">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     <span data-ttu-id="dc1f0-134">`AddMarginMapping` Metoda přidá nové mapování <xref:System.Windows.Forms.Control.Margin%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-134">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>  
  
     <span data-ttu-id="dc1f0-135">`OnMarginChange` Metoda přeloží <xref:System.Windows.Forms.Control.Margin%2A> vlastnost, která má [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-135">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>  
  
2.  <span data-ttu-id="dc1f0-136">Zkopírujte následující kód do definice pro `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-136">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     <span data-ttu-id="dc1f0-137">`AddRegionMapping` Metoda přidá nové mapování <xref:System.Windows.Forms.Control.Region%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-137">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="dc1f0-138">`OnRegionChange` Metoda přeloží <xref:System.Windows.Forms.Control.Region%2A> vlastnost, která má [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-138">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="dc1f0-139">`Form1_Resize` Metoda zpracovává formuláře <xref:System.Windows.Forms.Control.Resize> událostí a velikosti oblast ořezu podle hostované elementu.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-139">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="dc1f0-140">Odebrání výchozí vlastnost mapování</span><span class="sxs-lookup"><span data-stu-id="dc1f0-140">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="dc1f0-141">Odebrání výchozí vlastnost mapování voláním <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodu <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-141">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="dc1f0-142">Chcete-li odebrat mapování výchozí vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dc1f0-142">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="dc1f0-143">Zkopírujte následující kód do definice pro `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-143">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     <span data-ttu-id="dc1f0-144">`RemoveCursorMapping` Metoda odstraní výchozí mapování <xref:System.Windows.Forms.Control.Cursor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-144">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="dc1f0-145">Rozšíření výchozí vlastnost mapování</span><span class="sxs-lookup"><span data-stu-id="dc1f0-145">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="dc1f0-146">Můžete použít výchozí vlastnost mapování a také ho rozšířit pomocí vlastního mapování.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-146">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="dc1f0-147">Chcete-li rozšířit výchozí vlastnost mapování</span><span class="sxs-lookup"><span data-stu-id="dc1f0-147">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="dc1f0-148">Zkopírujte následující kód do definice pro `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-148">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     <span data-ttu-id="dc1f0-149">`ExtendBackColorMapping` Metoda přidá převaděče vlastní vlastnost ke stávající <xref:System.Windows.Forms.Control.BackColor%2A> mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-149">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>  
  
     <span data-ttu-id="dc1f0-150">`OnBackColorChange` Metoda přiřadí konkrétní image do ovládacího prvku hostované <xref:System.Windows.Controls.Control.Background%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-150">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="dc1f0-151">`OnBackColorChange` Metoda je volána, pokud je použita výchozí vlastnost mapování.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-151">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="dc1f0-152">Inicializace mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="dc1f0-152">Initializing Your Property Mappings</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="dc1f0-153">K chybě při inicializaci mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="dc1f0-153">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="dc1f0-154">Zkopírujte následující kód do definice pro `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-154">Copy the following code into the definition for the `Form1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     <span data-ttu-id="dc1f0-155">`Form1_Load` Metoda zpracovává <xref:System.Windows.Forms.Form.Load> událostí a provede následující inicializace.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-155">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="dc1f0-156">Vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-156">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>  
  
    -   <span data-ttu-id="dc1f0-157">Volá metody, které jste definovali dříve v tomto návodu nastavit mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-157">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="dc1f0-158">Přiřadí počáteční hodnoty pro vlastnosti namapované.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-158">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="dc1f0-159">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="dc1f0-159">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc1f0-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc1f0-160">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="dc1f0-161">Mapování vlastnosti Windows Forms a WPF</span><span class="sxs-lookup"><span data-stu-id="dc1f0-161">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="dc1f0-162">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="dc1f0-162">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="dc1f0-163">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc1f0-163">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
