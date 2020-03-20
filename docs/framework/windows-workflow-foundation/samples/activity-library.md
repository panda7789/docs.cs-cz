---
title: Knihovna aktivit
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: fae2a94b5e5e776625aa7f26700980640b66afd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142898"
---
# <a name="activity-library"></a>Knihovna aktivit
Tato část obsahuje ukázky, které ukazují pokročilé vlastní aktivity v základu pracovního postupu systému Windows (WF).  
  
## <a name="in-this-section"></a>V tomto oddílu

 [Vlastní aktivita SendMail](sendmail-custom-activity.md)  
 Ukazuje, jak vytvořit vlastní aktivitu, <xref:System.Activities.AsyncCodeActivity> která je odvozena od odesílání pošty pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu.  
  
 [Aktivita ThrottledParallelForEach](throttled-parallel-foreach.md)  
 Ukazuje, jak `ThrottleParallelForEach` aktivita je <xref:System.Activities.Statements.ParallelForEach%601> podobná aktivity s jedinou výjimkou, která umožňuje nastavení faktoru souběžnosti omezit počet souběžných větví spustit.
  
 [Aktivity přístupu k databázi](database-access-activities.md)  
 Ukazuje, jak vytvořit aktivity, které umožňují přístup k databázím načíst nebo upravit informace a použít [ADO.NET](../../data/adonet/index.md) pro přístup k databázi.  
  
 [Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5](externalized-policy-activity-in-net-framework-4-5.md)  
 Ukazuje, jak aktivita ExternalizedPolicy4 umožňuje spuštění existujících objektů Windows Workflow Foundation v <xref:System.Workflow.Activities.Rules.RuleSet> rozhraní .NET [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Framework 3.5 (WF 3.5) v systému Windows Workflow Foundation v (WF 4.5) přímo pomocí modulu pravidel, který je dodáván v wf 3.5.
  
 [Neobecná aktivita ForEach](non-generic-foreach.md)  
 Ukazuje, jak vytvořit neobecnou verzi <xref:System.Activities.Statements.ForEach%601> aktivity.  
  
 [Neobecná aktivita ParallelForEach](non-generic-parallelforeach.md)  
 Ukazuje, jak vytvořit neobecnou verzi <xref:System.Activities.Statements.ParallelForEach%601> aktivity.  
  
 [Získání WorkflowInstanceId](get-workflowinstanceid.md)  
 Ukazuje, jak používat vlastní `GetWorkflowInstanceId`aktivitu , chcete-li vrátit ID instance pracovního postupu.
