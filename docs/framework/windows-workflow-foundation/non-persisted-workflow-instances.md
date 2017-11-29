---
title: "Instance pracovního postupu netrvalé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8efaba416511856d7d2e0a70e171eed2d8e2e96b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="b1b6e-102">Instance pracovního postupu netrvalé</span><span class="sxs-lookup"><span data-stu-id="b1b6e-102">Non-Persisted Workflow Instances</span></span>
<span data-ttu-id="b1b6e-103">Novou instanci pracovního postupu vytvoření která je uchována jeho stav v <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, hostitel služby vytvoří záznam pro tuto službu v úložišti instance.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-103">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="b1b6e-104">Když je následně k instanci pracovního postupu trvalé poprvé, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> uloží aktuální stav instance.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-104">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="b1b6e-105">Pokud je pracovní postup je hostovaná v aktivační službě procesů systému Windows, data nasazení služby se zapisují také do instance úložiště při první instance.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-105">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>  
  
 <span data-ttu-id="b1b6e-106">Tak dlouho, dokud k instanci pracovního postupu nebyla byla jako trvalé, je v **netrvalé** stavu.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-106">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="b1b6e-107">V tomto stavu, nelze obnovit instance pracovního postupu po provedení recyklace domény aplikace, selhání hostitele nebo počítače se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-107">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>  
  
## <a name="the-non-persisted-state"></a><span data-ttu-id="b1b6e-108">Netrvalého stavu</span><span class="sxs-lookup"><span data-stu-id="b1b6e-108">The Non-Persisted State</span></span>  
 <span data-ttu-id="b1b6e-109">Instance pracovního postupu trvanlivý nezůstanou zůstanou v netrvalého stavu v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="b1b6e-109">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>  
  
-   <span data-ttu-id="b1b6e-110">Hostitel služby spadne, než se k instanci pracovního postupu je trvalá pro první.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-110">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="b1b6e-111">Instance pracovního postupu zůstává v úložišti instance a není obnoven.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-111">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="b1b6e-112">Pokud je korelační zpráva doručena, instance pracovního postupu zase aktivní.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-112">If a correlated message arrives, the workflow instance becomes active again.</span></span>  
  
-   <span data-ttu-id="b1b6e-113">Instance pracovního postupu dojde k výjimce předtím, než je nastavené jako trvalé poprvé.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-113">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="b1b6e-114">V závislosti na tom <xref:System.Activities.UnhandledExceptionAction> vrátí, dojde k následující scénáře:</span><span class="sxs-lookup"><span data-stu-id="b1b6e-114">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>  
  
    -   <span data-ttu-id="b1b6e-115"><xref:System.Activities.UnhandledExceptionAction>je nastavena na <xref:System.Activities.UnhandledExceptionAction.Abort>: když dojde k výjimce, informace o nasazení služby je zapsán do instance úložiště a k instanci pracovního postupu je uvolněn z paměti.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-115"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="b1b6e-116">Instance pracovního postupu zůstane v netrvalého stavu a nelze znovu načíst.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-116">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>  
  
    -   <span data-ttu-id="b1b6e-117"><xref:System.Activities.UnhandledExceptionAction>je nastavena na <xref:System.Activities.UnhandledExceptionAction.Cancel> nebo <xref:System.Activities.UnhandledExceptionAction.Terminate>: když dojde k výjimce, informace o nasazení služby je zapsán do úložiště instance a stav instance aktivity je nastavený na <xref:System.Activities.ActivityInstanceState.Closed>.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-117"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>  
  
 <span data-ttu-id="b1b6e-118">Chcete-li minimalizovat riziko zjištění instance pracovního postupu odpojen netrvalý, doporučujeme setrvání pracovního postupu již v rané fázi v jeho životním cyklu.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-118">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="b1b6e-119">Detekce a odebrání netrvalé instancí</span><span class="sxs-lookup"><span data-stu-id="b1b6e-119">Detection and Removal of Non-Persisted Instances</span></span>  
 <span data-ttu-id="b1b6e-120"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Neodebere všechny instance pracovního postupu netrvalé z obchodu instance.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-120">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="b1b6e-121">Také neodstraňuje žádné vypršela platnost zámku vlastníky, která mají instance pracovního postupu netrvalé s nimi spojených.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-121">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>  
  
 <span data-ttu-id="b1b6e-122">Doporučujeme, aby správce pravidelně zjišťuje, zda úložiště instance k netrvalé instancí.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-122">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="b1b6e-123">Tak dlouho, dokud věděli, že tento pracovní postup korelační zprávy nezobrazí, mohou správci odebrat tyto instance z obchodu instance.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-123">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="b1b6e-124">Například pokud instance byla v databázi několik měsíců a se ví, že pracovní postup má obvykle životnost několik dní, je bezpečné předpokládá, že bylo inicializovaného instanci, která měla došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-124">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>  
  
 <span data-ttu-id="b1b6e-125">Najít netrvalé instancí v úložišti Instance pracovního postupu SQL můžete použít následující dotazy SQL:</span><span class="sxs-lookup"><span data-stu-id="b1b6e-125">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>  
  
-   <span data-ttu-id="b1b6e-126">Tento dotaz najde všechny instance, které ještě jako trvalé a vrátí čas ID a vytvoření (uložené v čase UTC) pro ně.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-126">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
-   <span data-ttu-id="b1b6e-127">Tento dotaz najde všechny instance, která nezůstanou a které nejsou načíst a vrátí čas ID a vytvoření (uložené v čase UTC) pro ně.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-127">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
-   <span data-ttu-id="b1b6e-128">Tento dotaz najde všechny pozastavené instancí, které ještě jako trvalé a vrátí ID, čas vytvoření (uložené v čase UTC), Důvod pozastavení a název výjimky pro ně.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-128">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 <span data-ttu-id="b1b6e-129">Použijte pozor při odstraňování netrvalé instancí.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-129">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="b1b6e-130">Obecně je bezpečné odebrání netrvalé instance vytvořené <xref:System.ServiceModel.Activities.WorkflowServiceHost> , jsou pozastavené, nebo se nenačítají.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-130">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="b1b6e-131">Tyto určité instance můžete odstranit z úložiště odstraněním je z `[System.Activities.DurableInstancing].[Instances]` zobrazení pomocí následujícího příkazu SQL, nahraďte ID správné instance.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-131">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  <span data-ttu-id="b1b6e-132">Odebrání všech instancí netrvalý, protože to zahrnuje instance, které jste právě vytvořili a ještě nezůstanou nedoporučujeme.</span><span class="sxs-lookup"><span data-stu-id="b1b6e-132">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
