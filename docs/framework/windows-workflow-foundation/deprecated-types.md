---
title: Zastaralé typy ve Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: d41bf147cd079a3d6d3714da5595732de3dcb7de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774046"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Zastaralé typy ve Windows Workflow Foundation
V rozhraní .NET 4 pracovního postupu týmu vydali modul pro všechny nové pracovní postup v <xref:System.Activities> oboru názvů. Ve verzi beta verze rozhraní .NET 4.5 jsme se označení většina typů v "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, a <xref:System.Workflow.Runtime> obory názvů jako zastaralé.  
  
## <a name="obsolete-namespaces-and-tools"></a>Zastaralé obory názvů a nástroje  
 Následující sestavení mají jednu nebo více veřejných typů, které se přestanou používat:  
  
- System.Workflow.Activities.dll  
  
- System.Workflow.ComponentModel.dll  
  
- System.Workflow.Runtime.dll  
  
- System.WorkflowServices.dll  
  
- Microsoft.Workflow.DebugController.dll  
  
- Microsoft.Workflow.Compiler.exe  
  
- Wfc.exe  
  
 Zákazníci, kteří používají rozhraní API nepoužívané 3 WF v důsledku toho dojde upozornění a zobrazí se zpráva podobná této:  
  
 **Upozornění BC40000: X je zastaralý: WF 3 typy se považují za zastaralé. Místo toho použijte WF 4.** Typy jsme se odebrat z rozhraní .NET Framework v budoucí verzi, ale jsme ještě nebyla určena tohoto časového rámce (ne v 4.5). Tento krok aktuální umožňuje komunikaci naše směr pro naše zákazníky a poskytnout dostatek čas na přechod na nový model WF4. Budeme, samozřejmě, i nadále podporuje tyto typy WF 3 v části [životní cyklus podpory Microsoft](https://aka.ms/MicrosoftSupportLifecycle). Stávající aplikace WF3 poběží bez problému v rozhraní .NET 4.5 a Visual Studio 2012 budou podporovat nové i stávající řešení založená na WF3.  
  
 Pravidla souvisejících typů v <xref:System.Workflow.Activities.Rules> obor názvů, které nemají můžou nahradit aktuální soubor v systému Windows 4.5, nejsou zastaralé.  
  
 Zákazníci, kteří chtějí migrovat své aplikace WF 4 najdete v nápovědě [pokyny k migraci 4 pracovního postupu](migration-guidance.md).
