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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 908c340167d50d4d16e0eeff7cc2e01290b55e7a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="0a519-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="0a519-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="0a519-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="0a519-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="0a519-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="0a519-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="0a519-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0a519-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="0a519-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0a519-106">\<system.serviceModel></span></span>  
<span data-ttu-id="0a519-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="0a519-107">\<tracking></span></span>  
<span data-ttu-id="0a519-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="0a519-108">\<trackingProfile></span></span>  
<span data-ttu-id="0a519-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="0a519-109">\<workflow></span></span>  
<span data-ttu-id="0a519-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="0a519-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="0a519-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="0a519-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a519-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a519-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a519-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0a519-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0a519-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0a519-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a519-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="0a519-115">Attributes</span></span>  
  
|<span data-ttu-id="0a519-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="0a519-116">Attribute</span></span>|<span data-ttu-id="0a519-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0a519-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a519-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="0a519-118">activityName</span></span>|<span data-ttu-id="0a519-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="0a519-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="0a519-120">name</span><span class="sxs-lookup"><span data-stu-id="0a519-120">name</span></span>|<span data-ttu-id="0a519-121">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="0a519-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a519-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0a519-122">Child Elements</span></span>  
 <span data-ttu-id="0a519-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="0a519-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a519-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0a519-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0a519-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a519-125">Element</span></span>|<span data-ttu-id="0a519-126">Popis</span><span class="sxs-lookup"><span data-stu-id="0a519-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a519-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="0a519-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="0a519-128">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="0a519-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a519-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a519-129">See Also</span></span>  
 <span data-ttu-id="0a519-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0a519-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="0a519-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="0a519-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>         
 [<span data-ttu-id="0a519-132">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="0a519-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="0a519-133">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="0a519-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
