---
title: "Pomocí typem ModelItem úpravy kontextu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fde8bf45e01f8e3fede04c08d63177271a4a6faf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="81e3e-102">Pomocí typem ModelItem úpravy kontextu</span><span class="sxs-lookup"><span data-stu-id="81e3e-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="81e3e-103"><xref:System.Activities.Presentation.Model.ModelItem> Úpravy kontextu je objekt, který aplikace hostitele používá ke komunikaci pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="81e3e-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="81e3e-104"><xref:System.Activities.Presentation.EditingContext>poskytuje dvě metody, <xref:System.Activities.Presentation.EditingContext.Items%2A> a <xref:System.Activities.Presentation.EditingContext.Services%2A>, který může být použit</span><span class="sxs-lookup"><span data-stu-id="81e3e-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="81e3e-105">Kolekce položek</span><span class="sxs-lookup"><span data-stu-id="81e3e-105">The Items collection</span></span>  
 <span data-ttu-id="81e3e-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekce slouží pro přístup k data, která jsou sdílena mezi hostiteli a návrháře nebo data, která je k dispozici pro všechny Designer.</span><span class="sxs-lookup"><span data-stu-id="81e3e-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="81e3e-107">Tato kolekce má následující možnosti, přístup prostřednictvím <xref:System.Activities.Presentation.ContextItemManager> třídy:</span><span class="sxs-lookup"><span data-stu-id="81e3e-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1.  <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2.  <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="81e3e-108">Kolekce služeb</span><span class="sxs-lookup"><span data-stu-id="81e3e-108">The Services collection</span></span>  
 <span data-ttu-id="81e3e-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekce slouží k přístupu služby, které návrháře používá k interakci s hostitelem nebo služby, které používají všechny Designer.</span><span class="sxs-lookup"><span data-stu-id="81e3e-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="81e3e-110">Tato kolekce nemá tyto metody Poznámka:</span><span class="sxs-lookup"><span data-stu-id="81e3e-110">This collection has the following methods of note:</span></span>  
  
1.  <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2.  <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="81e3e-111">Přiřazení Návrhář aktivity</span><span class="sxs-lookup"><span data-stu-id="81e3e-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="81e3e-112">Chcete-li určit, které Návrhář aktivita používá, se používá atributu Designer.</span><span class="sxs-lookup"><span data-stu-id="81e3e-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="81e3e-113">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="81e3e-113">Creating a service</span></span>  
 <span data-ttu-id="81e3e-114">Pokud chcete vytvořit službu, která slouží jako kanál informací mezi designer a hostitele, musí být vytvořeny rozhraní a implementace.</span><span class="sxs-lookup"><span data-stu-id="81e3e-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="81e3e-115">Rozhraní používá <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metoda k definování členů služby a implementaci obsahuje logiku pro službu.</span><span class="sxs-lookup"><span data-stu-id="81e3e-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="81e3e-116">V následujícím příkladu kódu rozhraní služby a implementace vytvoří.</span><span class="sxs-lookup"><span data-stu-id="81e3e-116">In the following code example, a service interface and implementation are created.</span></span>  
  
```  
public interface IMyService  
    {  
        IEnumerable<string> GetValues(string DisplayName);  
    }  
  
    public class MyServiceImpl : IMyService  
    {  
        public IEnumerable<string> GetValues(string DisplayName)  
        {  
            return new string[]  {   
                DisplayName + " One",   
                DisplayName + " Two",  
                "Three " + DisplayName  
            } ;  
        }  
    }  
```  
  
## <a name="publishing-a-service"></a><span data-ttu-id="81e3e-117">Publikování služby</span><span class="sxs-lookup"><span data-stu-id="81e3e-117">Publishing a service</span></span>  
 <span data-ttu-id="81e3e-118">Pro Návrhář využívat službu, je třeba nejprve ji publikovat hostitele pomocí <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="81e3e-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="81e3e-119">K odběru služby</span><span class="sxs-lookup"><span data-stu-id="81e3e-119">Subscribing to a service</span></span>  
 <span data-ttu-id="81e3e-120">Návrhář získává přístup pomocí služby <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metoda v <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="81e3e-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="81e3e-121">Následující fragment kódu ukazuje, jak k odběru služby.</span><span class="sxs-lookup"><span data-stu-id="81e3e-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
```  
protected override void OnModelItemChanged(object newItem)  
{  
    if (!subscribed)  
    {  
        this.Context.Services.Subscribe<IMyService>(  
            servInstance =>  
            {  
                listBox1.ItemsSource = servInstance.GetValues(this.ModelItem.Properties["DisplayName"].ComputedValue.ToString());  
            }  
            );  
        subscribed = true;   
    }  
}  
```  
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="81e3e-122">Sdílení dat pomocí položky kolekce</span><span class="sxs-lookup"><span data-stu-id="81e3e-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="81e3e-123">Pomocí položky kolekce je podobná pomocí kolekce služeb, vyjma toho, že <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> se používá namísto publikovat.</span><span class="sxs-lookup"><span data-stu-id="81e3e-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="81e3e-124">Tato kolekce je vhodnější pro sdílení jednoduché datové mezi návrháři a na hostitele, nikoli komplexní funkce.</span><span class="sxs-lookup"><span data-stu-id="81e3e-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="81e3e-125">EditingContext hostitelských položek a služby</span><span class="sxs-lookup"><span data-stu-id="81e3e-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="81e3e-126">.Net Framework poskytuje řadu předdefinovaných položky a služby přistupovat prostřednictvím úprav kontextu.</span><span class="sxs-lookup"><span data-stu-id="81e3e-126">The .Net Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="81e3e-127">Položky:</span><span class="sxs-lookup"><span data-stu-id="81e3e-127">Items:</span></span>  
  
-   <span data-ttu-id="81e3e-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Spravuje seznam odkazovaná místní sestavení, které budou použity uvnitř pracovního postupu pro ovládací prvky (jako je například editor výrazu).</span><span class="sxs-lookup"><span data-stu-id="81e3e-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
-   <span data-ttu-id="81e3e-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Určuje, zda návrháře je ve stavu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="81e3e-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
-   <span data-ttu-id="81e3e-130"><xref:System.Activities.Presentation.View.Selection>: Definuje kolekci objektů, které jsou aktuálně vybrané.</span><span class="sxs-lookup"><span data-stu-id="81e3e-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
-   <span data-ttu-id="81e3e-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="81e3e-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
-   <span data-ttu-id="81e3e-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Poskytuje informace o souboru, který je na základě aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="81e3e-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="81e3e-133">Služba:</span><span class="sxs-lookup"><span data-stu-id="81e3e-133">Services:</span></span>  
  
-   <span data-ttu-id="81e3e-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umožňuje vlastnosti, které chcete přidat do aktuální instance pomocí <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="81e3e-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
-   <span data-ttu-id="81e3e-135"><xref:System.Activities.Presentation.View.DesignerView>: Umožňuje přístup k vlastnosti plátna návrháře.</span><span class="sxs-lookup"><span data-stu-id="81e3e-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
-   <span data-ttu-id="81e3e-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Umožňuje obsah sady nástrojů aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="81e3e-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
-   <span data-ttu-id="81e3e-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Umožňuje integraci s implementací služby poskytované vlastní návrháře příkazy (například Kontextová nabídka).</span><span class="sxs-lookup"><span data-stu-id="81e3e-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
-   <span data-ttu-id="81e3e-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Poskytuje funkce pro návrháře ladicí program.</span><span class="sxs-lookup"><span data-stu-id="81e3e-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
-   <span data-ttu-id="81e3e-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Poskytuje přístup k dialogu Editor výrazů.</span><span class="sxs-lookup"><span data-stu-id="81e3e-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
-   <span data-ttu-id="81e3e-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Poskytuje návrháře funkce integrované nápovědy.</span><span class="sxs-lookup"><span data-stu-id="81e3e-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
-   <span data-ttu-id="81e3e-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Poskytuje přístup k chyby ověření pomocí <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="81e3e-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
-   <span data-ttu-id="81e3e-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Poskytuje interní služby k ukládání a načítání dat.</span><span class="sxs-lookup"><span data-stu-id="81e3e-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="81e3e-143">Tato služba používá se interně pomocí rozhraní .net Framework a není určena pro externí použití.</span><span class="sxs-lookup"><span data-stu-id="81e3e-143">This service is used internally by the .Net Framework, and is not intended for external use.</span></span>  
  
-   <span data-ttu-id="81e3e-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Poskytuje přístup na pomocí kolekce XAML zatížení chyba <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="81e3e-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
-   <span data-ttu-id="81e3e-145"><xref:System.Activities.Presentation.Services.ModelService>: Používají návrháři k interakci s modelem upravovaný pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="81e3e-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
-   <span data-ttu-id="81e3e-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Poskytuje přístup ke kořenu stromu položky modelu pomocí <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="81e3e-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
-   <span data-ttu-id="81e3e-147"><xref:System.Activities.Presentation.UndoEngine>: Poskytuje vrácení zpět a vrátit funkce.</span><span class="sxs-lookup"><span data-stu-id="81e3e-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
-   <span data-ttu-id="81e3e-148"><xref:System.Activities.Presentation.Services.ViewService>: Mapuje vizuální prvky základní položky modelu.</span><span class="sxs-lookup"><span data-stu-id="81e3e-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
-   <span data-ttu-id="81e3e-149"><xref:System.Activities.Presentation.View.ViewStateService>: Úložiště zobrazit stavy položky modelu.</span><span class="sxs-lookup"><span data-stu-id="81e3e-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
-   <span data-ttu-id="81e3e-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Použít k přizpůsobení chování uživatelského rozhraní virtuální kontejneru.</span><span class="sxs-lookup"><span data-stu-id="81e3e-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
-   <span data-ttu-id="81e3e-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Používá k registraci a zrušit registraci delegáty pro oznamování událostí.</span><span class="sxs-lookup"><span data-stu-id="81e3e-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="81e3e-152">Také umožňuje nastavit vlastníka a okna.</span><span class="sxs-lookup"><span data-stu-id="81e3e-152">Also allows a window owner to be set.</span></span>
