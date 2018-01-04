---
title: "&lt;states&gt; služby WCF, &lt;workflowInstanceQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5995ebfc2cee0f636d2acd8b1cadead0bc7b67e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltstatesgt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="f24ee-102">&lt;states&gt; služby WCF, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="f24ee-102">&lt;states&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="f24ee-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="f24ee-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="f24ee-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f24ee-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="f24ee-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f24ee-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f24ee-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="f24ee-106">\<tracking></span></span>  
<span data-ttu-id="f24ee-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f24ee-107">\<trackingProfile></span></span>  
<span data-ttu-id="f24ee-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="f24ee-108">\<workflow></span></span>  
<span data-ttu-id="f24ee-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="f24ee-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="f24ee-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="f24ee-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="f24ee-111">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="f24ee-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f24ee-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f24ee-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f24ee-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f24ee-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f24ee-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f24ee-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f24ee-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="f24ee-115">Attributes</span></span>  
 <span data-ttu-id="f24ee-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="f24ee-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f24ee-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f24ee-117">Child Elements</span></span>  
  
|<span data-ttu-id="f24ee-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="f24ee-118">Element</span></span>|<span data-ttu-id="f24ee-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f24ee-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f24ee-120">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="f24ee-120">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="f24ee-121">Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="f24ee-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f24ee-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f24ee-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f24ee-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="f24ee-123">Element</span></span>|<span data-ttu-id="f24ee-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f24ee-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f24ee-125">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="f24ee-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="f24ee-126">Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="f24ee-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f24ee-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f24ee-127">Remarks</span></span>  
 <span data-ttu-id="f24ee-128">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="f24ee-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="f24ee-129">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f24ee-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="f24ee-130">Stav</span><span class="sxs-lookup"><span data-stu-id="f24ee-130">State</span></span>|<span data-ttu-id="f24ee-131">Popis</span><span class="sxs-lookup"><span data-stu-id="f24ee-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f24ee-132">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="f24ee-132">Aborted</span></span>|<span data-ttu-id="f24ee-133">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="f24ee-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="f24ee-134">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="f24ee-134">Completed</span></span>|<span data-ttu-id="f24ee-135">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="f24ee-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="f24ee-136">Odstranit</span><span class="sxs-lookup"><span data-stu-id="f24ee-136">Deleted</span></span>|<span data-ttu-id="f24ee-137">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="f24ee-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="f24ee-138">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="f24ee-138">Idle</span></span>|<span data-ttu-id="f24ee-139">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="f24ee-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="f24ee-140">Trvalé</span><span class="sxs-lookup"><span data-stu-id="f24ee-140">Persisted</span></span>|<span data-ttu-id="f24ee-141">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="f24ee-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="f24ee-142">Obnovení</span><span class="sxs-lookup"><span data-stu-id="f24ee-142">Resumed</span></span>|<span data-ttu-id="f24ee-143">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="f24ee-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="f24ee-144">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="f24ee-144">Started</span></span>|<span data-ttu-id="f24ee-145">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f24ee-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="f24ee-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="f24ee-146">UnhandledException</span></span>|<span data-ttu-id="f24ee-147">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="f24ee-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="f24ee-148">uvolněné</span><span class="sxs-lookup"><span data-stu-id="f24ee-148">Unloaded</span></span>|<span data-ttu-id="f24ee-149">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="f24ee-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="f24ee-150">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="f24ee-150">Canceled</span></span>|<span data-ttu-id="f24ee-151">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="f24ee-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="f24ee-152">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="f24ee-152">Suspended</span></span>|<span data-ttu-id="f24ee-153">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="f24ee-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="f24ee-154">Ukončen</span><span class="sxs-lookup"><span data-stu-id="f24ee-154">Terminated</span></span>|<span data-ttu-id="f24ee-155">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="f24ee-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="f24ee-156">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="f24ee-156">Unsuspended</span></span>|<span data-ttu-id="f24ee-157">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f24ee-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f24ee-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="f24ee-158">Example</span></span>  
 <span data-ttu-id="f24ee-159">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="f24ee-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f24ee-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="f24ee-160">See Also</span></span>  
 <span data-ttu-id="f24ee-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f24ee-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f24ee-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f24ee-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f24ee-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f24ee-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="f24ee-164">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="f24ee-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f24ee-165">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="f24ee-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
