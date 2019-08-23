---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 9ffe9f9f69f68b6f47cbc3a75200b2867aae2384
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947442"
---
# <a name="state"></a><span data-ttu-id="dae8b-101">\<> stavu</span><span class="sxs-lookup"><span data-stu-id="dae8b-101">\<state></span></span>
<span data-ttu-id="dae8b-102">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="dae8b-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="dae8b-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="dae8b-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="dae8b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dae8b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="dae8b-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="dae8b-105">\<tracking></span></span>  
<span data-ttu-id="dae8b-106">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="dae8b-106">\<trackingProfile></span></span>  
<span data-ttu-id="dae8b-107">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="dae8b-107">\<workflow></span></span>  
<span data-ttu-id="dae8b-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="dae8b-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="dae8b-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="dae8b-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="dae8b-110">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="dae8b-110">\<states></span></span>  
<span data-ttu-id="dae8b-111">\<> stavu</span><span class="sxs-lookup"><span data-stu-id="dae8b-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae8b-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dae8b-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dae8b-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dae8b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="dae8b-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dae8b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dae8b-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="dae8b-115">Attributes</span></span>  
  
|<span data-ttu-id="dae8b-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="dae8b-116">Attribute</span></span>|<span data-ttu-id="dae8b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="dae8b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dae8b-118">name</span><span class="sxs-lookup"><span data-stu-id="dae8b-118">name</span></span>|<span data-ttu-id="dae8b-119">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="dae8b-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dae8b-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dae8b-120">Child Elements</span></span>  
 <span data-ttu-id="dae8b-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="dae8b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dae8b-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dae8b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="dae8b-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="dae8b-123">Element</span></span>|<span data-ttu-id="dae8b-124">Popis</span><span class="sxs-lookup"><span data-stu-id="dae8b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dae8b-125">\<states></span><span class="sxs-lookup"><span data-stu-id="dae8b-125">\<states></span></span>](states.md)|<span data-ttu-id="dae8b-126">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="dae8b-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dae8b-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dae8b-127">Remarks</span></span>  
 <span data-ttu-id="dae8b-128">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="dae8b-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="dae8b-129">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="dae8b-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="dae8b-130">Stav</span><span class="sxs-lookup"><span data-stu-id="dae8b-130">State</span></span>|<span data-ttu-id="dae8b-131">Popis</span><span class="sxs-lookup"><span data-stu-id="dae8b-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dae8b-132">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="dae8b-132">Aborted</span></span>|<span data-ttu-id="dae8b-133">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="dae8b-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="dae8b-134">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="dae8b-134">Completed</span></span>|<span data-ttu-id="dae8b-135">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="dae8b-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="dae8b-136">Odstranit</span><span class="sxs-lookup"><span data-stu-id="dae8b-136">Deleted</span></span>|<span data-ttu-id="dae8b-137">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="dae8b-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="dae8b-138">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="dae8b-138">Idle</span></span>|<span data-ttu-id="dae8b-139">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="dae8b-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="dae8b-140">Trvalé</span><span class="sxs-lookup"><span data-stu-id="dae8b-140">Persisted</span></span>|<span data-ttu-id="dae8b-141">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="dae8b-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="dae8b-142">Obnovení</span><span class="sxs-lookup"><span data-stu-id="dae8b-142">Resumed</span></span>|<span data-ttu-id="dae8b-143">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="dae8b-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="dae8b-144">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="dae8b-144">Started</span></span>|<span data-ttu-id="dae8b-145">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="dae8b-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="dae8b-146">UnhandledException</span></span>|<span data-ttu-id="dae8b-147">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="dae8b-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="dae8b-148">uvolněné</span><span class="sxs-lookup"><span data-stu-id="dae8b-148">Unloaded</span></span>|<span data-ttu-id="dae8b-149">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="dae8b-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="dae8b-150">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="dae8b-150">Canceled</span></span>|<span data-ttu-id="dae8b-151">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="dae8b-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="dae8b-152">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="dae8b-152">Suspended</span></span>|<span data-ttu-id="dae8b-153">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="dae8b-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="dae8b-154">Ukončen</span><span class="sxs-lookup"><span data-stu-id="dae8b-154">Terminated</span></span>|<span data-ttu-id="dae8b-155">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="dae8b-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="dae8b-156">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="dae8b-156">Unsuspended</span></span>|<span data-ttu-id="dae8b-157">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dae8b-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="dae8b-158">Example</span></span>  
 <span data-ttu-id="dae8b-159">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="dae8b-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dae8b-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dae8b-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dae8b-161">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="dae8b-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dae8b-162">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="dae8b-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
