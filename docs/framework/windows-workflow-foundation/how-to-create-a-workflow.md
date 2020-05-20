---
title: 'Postupy: Vytvoření pracovního postupu'
description: Provedením jedné ze tří možností v této části vytvoříte pracovní postup v rámci tohoto kurzu pro účely postupu.
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: 7e4575436405e74b7575e55bea37a1a99d879a3e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419561"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="b5d32-103">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b5d32-103">How to: Create a Workflow</span></span>
<span data-ttu-id="b5d32-104">Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="b5d32-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="b5d32-105">Témata v této části popisují postup vytvoření pracovního postupu, který používá předdefinované aktivity, jako je <xref:System.Activities.Statements.Flowchart> aktivita, a vlastní aktivity z předchozího tématu [Postupy: vytvoření aktivity](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="b5d32-105">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="b5d32-106">Pracovní postup modeluje číslo odhadující hru.</span><span class="sxs-lookup"><span data-stu-id="b5d32-106">The workflow models a number guessing game.</span></span> <span data-ttu-id="b5d32-107">K dokončení kurzu je nutné pouze jedno z témat v této části. měli byste vybrat styl, který vás zajímá, a postupovat podle tohoto kroku.</span><span class="sxs-lookup"><span data-stu-id="b5d32-107">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="b5d32-108">V případě potřeby však můžete všechna témata dokončit.</span><span class="sxs-lookup"><span data-stu-id="b5d32-108">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5d32-109">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="b5d32-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="b5d32-110">Chcete-li dokončit toto téma, je nutné nejprve dokončit [Postupy: vytvoření aktivity](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="b5d32-110">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5d32-111">Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="b5d32-111">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5d32-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b5d32-112">In This Section</span></span>  
 [<span data-ttu-id="b5d32-113">Postupy: Vytvoření sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b5d32-113">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="b5d32-114">V této části najdete popis postupu vytvoření sekvenčního pracovního postupu pomocí <xref:System.Activities.Statements.Sequence> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b5d32-114">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="b5d32-115">Postupy: Vytvoření pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="b5d32-115">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="b5d32-116">Popisuje, jak vytvořit pracovní postup vývojového diagramu pomocí <xref:System.Activities.Statements.Flowchart> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b5d32-116">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="b5d32-117">Postupy: Vytvoření pracovního postupu stavového stroje</span><span class="sxs-lookup"><span data-stu-id="b5d32-117">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="b5d32-118">Popisuje, jak vytvořit pracovní postup stavového stroje pomocí <xref:System.Activities.Statements.StateMachine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b5d32-118">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d32-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5d32-119">See also</span></span>

- [<span data-ttu-id="b5d32-120">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="b5d32-120">Windows Workflow Foundation Programming</span></span>](programming.md)
