---
title: Netrvalé instance pracovních postupů
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 410451f0dfeb91111e77634245aa786c4afc5b04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644262"
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="8d278-102">Netrvalé instance pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8d278-102">Non-Persisted Workflow Instances</span></span>
<span data-ttu-id="8d278-103">Když pracovního postupu je vytvořena nová instance, která udržuje svůj stav v <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, hostitel služby vytvoří záznam pro tuto službu v úložišti instancí.</span><span class="sxs-lookup"><span data-stu-id="8d278-103">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="8d278-104">Následně, když instance pracovního postupu trvala poprvé, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> uloží aktuální stav instance.</span><span class="sxs-lookup"><span data-stu-id="8d278-104">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="8d278-105">Pokud pracovní postup je hostovaný v aktivační službě procesů Windows, data nasazení služby se zapisují také do úložiště instancí při instance je trvale uložena poprvé.</span><span class="sxs-lookup"><span data-stu-id="8d278-105">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>  
  
 <span data-ttu-id="8d278-106">Za předpokladu, instance pracovního postupu ještě nebyla trvale uložena, je v **netrvalé** stavu.</span><span class="sxs-lookup"><span data-stu-id="8d278-106">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="8d278-107">V tomto stavu nelze obnovit instance pracovního postupu po provedení recyklace domény aplikace, selhání hostitele nebo selhání počítače.</span><span class="sxs-lookup"><span data-stu-id="8d278-107">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>  
  
## <a name="the-non-persisted-state"></a><span data-ttu-id="8d278-108">-Trvalý stav</span><span class="sxs-lookup"><span data-stu-id="8d278-108">The Non-Persisted State</span></span>  
 <span data-ttu-id="8d278-109">Instance trvalý pracovních postupů, které ještě nebyla trvale uložena zůstanou ve stavu netrvalé v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="8d278-109">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>  
  
- <span data-ttu-id="8d278-110">Hostitel služby spadne, než se instance pracovního postupu je trvalý poprvé.</span><span class="sxs-lookup"><span data-stu-id="8d278-110">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="8d278-111">Instance pracovního postupu zůstává v úložišti instancí a není obnoven.</span><span class="sxs-lookup"><span data-stu-id="8d278-111">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="8d278-112">Pokud je korelační přijetí e-mailu, instance pracovního postupu aktivují znovu.</span><span class="sxs-lookup"><span data-stu-id="8d278-112">If a correlated message arrives, the workflow instance becomes active again.</span></span>  
  
- <span data-ttu-id="8d278-113">Instance pracovního postupu dojde k výjimce předtím, než je umístěný prvním.</span><span class="sxs-lookup"><span data-stu-id="8d278-113">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="8d278-114">V závislosti na tom <xref:System.Activities.UnhandledExceptionAction> vrátila, dojde k následující scénáře:</span><span class="sxs-lookup"><span data-stu-id="8d278-114">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>  
  
    - <span data-ttu-id="8d278-115"><xref:System.Activities.UnhandledExceptionAction> je nastavena na <xref:System.Activities.UnhandledExceptionAction.Abort>: Když dojde k výjimce, informace o nasazení služby se zapisují do úložiště instancí a instance pracovního postupu je uvolněn z paměti.</span><span class="sxs-lookup"><span data-stu-id="8d278-115"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="8d278-116">Zůstane ve stavu netrvalé instance pracovního postupu a nelze znovu načíst.</span><span class="sxs-lookup"><span data-stu-id="8d278-116">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>  
  
    - <span data-ttu-id="8d278-117"><xref:System.Activities.UnhandledExceptionAction> je nastavena na <xref:System.Activities.UnhandledExceptionAction.Cancel> nebo <xref:System.Activities.UnhandledExceptionAction.Terminate>: Když dojde k výjimce, informace o nasazení služby se zapisují do úložiště instancí a instance stav aktivity je nastavený na <xref:System.Activities.ActivityInstanceState.Closed>.</span><span class="sxs-lookup"><span data-stu-id="8d278-117"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>  
  
 <span data-ttu-id="8d278-118">Chcete-li minimalizovat riziko vzniku pracovní postup uvolněn netrvalé instance, doporučujeme uchování pracovního postupu v rané fázi svého životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="8d278-118">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="8d278-119">Rozpoznání a odstranění netrvalé instance</span><span class="sxs-lookup"><span data-stu-id="8d278-119">Detection and Removal of Non-Persisted Instances</span></span>  
 <span data-ttu-id="8d278-120"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Neodebere všechny instance pracovního postupu netrvalé instance storu.</span><span class="sxs-lookup"><span data-stu-id="8d278-120">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="8d278-121">Všechny vlastníky vypršela platnost zámku, které mají pracovní postup netrvalé instance k nim má přiřazené také nezpůsobí odebrání.</span><span class="sxs-lookup"><span data-stu-id="8d278-121">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>  
  
 <span data-ttu-id="8d278-122">Doporučujeme vám, že správce pravidelně kontroluje úložiště instance k netrvalé instance.</span><span class="sxs-lookup"><span data-stu-id="8d278-122">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="8d278-123">Za předpokladu, ví, že tento pracovní postup neobdrží korelovaných zpráv, mohou správci odebrat tyto instance ze v úložišti instancí.</span><span class="sxs-lookup"><span data-stu-id="8d278-123">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="8d278-124">Například pokud instance v databázi na několik měsíců, a je známo, že pracovní postup má obvykle životnost několik dní, by se dá předpokládat, že bylo inicializované instance, který měl došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="8d278-124">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>  
  
 <span data-ttu-id="8d278-125">Najít netrvalé instance v Store Instance pracovního postupu SQL můžete použít následující dotazy SQL:</span><span class="sxs-lookup"><span data-stu-id="8d278-125">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>  
  
- <span data-ttu-id="8d278-126">Tento dotaz najde všechny instance, která ještě nebyla trvale uložena a vrátí čas ID a vytvoření (uložené v čase UTC) pro ně.</span><span class="sxs-lookup"><span data-stu-id="8d278-126">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
- <span data-ttu-id="8d278-127">Tento dotaz najde všechny instance, která ještě nebyla trvale uložena, a, které nejsou načtené a vrátí čas ID a vytvoření (uložené v čase UTC) pro ně.</span><span class="sxs-lookup"><span data-stu-id="8d278-127">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
- <span data-ttu-id="8d278-128">Tento dotaz najde všechny pozastavené instance, která ještě nebyla trvale uložena a vrátí ID, čas vytvoření (uložené v čase UTC), pozastavení a název výjimky pro ně.</span><span class="sxs-lookup"><span data-stu-id="8d278-128">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 <span data-ttu-id="8d278-129">Při odstraňování netrvalé instance, použijte pozornost.</span><span class="sxs-lookup"><span data-stu-id="8d278-129">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="8d278-130">Obecně je bezpečně odebrat netrvalé instance vytvořené <xref:System.ServiceModel.Activities.WorkflowServiceHost> , které jsou pozastavené, nebo se nenačítají.</span><span class="sxs-lookup"><span data-stu-id="8d278-130">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="8d278-131">Tyto konkrétní instance můžete odstranit z úložiště tak, že odstraníte je z `[System.Activities.DurableInstancing].[Instances]` s použitím následujícího příkazu SQL, nahraďte ID instance správný.</span><span class="sxs-lookup"><span data-stu-id="8d278-131">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  <span data-ttu-id="8d278-132">Nedoporučujeme odebrání všech netrvalé instance, protože to zahrnuje instance, které jste právě vytvořili a ještě nebyla trvale uložena.</span><span class="sxs-lookup"><span data-stu-id="8d278-132">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
