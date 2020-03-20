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
# <a name="declarative-constraints"></a>Deklarativní omezení
Deklarativní omezení poskytují výkonnou metodu ověření aktivity a její vztahy s jinými aktivitami. Omezení jsou konfigurována pro aktivitu během procesu vytváření, ale další omezení mohou být také určena hostitelem pracovního postupu. Toto téma obsahuje přehled použití deklarativních omezení k ověření aktivity.  
  
## <a name="using-declarative-constraints"></a>Použití deklarativních omezení  
 Omezení je aktivita, která obsahuje logiku ověření. Tato aktivita omezení může být vytvořena v kódu nebo v XAML. Po vytvoření aktivity omezení autoři aktivity <xref:System.Activities.Activity.Constraints%2A> přidat toto omezení vlastnost aktivity k ověření nebo používají <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> omezení <xref:System.Activities.Validation.ValidationSettings> poskytnout další ověření pomocí vlastnost instance. Logika ověření se může skládat z jednoduchých ověření, jako je například ověření metadat aktivity, ale může také provádět ověření, které bere v úvahu vztah aktuální aktivity k nadřazeným, podřízeným a na sourozeneckým aktivitám. Omezení jsou vytvářena pomocí <xref:System.Activities.Validation.Constraint%601> aktivity a několik dalších ověřovacích aktivit je poskytováno, aby pomohly při vytváření chyb ověření a upozornění a poskytly informace o souvisejících aktivitách v pracovním postupu.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation a AddValidationError  
 Aktivita <xref:System.Activities.Validation.AssertValidation> vyhodnotí výraz, <xref:System.Activities.Validation.AssertValidation.Assertion%2A> na který odkazuje jeho vlastnost, a pokud je výraz vyhodnocen na `false`, je do pole <xref:System.Activities.Validation.ValidationResults>přidána chyba ověření nebo upozornění. Vlastnost <xref:System.Activities.Validation.AssertValidation.Message%2A> popisuje chybu ověření a <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> vlastnost označuje, zda je chyba ověření chyba nebo upozornění. Výchozí hodnota <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> pro `false`je .  
  
 V následujícím příkladu je deklarováno omezení, které vrací upozornění ověření, <xref:System.Activities.Activity.DisplayName%2A> pokud je ověřovaná aktivita dva znaky nebo méně dlouhá. Parametr obecného typu <xref:System.Activities.Validation.Constraint%601> použitý pro určuje typ aktivity, která je ověřena omezením. Toto <xref:System.Activities.Activity> omezení používá jako obecný typ a lze jej použít k ověření všech typů aktivit.  
  
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
  
 Chcete-li zadat toto omezení pro <xref:System.Activities.Activity.Constraints%2A> aktivitu, je přidán do aktivity, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Hostitel může také určit toto omezení pro <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>aktivity v pracovním postupu pomocí , který je popsán v další části.  
  
 Aktivita <xref:System.Activities.Validation.AddValidationError> se používá ke generování chyby ověření nebo upozornění bez nutnosti vyhodnocení výrazu. Jeho vlastnosti <xref:System.Activities.Validation.AssertValidation> jsou podobné a lze jej použít ve spojení s <xref:System.Activities.Statements.If> aktivitami řízení toku omezení, jako je například aktivita.
  
### <a name="workflow-relationship-activities"></a>Aktivity vztahů pracovního postupu

K dispozici je několik aktivit ověření, které poskytují informace o ostatních aktivitách v pracovním postupu ve vztahu k ověřované aktivitě. <xref:System.Activities.Validation.GetParentChain>vrátí kolekci aktivit, která obsahuje všechny aktivity mezi aktuální aktivitou a kořenovou aktivitou. <xref:System.Activities.Validation.GetChildSubtree>poskytuje kolekci aktivit, které obsahuje podřízené aktivity v <xref:System.Activities.Validation.GetWorkflowTree> rekurzivní vzor a získá všechny aktivity v pracovním postupu.  
  
V následujícím příkladu `CreateState` je definována aktivita. Aktivita `CreateState` musí být obsažena v `CreateCountry` `GetParent` rámci aktivity a metoda vrátí omezení, které vynucuje tento požadavek. `GetParent`používá <xref:System.Activities.Validation.GetParentChain> aktivitu ve <xref:System.Activities.Statements.ForEach%601> spojení s aktivitou ke `CreateState` kontrole nadřazených aktivit aktivity k určení, zda je splněn požadavek.  
  
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
  
## <a name="additional-constraints"></a>Další omezení  
 Autoři hostitele pracovního postupu mohou určit další omezení ověření pro aktivity <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> v pracovním <xref:System.Activities.Validation.ValidationSettings> postupu vytvořením omezení a jejich přidáním do slovníku instance. Každá položka <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> v obsahuje typ aktivity, pro které se vztahují omezení a seznam dalších omezení pro tento typ aktivity. Při ověřování je vyvolána pro pracovní postup, každá aktivita zadaného typu, včetně odvozených tříd, vyhodnotí omezení. V tomto příkladu `ActivityDisplayNameIsNotSetWarning` je omezení z předchozí části použito na všechny aktivity v pracovním postupu.  
  
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
  
 Pokud <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> <xref:System.Activities.Validation.ValidationSettings> je vlastnost `true`, pak jsou vyhodnocena pouze zadaná <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>další omezení při volání ověření . To může být užitečné pro kontrolu pracovních postupů pro konkrétní konfigurace ověření. Všimněte si však, že při vyvolání pracovního postupu je vyhodnocena ověřovací logika nakonfigurovaná v pracovním postupu a musí úspěšně předat pracovní postup, aby mohl úspěšně začít. Další informace o vyvolání ověření naleznete [v tématu Vyvolání ověření aktivity](invoking-activity-validation.md).
