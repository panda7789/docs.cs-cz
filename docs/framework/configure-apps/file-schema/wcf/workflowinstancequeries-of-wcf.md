---
title: <workflowInstanceQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: feae65a75f9f0b2b1b398f3f9e80ac4c8d971dcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915306"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="15946-102">\<workflowInstanceQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="15946-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="15946-103">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="15946-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="15946-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="15946-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="15946-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="15946-105">\<system.serviceModel></span></span>  
<span data-ttu-id="15946-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="15946-106">\<tracking></span></span>  
<span data-ttu-id="15946-107">\<profiles></span><span class="sxs-lookup"><span data-stu-id="15946-107">\<profiles></span></span>  
<span data-ttu-id="15946-108">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="15946-108">\<trackingProfile></span></span>  
<span data-ttu-id="15946-109">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="15946-109">\<workflow></span></span>  
<span data-ttu-id="15946-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="15946-110">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15946-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15946-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15946-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="15946-112">Attributes and elements</span></span>

<span data-ttu-id="15946-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="15946-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15946-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="15946-114">Attributes</span></span>  

<span data-ttu-id="15946-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="15946-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="15946-116">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="15946-116">Child elements</span></span>  
  
|<span data-ttu-id="15946-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="15946-117">Element</span></span>|<span data-ttu-id="15946-118">Popis</span><span class="sxs-lookup"><span data-stu-id="15946-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15946-119">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="15946-119">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="15946-120">Dotaz, který se používá ke sledování změny životního cyklu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="15946-120">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15946-121">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="15946-121">Parent elements</span></span>  
  
|<span data-ttu-id="15946-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="15946-122">Element</span></span>|<span data-ttu-id="15946-123">Popis</span><span class="sxs-lookup"><span data-stu-id="15946-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15946-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="15946-124">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="15946-125">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností [ID definice aktivity](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId)</span><span class="sxs-lookup"><span data-stu-id="15946-125">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15946-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15946-126">Remarks</span></span>

<span data-ttu-id="15946-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="15946-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="15946-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="15946-128">Example</span></span>  

<span data-ttu-id="15946-129">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="15946-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="15946-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15946-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="15946-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="15946-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="15946-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="15946-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
