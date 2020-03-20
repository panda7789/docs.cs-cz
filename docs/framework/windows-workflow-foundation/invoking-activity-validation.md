---
title: Vyvolání ověřování aktivit
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 1241e6445cde20a192581e8132e563e0f7ca8d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182889"
---
# <a name="invoking-activity-validation"></a>Vyvolání ověřování aktivit
Ověření aktivity poskytuje metodu k identifikaci a hlášení chyb v konfiguraci libovolné aktivity před jejím spuštěním. K ověření dochází při změně pracovního postupu v návrháři pracovního postupu a všechny chyby ověření nebo upozornění jsou zobrazeny v návrháři pracovního postupu. K ověření dochází také v době běhu, kdy je vyvolán <xref:System.Activities.InvalidWorkflowException> pracovní postup a pokud dojde k chybám ověření, je vyvolána výchozí ověřovací logikou. Windows Workflow Foundation (WF) poskytuje třídu, <xref:System.Activities.Validation.ActivityValidationServices> kterou mohou vývojáři pracovního postupu a nástrojů použít k explicitnímu ověření aktivity. Toto téma popisuje <xref:System.Activities.Validation.ActivityValidationServices> použití k ověření aktivity.  
  
## <a name="using-activityvalidationservices"></a>Použití služby ActivityValidationServices  
 <xref:System.Activities.Validation.ActivityValidationServices>má <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> dvě přetížení, které se používají k vyvolání logiky ověření aktivity. První přetížení trvá kořenové aktivity, které mají být ověřeny a vrátí kolekci chyb ověření a upozornění. V následujícím příkladu `Add` se používá vlastní aktivita, která má dva požadované argumenty.  
  
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
  
 Aktivita se `Add` používá <xref:System.Activities.Statements.Sequence>uvnitř , ale jeho dva požadované argumenty nejsou vázány, jak je znázorněno v následujícím příkladu.  
  
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
  
 Tento pracovní postup lze <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>ověřit voláním . <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>vrátí kolekci všech chyb ověření nebo upozornění obsažených aktivity a všechny podřízené, jak je znázorněno v následujícím příkladu.  
  
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
  
 Při <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> volání v tomto ukázkovém pracovním postupu jsou vráceny dvě chyby ověření.  
  
 **Chyba: Nebyla zadána hodnota pro argument požadované aktivity Operand2.**  
**Chyba: Nebyla zadána hodnota pro argument požadované aktivity Operand1.**  Pokud tento pracovní postup <xref:System.Activities.InvalidWorkflowException> byl vyvolán, by být vyvolána, jak je znázorněno v následujícím příkladu.  
  
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
**Přidání: Nebyla zadána hodnota pro argument požadované aktivity Operand2.** 
 **'Přidat': Hodnota pro argument požadované aktivity 'Operand1' nebyla zadána.**  Aby byl tento příklad pracovního postupu platný, `Add` musí být svázány dva požadované argumenty aktivity. V následujícím příkladu jsou dva požadované argumenty vázány na proměnné pracovního postupu spolu s hodnotou výsledku. V tomto <xref:System.Activities.Activity%601.Result%2A> příkladu je argument vázán spolu se dvěma požadovanými argumenty. Argument <xref:System.Activities.Activity%601.Result%2A> není nutné být vázána a nezpůsobí chybu ověření, pokud není. Je odpovědností autora pracovního <xref:System.Activities.Activity%601.Result%2A> postupu svázat, pokud jeho hodnota je použita jinde v pracovním postupu.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Ověření požadovaných argumentů v kořenové aktivitě  
 Pokud kořenová aktivita pracovního postupu má argumenty, nejsou vázány, dokud není pracovní postup vyvolán a parametry jsou předány pracovnímu postupu. Následující pracovní postup předá ověření, ale je vyvolána výjimka, pokud je pracovní postup vyvolán bez předání požadovaných argumentů, jak je znázorněno v následujícím příkladu.  
  
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
**Buď opravte definici pracovního postupu nebo zadejte vstupní hodnoty pro opravu těchto chyb:**
 **"Přidat": Nebyla zadána hodnota pro argument požadované aktivity Operand2.** 
 **'Přidat': Hodnota pro argument požadované aktivity 'Operand1' nebyla zadána.**  Po předání správných argumentů se pracovní postup úspěšně dokončí, jak je znázorněno v následujícím příkladu.  
  
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
> V tomto příkladu byla kořenová aktivita deklarována jako `Add` místo `Activity` jako v předchozím příkladu. To umožňuje `WorkflowInvoker.Invoke` metodu vrátit jedno celé číslo, které `Add` představuje výsledky aktivity `out` namísto slovníku argumentů. Proměnná `wf` mohla být také `Activity<int>`deklarována jako .  
  
 Při ověřování kořenových argumentů je odpovědností hostitelské aplikace zajistit, aby všechny požadované argumenty byly předány při vyvolání pracovního postupu.  
  
### <a name="invoking-imperative-code-based-validation"></a>Vyvolání imperativního ověření na základě kódu

Imperativní ověření založené na kódu poskytuje jednoduchý způsob, jak aktivita <xref:System.Activities.CodeActivity>poskytnout <xref:System.Activities.AsyncCodeActivity>ověření <xref:System.Activities.NativeActivity>o sobě a je k dispozici pro aktivity, které jsou odvozeny od , , a . Ověřovací kód, který určuje všechny chyby ověření nebo upozornění je přidán do aktivity. Při ověření je vyvolána na aktivitu, tato upozornění nebo chyby <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>jsou obsaženy v kolekci vrácené volání . V následujícím příkladu `CreateProduct` je definována aktivita. Pokud `Cost` je větší `Price`než , je k metadatům v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsání přidána chyba ověření.  
  
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
  
 V tomto příkladu je pracovní `CreateProduct` postup konfigurován pomocí aktivity. V tomto pracovním `Cost` postupu je `Price`větší než `Description` , a požadovaný argument není nastaven. Při vyvolání ověření jsou vráceny následující chyby.  
  
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
**Chyba: Nebyla zadána hodnota argumentu požadované aktivity "Popis".**
> [!NOTE]
> Vlastní autoři aktivity mohou poskytnout logiku ověření v přepsání aktivity. <xref:System.Activities.CodeActivity.CacheMetadata%2A> Všechny výjimky, které <xref:System.Activities.CodeActivity.CacheMetadata%2A> jsou vyvolány z nejsou považovány za chyby ověření. Tyto výjimky budou uniknout <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> z volání a musí být zpracovány volajícím.  
  
## <a name="using-validationsettings"></a>Použití nastavení ověření  
 Ve výchozím nastavení jsou všechny aktivity ve stromu <xref:System.Activities.Validation.ActivityValidationServices>aktivit vyhodnocovány při vyvolání ověření aplikací . <xref:System.Activities.Validation.ValidationSettings>umožňuje přizpůsobit ověření několika různými způsoby konfigurací jeho tří vlastností. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>určuje, zda má validátor procházet celý strom aktivit nebo používat pouze logiku ověření pro zadanou aktivitu. Výchozí hodnota pro `false`tuto hodnotu je . <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>určuje další mapování omezení z typu na seznam omezení. Pro základní typ každé aktivity ve stromu aktivity, <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>který je ověřován, je vyhledávání do . Pokud je nalezen odpovídající seznam omezení, jsou pro aktivitu vyhodnocena všechna omezení v seznamu. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>určuje, zda má validátor vyhodnotit všechna omezení <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>nebo pouze omezení uvedená v . Výchozí hodnota je `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>a <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> jsou užitečné pro autory hostitele pracovního postupu přidat další ověření pro pracovní postupy, jako jsou omezení zásad pro nástroje, jako je FxCop. Další informace o omezeních naleznete v tématu [Deklarativní omezení](declarative-constraints.md).  
  
 Chcete-li použít <xref:System.Activities.Validation.ValidationSettings>, nakonfigurujte požadované <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>vlastnosti a předejte je ve volání . V tomto příkladu je ověřen <xref:System.Activities.Statements.Sequence> pracovní postup, který se skládá z a s vlastní `Add` aktivitou. Aktivita `Add` má dva požadované argumenty.  
  
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
  
 Následující `Add` aktivita <xref:System.Activities.Statements.Sequence>se používá v , ale jeho dva požadované argumenty nejsou vázány.  
  
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
  
 V následujícím příkladu se <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> ověření `true`provádí s nastavenou na , takže je ověřena pouze kořenová <xref:System.Activities.Statements.Sequence> aktivita.  
  
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
  
 Tento kód zobrazuje následující výstup:  
  
 **Žádná varování nebo chyby** I v `Add` případě, že aktivita vyžaduje argumenty, které nejsou vázány, ověření je úspěšné, protože je vyhodnocena pouze kořenová aktivita. Tento typ ověření je užitečný pro ověření pouze určitých prvků ve stromu aktivit, jako je například ověření změny vlastnosti jedné aktivity v návrháři. Všimněte si, že pokud je tento pracovní postup vyvolán, <xref:System.Activities.InvalidWorkflowException> je vyhodnoceno úplné ověření nakonfigurované v pracovním postupu a bude vyvoláno. <xref:System.Activities.Validation.ActivityValidationServices>a <xref:System.Activities.Validation.ValidationSettings> nakonfigurujte pouze ověření explicitně vyvolané hostitelem a nikoli ověření, ke kterému dochází při vyvolání pracovního postupu.
