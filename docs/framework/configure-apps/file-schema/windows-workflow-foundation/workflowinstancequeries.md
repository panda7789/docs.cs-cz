---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 0a32e6ee22cdf984e64c1b8fa16836c4c56d0380
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932742"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="21bbc-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="21bbc-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="21bbc-102">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="21bbc-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="21bbc-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="21bbc-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="21bbc-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="21bbc-104">\<system.serviceModel></span></span>  
<span data-ttu-id="21bbc-105">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="21bbc-105">\<tracking></span></span>  
<span data-ttu-id="21bbc-106">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="21bbc-106">\<trackingProfile></span></span>  
<span data-ttu-id="21bbc-107">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="21bbc-107">\<workflow></span></span>  
<span data-ttu-id="21bbc-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="21bbc-108">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21bbc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21bbc-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21bbc-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="21bbc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="21bbc-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="21bbc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21bbc-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="21bbc-112">Attributes</span></span>  
 <span data-ttu-id="21bbc-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="21bbc-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21bbc-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="21bbc-114">Child Elements</span></span>  
  
|<span data-ttu-id="21bbc-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="21bbc-115">Element</span></span>|<span data-ttu-id="21bbc-116">Popis</span><span class="sxs-lookup"><span data-stu-id="21bbc-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21bbc-117">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="21bbc-117">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="21bbc-118">Dotaz, který se používá ke sledování změny životního cyklu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="21bbc-118">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21bbc-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="21bbc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="21bbc-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="21bbc-120">Element</span></span>|<span data-ttu-id="21bbc-121">Popis</span><span class="sxs-lookup"><span data-stu-id="21bbc-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21bbc-122">\<workflow></span><span class="sxs-lookup"><span data-stu-id="21bbc-122">\<workflow></span></span>](workflow.md)|<span data-ttu-id="21bbc-123">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="21bbc-123">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21bbc-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21bbc-124">Remarks</span></span>  
 <span data-ttu-id="21bbc-125"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="21bbc-125">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="21bbc-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="21bbc-126">Example</span></span>  
 <span data-ttu-id="21bbc-127">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="21bbc-127">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21bbc-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21bbc-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="21bbc-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="21bbc-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="21bbc-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="21bbc-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
