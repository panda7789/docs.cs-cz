---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398610"
---
# \<states>
<span data-ttu-id="cbf22-101">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="cbf22-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="cbf22-102">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="cbf22-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="cbf22-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbf22-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbf22-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cbf22-104">Attributes and Elements</span></span>  
 <span data-ttu-id="cbf22-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cbf22-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbf22-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="cbf22-106">Attributes</span></span>  
 <span data-ttu-id="cbf22-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="cbf22-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cbf22-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cbf22-108">Child Elements</span></span>  
  
|<span data-ttu-id="cbf22-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="cbf22-109">Element</span></span>|<span data-ttu-id="cbf22-110">Description</span><span class="sxs-lookup"><span data-stu-id="cbf22-110">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="cbf22-111">Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="cbf22-111">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbf22-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cbf22-112">Parent Elements</span></span>  
  
|<span data-ttu-id="cbf22-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="cbf22-113">Element</span></span>|<span data-ttu-id="cbf22-114">Description</span><span class="sxs-lookup"><span data-stu-id="cbf22-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="cbf22-115">Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="cbf22-115">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbf22-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cbf22-116">Remarks</span></span>  
 <span data-ttu-id="cbf22-117">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="cbf22-117">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="cbf22-118">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="cbf22-118">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="cbf22-119">State</span><span class="sxs-lookup"><span data-stu-id="cbf22-119">State</span></span>|<span data-ttu-id="cbf22-120">Popis</span><span class="sxs-lookup"><span data-stu-id="cbf22-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cbf22-121">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="cbf22-121">Aborted</span></span>|<span data-ttu-id="cbf22-122">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="cbf22-122">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="cbf22-123">Dokončeno</span><span class="sxs-lookup"><span data-stu-id="cbf22-123">Completed</span></span>|<span data-ttu-id="cbf22-124">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="cbf22-124">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="cbf22-125">Odstraněné</span><span class="sxs-lookup"><span data-stu-id="cbf22-125">Deleted</span></span>|<span data-ttu-id="cbf22-126">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="cbf22-126">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="cbf22-127">Období</span><span class="sxs-lookup"><span data-stu-id="cbf22-127">Idle</span></span>|<span data-ttu-id="cbf22-128">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="cbf22-128">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="cbf22-129">Trvalé</span><span class="sxs-lookup"><span data-stu-id="cbf22-129">Persisted</span></span>|<span data-ttu-id="cbf22-130">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="cbf22-130">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="cbf22-131">Obnovení</span><span class="sxs-lookup"><span data-stu-id="cbf22-131">Resumed</span></span>|<span data-ttu-id="cbf22-132">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="cbf22-132">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="cbf22-133">Zahájeno</span><span class="sxs-lookup"><span data-stu-id="cbf22-133">Started</span></span>|<span data-ttu-id="cbf22-134">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cbf22-134">The workflow instance is started.</span></span>|  
|<span data-ttu-id="cbf22-135">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="cbf22-135">UnhandledException</span></span>|<span data-ttu-id="cbf22-136">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="cbf22-136">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="cbf22-137">uvolněné</span><span class="sxs-lookup"><span data-stu-id="cbf22-137">Unloaded</span></span>|<span data-ttu-id="cbf22-138">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="cbf22-138">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="cbf22-139">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="cbf22-139">Canceled</span></span>|<span data-ttu-id="cbf22-140">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="cbf22-140">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="cbf22-141">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="cbf22-141">Suspended</span></span>|<span data-ttu-id="cbf22-142">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="cbf22-142">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="cbf22-143">Ukončen</span><span class="sxs-lookup"><span data-stu-id="cbf22-143">Terminated</span></span>|<span data-ttu-id="cbf22-144">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="cbf22-144">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="cbf22-145">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="cbf22-145">Unsuspended</span></span>|<span data-ttu-id="cbf22-146">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cbf22-146">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cbf22-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbf22-147">Example</span></span>  
 <span data-ttu-id="cbf22-148">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="cbf22-148">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbf22-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbf22-149">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cbf22-150">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="cbf22-150">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cbf22-151">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="cbf22-151">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
