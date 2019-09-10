---
title: <states>služby WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855036"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="17670-102">\<stavy > WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="17670-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="17670-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="17670-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="17670-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="17670-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="17670-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="17670-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="17670-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="17670-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="17670-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="17670-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="17670-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="17670-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="17670-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="17670-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="17670-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="17670-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="17670-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="17670-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="17670-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="17670-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="17670-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<stavy >**</span><span class="sxs-lookup"><span data-stu-id="17670-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17670-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17670-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17670-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="17670-115">Attributes and elements</span></span>

<span data-ttu-id="17670-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="17670-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17670-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="17670-117">Attributes</span></span>  

<span data-ttu-id="17670-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="17670-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="17670-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="17670-119">Child elements</span></span>
  
|<span data-ttu-id="17670-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="17670-120">Element</span></span>|<span data-ttu-id="17670-121">Popis</span><span class="sxs-lookup"><span data-stu-id="17670-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17670-122">\<states></span><span class="sxs-lookup"><span data-stu-id="17670-122">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="17670-123">Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="17670-123">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17670-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="17670-124">Parent elements</span></span>  
  
|<span data-ttu-id="17670-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="17670-125">Element</span></span>|<span data-ttu-id="17670-126">Popis</span><span class="sxs-lookup"><span data-stu-id="17670-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17670-127">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="17670-127">\<workflowInstanceQuery></span></span>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="17670-128">Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="17670-128">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17670-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17670-129">Remarks</span></span>

<span data-ttu-id="17670-130">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="17670-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="17670-131">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="17670-131">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="17670-132">Stav</span><span class="sxs-lookup"><span data-stu-id="17670-132">State</span></span>|<span data-ttu-id="17670-133">Popis</span><span class="sxs-lookup"><span data-stu-id="17670-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="17670-134">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="17670-134">Aborted</span></span>|<span data-ttu-id="17670-135">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="17670-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="17670-136">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="17670-136">Completed</span></span>|<span data-ttu-id="17670-137">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="17670-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="17670-138">Odstranit</span><span class="sxs-lookup"><span data-stu-id="17670-138">Deleted</span></span>|<span data-ttu-id="17670-139">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="17670-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="17670-140">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="17670-140">Idle</span></span>|<span data-ttu-id="17670-141">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="17670-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="17670-142">Trvalé</span><span class="sxs-lookup"><span data-stu-id="17670-142">Persisted</span></span>|<span data-ttu-id="17670-143">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="17670-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="17670-144">Obnovení</span><span class="sxs-lookup"><span data-stu-id="17670-144">Resumed</span></span>|<span data-ttu-id="17670-145">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="17670-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="17670-146">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="17670-146">Started</span></span>|<span data-ttu-id="17670-147">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="17670-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="17670-148">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="17670-148">UnhandledException</span></span>|<span data-ttu-id="17670-149">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="17670-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="17670-150">uvolněné</span><span class="sxs-lookup"><span data-stu-id="17670-150">Unloaded</span></span>|<span data-ttu-id="17670-151">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="17670-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="17670-152">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="17670-152">Canceled</span></span>|<span data-ttu-id="17670-153">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="17670-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="17670-154">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="17670-154">Suspended</span></span>|<span data-ttu-id="17670-155">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="17670-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="17670-156">Ukončen</span><span class="sxs-lookup"><span data-stu-id="17670-156">Terminated</span></span>|<span data-ttu-id="17670-157">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="17670-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="17670-158">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="17670-158">Unsuspended</span></span>|<span data-ttu-id="17670-159">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="17670-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17670-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="17670-160">Example</span></span>

<span data-ttu-id="17670-161">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="17670-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="17670-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17670-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="17670-163">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="17670-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="17670-164">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="17670-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
