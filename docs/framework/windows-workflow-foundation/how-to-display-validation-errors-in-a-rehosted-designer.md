---
title: 'Postupy: zobrazení chyb ověřování v přehostujícím návrháři'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: bd0c2c10665de4bc3364938167101655a9bdd056
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716281"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="049c8-102">Postupy: zobrazení chyb ověřování v přehostujícím návrháři</span><span class="sxs-lookup"><span data-stu-id="049c8-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="049c8-103">Toto téma popisuje, jak načíst a publikovat chyby ověřování v Návrhář postupu provádění v přehostovaných oknech.</span><span class="sxs-lookup"><span data-stu-id="049c8-103">This topic describes how to retrieve and publish validation errors in a rehosted Windows Workflow Designer.</span></span> <span data-ttu-id="049c8-104">Díky tomu je k dispozici postup, který potvrdí, že pracovní postup v přehostujícím návrháři je platný.</span><span class="sxs-lookup"><span data-stu-id="049c8-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="049c8-105">Tato úloha má dvě části.</span><span class="sxs-lookup"><span data-stu-id="049c8-105">This task has two parts.</span></span> <span data-ttu-id="049c8-106">První je poskytnout <xref:System.Activities.Presentation.Validation.IValidationErrorService>implementace.</span><span class="sxs-lookup"><span data-stu-id="049c8-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="049c8-107">Existuje jedna kritická metoda pro implementaci na tomto rozhraní <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>, která předává seznam objektů <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> obsahujících informace o chybách do protokolu ladění.</span><span class="sxs-lookup"><span data-stu-id="049c8-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="049c8-108">Po implementaci rozhraní načtěte informace o chybě publikováním instance této implementace do kontextu úprav.</span><span class="sxs-lookup"><span data-stu-id="049c8-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="049c8-109">Implementace rozhraní IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="049c8-109">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="049c8-110">Zde je ukázka kódu pro jednoduchou implementaci, která bude zapisovat chyby ověřování do protokolu ladění.</span><span class="sxs-lookup"><span data-stu-id="049c8-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
    ```csharp  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine($"Error: {vei.Message}"));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="049c8-111">Publikování do kontextu úprav</span><span class="sxs-lookup"><span data-stu-id="049c8-111">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="049c8-112">Zde je kód, který bude publikovat do kontextu úprav.</span><span class="sxs-lookup"><span data-stu-id="049c8-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
