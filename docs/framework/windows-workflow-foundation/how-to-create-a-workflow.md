---
title: 'Postupy: Vytvoření pracovního postupu'
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: 7f0bef673ff14ded13306a1fc26e09695601799d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962301"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="b2b95-102">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b2b95-102">How to: Create a Workflow</span></span>
<span data-ttu-id="b2b95-103">Pracovní postupy mohou být vytvořeny z vestavěných aktivit i z vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="b2b95-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="b2b95-104">Témata v této části popisují postup vytvoření pracovního postupu, který používá předdefinované aktivity, jako je <xref:System.Activities.Statements.Flowchart> aktivita, a vlastní aktivity z předchozího [postupu: Vytvoření tématu aktivity](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="b2b95-104">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="b2b95-105">Pracovní postup modeluje číslo odhadující hru.</span><span class="sxs-lookup"><span data-stu-id="b2b95-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="b2b95-106">K dokončení kurzu je nutné pouze jedno z témat v této části. měli byste vybrat styl, který vás zajímá, a postupovat podle tohoto kroku.</span><span class="sxs-lookup"><span data-stu-id="b2b95-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="b2b95-107">V případě potřeby však můžete všechna témata dokončit.</span><span class="sxs-lookup"><span data-stu-id="b2b95-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2b95-108">Každé téma v kurzu Začínáme závisí na předchozích tématech.</span><span class="sxs-lookup"><span data-stu-id="b2b95-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="b2b95-109">Chcete-li dokončit toto téma, je nutné [nejprve provést následující kroky: Vytvoří aktivitu](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="b2b95-109">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2b95-110">Pokud si chcete stáhnout dokončenou verzi kurzu, přečtěte si [kurz programovací model Windows Workflow Foundation (WF45) – začínáme](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="b2b95-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2b95-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b2b95-111">In This Section</span></span>  
 [<span data-ttu-id="b2b95-112">Postupy: Vytvoření sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b2b95-112">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="b2b95-113">V této části <xref:System.Activities.Statements.Sequence> najdete popis postupu vytvoření sekvenčního pracovního postupu pomocí aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2b95-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="b2b95-114">Postupy: Vytvoření pracovního postupu vývojového diagramu</span><span class="sxs-lookup"><span data-stu-id="b2b95-114">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="b2b95-115">Popisuje, jak vytvořit pracovní postup vývojového diagramu <xref:System.Activities.Statements.Flowchart> pomocí aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2b95-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="b2b95-116">Postupy: Vytvoření pracovního postupu stavového stroje</span><span class="sxs-lookup"><span data-stu-id="b2b95-116">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="b2b95-117">Popisuje, jak vytvořit pracovní postup stavového stroje pomocí <xref:System.Activities.Statements.StateMachine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b2b95-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b95-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2b95-118">See also</span></span>

- [<span data-ttu-id="b2b95-119">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="b2b95-119">Windows Workflow Foundation Programming</span></span>](programming.md)
