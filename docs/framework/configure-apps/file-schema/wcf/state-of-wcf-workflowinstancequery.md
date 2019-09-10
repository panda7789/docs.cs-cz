---
title: <state>služby WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 80f7532f3c51680a2e34713b526dc43822db61b9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854961"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="04ffb-102">\<Stavová > služby WCF \<, workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="04ffb-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="04ffb-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="04ffb-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="04ffb-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="04ffb-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="04ffb-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="04ffb-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="04ffb-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="04ffb-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="04ffb-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="04ffb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="04ffb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="04ffb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="04ffb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="04ffb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="04ffb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="04ffb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="04ffb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="04ffb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="04ffb-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="04ffb-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="04ffb-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<stavy >** ](states-of-wcf-workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="04ffb-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)</span></span>\
<span data-ttu-id="04ffb-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> stavu**</span><span class="sxs-lookup"><span data-stu-id="04ffb-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ffb-115">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04ffb-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04ffb-116">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="04ffb-116">Attributes and elements</span></span>

<span data-ttu-id="04ffb-117">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="04ffb-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="04ffb-118">Atributy</span><span class="sxs-lookup"><span data-stu-id="04ffb-118">Attributes</span></span>

|<span data-ttu-id="04ffb-119">Atribut</span><span class="sxs-lookup"><span data-stu-id="04ffb-119">Attribute</span></span>|<span data-ttu-id="04ffb-120">Popis</span><span class="sxs-lookup"><span data-stu-id="04ffb-120">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="04ffb-121">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="04ffb-121">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04ffb-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="04ffb-122">Child elements</span></span>

<span data-ttu-id="04ffb-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="04ffb-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="04ffb-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="04ffb-124">Parent elements</span></span>

|<span data-ttu-id="04ffb-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="04ffb-125">Element</span></span>|<span data-ttu-id="04ffb-126">Popis</span><span class="sxs-lookup"><span data-stu-id="04ffb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04ffb-127">\<states></span><span class="sxs-lookup"><span data-stu-id="04ffb-127">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="04ffb-128">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="04ffb-128">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04ffb-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04ffb-129">Remarks</span></span>  

<span data-ttu-id="04ffb-130">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="04ffb-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="04ffb-131">Hodnoty možných stavů jsou popsány v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="04ffb-131">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="04ffb-132">Stav</span><span class="sxs-lookup"><span data-stu-id="04ffb-132">State</span></span>|<span data-ttu-id="04ffb-133">Popis</span><span class="sxs-lookup"><span data-stu-id="04ffb-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04ffb-134">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="04ffb-134">Aborted</span></span>|<span data-ttu-id="04ffb-135">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="04ffb-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="04ffb-136">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="04ffb-136">Completed</span></span>|<span data-ttu-id="04ffb-137">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="04ffb-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="04ffb-138">Odstranit</span><span class="sxs-lookup"><span data-stu-id="04ffb-138">Deleted</span></span>|<span data-ttu-id="04ffb-139">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="04ffb-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="04ffb-140">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="04ffb-140">Idle</span></span>|<span data-ttu-id="04ffb-141">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="04ffb-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="04ffb-142">Trvalé</span><span class="sxs-lookup"><span data-stu-id="04ffb-142">Persisted</span></span>|<span data-ttu-id="04ffb-143">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="04ffb-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="04ffb-144">Obnovení</span><span class="sxs-lookup"><span data-stu-id="04ffb-144">Resumed</span></span>|<span data-ttu-id="04ffb-145">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="04ffb-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="04ffb-146">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="04ffb-146">Started</span></span>|<span data-ttu-id="04ffb-147">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="04ffb-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="04ffb-148">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="04ffb-148">UnhandledException</span></span>|<span data-ttu-id="04ffb-149">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="04ffb-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="04ffb-150">uvolněné</span><span class="sxs-lookup"><span data-stu-id="04ffb-150">Unloaded</span></span>|<span data-ttu-id="04ffb-151">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="04ffb-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="04ffb-152">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="04ffb-152">Canceled</span></span>|<span data-ttu-id="04ffb-153">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="04ffb-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="04ffb-154">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="04ffb-154">Suspended</span></span>|<span data-ttu-id="04ffb-155">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="04ffb-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="04ffb-156">Ukončen</span><span class="sxs-lookup"><span data-stu-id="04ffb-156">Terminated</span></span>|<span data-ttu-id="04ffb-157">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="04ffb-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="04ffb-158">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="04ffb-158">Unsuspended</span></span>|<span data-ttu-id="04ffb-159">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="04ffb-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="04ffb-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="04ffb-160">Example</span></span>

<span data-ttu-id="04ffb-161">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="04ffb-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="04ffb-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04ffb-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="04ffb-163">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="04ffb-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="04ffb-164">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="04ffb-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
