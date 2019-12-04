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
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Postupy: zobrazení chyb ověřování v přehostujícím návrháři
Toto téma popisuje, jak načíst a publikovat chyby ověřování v Návrhář postupu provádění v přehostovaných oknech. Díky tomu je k dispozici postup, který potvrdí, že pracovní postup v přehostujícím návrháři je platný.  
  
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
