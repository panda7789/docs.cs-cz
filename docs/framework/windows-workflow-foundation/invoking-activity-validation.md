---
title: Vyvolání ověřování aktivit
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: b45840081f5fc142cf3ec88853dea984b204c9d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934986"
---
# <a name="invoking-activity-validation"></a>Vyvolání ověřování aktivit
Ověření aktivity poskytuje metodu pro identifikaci a hlášení chyb v konfiguraci jakékoli aktivity před jejím spuštěním. K ověření dojde, když se v Návrháři pracovních postupů upraví pracovní postup a v Návrháři pracovních postupů se zobrazí všechny chyby nebo upozornění ověřování. K ověření dojde v době spuštění pracovního postupu, a pokud dojde k nějakým chybám ověření, <xref:System.Activities.InvalidWorkflowException> je vyvolána výchozí logikou ověřování. Programovací model Windows Workflow Foundation (WF) poskytuje <xref:System.Activities.Validation.ActivityValidationServices> třídu, kterou mohou používat aplikace pracovního postupu a vývojáři nástrojů k explicitnímu ověření aktivity. Toto téma popisuje, jak použít <xref:System.Activities.Validation.ActivityValidationServices> k provedení ověření aktivity.  
  
## <a name="using-activityvalidationservices"></a>Použití zobrazíte služby ActivityValidationServices  
 <xref:System.Activities.Validation.ActivityValidationServices>má dvě <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> přetížení, která se používají k vyvolání logiky ověřování aktivity. První přetížení převezme kořenovou aktivitu k ověření a vrátí kolekci chyb ověřování a upozornění. V následujícím příkladu se používá vlastní `Add` aktivita, která má dva povinné argumenty.  
  
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
  
 Aktivita se používá <xref:System.Activities.Statements.Sequence>uvnitř, ale její dva požadované argumenty nejsou svázané, jak je znázorněno v následujícím příkladu. `Add`  
  
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
  
 Tento pracovní postup lze ověřit voláním <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>Vrátí kolekci všech chyb ověřování nebo upozornění obsažených v aktivitě a všech podřízených, jak je znázorněno v následujícím příkladu.  
  
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
  
 Při <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> volání tohoto ukázkového pracovního postupu se vrátí dvě chyby ověřování.  
  
 **Chyba: Nebyla zadána hodnota pro argument požadované aktivity ' Operand2 '.**  
**Chyba: Nebyla zadána hodnota pro argument požadované aktivity ' Operand1 '.**  Pokud byl tento pracovní postup vyvolán <xref:System.Activities.InvalidWorkflowException> , bude vyvolána výjimka, jak je znázorněno v následujícím příkladu.  
  
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
  
 **System. Activities. InvalidWorkflowException:**  
**Při zpracování stromu pracovního postupu došlo k následujícím chybám:**    
**' Přidat ': Nebyla zadána hodnota pro argument požadované aktivity ' Operand2 '.**    
**' Přidat ': Nebyla zadána hodnota pro argument požadované aktivity ' Operand1 '.**  Aby byl tento ukázkový pracovní postup platný, musí být vázány dva požadované `Add` argumenty aktivity. V následujícím příkladu jsou dva požadované argumenty vázány na proměnné pracovního postupu spolu s výslednou hodnotou. V tomto příkladu <xref:System.Activities.Activity%601.Result%2A> je argument svázán spolu se dvěma požadovanými argumenty. <xref:System.Activities.Activity%601.Result%2A> Argument není nutné svázat a nezpůsobuje chybu ověřování, pokud není. Je odpovědností autora pracovního postupu, aby se vytvořila vazba <xref:System.Activities.Activity%601.Result%2A> , pokud se jeho hodnota používá jinde v pracovním postupu.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Ověřování požadovaných argumentů u kořenové aktivity  
 Pokud má kořenová aktivita pracovního postupu argumenty, nejsou tyto argumenty vázány, dokud není vyvolán pracovní postup a parametry jsou předány do pracovního postupu. Následující pracovní postup projde ověřením, ale výjimka je vyvolána, pokud je pracovní postup vyvolán bez předání požadovaných argumentů, jak je znázorněno v následujícím příkladu.  
  
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
  
 **System.ArgumentException: Nastavení argumentu kořenové aktivity jsou nesprávná.**  
**Opravte tyto chyby zadáním opravy definice pracovního postupu nebo zadáním vstupních hodnot:**    
**' Přidat ': Nebyla zadána hodnota pro argument požadované aktivity ' Operand2 '.**    
**' Přidat ': Nebyla zadána hodnota pro argument požadované aktivity ' Operand1 '.**  Po předání správných argumentů se pracovní postup úspěšně dokončí, jak je znázorněno v následujícím příkladu.  
  
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
> V tomto příkladu byla kořenová aktivita deklarována jako `Add` `Activity` místo v předchozím příkladu. To umožňuje `WorkflowInvoker.Invoke` metodě vracet jedno celé číslo, které představuje výsledky `Add` aktivity `out` namísto slovníku argumentů. Proměnná `wf` by mohla být také deklarována jako `Activity<int>`.  
  
 Při ověřování kořenových argumentů je zodpovědný hostitelská aplikace, aby zajistila, že všechny požadované argumenty jsou předány při vyvolání pracovního postupu.  
  
### <a name="invoking-imperative-code-based-validation"></a>Vyvolání imperativního ověřování na základě kódu

Imperativní ověřování na základě kódu poskytuje jednoduchý způsob, jak může aktivita poskytnout ověření sama o sobě, a je k dispozici pro aktivity, <xref:System.Activities.CodeActivity>které <xref:System.Activities.AsyncCodeActivity>jsou odvozeny z, a <xref:System.Activities.NativeActivity>. Ověřovací kód, který určuje chyby ověřování nebo upozornění, se přidají do aktivity. Když je vyvoláno ověřování u aktivity, jsou tato upozornění nebo chyby obsaženy v kolekci vrácené voláním metody <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. V následujícím příkladu `CreateProduct` je definována aktivita. Pokud je větší `Price`než, je do metadat v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsání přidána chyba ověřování. `Cost`  
  
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
  
 V tomto příkladu je pracovní postup nakonfigurován pomocí `CreateProduct` aktivity. V tomto pracovním postupu `Cost` je větší `Price`než a požadovaný `Description` argument není nastaven. Při vyvolání ověření se vrátí následující chyby.  
  
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
  
 **Chyba: Náklady musí být menší nebo rovny ceně.**  
**Chyba: Nebyla zadána hodnota pro argument požadované aktivity Description.**    
> [!NOTE]
> Vlastní autoři aktivit můžou v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsání aktivity poskytnout logiku ověřování. Všechny výjimky, které jsou vyvolány <xref:System.Activities.CodeActivity.CacheMetadata%2A> , nejsou považovány za chyby ověřování. Tyto výjimky budou ukončeny voláním <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a musí být zpracovány volajícím.  
  
## <a name="using-validationsettings"></a>Použití ValidationSettings  
 Ve výchozím nastavení jsou všechny aktivity ve stromu aktivit vyhodnocovány, když je vyvoláno ověřování pomocí <xref:System.Activities.Validation.ActivityValidationServices>. <xref:System.Activities.Validation.ValidationSettings>umožňuje, aby bylo ověřování upravováno několika různými způsoby konfigurací jejích tří vlastností. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>Určuje, zda má validátor procházet celý strom aktivity nebo pouze použít logiku ověřování pro zadanou aktivitu. Výchozí hodnota pro tuto hodnotu je `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>Určuje další mapování omezení z typu na seznam omezení. Pro základní typ každé aktivity ve stromu aktivity, ke kterému se ověřuje, se nachází vyhledávání <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Pokud je nalezen seznam vyhovujících omezení, jsou pro aktivitu vyhodnocena všechna omezení v seznamu. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>Určuje, zda má validátor vyhodnotit všechna omezení nebo pouze ty <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, které jsou zadány v. Výchozí hodnota je `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>a <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> jsou užitečné pro autory hostitele pracovního postupu k přidání dalšího ověřování pro pracovní postupy, jako jsou například omezení zásad pro nástroje, jako je například FxCop. Další informace o omezeních naleznete v tématu [deklarativní omezení](declarative-constraints.md).  
  
 Chcete- <xref:System.Activities.Validation.ValidationSettings>li použít, nakonfigurujte požadované vlastnosti a pak ji předejte při <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>volání. V tomto příkladu je ověřen pracovní postup, který se <xref:System.Activities.Statements.Sequence> skládá z s `Add` vlastní aktivitou. `Add` Aktivita má dva povinné argumenty.  
  
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
  
 Následující `Add` aktivita se používá <xref:System.Activities.Statements.Sequence>v, ale jejich dva požadované argumenty nejsou svázané.  
  
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
  
 V následujícím příkladu je ověřování provedeno s <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> nastavením na `true`, takže je ověřena pouze kořenová <xref:System.Activities.Statements.Sequence> aktivita.  
  
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
  
 **Žádná upozornění ani chyby** I když `Add` aktivita má požadované argumenty, které nejsou vázané, ověření proběhne úspěšně, protože je vyhodnocena pouze kořenová aktivita. Tento typ ověřování je vhodný pro ověřování pouze specifických prvků ve stromu aktivity, jako je například ověření vlastnosti jedné aktivity v návrháři. Všimněte si, že pokud je tento pracovní postup vyvolán, bude vyhodnoceno úplné ověření nakonfigurované v pracovním postupu a <xref:System.Activities.InvalidWorkflowException> bude vyvolána výjimka. <xref:System.Activities.Validation.ActivityValidationServices>a <xref:System.Activities.Validation.ValidationSettings> nakonfigurujte pouze ověřování explicitně vyvolané hostitelem, nikoli ověřování, ke kterému dojde při vyvolání pracovního postupu.
