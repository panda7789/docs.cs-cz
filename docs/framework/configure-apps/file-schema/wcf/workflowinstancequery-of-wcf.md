---
title: '&lt;workflowInstanceQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: c3b68dda42fd7a9356366a0887feb359d0232b32
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowinstancequerygt-of-wcf"></a><span data-ttu-id="9bd66-102">&lt;workflowInstanceQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="9bd66-102">&lt;workflowInstanceQuery&gt; of WCF</span></span>
<span data-ttu-id="9bd66-103">Představuje dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="9bd66-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="9bd66-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9bd66-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="9bd66-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9bd66-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9bd66-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="9bd66-106">\<tracking></span></span>  
<span data-ttu-id="9bd66-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9bd66-107">\<trackingProfile></span></span>  
<span data-ttu-id="9bd66-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9bd66-108">\<workflow></span></span>  
<span data-ttu-id="9bd66-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="9bd66-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="9bd66-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="9bd66-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd66-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bd66-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bd66-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9bd66-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9bd66-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9bd66-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bd66-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="9bd66-114">Attributes</span></span>  
 <span data-ttu-id="9bd66-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="9bd66-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9bd66-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9bd66-116">Child Elements</span></span>  
  
|<span data-ttu-id="9bd66-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="9bd66-117">Element</span></span>|<span data-ttu-id="9bd66-118">Popis</span><span class="sxs-lookup"><span data-stu-id="9bd66-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bd66-119">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="9bd66-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="9bd66-120">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="9bd66-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9bd66-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9bd66-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9bd66-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="9bd66-122">Element</span></span>|<span data-ttu-id="9bd66-123">Popis</span><span class="sxs-lookup"><span data-stu-id="9bd66-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bd66-124">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="9bd66-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="9bd66-125">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="9bd66-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bd66-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9bd66-126">Remarks</span></span>  
 <span data-ttu-id="9bd66-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="9bd66-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="9bd66-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="9bd66-128">Example</span></span>  
 <span data-ttu-id="9bd66-129">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="9bd66-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bd66-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bd66-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="9bd66-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9bd66-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9bd66-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9bd66-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
