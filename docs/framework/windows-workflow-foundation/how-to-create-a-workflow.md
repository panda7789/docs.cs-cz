---
title: "Postupy: vytvoření pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
caps.latest.revision: "34"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f16df123837b2233efd156bf35975e3adbe7279
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="3da4f-102">Postupy: vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3da4f-102">How to: Create a Workflow</span></span>
<span data-ttu-id="3da4f-103">Pracovní postupy lze sestavit z předdefinovaných aktivit a také z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="3da4f-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="3da4f-104">Tato témata v této části kroku procesem vytvoření pracovního postupu, který používá obě zabudované aktivity, jako <xref:System.Activities.Statements.Flowchart> aktivity a vlastní aktivity z předchozí [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="3da4f-104">This topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="3da4f-105">Pracovní postup modelů číslo hádání hru.</span><span class="sxs-lookup"><span data-stu-id="3da4f-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="3da4f-106">Pouze jeden témat v této části je vyžadováno k dokončení tohoto kurzu; měli byste vybrat styl, které vás zajímají a postupujte podle tohoto kroku.</span><span class="sxs-lookup"><span data-stu-id="3da4f-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="3da4f-107">Je však může provést všechna témata v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="3da4f-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3da4f-108">Každého tématu v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="3da4f-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="3da4f-109">K dokončení tohoto tématu, musíte nejdřív Dokončit [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="3da4f-109">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3da4f-110">Si můžete stáhnout dokončenou verzi kurzu [modelu Windows Workflow Foundation (WF45) - kurzu Začínáme](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="3da4f-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3da4f-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3da4f-111">In This Section</span></span>  
 [<span data-ttu-id="3da4f-112">Postupy: Vytvoření sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3da4f-112">How to: Create a Sequential Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="3da4f-113">Popisuje postup vytvoření sekvenční pracovní postup pomocí <xref:System.Activities.Statements.Sequence> aktivity.</span><span class="sxs-lookup"><span data-stu-id="3da4f-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="3da4f-114">Postupy: vytvoření vývojový diagram pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3da4f-114">How to: Create a Flowchart Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="3da4f-115">Popisuje, jak vytvořit vývojový diagram pracovního postupu pomocí <xref:System.Activities.Statements.Flowchart> aktivity.</span><span class="sxs-lookup"><span data-stu-id="3da4f-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="3da4f-116">Postupy: vytvoření pracovního postupu stavu počítače</span><span class="sxs-lookup"><span data-stu-id="3da4f-116">How to: Create a State Machine Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="3da4f-117">Popisuje postup vytvoření stavu počítače pracovního postupu pomocí <xref:System.Activities.Statements.StateMachine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="3da4f-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da4f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3da4f-118">See Also</span></span>  
 [<span data-ttu-id="3da4f-119">Windows Workflow Foundation programování</span><span class="sxs-lookup"><span data-stu-id="3da4f-119">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
