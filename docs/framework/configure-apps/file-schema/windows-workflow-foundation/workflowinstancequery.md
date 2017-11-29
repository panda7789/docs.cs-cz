---
title: '&lt;workflowInstanceQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e7ed855dc49c4e6639734dcc6a9bc1db7ae53d01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="57124-102">&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="57124-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="57124-103">Představuje dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="57124-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="57124-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="57124-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="57124-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="57124-105">\<system.serviceModel></span></span>  
<span data-ttu-id="57124-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="57124-106">\<tracking></span></span>  
<span data-ttu-id="57124-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="57124-107">\<trackingProfile></span></span>  
<span data-ttu-id="57124-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="57124-108">\<workflow></span></span>  
<span data-ttu-id="57124-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="57124-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="57124-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="57124-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57124-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57124-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57124-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="57124-112">Attributes and Elements</span></span>  
 <span data-ttu-id="57124-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="57124-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57124-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="57124-114">Attributes</span></span>  
 <span data-ttu-id="57124-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="57124-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57124-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="57124-116">Child Elements</span></span>  
  
|<span data-ttu-id="57124-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="57124-117">Element</span></span>|<span data-ttu-id="57124-118">Popis</span><span class="sxs-lookup"><span data-stu-id="57124-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57124-119">\<stavy ></span><span class="sxs-lookup"><span data-stu-id="57124-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="57124-120">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="57124-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57124-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="57124-121">Parent Elements</span></span>  
  
|<span data-ttu-id="57124-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="57124-122">Element</span></span>|<span data-ttu-id="57124-123">Popis</span><span class="sxs-lookup"><span data-stu-id="57124-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57124-124">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="57124-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="57124-125">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="57124-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57124-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57124-126">Remarks</span></span>  
 <span data-ttu-id="57124-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="57124-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="57124-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="57124-128">Example</span></span>  
 <span data-ttu-id="57124-129">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="57124-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57124-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="57124-130">See Also</span></span>  
 <span data-ttu-id="57124-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="57124-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="57124-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="57124-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="57124-133">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="57124-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="57124-134">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="57124-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
