---
title: '&lt;workflowInstanceQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: a165d6f55afbbf1489a7355d4207a74ac1f003ef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="48522-102">&lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="48522-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="48522-103">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="48522-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="48522-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="48522-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="48522-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="48522-105">\<system.serviceModel></span></span>  
<span data-ttu-id="48522-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="48522-106">\<tracking></span></span>  
<span data-ttu-id="48522-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="48522-107">\<trackingProfile></span></span>  
<span data-ttu-id="48522-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="48522-108">\<workflow></span></span>  
<span data-ttu-id="48522-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="48522-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48522-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48522-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48522-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="48522-111">Attributes and Elements</span></span>  
 <span data-ttu-id="48522-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="48522-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48522-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="48522-113">Attributes</span></span>  
 <span data-ttu-id="48522-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="48522-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="48522-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="48522-115">Child Elements</span></span>  
  
|<span data-ttu-id="48522-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="48522-116">Element</span></span>|<span data-ttu-id="48522-117">Popis</span><span class="sxs-lookup"><span data-stu-id="48522-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48522-118">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="48522-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="48522-119">Dotaz, který se používá ke sledování změny životního cyklu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="48522-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48522-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="48522-120">Parent Elements</span></span>  
  
|<span data-ttu-id="48522-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="48522-121">Element</span></span>|<span data-ttu-id="48522-122">Popis</span><span class="sxs-lookup"><span data-stu-id="48522-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48522-123">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="48522-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="48522-124">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **activityDefinitionId** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="48522-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48522-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48522-125">Remarks</span></span>  
 <span data-ttu-id="48522-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="48522-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="48522-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="48522-127">Example</span></span>  
 <span data-ttu-id="48522-128">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="48522-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48522-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="48522-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="48522-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="48522-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="48522-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="48522-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
