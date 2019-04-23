---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: e54f98c980f60d02377e38d53d9d0eb48581eec0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132480"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="7c4a5-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="7c4a5-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="7c4a5-102">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="7c4a5-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="7c4a5-103">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7c4a5-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7c4a5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7c4a5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7c4a5-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="7c4a5-105">\<tracking></span></span>  
<span data-ttu-id="7c4a5-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7c4a5-106">\<trackingProfile></span></span>  
<span data-ttu-id="7c4a5-107">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="7c4a5-107">\<workflow></span></span>  
<span data-ttu-id="7c4a5-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="7c4a5-108">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c4a5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c4a5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c4a5-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7c4a5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7c4a5-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7c4a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c4a5-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7c4a5-112">Attributes</span></span>  
 <span data-ttu-id="7c4a5-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="7c4a5-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7c4a5-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7c4a5-114">Child Elements</span></span>  
  
|<span data-ttu-id="7c4a5-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c4a5-115">Element</span></span>|<span data-ttu-id="7c4a5-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7c4a5-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c4a5-117">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="7c4a5-117">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="7c4a5-118">Dotaz, který se používá ke sledování změny životního cyklu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7c4a5-118">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c4a5-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7c4a5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7c4a5-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="7c4a5-120">Element</span></span>|<span data-ttu-id="7c4a5-121">Popis</span><span class="sxs-lookup"><span data-stu-id="7c4a5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c4a5-122">\<workflow></span><span class="sxs-lookup"><span data-stu-id="7c4a5-122">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7c4a5-123">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný **ID definice aktivity** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7c4a5-123">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c4a5-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c4a5-124">Remarks</span></span>  
 <span data-ttu-id="7c4a5-125"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="7c4a5-125">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="7c4a5-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c4a5-126">Example</span></span>  
 <span data-ttu-id="7c4a5-127">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="7c4a5-127">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c4a5-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c4a5-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7c4a5-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="7c4a5-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7c4a5-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="7c4a5-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
