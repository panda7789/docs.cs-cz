---
title: '&lt;state&gt; služby WCF, &lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 69ebedec40243d3e6580b8350c1253fca83e0802
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754568"
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="1440b-102">&lt;state&gt; služby WCF, &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="1440b-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="1440b-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="1440b-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="1440b-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1440b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="1440b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1440b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="1440b-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="1440b-106">\<tracking></span></span>  
<span data-ttu-id="1440b-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1440b-107">\<trackingProfile></span></span>  
<span data-ttu-id="1440b-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="1440b-108">\<workflow></span></span>  
<span data-ttu-id="1440b-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="1440b-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="1440b-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="1440b-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="1440b-111">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="1440b-111">\<states></span></span>  
<span data-ttu-id="1440b-112">\<Stav ></span><span class="sxs-lookup"><span data-stu-id="1440b-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1440b-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1440b-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1440b-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1440b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="1440b-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1440b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1440b-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="1440b-116">Attributes</span></span>  
  
|<span data-ttu-id="1440b-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="1440b-117">Attribute</span></span>|<span data-ttu-id="1440b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="1440b-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1440b-119">name</span><span class="sxs-lookup"><span data-stu-id="1440b-119">name</span></span>|<span data-ttu-id="1440b-120">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="1440b-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1440b-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1440b-121">Child Elements</span></span>  
 <span data-ttu-id="1440b-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="1440b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1440b-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1440b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1440b-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="1440b-124">Element</span></span>|<span data-ttu-id="1440b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="1440b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1440b-126">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="1440b-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="1440b-127">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="1440b-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1440b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1440b-128">Remarks</span></span>  
 <span data-ttu-id="1440b-129">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="1440b-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="1440b-130">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="1440b-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="1440b-131">Stav</span><span class="sxs-lookup"><span data-stu-id="1440b-131">State</span></span>|<span data-ttu-id="1440b-132">Popis</span><span class="sxs-lookup"><span data-stu-id="1440b-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1440b-133">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="1440b-133">Aborted</span></span>|<span data-ttu-id="1440b-134">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="1440b-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="1440b-135">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="1440b-135">Completed</span></span>|<span data-ttu-id="1440b-136">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="1440b-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="1440b-137">Odstranit</span><span class="sxs-lookup"><span data-stu-id="1440b-137">Deleted</span></span>|<span data-ttu-id="1440b-138">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="1440b-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="1440b-139">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="1440b-139">Idle</span></span>|<span data-ttu-id="1440b-140">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="1440b-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="1440b-141">Trvalé</span><span class="sxs-lookup"><span data-stu-id="1440b-141">Persisted</span></span>|<span data-ttu-id="1440b-142">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="1440b-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="1440b-143">Obnovení</span><span class="sxs-lookup"><span data-stu-id="1440b-143">Resumed</span></span>|<span data-ttu-id="1440b-144">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="1440b-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="1440b-145">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="1440b-145">Started</span></span>|<span data-ttu-id="1440b-146">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1440b-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="1440b-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="1440b-147">UnhandledException</span></span>|<span data-ttu-id="1440b-148">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="1440b-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="1440b-149">uvolněné</span><span class="sxs-lookup"><span data-stu-id="1440b-149">Unloaded</span></span>|<span data-ttu-id="1440b-150">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="1440b-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="1440b-151">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="1440b-151">Canceled</span></span>|<span data-ttu-id="1440b-152">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="1440b-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="1440b-153">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="1440b-153">Suspended</span></span>|<span data-ttu-id="1440b-154">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="1440b-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="1440b-155">Ukončen</span><span class="sxs-lookup"><span data-stu-id="1440b-155">Terminated</span></span>|<span data-ttu-id="1440b-156">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="1440b-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="1440b-157">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="1440b-157">Unsuspended</span></span>|<span data-ttu-id="1440b-158">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1440b-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1440b-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="1440b-159">Example</span></span>  
 <span data-ttu-id="1440b-160">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="1440b-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1440b-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="1440b-161">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="1440b-162">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1440b-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1440b-163">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="1440b-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
