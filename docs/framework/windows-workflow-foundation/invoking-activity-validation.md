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
# <a name="invoking-activity-validation"></a><span data-ttu-id="61b4e-102">Vyvolání ověřování aktivit</span><span class="sxs-lookup"><span data-stu-id="61b4e-102">Invoking Activity Validation</span></span>
<span data-ttu-id="61b4e-103">Ověření aktivity poskytuje metodu pro identifikaci a hlášení chyb v konfiguraci jakékoli aktivity před jejím spuštěním.</span><span class="sxs-lookup"><span data-stu-id="61b4e-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="61b4e-104">K ověření dojde, když se v Návrháři pracovních postupů upraví pracovní postup a v Návrháři pracovních postupů se zobrazí všechny chyby nebo upozornění ověřování.</span><span class="sxs-lookup"><span data-stu-id="61b4e-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="61b4e-105">K ověření dojde v době spuštění pracovního postupu, a pokud dojde k nějakým chybám ověření, <xref:System.Activities.InvalidWorkflowException> je vyvolána výchozí logikou ověřování.</span><span class="sxs-lookup"><span data-stu-id="61b4e-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="61b4e-106">Programovací model Windows Workflow Foundation (WF) poskytuje <xref:System.Activities.Validation.ActivityValidationServices> třídu, kterou mohou používat aplikace pracovního postupu a vývojáři nástrojů k explicitnímu ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="61b4e-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="61b4e-107">Toto téma popisuje, jak použít <xref:System.Activities.Validation.ActivityValidationServices> k provedení ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="61b4e-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="61b4e-108">Použití zobrazíte služby ActivityValidationServices</span><span class="sxs-lookup"><span data-stu-id="61b4e-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="61b4e-109"><xref:System.Activities.Validation.ActivityValidationServices>má dvě <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> přetížení, která se používají k vyvolání logiky ověřování aktivity.</span><span class="sxs-lookup"><span data-stu-id="61b4e-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="61b4e-110">První přetížení převezme kořenovou aktivitu k ověření a vrátí kolekci chyb ověřování a upozornění.</span><span class="sxs-lookup"><span data-stu-id="61b4e-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="61b4e-111">V následujícím příkladu se používá vlastní `Add` aktivita, která má dva povinné argumenty.</span><span class="sxs-lookup"><span data-stu-id="61b4e-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="61b4e-112">Aktivita se používá <xref:System.Activities.Statements.Sequence>uvnitř, ale její dva požadované argumenty nejsou svázané, jak je znázorněno v následujícím příkladu. `Add`</span><span class="sxs-lookup"><span data-stu-id="61b4e-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="61b4e-113">Tento pracovní postup lze ověřit voláním <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="61b4e-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="61b4e-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>Vrátí kolekci všech chyb ověřování nebo upozornění obsažených v aktivitě a všech podřízených, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="61b4e-115">Při <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> volání tohoto ukázkového pracovního postupu se vrátí dvě chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="61b4e-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="61b4e-116">**Chyba: Nebyla zadána hodnota pro argument požadované aktivity ' Operand2 '.**</span><span class="sxs-lookup"><span data-stu-id="61b4e-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="61b4e-117">**Chyba: Nebyla zadána hodnota pro argument požadované aktivity ' Operand1 '.**</span><span class="sxs-lookup"><span data-stu-id="61b4e-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="61b4e-118">Pokud byl tento pracovní postup vyvolán <xref:System.Activities.InvalidWorkflowException> , bude vyvolána výjimka, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="61b4e-119">**System. Activities. InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="61b4e-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="61b4e-120">**Při zpracování stromu pracovního postupu došlo k následujícím chybám:**  </span><span class="sxs-lookup"><span data-stu-id="61b4e-120">**The following errors were encountered while processing the workflow tree:** </span></span>  
<span data-ttu-id="61b4e-121">**' Přidat ': Nebyla zadána hodnota pro argument požadované aktivity ' Operand2 '.**  </span><span class="sxs-lookup"><span data-stu-id="61b4e-121">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="61b4e-122">**' Přidat ': Nebyla zadána hodnota pro argument požadované aktivity ' Operand1 '.**</span><span class="sxs-lookup"><span data-stu-id="61b4e-122">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="61b4e-123">Aby byl tento ukázkový pracovní postup platný, musí být vázány dva požadované `Add` argumenty aktivity.</span><span class="sxs-lookup"><span data-stu-id="61b4e-123">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="61b4e-124">V následujícím příkladu jsou dva požadované argumenty vázány na proměnné pracovního postupu spolu s výslednou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="61b4e-124">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="61b4e-125">V tomto příkladu <xref:System.Activities.Activity%601.Result%2A> je argument svázán spolu se dvěma požadovanými argumenty.</span><span class="sxs-lookup"><span data-stu-id="61b4e-125">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="61b4e-126"><xref:System.Activities.Activity%601.Result%2A> Argument není nutné svázat a nezpůsobuje chybu ověřování, pokud není.</span><span class="sxs-lookup"><span data-stu-id="61b4e-126">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="61b4e-127">Je odpovědností autora pracovního postupu, aby se vytvořila vazba <xref:System.Activities.Activity%601.Result%2A> , pokud se jeho hodnota používá jinde v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-127">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="61b4e-128">Ověřování požadovaných argumentů u kořenové aktivity</span><span class="sxs-lookup"><span data-stu-id="61b4e-128">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="61b4e-129">Pokud má kořenová aktivita pracovního postupu argumenty, nejsou tyto argumenty vázány, dokud není vyvolán pracovní postup a parametry jsou předány do pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-129">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="61b4e-130">Následující pracovní postup projde ověřením, ale výjimka je vyvolána, pokud je pracovní postup vyvolán bez předání požadovaných argumentů, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-130">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="61b4e-131">**System.ArgumentException: Nastavení argumentu kořenové aktivity jsou nesprávná.**</span><span class="sxs-lookup"><span data-stu-id="61b4e-131">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="61b4e-132">**Opravte tyto chyby zadáním opravy definice pracovního postupu nebo zadáním vstupních hodnot:**  </span><span class="sxs-lookup"><span data-stu-id="61b4e-132">**Either fix the workflow definition or supply input values to fix these errors:** </span></span>  
<span data-ttu-id="61b4e-133">**' Přidat ': Nebyla zadána hodnota pro argument požadované aktivity ' Operand2 '.**  </span><span class="sxs-lookup"><span data-stu-id="61b4e-133">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="61b4e-134">**' Přidat ': Nebyla zadána hodnota pro argument požadované aktivity ' Operand1 '.**</span><span class="sxs-lookup"><span data-stu-id="61b4e-134">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="61b4e-135">Po předání správných argumentů se pracovní postup úspěšně dokončí, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-135">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="61b4e-136">V tomto příkladu byla kořenová aktivita deklarována jako `Add` `Activity` místo v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-136">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="61b4e-137">To umožňuje `WorkflowInvoker.Invoke` metodě vracet jedno celé číslo, které představuje výsledky `Add` aktivity `out` namísto slovníku argumentů.</span><span class="sxs-lookup"><span data-stu-id="61b4e-137">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="61b4e-138">Proměnná `wf` by mohla být také deklarována jako `Activity<int>`.</span><span class="sxs-lookup"><span data-stu-id="61b4e-138">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="61b4e-139">Při ověřování kořenových argumentů je zodpovědný hostitelská aplikace, aby zajistila, že všechny požadované argumenty jsou předány při vyvolání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-139">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="61b4e-140">Vyvolání imperativního ověřování na základě kódu</span><span class="sxs-lookup"><span data-stu-id="61b4e-140">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="61b4e-141">Imperativní ověřování na základě kódu poskytuje jednoduchý způsob, jak může aktivita poskytnout ověření sama o sobě, a je k dispozici pro aktivity, <xref:System.Activities.CodeActivity>které <xref:System.Activities.AsyncCodeActivity>jsou odvozeny z, a <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="61b4e-141">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="61b4e-142">Ověřovací kód, který určuje chyby ověřování nebo upozornění, se přidají do aktivity.</span><span class="sxs-lookup"><span data-stu-id="61b4e-142">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="61b4e-143">Když je vyvoláno ověřování u aktivity, jsou tato upozornění nebo chyby obsaženy v kolekci vrácené voláním metody <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="61b4e-143">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="61b4e-144">V následujícím příkladu `CreateProduct` je definována aktivita.</span><span class="sxs-lookup"><span data-stu-id="61b4e-144">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="61b4e-145">Pokud je větší `Price`než, je do metadat v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsání přidána chyba ověřování. `Cost`</span><span class="sxs-lookup"><span data-stu-id="61b4e-145">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
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
  
 <span data-ttu-id="61b4e-146">V tomto příkladu je pracovní postup nakonfigurován pomocí `CreateProduct` aktivity.</span><span class="sxs-lookup"><span data-stu-id="61b4e-146">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="61b4e-147">V tomto pracovním postupu `Cost` je větší `Price`než a požadovaný `Description` argument není nastaven.</span><span class="sxs-lookup"><span data-stu-id="61b4e-147">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="61b4e-148">Při vyvolání ověření se vrátí následující chyby.</span><span class="sxs-lookup"><span data-stu-id="61b4e-148">When validation is invoked, the following errors are returned.</span></span>  
  
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
  
 <span data-ttu-id="61b4e-149">**Chyba: Náklady musí být menší nebo rovny ceně.**</span><span class="sxs-lookup"><span data-stu-id="61b4e-149">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="61b4e-150">**Chyba: Nebyla zadána hodnota pro argument požadované aktivity Description.**</span><span class="sxs-lookup"><span data-stu-id="61b4e-150">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>    
> [!NOTE]
> <span data-ttu-id="61b4e-151">Vlastní autoři aktivit můžou v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsání aktivity poskytnout logiku ověřování.</span><span class="sxs-lookup"><span data-stu-id="61b4e-151">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="61b4e-152">Všechny výjimky, které jsou vyvolány <xref:System.Activities.CodeActivity.CacheMetadata%2A> , nejsou považovány za chyby ověřování.</span><span class="sxs-lookup"><span data-stu-id="61b4e-152">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="61b4e-153">Tyto výjimky budou ukončeny voláním <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a musí být zpracovány volajícím.</span><span class="sxs-lookup"><span data-stu-id="61b4e-153">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="61b4e-154">Použití ValidationSettings</span><span class="sxs-lookup"><span data-stu-id="61b4e-154">Using ValidationSettings</span></span>  
 <span data-ttu-id="61b4e-155">Ve výchozím nastavení jsou všechny aktivity ve stromu aktivit vyhodnocovány, když je vyvoláno ověřování pomocí <xref:System.Activities.Validation.ActivityValidationServices>.</span><span class="sxs-lookup"><span data-stu-id="61b4e-155">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="61b4e-156"><xref:System.Activities.Validation.ValidationSettings>umožňuje, aby bylo ověřování upravováno několika různými způsoby konfigurací jejích tří vlastností.</span><span class="sxs-lookup"><span data-stu-id="61b4e-156"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="61b4e-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A>Určuje, zda má validátor procházet celý strom aktivity nebo pouze použít logiku ověřování pro zadanou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="61b4e-158">Výchozí hodnota pro tuto hodnotu je `false`.</span><span class="sxs-lookup"><span data-stu-id="61b4e-158">The default for this value is `false`.</span></span> <span data-ttu-id="61b4e-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>Určuje další mapování omezení z typu na seznam omezení.</span><span class="sxs-lookup"><span data-stu-id="61b4e-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="61b4e-160">Pro základní typ každé aktivity ve stromu aktivity, ke kterému se ověřuje, se nachází vyhledávání <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="61b4e-160">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="61b4e-161">Pokud je nalezen seznam vyhovujících omezení, jsou pro aktivitu vyhodnocena všechna omezení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-161">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="61b4e-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>Určuje, zda má validátor vyhodnotit všechna omezení nebo pouze ty <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, které jsou zadány v.</span><span class="sxs-lookup"><span data-stu-id="61b4e-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="61b4e-163">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="61b4e-163">The default value is `false`.</span></span> <span data-ttu-id="61b4e-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>a <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> jsou užitečné pro autory hostitele pracovního postupu k přidání dalšího ověřování pro pracovní postupy, jako jsou například omezení zásad pro nástroje, jako je například FxCop.</span><span class="sxs-lookup"><span data-stu-id="61b4e-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="61b4e-165">Další informace o omezeních naleznete v tématu [deklarativní omezení](declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="61b4e-165">For more information about constraints, see [Declarative Constraints](declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="61b4e-166">Chcete- <xref:System.Activities.Validation.ValidationSettings>li použít, nakonfigurujte požadované vlastnosti a pak ji předejte při <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>volání.</span><span class="sxs-lookup"><span data-stu-id="61b4e-166">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="61b4e-167">V tomto příkladu je ověřen pracovní postup, který se <xref:System.Activities.Statements.Sequence> skládá z s `Add` vlastní aktivitou.</span><span class="sxs-lookup"><span data-stu-id="61b4e-167">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="61b4e-168">`Add` Aktivita má dva povinné argumenty.</span><span class="sxs-lookup"><span data-stu-id="61b4e-168">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="61b4e-169">Následující `Add` aktivita se používá <xref:System.Activities.Statements.Sequence>v, ale jejich dva požadované argumenty nejsou svázané.</span><span class="sxs-lookup"><span data-stu-id="61b4e-169">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
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
  
 <span data-ttu-id="61b4e-170">V následujícím příkladu je ověřování provedeno s <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> nastavením na `true`, takže je ověřena pouze kořenová <xref:System.Activities.Statements.Sequence> aktivita.</span><span class="sxs-lookup"><span data-stu-id="61b4e-170">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
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
  
 <span data-ttu-id="61b4e-171">Tento kód zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="61b4e-171">This code displays the following output:</span></span>  
  
 <span data-ttu-id="61b4e-172">**Žádná upozornění ani chyby** I když `Add` aktivita má požadované argumenty, které nejsou vázané, ověření proběhne úspěšně, protože je vyhodnocena pouze kořenová aktivita.</span><span class="sxs-lookup"><span data-stu-id="61b4e-172">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="61b4e-173">Tento typ ověřování je vhodný pro ověřování pouze specifických prvků ve stromu aktivity, jako je například ověření vlastnosti jedné aktivity v návrháři.</span><span class="sxs-lookup"><span data-stu-id="61b4e-173">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="61b4e-174">Všimněte si, že pokud je tento pracovní postup vyvolán, bude vyhodnoceno úplné ověření nakonfigurované v pracovním postupu a <xref:System.Activities.InvalidWorkflowException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="61b4e-174">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="61b4e-175"><xref:System.Activities.Validation.ActivityValidationServices>a <xref:System.Activities.Validation.ValidationSettings> nakonfigurujte pouze ověřování explicitně vyvolané hostitelem, nikoli ověřování, ke kterému dojde při vyvolání pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="61b4e-175"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
