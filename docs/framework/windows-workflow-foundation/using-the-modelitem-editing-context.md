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
# <a name="using-the-modelitem-editing-context"></a>Použití kontextu úprav ModelItem
Kontext <xref:System.Activities.Presentation.Model.ModelItem> úprav je objekt, který hostitelská aplikace používá ke komunikaci s návrhářem. <xref:System.Activities.Presentation.EditingContext>poskytuje dvě <xref:System.Activities.Presentation.EditingContext.Items%2A> metody, <xref:System.Activities.Presentation.EditingContext.Services%2A>a , které mohou být použity  
  
## <a name="the-items-collection"></a>Kolekce položek  
 Kolekce <xref:System.Activities.Presentation.EditingContext.Items%2A> se používá pro přístup k datům, která je sdílena mezi hostitelem a návrháře nebo data, která je k dispozici pro všechny návrháře. Tato kolekce má následující možnosti, <xref:System.Activities.Presentation.ContextItemManager> přístupné prostřednictvím třídy:  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Kolekce Služeb  
 Kolekce <xref:System.Activities.Presentation.EditingContext.Services%2A> se používá pro přístup ke službám, které návrhář používá k interakci s hostitelem nebo služby, které používají všichni návrháři. Tato kolekce má následující metody poznámky:  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Přiřazení návrháře k aktivitě  
 Chcete-li určit, který návrhář aktivita používá, atribut Designer se používá.  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a>Vytvoření služby  
 Chcete-li vytvořit službu, která slouží jako potrubí informací mezi návrhářem a hostitelem, musí být vytvořeno rozhraní a implementace. Rozhraní se používá <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metodou k definování členů služby a implementace obsahuje logiku pro službu. V následujícím příkladu kódu jsou vytvořeny rozhraní služby a implementace.  
  
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
 Pro návrháře využívat službu, musí být nejprve publikovánhostitelem pomocí <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Přihlášení ke službě  
 Návrhář získá přístup ke službě <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> pomocí metody <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> v metodě. Následující fragment kódu ukazuje, jak se přihlásit k odběru služby.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Sdílení dat pomocí kolekce položek  
 Použití Items kolekce je podobný použití services <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> kolekce, s tím rozdílem, který se používá místo Publish. Tato kolekce je vhodnější pro sdílení jednoduchých dat mezi návrháři a hostitele, spíše než složité funkce.  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext hostitelské položky a služby  
 Rozhraní .NET Framework poskytuje řadu předdefinovaných položek a služeb, ke kterým se přistupuje prostřednictvím kontextu úprav.  
  
 Položky:  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Spravuje seznam odkazovaných místních sestavení, která budou použita uvnitř pracovního postupu pro ovládací prvky (například editor výrazů).  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Označuje, zda je návrhář ve stavu jen pro čtení.  
  
- <xref:System.Activities.Presentation.View.Selection>: Definuje kolekci objektů, které jsou aktuálně vybrány.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>: Obsahuje informace o souboru, na který je založena aktuální relace úprav.  
  
 Služby:  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umožňuje přidání vlastností do aktuální <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>instance pomocí .  
  
- <xref:System.Activities.Presentation.View.DesignerView>: Umožňuje přístup k vlastnostem plátna návrháře.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>: Umožňuje aktualizovat obsah panelu nástrojů.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>: Používá se k integraci příkazů návrháře (například kontextové nabídky) s implementacemi služby poskytované vlastními nastaveními.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Poskytuje funkce pro ladicí program návrháře.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>: Poskytuje přístup k dialogovému oknu Editor výrazů.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>: Poskytuje návrháři integrované funkce nápovědy.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Poskytuje přístup k <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>chybám ověření pomocí aplikace .  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Poskytuje interní službu pro ukládání a načítání dat. Tato služba je interně používána rozhraním .NET Framework a není určena pro externí použití.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>: Poskytuje přístup ke shromažďování chyb <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>zatížení XAML pomocí .  
  
- <xref:System.Activities.Presentation.Services.ModelService>: Používá návrhář e-li interakci s modelem upravovaného pracovního postupu.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>: Poskytuje přístup ke kořenovému adresáři stromu položek modelu pomocí <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
- <xref:System.Activities.Presentation.UndoEngine>: Poskytuje funkce vrátit a znovu.  
  
- <xref:System.Activities.Presentation.Services.ViewService>: Mapuje vizuální prvky na podkladové položky modelu.  
  
- <xref:System.Activities.Presentation.View.ViewStateService>: Ukládá stavy zobrazení pro položky modelu.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Slouží k přizpůsobení chování virtuálního kontejneru ui.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Slouží k registraci a zrušení registrace delegátů pro oznámení událostí. Také umožňuje nastavit vlastníka okna.
