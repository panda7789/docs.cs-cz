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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9f76f1ad5282ecf10a3ce58db0f6e1bd8df1b4d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="8f43a-102">Postupy: zobrazení chyb ověřování na opětovné hostování nástroje návrháře</span><span class="sxs-lookup"><span data-stu-id="8f43a-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="8f43a-103">Toto téma popisuje, jak načíst a publikování chyby ověření v opětovné hostování nástroje [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f43a-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="8f43a-104">To poskytuje nám postupu potvrďte, že pracovní postup opětovné hostování nástroje Designer je platný.</span><span class="sxs-lookup"><span data-stu-id="8f43a-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="8f43a-105">Tento úkol má dvě části.</span><span class="sxs-lookup"><span data-stu-id="8f43a-105">This task has two parts.</span></span> <span data-ttu-id="8f43a-106">Prvním je poskytnout implementaci <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="8f43a-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="8f43a-107">Neexistuje jeden kritické metody k implementaci na tomto rozhraní <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> kterého bude předat seznam <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objekty, které obsahují informace o chybách protokolu pro ladění.</span><span class="sxs-lookup"><span data-stu-id="8f43a-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="8f43a-108">Po implementaci rozhraní, můžete načíst informace o chybě tak, že publikování instance této implementace úpravy v kontextu.</span><span class="sxs-lookup"><span data-stu-id="8f43a-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="8f43a-109">Implementace rozhraní IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="8f43a-109">Implement the IValidationErrorService Interface</span></span>  
  
1.  <span data-ttu-id="8f43a-110">Zde je ukázka kódu pro jednoduché implementace, která bude zapisovat se chyby ověření protokolu pro ladění.</span><span class="sxs-lookup"><span data-stu-id="8f43a-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
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
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="8f43a-111">Publikování do úpravy kontextu</span><span class="sxs-lookup"><span data-stu-id="8f43a-111">Publishing to the Editing Context</span></span>  
  
1.  <span data-ttu-id="8f43a-112">Zde je kód, který bude publikovat toto úpravy v kontextu.</span><span class="sxs-lookup"><span data-stu-id="8f43a-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
