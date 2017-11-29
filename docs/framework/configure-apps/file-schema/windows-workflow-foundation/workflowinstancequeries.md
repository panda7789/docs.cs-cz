---
title: '&lt;workflowInstanceQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 182a4082de6f1c67b7a0bc26662e2491623b2bba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="bc8ad-102">&lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="bc8ad-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="bc8ad-103">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="bc8ad-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="bc8ad-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bc8ad-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="bc8ad-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bc8ad-105">\<system.serviceModel></span></span>  
<span data-ttu-id="bc8ad-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="bc8ad-106">\<tracking></span></span>  
<span data-ttu-id="bc8ad-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="bc8ad-107">\<trackingProfile></span></span>  
<span data-ttu-id="bc8ad-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="bc8ad-108">\<workflow></span></span>  
<span data-ttu-id="bc8ad-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="bc8ad-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc8ad-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc8ad-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc8ad-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bc8ad-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bc8ad-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bc8ad-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc8ad-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="bc8ad-113">Attributes</span></span>  
 <span data-ttu-id="bc8ad-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="bc8ad-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bc8ad-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bc8ad-115">Child Elements</span></span>  
  
|<span data-ttu-id="bc8ad-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc8ad-116">Element</span></span>|<span data-ttu-id="bc8ad-117">Popis</span><span class="sxs-lookup"><span data-stu-id="bc8ad-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc8ad-118">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="bc8ad-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="bc8ad-119">Dotaz, který se používá ke sledování změny životního cyklu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bc8ad-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc8ad-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bc8ad-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bc8ad-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc8ad-121">Element</span></span>|<span data-ttu-id="bc8ad-122">Popis</span><span class="sxs-lookup"><span data-stu-id="bc8ad-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc8ad-123">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="bc8ad-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="bc8ad-124">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **activityDefinitionId** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bc8ad-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc8ad-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc8ad-125">Remarks</span></span>  
 <span data-ttu-id="bc8ad-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="bc8ad-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="bc8ad-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc8ad-127">Example</span></span>  
 <span data-ttu-id="bc8ad-128">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="bc8ad-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc8ad-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc8ad-129">See Also</span></span>  
 <span data-ttu-id="bc8ad-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bc8ad-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="bc8ad-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bc8ad-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="bc8ad-132">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="bc8ad-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="bc8ad-133">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="bc8ad-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
