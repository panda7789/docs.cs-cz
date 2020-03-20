---
title: Použití kontextu úprav ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: e1481d96e39f837d72834222d2839c520e880cc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142511"
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="181ff-102">Použití kontextu úprav ModelItem</span><span class="sxs-lookup"><span data-stu-id="181ff-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="181ff-103">Kontext <xref:System.Activities.Presentation.Model.ModelItem> úprav je objekt, který hostitelská aplikace používá ke komunikaci s návrhářem.</span><span class="sxs-lookup"><span data-stu-id="181ff-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="181ff-104"><xref:System.Activities.Presentation.EditingContext>poskytuje dvě <xref:System.Activities.Presentation.EditingContext.Items%2A> metody, <xref:System.Activities.Presentation.EditingContext.Services%2A>a , které mohou být použity</span><span class="sxs-lookup"><span data-stu-id="181ff-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="181ff-105">Kolekce položek</span><span class="sxs-lookup"><span data-stu-id="181ff-105">The Items collection</span></span>  
 <span data-ttu-id="181ff-106">Kolekce <xref:System.Activities.Presentation.EditingContext.Items%2A> se používá pro přístup k datům, která je sdílena mezi hostitelem a návrháře nebo data, která je k dispozici pro všechny návrháře.</span><span class="sxs-lookup"><span data-stu-id="181ff-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="181ff-107">Tato kolekce má následující možnosti, <xref:System.Activities.Presentation.ContextItemManager> přístupné prostřednictvím třídy:</span><span class="sxs-lookup"><span data-stu-id="181ff-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="181ff-108">Kolekce Služeb</span><span class="sxs-lookup"><span data-stu-id="181ff-108">The Services collection</span></span>  
 <span data-ttu-id="181ff-109">Kolekce <xref:System.Activities.Presentation.EditingContext.Services%2A> se používá pro přístup ke službám, které návrhář používá k interakci s hostitelem nebo služby, které používají všichni návrháři.</span><span class="sxs-lookup"><span data-stu-id="181ff-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="181ff-110">Tato kolekce má následující metody poznámky:</span><span class="sxs-lookup"><span data-stu-id="181ff-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="181ff-111">Přiřazení návrháře k aktivitě</span><span class="sxs-lookup"><span data-stu-id="181ff-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="181ff-112">Chcete-li určit, který návrhář aktivita používá, atribut Designer se používá.</span><span class="sxs-lookup"><span data-stu-id="181ff-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="181ff-113">Vytvoření služby</span><span class="sxs-lookup"><span data-stu-id="181ff-113">Creating a service</span></span>  
 <span data-ttu-id="181ff-114">Chcete-li vytvořit službu, která slouží jako potrubí informací mezi návrhářem a hostitelem, musí být vytvořeno rozhraní a implementace.</span><span class="sxs-lookup"><span data-stu-id="181ff-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="181ff-115">Rozhraní se používá <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metodou k definování členů služby a implementace obsahuje logiku pro službu.</span><span class="sxs-lookup"><span data-stu-id="181ff-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="181ff-116">V následujícím příkladu kódu jsou vytvořeny rozhraní služby a implementace.</span><span class="sxs-lookup"><span data-stu-id="181ff-116">In the following code example, a service interface and implementation are created.</span></span>  
  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="181ff-117">Publikování služby</span><span class="sxs-lookup"><span data-stu-id="181ff-117">Publishing a service</span></span>  
 <span data-ttu-id="181ff-118">Pro návrháře využívat službu, musí být nejprve publikovánhostitelem pomocí <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="181ff-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="181ff-119">Přihlášení ke službě</span><span class="sxs-lookup"><span data-stu-id="181ff-119">Subscribing to a service</span></span>  
 <span data-ttu-id="181ff-120">Návrhář získá přístup ke službě <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> pomocí metody <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> v metodě.</span><span class="sxs-lookup"><span data-stu-id="181ff-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="181ff-121">Následující fragment kódu ukazuje, jak se přihlásit k odběru služby.</span><span class="sxs-lookup"><span data-stu-id="181ff-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="181ff-122">Sdílení dat pomocí kolekce položek</span><span class="sxs-lookup"><span data-stu-id="181ff-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="181ff-123">Použití Items kolekce je podobný použití services <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> kolekce, s tím rozdílem, který se používá místo Publish.</span><span class="sxs-lookup"><span data-stu-id="181ff-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="181ff-124">Tato kolekce je vhodnější pro sdílení jednoduchých dat mezi návrháři a hostitele, spíše než složité funkce.</span><span class="sxs-lookup"><span data-stu-id="181ff-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="181ff-125">EditingContext hostitelské položky a služby</span><span class="sxs-lookup"><span data-stu-id="181ff-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="181ff-126">Rozhraní .NET Framework poskytuje řadu předdefinovaných položek a služeb, ke kterým se přistupuje prostřednictvím kontextu úprav.</span><span class="sxs-lookup"><span data-stu-id="181ff-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="181ff-127">Položky:</span><span class="sxs-lookup"><span data-stu-id="181ff-127">Items:</span></span>  
  
- <span data-ttu-id="181ff-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Spravuje seznam odkazovaných místních sestavení, která budou použita uvnitř pracovního postupu pro ovládací prvky (například editor výrazů).</span><span class="sxs-lookup"><span data-stu-id="181ff-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="181ff-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Označuje, zda je návrhář ve stavu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="181ff-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="181ff-130"><xref:System.Activities.Presentation.View.Selection>: Definuje kolekci objektů, které jsou aktuálně vybrány.</span><span class="sxs-lookup"><span data-stu-id="181ff-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="181ff-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="181ff-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="181ff-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Obsahuje informace o souboru, na který je založena aktuální relace úprav.</span><span class="sxs-lookup"><span data-stu-id="181ff-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="181ff-133">Služby:</span><span class="sxs-lookup"><span data-stu-id="181ff-133">Services:</span></span>  
  
- <span data-ttu-id="181ff-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umožňuje přidání vlastností do aktuální <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>instance pomocí .</span><span class="sxs-lookup"><span data-stu-id="181ff-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="181ff-135"><xref:System.Activities.Presentation.View.DesignerView>: Umožňuje přístup k vlastnostem plátna návrháře.</span><span class="sxs-lookup"><span data-stu-id="181ff-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="181ff-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Umožňuje aktualizovat obsah panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="181ff-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="181ff-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Používá se k integraci příkazů návrháře (například kontextové nabídky) s implementacemi služby poskytované vlastními nastaveními.</span><span class="sxs-lookup"><span data-stu-id="181ff-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="181ff-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Poskytuje funkce pro ladicí program návrháře.</span><span class="sxs-lookup"><span data-stu-id="181ff-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="181ff-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Poskytuje přístup k dialogovému oknu Editor výrazů.</span><span class="sxs-lookup"><span data-stu-id="181ff-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="181ff-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Poskytuje návrháři integrované funkce nápovědy.</span><span class="sxs-lookup"><span data-stu-id="181ff-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="181ff-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Poskytuje přístup k <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>chybám ověření pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="181ff-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="181ff-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Poskytuje interní službu pro ukládání a načítání dat.</span><span class="sxs-lookup"><span data-stu-id="181ff-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="181ff-143">Tato služba je interně používána rozhraním .NET Framework a není určena pro externí použití.</span><span class="sxs-lookup"><span data-stu-id="181ff-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="181ff-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Poskytuje přístup ke shromažďování chyb <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>zatížení XAML pomocí .</span><span class="sxs-lookup"><span data-stu-id="181ff-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="181ff-145"><xref:System.Activities.Presentation.Services.ModelService>: Používá návrhář e-li interakci s modelem upravovaného pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="181ff-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="181ff-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Poskytuje přístup ke kořenovému adresáři stromu položek modelu pomocí <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span><span class="sxs-lookup"><span data-stu-id="181ff-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="181ff-147"><xref:System.Activities.Presentation.UndoEngine>: Poskytuje funkce vrátit a znovu.</span><span class="sxs-lookup"><span data-stu-id="181ff-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="181ff-148"><xref:System.Activities.Presentation.Services.ViewService>: Mapuje vizuální prvky na podkladové položky modelu.</span><span class="sxs-lookup"><span data-stu-id="181ff-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="181ff-149"><xref:System.Activities.Presentation.View.ViewStateService>: Ukládá stavy zobrazení pro položky modelu.</span><span class="sxs-lookup"><span data-stu-id="181ff-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="181ff-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Slouží k přizpůsobení chování virtuálního kontejneru ui.</span><span class="sxs-lookup"><span data-stu-id="181ff-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="181ff-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Slouží k registraci a zrušení registrace delegátů pro oznámení událostí.</span><span class="sxs-lookup"><span data-stu-id="181ff-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="181ff-152">Také umožňuje nastavit vlastníka okna.</span><span class="sxs-lookup"><span data-stu-id="181ff-152">Also allows a window owner to be set.</span></span>
