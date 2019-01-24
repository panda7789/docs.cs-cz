---
title: '&lt;stavy&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: d1ec35b1c434b8188fde7b546e2dee42a93f5c91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550575"
---
# <a name="ltstatesgt"></a><span data-ttu-id="fafb6-102">&lt;stavy&gt;</span><span class="sxs-lookup"><span data-stu-id="fafb6-102">&lt;states&gt;</span></span>
<span data-ttu-id="fafb6-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="fafb6-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="fafb6-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fafb6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fafb6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fafb6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="fafb6-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="fafb6-106">\<tracking></span></span>  
<span data-ttu-id="fafb6-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="fafb6-107">\<trackingProfile></span></span>  
<span data-ttu-id="fafb6-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="fafb6-108">\<workflow></span></span>  
<span data-ttu-id="fafb6-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="fafb6-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="fafb6-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="fafb6-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="fafb6-111">\<states></span><span class="sxs-lookup"><span data-stu-id="fafb6-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fafb6-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fafb6-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fafb6-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fafb6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="fafb6-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fafb6-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fafb6-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="fafb6-115">Attributes</span></span>  
 <span data-ttu-id="fafb6-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="fafb6-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fafb6-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fafb6-117">Child Elements</span></span>  
  
|<span data-ttu-id="fafb6-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="fafb6-118">Element</span></span>|<span data-ttu-id="fafb6-119">Popis</span><span class="sxs-lookup"><span data-stu-id="fafb6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fafb6-120">\<state></span><span class="sxs-lookup"><span data-stu-id="fafb6-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="fafb6-121">Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="fafb6-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fafb6-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fafb6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fafb6-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="fafb6-123">Element</span></span>|<span data-ttu-id="fafb6-124">Popis</span><span class="sxs-lookup"><span data-stu-id="fafb6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fafb6-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="fafb6-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="fafb6-126">Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="fafb6-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fafb6-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fafb6-127">Remarks</span></span>  
 <span data-ttu-id="fafb6-128">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="fafb6-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="fafb6-129">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="fafb6-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="fafb6-130">Stav</span><span class="sxs-lookup"><span data-stu-id="fafb6-130">State</span></span>|<span data-ttu-id="fafb6-131">Popis</span><span class="sxs-lookup"><span data-stu-id="fafb6-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fafb6-132">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="fafb6-132">Aborted</span></span>|<span data-ttu-id="fafb6-133">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="fafb6-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="fafb6-134">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="fafb6-134">Completed</span></span>|<span data-ttu-id="fafb6-135">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="fafb6-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="fafb6-136">Odstranit</span><span class="sxs-lookup"><span data-stu-id="fafb6-136">Deleted</span></span>|<span data-ttu-id="fafb6-137">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="fafb6-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="fafb6-138">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="fafb6-138">Idle</span></span>|<span data-ttu-id="fafb6-139">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="fafb6-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="fafb6-140">Trvalé</span><span class="sxs-lookup"><span data-stu-id="fafb6-140">Persisted</span></span>|<span data-ttu-id="fafb6-141">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="fafb6-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="fafb6-142">Obnovení</span><span class="sxs-lookup"><span data-stu-id="fafb6-142">Resumed</span></span>|<span data-ttu-id="fafb6-143">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="fafb6-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="fafb6-144">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="fafb6-144">Started</span></span>|<span data-ttu-id="fafb6-145">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fafb6-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="fafb6-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="fafb6-146">UnhandledException</span></span>|<span data-ttu-id="fafb6-147">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="fafb6-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="fafb6-148">uvolněné</span><span class="sxs-lookup"><span data-stu-id="fafb6-148">Unloaded</span></span>|<span data-ttu-id="fafb6-149">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="fafb6-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="fafb6-150">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="fafb6-150">Canceled</span></span>|<span data-ttu-id="fafb6-151">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="fafb6-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="fafb6-152">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="fafb6-152">Suspended</span></span>|<span data-ttu-id="fafb6-153">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="fafb6-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="fafb6-154">Ukončen</span><span class="sxs-lookup"><span data-stu-id="fafb6-154">Terminated</span></span>|<span data-ttu-id="fafb6-155">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="fafb6-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="fafb6-156">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="fafb6-156">Unsuspended</span></span>|<span data-ttu-id="fafb6-157">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fafb6-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fafb6-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="fafb6-158">Example</span></span>  
 <span data-ttu-id="fafb6-159">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="fafb6-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fafb6-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fafb6-160">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fafb6-161">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fafb6-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fafb6-162">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="fafb6-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
