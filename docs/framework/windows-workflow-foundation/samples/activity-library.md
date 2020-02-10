---
title: Knihovna aktivit
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: ce65bf8e7adad6acefd7aac6d69c3f836b94be29
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094693"
---
# <a name="activity-library"></a>Knihovna aktivit
V této části najdete ukázky, které ukazují rozšířené vlastní aktivity v programovací model Windows Workflow Foundation (WF).  
  
## <a name="in-this-section"></a>V tomto oddílu

 [Vlastní aktivita SendMail](sendmail-custom-activity.md)  
 Ukazuje, jak vytvořit vlastní aktivitu, která je odvozena z <xref:System.Activities.AsyncCodeActivity> k odeslání e-mailu pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu.  
  
 [Aktivita ThrottledParallelForEach](throttled-parallel-foreach.md)  
 Ukazuje, jak je aktivita `ThrottleParallelForEach` podobná aktivitě <xref:System.Activities.Statements.ParallelForEach%601> s jedinou výjimkou, kterou umožňuje nastavit faktor souběžnosti k omezení počtu souběžných větví, které mají být spuštěny.
  
 [Aktivity přístupu k databázi](database-access-activities.md)  
 Ukazuje, jak vytvořit aktivity, které umožňují přístup k databázím načíst nebo upravit informace a používat [ADO.NET](../../data/adonet/index.md) pro přístup k databázi.  
  
 [Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5](externalized-policy-activity-in-net-framework-4-5.md)  
 Ukazuje, jak aktivita ExternalizedPolicy4 umožňuje spouštět existující programovací model Windows Workflow Foundation v .NET Framework 3,5 (WF 3,5) <xref:System.Workflow.Activities.Rules.RuleSet> objektů v programovací model Windows Workflow Foundation v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4,5) přímo pomocí modulu pravidel, který je dodán v WF 3,5. 
  
 [Neobecná aktivita ForEach](non-generic-foreach.md)  
 Ukazuje, jak vytvořit neobecnou verzi aktivity <xref:System.Activities.Statements.ForEach%601>.  
  
 [Neobecná aktivita ParallelForEach](non-generic-parallelforeach.md)  
 Ukazuje, jak vytvořit neobecnou verzi aktivity <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 [Získání WorkflowInstanceId](get-workflowinstanceid.md)  
 Ukazuje, jak použít vlastní aktivitu `GetWorkflowInstanceId`k vrácení ID instance pracovního postupu.
