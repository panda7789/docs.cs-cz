---
title: Použití kontextu úprav ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: 8b2f2b8d4c528de14ea8b37e4eda8190f1757c22
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664708"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="ee57c-102">Použití kontextu úprav ModelItem</span><span class="sxs-lookup"><span data-stu-id="ee57c-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="ee57c-103"><xref:System.Activities.Presentation.Model.ModelItem> Kontextu úprav je objekt, který hostitelská aplikace používá ke komunikaci s návrhářem.</span><span class="sxs-lookup"><span data-stu-id="ee57c-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="ee57c-104"><xref:System.Activities.Presentation.EditingContext> poskytuje dvě metody <xref:System.Activities.Presentation.EditingContext.Items%2A> a <xref:System.Activities.Presentation.EditingContext.Services%2A>, které je možné použít</span><span class="sxs-lookup"><span data-stu-id="ee57c-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="ee57c-105">Kolekce položek</span><span class="sxs-lookup"><span data-stu-id="ee57c-105">The Items collection</span></span>  
 <span data-ttu-id="ee57c-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekce slouží k přístupu k data, jež jsou sdílena mezi hostitelem a návrháři nebo data, která je k dispozici pro všechny návrháře.</span><span class="sxs-lookup"><span data-stu-id="ee57c-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="ee57c-107">Tato kolekce má následující možnosti, získávat přístup <xref:System.Activities.Presentation.ContextItemManager> třídy:</span><span class="sxs-lookup"><span data-stu-id="ee57c-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="ee57c-108">Kolekce služeb</span><span class="sxs-lookup"><span data-stu-id="ee57c-108">The Services collection</span></span>  
 <span data-ttu-id="ee57c-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekce slouží k přístupu k službám, které Návrhář používá k interakci s hostitelem nebo služby, které používají všechny návrháře.</span><span class="sxs-lookup"><span data-stu-id="ee57c-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="ee57c-110">Tato kolekce má následující metody ze Poznámka:</span><span class="sxs-lookup"><span data-stu-id="ee57c-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="ee57c-111">Přiřazení návrháře aktivity</span><span class="sxs-lookup"><span data-stu-id="ee57c-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="ee57c-112">K určení, které Návrhář aktivita používá, se používá atribut návrháře.</span><span class="sxs-lookup"><span data-stu-id="ee57c-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="ee57c-113">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="ee57c-113">Creating a service</span></span>  
 <span data-ttu-id="ee57c-114">Pokud chcete vytvořit službu, která slouží jako kanál informací mezi návrháři a hostitele, musíte vytvořit rozhraní a implementaci.</span><span class="sxs-lookup"><span data-stu-id="ee57c-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="ee57c-115">Rozhraní používá <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metoda k definování členů služby a provádění obsahuje logiku pro službu.</span><span class="sxs-lookup"><span data-stu-id="ee57c-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="ee57c-116">V následujícím příkladu kódu se vytvoří služba rozhraní a implementaci.</span><span class="sxs-lookup"><span data-stu-id="ee57c-116">In the following code example, a service interface and implementation are created.</span></span>  
  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="ee57c-117">Publikování služby</span><span class="sxs-lookup"><span data-stu-id="ee57c-117">Publishing a service</span></span>  
 <span data-ttu-id="ee57c-118">Pro návrháře k využívání služby, je třeba nejprve ji publikovat pomocí hostitele <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ee57c-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="ee57c-119">K odběru služby</span><span class="sxs-lookup"><span data-stu-id="ee57c-119">Subscribing to a service</span></span>  
 <span data-ttu-id="ee57c-120">Návrhář získává přístup pomocí služby <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metoda ve <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ee57c-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="ee57c-121">Následující fragment kódu ukazuje, jak se k odběru služby.</span><span class="sxs-lookup"><span data-stu-id="ee57c-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="ee57c-122">Sdílení dat s využitím kolekce položek</span><span class="sxs-lookup"><span data-stu-id="ee57c-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="ee57c-123">Pomocí položky kolekce je podobný pomocí kolekce služeb, s výjimkou, že <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> se používá namísto publikovat.</span><span class="sxs-lookup"><span data-stu-id="ee57c-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="ee57c-124">Tato kolekce je vhodnější pro sdílení jednoduché dat mezi návrháři a hostitele, spíše než komplexní funkce.</span><span class="sxs-lookup"><span data-stu-id="ee57c-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="ee57c-125">EditingContext hostitelských položek a služby</span><span class="sxs-lookup"><span data-stu-id="ee57c-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="ee57c-126">Rozhraní .NET Framework poskytuje řadu předdefinovaných zboží a služeb prostřednictvím kontext úprav.</span><span class="sxs-lookup"><span data-stu-id="ee57c-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="ee57c-127">Položky:</span><span class="sxs-lookup"><span data-stu-id="ee57c-127">Items:</span></span>  
  
- <span data-ttu-id="ee57c-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Slouží ke správě seznamu odkazovaných místní sestavení, které budou použity v pracovním postupu pro ovládací prvky (jako je například editor výrazů).</span><span class="sxs-lookup"><span data-stu-id="ee57c-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="ee57c-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Označuje, zda návrháře je ve stavu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="ee57c-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="ee57c-130"><xref:System.Activities.Presentation.View.Selection>: Definuje kolekci objektů, které jsou aktuálně vybrány.</span><span class="sxs-lookup"><span data-stu-id="ee57c-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="ee57c-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="ee57c-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="ee57c-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Obsahuje informace o souboru, který je na základě aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="ee57c-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="ee57c-133">Služby:</span><span class="sxs-lookup"><span data-stu-id="ee57c-133">Services:</span></span>  
  
- <span data-ttu-id="ee57c-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umožňuje vlastnosti, které chcete přidat do aktuální instance pomocí <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee57c-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="ee57c-135"><xref:System.Activities.Presentation.View.DesignerView>: Umožňuje přístup k vlastnostem plátna návrháře.</span><span class="sxs-lookup"><span data-stu-id="ee57c-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="ee57c-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Umožňuje obsah na panelu nástrojů na aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="ee57c-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="ee57c-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Používají k integraci s implementací služby poskytované vlastní příkazy návrháře (jako je kontextová nabídka).</span><span class="sxs-lookup"><span data-stu-id="ee57c-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="ee57c-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Poskytuje funkce pro návrháře ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="ee57c-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="ee57c-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Poskytuje přístup do dialogového okna editoru výrazů.</span><span class="sxs-lookup"><span data-stu-id="ee57c-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="ee57c-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Poskytuje funkce integrovaná Nápověda Návrháře.</span><span class="sxs-lookup"><span data-stu-id="ee57c-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="ee57c-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Poskytuje přístup k chybám ověření pomocí <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee57c-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="ee57c-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Poskytuje interní služba ukládat a načítat data.</span><span class="sxs-lookup"><span data-stu-id="ee57c-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="ee57c-143">Tato služba používá se interně pomocí rozhraní .NET Framework a není určena pro externí použití.</span><span class="sxs-lookup"><span data-stu-id="ee57c-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="ee57c-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Poskytuje přístup k XAML zatížení chybu kolekce pomocí <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee57c-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="ee57c-145"><xref:System.Activities.Presentation.Services.ModelService>: Návrhář se používají k interakci s modelem pracovního postupu, který právě upravujete.</span><span class="sxs-lookup"><span data-stu-id="ee57c-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="ee57c-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Poskytuje přístup do kořenového adresáře pomocí stromu modelu položky <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee57c-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="ee57c-147"><xref:System.Activities.Presentation.UndoEngine>: Poskytuje vrácení zpět a znovu funkce.</span><span class="sxs-lookup"><span data-stu-id="ee57c-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="ee57c-148"><xref:System.Activities.Presentation.Services.ViewService>: Vizuální prvky Maps na základní položky modelu.</span><span class="sxs-lookup"><span data-stu-id="ee57c-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="ee57c-149"><xref:System.Activities.Presentation.View.ViewStateService>: Úložiště zobrazit stavy položky modelu.</span><span class="sxs-lookup"><span data-stu-id="ee57c-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="ee57c-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Použít k přizpůsobení chování virtuální kontejner uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ee57c-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="ee57c-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Umožňuje vytvářet a rušit registraci delegáty pro oznámení události.</span><span class="sxs-lookup"><span data-stu-id="ee57c-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="ee57c-152">Také umožňuje vlastníkovi okna nastavení.</span><span class="sxs-lookup"><span data-stu-id="ee57c-152">Also allows a window owner to be set.</span></span>
