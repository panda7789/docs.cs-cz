---
title: Ověřování na základě imperativního kódu
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 333e1e200825dd1fc8ed750abbecbb309da66663
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009770"
---
# <a name="imperative-code-based-validation"></a>Ověřování na základě imperativního kódu

Imperativní ověřování na základě kódu poskytuje jednoduchý způsob pro aktivitu pro ověřování o sobě a je k dispozici pro aktivity, které jsou odvozeny z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>. Ověřovací kód, který určuje všechny chyby nebo varování ověření je přidána do aktivity.  
  
## <a name="using-code-based-validation"></a>Použití ověřování na základě kódu

Podporuje ověřování na základě kódu aktivity, které jsou odvozeny z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>. Kód pro ověření je možné použít v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat a chyby nebo varování ověření lze přidat na argument metadat. V následujícím příkladu Pokud `Cost` je větší než `Price`, chyby ověřování se přidá do metadat.  
  
> [!NOTE]
> Všimněte si, že `Cost` a `Price` nejsou argumenty na aktivitu, ale jsou vlastnosti, které jsou nastaveny v době návrhu. To znamená proč jejich hodnoty můžete ověřit v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat. Hodnota dat předávaných argument nejde ověřit v době návrhu, protože není až do spuštění toku dat, ale může být ověřen argumenty aktivity k zajištění, že jsou vázány s použitím `RequiredArgument` atribut a skupiny přetížení. Tento příklad kódu se zobrazí `RequiredArgument` atribut pro `Description` argument a pokud příčka není svázána, je vygenerována chyba ověření. Povinné argumenty jsou popsané v [povinné argumenty a skupiny přetížení](required-arguments-and-overload-groups.md).  
  
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
  
 Ve výchozím nastavení, se přidá chyby ověření v metadatech při <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> je volána. Chcete-li přidat upozornění ověření, použijte <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> přetížení, které přijímá <xref:System.Activities.Validation.ValidationError>a určit, že <xref:System.Activities.Validation.ValidationError> představuje upozornění tak, že nastavíte <xref:System.Activities.Validation.ValidationError.IsWarning%2A> vlastnost.  
  
 Ověření vyvolá se při změně pracovního postupu v Návrháři pracovních postupů a všechny chyby nebo varování ověření se zobrazí v Návrháři pracovních postupů. Ověření se také dojde za běhu, když uživatel vyvolá pracovní postup, a pokud dojde k chybám ověření, <xref:System.Activities.InvalidWorkflowException> logiku ověřování výchozí vyvolá výjimku. Další informace o volání ověřování a přístup k žádným ověření upozornění ani chyby, najdete v části [vyvolání ověřování aktivit](invoking-activity-validation.md).  
  
 Všechny výjimky, které jsou vyvolány z <xref:System.Activities.CodeActivity.CacheMetadata%2A> nemají být považována za chyby ověření. Tyto výjimky budou návrat z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a volající musí být zpracován.  
  
 Ověřování na základě kódu je užitečné pro ověřování aktivity, která obsahuje kód, ale nemá vhled do další aktivity v pracovním postupu. Deklarativní omezení ověření umožňuje ověřovat vztahy mezi aktivity a další aktivity v pracovním postupu a věnuje se [deklarativní omezení](declarative-constraints.md) tématu.
