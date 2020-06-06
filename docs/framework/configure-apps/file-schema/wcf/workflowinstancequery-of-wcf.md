---
title: <workflowInstanceQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: eaf0cd204265aac7c1421e3de0c33963e6bbb7a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854737"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="e9afa-102">\<workflowInstanceQuery>služby WCF</span><span class="sxs-lookup"><span data-stu-id="e9afa-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="e9afa-103">Představuje dotaz, který sleduje změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="e9afa-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="e9afa-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="e9afa-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="e9afa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9afa-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9afa-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e9afa-106">Attributes and elements</span></span>  

<span data-ttu-id="e9afa-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e9afa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9afa-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="e9afa-108">Attributes</span></span>  

<span data-ttu-id="e9afa-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="e9afa-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9afa-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="e9afa-110">Child elements</span></span>  
  
|<span data-ttu-id="e9afa-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9afa-111">Element</span></span>|<span data-ttu-id="e9afa-112">Description</span><span class="sxs-lookup"><span data-stu-id="e9afa-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="e9afa-113">Kolekce předplacenému stavy z instance sledovaných pracovního postupu při vytváření záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="e9afa-113">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9afa-114">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="e9afa-114">Parent elements</span></span>  
  
|<span data-ttu-id="e9afa-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9afa-115">Element</span></span>|<span data-ttu-id="e9afa-116">Description</span><span class="sxs-lookup"><span data-stu-id="e9afa-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="e9afa-117">Představuje kolekci elementů konfigurace, které sledovat změny životního cyklu instance pracovního postupu, jako je spuštěna nebo dokončené události.</span><span class="sxs-lookup"><span data-stu-id="e9afa-117">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9afa-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9afa-118">Remarks</span></span>  

<span data-ttu-id="e9afa-119"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="e9afa-119">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="e9afa-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="e9afa-120">Example</span></span>  

<span data-ttu-id="e9afa-121">Následující konfigurace přihlásí na úrovni instance sledování záznamů pro pracovní postup `Started` stav instance pomocí tohoto dotazu.</span><span class="sxs-lookup"><span data-stu-id="e9afa-121">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="e9afa-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9afa-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e9afa-123">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e9afa-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e9afa-124">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="e9afa-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
