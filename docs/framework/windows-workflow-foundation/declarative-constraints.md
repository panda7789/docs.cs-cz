---
title: "Deklarativní omezení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a11c62c7011d7ffb13ed0d0ebf060a3cbeb7d7f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="declarative-constraints"></a><span data-ttu-id="2f95a-102">Deklarativní omezení</span><span class="sxs-lookup"><span data-stu-id="2f95a-102">Declarative Constraints</span></span>
<span data-ttu-id="2f95a-103">Deklarativní omezení poskytují výkonný metodu ověření pro aktivitu a jeho vztahů s dalšími aktivitami.</span><span class="sxs-lookup"><span data-stu-id="2f95a-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="2f95a-104">Omezení jsou nakonfigurovány pro aktivitu během procesu vytváření, ale další omezení lze zadat také od hostitele pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2f95a-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="2f95a-105">Toto téma obsahuje přehled používání deklarativní omezení pro ověřování aktivity.</span><span class="sxs-lookup"><span data-stu-id="2f95a-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="2f95a-106">Pomocí deklarativní omezení</span><span class="sxs-lookup"><span data-stu-id="2f95a-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="2f95a-107">Omezení je aktivitou, která obsahuje logiku ověření.</span><span class="sxs-lookup"><span data-stu-id="2f95a-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="2f95a-108">Tato aktivita omezení můžete vytvořené v kódu nebo v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="2f95a-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="2f95a-109">Po vytvoření aktivity omezení autoři aktivitu přidat tomuto omezení <xref:System.Activities.Activity.Constraints%2A> vlastnost aktivity na ověřit, nebo se používají pro další ověřování pomocí omezení <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> vlastnost <xref:System.Activities.Validation.ValidationSettings> instance .</span><span class="sxs-lookup"><span data-stu-id="2f95a-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="2f95a-110">Logiku ověření se může skládat z jednoduché ověření, jako je například ověřování aktivity metadata, ale můžete také provést ověření, který bere v úvahu relace aktuální aktivity k její nadřazené, děti a na stejné úrovni jako aktivity.</span><span class="sxs-lookup"><span data-stu-id="2f95a-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="2f95a-111">Omezení vytvořené pomocí <xref:System.Activities.Validation.Constraint%601> aktivity a několik dalších ověření aktivity jsou uvedeny vám pomůže při vytváření ověření chyby a upozornění a k poskytování informací o souvisejících činností v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="2f95a-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="2f95a-112">AssertValidation a AddValidationError</span><span class="sxs-lookup"><span data-stu-id="2f95a-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="2f95a-113"><xref:System.Activities.Validation.AssertValidation> Aktivita vyhodnotí výraz odkazuje jeho <xref:System.Activities.Validation.AssertValidation.Assertion%2A> vlastnost, a pokud je výsledkem výrazu `false`, ověření chyby nebo upozornění je přidán do <xref:System.Activities.Validation.ValidationResults>.</span><span class="sxs-lookup"><span data-stu-id="2f95a-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="2f95a-114"><xref:System.Activities.Validation.AssertValidation.Message%2A> Vlastnost popisuje chybu ověření a <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> vlastnost určuje, zda je chybu ověřování k chybě nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="2f95a-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="2f95a-115">Výchozí hodnota pro <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> je `false`.</span><span class="sxs-lookup"><span data-stu-id="2f95a-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="2f95a-116">V následujícím příkladu je deklarován omezení, která vrací upozornění ověření, pokud <xref:System.Activities.Activity.DisplayName%2A> aktivity ověřován je dva znaků nebo méně.</span><span class="sxs-lookup"><span data-stu-id="2f95a-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="2f95a-117">Parametr obecného typu používá pro <xref:System.Activities.Validation.Constraint%601> Určuje typ aktivity, které je ověřeno omezením.</span><span class="sxs-lookup"><span data-stu-id="2f95a-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="2f95a-118">Toto omezení používá <xref:System.Activities.Activity> jako Obecné zadejte a slouží k ověření všechny typy aktivit.</span><span class="sxs-lookup"><span data-stu-id="2f95a-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
```csharp  
public static Constraint ActivityDisplayNameIsNotSetWarning()  
{  
    DelegateInArgument<Activity> element = new DelegateInArgument<Activity>();  
  
    return new Constraint<Activity>  
    {  
        Body = new ActivityAction<Activity, ValidationContext>  
        {  
            Argument1 = element,  
            Handler = new AssertValidation  
            {  
                IsWarning = true,  
                Assertion = new InArgument<bool>(env => (element.Get(env).DisplayName.Length > 2)),  
                Message = new InArgument<string>("It is a best practice to have a DisplayName of more than 2 characters."),  
            }  
        }  
    };  
}  
```  
  
 <span data-ttu-id="2f95a-119">Pokud chcete zadat toto omezení pro aktivitu, je přidán do <xref:System.Activities.Activity.Constraints%2A> aktivity, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="2f95a-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
```csharp  
public sealed class SampleActivity : CodeActivity  
{  
    public SampleActivity()  
    {  
        base.Constraints.Add(ActivityDisplayNameIsNotSetWarning());  
    }  
  
    // Activity implementation omitted.  
}  
```  
  
 <span data-ttu-id="2f95a-120">Hostitel může také zadat toto omezení pro aktivity v pracovním postupu pomocí <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, která je popsaná v další části.</span><span class="sxs-lookup"><span data-stu-id="2f95a-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="2f95a-121"><xref:System.Activities.Validation.AddValidationError> Aktivity se používá ke generování ověřování chyb nebo upozornění bez nutnosti vyhodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="2f95a-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="2f95a-122">Jeho vlastnosti jsou podobné <xref:System.Activities.Validation.AssertValidation> a lze jej použít ve spojení s aktivity toku řízení omezení, jako <xref:System.Activities.Statements.If> aktivity.</span><span class="sxs-lookup"><span data-stu-id="2f95a-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>  
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="2f95a-123">Aktivity pracovního postupu relace</span><span class="sxs-lookup"><span data-stu-id="2f95a-123">Workflow Relationship Activities</span></span>  
 <span data-ttu-id="2f95a-124">Jsou k dispozici několik ověření aktivity které poskytují informace o další aktivity v pracovním postupu ve vztahu k aktivity, která je ověřována.</span><span class="sxs-lookup"><span data-stu-id="2f95a-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="2f95a-125"><xref:System.Activities.Validation.GetParentChain>Vrátí kolekci aktivity, která obsahuje všechny aktivity mezi aktuální aktivitu a kořenové aktivity.</span><span class="sxs-lookup"><span data-stu-id="2f95a-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="2f95a-126"><xref:System.Activities.Validation.GetChildSubtree>poskytuje kolekci aktivity, která obsahuje podřízené aktivity v rekurzivní vzor, a <xref:System.Activities.Validation.GetWorkflowTree> získá všechny aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="2f95a-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
 <span data-ttu-id="2f95a-127">V následujícím příkladu z [ověření vztahy aktivity](../../../docs/framework/windows-workflow-foundation/samples/activity-relationships-validation.md) ukázce `CreateState` aktivity je definována.</span><span class="sxs-lookup"><span data-stu-id="2f95a-127">In the following example from the [Activity Relationships Validation](../../../docs/framework/windows-workflow-foundation/samples/activity-relationships-validation.md) sample, a `CreateState` activity is defined.</span></span> <span data-ttu-id="2f95a-128">`CreateState` Aktivity musí být obsažena v `CreateCountry` aktivitu a `GetParent` metoda vrátí omezení, které vynucuje tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="2f95a-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="2f95a-129">`GetParent`používá <xref:System.Activities.Validation.GetParentChain> aktivity ve spojení s <xref:System.Activities.Statements.ForEach%601> aktivita ke kontrole nadřazené aktivity `CreateState` aktivity a určit, pokud se splní požadavek.</span><span class="sxs-lookup"><span data-stu-id="2f95a-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
```csharp  
public sealed class CreateState : CodeActivity  
{  
    public CreateState()  
    {  
        base.Constraints.Add(CheckParent());  
        this.Cities = new List<Activity>();              
    }  
  
    public List<Activity> Cities { get; set; }  
  
    public string Name { get; set; }    
  
    static Constraint CheckParent()  
    {  
        DelegateInArgument<CreateState> element = new DelegateInArgument<CreateState>();  
        DelegateInArgument<ValidationContext> context = new DelegateInArgument<ValidationContext>();                          
        Variable<bool> result = new Variable<bool>();  
        DelegateInArgument<Activity> parent = new DelegateInArgument<Activity>();  
  
        return new Constraint<CreateState>  
        {                                     
            Body = new ActivityAction<CreateState,ValidationContext>  
            {                      
                Argument1 = element,  
                Argument2 = context,  
                Handler = new Sequence  
                {  
                    Variables =  
                    {  
                        result   
                    },  
                    Activities =  
                    {  
                        new ForEach<Activity>  
                        {                                  
                            Values = new GetParentChain  
                            {  
                                ValidationContext = context                                      
                            },  
                            Body = new ActivityAction<Activity>  
                            {     
                                Argument = parent,   
                                Handler = new If()  
                                {                                            
                                    Condition = new InArgument<bool>((env) => object.Equals(parent.Get(env).GetType(),typeof(CreateCountry))),                                          
                                    Then = new Assign<bool>  
                                    {  
                                        Value = true,  
                                        To = result  
                                    }  
                                }  
                            }                                  
                        },  
                        new AssertValidation  
                        {  
                            Assertion = new InArgument<bool>(result),  
                            Message = new InArgument<string> ("CreateState has to be inside a CreateCountry activity"),                                                                  
                        }  
                    }  
                }  
            }  
        };  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // not needed for the sample  
    }  
}  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="2f95a-130">Windows Workflow Foundation [ověření](../../../docs/framework/windows-workflow-foundation/samples/validation.md) ukázky.</span><span class="sxs-lookup"><span data-stu-id="2f95a-130"> the Windows Workflow Foundation [Validation](../../../docs/framework/windows-workflow-foundation/samples/validation.md) samples.</span></span>  
  
## <a name="additional-constraints"></a><span data-ttu-id="2f95a-131">Další omezení</span><span class="sxs-lookup"><span data-stu-id="2f95a-131">Additional Constraints</span></span>  
 <span data-ttu-id="2f95a-132">Autoři hostitele pracovního postupu můžete zadat omezení další ověřování pro aktivity v pracovním postupu vytváření omezení a jejich přidáním <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> slovník <xref:System.Activities.Validation.ValidationSettings> instance.</span><span class="sxs-lookup"><span data-stu-id="2f95a-132">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="2f95a-133">Každá položka v <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> obsahuje typ aktivity, pro který platí omezení a seznam další omezení pro tento typ aktivity.</span><span class="sxs-lookup"><span data-stu-id="2f95a-133">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="2f95a-134">Po vyvolání ověření pro pracovní postup Každá aktivita zadaného typu, včetně odvozené třídy, vyhodnotí se omezení.</span><span class="sxs-lookup"><span data-stu-id="2f95a-134">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="2f95a-135">V tomto příkladu `ActivityDisplayNameIsNotSetWarning` omezení z předchozí části platí pro všechny aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="2f95a-135">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    // Workflow Details Omitted.  
};  
  
ValidationSettings settings = new ValidationSettings()  
{  
  
    AdditionalConstraints =  
    {  
        {typeof(Activity), new List<Constraint> {ActivityDisplayNameIsNotSetWarning()}},       
    }  
};  
  
// Validate the workflow.  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
// Evaluate the results.  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error in " + error.Source.DisplayName + ": " + error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning in " + warning.Source.DisplayName + ": " + warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="2f95a-136">Pokud <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> vlastnost <xref:System.Activities.Validation.ValidationSettings> je `true`, pak pouze zadané další omezení jsou vyhodnocována po ověření je vyvolán při volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f95a-136">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="2f95a-137">To může být užitečné pro zkontrolujete pracovní postupy pro ověřování podle konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2f95a-137">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="2f95a-138">Všimněte si ale, že po vyvolání pracovního postupu logiku ověření nakonfigurované v pracovním postupu vyhodnotí a musí projít pro pracovní postup úspěšně zahájíte.</span><span class="sxs-lookup"><span data-stu-id="2f95a-138">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="2f95a-139">volání ověření, najdete v části [ověření aktivity vyvolání](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="2f95a-139"> invoking validation, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>
