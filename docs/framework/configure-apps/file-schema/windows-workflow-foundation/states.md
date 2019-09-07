---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398610"
---
# <a name="states"></a><span data-ttu-id="a3c99-101">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="a3c99-101">\<states></span></span>
<span data-ttu-id="a3c99-102">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="a3c99-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="a3c99-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="a3c99-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a3c99-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a3c99-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a3c99-105">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a3c99-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="a3c99-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="a3c99-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="a3c99-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="a3c99-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="a3c99-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a3c99-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="a3c99-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="a3c99-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="a3c99-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="a3c99-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="a3c99-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<stavy >**</span><span class="sxs-lookup"><span data-stu-id="a3c99-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3c99-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3c99-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3c99-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a3c99-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a3c99-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a3c99-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3c99-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="a3c99-115">Attributes</span></span>  
 <span data-ttu-id="a3c99-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="a3c99-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a3c99-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a3c99-117">Child Elements</span></span>  
  
|<span data-ttu-id="a3c99-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="a3c99-118">Element</span></span>|<span data-ttu-id="a3c99-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a3c99-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3c99-120">\<> stavu</span><span class="sxs-lookup"><span data-stu-id="a3c99-120">\<state></span></span>](states.md)|<span data-ttu-id="a3c99-121">Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="a3c99-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3c99-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a3c99-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a3c99-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="a3c99-123">Element</span></span>|<span data-ttu-id="a3c99-124">Popis</span><span class="sxs-lookup"><span data-stu-id="a3c99-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3c99-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="a3c99-125">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="a3c99-126">Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="a3c99-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3c99-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3c99-127">Remarks</span></span>  
 <span data-ttu-id="a3c99-128">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="a3c99-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="a3c99-129">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a3c99-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="a3c99-130">Stav</span><span class="sxs-lookup"><span data-stu-id="a3c99-130">State</span></span>|<span data-ttu-id="a3c99-131">Popis</span><span class="sxs-lookup"><span data-stu-id="a3c99-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a3c99-132">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="a3c99-132">Aborted</span></span>|<span data-ttu-id="a3c99-133">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="a3c99-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="a3c99-134">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="a3c99-134">Completed</span></span>|<span data-ttu-id="a3c99-135">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="a3c99-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="a3c99-136">Odstranit</span><span class="sxs-lookup"><span data-stu-id="a3c99-136">Deleted</span></span>|<span data-ttu-id="a3c99-137">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="a3c99-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="a3c99-138">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="a3c99-138">Idle</span></span>|<span data-ttu-id="a3c99-139">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="a3c99-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="a3c99-140">Trvalé</span><span class="sxs-lookup"><span data-stu-id="a3c99-140">Persisted</span></span>|<span data-ttu-id="a3c99-141">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="a3c99-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="a3c99-142">Obnovení</span><span class="sxs-lookup"><span data-stu-id="a3c99-142">Resumed</span></span>|<span data-ttu-id="a3c99-143">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="a3c99-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="a3c99-144">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="a3c99-144">Started</span></span>|<span data-ttu-id="a3c99-145">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a3c99-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="a3c99-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="a3c99-146">UnhandledException</span></span>|<span data-ttu-id="a3c99-147">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="a3c99-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="a3c99-148">uvolněné</span><span class="sxs-lookup"><span data-stu-id="a3c99-148">Unloaded</span></span>|<span data-ttu-id="a3c99-149">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="a3c99-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="a3c99-150">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="a3c99-150">Canceled</span></span>|<span data-ttu-id="a3c99-151">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="a3c99-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="a3c99-152">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="a3c99-152">Suspended</span></span>|<span data-ttu-id="a3c99-153">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="a3c99-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="a3c99-154">Ukončen</span><span class="sxs-lookup"><span data-stu-id="a3c99-154">Terminated</span></span>|<span data-ttu-id="a3c99-155">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="a3c99-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="a3c99-156">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="a3c99-156">Unsuspended</span></span>|<span data-ttu-id="a3c99-157">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a3c99-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a3c99-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3c99-158">Example</span></span>  
 <span data-ttu-id="a3c99-159">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="a3c99-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3c99-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3c99-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a3c99-161">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a3c99-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a3c99-162">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a3c99-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
