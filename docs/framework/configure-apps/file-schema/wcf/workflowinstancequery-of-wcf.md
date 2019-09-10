---
title: <workflowInstanceQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: eaf0cd204265aac7c1421e3de0c33963e6bbb7a1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854737"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="c6145-102">\<workflowInstanceQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="c6145-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="c6145-103">Představuje dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="c6145-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="c6145-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="c6145-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c6145-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6145-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c6145-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c6145-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c6145-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sledování >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c6145-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="c6145-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilů**</span><span class="sxs-lookup"><span data-stu-id="c6145-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="c6145-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Profil TrackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c6145-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="c6145-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> pracovního postupu**](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c6145-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="c6145-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="c6145-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="c6145-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQuery >**</span><span class="sxs-lookup"><span data-stu-id="c6145-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6145-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6145-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6145-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c6145-114">Attributes and elements</span></span>  

<span data-ttu-id="c6145-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c6145-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6145-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="c6145-116">Attributes</span></span>  

<span data-ttu-id="c6145-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="c6145-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6145-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="c6145-118">Child elements</span></span>  
  
|<span data-ttu-id="c6145-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6145-119">Element</span></span>|<span data-ttu-id="c6145-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c6145-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6145-121">\<states></span><span class="sxs-lookup"><span data-stu-id="c6145-121">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="c6145-122">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="c6145-122">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6145-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="c6145-123">Parent elements</span></span>  
  
|<span data-ttu-id="c6145-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6145-124">Element</span></span>|<span data-ttu-id="c6145-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c6145-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6145-126">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="c6145-126">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="c6145-127">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="c6145-127">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6145-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6145-128">Remarks</span></span>  

<span data-ttu-id="c6145-129"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="c6145-129">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="c6145-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6145-130">Example</span></span>  

<span data-ttu-id="c6145-131">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="c6145-131">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="c6145-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6145-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c6145-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c6145-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c6145-134">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="c6145-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
