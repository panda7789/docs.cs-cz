---
title: Vyvolání ověřování aktivit
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 61491e906bfc58bbd19cf43a5980b2781493411b
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035133"
---
# <a name="invoking-activity-validation"></a>Vyvolání ověřování aktivit
Aktivita ověření poskytuje metodu, jak identifikovat a hlášení chyb v konfiguraci žádnou aktivitu před jeho provedením. Ověření vyvolá se při změně pracovního postupu v Návrháři pracovních postupů a všechny chyby nebo varování ověření se zobrazí v Návrháři pracovních postupů. Ověření se také dojde za běhu, když uživatel vyvolá pracovní postup, a pokud dojde k chybám ověření, <xref:System.Activities.InvalidWorkflowException> logiku ověřování výchozí vyvolá výjimku. Poskytuje Windows Workflow Foundation (WF) <xref:System.Activities.Validation.ActivityValidationServices> třídu, která je možné explicitně ověření aktivitu tak, že aplikace pracovního postupu a nástroje pro vývojáře. Toto téma popisuje způsob použití <xref:System.Activities.Validation.ActivityValidationServices> provádět ověřování aktivit.  
  
## <a name="using-activityvalidationservices"></a>Pomocí služby ActivityValidationServices  
 <xref:System.Activities.Validation.ActivityValidationServices> má dva <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> přetížení, které se používají k vyvolání aktivity logiku ověřování. První přetížení trvá kořenovou aktivitu k ověření a vrátí kolekci chyby a upozornění ověření. V následujícím příkladu, vlastní `Add` aktivita se používá, zda má dvě požadované argumenty.  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 `Add` Aktivity je použit uvnitř <xref:System.Activities.Statements.Sequence>, ale jeho dvě povinné argumenty nejsou vázány, jak je znázorněno v následujícím příkladu.  
  
```csharp  
Variable<int> Operand1 = new Variable<int>{ Default = 10 };  
Variable<int> Operand2 = new Variable<int>{ Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =   
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 Tento pracovní postup může být ověřen voláním <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Vrátí kolekci žádné chyby nebo varování ověření obsažené aktivity a žádné podřízené položky, jak je znázorněno v následujícím příkladu.  
  
```csharp  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 Když <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> je volán na tohoto ukázkového pracovního postupu, dva ověření jsou vráceny chyby.  
  
 **Chyba: Nebyla zadána hodnota pro povinný argument aktivity 'Operand2'.**  
**Chyba: Nebyla zadána hodnota pro povinný argument aktivity "Operand1".**  Pokud tento pracovní postup byl vyvolán, <xref:System.Activities.InvalidWorkflowException> by být vyvolána, jak je znázorněno v následujícím příkladu.  
  
```csharp  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 **System.Activities.InvalidWorkflowException:**  
**Při zpracování stromu pracovního postupu došlo k následujícím chybám:**   
**'Přidat': hodnota pro povinný argument aktivity 'Operand2' nebyl uveden.**   
**'Přidat': hodnota pro povinný argument aktivity 'Operand1' nebyl uveden.**  U tohoto ukázkového pracovního postupu platný vyžadovány dva argumenty `Add` aktivity musí být vázána. V následujícím příkladu dvě požadované argumenty jsou vázány na proměnné pracovního postupu spolu s výslednou hodnotu. V tomto příkladu <xref:System.Activities.Activity%601.Result%2A> argument je vázán spolu se dvěma povinnými argumenty. <xref:System.Activities.Activity%601.Result%2A> Argument není povinen být vázaný a nezpůsobí chybu ověřování, pokud není. Zodpovídá za autora pracovní postup k vytvoření vazby <xref:System.Activities.Activity%601.Result%2A> pokud jeho hodnota se používá jinde v pracovním postupu.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Ověřuje se povinné argumenty kořenové aktivity  
 Pokud kořenová aktivita pracovního postupu má argumenty, nejsou tyto vázána, dokud se vyvolá pracovní postup a parametry jsou předány do pracovního postupu. Následující pracovní postup projde ověřovacími, ale výjimka je vyvolána, pokud pracovní postup je vyvolán bez předávání povinné argumenty, jak je znázorněno v následujícím příkladu.  
  
```csharp  
Activity wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, but when the workflow  
// is invoked, an InvalidWorkflowException is thrown.  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 **System.ArgumentException: Nastavení argumentů kořenové aktivity je nesprávné.**  
**Opravte definice pracovního postupu nebo zadat vstupní hodnoty, chcete-li vyřešit tyto chyby:**   
**'Přidat': hodnota pro povinný argument aktivity 'Operand2' nebyl uveden.**   
**'Přidat': hodnota pro povinný argument aktivity 'Operand1' nebyl uveden.**  Po správné argumenty jsou předány, pracovní postup dokončí úspěšně, jak je znázorněno v následujícím příkladu.  
  
```csharp  
Add wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, and the workflow completes  
// successfully because the required arguments were passed.  
try  
{  
    Dictionary<string, object> wfparams = new Dictionary<string, object>  
    {  
        { "Operand1", 10 },  
        { "Operand2", 15 }  
    };  
  
    int result = WorkflowInvoker.Invoke(wf, wfparams);  
    Console.WriteLine("Result: {0}", result);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
> [!NOTE]
> V tomto příkladu se kořenovou aktivitu deklaroval jako `Add` místo `Activity` stejně jako v předchozím příkladu. Díky tomu `WorkflowInvoker.Invoke` metoda vrátí celá čísla, která představuje výsledky `Add` aktivity místo slovník `out` argumenty. Proměnná `wf` může také být deklarovány jako `Activity<int>`.  
  
 Při ověřování argumentů kořenové, se odpovědnost hostitelská aplikace k zajištění, že všechny požadované argumenty jsou předány, když uživatel vyvolá pracovní postup.  
  
### <a name="invoking-imperative-code-based-validation"></a>Vyvolání imperativní ověřování na základě kódu

Imperativní ověřování na základě kódu poskytuje jednoduchý způsob pro aktivitu pro ověřování o sobě a je k dispozici pro aktivity, které jsou odvozeny z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>. Ověřovací kód, který určuje všechny chyby nebo varování ověření je přidána do aktivity. Při vyvolání ověření v aktivitě těchto upozornění a chyby jsou obsaženy v kolekci vrácené poskytovatelem volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. V následujícím příkladu `CreateProduct` aktivity je definována. Pokud `Cost` je větší než `Price`, chyby ověřování se přidá do metadat <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat.  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error   
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 V tomto příkladu je nakonfigurován pomocí pracovního postupu `CreateProduct` aktivity. V tomto pracovním postupu `Cost` je větší než `Price`a požadované `Description` argument není nastaven. Při vyvolání ověření jsou vráceny tyto chyby.  
  
```csharp  
Activity wf = new Sequence  
{  
    Activities =   
    {  
        new CreateProduct  
        {  
            Cost = 75.00,  
            Price = 55.00  
            // Cost > Price and required Description argument not set.  
        },  
        new WriteLine  
        {  
            Text = "Product added."  
        }  
    }  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 **Chyba: Náklady na musí být menší než nebo rovna hodnotě cena.**  
**Chyba: Nebyla zadána hodnota pro povinný argument aktivity "Popisu".**    
> [!NOTE]
>  Vlastní aktivita autoři můžou poskytnout logiku ověřování v nějaké aktivitě <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat. Všechny výjimky, které jsou vyvolány z <xref:System.Activities.CodeActivity.CacheMetadata%2A> nemají být považována za chyby ověření. Tyto výjimky budou návrat z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a volající musí být zpracován.  
  
## <a name="using-validationsettings"></a>Pomocí ValidationSettings  
 Ve výchozím nastavení, jsou vyhodnoceny všechny aktivity ve stromu aktivit při vyvolání ověření podle <xref:System.Activities.Validation.ActivityValidationServices>. <xref:System.Activities.Validation.ValidationSettings> umožňuje ověření několika různými způsoby přizpůsobit tím, že nakonfigurujete její tři vlastnosti. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> Určuje, zda ověřovací modul by měl aktivity celý strom procházet nebo platí jenom logiku ověření pro zadané aktivita. Výchozí hodnota pro tuto hodnotu je `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> Určuje další omezení mapování z typu seznamu omezení. Pro základní typ každé aktivity ve stromu aktivit se ověřují se vyhledávání do <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Pokud je nalezen odpovídající seznam omezení, se vyhodnotí všechna omezení v seznamu aktivity. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> Určuje, zda ověřovací modul by se měl vyhodnotit všechna omezení nebo pouze ty podle <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Výchozí hodnota je `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> a <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> užitečných pro autory hostitele pracovního postupu pro přidání další ověřování pro pracovní postupy, jako je například omezení zásad pro nástroje, jako je FxCop. Další informace o omezení najdete v tématu [deklarativní omezení](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).  
  
 Chcete-li použít <xref:System.Activities.Validation.ValidationSettings>, nakonfigurujte požadované vlastnosti a pak ji předejte ve volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. V tomto příkladu pracovního postupu, který se skládá z <xref:System.Activities.Statements.Sequence> s vlastní `Add` aktivity se ověří. `Add` Aktivita má dvě požadované argumenty.  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 Následující `Add` aktivita se používá v <xref:System.Activities.Statements.Sequence>, ale jeho dvě povinné argumenty nejsou vázány.  
  
```csharp  
Variable<int> Operand1 = new Variable<int> { Default = 10 };  
Variable<int> Operand2 = new Variable<int> { Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =   
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 Následující příklad provede se ověření s <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> nastavena na `true`, takže pouze kořenové <xref:System.Activities.Statements.Sequence> aktivity se ověří.  
  
```csharp  
ValidationSettings settings = new ValidationSettings  
{  
    SingleLevel = true  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 Tento kód se zobrazí následující výstup:  
  
 **Žádná upozornění ani chyby** i v případě, `Add` aktivity vyžaduje argumenty, které nejsou vázány, ověření je úspěšné, protože je vyhodnocen pouze kořenovou aktivitu. Tento typ ověření, který je užitečný pro ověření pouze konkrétní prvky ve stromu aktivit, jako je třeba ověřování změnu vlastnosti z jediné aktivity v návrháři. Všimněte si, že pokud se tento pracovní postup je vyvolána, úplné ověření nakonfigurované v pracovním postupu se vyhodnotí a <xref:System.Activities.InvalidWorkflowException> by být vyvolána. <xref:System.Activities.Validation.ActivityValidationServices> a <xref:System.Activities.Validation.ValidationSettings> konfigurace pouze ověření explicitně vyvolat hostitelem a ne ověřování, ke které dochází, když uživatel vyvolá pracovní postup.
