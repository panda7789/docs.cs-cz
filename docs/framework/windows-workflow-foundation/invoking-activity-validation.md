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
# <a name="invoking-activity-validation"></a><span data-ttu-id="9fcc6-102">Vyvolání ověřování aktivit</span><span class="sxs-lookup"><span data-stu-id="9fcc6-102">Invoking Activity Validation</span></span>
<span data-ttu-id="9fcc6-103">Aktivita ověření poskytuje metodu, jak identifikovat a hlášení chyb v konfiguraci žádnou aktivitu před jeho provedením.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="9fcc6-104">Ověření vyvolá se při změně pracovního postupu v Návrháři pracovních postupů a všechny chyby nebo varování ověření se zobrazí v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="9fcc6-105">Ověření se také dojde za běhu, když uživatel vyvolá pracovní postup, a pokud dojde k chybám ověření, <xref:System.Activities.InvalidWorkflowException> logiku ověřování výchozí vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="9fcc6-106">Poskytuje Windows Workflow Foundation (WF) <xref:System.Activities.Validation.ActivityValidationServices> třídu, která je možné explicitně ověření aktivitu tak, že aplikace pracovního postupu a nástroje pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="9fcc6-107">Toto téma popisuje způsob použití <xref:System.Activities.Validation.ActivityValidationServices> provádět ověřování aktivit.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="9fcc6-108">Pomocí služby ActivityValidationServices</span><span class="sxs-lookup"><span data-stu-id="9fcc6-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="9fcc6-109"><xref:System.Activities.Validation.ActivityValidationServices> má dva <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> přetížení, které se používají k vyvolání aktivity logiku ověřování.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="9fcc6-110">První přetížení trvá kořenovou aktivitu k ověření a vrátí kolekci chyby a upozornění ověření.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="9fcc6-111">V následujícím příkladu, vlastní `Add` aktivita se používá, zda má dvě požadované argumenty.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="9fcc6-112">`Add` Aktivity je použit uvnitř <xref:System.Activities.Statements.Sequence>, ale jeho dvě povinné argumenty nejsou vázány, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9fcc6-113">Tento pracovní postup může být ověřen voláním <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="9fcc6-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Vrátí kolekci žádné chyby nebo varování ověření obsažené aktivity a žádné podřízené položky, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9fcc6-115">Když <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> je volán na tohoto ukázkového pracovního postupu, dva ověření jsou vráceny chyby.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="9fcc6-116">**Chyba: Nebyla zadána hodnota pro povinný argument aktivity 'Operand2'.**</span><span class="sxs-lookup"><span data-stu-id="9fcc6-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="9fcc6-117">**Chyba: Nebyla zadána hodnota pro povinný argument aktivity "Operand1".**</span><span class="sxs-lookup"><span data-stu-id="9fcc6-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="9fcc6-118">Pokud tento pracovní postup byl vyvolán, <xref:System.Activities.InvalidWorkflowException> by být vyvolána, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9fcc6-119">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="9fcc6-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="9fcc6-120">**Při zpracování stromu pracovního postupu došlo k následujícím chybám:** </span><span class="sxs-lookup"><span data-stu-id="9fcc6-120">**The following errors were encountered while processing the workflow tree:** </span></span>  
<span data-ttu-id="9fcc6-121">**'Přidat': hodnota pro povinný argument aktivity 'Operand2' nebyl uveden.** </span><span class="sxs-lookup"><span data-stu-id="9fcc6-121">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="9fcc6-122">**'Přidat': hodnota pro povinný argument aktivity 'Operand1' nebyl uveden.**</span><span class="sxs-lookup"><span data-stu-id="9fcc6-122">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="9fcc6-123">U tohoto ukázkového pracovního postupu platný vyžadovány dva argumenty `Add` aktivity musí být vázána.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-123">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="9fcc6-124">V následujícím příkladu dvě požadované argumenty jsou vázány na proměnné pracovního postupu spolu s výslednou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-124">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="9fcc6-125">V tomto příkladu <xref:System.Activities.Activity%601.Result%2A> argument je vázán spolu se dvěma povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-125">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="9fcc6-126"><xref:System.Activities.Activity%601.Result%2A> Argument není povinen být vázaný a nezpůsobí chybu ověřování, pokud není.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-126">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="9fcc6-127">Zodpovídá za autora pracovní postup k vytvoření vazby <xref:System.Activities.Activity%601.Result%2A> pokud jeho hodnota se používá jinde v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-127">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="9fcc6-128">Ověřuje se povinné argumenty kořenové aktivity</span><span class="sxs-lookup"><span data-stu-id="9fcc6-128">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="9fcc6-129">Pokud kořenová aktivita pracovního postupu má argumenty, nejsou tyto vázána, dokud se vyvolá pracovní postup a parametry jsou předány do pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-129">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="9fcc6-130">Následující pracovní postup projde ověřovacími, ale výjimka je vyvolána, pokud pracovní postup je vyvolán bez předávání povinné argumenty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-130">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9fcc6-131">**System.ArgumentException: Nastavení argumentů kořenové aktivity je nesprávné.**</span><span class="sxs-lookup"><span data-stu-id="9fcc6-131">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="9fcc6-132">**Opravte definice pracovního postupu nebo zadat vstupní hodnoty, chcete-li vyřešit tyto chyby:** </span><span class="sxs-lookup"><span data-stu-id="9fcc6-132">**Either fix the workflow definition or supply input values to fix these errors:** </span></span>  
<span data-ttu-id="9fcc6-133">**'Přidat': hodnota pro povinný argument aktivity 'Operand2' nebyl uveden.** </span><span class="sxs-lookup"><span data-stu-id="9fcc6-133">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="9fcc6-134">**'Přidat': hodnota pro povinný argument aktivity 'Operand1' nebyl uveden.**</span><span class="sxs-lookup"><span data-stu-id="9fcc6-134">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="9fcc6-135">Po správné argumenty jsou předány, pracovní postup dokončí úspěšně, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-135">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="9fcc6-136">V tomto příkladu se kořenovou aktivitu deklaroval jako `Add` místo `Activity` stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-136">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="9fcc6-137">Díky tomu `WorkflowInvoker.Invoke` metoda vrátí celá čísla, která představuje výsledky `Add` aktivity místo slovník `out` argumenty.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-137">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="9fcc6-138">Proměnná `wf` může také být deklarovány jako `Activity<int>`.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-138">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="9fcc6-139">Při ověřování argumentů kořenové, se odpovědnost hostitelská aplikace k zajištění, že všechny požadované argumenty jsou předány, když uživatel vyvolá pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-139">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="9fcc6-140">Vyvolání imperativní ověřování na základě kódu</span><span class="sxs-lookup"><span data-stu-id="9fcc6-140">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="9fcc6-141">Imperativní ověřování na základě kódu poskytuje jednoduchý způsob pro aktivitu pro ověřování o sobě a je k dispozici pro aktivity, které jsou odvozeny z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-141">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="9fcc6-142">Ověřovací kód, který určuje všechny chyby nebo varování ověření je přidána do aktivity.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-142">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="9fcc6-143">Při vyvolání ověření v aktivitě těchto upozornění a chyby jsou obsaženy v kolekci vrácené poskytovatelem volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-143">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="9fcc6-144">V následujícím příkladu `CreateProduct` aktivity je definována.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-144">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="9fcc6-145">Pokud `Cost` je větší než `Price`, chyby ověřování se přidá do metadat <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-145">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
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
  
 <span data-ttu-id="9fcc6-146">V tomto příkladu je nakonfigurován pomocí pracovního postupu `CreateProduct` aktivity.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-146">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="9fcc6-147">V tomto pracovním postupu `Cost` je větší než `Price`a požadované `Description` argument není nastaven.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-147">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="9fcc6-148">Při vyvolání ověření jsou vráceny tyto chyby.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-148">When validation is invoked, the following errors are returned.</span></span>  
  
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
  
 <span data-ttu-id="9fcc6-149">**Chyba: Náklady na musí být menší než nebo rovna hodnotě cena.**</span><span class="sxs-lookup"><span data-stu-id="9fcc6-149">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="9fcc6-150">**Chyba: Nebyla zadána hodnota pro povinný argument aktivity "Popisu".**</span><span class="sxs-lookup"><span data-stu-id="9fcc6-150">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="9fcc6-151">Vlastní aktivita autoři můžou poskytnout logiku ověřování v nějaké aktivitě <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-151">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="9fcc6-152">Všechny výjimky, které jsou vyvolány z <xref:System.Activities.CodeActivity.CacheMetadata%2A> nemají být považována za chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-152">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="9fcc6-153">Tyto výjimky budou návrat z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a volající musí být zpracován.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-153">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="9fcc6-154">Pomocí ValidationSettings</span><span class="sxs-lookup"><span data-stu-id="9fcc6-154">Using ValidationSettings</span></span>  
 <span data-ttu-id="9fcc6-155">Ve výchozím nastavení, jsou vyhodnoceny všechny aktivity ve stromu aktivit při vyvolání ověření podle <xref:System.Activities.Validation.ActivityValidationServices>.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-155">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="9fcc6-156"><xref:System.Activities.Validation.ValidationSettings> umožňuje ověření několika různými způsoby přizpůsobit tím, že nakonfigurujete její tři vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-156"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="9fcc6-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> Určuje, zda ověřovací modul by měl aktivity celý strom procházet nebo platí jenom logiku ověření pro zadané aktivita.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="9fcc6-158">Výchozí hodnota pro tuto hodnotu je `false`.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-158">The default for this value is `false`.</span></span> <span data-ttu-id="9fcc6-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> Určuje další omezení mapování z typu seznamu omezení.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="9fcc6-160">Pro základní typ každé aktivity ve stromu aktivit se ověřují se vyhledávání do <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-160">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="9fcc6-161">Pokud je nalezen odpovídající seznam omezení, se vyhodnotí všechna omezení v seznamu aktivity.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-161">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="9fcc6-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> Určuje, zda ověřovací modul by se měl vyhodnotit všechna omezení nebo pouze ty podle <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="9fcc6-163">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-163">The default value is `false`.</span></span> <span data-ttu-id="9fcc6-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> a <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> užitečných pro autory hostitele pracovního postupu pro přidání další ověřování pro pracovní postupy, jako je například omezení zásad pro nástroje, jako je FxCop.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="9fcc6-165">Další informace o omezení najdete v tématu [deklarativní omezení](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="9fcc6-165">For more information about constraints, see [Declarative Constraints](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="9fcc6-166">Chcete-li použít <xref:System.Activities.Validation.ValidationSettings>, nakonfigurujte požadované vlastnosti a pak ji předejte ve volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-166">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="9fcc6-167">V tomto příkladu pracovního postupu, který se skládá z <xref:System.Activities.Statements.Sequence> s vlastní `Add` aktivity se ověří.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-167">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="9fcc6-168">`Add` Aktivita má dvě požadované argumenty.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-168">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="9fcc6-169">Následující `Add` aktivita se používá v <xref:System.Activities.Statements.Sequence>, ale jeho dvě povinné argumenty nejsou vázány.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-169">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
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
  
 <span data-ttu-id="9fcc6-170">Následující příklad provede se ověření s <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> nastavena na `true`, takže pouze kořenové <xref:System.Activities.Statements.Sequence> aktivity se ověří.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-170">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
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
  
 <span data-ttu-id="9fcc6-171">Tento kód se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9fcc6-171">This code displays the following output:</span></span>  
  
 <span data-ttu-id="9fcc6-172">**Žádná upozornění ani chyby** i v případě, `Add` aktivity vyžaduje argumenty, které nejsou vázány, ověření je úspěšné, protože je vyhodnocen pouze kořenovou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-172">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="9fcc6-173">Tento typ ověření, který je užitečný pro ověření pouze konkrétní prvky ve stromu aktivit, jako je třeba ověřování změnu vlastnosti z jediné aktivity v návrháři.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-173">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="9fcc6-174">Všimněte si, že pokud se tento pracovní postup je vyvolána, úplné ověření nakonfigurované v pracovním postupu se vyhodnotí a <xref:System.Activities.InvalidWorkflowException> by být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-174">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="9fcc6-175"><xref:System.Activities.Validation.ActivityValidationServices> a <xref:System.Activities.Validation.ValidationSettings> konfigurace pouze ověření explicitně vyvolat hostitelem a ne ověřování, ke které dochází, když uživatel vyvolá pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="9fcc6-175"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
