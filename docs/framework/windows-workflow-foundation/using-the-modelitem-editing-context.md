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
# <a name="using-the-modelitem-editing-context"></a>Pomocí typem ModelItem úpravy kontextu
<xref:System.Activities.Presentation.Model.ModelItem> Úpravy kontextu je objekt, který aplikace hostitele používá ke komunikaci pomocí návrháře. <xref:System.Activities.Presentation.EditingContext>poskytuje dvě metody, <xref:System.Activities.Presentation.EditingContext.Items%2A> a <xref:System.Activities.Presentation.EditingContext.Services%2A>, který může být použit  
  
## <a name="the-items-collection"></a>Kolekce položek  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekce slouží pro přístup k data, která jsou sdílena mezi hostiteli a návrháře nebo data, která je k dispozici pro všechny Designer. Tato kolekce má následující možnosti, přístup prostřednictvím <xref:System.Activities.Presentation.ContextItemManager> třídy:  
  
1.  <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2.  <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Kolekce služeb  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekce slouží k přístupu služby, které návrháře používá k interakci s hostitelem nebo služby, které používají všechny Designer. Tato kolekce nemá tyto metody Poznámka:  
  
1.  <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2.  <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Přiřazení Návrhář aktivity  
 Chcete-li určit, které Návrhář aktivita používá, se používá atributu Designer.  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a>Vytvoření služby  
 Pokud chcete vytvořit službu, která slouží jako kanál informací mezi designer a hostitele, musí být vytvořeny rozhraní a implementace. Rozhraní používá <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metoda k definování členů služby a implementaci obsahuje logiku pro službu. V následujícím příkladu kódu rozhraní služby a implementace vytvoří.  
  
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
  
## <a name="publishing-a-service"></a>Publikování služby  
 Pro Návrhář využívat službu, je třeba nejprve ji publikovat hostitele pomocí <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metoda.  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>K odběru služby  
 Návrhář získává přístup pomocí služby <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metoda v <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metoda. Následující fragment kódu ukazuje, jak k odběru služby.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Sdílení dat pomocí položky kolekce  
 Pomocí položky kolekce je podobná pomocí kolekce služeb, vyjma toho, že <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> se používá namísto publikovat. Tato kolekce je vhodnější pro sdílení jednoduché datové mezi návrháři a na hostitele, nikoli komplexní funkce.  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext hostitelských položek a služby  
 .Net Framework poskytuje řadu předdefinovaných položky a služby přistupovat prostřednictvím úprav kontextu.  
  
 Položky:  
  
-   <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Spravuje seznam odkazovaná místní sestavení, které budou použity uvnitř pracovního postupu pro ovládací prvky (jako je například editor výrazu).  
  
-   <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Určuje, zda návrháře je ve stavu jen pro čtení.  
  
-   <xref:System.Activities.Presentation.View.Selection>: Definuje kolekci objektů, které jsou aktuálně vybrané.  
  
-   <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
-   <xref:System.Activities.Presentation.WorkflowFileItem>: Poskytuje informace o souboru, který je na základě aktuální relaci.  
  
 Služba:  
  
-   <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umožňuje vlastnosti, které chcete přidat do aktuální instance pomocí <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.  
  
-   <xref:System.Activities.Presentation.View.DesignerView>: Umožňuje přístup k vlastnosti plátna návrháře.  
  
-   <xref:System.Activities.Presentation.IActivityToolboxService>: Umožňuje obsah sady nástrojů aktualizovat.  
  
-   <xref:System.Activities.Presentation.Hosting.ICommandService>: Umožňuje integraci s implementací služby poskytované vlastní návrháře příkazy (například Kontextová nabídka).  
  
-   <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Poskytuje funkce pro návrháře ladicí program.  
  
-   <xref:System.Activities.Presentation.View.IExpressionEditorService>: Poskytuje přístup k dialogu Editor výrazů.  
  
-   <xref:System.Activities.Presentation.IIntegratedHelpService>: Poskytuje návrháře funkce integrované nápovědy.  
  
-   <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Poskytuje přístup k chyby ověření pomocí <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.  
  
-   <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Poskytuje interní služby k ukládání a načítání dat. Tato služba používá se interně pomocí rozhraní .net Framework a není určena pro externí použití.  
  
-   <xref:System.Activities.Presentation.IXamlLoadErrorService>: Poskytuje přístup na pomocí kolekce XAML zatížení chyba <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.  
  
-   <xref:System.Activities.Presentation.Services.ModelService>: Používají návrháři k interakci s modelem upravovaný pracovního postupu.  
  
-   <xref:System.Activities.Presentation.Model.ModelTreeManager>: Poskytuje přístup ke kořenu stromu položky modelu pomocí <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
-   <xref:System.Activities.Presentation.UndoEngine>: Poskytuje vrácení zpět a vrátit funkce.  
  
-   <xref:System.Activities.Presentation.Services.ViewService>: Mapuje vizuální prvky základní položky modelu.  
  
-   <xref:System.Activities.Presentation.View.ViewStateService>: Úložiště zobrazit stavy položky modelu.  
  
-   <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Použít k přizpůsobení chování uživatelského rozhraní virtuální kontejneru.  
  
-   <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Používá k registraci a zrušit registraci delegáty pro oznamování událostí. Také umožňuje nastavit vlastníka a okna.
