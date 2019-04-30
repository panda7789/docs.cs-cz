---
title: Deklarativní omezení
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: e3ced8f6f88d698273ace5c8b74fe90b94fa9720
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945818"
---
# <a name="declarative-constraints"></a><span data-ttu-id="05fd0-102">Deklarativní omezení</span><span class="sxs-lookup"><span data-stu-id="05fd0-102">Declarative Constraints</span></span>
<span data-ttu-id="05fd0-103">Deklarativní omezení poskytují výkonný způsob ověření aktivita a její vztahy s ostatními aktivitami.</span><span class="sxs-lookup"><span data-stu-id="05fd0-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="05fd0-104">Omezení jsou konfigurovány pro aktivitu během procesu vytváření, ale je také možné zadat další omezení, tak hostitele pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="05fd0-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="05fd0-105">Toto téma obsahuje přehled používání deklarativní omezení pro ověřování aktivity.</span><span class="sxs-lookup"><span data-stu-id="05fd0-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="05fd0-106">Použití deklarativní omezení</span><span class="sxs-lookup"><span data-stu-id="05fd0-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="05fd0-107">Omezení je aktivitou, která obsahuje logiku ověřování.</span><span class="sxs-lookup"><span data-stu-id="05fd0-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="05fd0-108">Tato aktivita omezení se můžou vytvořit v kódu nebo v XAML.</span><span class="sxs-lookup"><span data-stu-id="05fd0-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="05fd0-109">Po vytvoření aktivity omezení autoři aktivitu přidat tomuto omezení <xref:System.Activities.Activity.Constraints%2A> vlastnost aktivity k ověření, nebo používají omezení pro další ověřování s použitím <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> vlastnost <xref:System.Activities.Validation.ValidationSettings> instance .</span><span class="sxs-lookup"><span data-stu-id="05fd0-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="05fd0-110">Logiku ověřování se může skládat z jednoduchého ověření, jako je například ověřování metadat aktivity, ale můžete také provést ověření, který bere v úvahu vztah aktuální aktivitu do aktivity jeho nadřazeného, podřízené položky a na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="05fd0-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="05fd0-111">Omezení jsou vytvořené s použitím <xref:System.Activities.Validation.Constraint%601> aktivity a několika dalších ověřování aktivit jsou k dispozici jako pomoc s vytváření chyby a upozornění ověření a k poskytnutí informací o související aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="05fd0-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="05fd0-112">AssertValidation a metodu AddValidationError</span><span class="sxs-lookup"><span data-stu-id="05fd0-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="05fd0-113"><xref:System.Activities.Validation.AssertValidation> Aktivita vyhodnotí výraz odkazuje jeho <xref:System.Activities.Validation.AssertValidation.Assertion%2A> vlastnost, a pokud je výraz vyhodnocen `false`, upozornění a chyby ověřování se přidá do <xref:System.Activities.Validation.ValidationResults>.</span><span class="sxs-lookup"><span data-stu-id="05fd0-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="05fd0-114"><xref:System.Activities.Validation.AssertValidation.Message%2A> Vlastnost popisuje chybu ověření a <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> vlastnost určuje, zda Chyba ověřování je chybu nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="05fd0-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="05fd0-115">Výchozí hodnota pro <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> je `false`.</span><span class="sxs-lookup"><span data-stu-id="05fd0-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="05fd0-116">V následujícím příkladu je deklarován omezení, která vrací upozornění ověření, pokud <xref:System.Activities.Activity.DisplayName%2A> aktivity se ověřují se dvou znaků nebo méně.</span><span class="sxs-lookup"><span data-stu-id="05fd0-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="05fd0-117">Parametr obecného typu pro <xref:System.Activities.Validation.Constraint%601> Určuje typ aktivity, který je potvrzen v omezení.</span><span class="sxs-lookup"><span data-stu-id="05fd0-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="05fd0-118">Toto omezení používá <xref:System.Activities.Activity> jako obecného typu a slouží k ověření všech druhů aktivit.</span><span class="sxs-lookup"><span data-stu-id="05fd0-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
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
  
 <span data-ttu-id="05fd0-119">Pokud chcete zadat toto omezení pro aktivitu, přidá se do <xref:System.Activities.Activity.Constraints%2A> aktivity, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="05fd0-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="05fd0-120">Hostitel může také určit toto omezení pro aktivity v pracovním postupu pomocí <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, který je popsaný v další části.</span><span class="sxs-lookup"><span data-stu-id="05fd0-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="05fd0-121"><xref:System.Activities.Validation.AddValidationError> Aktivita se používá k vygenerování upozornění a Chyba ověření bez nutnosti vyhodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="05fd0-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="05fd0-122">Její vlastnosti jsou podobné <xref:System.Activities.Validation.AssertValidation> a ho můžou používat ve spojení s aktivity toku řízení omezení, jako <xref:System.Activities.Statements.If> aktivity.</span><span class="sxs-lookup"><span data-stu-id="05fd0-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="05fd0-123">Relace aktivit pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="05fd0-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="05fd0-124">Jsou k dispozici několik ověřování aktivity, které poskytují informace o aktivitách pracovního postupu ve vztahu k aktivity ověřován.</span><span class="sxs-lookup"><span data-stu-id="05fd0-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="05fd0-125"><xref:System.Activities.Validation.GetParentChain> Vrátí kolekci aktivity, která obsahuje všechny aktivity mezi aktuální aktivitu a kořenovou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="05fd0-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="05fd0-126"><xref:System.Activities.Validation.GetChildSubtree> obsahuje kolekce aktivit, která obsahuje podřízené aktivity ve vzoru rekurzivní a <xref:System.Activities.Validation.GetWorkflowTree> získá všechny aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="05fd0-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="05fd0-127">V následujícím příkladu `CreateState` aktivity je definována.</span><span class="sxs-lookup"><span data-stu-id="05fd0-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="05fd0-128">`CreateState` Aktivity musí být obsažena v rámci `CreateCountry` aktivitu a `GetParent` metoda vrátí omezení, které vynucuje tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="05fd0-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="05fd0-129">`GetParent` používá <xref:System.Activities.Validation.GetParentChain> aktivity ve spojení s <xref:System.Activities.Statements.ForEach%601> aktivita ke kontrole nadřazené aktivity `CreateState` aktivity a určit, pokud požadavek se splní.</span><span class="sxs-lookup"><span data-stu-id="05fd0-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
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
  
## <a name="additional-constraints"></a><span data-ttu-id="05fd0-130">Další omezení</span><span class="sxs-lookup"><span data-stu-id="05fd0-130">Additional Constraints</span></span>  
 <span data-ttu-id="05fd0-131">Autoři hostitele pracovního postupu můžete určit další ověření omezení pro aktivity v pracovním postupu vytváření omezení a jejich přidání na <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> slovník <xref:System.Activities.Validation.ValidationSettings> instance.</span><span class="sxs-lookup"><span data-stu-id="05fd0-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="05fd0-132">Každou položku v <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> obsahuje typ aktivity, pro které platí omezení a seznam další omezení pro tento typ aktivity.</span><span class="sxs-lookup"><span data-stu-id="05fd0-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="05fd0-133">Při vyvolání ověření pracovního postupu, každá aktivita zadaného typu, včetně odvozených tříd, vyhodnotí jako omezení.</span><span class="sxs-lookup"><span data-stu-id="05fd0-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="05fd0-134">V tomto příkladu `ActivityDisplayNameIsNotSetWarning` omezením z předchozí části platí pro všechny aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="05fd0-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="05fd0-135">Pokud <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> vlastnost <xref:System.Activities.Validation.ValidationSettings> je `true`, pak pouze zadaný další omezení se vyhodnocují při vyvolání ověření zavoláním <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="05fd0-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="05fd0-136">To může být užitečné pro kontrolu pracovních postupů pro ověřování podle konfigurace.</span><span class="sxs-lookup"><span data-stu-id="05fd0-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="05fd0-137">Všimněte si však, že když uživatel vyvolá pracovní postup, logiku ověřování, které jsou nakonfigurované v pracovním postupu je vyhodnocen a musíte předat pro pracovní postup, chcete-li úspěšně začít.</span><span class="sxs-lookup"><span data-stu-id="05fd0-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="05fd0-138">Další informace o vyvolání ověřování najdete v tématu [vyvolání ověřování aktivit](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="05fd0-138">For more information about invoking validation, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>
