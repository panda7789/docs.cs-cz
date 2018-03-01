---
title: "Trvalost pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e65f07fc01d0d364d7271c4f1378b968b687881
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-persistence"></a><span data-ttu-id="1e203-102">Trvalost pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1e203-102">Workflow Persistence</span></span>
<span data-ttu-id="1e203-103">Trvalost pracovního postupu je trvanlivý zaznamenávání stavu instance pracovního postupu, nezávisle na informace o procesu nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="1e203-103">Workflow persistence is the durable capture of a workflow instance's state, independent of process or computer information.</span></span> <span data-ttu-id="1e203-104">To se provádí nabízí dobře známé bod obnovení pro instanci pracovního postupu v případě selhání systému, nebo zachovat paměti uvolnění instancí pracovního postupu, které nejsou aktivně věnovat práci nebo přesunout stav instance pracovního postupu z jednoho uzlu do jiného uzel ve farmě serverů.</span><span class="sxs-lookup"><span data-stu-id="1e203-104">This is done to provide a well-known point of recovery for the workflow instance in the event of system failure, or to preserve memory by unloading workflow instances that are not actively doing work, or to move the state of the workflow instance from one node to another node in a server farm.</span></span>  
  
 <span data-ttu-id="1e203-105">Trvalost umožňuje proces flexibility, škálovatelnost, obnovení při krátkodobém selhání a možnosti správy paměti efektivněji.</span><span class="sxs-lookup"><span data-stu-id="1e203-105">Persistence enables process agility, scalability, recovery in the face of failure, and the ability to manage memory more efficiently.</span></span> <span data-ttu-id="1e203-106">Proces trvalost zahrnuje identifikace bod trvalost, shromažďování dat pro ukládaný a nakonec delegování skutečné úložiště dat k poskytovateli trvalost.</span><span class="sxs-lookup"><span data-stu-id="1e203-106">The persistence process includes the identification of a persistence point, the gathering of the data to be saved, and finally the delegation of the actual storage of the data to a persistence provider.</span></span>  
  
 <span data-ttu-id="1e203-107">Chcete-li zapnout stálost pro pracovní postup, je potřeba přidružit ukládání instance s **WorkflowApplication** nebo **hostitele služby pracovního postupu** jak je uvedeno v [postup: Povolit trvalost pro Pracovní postupy a pracovní postup služby](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="1e203-107">To enable persistence for a workflow, you need to associate an instance store with the **WorkflowApplication** or **WorkflowServiceHost** as mentioned in [How to: Enable Persistence for Workflows and Workflow Services](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="1e203-108">**WorkflowApplication** a **hostitele služby pracovního postupu** použití instance úložiště s nimi spojených povolit zachování instancí pracovního postupu do úložiště trvalosti a načítání instance pracovního postupu do paměť podle data instance pracovního postupu, který je uložen v úložišti trvalost.</span><span class="sxs-lookup"><span data-stu-id="1e203-108">The **WorkflowApplication** and **WorkflowServiceHost** use the instance store associated with them to enable persisting workflow instances into a persistence store and loading workflow instances into memory based on the workflow instance data stored in the persistence store.</span></span>  
  
 <span data-ttu-id="1e203-109">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Se dodává s verzí **SqlWorkflowInstanceStore** třídy, která umožňuje trvalosti dat a metadata o instance pracovního postupu do databáze systému SQL Server 2005 nebo SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="1e203-109">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ships with the **SqlWorkflowInstanceStore** class, which allows persistence of data and metadata about workflow instances into a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="1e203-110">V tématu [úložiště Instance pracovního postupu SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="1e203-110">See [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) for more details.</span></span>  
  
 <span data-ttu-id="1e203-111">K ukládání a načíst vaše data specifické pro aplikaci společně s informace týkající se instance pracovního postupu, můžete vytvořit trvalost účastníci, které rozšiřují <xref:System.Activities.Persistence.PersistenceParticipant> třídy.</span><span class="sxs-lookup"><span data-stu-id="1e203-111">To store and load your application-specific data along with the workflow instance-related information, you can create persistence participants that extend the <xref:System.Activities.Persistence.PersistenceParticipant> class.</span></span> <span data-ttu-id="1e203-112">Trvalost účastník účastní procesu trvalost vlastní serializovatelný data uložit do úložiště trvalosti, načítání dat z úložiště instance do paměti a provádět žádné další logiku v rámci transakce trvalost.</span><span class="sxs-lookup"><span data-stu-id="1e203-112">A persistence participant participates in the persistence process to save custom serializable data into the persistence store, to load the data from the instance store into memory, and to perform any additional logic under a persistence transaction.</span></span> <span data-ttu-id="1e203-113">Další informace najdete v tématu [trvalost účastníky](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).</span><span class="sxs-lookup"><span data-stu-id="1e203-113">For more information, see [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).</span></span>  
  
 <span data-ttu-id="1e203-114">Windows Server App Fabric zjednodušuje proces konfigurace trvalosti.</span><span class="sxs-lookup"><span data-stu-id="1e203-114">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="1e203-115">[Trvalost koncepty pomocí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201200)</span><span class="sxs-lookup"><span data-stu-id="1e203-115"> [Persistence Concepts with Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201200)</span></span>  
  
## <a name="implicit-persistence-points"></a><span data-ttu-id="1e203-116">Implicitní trvalost body</span><span class="sxs-lookup"><span data-stu-id="1e203-116">Implicit Persistence Points</span></span>  
 <span data-ttu-id="1e203-117">Následující seznam obsahuje příklady podmínek, na kterých je trvalá pracovního postupu, pokud je instance úložiště spojeno s pracovním postupem.</span><span class="sxs-lookup"><span data-stu-id="1e203-117">The following list contains examples of the conditions upon which a workflow is persisted when an instance store is associated with a workflow.</span></span>  
  
-   <span data-ttu-id="1e203-118">Když **TransactionScope** dokončení aktivity nebo **TransactedReceiveScope** dokončení aktivity.</span><span class="sxs-lookup"><span data-stu-id="1e203-118">When a **TransactionScope** activity completes or a **TransactedReceiveScope** activity completes.</span></span>  
  
-   <span data-ttu-id="1e203-119">Když se změní na nečinnosti instanci pracovního postupu a **WorkflowIdleBehavior** je nastavený na hostitele pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1e203-119">When a workflow instance becomes idle and the **WorkflowIdleBehavior** is set on workflow host.</span></span> <span data-ttu-id="1e203-120">K tomu dojde, například při zasílání zpráv aktivity nebo **zpoždění** aktivity.</span><span class="sxs-lookup"><span data-stu-id="1e203-120">This occurs, for example, when you use messaging activities or a **Delay** activity.</span></span>  
  
-   <span data-ttu-id="1e203-121">Když se změní na nečinnosti WorkflowApplication a **PersistableIdle** aplikace je nastavena na **PersistableIdleAction.Persist**.</span><span class="sxs-lookup"><span data-stu-id="1e203-121">When a WorkflowApplication becomes idle and the **PersistableIdle** property of the application is set to **PersistableIdleAction.Persist**.</span></span>  
  
-   <span data-ttu-id="1e203-122">Když je hostitelskou aplikaci pokyn k zachování nebo odinstalování instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1e203-122">When a host application is instructed to persist or unload a workflow instance.</span></span>  
  
-   <span data-ttu-id="1e203-123">Pokud instance pracovního postupu je ukončeno, nebo dokončí.</span><span class="sxs-lookup"><span data-stu-id="1e203-123">When a workflow instance is terminated or finishes.</span></span>  
  
-   <span data-ttu-id="1e203-124">Když **zachovat** provádí aktivity.</span><span class="sxs-lookup"><span data-stu-id="1e203-124">When a **Persist** activity executes.</span></span>  
  
-   <span data-ttu-id="1e203-125">Instance pracovního postupu vyvinuté pomocí předchozí verze Windows Workflow Foundation, když zaznamená bod trvalost během provádění umožňuje vzájemnou spolupráci.</span><span class="sxs-lookup"><span data-stu-id="1e203-125">When an instance of a workflow developed using a previous version of Windows Workflow Foundation encounters a persistence point during interoperable execution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e203-126">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1e203-126">In This Section</span></span>  
  
-   [<span data-ttu-id="1e203-127">Úložiště instancí pracovních postupů SQL</span><span class="sxs-lookup"><span data-stu-id="1e203-127">SQL Workflow Instance Store</span></span>](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [<span data-ttu-id="1e203-128">Úložiště instancí</span><span class="sxs-lookup"><span data-stu-id="1e203-128">Instance Stores</span></span>](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [<span data-ttu-id="1e203-129">Účastníci trvalosti</span><span class="sxs-lookup"><span data-stu-id="1e203-129">Persistence Participants</span></span>](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [<span data-ttu-id="1e203-130">Osvědčené postupy pro trvalost</span><span class="sxs-lookup"><span data-stu-id="1e203-130">Persistence Best Practices</span></span>](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [<span data-ttu-id="1e203-131">Netrvalé instance pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1e203-131">Non-Persisted Workflow Instances</span></span>](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [<span data-ttu-id="1e203-132">Pozastavení a obnovení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1e203-132">Pausing and Resuming a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
