---
title: 'Postupy: Vytvoření pracovního postupu'
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: 4b24e57cce4d42645fc1750ac932e5f24cf24913
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773338"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="9e723-102">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9e723-102">How to: Create a Workflow</span></span>
<span data-ttu-id="9e723-103">Pracovní postupy lze zkonstruovat z předdefinovaných aktivit a také z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="9e723-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="9e723-104">Témata v této části kroku vytvořením pracovního postupu, který používá obě integrované aktivity, jako <xref:System.Activities.Statements.Flowchart> aktivity a vlastní aktivity z předchozího [jak: Vytvořit aktivitu](how-to-create-an-activity.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="9e723-104">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="9e723-105">Pracovní postup modely číslo rozluštění hru.</span><span class="sxs-lookup"><span data-stu-id="9e723-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="9e723-106">Pouze jeden z témata v této části se vyžaduje k dokončení tohoto kurzu; měli byste vybrat styl, který vás zajímá a postupujte podle tohoto kroku.</span><span class="sxs-lookup"><span data-stu-id="9e723-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="9e723-107">V případě potřeby je ale může všechna témata dokončit.</span><span class="sxs-lookup"><span data-stu-id="9e723-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e723-108">Každé téma v kurzu Začínáme závisí na předchozí témata.</span><span class="sxs-lookup"><span data-stu-id="9e723-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="9e723-109">K dokončení tohoto tématu, musíte nejdřív Dokončit [jak: Vytvořit aktivitu](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="9e723-109">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e723-110">Chcete-li stáhnout úplnou verzi tohoto kurzu, přečtěte si téma [Windows Workflow Foundation (WF45) – kurz Začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="9e723-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e723-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9e723-111">In This Section</span></span>  
 [<span data-ttu-id="9e723-112">Postupy: Vytvoření sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="9e723-112">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="9e723-113">Popisuje postup vytvoření sekvenčního pracovního postupu pomocí <xref:System.Activities.Statements.Sequence> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e723-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="9e723-114">Postupy: Vytvoření pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="9e723-114">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="9e723-115">Popisuje, jak vytvořit vývojový diagram pracovního postupu pomocí <xref:System.Activities.Statements.Flowchart> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e723-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="9e723-116">Postupy: Vytvoření pracovního postupu stavového stroje</span><span class="sxs-lookup"><span data-stu-id="9e723-116">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="9e723-117">Popisuje, jak vytvořit pomocí pracovního postupu stav počítače <xref:System.Activities.Statements.StateMachine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e723-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e723-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e723-118">See also</span></span>

- [<span data-ttu-id="9e723-119">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="9e723-119">Windows Workflow Foundation Programming</span></span>](programming.md)
