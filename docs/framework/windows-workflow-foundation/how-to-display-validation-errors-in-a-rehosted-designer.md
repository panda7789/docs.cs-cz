---
title: 'Postupy: Zobrazení chyb ověřování v návrháři se změněným hostováním'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: 608868882f4bec23c03f0ec78f65673e76056030
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989654"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Postupy: Zobrazení chyb ověřování v návrháři se změněným hostováním
Toto téma popisuje, jak načíst a publikovat chyby ověřování na hostiteli [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]. Díky tomu je k dispozici postup, který potvrdí, že pracovní postup v přehostujícím návrháři je platný.  
  
 Tato úloha má dvě části. První je poskytnout implementaci <xref:System.Activities.Presentation.Validation.IValidationErrorService>.  K implementaci na tomto rozhraní existuje jedna kritická metoda, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> která vás předává <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> seznam objektů obsahujících informace o chybách do protokolu ladění.  Po implementaci rozhraní načtěte informace o chybě publikováním instance této implementace do kontextu úprav.  
  
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
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a>Publikování do kontextu úprav  
  
1. Zde je kód, který bude publikovat do kontextu úprav.  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
