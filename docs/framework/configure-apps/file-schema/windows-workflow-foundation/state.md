---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 38b0522b93c051473d7cdc28ae955cc3b7b58efe
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287232"
---
# <a name="state"></a><span data-ttu-id="1f7a6-101">\<Stav ></span><span class="sxs-lookup"><span data-stu-id="1f7a6-101">\<state></span></span>
<span data-ttu-id="1f7a6-102">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="1f7a6-103">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1f7a6-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="1f7a6-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1f7a6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1f7a6-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="1f7a6-105">\<tracking></span></span>  
<span data-ttu-id="1f7a6-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1f7a6-106">\<trackingProfile></span></span>  
<span data-ttu-id="1f7a6-107">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="1f7a6-107">\<workflow></span></span>  
<span data-ttu-id="1f7a6-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="1f7a6-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="1f7a6-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="1f7a6-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="1f7a6-110">\<states></span><span class="sxs-lookup"><span data-stu-id="1f7a6-110">\<states></span></span>  
<span data-ttu-id="1f7a6-111">\<Stav ></span><span class="sxs-lookup"><span data-stu-id="1f7a6-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f7a6-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f7a6-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f7a6-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1f7a6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1f7a6-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f7a6-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f7a6-115">Attributes</span></span>  
  
|<span data-ttu-id="1f7a6-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="1f7a6-116">Attribute</span></span>|<span data-ttu-id="1f7a6-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1f7a6-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f7a6-118">name</span><span class="sxs-lookup"><span data-stu-id="1f7a6-118">name</span></span>|<span data-ttu-id="1f7a6-119">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f7a6-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1f7a6-120">Child Elements</span></span>  
 <span data-ttu-id="1f7a6-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="1f7a6-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f7a6-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1f7a6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1f7a6-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="1f7a6-123">Element</span></span>|<span data-ttu-id="1f7a6-124">Popis</span><span class="sxs-lookup"><span data-stu-id="1f7a6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f7a6-125">\<states></span><span class="sxs-lookup"><span data-stu-id="1f7a6-125">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="1f7a6-126">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f7a6-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f7a6-127">Remarks</span></span>  
 <span data-ttu-id="1f7a6-128">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="1f7a6-129">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="1f7a6-130">Stav</span><span class="sxs-lookup"><span data-stu-id="1f7a6-130">State</span></span>|<span data-ttu-id="1f7a6-131">Popis</span><span class="sxs-lookup"><span data-stu-id="1f7a6-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1f7a6-132">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="1f7a6-132">Aborted</span></span>|<span data-ttu-id="1f7a6-133">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="1f7a6-134">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="1f7a6-134">Completed</span></span>|<span data-ttu-id="1f7a6-135">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="1f7a6-136">Odstranit</span><span class="sxs-lookup"><span data-stu-id="1f7a6-136">Deleted</span></span>|<span data-ttu-id="1f7a6-137">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="1f7a6-138">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="1f7a6-138">Idle</span></span>|<span data-ttu-id="1f7a6-139">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="1f7a6-140">Trvalé</span><span class="sxs-lookup"><span data-stu-id="1f7a6-140">Persisted</span></span>|<span data-ttu-id="1f7a6-141">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="1f7a6-142">Obnovení</span><span class="sxs-lookup"><span data-stu-id="1f7a6-142">Resumed</span></span>|<span data-ttu-id="1f7a6-143">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="1f7a6-144">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="1f7a6-144">Started</span></span>|<span data-ttu-id="1f7a6-145">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="1f7a6-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="1f7a6-146">UnhandledException</span></span>|<span data-ttu-id="1f7a6-147">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="1f7a6-148">uvolněné</span><span class="sxs-lookup"><span data-stu-id="1f7a6-148">Unloaded</span></span>|<span data-ttu-id="1f7a6-149">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="1f7a6-150">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="1f7a6-150">Canceled</span></span>|<span data-ttu-id="1f7a6-151">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="1f7a6-152">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-152">Suspended</span></span>|<span data-ttu-id="1f7a6-153">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="1f7a6-154">Ukončen</span><span class="sxs-lookup"><span data-stu-id="1f7a6-154">Terminated</span></span>|<span data-ttu-id="1f7a6-155">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="1f7a6-156">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="1f7a6-156">Unsuspended</span></span>|<span data-ttu-id="1f7a6-157">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1f7a6-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f7a6-158">Example</span></span>  
 <span data-ttu-id="1f7a6-159">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="1f7a6-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f7a6-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f7a6-160">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1f7a6-161">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1f7a6-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1f7a6-162">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="1f7a6-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
