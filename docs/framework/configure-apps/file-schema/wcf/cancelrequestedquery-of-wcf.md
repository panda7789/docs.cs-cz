---
title: <cancelRequestedQuery> služby WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: bd6157e63761efa954744ab08ea6c66535def514
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673347"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="d786e-102">\<cancelRequestedQuery > služby WCF</span><span class="sxs-lookup"><span data-stu-id="d786e-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="d786e-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="d786e-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d786e-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="d786e-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="d786e-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d786e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="d786e-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d786e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d786e-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="d786e-107">\<tracking></span></span>  
<span data-ttu-id="d786e-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="d786e-108">\<profiles></span></span>  
<span data-ttu-id="d786e-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d786e-109">\<trackingProfile></span></span>  
<span data-ttu-id="d786e-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="d786e-110">\<workflow></span></span>  
<span data-ttu-id="d786e-111">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="d786e-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="d786e-112">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="d786e-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d786e-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d786e-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d786e-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d786e-114">Attributes and elements</span></span>

<span data-ttu-id="d786e-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d786e-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d786e-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="d786e-116">Attributes</span></span>  
  
|<span data-ttu-id="d786e-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="d786e-117">Attribute</span></span>|<span data-ttu-id="d786e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d786e-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="d786e-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="d786e-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="d786e-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="d786e-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d786e-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="d786e-121">Child elements</span></span>

<span data-ttu-id="d786e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="d786e-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="d786e-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="d786e-123">Parent elements</span></span>
  
|<span data-ttu-id="d786e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="d786e-124">Element</span></span>|<span data-ttu-id="d786e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d786e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d786e-126">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="d786e-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="d786e-127">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="d786e-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d786e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d786e-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d786e-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d786e-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d786e-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="d786e-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
