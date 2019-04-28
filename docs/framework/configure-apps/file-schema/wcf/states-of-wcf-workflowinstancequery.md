---
title: <states> služby WCF, <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: fad6f9c8871f79e4a1e26c893eed86ba168f6d01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757947"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="2046a-102">\<stavy > služby WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="2046a-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="2046a-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="2046a-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="2046a-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2046a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2046a-105">\<system.serviceModel> \<tracking></span><span class="sxs-lookup"><span data-stu-id="2046a-105">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="2046a-106">\<profiles></span><span class="sxs-lookup"><span data-stu-id="2046a-106">\<profiles></span></span>  
<span data-ttu-id="2046a-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2046a-107">\<trackingProfile></span></span>  
<span data-ttu-id="2046a-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="2046a-108">\<workflow></span></span>  
<span data-ttu-id="2046a-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="2046a-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="2046a-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="2046a-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="2046a-111">\<states></span><span class="sxs-lookup"><span data-stu-id="2046a-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2046a-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2046a-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2046a-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2046a-113">Attributes and elements</span></span>

<span data-ttu-id="2046a-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2046a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2046a-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="2046a-115">Attributes</span></span>  

<span data-ttu-id="2046a-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="2046a-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2046a-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="2046a-117">Child elements</span></span>
  
|<span data-ttu-id="2046a-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="2046a-118">Element</span></span>|<span data-ttu-id="2046a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2046a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2046a-120">\<states></span><span class="sxs-lookup"><span data-stu-id="2046a-120">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="2046a-121">Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="2046a-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2046a-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="2046a-122">Parent elements</span></span>  
  
|<span data-ttu-id="2046a-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="2046a-123">Element</span></span>|<span data-ttu-id="2046a-124">Popis</span><span class="sxs-lookup"><span data-stu-id="2046a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2046a-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="2046a-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="2046a-126">Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="2046a-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2046a-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2046a-127">Remarks</span></span>

<span data-ttu-id="2046a-128">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="2046a-128">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="2046a-129">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="2046a-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="2046a-130">Stav</span><span class="sxs-lookup"><span data-stu-id="2046a-130">State</span></span>|<span data-ttu-id="2046a-131">Popis</span><span class="sxs-lookup"><span data-stu-id="2046a-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2046a-132">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="2046a-132">Aborted</span></span>|<span data-ttu-id="2046a-133">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="2046a-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="2046a-134">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="2046a-134">Completed</span></span>|<span data-ttu-id="2046a-135">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="2046a-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="2046a-136">Odstranit</span><span class="sxs-lookup"><span data-stu-id="2046a-136">Deleted</span></span>|<span data-ttu-id="2046a-137">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="2046a-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="2046a-138">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="2046a-138">Idle</span></span>|<span data-ttu-id="2046a-139">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="2046a-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="2046a-140">Trvalé</span><span class="sxs-lookup"><span data-stu-id="2046a-140">Persisted</span></span>|<span data-ttu-id="2046a-141">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="2046a-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="2046a-142">Obnovení</span><span class="sxs-lookup"><span data-stu-id="2046a-142">Resumed</span></span>|<span data-ttu-id="2046a-143">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="2046a-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="2046a-144">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="2046a-144">Started</span></span>|<span data-ttu-id="2046a-145">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2046a-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="2046a-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="2046a-146">UnhandledException</span></span>|<span data-ttu-id="2046a-147">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="2046a-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="2046a-148">uvolněné</span><span class="sxs-lookup"><span data-stu-id="2046a-148">Unloaded</span></span>|<span data-ttu-id="2046a-149">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="2046a-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="2046a-150">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="2046a-150">Canceled</span></span>|<span data-ttu-id="2046a-151">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="2046a-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="2046a-152">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="2046a-152">Suspended</span></span>|<span data-ttu-id="2046a-153">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="2046a-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="2046a-154">Ukončen</span><span class="sxs-lookup"><span data-stu-id="2046a-154">Terminated</span></span>|<span data-ttu-id="2046a-155">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="2046a-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="2046a-156">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="2046a-156">Unsuspended</span></span>|<span data-ttu-id="2046a-157">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2046a-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2046a-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="2046a-158">Example</span></span>

<span data-ttu-id="2046a-159">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="2046a-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="2046a-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2046a-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2046a-161">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2046a-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2046a-162">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="2046a-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
