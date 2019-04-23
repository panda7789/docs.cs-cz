---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 6f1a9474f3f12005df364a6fb84dc63aa1b68e04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108161"
---
# <a name="state"></a><span data-ttu-id="5b0a7-101">\<Stav ></span><span class="sxs-lookup"><span data-stu-id="5b0a7-101">\<state></span></span>
<span data-ttu-id="5b0a7-102">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="5b0a7-103">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5b0a7-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5b0a7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5b0a7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5b0a7-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="5b0a7-105">\<tracking></span></span>  
<span data-ttu-id="5b0a7-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5b0a7-106">\<trackingProfile></span></span>  
<span data-ttu-id="5b0a7-107">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="5b0a7-107">\<workflow></span></span>  
<span data-ttu-id="5b0a7-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="5b0a7-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="5b0a7-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="5b0a7-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="5b0a7-110">\<states></span><span class="sxs-lookup"><span data-stu-id="5b0a7-110">\<states></span></span>  
<span data-ttu-id="5b0a7-111">\<Stav ></span><span class="sxs-lookup"><span data-stu-id="5b0a7-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b0a7-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b0a7-112">Syntax</span></span>  
  
```xml  
<tracking>
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
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b0a7-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5b0a7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5b0a7-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b0a7-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="5b0a7-115">Attributes</span></span>  
  
|<span data-ttu-id="5b0a7-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="5b0a7-116">Attribute</span></span>|<span data-ttu-id="5b0a7-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5b0a7-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b0a7-118">name</span><span class="sxs-lookup"><span data-stu-id="5b0a7-118">name</span></span>|<span data-ttu-id="5b0a7-119">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b0a7-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5b0a7-120">Child Elements</span></span>  
 <span data-ttu-id="5b0a7-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="5b0a7-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b0a7-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5b0a7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5b0a7-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="5b0a7-123">Element</span></span>|<span data-ttu-id="5b0a7-124">Popis</span><span class="sxs-lookup"><span data-stu-id="5b0a7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b0a7-125">\<states></span><span class="sxs-lookup"><span data-stu-id="5b0a7-125">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="5b0a7-126">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b0a7-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b0a7-127">Remarks</span></span>  
 <span data-ttu-id="5b0a7-128">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="5b0a7-129">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="5b0a7-130">Stav</span><span class="sxs-lookup"><span data-stu-id="5b0a7-130">State</span></span>|<span data-ttu-id="5b0a7-131">Popis</span><span class="sxs-lookup"><span data-stu-id="5b0a7-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5b0a7-132">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="5b0a7-132">Aborted</span></span>|<span data-ttu-id="5b0a7-133">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="5b0a7-134">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="5b0a7-134">Completed</span></span>|<span data-ttu-id="5b0a7-135">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="5b0a7-136">Odstranit</span><span class="sxs-lookup"><span data-stu-id="5b0a7-136">Deleted</span></span>|<span data-ttu-id="5b0a7-137">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="5b0a7-138">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="5b0a7-138">Idle</span></span>|<span data-ttu-id="5b0a7-139">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="5b0a7-140">Trvalé</span><span class="sxs-lookup"><span data-stu-id="5b0a7-140">Persisted</span></span>|<span data-ttu-id="5b0a7-141">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="5b0a7-142">Obnovení</span><span class="sxs-lookup"><span data-stu-id="5b0a7-142">Resumed</span></span>|<span data-ttu-id="5b0a7-143">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="5b0a7-144">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="5b0a7-144">Started</span></span>|<span data-ttu-id="5b0a7-145">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="5b0a7-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="5b0a7-146">UnhandledException</span></span>|<span data-ttu-id="5b0a7-147">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="5b0a7-148">uvolněné</span><span class="sxs-lookup"><span data-stu-id="5b0a7-148">Unloaded</span></span>|<span data-ttu-id="5b0a7-149">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="5b0a7-150">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="5b0a7-150">Canceled</span></span>|<span data-ttu-id="5b0a7-151">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="5b0a7-152">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-152">Suspended</span></span>|<span data-ttu-id="5b0a7-153">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="5b0a7-154">Ukončen</span><span class="sxs-lookup"><span data-stu-id="5b0a7-154">Terminated</span></span>|<span data-ttu-id="5b0a7-155">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="5b0a7-156">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="5b0a7-156">Unsuspended</span></span>|<span data-ttu-id="5b0a7-157">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b0a7-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b0a7-158">Example</span></span>  
 <span data-ttu-id="5b0a7-159">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="5b0a7-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b0a7-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b0a7-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5b0a7-161">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5b0a7-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5b0a7-162">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="5b0a7-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
