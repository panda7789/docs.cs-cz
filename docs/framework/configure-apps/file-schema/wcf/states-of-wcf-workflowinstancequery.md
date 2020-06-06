---
title: <states>služby WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855036"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="9d224-102">\<states>služby WCF,\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="9d224-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="9d224-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="9d224-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="9d224-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="9d224-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="9d224-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d224-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d224-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9d224-106">Attributes and elements</span></span>

<span data-ttu-id="9d224-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9d224-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d224-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="9d224-108">Attributes</span></span>  

<span data-ttu-id="9d224-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="9d224-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d224-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="9d224-110">Child elements</span></span>
  
|<span data-ttu-id="9d224-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d224-111">Element</span></span>|<span data-ttu-id="9d224-112">Description</span><span class="sxs-lookup"><span data-stu-id="9d224-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="9d224-113">Odebírané stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="9d224-113">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d224-114">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="9d224-114">Parent elements</span></span>  
  
|<span data-ttu-id="9d224-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d224-115">Element</span></span>|<span data-ttu-id="9d224-116">Description</span><span class="sxs-lookup"><span data-stu-id="9d224-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="9d224-117">Dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="9d224-117">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d224-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d224-118">Remarks</span></span>

<span data-ttu-id="9d224-119">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="9d224-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="9d224-120">Stav možné hodnoty jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9d224-120">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="9d224-121">State</span><span class="sxs-lookup"><span data-stu-id="9d224-121">State</span></span>|<span data-ttu-id="9d224-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9d224-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9d224-123">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="9d224-123">Aborted</span></span>|<span data-ttu-id="9d224-124">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="9d224-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="9d224-125">Dokončeno</span><span class="sxs-lookup"><span data-stu-id="9d224-125">Completed</span></span>|<span data-ttu-id="9d224-126">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="9d224-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="9d224-127">Odstraněné</span><span class="sxs-lookup"><span data-stu-id="9d224-127">Deleted</span></span>|<span data-ttu-id="9d224-128">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="9d224-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="9d224-129">Období</span><span class="sxs-lookup"><span data-stu-id="9d224-129">Idle</span></span>|<span data-ttu-id="9d224-130">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="9d224-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="9d224-131">Trvalé</span><span class="sxs-lookup"><span data-stu-id="9d224-131">Persisted</span></span>|<span data-ttu-id="9d224-132">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="9d224-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="9d224-133">Obnovení</span><span class="sxs-lookup"><span data-stu-id="9d224-133">Resumed</span></span>|<span data-ttu-id="9d224-134">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="9d224-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="9d224-135">Zahájeno</span><span class="sxs-lookup"><span data-stu-id="9d224-135">Started</span></span>|<span data-ttu-id="9d224-136">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9d224-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="9d224-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="9d224-137">UnhandledException</span></span>|<span data-ttu-id="9d224-138">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="9d224-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="9d224-139">uvolněné</span><span class="sxs-lookup"><span data-stu-id="9d224-139">Unloaded</span></span>|<span data-ttu-id="9d224-140">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="9d224-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="9d224-141">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="9d224-141">Canceled</span></span>|<span data-ttu-id="9d224-142">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="9d224-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="9d224-143">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="9d224-143">Suspended</span></span>|<span data-ttu-id="9d224-144">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="9d224-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="9d224-145">Ukončen</span><span class="sxs-lookup"><span data-stu-id="9d224-145">Terminated</span></span>|<span data-ttu-id="9d224-146">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="9d224-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="9d224-147">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="9d224-147">Unsuspended</span></span>|<span data-ttu-id="9d224-148">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9d224-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9d224-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d224-149">Example</span></span>

<span data-ttu-id="9d224-150">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="9d224-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="9d224-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d224-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9d224-152">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9d224-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9d224-153">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9d224-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
