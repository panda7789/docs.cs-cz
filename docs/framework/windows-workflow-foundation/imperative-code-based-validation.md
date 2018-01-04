---
title: "Imperativní ověření založené na kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79e50c9cc756915ffc1a2f376d6b46469c85dbf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imperative-code-based-validation"></a><span data-ttu-id="0b718-102">Imperativní ověření založené na kódu</span><span class="sxs-lookup"><span data-stu-id="0b718-102">Imperative Code-Based Validation</span></span>
<span data-ttu-id="0b718-103">Imperativní ověřování založené na kódu poskytuje jednoduchý způsob, jak aktivity pro ověřování o samotné a je k dispozici pro aktivity, které jsou odvozeny od <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="0b718-103">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="0b718-104">Ověřovací kód, který určuje všechny chyby ověření nebo upozornění je přidána do aktivity.</span><span class="sxs-lookup"><span data-stu-id="0b718-104">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="0b718-105">Pomocí ověřování založené na kódu</span><span class="sxs-lookup"><span data-stu-id="0b718-105">Using Code-Based Validation</span></span>  
 <span data-ttu-id="0b718-106">Podporuje ověřování založené na kódu aktivity, které jsou odvozeny od <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, a <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="0b718-106">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="0b718-107">Ověření kódu mohou být umístěny v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsání a ověření chyby nebo výstrahy mohou být přidány do argument metadat.</span><span class="sxs-lookup"><span data-stu-id="0b718-107">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="0b718-108">V následujícím příkladu převzat ze [základní ověření](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) ukázkové, pokud `Cost` je větší než `Price`, Chyba ověření se přidá do metadat.</span><span class="sxs-lookup"><span data-stu-id="0b718-108">In the following example, taken from the [Basic Validation](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) sample, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b718-109">Všimněte si, že `Cost` a `Price` nejsou argumenty pro aktivity, ale jsou vlastnosti, které jsou nastaveny v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="0b718-109">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="0b718-110">To znamená proč jejich hodnoty lze ověřit v <xref:System.Activities.CodeActivity.CacheMetadata%2A> přepsat.</span><span class="sxs-lookup"><span data-stu-id="0b718-110">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="0b718-111">Hodnota dat předávaných mezi argument nelze ověřit v době návrhu, protože není až do spuštění toku dat, ale argumenty aktivity může být ověřen zajistit, že je vázána pomocí `RequiredArgument` atribut a přetížení skupiny.</span><span class="sxs-lookup"><span data-stu-id="0b718-111">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="0b718-112">Tento příklad kódu se zobrazí `RequiredArgument` atribut pro `Description` argument a pokud není vázaný a je generována chyba ověření.</span><span class="sxs-lookup"><span data-stu-id="0b718-112">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="0b718-113">Vyžaduje argumenty jsou popsané v [vyžaduje argumenty a přetížení skupiny](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="0b718-113">Required arguments are covered in [Required Arguments and Overload Groups](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).</span></span>  
  
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
  
 <span data-ttu-id="0b718-114">Ve výchozím nastavení, je chyba ověření do metadat při <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="0b718-114">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="0b718-115">K přidání upozornění ověření použijte <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> přetížení, které přijímá <xref:System.Activities.Validation.ValidationError>a určit, že <xref:System.Activities.Validation.ValidationError> představuje upozornění nastavením <xref:System.Activities.Validation.ValidationError.IsWarning%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0b718-115">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="0b718-116">Ověření nastane, když pracovní postup se mění v Návrháři pracovních postupů a všechny chyby ověření nebo upozornění se zobrazí v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="0b718-116">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="0b718-117">Ověřování také dochází za běhu, při vyvolání pracovního postupu, a pokud dojde k chybám ověření, <xref:System.Activities.InvalidWorkflowException> logiku ověření výchozí vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="0b718-117">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="0b718-118">volání ověření a přístup k žádné ověření upozornění ani chyby, najdete v části [ověření aktivity vyvolání](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="0b718-118"> invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="0b718-119">Jakékoli výjimky, které jsou vyvolány z <xref:System.Activities.CodeActivity.CacheMetadata%2A> nejsou považovány za chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="0b718-119">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="0b718-120">Tyto výjimky bude vyhnuli z volání <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> a musí být zpracována volající.</span><span class="sxs-lookup"><span data-stu-id="0b718-120">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="0b718-121">Ověřování založené na kódu je užitečné pro ověřování aktivity, která obsahuje kód, ale nemá viditelnost do další aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="0b718-121">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="0b718-122">Deklarativní omezení ověření poskytuje možnost ověření vztahy mezi aktivity a další aktivity v pracovním postupu a věnuje se [deklarativní omezení](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="0b718-122">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) topic.</span></span>
