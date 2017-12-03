---
title: "Aktivity stavu počítače v WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed2b5ace499af3c050529e9f0f2cdd3634c247fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="state-machine-activities-in-wf"></a>Aktivity stavu počítače v WF
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]poskytuje několik poskytované systémem aktivity a návrháře aktivit pro vytváření pracovních postupů stav počítače.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Provede obsažené aktivity pomocí zlepší známé stav počítače.|  
|<xref:System.Activities.Statements.State>|Představuje stav ve stavu počítače.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Představuje ukončující stavu stav počítače. <xref:System.Activities.Core.Presentation.FinalState>je Návrhář aktivity který po používá vytvoří <xref:System.Activities.Statements.State> předkonfigurované jako ukončující stav. Další informace najdete v tématu [Návrhář aktivity FinalState](/visualstudio/workflow-designer/finalstate-activity-designer).|  
|<xref:System.Activities.Statements.Transition>|Představuje přechod mezi dvěma stavy. Neexistuje žádné **sada nástrojů** položky pro <xref:System.Activities.Statements.Transition>; přechody jsou vytvořené v Návrháři pracovních postupů pomocí přetahování řádek mezi dvěma stavy nebo umístěním stav na trojúhelníčky, které se objeví jeden stav je při přechodu myší na jiné . Další informace najdete v tématu [Návrhář aktivity přechod](/visualstudio/workflow-designer/transition-activity-designer).|  
  
## <a name="see-also"></a>Viz také  
 [Kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
