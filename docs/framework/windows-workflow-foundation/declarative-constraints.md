---
title: Deklarativní omezení
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 321021e3d73daecae07268f33807c992414a7b4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182963"
---
# <a name="declarative-constraints"></a><span data-ttu-id="3cda5-102">Deklarativní omezení</span><span class="sxs-lookup"><span data-stu-id="3cda5-102">Declarative Constraints</span></span>
<span data-ttu-id="3cda5-103">Deklarativní omezení poskytují výkonnou metodu ověření aktivity a její vztahy s jinými aktivitami.</span><span class="sxs-lookup"><span data-stu-id="3cda5-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="3cda5-104">Omezení jsou konfigurována pro aktivitu během procesu vytváření, ale další omezení mohou být také určena hostitelem pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3cda5-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="3cda5-105">Toto téma obsahuje přehled použití deklarativních omezení k ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="3cda5-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="3cda5-106">Použití deklarativních omezení</span><span class="sxs-lookup"><span data-stu-id="3cda5-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="3cda5-107">Omezení je aktivita, která obsahuje logiku ověření.</span><span class="sxs-lookup"><span data-stu-id="3cda5-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="3cda5-108">Tato aktivita omezení může být vytvořena v kódu nebo v XAML.</span><span class="sxs-lookup"><span data-stu-id="3cda5-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="3cda5-109">Po vytvoření aktivity omezení autoři aktivity <xref:System.Activities.Activity.Constraints%2A> přidat toto omezení vlastnost aktivity k ověření nebo používají <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> omezení <xref:System.Activities.Validation.ValidationSettings> poskytnout další ověření pomocí vlastnost instance.</span><span class="sxs-lookup"><span data-stu-id="3cda5-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="3cda5-110">Logika ověření se může skládat z jednoduchých ověření, jako je například ověření metadat aktivity, ale může také provádět ověření, které bere v úvahu vztah aktuální aktivity k nadřazeným, podřízeným a na sourozeneckým aktivitám.</span><span class="sxs-lookup"><span data-stu-id="3cda5-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="3cda5-111">Omezení jsou vytvářena pomocí <xref:System.Activities.Validation.Constraint%601> aktivity a několik dalších ověřovacích aktivit je poskytováno, aby pomohly při vytváření chyb ověření a upozornění a poskytly informace o souvisejících aktivitách v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="3cda5-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="3cda5-112">AssertValidation a AddValidationError</span><span class="sxs-lookup"><span data-stu-id="3cda5-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="3cda5-113">Aktivita <xref:System.Activities.Validation.AssertValidation> vyhodnotí výraz, <xref:System.Activities.Validation.AssertValidation.Assertion%2A> na který odkazuje jeho vlastnost, a pokud je výraz vyhodnocen na `false`, je do pole <xref:System.Activities.Validation.ValidationResults>přidána chyba ověření nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="3cda5-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="3cda5-114">Vlastnost <xref:System.Activities.Validation.AssertValidation.Message%2A> popisuje chybu ověření a <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> vlastnost označuje, zda je chyba ověření chyba nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="3cda5-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="3cda5-115">Výchozí hodnota <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> pro `false`je .</span><span class="sxs-lookup"><span data-stu-id="3cda5-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="3cda5-116">V následujícím příkladu je deklarováno omezení, které vrací upozornění ověření, <xref:System.Activities.Activity.DisplayName%2A> pokud je ověřovaná aktivita dva znaky nebo méně dlouhá.</span><span class="sxs-lookup"><span data-stu-id="3cda5-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="3cda5-117">Parametr obecného typu <xref:System.Activities.Validation.Constraint%601> použitý pro určuje typ aktivity, která je ověřena omezením.</span><span class="sxs-lookup"><span data-stu-id="3cda5-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="3cda5-118">Toto <xref:System.Activities.Activity> omezení používá jako obecný typ a lze jej použít k ověření všech typů aktivit.</span><span class="sxs-lookup"><span data-stu-id="3cda5-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
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
  
 <span data-ttu-id="3cda5-119">Chcete-li zadat toto omezení pro <xref:System.Activities.Activity.Constraints%2A> aktivitu, je přidán do aktivity, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="3cda5-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="3cda5-120">Hostitel může také určit toto omezení pro <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>aktivity v pracovním postupu pomocí , který je popsán v další části.</span><span class="sxs-lookup"><span data-stu-id="3cda5-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="3cda5-121">Aktivita <xref:System.Activities.Validation.AddValidationError> se používá ke generování chyby ověření nebo upozornění bez nutnosti vyhodnocení výrazu.</span><span class="sxs-lookup"><span data-stu-id="3cda5-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="3cda5-122">Jeho vlastnosti <xref:System.Activities.Validation.AssertValidation> jsou podobné a lze jej použít ve spojení s <xref:System.Activities.Statements.If> aktivitami řízení toku omezení, jako je například aktivita.</span><span class="sxs-lookup"><span data-stu-id="3cda5-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="3cda5-123">Aktivity vztahů pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3cda5-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="3cda5-124">K dispozici je několik aktivit ověření, které poskytují informace o ostatních aktivitách v pracovním postupu ve vztahu k ověřované aktivitě.</span><span class="sxs-lookup"><span data-stu-id="3cda5-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="3cda5-125"><xref:System.Activities.Validation.GetParentChain>vrátí kolekci aktivit, která obsahuje všechny aktivity mezi aktuální aktivitou a kořenovou aktivitou.</span><span class="sxs-lookup"><span data-stu-id="3cda5-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="3cda5-126"><xref:System.Activities.Validation.GetChildSubtree>poskytuje kolekci aktivit, které obsahuje podřízené aktivity v <xref:System.Activities.Validation.GetWorkflowTree> rekurzivní vzor a získá všechny aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="3cda5-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="3cda5-127">V následujícím příkladu `CreateState` je definována aktivita.</span><span class="sxs-lookup"><span data-stu-id="3cda5-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="3cda5-128">Aktivita `CreateState` musí být obsažena v `CreateCountry` `GetParent` rámci aktivity a metoda vrátí omezení, které vynucuje tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="3cda5-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="3cda5-129">`GetParent`používá <xref:System.Activities.Validation.GetParentChain> aktivitu ve <xref:System.Activities.Statements.ForEach%601> spojení s aktivitou ke `CreateState` kontrole nadřazených aktivit aktivity k určení, zda je splněn požadavek.</span><span class="sxs-lookup"><span data-stu-id="3cda5-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
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
  
## <a name="additional-constraints"></a><span data-ttu-id="3cda5-130">Další omezení</span><span class="sxs-lookup"><span data-stu-id="3cda5-130">Additional Constraints</span></span>  
 <span data-ttu-id="3cda5-131">Autoři hostitele pracovního postupu mohou určit další omezení ověření pro aktivity <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> v pracovním <xref:System.Activities.Validation.ValidationSettings> postupu vytvořením omezení a jejich přidáním do slovníku instance.</span><span class="sxs-lookup"><span data-stu-id="3cda5-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="3cda5-132">Každá položka <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> v obsahuje typ aktivity, pro které se vztahují omezení a seznam dalších omezení pro tento typ aktivity.</span><span class="sxs-lookup"><span data-stu-id="3cda5-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="3cda5-133">Při ověřování je vyvolána pro pracovní postup, každá aktivita zadaného typu, včetně odvozených tříd, vyhodnotí omezení.</span><span class="sxs-lookup"><span data-stu-id="3cda5-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="3cda5-134">V tomto příkladu `ActivityDisplayNameIsNotSetWarning` je omezení z předchozí části použito na všechny aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="3cda5-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="3cda5-135">Pokud <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> <xref:System.Activities.Validation.ValidationSettings> je vlastnost `true`, pak jsou vyhodnocena pouze zadaná <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>další omezení při volání ověření .</span><span class="sxs-lookup"><span data-stu-id="3cda5-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="3cda5-136">To může být užitečné pro kontrolu pracovních postupů pro konkrétní konfigurace ověření.</span><span class="sxs-lookup"><span data-stu-id="3cda5-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="3cda5-137">Všimněte si však, že při vyvolání pracovního postupu je vyhodnocena ověřovací logika nakonfigurovaná v pracovním postupu a musí úspěšně předat pracovní postup, aby mohl úspěšně začít.</span><span class="sxs-lookup"><span data-stu-id="3cda5-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="3cda5-138">Další informace o vyvolání ověření naleznete [v tématu Vyvolání ověření aktivity](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="3cda5-138">For more information about invoking validation, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>
