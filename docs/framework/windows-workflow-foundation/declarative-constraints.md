---
title: Deklarativní omezení
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 5599513405c77aa213b329b085075660baed5c47
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842369"
---
# <a name="declarative-constraints"></a>Deklarativní omezení
Deklarativní omezení poskytují výkonný způsob ověření aktivita a její vztahy s ostatními aktivitami. Omezení jsou konfigurovány pro aktivitu během procesu vytváření, ale je také možné zadat další omezení, tak hostitele pracovního postupu. Toto téma obsahuje přehled používání deklarativní omezení pro ověřování aktivity.  
  
## <a name="using-declarative-constraints"></a>Použití deklarativní omezení  
 Omezení je aktivitou, která obsahuje logiku ověřování. Tato aktivita omezení se můžou vytvořit v kódu nebo v XAML. Po vytvoření aktivity omezení autoři aktivitu přidat tomuto omezení <xref:System.Activities.Activity.Constraints%2A> vlastnost aktivity k ověření, nebo používají omezení pro další ověřování s použitím <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> vlastnost <xref:System.Activities.Validation.ValidationSettings> instance . Logiku ověřování se může skládat z jednoduchého ověření, jako je například ověřování metadat aktivity, ale můžete také provést ověření, který bere v úvahu vztah aktuální aktivitu do aktivity jeho nadřazeného, podřízené položky a na stejné úrovni. Omezení jsou vytvořené s použitím <xref:System.Activities.Validation.Constraint%601> aktivity a několika dalších ověřování aktivit jsou k dispozici jako pomoc s vytváření chyby a upozornění ověření a k poskytnutí informací o související aktivity v pracovním postupu.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation a metodu AddValidationError  
 <xref:System.Activities.Validation.AssertValidation> Aktivita vyhodnotí výraz odkazuje jeho <xref:System.Activities.Validation.AssertValidation.Assertion%2A> vlastnost, a pokud je výraz vyhodnocen `false`, upozornění a chyby ověřování se přidá do <xref:System.Activities.Validation.ValidationResults>. <xref:System.Activities.Validation.AssertValidation.Message%2A> Vlastnost popisuje chybu ověření a <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> vlastnost určuje, zda Chyba ověřování je chybu nebo upozornění. Výchozí hodnota pro <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> je `false`.  
  
 V následujícím příkladu je deklarován omezení, která vrací upozornění ověření, pokud <xref:System.Activities.Activity.DisplayName%2A> aktivity se ověřují se dvou znaků nebo méně. Parametr obecného typu pro <xref:System.Activities.Validation.Constraint%601> Určuje typ aktivity, který je potvrzen v omezení. Toto omezení používá <xref:System.Activities.Activity> jako obecného typu a slouží k ověření všech druhů aktivit.  
  
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
  
 Pokud chcete zadat toto omezení pro aktivitu, přidá se do <xref:System.Activities.Activity.Constraints%2A> aktivity, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Hostitel může také určit toto omezení pro aktivity v pracovním postupu pomocí <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, který je popsaný v další části.  
  
 <xref:System.Activities.Validation.AddValidationError> Aktivita se používá k vygenerování upozornění a Chyba ověření bez nutnosti vyhodnocení výrazu. Její vlastnosti jsou podobné <xref:System.Activities.Validation.AssertValidation> a ho můžou používat ve spojení s aktivity toku řízení omezení, jako <xref:System.Activities.Statements.If> aktivity.
  
### <a name="workflow-relationship-activities"></a>Relace aktivit pracovního postupu

Jsou k dispozici několik ověřování aktivity, které poskytují informace o aktivitách pracovního postupu ve vztahu k aktivity ověřován. <xref:System.Activities.Validation.GetParentChain> Vrátí kolekci aktivity, která obsahuje všechny aktivity mezi aktuální aktivitu a kořenovou aktivitu. <xref:System.Activities.Validation.GetChildSubtree> obsahuje kolekce aktivit, která obsahuje podřízené aktivity ve vzoru rekurzivní a <xref:System.Activities.Validation.GetWorkflowTree> získá všechny aktivity v pracovním postupu.  
  
V následujícím příkladu `CreateState` aktivity je definována. `CreateState` Aktivity musí být obsažena v rámci `CreateCountry` aktivitu a `GetParent` metoda vrátí omezení, které vynucuje tento požadavek. `GetParent` používá <xref:System.Activities.Validation.GetParentChain> aktivity ve spojení s <xref:System.Activities.Statements.ForEach%601> aktivita ke kontrole nadřazené aktivity `CreateState` aktivity a určit, pokud požadavek se splní.  
  
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
 Autoři hostitele pracovního postupu můžete určit další ověření omezení pro aktivity v pracovním postupu vytváření omezení a jejich přidání na <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> slovník <xref:System.Activities.Validation.ValidationSettings> instance. Každou položku v <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> obsahuje typ aktivity, pro které platí omezení a seznam další omezení pro tento typ aktivity. Při vyvolání ověření pracovního postupu, každá aktivita zadaného typu, včetně odvozených tříd, vyhodnotí jako omezení. V tomto příkladu `ActivityDisplayNameIsNotSetWarning` omezením z předchozí části platí pro všechny aktivity v pracovním postupu.  
  
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
  
 Pokud <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> vlastnost <xref:System.Activities.Validation.ValidationSettings> je `true`, pak pouze zadaný další omezení se vyhodnocují při vyvolání ověření zavoláním <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. To může být užitečné pro kontrolu pracovních postupů pro ověřování podle konfigurace. Všimněte si však, že když uživatel vyvolá pracovní postup, logiku ověřování, které jsou nakonfigurované v pracovním postupu je vyhodnocen a musíte předat pro pracovní postup, chcete-li úspěšně začít. Další informace o vyvolání ověřování najdete v tématu [vyvolání ověřování aktivit](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).
