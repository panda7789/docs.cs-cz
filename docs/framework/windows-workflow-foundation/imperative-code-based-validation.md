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
# <a name="imperative-code-based-validation"></a><span data-ttu-id="d0ddc-102">Ověřování na základě imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="d0ddc-102">Imperative Code-Based Validation</span></span>

<span data-ttu-id="d0ddc-103">Imperativní ověření založené na kódu poskytuje jednoduchý způsob, jak aktivita <xref:System.Activities.CodeActivity>poskytnout <xref:System.Activities.AsyncCodeActivity>ověření <xref:System.Activities.NativeActivity>o sobě a je k dispozici pro aktivity, které jsou odvozeny od , , a .</span><span class="sxs-lookup"><span data-stu-id="d0ddc-103">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="d0ddc-104">Ověřovací kód, který určuje všechny chyby ověření nebo upozornění je přidán do aktivity.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-104">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="d0ddc-105">Použití ověření na základě kódu</span><span class="sxs-lookup"><span data-stu-id="d0ddc-105">Using Code-Based Validation</span></span>

<span data-ttu-id="d0ddc-106">Ověřování na základě kódu je podporováno aktivitami, které jsou odvozeny z , <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity>a <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-106">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="d0ddc-107">Ověřovací kód lze umístit <xref:System.Activities.CodeActivity.CacheMetadata%2A> do přepsání a chyby ověření nebo upozornění mohou být přidány do argumentu metadat.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-107">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="d0ddc-108">V následujícím příkladu, `Cost` pokud je `Price`větší než , je do metadat přidána chyba ověření.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-108">In the following example, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0ddc-109">Všimněte `Cost` `Price` si, že a nejsou argumenty k aktivitě, ale jsou vlastnosti, které jsou nastaveny v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-109">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="d0ddc-110">To je důvod, proč jejich <xref:System.Activities.CodeActivity.CacheMetadata%2A> hodnoty mohou být ověřeny v přepsání.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-110">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="d0ddc-111">Hodnotu dat toku přes argument nelze ověřit v době návrhu, protože data netokuje až do běhu, ale argumenty aktivity lze ověřit, aby bylo zajištěno, že jsou vázány pomocí atributu `RequiredArgument` a skupin přetížení.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-111">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="d0ddc-112">Tento ukázkový kód `RequiredArgument` vidí `Description` atribut pro argument a pokud není vázán, je generována chyba ověření.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-112">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="d0ddc-113">Požadované argumenty jsou popsány v [požadované argumenty a skupiny přetížení](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="d0ddc-113">Required arguments are covered in [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>  
  
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
  
 <span data-ttu-id="d0ddc-114">Ve výchozím nastavení je chyba ověření přidána do metadat při <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> volání.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-114">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="d0ddc-115">Chcete-li přidat upozornění <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> ověření, použijte <xref:System.Activities.Validation.ValidationError>přetížení, které <xref:System.Activities.Validation.ValidationError> trvá , a <xref:System.Activities.Validation.ValidationError.IsWarning%2A> určete, že představuje upozornění nastavením vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-115">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="d0ddc-116">K ověření dochází při změně pracovního postupu v návrháři pracovního postupu a všechny chyby ověření nebo upozornění jsou zobrazeny v návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-116">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="d0ddc-117">K ověření dochází také v době běhu, kdy je vyvolán <xref:System.Activities.InvalidWorkflowException> pracovní postup a pokud dojde k chybám ověření, je vyvolána výchozí ověřovací logikou.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-117">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="d0ddc-118">Další informace o vyvolání ověření a přístupu k všem ověřovacím upozorněním nebo chybám naleznete [v tématu Vyvolání ověření aktivity](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="d0ddc-118">For more information about invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="d0ddc-119">Všechny výjimky, které <xref:System.Activities.CodeActivity.CacheMetadata%2A> jsou vyvolány z nejsou považovány za chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-119">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="d0ddc-120">Tyto výjimky budou uniknout <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> z volání a musí být zpracovány volajícím.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-120">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="d0ddc-121">Ověření založené na kódu je užitečné pro ověření aktivity, která obsahuje kód, ale nemá přehled o ostatních aktivitách v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="d0ddc-121">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="d0ddc-122">Deklarativní omezení ověření poskytuje možnost ověřit vztahy mezi aktivitou a další mise v pracovním postupu a je zahrnuta v tématu [deklarativní omezení.](declarative-constraints.md)</span><span class="sxs-lookup"><span data-stu-id="d0ddc-122">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](declarative-constraints.md) topic.</span></span>
