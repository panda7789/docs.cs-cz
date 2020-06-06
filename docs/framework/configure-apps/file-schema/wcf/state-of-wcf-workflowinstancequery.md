---
title: <state>služby WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 80f7532f3c51680a2e34713b526dc43822db61b9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854961"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="a27c5-102">\<state>služby WCF,\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="a27c5-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="a27c5-103">Představuje kolekci předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="a27c5-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="a27c5-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="a27c5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**  
  
## <a name="syntax"></a><span data-ttu-id="a27c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a27c5-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a27c5-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a27c5-106">Attributes and elements</span></span>

<span data-ttu-id="a27c5-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a27c5-107">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="a27c5-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="a27c5-108">Attributes</span></span>

|<span data-ttu-id="a27c5-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="a27c5-109">Attribute</span></span>|<span data-ttu-id="a27c5-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a27c5-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="a27c5-111">Řetězec, který určuje předplacenému stavu z instance sledovaných pracovního postupu, pokud je vytvořena položka sledování.</span><span class="sxs-lookup"><span data-stu-id="a27c5-111">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a27c5-112">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="a27c5-112">Child elements</span></span>

<span data-ttu-id="a27c5-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="a27c5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a27c5-114">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="a27c5-114">Parent elements</span></span>

|<span data-ttu-id="a27c5-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="a27c5-115">Element</span></span>|<span data-ttu-id="a27c5-116">Description</span><span class="sxs-lookup"><span data-stu-id="a27c5-116">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="a27c5-117">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="a27c5-117">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a27c5-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a27c5-118">Remarks</span></span>  

<span data-ttu-id="a27c5-119">Vrácené záznamy jsou filtrovány státy v této kolekci.</span><span class="sxs-lookup"><span data-stu-id="a27c5-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="a27c5-120">Hodnoty možných stavů jsou popsány v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="a27c5-120">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="a27c5-121">State</span><span class="sxs-lookup"><span data-stu-id="a27c5-121">State</span></span>|<span data-ttu-id="a27c5-122">Description</span><span class="sxs-lookup"><span data-stu-id="a27c5-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a27c5-123">Bylo přerušeno</span><span class="sxs-lookup"><span data-stu-id="a27c5-123">Aborted</span></span>|<span data-ttu-id="a27c5-124">Instance pracovního postupu byla zrušena.</span><span class="sxs-lookup"><span data-stu-id="a27c5-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="a27c5-125">Dokončeno</span><span class="sxs-lookup"><span data-stu-id="a27c5-125">Completed</span></span>|<span data-ttu-id="a27c5-126">Instance pracovního postupu je dokončen.</span><span class="sxs-lookup"><span data-stu-id="a27c5-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="a27c5-127">Odstraněné</span><span class="sxs-lookup"><span data-stu-id="a27c5-127">Deleted</span></span>|<span data-ttu-id="a27c5-128">Instance pracovního postupu byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="a27c5-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="a27c5-129">Období</span><span class="sxs-lookup"><span data-stu-id="a27c5-129">Idle</span></span>|<span data-ttu-id="a27c5-130">Instance pracovního postupu nečinnosti.</span><span class="sxs-lookup"><span data-stu-id="a27c5-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="a27c5-131">Trvalé</span><span class="sxs-lookup"><span data-stu-id="a27c5-131">Persisted</span></span>|<span data-ttu-id="a27c5-132">Instance pracovního postupu je trvalý.</span><span class="sxs-lookup"><span data-stu-id="a27c5-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="a27c5-133">Obnovení</span><span class="sxs-lookup"><span data-stu-id="a27c5-133">Resumed</span></span>|<span data-ttu-id="a27c5-134">Instance pracovního postupu po obnovení.</span><span class="sxs-lookup"><span data-stu-id="a27c5-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="a27c5-135">Zahájeno</span><span class="sxs-lookup"><span data-stu-id="a27c5-135">Started</span></span>|<span data-ttu-id="a27c5-136">Je spuštěn, instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a27c5-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="a27c5-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="a27c5-137">UnhandledException</span></span>|<span data-ttu-id="a27c5-138">Instance pracovního postupu došlo k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="a27c5-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="a27c5-139">uvolněné</span><span class="sxs-lookup"><span data-stu-id="a27c5-139">Unloaded</span></span>|<span data-ttu-id="a27c5-140">Instance pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="a27c5-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="a27c5-141">Zrušeno</span><span class="sxs-lookup"><span data-stu-id="a27c5-141">Canceled</span></span>|<span data-ttu-id="a27c5-142">Instance pracovního postupu bylo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="a27c5-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="a27c5-143">Dočasně blokován.</span><span class="sxs-lookup"><span data-stu-id="a27c5-143">Suspended</span></span>|<span data-ttu-id="a27c5-144">Instance pracovního postupu je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="a27c5-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="a27c5-145">Ukončen</span><span class="sxs-lookup"><span data-stu-id="a27c5-145">Terminated</span></span>|<span data-ttu-id="a27c5-146">Instance pracovního postupu je ukončeno.</span><span class="sxs-lookup"><span data-stu-id="a27c5-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="a27c5-147">Pozastavení</span><span class="sxs-lookup"><span data-stu-id="a27c5-147">Unsuspended</span></span>|<span data-ttu-id="a27c5-148">Pozastavení je instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a27c5-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a27c5-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="a27c5-149">Example</span></span>

<span data-ttu-id="a27c5-150">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="a27c5-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="a27c5-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="a27c5-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a27c5-152">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a27c5-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a27c5-153">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="a27c5-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
