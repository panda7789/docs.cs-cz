---
title: '&lt;state&gt; služby WCF, &lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 168a6980e955f602ee60bff26461f06cb16c836a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145923"
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="e09d9-102">&lt;state&gt; služby WCF, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="e09d9-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="e09d9-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="e09d9-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="e09d9-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e09d9-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e09d9-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e09d9-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e09d9-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="e09d9-106">\<tracking></span></span>  
<span data-ttu-id="e09d9-107">\<profily ></span><span class="sxs-lookup"><span data-stu-id="e09d9-107">\<profiles></span></span>  
<span data-ttu-id="e09d9-108">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e09d9-108">\<trackingProfile></span></span>  
<span data-ttu-id="e09d9-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="e09d9-109">\<workflow></span></span>  
<span data-ttu-id="e09d9-110">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="e09d9-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="e09d9-111">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="e09d9-111">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="e09d9-112">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="e09d9-112">\<states></span></span>  
<span data-ttu-id="e09d9-113">\<Stav ></span><span class="sxs-lookup"><span data-stu-id="e09d9-113">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e09d9-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e09d9-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e09d9-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e09d9-115">Attributes and elements</span></span>

<span data-ttu-id="e09d9-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e09d9-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="e09d9-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="e09d9-117">Attributes</span></span>

|<span data-ttu-id="e09d9-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="e09d9-118">Attribute</span></span>|<span data-ttu-id="e09d9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e09d9-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="e09d9-120">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="e09d9-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e09d9-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="e09d9-121">Child elements</span></span>

<span data-ttu-id="e09d9-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="e09d9-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e09d9-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="e09d9-123">Parent elements</span></span>

|<span data-ttu-id="e09d9-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="e09d9-124">Element</span></span>|<span data-ttu-id="e09d9-125">Popis</span><span class="sxs-lookup"><span data-stu-id="e09d9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e09d9-126">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="e09d9-126">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="e09d9-127">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="e09d9-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e09d9-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e09d9-128">Remarks</span></span>  

<span data-ttu-id="e09d9-129">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="e09d9-129">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="e09d9-130">Stav možné hodnoty jsou popsány v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="e09d9-130">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="e09d9-131">Stav</span><span class="sxs-lookup"><span data-stu-id="e09d9-131">State</span></span>|<span data-ttu-id="e09d9-132">Popis</span><span class="sxs-lookup"><span data-stu-id="e09d9-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e09d9-133">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="e09d9-133">Aborted</span></span>|<span data-ttu-id="e09d9-134">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="e09d9-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="e09d9-135">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="e09d9-135">Completed</span></span>|<span data-ttu-id="e09d9-136">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="e09d9-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="e09d9-137">Odstranit</span><span class="sxs-lookup"><span data-stu-id="e09d9-137">Deleted</span></span>|<span data-ttu-id="e09d9-138">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="e09d9-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="e09d9-139">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="e09d9-139">Idle</span></span>|<span data-ttu-id="e09d9-140">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="e09d9-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="e09d9-141">Trvalé</span><span class="sxs-lookup"><span data-stu-id="e09d9-141">Persisted</span></span>|<span data-ttu-id="e09d9-142">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="e09d9-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="e09d9-143">Obnovení</span><span class="sxs-lookup"><span data-stu-id="e09d9-143">Resumed</span></span>|<span data-ttu-id="e09d9-144">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="e09d9-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="e09d9-145">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="e09d9-145">Started</span></span>|<span data-ttu-id="e09d9-146">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e09d9-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="e09d9-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="e09d9-147">UnhandledException</span></span>|<span data-ttu-id="e09d9-148">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="e09d9-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="e09d9-149">uvolněné</span><span class="sxs-lookup"><span data-stu-id="e09d9-149">Unloaded</span></span>|<span data-ttu-id="e09d9-150">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="e09d9-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="e09d9-151">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="e09d9-151">Canceled</span></span>|<span data-ttu-id="e09d9-152">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="e09d9-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="e09d9-153">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="e09d9-153">Suspended</span></span>|<span data-ttu-id="e09d9-154">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="e09d9-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="e09d9-155">Ukončen</span><span class="sxs-lookup"><span data-stu-id="e09d9-155">Terminated</span></span>|<span data-ttu-id="e09d9-156">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="e09d9-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="e09d9-157">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="e09d9-157">Unsuspended</span></span>|<span data-ttu-id="e09d9-158">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e09d9-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e09d9-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="e09d9-159">Example</span></span>

<span data-ttu-id="e09d9-160">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="e09d9-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="e09d9-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e09d9-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e09d9-162">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e09d9-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e09d9-163">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="e09d9-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
