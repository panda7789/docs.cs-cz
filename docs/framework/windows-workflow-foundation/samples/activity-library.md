---
title: Knihovna aktivit
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99d8fba848129156d94e54d1da7d08122ccfa735
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="activity-library"></a>Knihovna aktivit
Tato část obsahuje příklady vysvětlující pokročilé vlastních aktivit v [!INCLUDE[wf](../../../../includes/wf-md.md)].  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Aktivita Policy v rozhraní .NET Framework 4.5](../../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md)  
 Ukazuje, jak aktivity Policy4 umožňuje [!INCLUDE[wf2](../../../../includes/wf2-md.md)] v [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objekty, které chcete použít v [!INCLUDE[wf2](../../../../includes/wf2-md.md)]v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) přímo pomocí pravidla modulem, který se dodává v WF 3.5.  
  
 [Vlastní aktivita pro přepnutí u rozsahu hodnot](../../../../docs/framework/windows-workflow-foundation/samples/custom-activity-to-switch-on-a-range-of-values.md)  
 Ukazuje, jak vytvořit vlastní aktivitu, která rozšiřuje použití <xref:System.Activities.Statements.Switch%601>.  
  
 [Aktivita LINQ to Objects](../../../../docs/framework/windows-workflow-foundation/samples/linq-to-objects-activity.md)  
 Demonstruje postup vytvoření aktivitu pomocí LINQ na objekty dotazu elementů v kolekci.  
  
 [Ukázka LINQ to SQL](../../../../docs/framework/windows-workflow-foundation/samples/linq-to-sql-sample.md)  
 Demonstruje postup vytvoření aktivity použití LINQ na entity dotazu SQL z tabulek v databáze systému SQL Server.  
  
 [Použití aktivity InvokePowerShell](../../../../docs/framework/windows-workflow-foundation/samples/using-the-invokepowershell-activity.md)  
 Ukazuje, jak volat pomocí aktivity InvokePowerShell příkazy prostředí Windows PowerShell.  
  
 [Aktivita RangeEnumeration](../../../../docs/framework/windows-workflow-foundation/samples/rangeenumeration-activity.md)  
 Ukazuje, jak vytvořit vlastní aktivitu, který iteruje nad kolekcí čísel.  
  
 [Aktivity s regulárními výrazy](../../../../docs/framework/windows-workflow-foundation/samples/regular-expression-activities.md)  
 Ukazuje, jak vytvořit sadu aktivit, které poskytují funkce regulární výraz <xref:System.Text.RegularExpressions> oboru názvů.  
  
 [Vlastní aktivita SendMail](../../../../docs/framework/windows-workflow-foundation/samples/sendmail-custom-activity.md)  
 Ukazuje, jak vytvořit vlastní aktivitu, která je odvozena od <xref:System.Activities.AsyncCodeActivity> k odesílání pošty přes protokol SMTP pro použití v rámci aplikace pracovního postupu.  
  
 [Aktivita For](../../../../docs/framework/windows-workflow-foundation/samples/for-activity.md)  
 Ukazuje, jak vytvářet vlastní aktivity, která dědí z <xref:System.Activities.NativeActivity> a použít ho k iteraci v rozsahu hodnot v pracovním postupu.  
  
 [Aktivita WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/wait-for-input-activity.md)  
 Ukazuje, jak vytvořit pojmenovaný záložky v pracovním postupu.  
  
 [Aktivita ThrottledParallelForEach](../../../../docs/framework/windows-workflow-foundation/samples/throttled-parallel-foreach.md)  
 Ukazuje, jak `ThrottleParallelForEach` aktivity je podobná <xref:System.Activities.Statements.ParallelForEach%601> aktivity s jednou výjimkou to umožňuje nastavení souběžnosti Multi-Factor omezit počet souběžných větví provést.  
  
 [Aktivity entit](../../../../docs/framework/windows-workflow-foundation/samples/entity-activities.md)  
 Ukazuje, jak používat ADO.NET Entity Framework s [!INCLUDE[wf2](../../../../includes/wf2-md.md)] zjednodušit přístup k datům.  
  
 [Aktivity přístupu k databázi](../../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md)  
 Demonstruje postup vytvoření aktivity, které umožňují přístup k databázím načtení nebo upravte informace a použití [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) pro přístup k databázi.  
  
 [Aktivita CommentOut](../../../../docs/framework/windows-workflow-foundation/samples/commentout-activity.md)  
 Ukazuje, jak psát vlastní aktivity, která odebere z cesty k provádění, efektivně komentářů je ostatní aktivity.  
  
 [Externalizovaná aktivita Policy v rozhraní .NET Framework 4.5](../../../../docs/framework/windows-workflow-foundation/samples/externalized-policy-activity-in-net-framework-4-5.md)  
 Ukazuje, jak aktivity ExternalizedPolicy4 umožňuje provádění stávající [!INCLUDE[wf2](../../../../includes/wf2-md.md)] v [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objekty v [!INCLUDE[wf2](../../../../includes/wf2-md.md)] v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) přímo pomocí pravidla modulem, který se dodává v WF 3.5.  
  
 [Aktivita NoPersistScope](../../../../docs/framework/windows-workflow-foundation/samples/nopersistscope-activity.md)  
 Ukazuje, jak pracovat s neserializovatelných a na jedno použití stavu v pracovním postupu.  
  
 [Neobecná aktivita ForEach](../../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md)  
 Ukazuje, jak vytvořit neobecnou verzi <xref:System.Activities.Statements.ForEach%601> aktivity.  
  
 [Neobecná aktivita ParallelForEach](../../../../docs/framework/windows-workflow-foundation/samples/non-generic-parallelforeach.md)  
 Ukazuje, jak vytvořit neobecnou verzi <xref:System.Activities.Statements.ParallelForEach%601> aktivity.  
  
 [Získání WorkflowInstanceId](../../../../docs/framework/windows-workflow-foundation/samples/get-workflowinstanceid.md)  
 Ukazuje, jak používat vlastní aktivitu, `GetWorkflowInstanceId`, vrátit ID instance pracovního postupu
