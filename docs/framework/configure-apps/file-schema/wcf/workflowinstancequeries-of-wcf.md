---
title: <workflowInstanceQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 8a58767745efab67fb7550de8770fec2c6226117
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854768"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="9f0c5-102">\<workflowInstanceQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="9f0c5-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="9f0c5-103">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="9f0c5-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="9f0c5-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="9f0c5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9f0c5-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9f0c5-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9f0c5-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9f0c5-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9f0c5-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="9f0c5-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="9f0c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="9f0c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="9f0c5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="9f0c5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="9f0c5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="9f0c5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="9f0c5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQueries >**</span><span class="sxs-lookup"><span data-stu-id="9f0c5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f0c5-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f0c5-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f0c5-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9f0c5-113">Attributes and elements</span></span>

<span data-ttu-id="9f0c5-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9f0c5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f0c5-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="9f0c5-115">Attributes</span></span>  

<span data-ttu-id="9f0c5-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="9f0c5-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9f0c5-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="9f0c5-117">Child elements</span></span>  
  
|<span data-ttu-id="9f0c5-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="9f0c5-118">Element</span></span>|<span data-ttu-id="9f0c5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9f0c5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f0c5-120">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="9f0c5-120">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="9f0c5-121">Dotaz, který se používá ke sledování změny životního cyklu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9f0c5-121">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f0c5-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="9f0c5-122">Parent elements</span></span>  
  
|<span data-ttu-id="9f0c5-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="9f0c5-123">Element</span></span>|<span data-ttu-id="9f0c5-124">Popis</span><span class="sxs-lookup"><span data-stu-id="9f0c5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f0c5-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="9f0c5-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="9f0c5-126">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností [ID definice aktivity](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId)</span><span class="sxs-lookup"><span data-stu-id="9f0c5-126">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f0c5-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f0c5-127">Remarks</span></span>

<span data-ttu-id="9f0c5-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="9f0c5-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="9f0c5-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f0c5-129">Example</span></span>  

<span data-ttu-id="9f0c5-130">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="9f0c5-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="9f0c5-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f0c5-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9f0c5-132">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9f0c5-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9f0c5-133">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9f0c5-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
