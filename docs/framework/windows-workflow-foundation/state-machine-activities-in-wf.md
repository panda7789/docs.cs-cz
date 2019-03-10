---
title: Aktivit stavového stroje v WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: eee507f873cde3aabce09c9b3fdb1620cd79fdab
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710313"
---
# <a name="state-machine-activities-in-wf"></a>Aktivit stavového stroje v WF
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] poskytuje několik aktivit poskytované systémem a návrháři aktivit pro vytvoření pracovní postupy stavu počítače.  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|Provede obsažené aktivity pomocí paradigma známé stav počítače.|  
|<xref:System.Activities.Statements.State>|Představuje stav stavového stroje.|  
|<xref:System.Activities.Core.Presentation.FinalState>|Představuje ukončující stav stavového stroje. <xref:System.Activities.Core.Presentation.FinalState> je návrháře aktivit, že používá vytvoří <xref:System.Activities.Statements.State> předkonfigurované jako ukončující stavu. Další informace najdete v tématu [Návrhář aktivity Finalstate](/visualstudio/workflow-designer/finalstate-activity-designer).|  
|<xref:System.Activities.Statements.Transition>|Představuje přechod mezi dvěma stavy. Neexistuje žádné **nástrojů** položku <xref:System.Activities.Statements.Transition>; přechody jsou vytvořeny v Návrháři postupu provádění přetahováním řádku mezi dvěma stavy nebo přetažením stavu na trojúhelníky, které se objeví jeden stav je myš jiného . Další informace najdete v tématu [Návrhář aktivity Transition](/visualstudio/workflow-designer/transition-activity-designer).|  
  
## <a name="see-also"></a>Viz také:
- [Kurz Začínáme](getting-started-tutorial.md)
