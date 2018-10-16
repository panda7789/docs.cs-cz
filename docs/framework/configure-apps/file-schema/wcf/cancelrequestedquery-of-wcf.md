---
title: '&lt;cancelRequestedQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 3943d604b586eec37a1d153f10ac049fc9bd5747
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347564"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="2ec5a-102">&lt;cancelRequestedQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="2ec5a-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>

<span data-ttu-id="2ec5a-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="2ec5a-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="2ec5a-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="2ec5a-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="2ec5a-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2ec5a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="2ec5a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2ec5a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2ec5a-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="2ec5a-107">\<tracking></span></span>  
<span data-ttu-id="2ec5a-108">\<profily ></span><span class="sxs-lookup"><span data-stu-id="2ec5a-108">\<profiles></span></span>  
<span data-ttu-id="2ec5a-109">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="2ec5a-109">\<trackingProfile></span></span>  
<span data-ttu-id="2ec5a-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="2ec5a-110">\<workflow></span></span>  
<span data-ttu-id="2ec5a-111">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="2ec5a-111">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="2ec5a-112">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="2ec5a-112">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec5a-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ec5a-113">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                              childActivityName="String"/>
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ec5a-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ec5a-114">Attributes and elements</span></span>

<span data-ttu-id="2ec5a-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ec5a-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ec5a-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ec5a-116">Attributes</span></span>  
  
|<span data-ttu-id="2ec5a-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="2ec5a-117">Attribute</span></span>|<span data-ttu-id="2ec5a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2ec5a-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="2ec5a-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="2ec5a-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="2ec5a-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="2ec5a-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ec5a-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="2ec5a-121">Child elements</span></span>

<span data-ttu-id="2ec5a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ec5a-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="2ec5a-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="2ec5a-123">Parent elements</span></span>
  
|<span data-ttu-id="2ec5a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ec5a-124">Element</span></span>|<span data-ttu-id="2ec5a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2ec5a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ec5a-126">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="2ec5a-126">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="2ec5a-127">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="2ec5a-127">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ec5a-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ec5a-128">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2ec5a-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2ec5a-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2ec5a-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="2ec5a-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
