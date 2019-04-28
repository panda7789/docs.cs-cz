---
title: 'Postupy: Zobrazení chyb ověřování v návrháři se změněným hostováním'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: a3d993f55bf130039905f1a6512a7ae104512432
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761476"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Postupy: Zobrazení chyb ověřování v návrháři se změněným hostováním
Toto téma popisuje, jak načíst a publikovat chyby ověření provádění se změněným hostováním [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]. To nám poskytuje s postupem, abyste se ujistili, že pracovního postupu v návrháři se změněným hostováním platný.  
  
 Tento úkol má dvě části. První je k dispozici implementace <xref:System.Activities.Presentation.Validation.IValidationErrorService>.  Existuje jedna kritické metody k implementaci tohoto rozhraní <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> který bude předávat seznam <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objekty, které obsahují informace o chybách v protokolu ladění.  Po implementaci rozhraní načíst informace o této chybě a publikujte instance tuto implementaci kontextu úprav.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>Implementovat rozhraní IValidationErrorService  
  
1. Tady je ukázka kódu pro jednoduché implementace, která bude zapisovat chyby ověření protokolu pro ladění.  
  
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
  
### <a name="publishing-to-the-editing-context"></a>Publikování do kontextu úprav  
  
1. Tady je kód, který se bude publikovat ji do kontextu úprav.  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
