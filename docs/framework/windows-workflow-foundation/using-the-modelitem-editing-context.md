---
title: Použití kontextu úprav ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: d8d2e7d055099a6aedd13dd48dd78403cdff2a50
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57846269"
---
# <a name="using-the-modelitem-editing-context"></a>Použití kontextu úprav ModelItem
<xref:System.Activities.Presentation.Model.ModelItem> Kontextu úprav je objekt, který hostitelská aplikace používá ke komunikaci s návrhářem. <xref:System.Activities.Presentation.EditingContext> poskytuje dvě metody <xref:System.Activities.Presentation.EditingContext.Items%2A> a <xref:System.Activities.Presentation.EditingContext.Services%2A>, které je možné použít  
  
## <a name="the-items-collection"></a>Kolekce položek  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> Kolekce slouží k přístupu k data, jež jsou sdílena mezi hostitelem a návrháři nebo data, která je k dispozici pro všechny návrháře. Tato kolekce má následující možnosti, získávat přístup <xref:System.Activities.Presentation.ContextItemManager> třídy:  
  
1.  <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2.  <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Kolekce služeb  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> Kolekce slouží k přístupu k službám, které Návrhář používá k interakci s hostitelem nebo služby, které používají všechny návrháře. Tato kolekce má následující metody ze Poznámka:  
  
1.  <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2.  <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Přiřazení návrháře aktivity  
 K určení, které Návrhář aktivita používá, se používá atribut návrháře.  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a>Vytvoření služby  
 Pokud chcete vytvořit službu, která slouží jako kanál informací mezi návrháři a hostitele, musíte vytvořit rozhraní a implementaci. Rozhraní používá <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metoda k definování členů služby a provádění obsahuje logiku pro službu. V následujícím příkladu kódu se vytvoří služba rozhraní a implementaci.  
  
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
 Pro návrháře k využívání služby, je třeba nejprve ji publikovat pomocí hostitele <xref:System.Activities.Presentation.ServiceManager.Publish%2A> metody.  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>K odběru služby  
 Návrhář získává přístup pomocí služby <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> metoda ve <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> metoda. Následující fragment kódu ukazuje, jak se k odběru služby.  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>Sdílení dat s využitím kolekce položek  
 Pomocí položky kolekce je podobný pomocí kolekce služeb, s výjimkou, že <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> se používá namísto publikovat. Tato kolekce je vhodnější pro sdílení jednoduché dat mezi návrháři a hostitele, spíše než komplexní funkce.  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext hostitelských položek a služby  
 Rozhraní .NET Framework poskytuje řadu předdefinovaných zboží a služeb prostřednictvím kontext úprav.  
  
 Položky:  
  
-   <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Slouží ke správě seznamu odkazovaných místní sestavení, které budou použity v pracovním postupu pro ovládací prvky (jako je například editor výrazů).  
  
-   <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Označuje, zda návrháře je ve stavu jen pro čtení.  
  
-   <xref:System.Activities.Presentation.View.Selection>: Definuje kolekci objektů, které jsou aktuálně vybrány.  
  
-   <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
-   <xref:System.Activities.Presentation.WorkflowFileItem>: Obsahuje informace o souboru, který je na základě aktuální relaci.  
  
 Služby:  
  
-   <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Umožňuje vlastnosti, které chcete přidat do aktuální instance pomocí <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.  
  
-   <xref:System.Activities.Presentation.View.DesignerView>: Umožňuje přístup k vlastnostem plátna návrháře.  
  
-   <xref:System.Activities.Presentation.IActivityToolboxService>: Umožňuje obsah na panelu nástrojů na aktualizovat.  
  
-   <xref:System.Activities.Presentation.Hosting.ICommandService>: Používají k integraci s implementací služby poskytované vlastní příkazy návrháře (jako je kontextová nabídka).  
  
-   <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Poskytuje funkce pro návrháře ladicího programu.  
  
-   <xref:System.Activities.Presentation.View.IExpressionEditorService>: Poskytuje přístup do dialogového okna editoru výrazů.  
  
-   <xref:System.Activities.Presentation.IIntegratedHelpService>: Poskytuje funkce integrovaná Nápověda Návrháře.  
  
-   <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Poskytuje přístup k chybám ověření pomocí <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.  
  
-   <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Poskytuje interní služba ukládat a načítat data. Tato služba používá se interně pomocí rozhraní .NET Framework a není určena pro externí použití.  
  
-   <xref:System.Activities.Presentation.IXamlLoadErrorService>: Poskytuje přístup k XAML zatížení chybu kolekce pomocí <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.  
  
-   <xref:System.Activities.Presentation.Services.ModelService>: Návrhář se používají k interakci s modelem pracovního postupu, který právě upravujete.  
  
-   <xref:System.Activities.Presentation.Model.ModelTreeManager>: Poskytuje přístup do kořenového adresáře pomocí stromu modelu položky <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
-   <xref:System.Activities.Presentation.UndoEngine>: Poskytuje vrácení zpět a znovu funkce.  
  
-   <xref:System.Activities.Presentation.Services.ViewService>: Vizuální prvky Maps na základní položky modelu.  
  
-   <xref:System.Activities.Presentation.View.ViewStateService>: Úložiště zobrazit stavy položky modelu.  
  
-   <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Použít k přizpůsobení chování virtuální kontejner uživatelského rozhraní.  
  
-   <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Umožňuje vytvářet a rušit registraci delegáty pro oznámení události. Také umožňuje vlastníkovi okna nastavení.
