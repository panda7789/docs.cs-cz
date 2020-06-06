---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398642"
---
# \<state>
<span data-ttu-id="81324-101">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="81324-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="81324-102">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="81324-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="81324-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81324-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81324-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="81324-104">Attributes and Elements</span></span>  
 <span data-ttu-id="81324-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="81324-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81324-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="81324-106">Attributes</span></span>  
  
|<span data-ttu-id="81324-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="81324-107">Attribute</span></span>|<span data-ttu-id="81324-108">Popis</span><span class="sxs-lookup"><span data-stu-id="81324-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81324-109">name</span><span class="sxs-lookup"><span data-stu-id="81324-109">name</span></span>|<span data-ttu-id="81324-110">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="81324-110">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81324-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="81324-111">Child Elements</span></span>  
 <span data-ttu-id="81324-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="81324-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81324-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="81324-113">Parent Elements</span></span>  
  
|<span data-ttu-id="81324-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="81324-114">Element</span></span>|<span data-ttu-id="81324-115">Description</span><span class="sxs-lookup"><span data-stu-id="81324-115">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="81324-116">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="81324-116">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81324-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81324-117">Remarks</span></span>  
 <span data-ttu-id="81324-118">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="81324-118">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="81324-119">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="81324-119">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="81324-120">State</span><span class="sxs-lookup"><span data-stu-id="81324-120">State</span></span>|<span data-ttu-id="81324-121">Description</span><span class="sxs-lookup"><span data-stu-id="81324-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81324-122">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="81324-122">Aborted</span></span>|<span data-ttu-id="81324-123">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="81324-123">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="81324-124">Dokončeno</span><span class="sxs-lookup"><span data-stu-id="81324-124">Completed</span></span>|<span data-ttu-id="81324-125">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="81324-125">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="81324-126">Odstraněné</span><span class="sxs-lookup"><span data-stu-id="81324-126">Deleted</span></span>|<span data-ttu-id="81324-127">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="81324-127">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="81324-128">Období</span><span class="sxs-lookup"><span data-stu-id="81324-128">Idle</span></span>|<span data-ttu-id="81324-129">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="81324-129">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="81324-130">Trvalé</span><span class="sxs-lookup"><span data-stu-id="81324-130">Persisted</span></span>|<span data-ttu-id="81324-131">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="81324-131">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="81324-132">Obnovení</span><span class="sxs-lookup"><span data-stu-id="81324-132">Resumed</span></span>|<span data-ttu-id="81324-133">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="81324-133">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="81324-134">Zahájeno</span><span class="sxs-lookup"><span data-stu-id="81324-134">Started</span></span>|<span data-ttu-id="81324-135">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="81324-135">The workflow instance is started.</span></span>|  
|<span data-ttu-id="81324-136">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="81324-136">UnhandledException</span></span>|<span data-ttu-id="81324-137">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="81324-137">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="81324-138">uvolněné</span><span class="sxs-lookup"><span data-stu-id="81324-138">Unloaded</span></span>|<span data-ttu-id="81324-139">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="81324-139">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="81324-140">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="81324-140">Canceled</span></span>|<span data-ttu-id="81324-141">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="81324-141">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="81324-142">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="81324-142">Suspended</span></span>|<span data-ttu-id="81324-143">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="81324-143">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="81324-144">Ukončen</span><span class="sxs-lookup"><span data-stu-id="81324-144">Terminated</span></span>|<span data-ttu-id="81324-145">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="81324-145">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="81324-146">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="81324-146">Unsuspended</span></span>|<span data-ttu-id="81324-147">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="81324-147">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="81324-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="81324-148">Example</span></span>  
 <span data-ttu-id="81324-149">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="81324-149">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="81324-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="81324-150">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="81324-151">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="81324-151">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="81324-152">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="81324-152">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
