---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 88ad61dca6c0f756a14538e7b207532ff7173ec5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624750"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="27438-101">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="27438-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="27438-102">Představuje dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="27438-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="27438-103">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="27438-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="27438-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="27438-104">\<system.serviceModel></span></span>  
<span data-ttu-id="27438-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="27438-105">\<tracking></span></span>  
<span data-ttu-id="27438-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="27438-106">\<trackingProfile></span></span>  
<span data-ttu-id="27438-107">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="27438-107">\<workflow></span></span>  
<span data-ttu-id="27438-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="27438-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="27438-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="27438-109">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27438-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27438-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27438-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="27438-111">Attributes and Elements</span></span>  
 <span data-ttu-id="27438-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="27438-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27438-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="27438-113">Attributes</span></span>  
 <span data-ttu-id="27438-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="27438-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="27438-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="27438-115">Child Elements</span></span>  
  
|<span data-ttu-id="27438-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="27438-116">Element</span></span>|<span data-ttu-id="27438-117">Popis</span><span class="sxs-lookup"><span data-stu-id="27438-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27438-118">\<states></span><span class="sxs-lookup"><span data-stu-id="27438-118">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="27438-119">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="27438-119">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27438-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="27438-120">Parent Elements</span></span>  
  
|<span data-ttu-id="27438-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="27438-121">Element</span></span>|<span data-ttu-id="27438-122">Popis</span><span class="sxs-lookup"><span data-stu-id="27438-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27438-123">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="27438-123">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="27438-124">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="27438-124">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27438-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27438-125">Remarks</span></span>  
 <span data-ttu-id="27438-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="27438-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="27438-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="27438-127">Example</span></span>  
 <span data-ttu-id="27438-128">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="27438-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27438-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27438-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="27438-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="27438-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="27438-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="27438-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
