---
title: "Návod: Mapování vlastností použitím elementu WindowsFormsHost"
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
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eaab6b7724a1e6145dfce3998ccf75904df01802
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="073b2-102">Návod: Mapování vlastností použitím elementu WindowsFormsHost</span><span class="sxs-lookup"><span data-stu-id="073b2-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>
<span data-ttu-id="073b2-103">Tento postup vám ukáže, jak používat <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> vlastnost mapovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti na odpovídající vlastnosti na hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="073b2-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
 <span data-ttu-id="073b2-104">Úkoly v tomto návodu zahrnují:</span><span class="sxs-lookup"><span data-stu-id="073b2-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="073b2-105">Vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="073b2-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="073b2-106">Definování rozložení aplikace.</span><span class="sxs-lookup"><span data-stu-id="073b2-106">Defining the application layout.</span></span>  
  
-   <span data-ttu-id="073b2-107">Definování nového mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="073b2-107">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="073b2-108">Odebrání výchozí vlastnost mapování.</span><span class="sxs-lookup"><span data-stu-id="073b2-108">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="073b2-109">Nahrazení výchozí vlastnost mapování.</span><span class="sxs-lookup"><span data-stu-id="073b2-109">Replacing a default property mapping.</span></span>  
  
-   <span data-ttu-id="073b2-110">Rozšíření výchozí vlastnost mapování.</span><span class="sxs-lookup"><span data-stu-id="073b2-110">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="073b2-111">Kompletní kód tak seznam všech úloh v tomto návodu, najdete v části [mapování vlastností pomocí ukázka prvky WindowsFormsHost](http://go.microsoft.com/fwlink/?LinkID=160019).</span><span class="sxs-lookup"><span data-stu-id="073b2-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](http://go.microsoft.com/fwlink/?LinkID=160019).</span></span>  
  
 <span data-ttu-id="073b2-112">Po dokončení bude možné mapovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti na odpovídající vlastnosti na hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="073b2-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="073b2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="073b2-113">Prerequisites</span></span>  
 <span data-ttu-id="073b2-114">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="073b2-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="073b2-115">.</span><span class="sxs-lookup"><span data-stu-id="073b2-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="073b2-116">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="073b2-116">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="073b2-117">Vytvoření a nastavení projektu</span><span class="sxs-lookup"><span data-stu-id="073b2-117">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="073b2-118">Vytvořte projekt aplikace WPF s názvem `PropertyMappingWithWfhSample`.</span><span class="sxs-lookup"><span data-stu-id="073b2-118">Create a WPF Application project named `PropertyMappingWithWfhSample`.</span></span>  
  
2.  <span data-ttu-id="073b2-119">V Průzkumníku řešení přidáte odkaz na sestavení WindowsFormsIntegration, která se nazývá WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="073b2-119">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="073b2-120">V Průzkumníku řešení přidejte odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="073b2-120">In Solution Explorer, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="defining-the-application-layout"></a><span data-ttu-id="073b2-121">Definování rozložení aplikace</span><span class="sxs-lookup"><span data-stu-id="073b2-121">Defining the Application Layout</span></span>  
 <span data-ttu-id="073b2-122">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– Na základě používá aplikace <xref:System.Windows.Forms.Integration.WindowsFormsHost> element hostitele [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="073b2-122">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-define-the-application-layout"></a><span data-ttu-id="073b2-123">Chcete-li definovat rozložení aplikace</span><span class="sxs-lookup"><span data-stu-id="073b2-123">To define the application layout</span></span>  
  
1.  <span data-ttu-id="073b2-124">Otevřete Window1.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="073b2-124">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="073b2-125">Existujícího kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="073b2-125">Replace the existing code with the following code.</span></span>  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  <span data-ttu-id="073b2-126">Otevřete Window1.xaml.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="073b2-126">Open Window1.xaml.cs in the Code Editor.</span></span>  
  
4.  <span data-ttu-id="073b2-127">V horní části souboru importujte následujících oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="073b2-127">At the top of the file, import the following namespaces.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="073b2-128">Definování nového mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="073b2-128">Defining a New Property Mapping</span></span>  
 <span data-ttu-id="073b2-129"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element poskytuje několik výchozí mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="073b2-129">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="073b2-130">Přidat nové mapování vlastností voláním <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="073b2-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="073b2-131">Chcete-li definovat nové mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="073b2-131">To define a new property mapping</span></span>  
  
-   <span data-ttu-id="073b2-132">Zkopírujte následující kód do definice pro `Window1` třídy.</span><span class="sxs-lookup"><span data-stu-id="073b2-132">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     <span data-ttu-id="073b2-133">`AddClipMapping` Metoda přidá nové mapování <xref:System.Windows.UIElement.Clip%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="073b2-133">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="073b2-134">`OnClipChange` Metoda přeloží <xref:System.Windows.UIElement.Clip%2A> vlastnost, která má [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="073b2-134">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="073b2-135">`Window1_SizeChanged` Metoda zpracovává okna <xref:System.Windows.FrameworkElement.SizeChanged> událostí a velikosti oblast ořezu velikosti okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="073b2-135">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="073b2-136">Odebrání výchozí vlastnost mapování</span><span class="sxs-lookup"><span data-stu-id="073b2-136">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="073b2-137">Odebrání výchozí vlastnost mapování voláním <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="073b2-137">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="073b2-138">Chcete-li odebrat mapování výchozí vlastnosti</span><span class="sxs-lookup"><span data-stu-id="073b2-138">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="073b2-139">Zkopírujte následující kód do definice pro `Window1` třídy.</span><span class="sxs-lookup"><span data-stu-id="073b2-139">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     <span data-ttu-id="073b2-140">`RemoveCursorMapping` Metoda odstraní výchozí mapování <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="073b2-140">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>  
  
## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="073b2-141">Nahrazení výchozí vlastnost mapování</span><span class="sxs-lookup"><span data-stu-id="073b2-141">Replacing a Default Property Mapping</span></span>  
 <span data-ttu-id="073b2-142">Nahraďte odebráním výchozí mapování a volání výchozí vlastnosti mapování <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span><span class="sxs-lookup"><span data-stu-id="073b2-142">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="073b2-143">Chcete-li nahradit výchozí vlastnost mapování</span><span class="sxs-lookup"><span data-stu-id="073b2-143">To replace a default property mapping</span></span>  
  
-   <span data-ttu-id="073b2-144">Zkopírujte následující kód do definice pro `Window1` třídy.</span><span class="sxs-lookup"><span data-stu-id="073b2-144">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     <span data-ttu-id="073b2-145">`ReplaceFlowDirectionMapping` Metoda nahrazuje výchozí mapování <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="073b2-145">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>  
  
     <span data-ttu-id="073b2-146">`OnFlowDirectionChange` Metoda přeloží <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost, která má [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="073b2-146">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>  
  
     <span data-ttu-id="073b2-147">`cb_CheckedChanged` Metoda zpracovává <xref:System.Windows.Forms.CheckBox.CheckedChanged> událostí na <xref:System.Windows.Forms.CheckBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="073b2-147">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="073b2-148">Přiřadí <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost podle hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnost</span><span class="sxs-lookup"><span data-stu-id="073b2-148">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="073b2-149">Rozšíření výchozí vlastnost mapování</span><span class="sxs-lookup"><span data-stu-id="073b2-149">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="073b2-150">Můžete použít výchozí vlastnost mapování a také ho rozšířit pomocí vlastního mapování.</span><span class="sxs-lookup"><span data-stu-id="073b2-150">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="073b2-151">Chcete-li rozšířit výchozí vlastnost mapování</span><span class="sxs-lookup"><span data-stu-id="073b2-151">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="073b2-152">Zkopírujte následující kód do definice pro `Window1` třídy.</span><span class="sxs-lookup"><span data-stu-id="073b2-152">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     <span data-ttu-id="073b2-153">`ExtendBackgroundMapping` Metoda přidá převaděče vlastní vlastnost ke stávající <xref:System.Windows.Controls.Control.Background%2A> mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="073b2-153">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>  
  
     <span data-ttu-id="073b2-154">`OnBackgroundChange` Metoda přiřadí konkrétní image do ovládacího prvku hostované <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="073b2-154">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="073b2-155">`OnBackgroundChange` Metoda je volána, pokud je použita výchozí vlastnost mapování.</span><span class="sxs-lookup"><span data-stu-id="073b2-155">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="073b2-156">Inicializace mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="073b2-156">Initializing Your Property Mappings</span></span>  
 <span data-ttu-id="073b2-157">Nastavit mapování vlastností voláním výše uvedené postupy v <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="073b2-157">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="073b2-158">K chybě při inicializaci mapování vlastností</span><span class="sxs-lookup"><span data-stu-id="073b2-158">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="073b2-159">Zkopírujte následující kód do definice pro `Window1` třídy.</span><span class="sxs-lookup"><span data-stu-id="073b2-159">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     <span data-ttu-id="073b2-160">`WindowLoaded` Metoda zpracovává <xref:System.Windows.FrameworkElement.Loaded> událostí a provede následující inicializace.</span><span class="sxs-lookup"><span data-stu-id="073b2-160">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="073b2-161">Vytvoří [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="073b2-161">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>  
  
    -   <span data-ttu-id="073b2-162">Volá metody, které jste definovali dříve v tomto návodu nastavit mapování vlastností.</span><span class="sxs-lookup"><span data-stu-id="073b2-162">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="073b2-163">Přiřadí počáteční hodnoty pro vlastnosti namapované.</span><span class="sxs-lookup"><span data-stu-id="073b2-163">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="073b2-164">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="073b2-164">Press F5 to build and run the application.</span></span> <span data-ttu-id="073b2-165">Klikněte na zaškrtávací políčko zobrazíte účinku <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapování.</span><span class="sxs-lookup"><span data-stu-id="073b2-165">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="073b2-166">Po kliknutí na tlačítko zaškrtnutí políčka, rozložení obrátí její orientace zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="073b2-166">When you click the check box, the layout reverses its left-right orientation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="073b2-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="073b2-167">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="073b2-168">Mapování vlastnosti Windows Forms a WPF</span><span class="sxs-lookup"><span data-stu-id="073b2-168">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="073b2-169">WPF Designer</span><span class="sxs-lookup"><span data-stu-id="073b2-169">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="073b2-170">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="073b2-170">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
