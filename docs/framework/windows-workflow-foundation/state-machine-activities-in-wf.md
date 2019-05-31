---
title: Aktivit stavového stroje v WF
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 64af2698c878066464e2ca3f32d4522d99999aec
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378054"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="fa414-102">Aktivit stavového stroje v WF</span><span class="sxs-lookup"><span data-stu-id="fa414-102">State Machine Activities in WF</span></span>
<span data-ttu-id="fa414-103">Rozhraní .NET framework 4.5 poskytuje několik aktivit poskytované systémem a návrháři aktivit pro vytvoření pracovní postupy stavu počítače.</span><span class="sxs-lookup"><span data-stu-id="fa414-103">.NET Framework 4.5 provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="fa414-104">Provede obsažené aktivity pomocí paradigma známé stav počítače.</span><span class="sxs-lookup"><span data-stu-id="fa414-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="fa414-105">Představuje stav stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="fa414-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="fa414-106">Představuje ukončující stav stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="fa414-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="fa414-107"><xref:System.Activities.Core.Presentation.FinalState> je návrháře aktivit, že používá vytvoří <xref:System.Activities.Statements.State> předkonfigurované jako ukončující stavu.</span><span class="sxs-lookup"><span data-stu-id="fa414-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="fa414-108">Další informace najdete v tématu [Návrhář aktivity Finalstate](/visualstudio/workflow-designer/finalstate-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="fa414-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="fa414-109">Představuje přechod mezi dvěma stavy.</span><span class="sxs-lookup"><span data-stu-id="fa414-109">Represents the transition between two states.</span></span> <span data-ttu-id="fa414-110">Neexistuje žádné **nástrojů** položku <xref:System.Activities.Statements.Transition>; přechody jsou vytvořeny v Návrháři postupu provádění přetahováním řádku mezi dvěma stavy nebo přetažením stavu na trojúhelníky, které se objeví jeden stav je myš jiného .</span><span class="sxs-lookup"><span data-stu-id="fa414-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="fa414-111">Další informace najdete v tématu [Návrhář aktivity Transition](/visualstudio/workflow-designer/transition-activity-designer).</span><span class="sxs-lookup"><span data-stu-id="fa414-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa414-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa414-112">See also</span></span>

- [<span data-ttu-id="fa414-113">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="fa414-113">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
