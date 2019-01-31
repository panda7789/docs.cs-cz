---
title: <state> služby WCF, <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 1615c83ffe0735d9e55e822f2651da41d02b1610
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270845"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="57318-102">\<Stav > služby WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="57318-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="57318-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="57318-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="57318-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="57318-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="57318-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="57318-105">\<system.serviceModel></span></span>  
<span data-ttu-id="57318-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="57318-106">\<tracking></span></span>  
<span data-ttu-id="57318-107">\<profiles></span><span class="sxs-lookup"><span data-stu-id="57318-107">\<profiles></span></span>  
<span data-ttu-id="57318-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="57318-108">\<trackingProfile></span></span>  
<span data-ttu-id="57318-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="57318-109">\<workflow></span></span>  
<span data-ttu-id="57318-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="57318-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="57318-111">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="57318-111">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="57318-112">\<states></span><span class="sxs-lookup"><span data-stu-id="57318-112">\<states></span></span>  
<span data-ttu-id="57318-113">\<Stav ></span><span class="sxs-lookup"><span data-stu-id="57318-113">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57318-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57318-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57318-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="57318-115">Attributes and elements</span></span>

<span data-ttu-id="57318-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="57318-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="57318-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="57318-117">Attributes</span></span>

|<span data-ttu-id="57318-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="57318-118">Attribute</span></span>|<span data-ttu-id="57318-119">Popis</span><span class="sxs-lookup"><span data-stu-id="57318-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="57318-120">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="57318-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57318-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="57318-121">Child elements</span></span>

<span data-ttu-id="57318-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="57318-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="57318-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="57318-123">Parent elements</span></span>

|<span data-ttu-id="57318-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="57318-124">Element</span></span>|<span data-ttu-id="57318-125">Popis</span><span class="sxs-lookup"><span data-stu-id="57318-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57318-126">\<states></span><span class="sxs-lookup"><span data-stu-id="57318-126">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="57318-127">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="57318-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57318-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57318-128">Remarks</span></span>  

<span data-ttu-id="57318-129">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="57318-129">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="57318-130">Stav možné hodnoty jsou popsány v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="57318-130">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="57318-131">Stav</span><span class="sxs-lookup"><span data-stu-id="57318-131">State</span></span>|<span data-ttu-id="57318-132">Popis</span><span class="sxs-lookup"><span data-stu-id="57318-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="57318-133">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="57318-133">Aborted</span></span>|<span data-ttu-id="57318-134">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="57318-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="57318-135">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="57318-135">Completed</span></span>|<span data-ttu-id="57318-136">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="57318-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="57318-137">Odstranit</span><span class="sxs-lookup"><span data-stu-id="57318-137">Deleted</span></span>|<span data-ttu-id="57318-138">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="57318-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="57318-139">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="57318-139">Idle</span></span>|<span data-ttu-id="57318-140">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="57318-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="57318-141">Trvalé</span><span class="sxs-lookup"><span data-stu-id="57318-141">Persisted</span></span>|<span data-ttu-id="57318-142">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="57318-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="57318-143">Obnovení</span><span class="sxs-lookup"><span data-stu-id="57318-143">Resumed</span></span>|<span data-ttu-id="57318-144">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="57318-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="57318-145">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="57318-145">Started</span></span>|<span data-ttu-id="57318-146">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="57318-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="57318-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="57318-147">UnhandledException</span></span>|<span data-ttu-id="57318-148">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="57318-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="57318-149">uvolněné</span><span class="sxs-lookup"><span data-stu-id="57318-149">Unloaded</span></span>|<span data-ttu-id="57318-150">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="57318-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="57318-151">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="57318-151">Canceled</span></span>|<span data-ttu-id="57318-152">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="57318-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="57318-153">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="57318-153">Suspended</span></span>|<span data-ttu-id="57318-154">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="57318-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="57318-155">Ukončen</span><span class="sxs-lookup"><span data-stu-id="57318-155">Terminated</span></span>|<span data-ttu-id="57318-156">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="57318-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="57318-157">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="57318-157">Unsuspended</span></span>|<span data-ttu-id="57318-158">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="57318-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="57318-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="57318-159">Example</span></span>

<span data-ttu-id="57318-160">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="57318-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="57318-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57318-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="57318-162">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="57318-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="57318-163">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="57318-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
