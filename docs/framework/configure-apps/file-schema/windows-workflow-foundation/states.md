---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 30cb2efa4c00c8b292a8ace6a03306d6ac76a7f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797797"
---
# <a name="states"></a><span data-ttu-id="45917-101">\<states></span><span class="sxs-lookup"><span data-stu-id="45917-101">\<states></span></span>
<span data-ttu-id="45917-102">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="45917-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="45917-103">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="45917-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="45917-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="45917-104">\<system.serviceModel></span></span>  
<span data-ttu-id="45917-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="45917-105">\<tracking></span></span>  
<span data-ttu-id="45917-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="45917-106">\<trackingProfile></span></span>  
<span data-ttu-id="45917-107">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="45917-107">\<workflow></span></span>  
<span data-ttu-id="45917-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="45917-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="45917-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="45917-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="45917-110">\<states></span><span class="sxs-lookup"><span data-stu-id="45917-110">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45917-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45917-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45917-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="45917-112">Attributes and Elements</span></span>  
 <span data-ttu-id="45917-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="45917-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45917-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="45917-114">Attributes</span></span>  
 <span data-ttu-id="45917-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="45917-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="45917-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="45917-116">Child Elements</span></span>  
  
|<span data-ttu-id="45917-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="45917-117">Element</span></span>|<span data-ttu-id="45917-118">Popis</span><span class="sxs-lookup"><span data-stu-id="45917-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45917-119">\<state></span><span class="sxs-lookup"><span data-stu-id="45917-119">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="45917-120">Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="45917-120">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="45917-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="45917-121">Parent Elements</span></span>  
  
|<span data-ttu-id="45917-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="45917-122">Element</span></span>|<span data-ttu-id="45917-123">Popis</span><span class="sxs-lookup"><span data-stu-id="45917-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45917-124">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="45917-124">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="45917-125">Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="45917-125">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45917-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45917-126">Remarks</span></span>  
 <span data-ttu-id="45917-127">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="45917-127">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="45917-128">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="45917-128">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="45917-129">Stav</span><span class="sxs-lookup"><span data-stu-id="45917-129">State</span></span>|<span data-ttu-id="45917-130">Popis</span><span class="sxs-lookup"><span data-stu-id="45917-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="45917-131">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="45917-131">Aborted</span></span>|<span data-ttu-id="45917-132">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="45917-132">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="45917-133">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="45917-133">Completed</span></span>|<span data-ttu-id="45917-134">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="45917-134">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="45917-135">Odstranit</span><span class="sxs-lookup"><span data-stu-id="45917-135">Deleted</span></span>|<span data-ttu-id="45917-136">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="45917-136">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="45917-137">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="45917-137">Idle</span></span>|<span data-ttu-id="45917-138">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="45917-138">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="45917-139">Trvalé</span><span class="sxs-lookup"><span data-stu-id="45917-139">Persisted</span></span>|<span data-ttu-id="45917-140">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="45917-140">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="45917-141">Obnovení</span><span class="sxs-lookup"><span data-stu-id="45917-141">Resumed</span></span>|<span data-ttu-id="45917-142">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="45917-142">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="45917-143">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="45917-143">Started</span></span>|<span data-ttu-id="45917-144">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="45917-144">The workflow instance is started.</span></span>|  
|<span data-ttu-id="45917-145">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="45917-145">UnhandledException</span></span>|<span data-ttu-id="45917-146">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="45917-146">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="45917-147">uvolněné</span><span class="sxs-lookup"><span data-stu-id="45917-147">Unloaded</span></span>|<span data-ttu-id="45917-148">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="45917-148">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="45917-149">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="45917-149">Canceled</span></span>|<span data-ttu-id="45917-150">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="45917-150">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="45917-151">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="45917-151">Suspended</span></span>|<span data-ttu-id="45917-152">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="45917-152">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="45917-153">Ukončen</span><span class="sxs-lookup"><span data-stu-id="45917-153">Terminated</span></span>|<span data-ttu-id="45917-154">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="45917-154">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="45917-155">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="45917-155">Unsuspended</span></span>|<span data-ttu-id="45917-156">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="45917-156">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="45917-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="45917-157">Example</span></span>  
 <span data-ttu-id="45917-158">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="45917-158">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45917-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45917-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="45917-160">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="45917-160">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="45917-161">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="45917-161">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
