---
title: "Aktivity toku řízení ve WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5312012a74f5e11b02c0191dc00fa23fb25a73a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="control-flow-activities-in-wf"></a>Aktivity toku řízení ve WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Poskytuje několik aktivit pro řízení toku provádění v rámci pracovního postupu. Některé z těchto aktivit (například `Switch` a `If`) implementovat toku řízení struktury podobná těm v programovacím prostředí, jako [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], při ostatní (, jako `Pick`) nové struktury programovací model.  
  
 Všimněte si, že při aktivity, jako `Parallel` a `ParallelForEach` aktivity naplánovat více podřízených aktivit pro provedení současně, pouze jedno vlákno se používá pro pracovní postup. Každá aktivita podřízené tyto aktivity spouští sekvenčně a následných aktivity se neprovedou, dokud nebude předchozí aktivity dokončit nebo přejděte nečinnosti. Tyto aktivity jsou v důsledku toho je nejvhodnější pro aplikace, ve kterých několik potenciálně blokování aktivity musí být spuštěn v prokládaná způsobem. Pokud žádná z podřízené aktivity tyto aktivity přejděte nečinnosti, `Parallel` aktivita provede podobně jako `Sequence` aktivitu a `ParallelForEach` aktivita provede podobně jako `ForEach` aktivity. V případě, ale asynchronní aktivit (například aktivit, které jsou odvozeny od <xref:System.Activities.AsyncCodeActivity>) nebo zasílání zpráv aktivity se používají, řízení předá další větev při podřízené aktivity čeká na jeho zprávy lze přijímat nebo jeho asynchronní pracovní dokončit.  
  
## <a name="flow-control-activities"></a>Aktivity toku řízení  
  
|Aktivita|Popis|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|Provede obsažené aktivity jednou a pokračuje k tomu, když podmínku `true`.|  
|<xref:System.Activities.Statements.ForEach%601>|Spustí příkaz vložené v pořadí pro každý prvek v kolekci. <xref:System.Activities.Statements.ForEach%601>je podobná klíčové slovo `foreach`, ale je implementovaná jako aktivity, nikoli příkaz jazyka.|  
|<xref:System.Activities.Statements.If>|Provede obsažené aktivity, pokud je podmínka `true`a můžete provést aktivity obsažené v <xref:System.Activities.Statements.If.Else%2A> vlastnost, pokud je podmínka vyhodnocena `false`.|  
|<xref:System.Activities.Statements.Parallel>|Provede obsažené aktivity paralelně.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Zpracuje vložený příkaz paralelně pro každý prvek v kolekci.|  
|<xref:System.Activities.Statements.Pick>|Poskytuje modelování toku řízení na základě událostí.|  
|<xref:System.Activities.Statements.PickBranch>|Představuje potenciální cesty spouštění v <xref:System.Activities.Statements.Pick> aktivity.|  
|<xref:System.Activities.Statements.Sequence>|Provádí aktivity obsažené v pořadí.|  
|<xref:System.Activities.Statements.Switch%601>|Vybere jeden výběr z mnoha různých aktivity, na základě daného výrazu hodnoty.|  
|<xref:System.Activities.Statements.While>|Provede obsažené aktivity při podmínku `true`.|
