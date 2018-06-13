---
title: Volání ověření aktivity
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 7e8be762e6c5c67687864727dcd4ca1cde9a8e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520172"
---
# <a name="invoking-activity-validation"></a>Volání ověření aktivity
Aktivita ověření poskytuje metodu, jak identifikovat a zprávy o chybách v konfiguraci libovolné aktivity před jeho spuštění. Ověření nastane, když pracovní postup se mění v Návrháři pracovních postupů a všechny chyby ověření nebo upozornění se zobrazí v Návrháři pracovních postupů. Ověřování také dochází za běhu, při vyvolání pracovního postupu, a pokud dojde k chybám ověření, <xref:System.Activities.InvalidWorkflowException> logiku ověření výchozí vyvolá výjimku. Windows Workflow Foundation (WF) poskytuje <xref:System.Activities.Validation.ActivityValidationServices> třídu, která lze použít aplikace pracovního postupu a nástrojů vývojáři explicitně ověření aktivity. Toto téma popisuje postup použití <xref:System.Activities.Validation.ActivityValidationServices> k provedení ověření aktivity.  
  
## <a name="using-activityvalidationservices"></a>Pomocí ActivityValidationServices  
 <xref:System.Activities.Validation.ActivityValidationServices> má dva <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> přetížení, které se používají k vyvolání logiku ověření aktivity. První přetížení trvá kořenovou aktivitu k ověření a vrátí kolekci ověření chyby a upozornění. V následujícím příkladu, vlastní `Add` aktivita se používá, že má dva požadované argumenty.  
  
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
  
 `Add` Aktivita používá uvnitř <xref:System.Activities.Statements.Sequence>, ale vyžaduje se jeho dva argumenty nejsou vázaná znázorněné v následujícím příkladu.  
  
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
  
 Tento pracovní postup může být ověřen voláním <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Vrátí kolekci všechny chyby ověření nebo upozornění obsažené aktivity a všechny podřízené objekty, jak je znázorněno v následujícím příkladu.  
  
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
  
 Když <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> se volá na tento pracovní postup ukázka dvěma ověření chyby jsou vráceny.  
  
 **Chyba: Nebyla zadána hodnota pro argument požadované aktivity 'Operand2'.**  
**Chyba: Nebyla zadána hodnota pro argument požadované aktivity 'Operand1'.**  Pokud tento pracovní postup byl vyvolán, <xref:System.Activities.InvalidWorkflowException> by být vyvolána, jak je znázorněno v následujícím příkladu.  
  
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
**Při zpracování stromu pracovního postupu byly zjištěny následující chyby:**   
**"Přidat": hodnota pro argument požadované aktivity 'Operand2' nebyla zadána.**   
**"Přidat": hodnota pro argument požadované aktivity 'Operand1' nebyla zadána.**  Pro tento pracovní postup příklad platná vyžaduje dva argumenty `Add` aktivity musí být vázána. V následujícím příkladu dva požadované argumenty je vázána na proměnné pracovního postupu spolu s hodnotou výsledek. V tomto příkladu <xref:System.Activities.Activity%601.Result%2A> argument je vázán spolu se dvěma povinnými argumenty. <xref:System.Activities.Activity%601.Result%2A> Argument není vyžadován vázat a nezpůsobí chybu ověření, pokud není. Je zodpovědností Autor pracovního postupu pro vazbu <xref:System.Activities.Activity%601.Result%2A> pokud jeho hodnota se používá jinde v pracovním postupu.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Ověřování povinnými argumenty v kořenové aktivitě  
 Pokud kořenový aktivity pracovního postupu má argumenty, nejsou tyto vázána, dokud je volána pracovního postupu a parametry jsou předány do pracovního postupu. Následující pracovní postup ověřením úspěšně projde, ale je vyvolána výjimka pokud pracovní postup je volána bez předávání povinnými argumenty, jak je znázorněno v následujícím příkladu.  
  
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
  
 **System.ArgumentException: Argument nastavení kořenové aktivity jsou nesprávná.**  
**Opravte definice pracovního postupu nebo zadat vstupní hodnoty pro opravte tyto chyby:**   
**"Přidat": hodnota pro argument požadované aktivity 'Operand2' nebyla zadána.**   
**"Přidat": hodnota pro argument požadované aktivity 'Operand1' nebyla zadána.**  Jakmile jsou předány správné argumenty, dokončení pracovního postupu úspěšně, jak je znázorněno v následujícím příkladu.  
  
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
>  V tomto příkladu kořenová aktivita byla deklarována jako `Add` místo `Activity` jako v předchozím příkladu. To umožňuje `WorkflowInvoker.Invoke` metoda vrátí jeden celé číslo, které představuje výsledky `Add` aktivity místo slovník `out` argumenty. Proměnná `wf` může také byla deklarována jako `Activity<int>`.  
  
 Při ověřování kořenové argumenty, je odpovídá hostitele aplikace k zajištění, že všechny požadované, argumenty se předá, když je volána pracovního postupu.  
  
### <a name="invoking-imperative-code-based-validation"></a>Vyvolání imperativní ověření založené na kódu  
 Imperativní ověřování založené na kódu poskytuje jednoduchý způsob, jak aktivity pro ověřování o samotné a je k dispozici pro aktivity, které jsou odvozeny od <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>. Ověřovací kód, který určuje všechny chyby ověření nebo upozornění je přidána do aktivity. Po vyvolání ověření aktivita tyto varování nebo chyby jsou obsaženy v kolekci vrácený volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. V následujícím příkladu převzaty z [základní ověření](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) ukázce `CreateProduct` aktivity je definována. Pokud `Cost` je větší než `Price`, Chyba ověření se přidá do metadat v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat.  
  
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
  
 V tomto příkladu je nakonfigurované pracovní postup pomocí `CreateProduct` aktivity. V tomto pracovním postupu `Cost` je větší než `Price`a požadované `Description` argument není nastaven. Po vyvolání ověření se vrátí k následujícím chybám.  
  
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
  
 **Chyba: Náklady musí být menší než nebo rovno cenu.**  
**Chyba: Nebyla zadána hodnota pro argument požadované aktivity "Popis".**    
> [!NOTE]
>  Autoři vlastní aktivity může poskytnout logiku ověření v nějaké aktivitě <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat. Jakékoli výjimky, které jsou vyvolány z <xref:System.Activities.CodeActivity.CacheMetadata%2A> nejsou považovány za chyby ověření. Tyto výjimky bude vyhnuli z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a musí být zpracována volající.  
  
## <a name="using-validationsettings"></a>Pomocí ValidationSettings  
 Ve výchozím nastavení, všechny aktivity ve stromové struktuře aktivity jsou vyhodnocována po ověření je vyvolané <xref:System.Activities.Validation.ActivityValidationServices>. <xref:System.Activities.Validation.ValidationSettings> umožňuje ověření k přizpůsobení v několika různými způsoby podle konfigurace jeho tři vlastnosti. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> Určuje, zda by měl validátor provede stromu celý aktivity nebo platí pouze logiku ověření pro zadané aktivity. Výchozí hodnota pro tuto hodnotu je `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> Určuje další omezení mapování z typu do seznamu omezení. Pro základní typ každé aktivity ve stromové struktuře aktivity ověřován je vyhledávání do <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Pokud je nalezen odpovídající seznamu omezení, všechna omezení v seznamu se vyhodnocují aktivity. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> Určuje, zda validátor by měly vyhodnotit všechna omezení nebo jenom ty zadaný v <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Výchozí hodnota je `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> a <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> jsou užitečné pro hostitele autoři pracovního postupu přidat další ověřování pro pracovní postupy, jako je například omezení zásad pro nástroje, jako je FxCop. Další informace o omezení najdete v tématu [deklarativní omezení](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).  
  
 Chcete-li použít <xref:System.Activities.Validation.ValidationSettings>, nakonfigurujte požadované vlastnosti a předejte ji ve volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. V tomto příkladu pracovní postup, se skládá z <xref:System.Activities.Statements.Sequence> s vlastní `Add` ověření aktivity. `Add` Aktivita má dva povinnými argumenty.  
  
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
  
 Následující `Add` aktivita se používá v <xref:System.Activities.Statements.Sequence>, ale jeho dva vyžaduje argumenty nejsou vázána.  
  
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
  
 Pro následující příklad, ověření se provádí pomocí <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> nastavena na `true`, takže pouze kořenové <xref:System.Activities.Statements.Sequence> ověření aktivity.  
  
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
  
 Tento kód zobrazí následující výstup:  
  
 **Žádná varování nebo chyby** i když `Add` aktivita vyžaduje argumenty, které nejsou vázané, ověření je úspěšné, protože je vyhodnocena pouze kořenové aktivity. Tento typ ověření, který je užitečný pro ověření pouze konkrétní prvky ve stromové struktuře aktivity, jako je například ověřování změnu vlastnosti z jediné aktivity v návrháři. Všimněte si, že pokud je tento pracovní postup je vyvolána, úplného ověření nakonfigurované v pracovním postupu vyhodnotí a <xref:System.Activities.InvalidWorkflowException> by být vyvolána. <xref:System.Activities.Validation.ActivityValidationServices> a <xref:System.Activities.Validation.ValidationSettings> konfigurovat pouze ověření explicitně vyvolané hostitele a není ověřování, který nastane, když je volána pracovního postupu.
