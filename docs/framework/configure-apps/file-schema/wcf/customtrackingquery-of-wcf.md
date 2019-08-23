---
title: <customTrackingQuery>služby WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: b034727dc89b58794ec2834cb0ff39cd7e5f1dca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919364"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="0ec5a-102">\<customTrackingQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="0ec5a-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="0ec5a-103">Představuje dotaz, který se používá ke sledování událostí, které definujete v aktivitách kódu.</span><span class="sxs-lookup"><span data-stu-id="0ec5a-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="0ec5a-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="0ec5a-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="0ec5a-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="0ec5a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="0ec5a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0ec5a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="0ec5a-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="0ec5a-107">\<tracking></span></span>  
<span data-ttu-id="0ec5a-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="0ec5a-108">\<profiles></span></span>  
<span data-ttu-id="0ec5a-109">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="0ec5a-109">\<trackingProfile></span></span>  
<span data-ttu-id="0ec5a-110">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="0ec5a-110">\<workflow></span></span>  
<span data-ttu-id="0ec5a-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="0ec5a-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="0ec5a-112">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="0ec5a-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec5a-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ec5a-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ec5a-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0ec5a-114">Attributes and elements</span></span>  

<span data-ttu-id="0ec5a-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0ec5a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ec5a-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="0ec5a-116">Attributes</span></span>  
  
|<span data-ttu-id="0ec5a-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="0ec5a-117">Attribute</span></span>|<span data-ttu-id="0ec5a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="0ec5a-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="0ec5a-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="0ec5a-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="0ec5a-120">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="0ec5a-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ec5a-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="0ec5a-121">Child elements</span></span>

<span data-ttu-id="0ec5a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ec5a-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0ec5a-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="0ec5a-123">Parent elements</span></span>

|<span data-ttu-id="0ec5a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="0ec5a-124">Element</span></span>|<span data-ttu-id="0ec5a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="0ec5a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ec5a-126">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="0ec5a-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="0ec5a-127">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="0ec5a-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="0ec5a-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ec5a-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0ec5a-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="0ec5a-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0ec5a-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="0ec5a-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
