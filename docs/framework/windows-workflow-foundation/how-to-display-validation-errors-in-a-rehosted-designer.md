---
title: 'Postupy: zobrazení chyb ověřování v přehostujícím návrháři'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: d36883eb77864ccc16cb5882d0de216e1aaaa589
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420600"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Postupy: zobrazení chyb ověřování v přehostujícím návrháři
Toto téma popisuje, jak načíst a publikovat chyby ověřování v [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]hostitele. Díky tomu je k dispozici postup, který potvrdí, že pracovní postup v přehostujícím návrháři je platný.  
  
 Tato úloha má dvě části. První je poskytnout <xref:System.Activities.Presentation.Validation.IValidationErrorService>implementace.  Existuje jedna kritická metoda pro implementaci na tomto rozhraní <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>, která předává seznam objektů <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> obsahujících informace o chybách do protokolu ladění.  Po implementaci rozhraní načtěte informace o chybě publikováním instance této implementace do kontextu úprav.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>Implementace rozhraní IValidationErrorService  
  
1. Zde je ukázka kódu pro jednoduchou implementaci, která bude zapisovat chyby ověřování do protokolu ladění.  
  
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
  
### <a name="publishing-to-the-editing-context"></a>Publikování do kontextu úprav  
  
1. Zde je kód, který bude publikovat do kontextu úprav.  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
