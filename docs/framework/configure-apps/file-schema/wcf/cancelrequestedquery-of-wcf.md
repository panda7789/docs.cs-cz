---
title: <cancelRequestedQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 7952520edbf799e5fab6864e50962c6ec2860928
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919650"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="6e53c-102">\<cancelRequestedQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="6e53c-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="6e53c-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="6e53c-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6e53c-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="6e53c-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="6e53c-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6e53c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="6e53c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6e53c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6e53c-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="6e53c-107">\<tracking></span></span>  
<span data-ttu-id="6e53c-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="6e53c-108">\<profiles></span></span>  
<span data-ttu-id="6e53c-109">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6e53c-109">\<trackingProfile></span></span>  
<span data-ttu-id="6e53c-110">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6e53c-110">\<workflow></span></span>  
<span data-ttu-id="6e53c-111">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="6e53c-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="6e53c-112">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="6e53c-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e53c-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e53c-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e53c-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6e53c-114">Attributes and elements</span></span>

<span data-ttu-id="6e53c-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6e53c-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e53c-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="6e53c-116">Attributes</span></span>  
  
|<span data-ttu-id="6e53c-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="6e53c-117">Attribute</span></span>|<span data-ttu-id="6e53c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6e53c-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="6e53c-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="6e53c-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="6e53c-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="6e53c-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e53c-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6e53c-121">Child elements</span></span>

<span data-ttu-id="6e53c-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="6e53c-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="6e53c-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6e53c-123">Parent elements</span></span>
  
|<span data-ttu-id="6e53c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e53c-124">Element</span></span>|<span data-ttu-id="6e53c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="6e53c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e53c-126">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="6e53c-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="6e53c-127">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="6e53c-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e53c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e53c-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6e53c-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6e53c-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6e53c-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="6e53c-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
