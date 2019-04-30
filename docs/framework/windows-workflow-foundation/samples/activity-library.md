---
title: Knihovna aktivit
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: b701d382c25644181b23f3c0f0cd8e019b8d37d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909178"
---
# <a name="activity-library"></a>Knihovna aktivit
Tato část obsahuje ukázky, které předvádějí pokročilých vlastních aktivit Windows Workflow Foundation (WF).  
  
## <a name="in-this-section"></a>V tomto oddílu

 [Vlastní aktivita SendMail](sendmail-custom-activity.md)  
 Ukazuje, jak vytvořit vlastní aktivitu, která je odvozena z <xref:System.Activities.AsyncCodeActivity> k odesílání e-mailu pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu.  
  
 [Aktivita ThrottledParallelForEach](throttled-parallel-foreach.md)  
 Ukazuje, jak `ThrottleParallelForEach` aktivity se podobá <xref:System.Activities.Statements.ParallelForEach%601> činnost s jednou výjimkou, že umožňuje nastavení faktor souběžnost chcete omezit počet souběžných větve ke spuštění.
  
 [Aktivity přístupu k databázi](database-access-activities.md)  
 Ukazuje, jak vytvořit aktivity, které umožňují přístup k databázím nebo upravte informace a použití [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) pro přístup k databázi.  
  
 [Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5](externalized-policy-activity-in-net-framework-4-5.md)  
 Ukazuje, jak aktivity ExternalizedPolicy4 umožňuje provádění stávající Windows Workflow Foundation v [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objekty v modelu Windows Workflow Foundation v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) přímo pomocí pravidla modul, který je poskytuje WF 3.5. 
  
 [Neobecná aktivita ForEach](non-generic-foreach.md)  
 Ukazuje, jak vytvořit obecné verzi <xref:System.Activities.Statements.ForEach%601> aktivity.  
  
 [Neobecná aktivita ParallelForEach](non-generic-parallelforeach.md)  
 Ukazuje, jak vytvořit obecné verzi <xref:System.Activities.Statements.ParallelForEach%601> aktivity.  
  
 [Získání WorkflowInstanceId](get-workflowinstanceid.md)  
 Ukazuje, jak použít vlastní aktivitu, `GetWorkflowInstanceId`, který vrátí ID instance pracovního postupu
