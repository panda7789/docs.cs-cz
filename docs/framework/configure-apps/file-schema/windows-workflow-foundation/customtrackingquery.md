---
title: '&lt;customTrackingQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 7ddf19ed75d50f3cd5f20de8b0e2dfcdd5ea82b0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="247d5-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="247d5-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="247d5-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="247d5-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="247d5-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="247d5-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="247d5-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="247d5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="247d5-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="247d5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="247d5-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="247d5-107">\<tracking></span></span>  
<span data-ttu-id="247d5-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="247d5-108">\<trackingProfile></span></span>  
<span data-ttu-id="247d5-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="247d5-109">\<workflow></span></span>  
<span data-ttu-id="247d5-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="247d5-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="247d5-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="247d5-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="247d5-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="247d5-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="247d5-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="247d5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="247d5-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="247d5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="247d5-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="247d5-115">Attributes</span></span>  
  
|<span data-ttu-id="247d5-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="247d5-116">Attribute</span></span>|<span data-ttu-id="247d5-117">Popis</span><span class="sxs-lookup"><span data-stu-id="247d5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="247d5-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="247d5-118">activityName</span></span>|<span data-ttu-id="247d5-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="247d5-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="247d5-120">name</span><span class="sxs-lookup"><span data-stu-id="247d5-120">name</span></span>|<span data-ttu-id="247d5-121">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="247d5-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="247d5-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="247d5-122">Child Elements</span></span>  
 <span data-ttu-id="247d5-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="247d5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="247d5-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="247d5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="247d5-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="247d5-125">Element</span></span>|<span data-ttu-id="247d5-126">Popis</span><span class="sxs-lookup"><span data-stu-id="247d5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="247d5-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="247d5-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="247d5-128">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="247d5-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="247d5-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="247d5-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>         
 [<span data-ttu-id="247d5-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="247d5-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="247d5-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="247d5-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
