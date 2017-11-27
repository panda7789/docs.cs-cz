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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a51f77864478dcefbe5b2742288f9cc91648f7bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="declarative-constraints"></a>Deklarativní omezení
Deklarativní omezení poskytují výkonný metodu ověření pro aktivitu a jeho vztahů s dalšími aktivitami. Omezení jsou nakonfigurovány pro aktivitu během procesu vytváření, ale další omezení lze zadat také od hostitele pracovního postupu. Toto téma obsahuje přehled používání deklarativní omezení pro ověřování aktivity.  
  
## <a name="using-declarative-constraints"></a>Pomocí deklarativní omezení  
 Omezení je aktivitou, která obsahuje logiku ověření. Tato aktivita omezení můžete vytvořené v kódu nebo v jazyce XAML. Po vytvoření aktivity omezení autoři aktivitu přidat tomuto omezení <xref:System.Activities.Activity.Constraints%2A> vlastnost aktivity na ověřit, nebo se používají pro další ověřování pomocí omezení <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> vlastnost <xref:System.Activities.Validation.ValidationSettings> instance . Logiku ověření se může skládat z jednoduché ověření, jako je například ověřování aktivity metadata, ale můžete také provést ověření, který bere v úvahu relace aktuální aktivity k její nadřazené, děti a na stejné úrovni jako aktivity. Omezení vytvořené pomocí <xref:System.Activities.Validation.Constraint%601> aktivity a několik dalších ověření aktivity jsou uvedeny vám pomůže při vytváření ověření chyby a upozornění a k poskytování informací o souvisejících činností v pracovním postupu.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation a AddValidationError  
 <xref:System.Activities.Validation.AssertValidation> Aktivita vyhodnotí výraz odkazuje jeho <xref:System.Activities.Validation.AssertValidation.Assertion%2A> vlastnost, a pokud je výsledkem výrazu `false`, ověření chyby nebo upozornění je přidán do <xref:System.Activities.Validation.ValidationResults>. <xref:System.Activities.Validation.AssertValidation.Message%2A> Vlastnost popisuje chybu ověření a <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> vlastnost určuje, zda je chybu ověřování k chybě nebo upozornění. Výchozí hodnota pro <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> je `false`.  
  
 V následujícím příkladu je deklarován omezení, která vrací upozornění ověření, pokud <xref:System.Activities.Activity.DisplayName%2A> aktivity ověřován je dva znaků nebo méně. Parametr obecného typu používá pro <xref:System.Activities.Validation.Constraint%601> Určuje typ aktivity, které je ověřeno omezením. Toto omezení používá <xref:System.Activities.Activity> jako Obecné zadejte a slouží k ověření všechny typy aktivit.  
  
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
  
 Pokud chcete zadat toto omezení pro aktivitu, je přidán do <xref:System.Activities.Activity.Constraints%2A> aktivity, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Hostitel může také zadat toto omezení pro aktivity v pracovním postupu pomocí <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, která je popsaná v další části.  
  
 <xref:System.Activities.Validation.AddValidationError> Aktivity se používá ke generování ověřování chyb nebo upozornění bez nutnosti vyhodnocení výrazu. Jeho vlastnosti jsou podobné <xref:System.Activities.Validation.AssertValidation> a lze jej použít ve spojení s aktivity toku řízení omezení, jako <xref:System.Activities.Statements.If> aktivity.  
  
### <a name="workflow-relationship-activities"></a>Aktivity pracovního postupu relace  
 Jsou k dispozici několik ověření aktivity které poskytují informace o další aktivity v pracovním postupu ve vztahu k aktivity, která je ověřována. <xref:System.Activities.Validation.GetParentChain>Vrátí kolekci aktivity, která obsahuje všechny aktivity mezi aktuální aktivitu a kořenové aktivity. <xref:System.Activities.Validation.GetChildSubtree>poskytuje kolekci aktivity, která obsahuje podřízené aktivity v rekurzivní vzor, a <xref:System.Activities.Validation.GetWorkflowTree> získá všechny aktivity v pracovním postupu.  
  
 V následujícím příkladu z [ověření vztahy aktivity](../../../docs/framework/windows-workflow-foundation/samples/activity-relationships-validation.md) ukázce `CreateState` aktivity je definována. `CreateState` Aktivity musí být obsažena v `CreateCountry` aktivitu a `GetParent` metoda vrátí omezení, které vynucuje tento požadavek. `GetParent`používá <xref:System.Activities.Validation.GetParentChain> aktivity ve spojení s <xref:System.Activities.Statements.ForEach%601> aktivita ke kontrole nadřazené aktivity `CreateState` aktivity a určit, pokud se splní požadavek.  
  
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
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]Windows Workflow Foundation [ověření](../../../docs/framework/windows-workflow-foundation/samples/validation.md) ukázky.  
  
## <a name="additional-constraints"></a>Další omezení  
 Autoři hostitele pracovního postupu můžete zadat omezení další ověřování pro aktivity v pracovním postupu vytváření omezení a jejich přidáním <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> slovník <xref:System.Activities.Validation.ValidationSettings> instance. Každá položka v <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> obsahuje typ aktivity, pro který platí omezení a seznam další omezení pro tento typ aktivity. Po vyvolání ověření pro pracovní postup Každá aktivita zadaného typu, včetně odvozené třídy, vyhodnotí se omezení. V tomto příkladu `ActivityDisplayNameIsNotSetWarning` omezení z předchozí části platí pro všechny aktivity v pracovním postupu.  
  
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
  
 Pokud <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> vlastnost <xref:System.Activities.Validation.ValidationSettings> je `true`, pak pouze zadané další omezení jsou vyhodnocována po ověření je vyvolán při volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. To může být užitečné pro zkontrolujete pracovní postupy pro ověřování podle konfigurace. Všimněte si ale, že po vyvolání pracovního postupu logiku ověření nakonfigurované v pracovním postupu vyhodnotí a musí projít pro pracovní postup úspěšně zahájíte. [!INCLUDE[crabout](../../../includes/crabout-md.md)]volání ověření, najdete v části [ověření aktivity vyvolání](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).
