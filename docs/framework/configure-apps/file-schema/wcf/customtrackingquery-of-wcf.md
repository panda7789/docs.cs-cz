---
title: '&lt;customTrackingQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 234703e677f838dcdccdf857ba38b8729d25a488
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146378"
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="d3452-102">&lt;customTrackingQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="d3452-102">&lt;customTrackingQuery&gt; of WCF</span></span>

<span data-ttu-id="d3452-103">Představuje dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="d3452-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="d3452-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="d3452-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="d3452-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d3452-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d3452-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d3452-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d3452-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="d3452-107">\<tracking></span></span>  
<span data-ttu-id="d3452-108">\<profily ></span><span class="sxs-lookup"><span data-stu-id="d3452-108">\<profiles></span></span>  
<span data-ttu-id="d3452-109">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d3452-109">\<trackingProfile></span></span>  
<span data-ttu-id="d3452-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="d3452-110">\<workflow></span></span>  
<span data-ttu-id="d3452-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="d3452-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="d3452-112">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="d3452-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3452-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3452-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3452-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d3452-114">Attributes and elements</span></span>  

<span data-ttu-id="d3452-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d3452-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3452-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="d3452-116">Attributes</span></span>  
  
|<span data-ttu-id="d3452-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="d3452-117">Attribute</span></span>|<span data-ttu-id="d3452-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d3452-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="d3452-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="d3452-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="d3452-120">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="d3452-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3452-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="d3452-121">Child elements</span></span>

<span data-ttu-id="d3452-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="d3452-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d3452-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="d3452-123">Parent elements</span></span>

|<span data-ttu-id="d3452-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3452-124">Element</span></span>|<span data-ttu-id="d3452-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d3452-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3452-126">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="d3452-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="d3452-127">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="d3452-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="d3452-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3452-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d3452-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d3452-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d3452-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="d3452-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
