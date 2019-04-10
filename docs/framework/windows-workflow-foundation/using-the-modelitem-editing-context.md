---
title: Použití kontextu úprav ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a2628bbbf2f6684e5d484b05cd5a2ac622f3b664
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296875"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="080b3-102">Použití kontextu úprav ModelItem</span><span class="sxs-lookup"><span data-stu-id="080b3-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="080b3-103"><xref:System.Activities.Presentation.Model.ModelItem> Kontextu úprav je objekt, který hostitelská aplikace používá ke komunikaci s návrhářem.</span><span class="sxs-lookup"><span data-stu-id="080b3-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <xref:System.Activities.Presentation.EditingContext> <span data-ttu-id="080b3-104">poskytuje dvě metody <xref:System.Activities.Presentation.EditingContext.Items%2A> a <xref:System.Activities.Presentation.EditingContext.Services%2A>, které je možné použít</span><span class="sxs-lookup"><span data-stu-id="080b3-104">exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="080b3-105">Kolekce položek</span><span class="sxs-lookup"><span data-stu-id="080b3-105">The Items collection</span></span>  
 <span data-ttu-id="080b3-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekce slouží k přístupu k data, jež jsou sdílena mezi hostitelem a návrháři nebo data, která je k dispozici pro všechny návrháře.</span><span class="sxs-lookup"><span data-stu-id="080b3-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="080b3-107">Tato kolekce má následující možnosti, získávat přístup <xref:System.Activities.Presentation.ContextItemManager> třídy:</span><span class="sxs-lookup"><span data-stu-id="080b3-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="080b3-108">Kolekce služeb</span><span class="sxs-lookup"><span data-stu-id="080b3-108">The Services collection</span></span>  
 <span data-ttu-id="080b3-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekce slouží k přístupu k službám, které Návrhář používá k interakci s hostitelem nebo služby, které používají všechny návrháře.</span><span class="sxs-lookup"><span data-stu-id="080b3-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="080b3-110">Tato kolekce má následující metody ze Poznámka:</span><span class="sxs-lookup"><span data-stu-id="080b3-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="080b3-111">Přiřazení návrháře aktivity</span><span class="sxs-lookup"><span data-stu-id="080b3-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="080b3-112">K určení, které Návrhář aktivita používá, se používá atribut návrháře.</span><span class="sxs-lookup"><span data-stu-id="080b3-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="080b3-113">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="080b3-113">Creating a service</span></span>  
 <span data-ttu-id="080b3-114">Pokud chcete vytvořit službu, která slouží jako kanál informací mezi návrháři a hostitele, musíte vytvořit rozhraní a implementaci.</span><span class="sxs-lookup"><span data-stu-id="080b3-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="080b3-115">Rozhraní používá <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metoda k definování členů služby a provádění obsahuje logiku pro službu.</span><span class="sxs-lookup"><span data-stu-id="080b3-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="080b3-116">V následujícím příkladu kódu se vytvoří služba rozhraní a implementaci.</span><span class="sxs-lookup"><span data-stu-id="080b3-116">In the following code example, a service interface and implementation are created.</span></span>  
  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="080b3-117">Publikování služby</span><span class="sxs-lookup"><span data-stu-id="080b3-117">Publishing a service</span></span>  
 <span data-ttu-id="080b3-118">Pro návrháře k využívání služby, je třeba nejprve ji publikovat pomocí hostitele <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="080b3-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="080b3-119">K odběru služby</span><span class="sxs-lookup"><span data-stu-id="080b3-119">Subscribing to a service</span></span>  
 <span data-ttu-id="080b3-120">Návrhář získává přístup pomocí služby <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metoda ve <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="080b3-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="080b3-121">Následující fragment kódu ukazuje, jak se k odběru služby.</span><span class="sxs-lookup"><span data-stu-id="080b3-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="080b3-122">Sdílení dat s využitím kolekce položek</span><span class="sxs-lookup"><span data-stu-id="080b3-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="080b3-123">Pomocí položky kolekce je podobný pomocí kolekce služeb, s výjimkou, že <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> se používá namísto publikovat.</span><span class="sxs-lookup"><span data-stu-id="080b3-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="080b3-124">Tato kolekce je vhodnější pro sdílení jednoduché dat mezi návrháři a hostitele, spíše než komplexní funkce.</span><span class="sxs-lookup"><span data-stu-id="080b3-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="080b3-125">EditingContext hostitelských položek a služby</span><span class="sxs-lookup"><span data-stu-id="080b3-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="080b3-126">Rozhraní .NET Framework poskytuje řadu předdefinovaných zboží a služeb prostřednictvím kontext úprav.</span><span class="sxs-lookup"><span data-stu-id="080b3-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="080b3-127">Položky:</span><span class="sxs-lookup"><span data-stu-id="080b3-127">Items:</span></span>  
  
-   <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem><span data-ttu-id="080b3-128">: Slouží ke správě seznamu odkazovaných místní sestavení, které budou použity v pracovním postupu pro ovládací prvky (jako je například editor výrazů).</span><span class="sxs-lookup"><span data-stu-id="080b3-128">: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
-   <xref:System.Activities.Presentation.Hosting.ReadOnlyState><span data-ttu-id="080b3-129">: Označuje, zda návrháře je ve stavu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="080b3-129">: Indicates whether the designer is in a read-only state.</span></span>  
  
-   <xref:System.Activities.Presentation.View.Selection><span data-ttu-id="080b3-130">: Definuje kolekci objektů, které jsou aktuálně vybrány.</span><span class="sxs-lookup"><span data-stu-id="080b3-130">: Defines the collection of objects that are currently selected.</span></span>  
  
-   <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem><span data-ttu-id="080b3-131">:</span><span class="sxs-lookup"><span data-stu-id="080b3-131">:</span></span>  
  
-   <xref:System.Activities.Presentation.WorkflowFileItem><span data-ttu-id="080b3-132">: Obsahuje informace o souboru, který je na základě aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="080b3-132">: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="080b3-133">Služby:</span><span class="sxs-lookup"><span data-stu-id="080b3-133">Services:</span></span>  
  
-   <xref:System.Activities.Presentation.Model.AttachedPropertiesService><span data-ttu-id="080b3-134">: Umožňuje vlastnosti, které chcete přidat do aktuální instance pomocí <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="080b3-134">: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
-   <xref:System.Activities.Presentation.View.DesignerView><span data-ttu-id="080b3-135">: Umožňuje přístup k vlastnostem plátna návrháře.</span><span class="sxs-lookup"><span data-stu-id="080b3-135">: Allows access to the properties of the designer canvas.</span></span>  
  
-   <xref:System.Activities.Presentation.IActivityToolboxService><span data-ttu-id="080b3-136">: Umožňuje obsah na panelu nástrojů na aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="080b3-136">: Allows the contents of the toolbox to be updated.</span></span>  
  
-   <xref:System.Activities.Presentation.Hosting.ICommandService><span data-ttu-id="080b3-137">: Používají k integraci s implementací služby poskytované vlastní příkazy návrháře (jako je kontextová nabídka).</span><span class="sxs-lookup"><span data-stu-id="080b3-137">: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
-   <xref:System.Activities.Presentation.Debug.IDesignerDebugView><span data-ttu-id="080b3-138">: Poskytuje funkce pro návrháře ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="080b3-138">: Provides functionality for the designer debugger.</span></span>  
  
-   <xref:System.Activities.Presentation.View.IExpressionEditorService><span data-ttu-id="080b3-139">: Poskytuje přístup do dialogového okna editoru výrazů.</span><span class="sxs-lookup"><span data-stu-id="080b3-139">: Provides access to the Expression Editor dialog.</span></span>  
  
-   <xref:System.Activities.Presentation.IIntegratedHelpService><span data-ttu-id="080b3-140">: Poskytuje funkce integrovaná Nápověda Návrháře.</span><span class="sxs-lookup"><span data-stu-id="080b3-140">: Provides the designer with integrated help functionality.</span></span>  
  
-   <xref:System.Activities.Presentation.Validation.IValidationErrorService><span data-ttu-id="080b3-141">: Poskytuje přístup k chybám ověření pomocí <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="080b3-141">: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
-   <xref:System.Activities.Presentation.IWorkflowDesignerStorageService><span data-ttu-id="080b3-142">: Poskytuje interní služba ukládat a načítat data.</span><span class="sxs-lookup"><span data-stu-id="080b3-142">: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="080b3-143">Tato služba používá se interně pomocí rozhraní .NET Framework a není určena pro externí použití.</span><span class="sxs-lookup"><span data-stu-id="080b3-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
-   <xref:System.Activities.Presentation.IXamlLoadErrorService><span data-ttu-id="080b3-144">: Poskytuje přístup k XAML zatížení chybu kolekce pomocí <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="080b3-144">: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
-   <xref:System.Activities.Presentation.Services.ModelService><span data-ttu-id="080b3-145">: Návrhář se používají k interakci s modelem pracovního postupu, který právě upravujete.</span><span class="sxs-lookup"><span data-stu-id="080b3-145">: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
-   <xref:System.Activities.Presentation.Model.ModelTreeManager><span data-ttu-id="080b3-146">: Poskytuje přístup do kořenového adresáře pomocí stromu modelu položky <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="080b3-146">: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
-   <xref:System.Activities.Presentation.UndoEngine><span data-ttu-id="080b3-147">: Poskytuje vrácení zpět a znovu funkce.</span><span class="sxs-lookup"><span data-stu-id="080b3-147">: Provides undo and redo functionality.</span></span>  
  
-   <xref:System.Activities.Presentation.Services.ViewService><span data-ttu-id="080b3-148">: Vizuální prvky Maps na základní položky modelu.</span><span class="sxs-lookup"><span data-stu-id="080b3-148">: Maps visual elements to underlying model items.</span></span>  
  
-   <xref:System.Activities.Presentation.View.ViewStateService><span data-ttu-id="080b3-149">: Úložiště zobrazit stavy položky modelu.</span><span class="sxs-lookup"><span data-stu-id="080b3-149">: Stores view states for model items.</span></span>  
  
-   <xref:System.Activities.Presentation.View.VirtualizedContainerService><span data-ttu-id="080b3-150">: Použít k přizpůsobení chování virtuální kontejner uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="080b3-150">: Used to customize the virtual container UI behavior.</span></span>  
  
-   <xref:System.Activities.Presentation.Hosting.WindowHelperService><span data-ttu-id="080b3-151">: Umožňuje vytvářet a rušit registraci delegáty pro oznámení události.</span><span class="sxs-lookup"><span data-stu-id="080b3-151">: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="080b3-152">Také umožňuje vlastníkovi okna nastavení.</span><span class="sxs-lookup"><span data-stu-id="080b3-152">Also allows a window owner to be set.</span></span>
