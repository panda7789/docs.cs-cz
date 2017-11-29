---
title: "&lt;workflowInstanceQueries&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6ca8104ba2470593e07e03a7fe0bc80c9cd2f6a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="72c53-102">&lt;workflowInstanceQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="72c53-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>
<span data-ttu-id="72c53-103">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="72c53-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="72c53-104">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="72c53-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="72c53-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="72c53-105">\<system.serviceModel></span></span>  
<span data-ttu-id="72c53-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="72c53-106">\<tracking></span></span>  
<span data-ttu-id="72c53-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="72c53-107">\<trackingProfile></span></span>  
<span data-ttu-id="72c53-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="72c53-108">\<workflow></span></span>  
<span data-ttu-id="72c53-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="72c53-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72c53-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72c53-110">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72c53-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="72c53-111">Attributes and Elements</span></span>  
 <span data-ttu-id="72c53-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="72c53-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72c53-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="72c53-113">Attributes</span></span>  
 <span data-ttu-id="72c53-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="72c53-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="72c53-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="72c53-115">Child Elements</span></span>  
  
|<span data-ttu-id="72c53-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="72c53-116">Element</span></span>|<span data-ttu-id="72c53-117">Popis</span><span class="sxs-lookup"><span data-stu-id="72c53-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72c53-118">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="72c53-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="72c53-119">Dotaz, který se používá ke sledování změny životního cyklu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="72c53-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72c53-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="72c53-120">Parent Elements</span></span>  
  
|<span data-ttu-id="72c53-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="72c53-121">Element</span></span>|<span data-ttu-id="72c53-122">Popis</span><span class="sxs-lookup"><span data-stu-id="72c53-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72c53-123">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="72c53-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="72c53-124">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný [activityDefinitionId](http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) vlastnost.</span><span class="sxs-lookup"><span data-stu-id="72c53-124">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72c53-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72c53-125">Remarks</span></span>  
 <span data-ttu-id="72c53-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="72c53-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="72c53-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="72c53-127">Example</span></span>  
 <span data-ttu-id="72c53-128">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="72c53-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72c53-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="72c53-129">See Also</span></span>  
 <span data-ttu-id="72c53-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="72c53-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="72c53-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="72c53-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="72c53-132">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="72c53-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="72c53-133">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="72c53-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
