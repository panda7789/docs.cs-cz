---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 11e301de1ab3dbd4c97f236bfd07c5de4a632272
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398581"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="9186f-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="9186f-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="9186f-102">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="9186f-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="9186f-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="9186f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9186f-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9186f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9186f-105">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9186f-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="9186f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="9186f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="9186f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="9186f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="9186f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9186f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="9186f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQueries >**</span><span class="sxs-lookup"><span data-stu-id="9186f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9186f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9186f-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9186f-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9186f-111">Attributes and Elements</span></span>  

<span data-ttu-id="9186f-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9186f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9186f-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="9186f-113">Attributes</span></span>  

<span data-ttu-id="9186f-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="9186f-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9186f-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9186f-115">Child Elements</span></span>  
  
|<span data-ttu-id="9186f-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="9186f-116">Element</span></span>|<span data-ttu-id="9186f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9186f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9186f-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="9186f-118">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="9186f-119">Dotaz, který se používá ke sledování změny životního cyklu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9186f-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9186f-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9186f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9186f-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="9186f-121">Element</span></span>|<span data-ttu-id="9186f-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9186f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9186f-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="9186f-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="9186f-124">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="9186f-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9186f-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9186f-125">Remarks</span></span>  

<span data-ttu-id="9186f-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="9186f-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="9186f-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="9186f-127">Example</span></span>  

<span data-ttu-id="9186f-128">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="9186f-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9186f-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9186f-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9186f-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9186f-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9186f-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9186f-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
