---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398642"
---
# <a name="state"></a><span data-ttu-id="0a750-101">\<> stavu</span><span class="sxs-lookup"><span data-stu-id="0a750-101">\<state></span></span>
<span data-ttu-id="0a750-102">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="0a750-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="0a750-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="0a750-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="0a750-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0a750-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0a750-105">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0a750-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="0a750-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="0a750-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="0a750-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="0a750-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="0a750-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0a750-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="0a750-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="0a750-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="0a750-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="0a750-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="0a750-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<stavy >** ](states.md)</span><span class="sxs-lookup"><span data-stu-id="0a750-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)</span></span>\
<span data-ttu-id="0a750-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> stavu**</span><span class="sxs-lookup"><span data-stu-id="0a750-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a750-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a750-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a750-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0a750-114">Attributes and Elements</span></span>  
 <span data-ttu-id="0a750-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0a750-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a750-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="0a750-116">Attributes</span></span>  
  
|<span data-ttu-id="0a750-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="0a750-117">Attribute</span></span>|<span data-ttu-id="0a750-118">Popis</span><span class="sxs-lookup"><span data-stu-id="0a750-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a750-119">name</span><span class="sxs-lookup"><span data-stu-id="0a750-119">name</span></span>|<span data-ttu-id="0a750-120">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="0a750-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a750-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0a750-121">Child Elements</span></span>  
 <span data-ttu-id="0a750-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="0a750-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a750-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0a750-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0a750-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a750-124">Element</span></span>|<span data-ttu-id="0a750-125">Popis</span><span class="sxs-lookup"><span data-stu-id="0a750-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a750-126">\<states></span><span class="sxs-lookup"><span data-stu-id="0a750-126">\<states></span></span>](states.md)|<span data-ttu-id="0a750-127">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="0a750-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a750-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a750-128">Remarks</span></span>  
 <span data-ttu-id="0a750-129">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="0a750-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="0a750-130">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="0a750-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="0a750-131">Stav</span><span class="sxs-lookup"><span data-stu-id="0a750-131">State</span></span>|<span data-ttu-id="0a750-132">Popis</span><span class="sxs-lookup"><span data-stu-id="0a750-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a750-133">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="0a750-133">Aborted</span></span>|<span data-ttu-id="0a750-134">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="0a750-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="0a750-135">Byla dokončena</span><span class="sxs-lookup"><span data-stu-id="0a750-135">Completed</span></span>|<span data-ttu-id="0a750-136">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="0a750-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="0a750-137">Odstranit</span><span class="sxs-lookup"><span data-stu-id="0a750-137">Deleted</span></span>|<span data-ttu-id="0a750-138">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="0a750-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="0a750-139">Nečinnosti</span><span class="sxs-lookup"><span data-stu-id="0a750-139">Idle</span></span>|<span data-ttu-id="0a750-140">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="0a750-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="0a750-141">Trvalé</span><span class="sxs-lookup"><span data-stu-id="0a750-141">Persisted</span></span>|<span data-ttu-id="0a750-142">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="0a750-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="0a750-143">Obnovení</span><span class="sxs-lookup"><span data-stu-id="0a750-143">Resumed</span></span>|<span data-ttu-id="0a750-144">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="0a750-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="0a750-145">Bylo zahájeno</span><span class="sxs-lookup"><span data-stu-id="0a750-145">Started</span></span>|<span data-ttu-id="0a750-146">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0a750-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="0a750-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="0a750-147">UnhandledException</span></span>|<span data-ttu-id="0a750-148">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="0a750-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="0a750-149">uvolněné</span><span class="sxs-lookup"><span data-stu-id="0a750-149">Unloaded</span></span>|<span data-ttu-id="0a750-150">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="0a750-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="0a750-151">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="0a750-151">Canceled</span></span>|<span data-ttu-id="0a750-152">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="0a750-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="0a750-153">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="0a750-153">Suspended</span></span>|<span data-ttu-id="0a750-154">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="0a750-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="0a750-155">Ukončen</span><span class="sxs-lookup"><span data-stu-id="0a750-155">Terminated</span></span>|<span data-ttu-id="0a750-156">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="0a750-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="0a750-157">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="0a750-157">Unsuspended</span></span>|<span data-ttu-id="0a750-158">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0a750-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0a750-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a750-159">Example</span></span>  
 <span data-ttu-id="0a750-160">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="0a750-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a750-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a750-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0a750-162">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="0a750-162">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0a750-163">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="0a750-163">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
