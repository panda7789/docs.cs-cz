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
# <a name="using-the-modelitem-editing-context"></a>Použití kontextu úprav ModelItem
Kontext <xref:System.Activities.Presentation.Model.ModelItem> úprav je objekt, který hostitelská aplikace používá ke komunikaci s návrhářem. <xref:System.Activities.Presentation.EditingContext>zpřístupňuje dvě metody <xref:System.Activities.Presentation.EditingContext.Items%2A> , <xref:System.Activities.Presentation.EditingContext.Services%2A>a, které se dají použít.  
  
## <a name="the-items-collection"></a>Kolekce Items  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekce se používá pro přístup k datům, která jsou sdílena mezi hostitelem a návrhářem, nebo daty, která jsou k dispozici pro všechny návrháře. Tato kolekce má následující možnosti, ke kterým se přistupoval prostřednictvím <xref:System.Activities.Presentation.ContextItemManager> třídy:  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Kolekce služeb  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekce se používá pro přístup ke službám, které Návrhář používá pro interakci s hostitelem, nebo služeb, které používají všichni návrháři. Tato kolekce má následující metody:  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Přiřazení aktivity návrháře  
 Pro určení návrháře, který aktivita používá, se použije atribut Designer.  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a>Vytvoření služby  
 Chcete-li vytvořit službu, která slouží jako informační potrubí mezi návrhářem a hostitelem, musí být vytvořeno rozhraní a implementace. Rozhraní používá <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metoda k definování členů služby a implementace obsahuje logiku pro službu. V následujícím příkladu kódu se vytvoří rozhraní služby a implementace.  
  
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
  
## <a name="publishing-a-service"></a>Publikování služby  
 Aby mohl Návrhář využívat službu, musí být nejprve publikován hostitelem pomocí <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Přihlášení k odběru služby  
 Návrhář získá přístup ke službě pomocí <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metody <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> v metodě. Následující fragment kódu ukazuje, jak se přihlásit k odběru služby.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Sdílení dat pomocí kolekce Items  
 Použití kolekce Items je podobné jako při použití kolekce Services, s výjimkou toho, že <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> se používá místo publikovat. Tato kolekce je vhodnější pro sdílení jednoduchých dat mezi návrháři a hostitelem, nikoli složité funkce.  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext položky a služby hostitele  
 .NET Framework poskytuje řadu integrovaných položek a služeb, které jsou k dispozici prostřednictvím kontextu úprav.  
  
 Položek  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Spravuje seznam odkazovaných místních sestavení, která budou použita v pracovním postupu pro ovládací prvky (například editor výrazů).  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Určuje, zda je Návrhář ve stavu jen pro čtení.  
  
- <xref:System.Activities.Presentation.View.Selection>: Definuje kolekci objektů, které jsou aktuálně vybrány.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>: Poskytuje informace o souboru, na kterém je založena aktuální relace úprav.  
  
 Orgány  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umožňuje přidat do aktuální instance vlastnosti pomocí <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.  
  
- <xref:System.Activities.Presentation.View.DesignerView>: Umožňuje přístup k vlastnostem plátna návrháře.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>: Umožňuje aktualizovat obsah sady nástrojů.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>: Slouží k integraci příkazů návrháře (například kontextové nabídky) s vlastními implementacemi služby.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Poskytuje funkce pro ladicí program návrháře.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>: Poskytuje přístup k dialogovému oknu Editor výrazů.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>: Poskytuje návrháře s integrovanými funkcemi pro podporu.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Poskytuje přístup k chybám ověřování <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>pomocí.  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Poskytuje interní službu pro ukládání a načítání dat. Tato služba se interně používá .NET Framework a není určená pro externí použití.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>: Poskytuje přístup ke kolekci chyb načtení XAML pomocí <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.  
  
- <xref:System.Activities.Presentation.Services.ModelService>: Používáno návrhářem pro interakci s modelem upravovaného pracovního postupu.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>: Poskytuje přístup ke kořenu stromu položky modelu pomocí <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
- <xref:System.Activities.Presentation.UndoEngine>: Poskytuje funkce vrácení zpět a opětovného provedení.  
  
- <xref:System.Activities.Presentation.Services.ViewService>: Mapuje vizuální prvky na podkladové položky modelu.  
  
- <xref:System.Activities.Presentation.View.ViewStateService>: Ukládá stavy zobrazení pro položky modelu.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Slouží k přizpůsobení chování uživatelského rozhraní virtuálního kontejneru.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Slouží k registraci a zrušení registrace delegátů pro oznamování událostí. Umožňuje také nastavit vlastníka okna.
