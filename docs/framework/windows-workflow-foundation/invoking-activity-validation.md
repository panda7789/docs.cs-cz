---
title: Volání ověření aktivity
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 39c059e7d8ed2191a4e0ce42d7d5b2087db84a5c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="e6c5b-102">Volání ověření aktivity</span><span class="sxs-lookup"><span data-stu-id="e6c5b-102">Invoking Activity Validation</span></span>
<span data-ttu-id="e6c5b-103">Aktivita ověření poskytuje metodu, jak identifikovat a zprávy o chybách v konfiguraci libovolné aktivity před jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="e6c5b-104">Ověření nastane, když pracovní postup se mění v Návrháři pracovních postupů a všechny chyby ověření nebo upozornění se zobrazí v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="e6c5b-105">Ověřování také dochází za běhu, při vyvolání pracovního postupu, a pokud dojde k chybám ověření, <xref:System.Activities.InvalidWorkflowException> logiku ověření výchozí vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="e6c5b-106">Windows Workflow Foundation (WF) poskytuje <xref:System.Activities.Validation.ActivityValidationServices> třídu, která lze použít aplikace pracovního postupu a nástrojů vývojáři explicitně ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="e6c5b-107">Toto téma popisuje postup použití <xref:System.Activities.Validation.ActivityValidationServices> k provedení ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="e6c5b-108">Pomocí ActivityValidationServices</span><span class="sxs-lookup"><span data-stu-id="e6c5b-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="e6c5b-109"><xref:System.Activities.Validation.ActivityValidationServices> má dva <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> přetížení, které se používají k vyvolání logiku ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="e6c5b-110">První přetížení trvá kořenovou aktivitu k ověření a vrátí kolekci ověření chyby a upozornění.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="e6c5b-111">V následujícím příkladu, vlastní `Add` aktivita se používá, že má dva požadované argumenty.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="e6c5b-112">`Add` Aktivita používá uvnitř <xref:System.Activities.Statements.Sequence>, ale vyžaduje se jeho dva argumenty nejsou vázaná znázorněné v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e6c5b-113">Tento pracovní postup může být ověřen voláním <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="e6c5b-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Vrátí kolekci všechny chyby ověření nebo upozornění obsažené aktivity a všechny podřízené objekty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e6c5b-115">Když <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> se volá na tento pracovní postup ukázka dvěma ověření chyby jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="e6c5b-116">**Chyba: Nebyla zadána hodnota pro argument požadované aktivity 'Operand2'.**</span><span class="sxs-lookup"><span data-stu-id="e6c5b-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="e6c5b-117">**Chyba: Nebyla zadána hodnota pro argument požadované aktivity 'Operand1'.**</span><span class="sxs-lookup"><span data-stu-id="e6c5b-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="e6c5b-118">Pokud tento pracovní postup byl vyvolán, <xref:System.Activities.InvalidWorkflowException> by být vyvolána, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e6c5b-119">**System.Activities.InvalidWorkflowException:**</span><span class="sxs-lookup"><span data-stu-id="e6c5b-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="e6c5b-120">**Při zpracování stromu pracovního postupu byly zjištěny následující chyby:** </span><span class="sxs-lookup"><span data-stu-id="e6c5b-120">**The following errors were encountered while processing the workflow tree:** </span></span>  
<span data-ttu-id="e6c5b-121">**"Přidat": hodnota pro argument požadované aktivity 'Operand2' nebyla zadána.** </span><span class="sxs-lookup"><span data-stu-id="e6c5b-121">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="e6c5b-122">**"Přidat": hodnota pro argument požadované aktivity 'Operand1' nebyla zadána.**</span><span class="sxs-lookup"><span data-stu-id="e6c5b-122">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="e6c5b-123">Pro tento pracovní postup příklad platná vyžaduje dva argumenty `Add` aktivity musí být vázána.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-123">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="e6c5b-124">V následujícím příkladu dva požadované argumenty je vázána na proměnné pracovního postupu spolu s hodnotou výsledek.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-124">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="e6c5b-125">V tomto příkladu <xref:System.Activities.Activity%601.Result%2A> argument je vázán spolu se dvěma povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-125">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="e6c5b-126"><xref:System.Activities.Activity%601.Result%2A> Argument není vyžadován vázat a nezpůsobí chybu ověření, pokud není.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-126">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="e6c5b-127">Je zodpovědností Autor pracovního postupu pro vazbu <xref:System.Activities.Activity%601.Result%2A> pokud jeho hodnota se používá jinde v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-127">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="e6c5b-128">Ověřování povinnými argumenty v kořenové aktivitě</span><span class="sxs-lookup"><span data-stu-id="e6c5b-128">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="e6c5b-129">Pokud kořenový aktivity pracovního postupu má argumenty, nejsou tyto vázána, dokud je volána pracovního postupu a parametry jsou předány do pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-129">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="e6c5b-130">Následující pracovní postup ověřením úspěšně projde, ale je vyvolána výjimka pokud pracovní postup je volána bez předávání povinnými argumenty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-130">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e6c5b-131">**System.ArgumentException: Argument nastavení kořenové aktivity jsou nesprávná.**</span><span class="sxs-lookup"><span data-stu-id="e6c5b-131">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="e6c5b-132">**Opravte definice pracovního postupu nebo zadat vstupní hodnoty pro opravte tyto chyby:** </span><span class="sxs-lookup"><span data-stu-id="e6c5b-132">**Either fix the workflow definition or supply input values to fix these errors:** </span></span>  
<span data-ttu-id="e6c5b-133">**"Přidat": hodnota pro argument požadované aktivity 'Operand2' nebyla zadána.** </span><span class="sxs-lookup"><span data-stu-id="e6c5b-133">**'Add': Value for a required activity argument 'Operand2' was not supplied.** </span></span>  
<span data-ttu-id="e6c5b-134">**"Přidat": hodnota pro argument požadované aktivity 'Operand1' nebyla zadána.**</span><span class="sxs-lookup"><span data-stu-id="e6c5b-134">**'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="e6c5b-135">Jakmile jsou předány správné argumenty, dokončení pracovního postupu úspěšně, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-135">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="e6c5b-136">V tomto příkladu kořenová aktivita byla deklarována jako `Add` místo `Activity` jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-136">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="e6c5b-137">To umožňuje `WorkflowInvoker.Invoke` metoda vrátí jeden celé číslo, které představuje výsledky `Add` aktivity místo slovník `out` argumenty.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-137">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="e6c5b-138">Proměnná `wf` může také byla deklarována jako `Activity<int>`.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-138">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="e6c5b-139">Při ověřování kořenové argumenty, je odpovídá hostitele aplikace k zajištění, že všechny požadované, argumenty se předá, když je volána pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-139">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="e6c5b-140">Vyvolání imperativní ověření založené na kódu</span><span class="sxs-lookup"><span data-stu-id="e6c5b-140">Invoking Imperative Code-Based Validation</span></span>  
 <span data-ttu-id="e6c5b-141">Imperativní ověřování založené na kódu poskytuje jednoduchý způsob, jak aktivity pro ověřování o samotné a je k dispozici pro aktivity, které jsou odvozeny od <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-141">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="e6c5b-142">Ověřovací kód, který určuje všechny chyby ověření nebo upozornění je přidána do aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-142">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="e6c5b-143">Po vyvolání ověření aktivita tyto varování nebo chyby jsou obsaženy v kolekci vrácený volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-143">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="e6c5b-144">V následujícím příkladu převzaty z [základní ověření](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) ukázce `CreateProduct` aktivity je definována.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-144">In the following example, taken from the [Basic Validation](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) sample, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="e6c5b-145">Pokud `Cost` je větší než `Price`, Chyba ověření se přidá do metadat v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-145">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
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
  
 <span data-ttu-id="e6c5b-146">V tomto příkladu je nakonfigurované pracovní postup pomocí `CreateProduct` aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-146">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="e6c5b-147">V tomto pracovním postupu `Cost` je větší než `Price`a požadované `Description` argument není nastaven.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-147">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="e6c5b-148">Po vyvolání ověření se vrátí k následujícím chybám.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-148">When validation is invoked, the following errors are returned.</span></span>  
  
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
  
 <span data-ttu-id="e6c5b-149">**Chyba: Náklady musí být menší než nebo rovno cenu.**</span><span class="sxs-lookup"><span data-stu-id="e6c5b-149">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="e6c5b-150">**Chyba: Nebyla zadána hodnota pro argument požadované aktivity "Popis".**</span><span class="sxs-lookup"><span data-stu-id="e6c5b-150">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>    
> [!NOTE]
>  <span data-ttu-id="e6c5b-151">Autoři vlastní aktivity může poskytnout logiku ověření v nějaké aktivitě <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-151">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="e6c5b-152">Jakékoli výjimky, které jsou vyvolány z <xref:System.Activities.CodeActivity.CacheMetadata%2A> nejsou považovány za chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-152">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="e6c5b-153">Tyto výjimky bude vyhnuli z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a musí být zpracována volající.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-153">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="e6c5b-154">Pomocí ValidationSettings</span><span class="sxs-lookup"><span data-stu-id="e6c5b-154">Using ValidationSettings</span></span>  
 <span data-ttu-id="e6c5b-155">Ve výchozím nastavení, všechny aktivity ve stromové struktuře aktivity jsou vyhodnocována po ověření je vyvolané <xref:System.Activities.Validation.ActivityValidationServices>.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-155">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="e6c5b-156"><xref:System.Activities.Validation.ValidationSettings> umožňuje ověření k přizpůsobení v několika různými způsoby podle konfigurace jeho tři vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-156"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="e6c5b-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> Určuje, zda by měl validátor provede stromu celý aktivity nebo platí pouze logiku ověření pro zadané aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-157"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="e6c5b-158">Výchozí hodnota pro tuto hodnotu je `false`.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-158">The default for this value is `false`.</span></span> <span data-ttu-id="e6c5b-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> Určuje další omezení mapování z typu do seznamu omezení.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-159"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="e6c5b-160">Pro základní typ každé aktivity ve stromové struktuře aktivity ověřován je vyhledávání do <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-160">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="e6c5b-161">Pokud je nalezen odpovídající seznamu omezení, všechna omezení v seznamu se vyhodnocují aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-161">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="e6c5b-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> Určuje, zda validátor by měly vyhodnotit všechna omezení nebo jenom ty zadaný v <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-162"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="e6c5b-163">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-163">The default value is `false`.</span></span> <span data-ttu-id="e6c5b-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> a <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> jsou užitečné pro hostitele autoři pracovního postupu přidat další ověřování pro pracovní postupy, jako je například omezení zásad pro nástroje, jako je FxCop.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-164"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="e6c5b-165"> omezení, najdete v části [deklarativní omezení](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="e6c5b-165"> constraints, see [Declarative Constraints](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="e6c5b-166">Chcete-li použít <xref:System.Activities.Validation.ValidationSettings>, nakonfigurujte požadované vlastnosti a předejte ji ve volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-166">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="e6c5b-167">V tomto příkladu pracovní postup, se skládá z <xref:System.Activities.Statements.Sequence> s vlastní `Add` ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-167">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="e6c5b-168">`Add` Aktivita má dva povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-168">The `Add` activity has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="e6c5b-169">Následující `Add` aktivita se používá v <xref:System.Activities.Statements.Sequence>, ale jeho dva vyžaduje argumenty nejsou vázána.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-169">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
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
  
 <span data-ttu-id="e6c5b-170">Pro následující příklad, ověření se provádí pomocí <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> nastavena na `true`, takže pouze kořenové <xref:System.Activities.Statements.Sequence> ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-170">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
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
  
 <span data-ttu-id="e6c5b-171">Tento kód zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e6c5b-171">This code displays the following output:</span></span>  
  
 <span data-ttu-id="e6c5b-172">**Žádná varování nebo chyby** i když `Add` aktivita vyžaduje argumenty, které nejsou vázané, ověření je úspěšné, protože je vyhodnocena pouze kořenové aktivity.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-172">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="e6c5b-173">Tento typ ověření, který je užitečný pro ověření pouze konkrétní prvky ve stromové struktuře aktivity, jako je například ověřování změnu vlastnosti z jediné aktivity v návrháři.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-173">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="e6c5b-174">Všimněte si, že pokud je tento pracovní postup je vyvolána, úplného ověření nakonfigurované v pracovním postupu vyhodnotí a <xref:System.Activities.InvalidWorkflowException> by být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-174">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="e6c5b-175"><xref:System.Activities.Validation.ActivityValidationServices> a <xref:System.Activities.Validation.ValidationSettings> konfigurovat pouze ověření explicitně vyvolané hostitele a není ověřování, který nastane, když je volána pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e6c5b-175"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
