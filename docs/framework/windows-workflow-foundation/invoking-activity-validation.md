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
# <a name="invoking-activity-validation"></a><span data-ttu-id="9bd45-102">Vyvolání ověřování aktivit</span><span class="sxs-lookup"><span data-stu-id="9bd45-102">Invoking Activity Validation</span></span>
<span data-ttu-id="9bd45-103">Ověření aktivity poskytuje metodu k identifikaci a hlášení chyb v konfiguraci libovolné aktivity před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="9bd45-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="9bd45-104">K ověření dochází při změně pracovního postupu v návrháři pracovního postupu a všechny chyby ověření nebo upozornění jsou zobrazeny v návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="9bd45-105">K ověření dochází také v době běhu, kdy je vyvolán <xref:System.Activities.InvalidWorkflowException> pracovní postup a pokud dojde k chybám ověření, je vyvolána výchozí ověřovací logikou.</span><span class="sxs-lookup"><span data-stu-id="9bd45-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="9bd45-106">Windows Workflow Foundation (WF) poskytuje třídu, <xref:System.Activities.Validation.ActivityValidationServices> kterou mohou vývojáři pracovního postupu a nástrojů použít k explicitnímu ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="9bd45-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="9bd45-107">Toto téma popisuje <xref:System.Activities.Validation.ActivityValidationServices> použití k ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="9bd45-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="9bd45-108">Použití služby ActivityValidationServices</span><span class="sxs-lookup"><span data-stu-id="9bd45-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="9bd45-109"><xref:System.Activities.Validation.ActivityValidationServices>má <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> dvě přetížení, které se používají k vyvolání logiky ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="9bd45-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="9bd45-110">První přetížení trvá kořenové aktivity, které mají být ověřeny a vrátí kolekci chyb ověření a upozornění.</span><span class="sxs-lookup"><span data-stu-id="9bd45-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="9bd45-111">V následujícím příkladu `Add` se používá vlastní aktivita, která má dva požadované argumenty.</span><span class="sxs-lookup"><span data-stu-id="9bd45-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="9bd45-112">Aktivita se `Add` používá <xref:System.Activities.Statements.Sequence>uvnitř , ale jeho dva požadované argumenty nejsou vázány, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9bd45-113">Tento pracovní postup lze <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>ověřit voláním .</span><span class="sxs-lookup"><span data-stu-id="9bd45-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="9bd45-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>vrátí kolekci všech chyb ověření nebo upozornění obsažených aktivity a všechny podřízené, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9bd45-115">Při <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> volání v tomto ukázkovém pracovním postupu jsou vráceny dvě chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="9bd45-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="9bd45-116">**Chyba: Nebyla zadána hodnota pro argument požadované aktivity Operand2.**</span><span class="sxs-lookup"><span data-stu-id="9bd45-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="9bd45-117">**Chyba: Nebyla zadána hodnota pro argument požadované aktivity Operand1.**</span><span class="sxs-lookup"><span data-stu-id="9bd45-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="9bd45-118">Pokud tento pracovní postup <xref:System.Activities.InvalidWorkflowException> byl vyvolán, by být vyvolána, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9bd45-119">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="9bd45-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="9bd45-120">**Při zpracování stromu pracovního postupu došlo k následujícím chybám:**
**Přidání: Nebyla zadána hodnota pro argument požadované aktivity Operand2.** 
 **'Přidat': Hodnota pro argument požadované aktivity 'Operand1' nebyla zadána.**</span><span class="sxs-lookup"><span data-stu-id="9bd45-120">**The following errors were encountered while processing the workflow tree:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="9bd45-121">Aby byl tento příklad pracovního postupu platný, `Add` musí být svázány dva požadované argumenty aktivity.</span><span class="sxs-lookup"><span data-stu-id="9bd45-121">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="9bd45-122">V následujícím příkladu jsou dva požadované argumenty vázány na proměnné pracovního postupu spolu s hodnotou výsledku.</span><span class="sxs-lookup"><span data-stu-id="9bd45-122">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="9bd45-123">V tomto <xref:System.Activities.Activity%601.Result%2A> příkladu je argument vázán spolu se dvěma požadovanými argumenty.</span><span class="sxs-lookup"><span data-stu-id="9bd45-123">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="9bd45-124">Argument <xref:System.Activities.Activity%601.Result%2A> není nutné být vázána a nezpůsobí chybu ověření, pokud není.</span><span class="sxs-lookup"><span data-stu-id="9bd45-124">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="9bd45-125">Je odpovědností autora pracovního <xref:System.Activities.Activity%601.Result%2A> postupu svázat, pokud jeho hodnota je použita jinde v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-125">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="9bd45-126">Ověření požadovaných argumentů v kořenové aktivitě</span><span class="sxs-lookup"><span data-stu-id="9bd45-126">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="9bd45-127">Pokud kořenová aktivita pracovního postupu má argumenty, nejsou vázány, dokud není pracovní postup vyvolán a parametry jsou předány pracovnímu postupu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-127">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="9bd45-128">Následující pracovní postup předá ověření, ale je vyvolána výjimka, pokud je pracovní postup vyvolán bez předání požadovaných argumentů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-128">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9bd45-129">**System.ArgumentException: Nastavení argumentů kořenové aktivity je nesprávné.**</span><span class="sxs-lookup"><span data-stu-id="9bd45-129">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="9bd45-130">**Buď opravte definici pracovního postupu nebo zadejte vstupní hodnoty pro opravu těchto chyb:**
 **"Přidat": Nebyla zadána hodnota pro argument požadované aktivity Operand2.** 
 **'Přidat': Hodnota pro argument požadované aktivity 'Operand1' nebyla zadána.**</span><span class="sxs-lookup"><span data-stu-id="9bd45-130">**Either fix the workflow definition or supply input values to fix these errors:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="9bd45-131">Po předání správných argumentů se pracovní postup úspěšně dokončí, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-131">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="9bd45-132">V tomto příkladu byla kořenová aktivita deklarována jako `Add` místo `Activity` jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-132">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="9bd45-133">To umožňuje `WorkflowInvoker.Invoke` metodu vrátit jedno celé číslo, které `Add` představuje výsledky aktivity `out` namísto slovníku argumentů.</span><span class="sxs-lookup"><span data-stu-id="9bd45-133">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="9bd45-134">Proměnná `wf` mohla být také `Activity<int>`deklarována jako .</span><span class="sxs-lookup"><span data-stu-id="9bd45-134">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="9bd45-135">Při ověřování kořenových argumentů je odpovědností hostitelské aplikace zajistit, aby všechny požadované argumenty byly předány při vyvolání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-135">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="9bd45-136">Vyvolání imperativního ověření na základě kódu</span><span class="sxs-lookup"><span data-stu-id="9bd45-136">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="9bd45-137">Imperativní ověření založené na kódu poskytuje jednoduchý způsob, jak aktivita <xref:System.Activities.CodeActivity>poskytnout <xref:System.Activities.AsyncCodeActivity>ověření <xref:System.Activities.NativeActivity>o sobě a je k dispozici pro aktivity, které jsou odvozeny od , , a .</span><span class="sxs-lookup"><span data-stu-id="9bd45-137">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="9bd45-138">Ověřovací kód, který určuje všechny chyby ověření nebo upozornění je přidán do aktivity.</span><span class="sxs-lookup"><span data-stu-id="9bd45-138">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="9bd45-139">Při ověření je vyvolána na aktivitu, tato upozornění nebo chyby <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>jsou obsaženy v kolekci vrácené volání .</span><span class="sxs-lookup"><span data-stu-id="9bd45-139">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="9bd45-140">V následujícím příkladu `CreateProduct` je definována aktivita.</span><span class="sxs-lookup"><span data-stu-id="9bd45-140">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="9bd45-141">Pokud `Cost` je větší `Price`než , je k metadatům v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsání přidána chyba ověření.</span><span class="sxs-lookup"><span data-stu-id="9bd45-141">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
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
  
 <span data-ttu-id="9bd45-142">V tomto příkladu je pracovní `CreateProduct` postup konfigurován pomocí aktivity.</span><span class="sxs-lookup"><span data-stu-id="9bd45-142">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="9bd45-143">V tomto pracovním `Cost` postupu je `Price`větší než `Description` , a požadovaný argument není nastaven.</span><span class="sxs-lookup"><span data-stu-id="9bd45-143">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="9bd45-144">Při vyvolání ověření jsou vráceny následující chyby.</span><span class="sxs-lookup"><span data-stu-id="9bd45-144">When validation is invoked, the following errors are returned.</span></span>  
  
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
  
 <span data-ttu-id="9bd45-145">**Chyba: Náklady musí být menší nebo rovny ceně.**</span><span class="sxs-lookup"><span data-stu-id="9bd45-145">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="9bd45-146">**Chyba: Nebyla zadána hodnota argumentu požadované aktivity "Popis".**</span><span class="sxs-lookup"><span data-stu-id="9bd45-146">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>
> [!NOTE]
> <span data-ttu-id="9bd45-147">Vlastní autoři aktivity mohou poskytnout logiku ověření v přepsání aktivity. <xref:System.Activities.CodeActivity.CacheMetadata%2A></span><span class="sxs-lookup"><span data-stu-id="9bd45-147">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="9bd45-148">Všechny výjimky, které <xref:System.Activities.CodeActivity.CacheMetadata%2A> jsou vyvolány z nejsou považovány za chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="9bd45-148">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="9bd45-149">Tyto výjimky budou uniknout <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> z volání a musí být zpracovány volajícím.</span><span class="sxs-lookup"><span data-stu-id="9bd45-149">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="9bd45-150">Použití nastavení ověření</span><span class="sxs-lookup"><span data-stu-id="9bd45-150">Using ValidationSettings</span></span>  
 <span data-ttu-id="9bd45-151">Ve výchozím nastavení jsou všechny aktivity ve stromu <xref:System.Activities.Validation.ActivityValidationServices>aktivit vyhodnocovány při vyvolání ověření aplikací .</span><span class="sxs-lookup"><span data-stu-id="9bd45-151">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="9bd45-152"><xref:System.Activities.Validation.ValidationSettings>umožňuje přizpůsobit ověření několika různými způsoby konfigurací jeho tří vlastností.</span><span class="sxs-lookup"><span data-stu-id="9bd45-152"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="9bd45-153"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>určuje, zda má validátor procházet celý strom aktivit nebo používat pouze logiku ověření pro zadanou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-153"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="9bd45-154">Výchozí hodnota pro `false`tuto hodnotu je .</span><span class="sxs-lookup"><span data-stu-id="9bd45-154">The default for this value is `false`.</span></span> <span data-ttu-id="9bd45-155"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>určuje další mapování omezení z typu na seznam omezení.</span><span class="sxs-lookup"><span data-stu-id="9bd45-155"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="9bd45-156">Pro základní typ každé aktivity ve stromu aktivity, <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>který je ověřován, je vyhledávání do .</span><span class="sxs-lookup"><span data-stu-id="9bd45-156">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="9bd45-157">Pokud je nalezen odpovídající seznam omezení, jsou pro aktivitu vyhodnocena všechna omezení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-157">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="9bd45-158"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>určuje, zda má validátor vyhodnotit všechna omezení <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>nebo pouze omezení uvedená v .</span><span class="sxs-lookup"><span data-stu-id="9bd45-158"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="9bd45-159">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="9bd45-159">The default value is `false`.</span></span> <span data-ttu-id="9bd45-160"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>a <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> jsou užitečné pro autory hostitele pracovního postupu přidat další ověření pro pracovní postupy, jako jsou omezení zásad pro nástroje, jako je FxCop.</span><span class="sxs-lookup"><span data-stu-id="9bd45-160"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="9bd45-161">Další informace o omezeních naleznete v tématu [Deklarativní omezení](declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="9bd45-161">For more information about constraints, see [Declarative Constraints](declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="9bd45-162">Chcete-li použít <xref:System.Activities.Validation.ValidationSettings>, nakonfigurujte požadované <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>vlastnosti a předejte je ve volání .</span><span class="sxs-lookup"><span data-stu-id="9bd45-162">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="9bd45-163">V tomto příkladu je ověřen <xref:System.Activities.Statements.Sequence> pracovní postup, který se skládá z a s vlastní `Add` aktivitou.</span><span class="sxs-lookup"><span data-stu-id="9bd45-163">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="9bd45-164">Aktivita `Add` má dva požadované argumenty.</span><span class="sxs-lookup"><span data-stu-id="9bd45-164">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="9bd45-165">Následující `Add` aktivita <xref:System.Activities.Statements.Sequence>se používá v , ale jeho dva požadované argumenty nejsou vázány.</span><span class="sxs-lookup"><span data-stu-id="9bd45-165">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
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
  
 <span data-ttu-id="9bd45-166">V následujícím příkladu se <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> ověření `true`provádí s nastavenou na , takže je ověřena pouze kořenová <xref:System.Activities.Statements.Sequence> aktivita.</span><span class="sxs-lookup"><span data-stu-id="9bd45-166">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
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
  
 <span data-ttu-id="9bd45-167">Tento kód zobrazuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9bd45-167">This code displays the following output:</span></span>  
  
 <span data-ttu-id="9bd45-168">**Žádná varování nebo chyby** I v `Add` případě, že aktivita vyžaduje argumenty, které nejsou vázány, ověření je úspěšné, protože je vyhodnocena pouze kořenová aktivita.</span><span class="sxs-lookup"><span data-stu-id="9bd45-168">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="9bd45-169">Tento typ ověření je užitečný pro ověření pouze určitých prvků ve stromu aktivit, jako je například ověření změny vlastnosti jedné aktivity v návrháři.</span><span class="sxs-lookup"><span data-stu-id="9bd45-169">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="9bd45-170">Všimněte si, že pokud je tento pracovní postup vyvolán, <xref:System.Activities.InvalidWorkflowException> je vyhodnoceno úplné ověření nakonfigurované v pracovním postupu a bude vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="9bd45-170">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="9bd45-171"><xref:System.Activities.Validation.ActivityValidationServices>a <xref:System.Activities.Validation.ValidationSettings> nakonfigurujte pouze ověření explicitně vyvolané hostitelem a nikoli ověření, ke kterému dochází při vyvolání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9bd45-171"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
