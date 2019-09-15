---
title: Použití kontextu úprav ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a47cb53e50d221c0ae07cf0841688fe4f8ced7d4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988924"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="8e378-102">Použití kontextu úprav ModelItem</span><span class="sxs-lookup"><span data-stu-id="8e378-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="8e378-103">Kontext <xref:System.Activities.Presentation.Model.ModelItem> úprav je objekt, který hostitelská aplikace používá ke komunikaci s návrhářem.</span><span class="sxs-lookup"><span data-stu-id="8e378-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="8e378-104"><xref:System.Activities.Presentation.EditingContext>zpřístupňuje dvě metody <xref:System.Activities.Presentation.EditingContext.Items%2A> , <xref:System.Activities.Presentation.EditingContext.Services%2A>a, které se dají použít.</span><span class="sxs-lookup"><span data-stu-id="8e378-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="8e378-105">Kolekce Items</span><span class="sxs-lookup"><span data-stu-id="8e378-105">The Items collection</span></span>  
 <span data-ttu-id="8e378-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekce se používá pro přístup k datům, která jsou sdílena mezi hostitelem a návrhářem, nebo daty, která jsou k dispozici pro všechny návrháře.</span><span class="sxs-lookup"><span data-stu-id="8e378-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="8e378-107">Tato kolekce má následující možnosti, ke kterým se přistupoval prostřednictvím <xref:System.Activities.Presentation.ContextItemManager> třídy:</span><span class="sxs-lookup"><span data-stu-id="8e378-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="8e378-108">Kolekce služeb</span><span class="sxs-lookup"><span data-stu-id="8e378-108">The Services collection</span></span>  
 <span data-ttu-id="8e378-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekce se používá pro přístup ke službám, které Návrhář používá pro interakci s hostitelem, nebo služeb, které používají všichni návrháři.</span><span class="sxs-lookup"><span data-stu-id="8e378-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="8e378-110">Tato kolekce má následující metody:</span><span class="sxs-lookup"><span data-stu-id="8e378-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="8e378-111">Přiřazení aktivity návrháře</span><span class="sxs-lookup"><span data-stu-id="8e378-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="8e378-112">Pro určení návrháře, který aktivita používá, se použije atribut Designer.</span><span class="sxs-lookup"><span data-stu-id="8e378-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="8e378-113">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="8e378-113">Creating a service</span></span>  
 <span data-ttu-id="8e378-114">Chcete-li vytvořit službu, která slouží jako informační potrubí mezi návrhářem a hostitelem, musí být vytvořeno rozhraní a implementace.</span><span class="sxs-lookup"><span data-stu-id="8e378-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="8e378-115">Rozhraní používá <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metoda k definování členů služby a implementace obsahuje logiku pro službu.</span><span class="sxs-lookup"><span data-stu-id="8e378-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="8e378-116">V následujícím příkladu kódu se vytvoří rozhraní služby a implementace.</span><span class="sxs-lookup"><span data-stu-id="8e378-116">In the following code example, a service interface and implementation are created.</span></span>  
  
```csharp  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="8e378-117">Publikování služby</span><span class="sxs-lookup"><span data-stu-id="8e378-117">Publishing a service</span></span>  
 <span data-ttu-id="8e378-118">Aby mohl Návrhář využívat službu, musí být nejprve publikován hostitelem pomocí <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8e378-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="8e378-119">Přihlášení k odběru služby</span><span class="sxs-lookup"><span data-stu-id="8e378-119">Subscribing to a service</span></span>  
 <span data-ttu-id="8e378-120">Návrhář získá přístup ke službě pomocí <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metody <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> v metodě.</span><span class="sxs-lookup"><span data-stu-id="8e378-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="8e378-121">Následující fragment kódu ukazuje, jak se přihlásit k odběru služby.</span><span class="sxs-lookup"><span data-stu-id="8e378-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
```csharp  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="8e378-122">Sdílení dat pomocí kolekce Items</span><span class="sxs-lookup"><span data-stu-id="8e378-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="8e378-123">Použití kolekce Items je podobné jako při použití kolekce Services, s výjimkou toho, že <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> se používá místo publikovat.</span><span class="sxs-lookup"><span data-stu-id="8e378-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="8e378-124">Tato kolekce je vhodnější pro sdílení jednoduchých dat mezi návrháři a hostitelem, nikoli složité funkce.</span><span class="sxs-lookup"><span data-stu-id="8e378-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="8e378-125">EditingContext položky a služby hostitele</span><span class="sxs-lookup"><span data-stu-id="8e378-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="8e378-126">.NET Framework poskytuje řadu integrovaných položek a služeb, které jsou k dispozici prostřednictvím kontextu úprav.</span><span class="sxs-lookup"><span data-stu-id="8e378-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="8e378-127">Položek</span><span class="sxs-lookup"><span data-stu-id="8e378-127">Items:</span></span>  
  
- <span data-ttu-id="8e378-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Spravuje seznam odkazovaných místních sestavení, která budou použita v pracovním postupu pro ovládací prvky (například editor výrazů).</span><span class="sxs-lookup"><span data-stu-id="8e378-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="8e378-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Určuje, zda je Návrhář ve stavu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="8e378-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="8e378-130"><xref:System.Activities.Presentation.View.Selection>: Definuje kolekci objektů, které jsou aktuálně vybrány.</span><span class="sxs-lookup"><span data-stu-id="8e378-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="8e378-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="8e378-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="8e378-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Poskytuje informace o souboru, na kterém je založena aktuální relace úprav.</span><span class="sxs-lookup"><span data-stu-id="8e378-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="8e378-133">Orgány</span><span class="sxs-lookup"><span data-stu-id="8e378-133">Services:</span></span>  
  
- <span data-ttu-id="8e378-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umožňuje přidat do aktuální instance vlastnosti pomocí <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e378-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="8e378-135"><xref:System.Activities.Presentation.View.DesignerView>: Umožňuje přístup k vlastnostem plátna návrháře.</span><span class="sxs-lookup"><span data-stu-id="8e378-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="8e378-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Umožňuje aktualizovat obsah sady nástrojů.</span><span class="sxs-lookup"><span data-stu-id="8e378-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="8e378-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Slouží k integraci příkazů návrháře (například kontextové nabídky) s vlastními implementacemi služby.</span><span class="sxs-lookup"><span data-stu-id="8e378-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="8e378-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Poskytuje funkce pro ladicí program návrháře.</span><span class="sxs-lookup"><span data-stu-id="8e378-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="8e378-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Poskytuje přístup k dialogovému oknu Editor výrazů.</span><span class="sxs-lookup"><span data-stu-id="8e378-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="8e378-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Poskytuje návrháře s integrovanými funkcemi pro podporu.</span><span class="sxs-lookup"><span data-stu-id="8e378-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="8e378-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Poskytuje přístup k chybám ověřování <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>pomocí.</span><span class="sxs-lookup"><span data-stu-id="8e378-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="8e378-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Poskytuje interní službu pro ukládání a načítání dat.</span><span class="sxs-lookup"><span data-stu-id="8e378-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="8e378-143">Tato služba se interně používá .NET Framework a není určená pro externí použití.</span><span class="sxs-lookup"><span data-stu-id="8e378-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="8e378-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Poskytuje přístup ke kolekci chyb načtení XAML pomocí <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e378-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="8e378-145"><xref:System.Activities.Presentation.Services.ModelService>: Používáno návrhářem pro interakci s modelem upravovaného pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8e378-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="8e378-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Poskytuje přístup ke kořenu stromu položky modelu pomocí <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e378-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="8e378-147"><xref:System.Activities.Presentation.UndoEngine>: Poskytuje funkce vrácení zpět a opětovného provedení.</span><span class="sxs-lookup"><span data-stu-id="8e378-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="8e378-148"><xref:System.Activities.Presentation.Services.ViewService>: Mapuje vizuální prvky na podkladové položky modelu.</span><span class="sxs-lookup"><span data-stu-id="8e378-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="8e378-149"><xref:System.Activities.Presentation.View.ViewStateService>: Ukládá stavy zobrazení pro položky modelu.</span><span class="sxs-lookup"><span data-stu-id="8e378-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="8e378-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Slouží k přizpůsobení chování uživatelského rozhraní virtuálního kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8e378-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="8e378-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Slouží k registraci a zrušení registrace delegátů pro oznamování událostí.</span><span class="sxs-lookup"><span data-stu-id="8e378-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="8e378-152">Umožňuje také nastavit vlastníka okna.</span><span class="sxs-lookup"><span data-stu-id="8e378-152">Also allows a window owner to be set.</span></span>
