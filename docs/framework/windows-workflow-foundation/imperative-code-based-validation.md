---
title: Imperativní ověřování na základě kódu
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 333e1e200825dd1fc8ed750abbecbb309da66663
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707830"
---
# <a name="imperative-code-based-validation"></a><span data-ttu-id="ab724-102">Imperativní ověřování na základě kódu</span><span class="sxs-lookup"><span data-stu-id="ab724-102">Imperative Code-Based Validation</span></span>

<span data-ttu-id="ab724-103">Imperativní ověřování na základě kódu poskytuje jednoduchý způsob pro aktivitu pro ověřování o sobě a je k dispozici pro aktivity, které jsou odvozeny z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="ab724-103">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="ab724-104">Ověřovací kód, který určuje všechny chyby nebo varování ověření je přidána do aktivity.</span><span class="sxs-lookup"><span data-stu-id="ab724-104">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="ab724-105">Použití ověřování na základě kódu</span><span class="sxs-lookup"><span data-stu-id="ab724-105">Using Code-Based Validation</span></span>

<span data-ttu-id="ab724-106">Podporuje ověřování na základě kódu aktivity, které jsou odvozeny z <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="ab724-106">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="ab724-107">Kód pro ověření je možné použít v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat a chyby nebo varování ověření lze přidat na argument metadat.</span><span class="sxs-lookup"><span data-stu-id="ab724-107">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="ab724-108">V následujícím příkladu Pokud `Cost` je větší než `Price`, chyby ověřování se přidá do metadat.</span><span class="sxs-lookup"><span data-stu-id="ab724-108">In the following example, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab724-109">Všimněte si, že `Cost` a `Price` nejsou argumenty na aktivitu, ale jsou vlastnosti, které jsou nastaveny v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="ab724-109">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="ab724-110">To znamená proč jejich hodnoty můžete ověřit v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat.</span><span class="sxs-lookup"><span data-stu-id="ab724-110">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="ab724-111">Hodnota dat předávaných argument nejde ověřit v době návrhu, protože není až do spuštění toku dat, ale může být ověřen argumenty aktivity k zajištění, že jsou vázány s použitím `RequiredArgument` atribut a skupiny přetížení.</span><span class="sxs-lookup"><span data-stu-id="ab724-111">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="ab724-112">Tento příklad kódu se zobrazí `RequiredArgument` atribut pro `Description` argument a pokud příčka není svázána, je vygenerována chyba ověření.</span><span class="sxs-lookup"><span data-stu-id="ab724-112">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="ab724-113">Povinné argumenty jsou popsané v [povinné argumenty a skupiny přetížení](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="ab724-113">Required arguments are covered in [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>  
  
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
  
 <span data-ttu-id="ab724-114">Ve výchozím nastavení, se přidá chyby ověření v metadatech při <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="ab724-114">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="ab724-115">Chcete-li přidat upozornění ověření, použijte <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> přetížení, které přijímá <xref:System.Activities.Validation.ValidationError>a určit, že <xref:System.Activities.Validation.ValidationError> představuje upozornění tak, že nastavíte <xref:System.Activities.Validation.ValidationError.IsWarning%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ab724-115">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="ab724-116">Ověření vyvolá se při změně pracovního postupu v Návrháři pracovních postupů a všechny chyby nebo varování ověření se zobrazí v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="ab724-116">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="ab724-117">Ověření se také dojde za běhu, když uživatel vyvolá pracovní postup, a pokud dojde k chybám ověření, <xref:System.Activities.InvalidWorkflowException> logiku ověřování výchozí vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="ab724-117">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="ab724-118">Další informace o volání ověřování a přístup k žádným ověření upozornění ani chyby, najdete v části [vyvolání ověřování aktivit](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="ab724-118">For more information about invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="ab724-119">Všechny výjimky, které jsou vyvolány z <xref:System.Activities.CodeActivity.CacheMetadata%2A> nemají být považována za chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="ab724-119">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="ab724-120">Tyto výjimky budou návrat z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a volající musí být zpracován.</span><span class="sxs-lookup"><span data-stu-id="ab724-120">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="ab724-121">Ověřování na základě kódu je užitečné pro ověřování aktivity, která obsahuje kód, ale nemá vhled do další aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="ab724-121">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="ab724-122">Deklarativní omezení ověření umožňuje ověřovat vztahy mezi aktivity a další aktivity v pracovním postupu a věnuje se [deklarativní omezení](declarative-constraints.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="ab724-122">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](declarative-constraints.md) topic.</span></span>
