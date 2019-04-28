---
title: <workflowInstanceQuery> služby WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: 726d4db3bad9f57663790e2bb4e081faba28f1ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672962"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="045a8-102">\<workflowInstanceQuery > služby WCF</span><span class="sxs-lookup"><span data-stu-id="045a8-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="045a8-103">Představuje dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="045a8-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="045a8-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="045a8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="045a8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="045a8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="045a8-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="045a8-106">\<tracking></span></span>  
<span data-ttu-id="045a8-107">\<profiles></span><span class="sxs-lookup"><span data-stu-id="045a8-107">\<profiles></span></span>  
<span data-ttu-id="045a8-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="045a8-108">\<trackingProfile></span></span>  
<span data-ttu-id="045a8-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="045a8-109">\<workflow></span></span>  
<span data-ttu-id="045a8-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="045a8-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="045a8-111">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="045a8-111">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="045a8-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="045a8-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="045a8-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="045a8-113">Attributes and elements</span></span>  

<span data-ttu-id="045a8-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="045a8-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="045a8-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="045a8-115">Attributes</span></span>  

<span data-ttu-id="045a8-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="045a8-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="045a8-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="045a8-117">Child elements</span></span>  
  
|<span data-ttu-id="045a8-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="045a8-118">Element</span></span>|<span data-ttu-id="045a8-119">Popis</span><span class="sxs-lookup"><span data-stu-id="045a8-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="045a8-120">\<states></span><span class="sxs-lookup"><span data-stu-id="045a8-120">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="045a8-121">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="045a8-121">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="045a8-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="045a8-122">Parent elements</span></span>  
  
|<span data-ttu-id="045a8-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="045a8-123">Element</span></span>|<span data-ttu-id="045a8-124">Popis</span><span class="sxs-lookup"><span data-stu-id="045a8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="045a8-125">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="045a8-125">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="045a8-126">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="045a8-126">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="045a8-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="045a8-127">Remarks</span></span>  

<span data-ttu-id="045a8-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="045a8-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="045a8-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="045a8-129">Example</span></span>  

<span data-ttu-id="045a8-130">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="045a8-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="045a8-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="045a8-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="045a8-132">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="045a8-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="045a8-133">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="045a8-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
