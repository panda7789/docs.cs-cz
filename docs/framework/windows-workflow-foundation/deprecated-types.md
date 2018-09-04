---
title: Zastaralé typy v programovacím modelu Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: b25be26d4c0ad6c423b011cd7cad24a8728333f5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43658896"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Zastaralé typy v programovacím modelu Windows Workflow Foundation
V rozhraní .NET 4 pracovního postupu týmu vydali modul pro všechny nové pracovní postup v <xref:System.Activities> oboru názvů. Ve verzi beta verze rozhraní .NET 4.5 jsme se označení většina typů v "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, a <xref:System.Workflow.Runtime> obory názvů jako zastaralé.  
  
## <a name="obsolete-namespaces-and-tools"></a>Zastaralé obory názvů a nástroje  
 Následující sestavení mají jednu nebo více veřejných typů, které se přestanou používat:  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   Wfc.exe  
  
 Zákazníci, kteří používají rozhraní API nepoužívané 3 WF v důsledku toho dojde upozornění a zobrazí se zpráva podobná této:  
  
 **Upozornění BC40000: X je zastaralý: WF 3 typy se považují za zastaralé. Místo toho použijte WF 4.** Typy jsme se odebrat z rozhraní .NET Framework v budoucí verzi, ale jsme ještě nebyla určena tohoto časového rámce (ne v 4.5). Tento krok aktuální umožňuje komunikaci naše směr pro naše zákazníky a poskytnout dostatek čas na přechod na nový model WF4. Budeme, samozřejmě, i nadále podporuje tyto typy WF 3 v části [životní cyklus podpory Microsoft](https://aka.ms/MicrosoftSupportLifecycle). Stávající WF3 aplikace se spustí bez problému na rozhraní .NET 4.5, a [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] budou podporovat nové i stávající řešení založená na WF3.  
  
 Pravidla souvisejících typů v <xref:System.Workflow.Activities.Rules> obor názvů, které nemají můžou nahradit aktuální soubor v systému Windows 4.5, nejsou zastaralé.  
  
 Zákazníci, kteří chtějí migrovat své aplikace WF 4 najdete v nápovědě [pokyny k migraci 4 pracovního postupu](migration-guidance.md).
