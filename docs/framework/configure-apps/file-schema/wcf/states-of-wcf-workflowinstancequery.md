---
title: '&lt;states&gt; služby WCF, &lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: ef3d8d05dad684b07ee527dbd34ae6269ae57657
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltstatesgt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="138b1-102">&lt;states&gt; služby WCF, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="138b1-102">&lt;states&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="138b1-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="138b1-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="138b1-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="138b1-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="138b1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="138b1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="138b1-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="138b1-106">\<tracking></span></span>  
<span data-ttu-id="138b1-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="138b1-107">\<trackingProfile></span></span>  
<span data-ttu-id="138b1-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="138b1-108">\<workflow></span></span>  
<span data-ttu-id="138b1-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="138b1-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="138b1-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="138b1-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="138b1-111">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="138b1-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="138b1-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="138b1-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="138b1-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="138b1-113">Attributes and Elements</span></span>  
 <span data-ttu-id="138b1-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="138b1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="138b1-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="138b1-115">Attributes</span></span>  
 <span data-ttu-id="138b1-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="138b1-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="138b1-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="138b1-117">Child Elements</span></span>  
  
|<span data-ttu-id="138b1-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="138b1-118">Element</span></span>|<span data-ttu-id="138b1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="138b1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="138b1-120">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="138b1-120">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="138b1-121">Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="138b1-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="138b1-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="138b1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="138b1-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="138b1-123">Element</span></span>|<span data-ttu-id="138b1-124">Popis</span><span class="sxs-lookup"><span data-stu-id="138b1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="138b1-125">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="138b1-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="138b1-126">Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="138b1-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="138b1-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="138b1-127">Remarks</span></span>  
 <span data-ttu-id="138b1-128">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="138b1-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="138b1-129">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="138b1-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="138b1-130">Stav</span><span class="sxs-lookup"><span data-stu-id="138b1-130">State</span></span>|<span data-ttu-id="138b1-131">Popis</span><span class="sxs-lookup"><span data-stu-id="138b1-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="138b1-132">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="138b1-132">Aborted</span></span>|<span data-ttu-id="138b1-133">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="138b1-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="138b1-134">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="138b1-134">Completed</span></span>|<span data-ttu-id="138b1-135">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="138b1-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="138b1-136">Odstranit</span><span class="sxs-lookup"><span data-stu-id="138b1-136">Deleted</span></span>|<span data-ttu-id="138b1-137">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="138b1-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="138b1-138">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="138b1-138">Idle</span></span>|<span data-ttu-id="138b1-139">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="138b1-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="138b1-140">Trvalé</span><span class="sxs-lookup"><span data-stu-id="138b1-140">Persisted</span></span>|<span data-ttu-id="138b1-141">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="138b1-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="138b1-142">Obnovení</span><span class="sxs-lookup"><span data-stu-id="138b1-142">Resumed</span></span>|<span data-ttu-id="138b1-143">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="138b1-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="138b1-144">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="138b1-144">Started</span></span>|<span data-ttu-id="138b1-145">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="138b1-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="138b1-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="138b1-146">UnhandledException</span></span>|<span data-ttu-id="138b1-147">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="138b1-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="138b1-148">uvolněné</span><span class="sxs-lookup"><span data-stu-id="138b1-148">Unloaded</span></span>|<span data-ttu-id="138b1-149">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="138b1-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="138b1-150">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="138b1-150">Canceled</span></span>|<span data-ttu-id="138b1-151">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="138b1-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="138b1-152">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="138b1-152">Suspended</span></span>|<span data-ttu-id="138b1-153">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="138b1-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="138b1-154">Ukončen</span><span class="sxs-lookup"><span data-stu-id="138b1-154">Terminated</span></span>|<span data-ttu-id="138b1-155">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="138b1-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="138b1-156">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="138b1-156">Unsuspended</span></span>|<span data-ttu-id="138b1-157">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="138b1-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="138b1-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="138b1-158">Example</span></span>  
 <span data-ttu-id="138b1-159">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="138b1-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="138b1-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="138b1-160">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="138b1-161">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="138b1-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="138b1-162">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="138b1-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
