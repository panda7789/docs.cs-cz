---
title: Ověřování na základě imperativního kódu
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: f3b07d0ab06b3753286c929b90e713a6941684ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143093"
---
# <a name="imperative-code-based-validation"></a>Ověřování na základě imperativního kódu

Imperativní ověření založené na kódu poskytuje jednoduchý způsob, jak aktivita <xref:System.Activities.CodeActivity>poskytnout <xref:System.Activities.AsyncCodeActivity>ověření <xref:System.Activities.NativeActivity>o sobě a je k dispozici pro aktivity, které jsou odvozeny od , , a . Ověřovací kód, který určuje všechny chyby ověření nebo upozornění je přidán do aktivity.  
  
## <a name="using-code-based-validation"></a>Použití ověření na základě kódu

Ověřování na základě kódu je podporováno aktivitami, které jsou odvozeny z , <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity>a <xref:System.Activities.NativeActivity>. Ověřovací kód lze umístit <xref:System.Activities.CodeActivity.CacheMetadata%2A> do přepsání a chyby ověření nebo upozornění mohou být přidány do argumentu metadat. V následujícím příkladu, `Cost` pokud je `Price`větší než , je do metadat přidána chyba ověření.  
  
> [!NOTE]
> Všimněte `Cost` `Price` si, že a nejsou argumenty k aktivitě, ale jsou vlastnosti, které jsou nastaveny v době návrhu. To je důvod, proč jejich <xref:System.Activities.CodeActivity.CacheMetadata%2A> hodnoty mohou být ověřeny v přepsání. Hodnotu dat toku přes argument nelze ověřit v době návrhu, protože data netokuje až do běhu, ale argumenty aktivity lze ověřit, aby bylo zajištěno, že jsou vázány pomocí atributu `RequiredArgument` a skupin přetížení. Tento ukázkový kód `RequiredArgument` vidí `Description` atribut pro argument a pokud není vázán, je generována chyba ověření. Požadované argumenty jsou popsány v [požadované argumenty a skupiny přetížení](required-arguments-and-overload-groups.md).  
  
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
  
 Ve výchozím nastavení je chyba ověření přidána do metadat při <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> volání. Chcete-li přidat upozornění <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> ověření, použijte <xref:System.Activities.Validation.ValidationError>přetížení, které <xref:System.Activities.Validation.ValidationError> trvá , a <xref:System.Activities.Validation.ValidationError.IsWarning%2A> určete, že představuje upozornění nastavením vlastnosti.  
  
 K ověření dochází při změně pracovního postupu v návrháři pracovního postupu a všechny chyby ověření nebo upozornění jsou zobrazeny v návrháři pracovního postupu. K ověření dochází také v době běhu, kdy je vyvolán <xref:System.Activities.InvalidWorkflowException> pracovní postup a pokud dojde k chybám ověření, je vyvolána výchozí ověřovací logikou. Další informace o vyvolání ověření a přístupu k všem ověřovacím upozorněním nebo chybám naleznete [v tématu Vyvolání ověření aktivity](invoking-activity-validation.md).  
  
 Všechny výjimky, které <xref:System.Activities.CodeActivity.CacheMetadata%2A> jsou vyvolány z nejsou považovány za chyby ověření. Tyto výjimky budou uniknout <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> z volání a musí být zpracovány volajícím.  
  
 Ověření založené na kódu je užitečné pro ověření aktivity, která obsahuje kód, ale nemá přehled o ostatních aktivitách v pracovním postupu. Deklarativní omezení ověření poskytuje možnost ověřit vztahy mezi aktivitou a další mise v pracovním postupu a je zahrnuta v tématu [deklarativní omezení.](declarative-constraints.md)
