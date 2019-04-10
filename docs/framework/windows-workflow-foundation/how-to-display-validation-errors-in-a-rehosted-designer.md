---
title: 'Postupy: Zobrazení chyb ověřování v návrháři se změněným hostováním'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: a3d993f55bf130039905f1a6512a7ae104512432
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310197"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="610dc-102">Postupy: Zobrazení chyb ověřování v návrháři se změněným hostováním</span><span class="sxs-lookup"><span data-stu-id="610dc-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="610dc-103">Toto téma popisuje, jak načíst a publikovat chyby ověření provádění se změněným hostováním [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="610dc-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="610dc-104">To nám poskytuje s postupem, abyste se ujistili, že pracovního postupu v návrháři se změněným hostováním platný.</span><span class="sxs-lookup"><span data-stu-id="610dc-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="610dc-105">Tento úkol má dvě části.</span><span class="sxs-lookup"><span data-stu-id="610dc-105">This task has two parts.</span></span> <span data-ttu-id="610dc-106">První je k dispozici implementace <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="610dc-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="610dc-107">Existuje jedna kritické metody k implementaci tohoto rozhraní <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> který bude předávat seznam <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objekty, které obsahují informace o chybách v protokolu ladění.</span><span class="sxs-lookup"><span data-stu-id="610dc-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="610dc-108">Po implementaci rozhraní načíst informace o této chybě a publikujte instance tuto implementaci kontextu úprav.</span><span class="sxs-lookup"><span data-stu-id="610dc-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="610dc-109">Implementovat rozhraní IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="610dc-109">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="610dc-110">Tady je ukázka kódu pro jednoduché implementace, která bude zapisovat chyby ověření protokolu pro ladění.</span><span class="sxs-lookup"><span data-stu-id="610dc-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
    ```  
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
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="610dc-111">Publikování do kontextu úprav</span><span class="sxs-lookup"><span data-stu-id="610dc-111">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="610dc-112">Tady je kód, který se bude publikovat ji do kontextu úprav.</span><span class="sxs-lookup"><span data-stu-id="610dc-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
