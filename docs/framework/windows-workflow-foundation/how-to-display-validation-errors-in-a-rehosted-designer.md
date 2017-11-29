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
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Postupy: zobrazení chyb ověřování na opětovné hostování nástroje návrháře
Toto téma popisuje, jak načíst a publikování chyby ověření v opětovné hostování nástroje [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]. To poskytuje nám postupu potvrďte, že pracovní postup opětovné hostování nástroje Designer je platný.  
  
 Tento úkol má dvě části. Prvním je poskytnout implementaci <xref:System.Activities.Presentation.Validation.IValidationErrorService>.  Neexistuje jeden kritické metody k implementaci na tomto rozhraní <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> kterého bude předat seznam <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objekty, které obsahují informace o chybách protokolu pro ladění.  Po implementaci rozhraní, můžete načíst informace o chybě tak, že publikování instance této implementace úpravy v kontextu.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>Implementace rozhraní IValidationErrorService  
  
1.  Zde je ukázka kódu pro jednoduché implementace, která bude zapisovat se chyby ověření protokolu pro ladění.  
  
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
  
### <a name="publishing-to-the-editing-context"></a>Publikování do úpravy kontextu  
  
1.  Zde je kód, který bude publikovat toto úpravy v kontextu.  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
