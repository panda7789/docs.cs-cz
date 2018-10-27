---
title: '&lt;workflowInstanceQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 300637031c64f7c9e072f04835fc3590348ddc9e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192691"
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="f7e83-102">&lt;workflowInstanceQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="f7e83-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>

<span data-ttu-id="f7e83-103">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="f7e83-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="f7e83-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f7e83-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f7e83-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f7e83-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f7e83-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="f7e83-106">\<tracking></span></span>  
<span data-ttu-id="f7e83-107">\<profily ></span><span class="sxs-lookup"><span data-stu-id="f7e83-107">\<profiles></span></span>  
<span data-ttu-id="f7e83-108">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f7e83-108">\<trackingProfile></span></span>  
<span data-ttu-id="f7e83-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="f7e83-109">\<workflow></span></span>  
<span data-ttu-id="f7e83-110">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="f7e83-110">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e83-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7e83-111">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7e83-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f7e83-112">Attributes and elements</span></span>

<span data-ttu-id="f7e83-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f7e83-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7e83-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="f7e83-114">Attributes</span></span>  

<span data-ttu-id="f7e83-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="f7e83-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7e83-116">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="f7e83-116">Child elements</span></span>  
  
|<span data-ttu-id="f7e83-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="f7e83-117">Element</span></span>|<span data-ttu-id="f7e83-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f7e83-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7e83-119">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="f7e83-119">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="f7e83-120">Dotaz, který se používá ke sledování změny životního cyklu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f7e83-120">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7e83-121">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="f7e83-121">Parent elements</span></span>  
  
|<span data-ttu-id="f7e83-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="f7e83-122">Element</span></span>|<span data-ttu-id="f7e83-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f7e83-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7e83-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="f7e83-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f7e83-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný [ID definice aktivity](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f7e83-125">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7e83-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7e83-126">Remarks</span></span>

<span data-ttu-id="f7e83-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="f7e83-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="f7e83-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7e83-128">Example</span></span>  

<span data-ttu-id="f7e83-129">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="f7e83-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>  
    <states>  
      <state name="Started"/>  
    </states>  
  </workflowInstanceQuery>  
</workflowInstanceQueries>
```
  
## <a name="see-also"></a><span data-ttu-id="f7e83-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7e83-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f7e83-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="f7e83-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f7e83-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="f7e83-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
