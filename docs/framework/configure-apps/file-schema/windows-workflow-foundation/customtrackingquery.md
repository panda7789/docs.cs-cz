---
title: '&lt;customTrackingQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fc06c34cb4db99f5e7b6850ed8e7cf7ed073ef72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="a8247-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="a8247-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="a8247-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="a8247-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="a8247-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="a8247-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="a8247-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a8247-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a8247-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a8247-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a8247-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="a8247-107">\<tracking></span></span>  
<span data-ttu-id="a8247-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a8247-108">\<trackingProfile></span></span>  
<span data-ttu-id="a8247-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="a8247-109">\<workflow></span></span>  
<span data-ttu-id="a8247-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="a8247-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="a8247-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="a8247-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8247-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8247-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8247-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a8247-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a8247-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a8247-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8247-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="a8247-115">Attributes</span></span>  
  
|<span data-ttu-id="a8247-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="a8247-116">Attribute</span></span>|<span data-ttu-id="a8247-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a8247-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8247-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="a8247-118">activityName</span></span>|<span data-ttu-id="a8247-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="a8247-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="a8247-120">name</span><span class="sxs-lookup"><span data-stu-id="a8247-120">name</span></span>|<span data-ttu-id="a8247-121">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="a8247-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8247-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a8247-122">Child Elements</span></span>  
 <span data-ttu-id="a8247-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="a8247-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8247-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a8247-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a8247-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="a8247-125">Element</span></span>|<span data-ttu-id="a8247-126">Popis</span><span class="sxs-lookup"><span data-stu-id="a8247-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8247-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="a8247-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="a8247-128">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="a8247-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8247-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8247-129">See Also</span></span>  
 <span data-ttu-id="a8247-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a8247-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="a8247-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a8247-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>         
 [<span data-ttu-id="a8247-132">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="a8247-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a8247-133">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="a8247-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
