---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 68e44584858e55c136bc3c3dc5f1fb333485fa17
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397517"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="951ff-101">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="951ff-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="951ff-102">Představuje dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="951ff-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="951ff-103">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="951ff-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="951ff-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="951ff-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="951ff-105">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="951ff-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="951ff-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="951ff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="951ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="951ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="951ff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="951ff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="951ff-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="951ff-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="951ff-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQuery >**</span><span class="sxs-lookup"><span data-stu-id="951ff-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="951ff-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="951ff-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="951ff-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="951ff-112">Attributes and Elements</span></span>  
 <span data-ttu-id="951ff-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="951ff-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="951ff-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="951ff-114">Attributes</span></span>  
 <span data-ttu-id="951ff-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="951ff-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="951ff-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="951ff-116">Child Elements</span></span>  
  
|<span data-ttu-id="951ff-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="951ff-117">Element</span></span>|<span data-ttu-id="951ff-118">Popis</span><span class="sxs-lookup"><span data-stu-id="951ff-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="951ff-119">\<states></span><span class="sxs-lookup"><span data-stu-id="951ff-119">\<states></span></span>](states.md)|<span data-ttu-id="951ff-120">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="951ff-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="951ff-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="951ff-121">Parent Elements</span></span>  
  
|<span data-ttu-id="951ff-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="951ff-122">Element</span></span>|<span data-ttu-id="951ff-123">Popis</span><span class="sxs-lookup"><span data-stu-id="951ff-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="951ff-124">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="951ff-124">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="951ff-125">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="951ff-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="951ff-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="951ff-126">Remarks</span></span>  
 <span data-ttu-id="951ff-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="951ff-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="951ff-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="951ff-128">Example</span></span>  
 <span data-ttu-id="951ff-129">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="951ff-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="951ff-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="951ff-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="951ff-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="951ff-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="951ff-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="951ff-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
