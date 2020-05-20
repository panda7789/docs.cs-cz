---
title: Začínáme Tutorial2
description: Tento článek zahájí sekvenci kurzů, které vás zavedou k programování programovací model Windows Workflow Foundation aplikací.
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: 148ba77231067bf5f8ff1d8b444b83d951ce8761
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419847"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="57247-103">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="57247-103">Getting Started Tutorial</span></span>
<span data-ttu-id="57247-104">Tato část obsahuje sadu návodových témat, která vás seznámí s programováním aplikací programovací model Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="57247-104">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="57247-105">Pomocí postupů v těchto tématech sestavíte aplikaci, která představuje číslo pro vystavování her.</span><span class="sxs-lookup"><span data-stu-id="57247-105">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="57247-106">První téma v kurzu vás provede kroky k vytvoření vlastních aktivit požadovaných pro pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="57247-106">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="57247-107">V druhém tématu jsou tyto aktivity sestaveny spolu s integrovanými aktivitami pracovního postupu do pracovního postupu vývojového diagramu.</span><span class="sxs-lookup"><span data-stu-id="57247-107">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="57247-108">V třetím tématu je hostitelská aplikace nakonfigurovaná tak, aby spouštěla pracovní postup, a v konečném případě je zavedena konečná trvalá témata.</span><span class="sxs-lookup"><span data-stu-id="57247-108">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="57247-109">Každý krok tohoto procesu závisí na předchozích krocích, takže doporučujeme, abyste je dokončili v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="57247-109">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57247-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="57247-110">In This Section</span></span>  
 [<span data-ttu-id="57247-111">Postupy: Vytvoření aktivity</span><span class="sxs-lookup"><span data-stu-id="57247-111">How to: Create an Activity</span></span>](how-to-create-an-activity.md)  
 <span data-ttu-id="57247-112">Popisuje, jak vytvořit vlastní aktivitu, která je odvozena z <xref:System.Activities.NativeActivity%601> a jak tuto aktivitu vytvořit spolu s integrovanou aktivitou do složené aktivity pomocí návrháře aktivit.</span><span class="sxs-lookup"><span data-stu-id="57247-112">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="57247-113">Postupy: Vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="57247-113">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)  
 <span data-ttu-id="57247-114">V této části najdete popis postupu vytvoření pracovních postupů v rámci diagramu, sekvenčního a stavového počítače pomocí integrovaných aktivit a vlastních aktivit z předchozího kurzu.</span><span class="sxs-lookup"><span data-stu-id="57247-114">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="57247-115">Postupy: Spuštění pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="57247-115">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)  
 <span data-ttu-id="57247-116">Popisuje, jak vyvolat pracovní postup z hostitelského prostředí, předávat data do pracovního postupu a přejít do něj a jak obnovit záložky.</span><span class="sxs-lookup"><span data-stu-id="57247-116">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="57247-117">Postupy: Vytvoření a spuštění dlouhodobého pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="57247-117">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="57247-118">Popisuje, jak přidat trvalost do aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="57247-118">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="57247-119">Postupy: Vytvoření vlastního účastníka sledování</span><span class="sxs-lookup"><span data-stu-id="57247-119">How to: Create a Custom Tracking Participant</span></span>](how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="57247-120">Popisuje, jak vytvořit vlastního účastníka sledování a profil sledování.</span><span class="sxs-lookup"><span data-stu-id="57247-120">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="57247-121">Postupy: Hostování několika verzí pracovního postupu současně</span><span class="sxs-lookup"><span data-stu-id="57247-121">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="57247-122">Popisuje, jak použít `WorkflowIdentity` k hostování více verzí pracovního postupu vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="57247-122">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="57247-123">Postupy: Aktualizace definice běžící instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="57247-123">How to: Update the Definition of a Running Workflow Instance</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="57247-124">Popisuje, jak použít dynamickou aktualizaci k úpravě spuštěných instancí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="57247-124">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57247-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="57247-125">See also</span></span>

- [<span data-ttu-id="57247-126">Programování Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="57247-126">Windows Workflow Foundation Programming</span></span>](programming.md)
