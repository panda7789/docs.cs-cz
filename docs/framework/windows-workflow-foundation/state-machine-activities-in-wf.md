---
title: Aktivity stavu počítače v WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 78727bab0102909e9f1e479210cf4b42801aa3ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515766"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="22d2f-102">Aktivity stavu počítače v WF</span><span class="sxs-lookup"><span data-stu-id="22d2f-102">State Machine Activities in WF</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="22d2f-103"> poskytuje několik poskytované systémem aktivity a návrháře aktivit pro vytváření pracovních postupů stav počítače.</span><span class="sxs-lookup"><span data-stu-id="22d2f-103"> provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="22d2f-104">Provede obsažené aktivity pomocí zlepší známé stav počítače.</span><span class="sxs-lookup"><span data-stu-id="22d2f-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="22d2f-105">Představuje stav ve stavu počítače.</span><span class="sxs-lookup"><span data-stu-id="22d2f-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="22d2f-106">Představuje ukončující stavu stav počítače.</span><span class="sxs-lookup"><span data-stu-id="22d2f-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="22d2f-107"><xref:System.Activities.Core.Presentation.FinalState> je Návrhář aktivity který po používá vytvoří <xref:System.Activities.Statements.State> předkonfigurované jako ukončující stav.</span><span class="sxs-lookup"><span data-stu-id="22d2f-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="22d2f-108">Další informace najdete v tématu [Návrhář aktivity FinalState](/visualstudio/workflow-designer/finalstate-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="22d2f-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="22d2f-109">Představuje přechod mezi dvěma stavy.</span><span class="sxs-lookup"><span data-stu-id="22d2f-109">Represents the transition between two states.</span></span> <span data-ttu-id="22d2f-110">Neexistuje žádné **sada nástrojů** položky pro <xref:System.Activities.Statements.Transition>; přechody jsou vytvořené v Návrháři pracovních postupů pomocí přetahování řádek mezi dvěma stavy nebo umístěním stav na trojúhelníčky, které se objeví jeden stav je při přechodu myší na jiné .</span><span class="sxs-lookup"><span data-stu-id="22d2f-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="22d2f-111">Další informace najdete v tématu [Návrhář aktivity přechod](/visualstudio/workflow-designer/transition-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="22d2f-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22d2f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="22d2f-112">See Also</span></span>  
 [<span data-ttu-id="22d2f-113">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="22d2f-113">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
