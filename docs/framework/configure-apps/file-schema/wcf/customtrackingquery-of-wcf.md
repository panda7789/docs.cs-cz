---
title: '&lt;customTrackingQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: e13064afbd9f5dbc8d7216eb384001e1e005785c
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316230"
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="8930f-102">&lt;customTrackingQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="8930f-102">&lt;customTrackingQuery&gt; of WCF</span></span>

<span data-ttu-id="8930f-103">Představuje dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="8930f-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="8930f-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="8930f-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="8930f-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8930f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8930f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8930f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8930f-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="8930f-107">\<tracking></span></span>  
<span data-ttu-id="8930f-108">\<profily ></span><span class="sxs-lookup"><span data-stu-id="8930f-108">\<profiles></span></span>  
<span data-ttu-id="8930f-109">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8930f-109">\<trackingProfile></span></span>  
<span data-ttu-id="8930f-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="8930f-110">\<workflow></span></span>  
<span data-ttu-id="8930f-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="8930f-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="8930f-112">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="8930f-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8930f-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8930f-113">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8930f-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8930f-114">Attributes and elements</span></span>  

<span data-ttu-id="8930f-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8930f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8930f-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="8930f-116">Attributes</span></span>  
  
|<span data-ttu-id="8930f-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="8930f-117">Attribute</span></span>|<span data-ttu-id="8930f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8930f-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="8930f-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="8930f-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="8930f-120">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="8930f-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8930f-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="8930f-121">Child elements</span></span>

<span data-ttu-id="8930f-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="8930f-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8930f-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="8930f-123">Parent elements</span></span>

|<span data-ttu-id="8930f-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="8930f-124">Element</span></span>|<span data-ttu-id="8930f-125">Popis</span><span class="sxs-lookup"><span data-stu-id="8930f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8930f-126">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="8930f-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="8930f-127">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="8930f-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="8930f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8930f-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8930f-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8930f-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8930f-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="8930f-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
