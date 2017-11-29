---
title: "Postupy: zobrazení chyb ověřování na opětovné hostování nástroje návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bbf6bcf6550c17a514edb28eecbe8d5d74ba7af2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="b7a3a-102">Postupy: zobrazení chyb ověřování na opětovné hostování nástroje návrháře</span><span class="sxs-lookup"><span data-stu-id="b7a3a-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="b7a3a-103">Toto téma popisuje, jak načíst a publikování chyby ověření v opětovné hostování nástroje [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7a3a-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="b7a3a-104">To poskytuje nám postupu potvrďte, že pracovní postup opětovné hostování nástroje Designer je platný.</span><span class="sxs-lookup"><span data-stu-id="b7a3a-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="b7a3a-105">Tento úkol má dvě části.</span><span class="sxs-lookup"><span data-stu-id="b7a3a-105">This task has two parts.</span></span> <span data-ttu-id="b7a3a-106">Prvním je poskytnout implementaci <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="b7a3a-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="b7a3a-107">Neexistuje jeden kritické metody k implementaci na tomto rozhraní <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> kterého bude předat seznam <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objekty, které obsahují informace o chybách protokolu pro ladění.</span><span class="sxs-lookup"><span data-stu-id="b7a3a-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="b7a3a-108">Po implementaci rozhraní, můžete načíst informace o chybě tak, že publikování instance této implementace úpravy v kontextu.</span><span class="sxs-lookup"><span data-stu-id="b7a3a-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="b7a3a-109">Implementace rozhraní IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="b7a3a-109">Implement the IValidationErrorService Interface</span></span>  
  
1.  <span data-ttu-id="b7a3a-110">Zde je ukázka kódu pro jednoduché implementace, která bude zapisovat se chyby ověření protokolu pro ladění.</span><span class="sxs-lookup"><span data-stu-id="b7a3a-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
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
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="b7a3a-111">Publikování do úpravy kontextu</span><span class="sxs-lookup"><span data-stu-id="b7a3a-111">Publishing to the Editing Context</span></span>  
  
1.  <span data-ttu-id="b7a3a-112">Zde je kód, který bude publikovat toto úpravy v kontextu.</span><span class="sxs-lookup"><span data-stu-id="b7a3a-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
