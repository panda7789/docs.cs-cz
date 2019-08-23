---
title: <state>služby WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 99387a8f60e96beb2ec7706d9abf4bb6ae84b868
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938211"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="c9b72-102">\<Stavová > služby WCF \<, workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="c9b72-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="c9b72-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="c9b72-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="c9b72-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="c9b72-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c9b72-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c9b72-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c9b72-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="c9b72-106">\<tracking></span></span>  
<span data-ttu-id="c9b72-107">\<profiles></span><span class="sxs-lookup"><span data-stu-id="c9b72-107">\<profiles></span></span>  
<span data-ttu-id="c9b72-108">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c9b72-108">\<trackingProfile></span></span>  
<span data-ttu-id="c9b72-109">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c9b72-109">\<workflow></span></span>  
<span data-ttu-id="c9b72-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="c9b72-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="c9b72-111">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="c9b72-111">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="c9b72-112">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="c9b72-112">\<states></span></span>  
<span data-ttu-id="c9b72-113">\<> stavu</span><span class="sxs-lookup"><span data-stu-id="c9b72-113">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9b72-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9b72-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9b72-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c9b72-115">Attributes and elements</span></span>

<span data-ttu-id="c9b72-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c9b72-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="c9b72-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="c9b72-117">Attributes</span></span>

|<span data-ttu-id="c9b72-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="c9b72-118">Attribute</span></span>|<span data-ttu-id="c9b72-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c9b72-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c9b72-120">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="c9b72-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9b72-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="c9b72-121">Child elements</span></span>

<span data-ttu-id="c9b72-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="c9b72-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9b72-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="c9b72-123">Parent elements</span></span>

|<span data-ttu-id="c9b72-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="c9b72-124">Element</span></span>|<span data-ttu-id="c9b72-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c9b72-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9b72-126">\<states></span><span class="sxs-lookup"><span data-stu-id="c9b72-126">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="c9b72-127">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="c9b72-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9b72-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9b72-128">Remarks</span></span>  

<span data-ttu-id="c9b72-129">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="c9b72-129">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="c9b72-130">Hodnoty možných stavů jsou popsány v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="c9b72-130">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="c9b72-131">Stav</span><span class="sxs-lookup"><span data-stu-id="c9b72-131">State</span></span>|<span data-ttu-id="c9b72-132">Popis</span><span class="sxs-lookup"><span data-stu-id="c9b72-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9b72-133">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="c9b72-133">Aborted</span></span>|<span data-ttu-id="c9b72-134">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="c9b72-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="c9b72-135">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="c9b72-135">Completed</span></span>|<span data-ttu-id="c9b72-136">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="c9b72-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="c9b72-137">Odstranit</span><span class="sxs-lookup"><span data-stu-id="c9b72-137">Deleted</span></span>|<span data-ttu-id="c9b72-138">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="c9b72-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="c9b72-139">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="c9b72-139">Idle</span></span>|<span data-ttu-id="c9b72-140">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="c9b72-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="c9b72-141">Trvalé</span><span class="sxs-lookup"><span data-stu-id="c9b72-141">Persisted</span></span>|<span data-ttu-id="c9b72-142">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="c9b72-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="c9b72-143">Obnovení</span><span class="sxs-lookup"><span data-stu-id="c9b72-143">Resumed</span></span>|<span data-ttu-id="c9b72-144">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="c9b72-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="c9b72-145">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="c9b72-145">Started</span></span>|<span data-ttu-id="c9b72-146">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c9b72-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="c9b72-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="c9b72-147">UnhandledException</span></span>|<span data-ttu-id="c9b72-148">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="c9b72-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="c9b72-149">uvolněné</span><span class="sxs-lookup"><span data-stu-id="c9b72-149">Unloaded</span></span>|<span data-ttu-id="c9b72-150">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="c9b72-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="c9b72-151">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="c9b72-151">Canceled</span></span>|<span data-ttu-id="c9b72-152">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="c9b72-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="c9b72-153">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="c9b72-153">Suspended</span></span>|<span data-ttu-id="c9b72-154">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="c9b72-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="c9b72-155">Ukončen</span><span class="sxs-lookup"><span data-stu-id="c9b72-155">Terminated</span></span>|<span data-ttu-id="c9b72-156">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="c9b72-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="c9b72-157">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="c9b72-157">Unsuspended</span></span>|<span data-ttu-id="c9b72-158">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c9b72-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c9b72-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9b72-159">Example</span></span>

<span data-ttu-id="c9b72-160">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="c9b72-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="c9b72-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9b72-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c9b72-162">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c9b72-162">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c9b72-163">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="c9b72-163">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
