---
title: Imperativní ověření založené na kódu
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 87585050d7ab8c9adc5f0ac4ac5396862975cc25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515455"
---
# <a name="imperative-code-based-validation"></a>Imperativní ověření založené na kódu
Imperativní ověřování založené na kódu poskytuje jednoduchý způsob, jak aktivity pro ověřování o samotné a je k dispozici pro aktivity, které jsou odvozeny od <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>. Ověřovací kód, který určuje všechny chyby ověření nebo upozornění je přidána do aktivity.  
  
## <a name="using-code-based-validation"></a>Pomocí ověřování založené na kódu  
 Podporuje ověřování založené na kódu aktivity, které jsou odvozeny od <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>. Ověření kódu mohou být umístěny v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsání a ověření chyby nebo výstrahy mohou být přidány do argument metadat. V následujícím příkladu převzat ze [základní ověření](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) ukázkové, pokud `Cost` je větší než `Price`, Chyba ověření se přidá do metadat.  
  
> [!NOTE]
>  Všimněte si, že `Cost` a `Price` nejsou argumenty pro aktivity, ale jsou vlastnosti, které jsou nastaveny v době návrhu. To znamená proč jejich hodnoty lze ověřit v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat. Hodnota dat předávaných mezi argument nelze ověřit v době návrhu, protože není až do spuštění toku dat, ale argumenty aktivity může být ověřen zajistit, že je vázána pomocí `RequiredArgument` atribut a přetížení skupiny. Tento příklad kódu se zobrazí `RequiredArgument` atribut pro `Description` argument a pokud není vázaný a je generována chyba ověření. Vyžaduje argumenty jsou popsané v [vyžaduje argumenty a přetížení skupiny](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).  
  
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
  
 Ve výchozím nastavení, je chyba ověření do metadat při <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> je volána. K přidání upozornění ověření použijte <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> přetížení, které přijímá <xref:System.Activities.Validation.ValidationError>a určit, že <xref:System.Activities.Validation.ValidationError> představuje upozornění nastavením <xref:System.Activities.Validation.ValidationError.IsWarning%2A> vlastnost.  
  
 Ověření nastane, když pracovní postup se mění v Návrháři pracovních postupů a všechny chyby ověření nebo upozornění se zobrazí v Návrháři pracovních postupů. Ověřování také dochází za běhu, při vyvolání pracovního postupu, a pokud dojde k chybám ověření, <xref:System.Activities.InvalidWorkflowException> logiku ověření výchozí vyvolá výjimku. Další informace o vyvolání ověření a přístup k žádné ověření varování nebo chyby najdete v tématu [ověření aktivity vyvolání](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
 Jakékoli výjimky, které jsou vyvolány z <xref:System.Activities.CodeActivity.CacheMetadata%2A> nejsou považovány za chyby ověření. Tyto výjimky bude vyhnuli z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a musí být zpracována volající.  
  
 Ověřování založené na kódu je užitečné pro ověřování aktivity, která obsahuje kód, ale nemá viditelnost do další aktivity v pracovním postupu. Deklarativní omezení ověření poskytuje možnost ověření vztahy mezi aktivity a další aktivity v pracovním postupu a věnuje se [deklarativní omezení](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) tématu.
