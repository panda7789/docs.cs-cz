---
title: Aktivity toku řízení v WF
description: Tento článek shrnuje .NET Framework 4.6.1 aktivity pro řízení toku provádění v rámci pracovního postupu.
ms.date: 03/30/2017
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
ms.openlocfilehash: 18ff982d3f215e3fd46108eb2411f3d1a5ab9745
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420068"
---
# <a name="control-flow-activities-in-wf"></a>Aktivity toku řízení v WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]Poskytuje několik aktivit pro řízení toku provádění v rámci pracovního postupu. Některé z těchto aktivit (například `Switch` a `If` ) implementují struktury řízení toku podobné těm v programovacích prostředích, jako je například Visual C#, zatímco jiné (například `Pick` ) modelu nové programové struktury.  
  
 Všimněte si, že i když aktivity `Parallel` jako `ParallelForEach` aktivity a naplánují více podřízených aktivit současně, pro pracovní postup se používá pouze jedno vlákno. Každá podřízená aktivita těchto aktivit se provádí postupně a následné aktivity se nespustí, dokud nebudou předchozí aktivity dokončeny nebo nečinné. V důsledku toho jsou tyto aktivity nejužitečnější pro aplikace, ve kterých se několik potenciálně blokovaných aktivit musí provádět prokládaným způsobem. Pokud žádná z podřízených aktivit těchto aktivit nepřejde do nečinnosti, `Parallel` aktivita se spustí stejně jako `Sequence` aktivita a `ParallelForEach` aktivita se spustí stejně jako `ForEach` aktivita. Pokud se však používají asynchronní aktivity (například aktivity odvozené z <xref:System.Activities.AsyncCodeActivity> ) nebo aktivity zasílání zpráv, řízení se předá do další větve, zatímco podřízená aktivita čeká na přijetí zprávy nebo na její asynchronní zpracování.  
  
## <a name="flow-control-activities"></a>Aktivity řízení toku  
  
|Aktivita|Popis|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|Spustí obsažené aktivity jednou a pokračuje v tom, i když je podmínka `true` .|  
|<xref:System.Activities.Statements.ForEach%601>|Spustí vložený příkaz v sekvenci pro každý prvek v kolekci. <xref:System.Activities.Statements.ForEach%601>je podobná klíčovému slovu `foreach` , ale je implementována jako aktivita, nikoli jako příkaz jazyka.|  
|<xref:System.Activities.Statements.If>|Provede obsažené aktivity, pokud je podmínka `true` , a může spustit aktivity obsažené ve <xref:System.Activities.Statements.If.Else%2A> vlastnosti, pokud je podmínka `false` .|  
|<xref:System.Activities.Statements.Parallel>|Provede obsažené aktivity paralelně.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Spustí vložený příkaz paralelně pro každý prvek v kolekci.|  
|<xref:System.Activities.Statements.Pick>|Poskytuje modelování toku řízení založené na událostech.|  
|<xref:System.Activities.Statements.PickBranch>|Představuje potenciální cestu spuštění v <xref:System.Activities.Statements.Pick> aktivitě.|  
|<xref:System.Activities.Statements.Sequence>|Provede obsažené aktivity v sekvenci.|  
|<xref:System.Activities.Statements.Switch%601>|Vybere jednu volbu z několika aktivit, které se mají provést, na základě hodnoty daného výrazu.|  
|<xref:System.Activities.Statements.While>|Provede obsažené aktivity, pokud je podmínka `true` .|
