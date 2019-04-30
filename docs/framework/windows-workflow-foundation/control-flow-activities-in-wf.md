---
title: Aktivity toku řízení do pracovního postupu
ms.date: 03/30/2017
ms.assetid: 6892885b-f7c5-4aea-8f5e-28863fb4ae75
ms.openlocfilehash: bcbb12210af2d0172977dca6f81355031baa043a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945909"
---
# <a name="control-flow-activities-in-wf"></a>Aktivity toku řízení do pracovního postupu
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Poskytuje několik aktivit pro řízení toku provádění v rámci pracovního postupu. Některé z těchto aktivit (například `Switch` a `If`) implementovat tok řídicí struktury podobné těm v programovací prostředí, jako je vizuál C#, while ostatním uživatelům (například `Pick`) nových struktur programovací model.  
  
 Všimněte si, že při aktivity, jako `Parallel` a `ParallelForEach` aktivity naplánovat současně více podřízených aktivit pro spuštění, pro pracovní postup se používá pouze jedno vlákno. Každá podřízená aktivita tyto aktivity spouští sekvenčně a následné aktivity se neprovedou až do předchozí aktivity dokončení nebo přejděte nečinnosti. V důsledku toho tyto aktivity jsou zvláště užitečná pro aplikace, ve kterých musí provést několik potenciálně blokující aktivity prokládané způsobem. Pokud žádná z podřízených aktivit tyto aktivity přejít nečinný, `Parallel` aktivity spustí podobně jako `Sequence` aktivity a `ParallelForEach` aktivity spustí podobně jako `ForEach` aktivity. Pokud však asynchronních aktivitách (například aktivit, které jsou odvozeny z <xref:System.Activities.AsyncCodeActivity>) nebo zasílání zpráv aktivity se používají, ovládací prvek předá do další větve, zatímco podřízená aktivita čeká na jeho má přijmout zprávu nebo jeho asynchronní práce k dokončení.  
  
## <a name="flow-control-activities"></a>Aktivity toku řízení  
  
|Aktivita|Popis|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.DoWhile>|Provede obsažené aktivity jednou a pokračuje k tomu, dokud je podmínka `true`.|  
|<xref:System.Activities.Statements.ForEach%601>|Vloženým příkazem spouští postupně pro každý prvek v kolekci. <xref:System.Activities.Statements.ForEach%601> je podobný klíčové slovo `foreach`, ale je implementovaná jako aktivity místo příkaz jazyka.|  
|<xref:System.Activities.Statements.If>|Provede obsažené aktivity, pokud je podmínka `true`a mohou spouštět aktivity obsažené v <xref:System.Activities.Statements.If.Else%2A> vlastnosti, pokud je podmínka `false`.|  
|<xref:System.Activities.Statements.Parallel>|Provede obsažené aktivity paralelně.|  
|<xref:System.Activities.Statements.ParallelForEach%601>|Vloženým příkazem spustí paralelně pro každý prvek v kolekci.|  
|<xref:System.Activities.Statements.Pick>|Poskytuje modelování toku řízení na základě událostí.|  
|<xref:System.Activities.Statements.PickBranch>|Představuje potenciální cesta provádění v <xref:System.Activities.Statements.Pick> aktivity.|  
|<xref:System.Activities.Statements.Sequence>|Provede obsažené aktivity postupně.|  
|<xref:System.Activities.Statements.Switch%601>|Vybere jednu možnost z mnoha aktivity, na základě hodnoty daného výrazu.|  
|<xref:System.Activities.Statements.While>|Provede obsažené aktivity, dokud je podmínka `true`.|
