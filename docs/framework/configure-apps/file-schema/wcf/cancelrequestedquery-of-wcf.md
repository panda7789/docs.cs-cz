---
title: <cancelRequestedQuery> služby WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: bd6157e63761efa954744ab08ea6c66535def514
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281330"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="265c5-102">\<cancelRequestedQuery > služby WCF</span><span class="sxs-lookup"><span data-stu-id="265c5-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="265c5-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="265c5-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="265c5-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="265c5-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="265c5-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="265c5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="265c5-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="265c5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="265c5-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="265c5-107">\<tracking></span></span>  
<span data-ttu-id="265c5-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="265c5-108">\<profiles></span></span>  
<span data-ttu-id="265c5-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="265c5-109">\<trackingProfile></span></span>  
<span data-ttu-id="265c5-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="265c5-110">\<workflow></span></span>  
<span data-ttu-id="265c5-111">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="265c5-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="265c5-112">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="265c5-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="265c5-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="265c5-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="265c5-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="265c5-114">Attributes and elements</span></span>

<span data-ttu-id="265c5-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="265c5-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="265c5-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="265c5-116">Attributes</span></span>  
  
|<span data-ttu-id="265c5-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="265c5-117">Attribute</span></span>|<span data-ttu-id="265c5-118">Popis</span><span class="sxs-lookup"><span data-stu-id="265c5-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="265c5-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="265c5-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="265c5-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="265c5-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="265c5-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="265c5-121">Child elements</span></span>

<span data-ttu-id="265c5-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="265c5-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="265c5-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="265c5-123">Parent elements</span></span>
  
|<span data-ttu-id="265c5-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="265c5-124">Element</span></span>|<span data-ttu-id="265c5-125">Popis</span><span class="sxs-lookup"><span data-stu-id="265c5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="265c5-126">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="265c5-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="265c5-127">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="265c5-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="265c5-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="265c5-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="265c5-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="265c5-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="265c5-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="265c5-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
