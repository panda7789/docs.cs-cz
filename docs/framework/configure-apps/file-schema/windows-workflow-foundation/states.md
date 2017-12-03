---
title: '&lt;stavy&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5e9050a01cf58c3c103fdbe4e8b22e173efaf5c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltstatesgt"></a><span data-ttu-id="e55be-102">&lt;stavy&gt;</span><span class="sxs-lookup"><span data-stu-id="e55be-102">&lt;states&gt;</span></span>
<span data-ttu-id="e55be-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="e55be-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="e55be-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e55be-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e55be-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e55be-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e55be-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="e55be-106">\<tracking></span></span>  
<span data-ttu-id="e55be-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e55be-107">\<trackingProfile></span></span>  
<span data-ttu-id="e55be-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="e55be-108">\<workflow></span></span>  
<span data-ttu-id="e55be-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="e55be-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="e55be-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="e55be-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="e55be-111">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="e55be-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e55be-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e55be-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e55be-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e55be-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e55be-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e55be-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e55be-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="e55be-115">Attributes</span></span>  
 <span data-ttu-id="e55be-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="e55be-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e55be-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e55be-117">Child Elements</span></span>  
  
|<span data-ttu-id="e55be-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="e55be-118">Element</span></span>|<span data-ttu-id="e55be-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e55be-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e55be-120">\<Stav ></span><span class="sxs-lookup"><span data-stu-id="e55be-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="e55be-121">Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="e55be-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e55be-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e55be-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e55be-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="e55be-123">Element</span></span>|<span data-ttu-id="e55be-124">Popis</span><span class="sxs-lookup"><span data-stu-id="e55be-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e55be-125">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="e55be-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="e55be-126">Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="e55be-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e55be-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e55be-127">Remarks</span></span>  
 <span data-ttu-id="e55be-128">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="e55be-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="e55be-129">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="e55be-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="e55be-130">Stav</span><span class="sxs-lookup"><span data-stu-id="e55be-130">State</span></span>|<span data-ttu-id="e55be-131">Popis</span><span class="sxs-lookup"><span data-stu-id="e55be-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e55be-132">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="e55be-132">Aborted</span></span>|<span data-ttu-id="e55be-133">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="e55be-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="e55be-134">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="e55be-134">Completed</span></span>|<span data-ttu-id="e55be-135">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="e55be-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="e55be-136">Odstranit</span><span class="sxs-lookup"><span data-stu-id="e55be-136">Deleted</span></span>|<span data-ttu-id="e55be-137">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="e55be-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="e55be-138">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="e55be-138">Idle</span></span>|<span data-ttu-id="e55be-139">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="e55be-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="e55be-140">Trvalé</span><span class="sxs-lookup"><span data-stu-id="e55be-140">Persisted</span></span>|<span data-ttu-id="e55be-141">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="e55be-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="e55be-142">Obnovení</span><span class="sxs-lookup"><span data-stu-id="e55be-142">Resumed</span></span>|<span data-ttu-id="e55be-143">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="e55be-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="e55be-144">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="e55be-144">Started</span></span>|<span data-ttu-id="e55be-145">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e55be-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="e55be-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="e55be-146">UnhandledException</span></span>|<span data-ttu-id="e55be-147">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="e55be-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="e55be-148">uvolněné</span><span class="sxs-lookup"><span data-stu-id="e55be-148">Unloaded</span></span>|<span data-ttu-id="e55be-149">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="e55be-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="e55be-150">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="e55be-150">Canceled</span></span>|<span data-ttu-id="e55be-151">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="e55be-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="e55be-152">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="e55be-152">Suspended</span></span>|<span data-ttu-id="e55be-153">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="e55be-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="e55be-154">Ukončen</span><span class="sxs-lookup"><span data-stu-id="e55be-154">Terminated</span></span>|<span data-ttu-id="e55be-155">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="e55be-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="e55be-156">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="e55be-156">Unsuspended</span></span>|<span data-ttu-id="e55be-157">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e55be-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e55be-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="e55be-158">Example</span></span>  
 <span data-ttu-id="e55be-159">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="e55be-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e55be-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="e55be-160">See Also</span></span>  
 <span data-ttu-id="e55be-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e55be-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e55be-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e55be-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e55be-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e55be-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e55be-164">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="e55be-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e55be-165">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="e55be-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
