---
title: "Zastaralé typy v modelu Windows Workflow Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5254beb4c338d14d11922312c74dfe1962d88921
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Zastaralé typy v modelu Windows Workflow Foundation
V rozhraní .NET 4 týmem pracovního postupu vydané modul všechny nové pracovní postup v <xref:System.Activities> oboru názvů. Ve verzi beta verzi rozhraní .NET 4.5 jsme jsou označení většinu typů v "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, a <xref:System.Workflow.Runtime> obory názvů jako zastaralé.  
  
## <a name="obsolete-namespaces-and-tools"></a>Zastaralé obory názvů a nástroje  
 Následující sestavení mít jeden nebo více veřejné typy, které přestanou:  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   Wfc.exe  
  
 Zákazníci, kteří používají rozhraní API pro zastaralé 3 WF v důsledku toho se setkají sestavení upozornění s zpráva podobná následující:  
  
 **Upozornění BC40000: X je zastaralý: WF 3 typy jsou zastaralé. Místo toho použijte WF 4.** Typy jsme se odebrat z rozhraní .NET Framework v budoucí verzi, ale zjistili jsme nebyly dosud tohoto časového období (ne ve 4.5). Tento krok aktuální umožňuje komunikaci naše směr zákazníkům a povolit dostatek času pro přesun do nového modelu WF4. Budeme, samozřejmě nadále podporu těchto typů WF 3 v části [o zásadách životního cyklu podpory společnosti Microsoft](http://aka.ms/MicrosoftSupportLifecycle). Existující WF3 aplikací spustit bez problém v rozhraní .NET 4.5 a [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] budou podporovat nové a stávající na základě WF3 řešení.  
  
 Pravidla související typy v <xref:System.Workflow.Activities.Rules> obor názvů, které nemají náhradní v WF 4.5, nebyly zastaralá.  
  
 Zákazníci, kteří chtějí migrovat své aplikace na WF 4 najdete v nápovědě [pracovního postupu 4 migrace pokyny](migration-guidance.md).
