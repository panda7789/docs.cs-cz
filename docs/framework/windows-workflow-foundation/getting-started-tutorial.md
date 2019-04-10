---
title: Začínáme se službou Tutorial2
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: 540765c09dceef583798ceaf1abf9f191f444697
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217429"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="ce06c-102">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="ce06c-102">Getting Started Tutorial</span></span>
<span data-ttu-id="ce06c-103">Tato část obsahuje sadu témat, které vám představí programování aplikací pro Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="ce06c-103">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="ce06c-104">Pomocí následujících postupů v těchto tématech, vytvoříte aplikaci, která je číslo rozluštění hra.</span><span class="sxs-lookup"><span data-stu-id="ce06c-104">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="ce06c-105">První téma v tomto kurzu vás provede kroky k vytvoření vlastních aktivit nutný pro pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="ce06c-105">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="ce06c-106">V druhém tématu tyto aktivity jsou součástí spolu s integrované pracovního postupu aktivit pracovního postupu vývojového diagramu.</span><span class="sxs-lookup"><span data-stu-id="ce06c-106">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="ce06c-107">V třetí tématu hostitelská aplikace je nakonfigurovaná pro spuštění pracovního postupu a v posledním tématu je zavedená trvalosti.</span><span class="sxs-lookup"><span data-stu-id="ce06c-107">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="ce06c-108">Každý krok v tomto procesu závisí na předchozí kroky, proto doporučujeme je provést v pořadí.</span><span class="sxs-lookup"><span data-stu-id="ce06c-108">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce06c-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ce06c-109">In This Section</span></span>  
 [<span data-ttu-id="ce06c-110">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="ce06c-110">How to: Create an Activity</span></span>](how-to-create-an-activity.md)  
 <span data-ttu-id="ce06c-111">Popisuje, jak vytvořit vlastní aktivitu, která je odvozena z <xref:System.Activities.NativeActivity%601>a jak sestavit tuto aktivitu spolu s předdefinovanou aktivitu do složených aktivit pomocí návrháře aktivit.</span><span class="sxs-lookup"><span data-stu-id="ce06c-111">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="ce06c-112">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="ce06c-112">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)  
 <span data-ttu-id="ce06c-113">Popisuje, jak vytvořit vývojový diagram sekvenční a pracovní postupy stavu počítače pomocí předdefinované i vlastní aktivity v předchozím kurzu.</span><span class="sxs-lookup"><span data-stu-id="ce06c-113">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="ce06c-114">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="ce06c-114">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)  
 <span data-ttu-id="ce06c-115">Popisuje vyvolat pracovní postup z hostitelské prostředí, předat data do a z pracovního postupu a obnovit záložky.</span><span class="sxs-lookup"><span data-stu-id="ce06c-115">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="ce06c-116">Postupy: Vytvoření a spuštění dlouhotrvajícího pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="ce06c-116">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="ce06c-117">Popisuje, jak přidat trvalost aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ce06c-117">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="ce06c-118">Postupy: Vytvoření vlastního účastníka sledování</span><span class="sxs-lookup"><span data-stu-id="ce06c-118">How to: Create a Custom Tracking Participant</span></span>](how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="ce06c-119">Popisuje postup vytvoření vlastního účastníka sledování a profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="ce06c-119">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="ce06c-120">Postupy: Hostování několika verzí pracovního postupu současně</span><span class="sxs-lookup"><span data-stu-id="ce06c-120">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="ce06c-121">Popisuje způsob použití `WorkflowIdentity` k hostování více verzí pracovní postup-souběžně.</span><span class="sxs-lookup"><span data-stu-id="ce06c-121">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="ce06c-122">Postupy: Aktualizace definice běžící instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="ce06c-122">How to: Update the Definition of a Running Workflow Instance</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="ce06c-123">Popisuje, jak změnit běžící instance pracovního postupu pomocí dynamické aktualizace.</span><span class="sxs-lookup"><span data-stu-id="ce06c-123">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce06c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce06c-124">See also</span></span>

- [<span data-ttu-id="ce06c-125">Programování ve Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="ce06c-125">Windows Workflow Foundation Programming</span></span>](programming.md)
