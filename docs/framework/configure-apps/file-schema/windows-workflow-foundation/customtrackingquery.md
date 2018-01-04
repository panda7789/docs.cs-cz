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
ms.workload: dotnet
ms.openlocfilehash: 7d4427ad1b45ceade29b8859d30eba746a70a27d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="88ef7-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="88ef7-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="88ef7-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="88ef7-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="88ef7-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="88ef7-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="88ef7-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="88ef7-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="88ef7-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="88ef7-106">\<system.serviceModel></span></span>  
<span data-ttu-id="88ef7-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="88ef7-107">\<tracking></span></span>  
<span data-ttu-id="88ef7-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="88ef7-108">\<trackingProfile></span></span>  
<span data-ttu-id="88ef7-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="88ef7-109">\<workflow></span></span>  
<span data-ttu-id="88ef7-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="88ef7-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="88ef7-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="88ef7-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88ef7-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88ef7-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88ef7-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="88ef7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="88ef7-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="88ef7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88ef7-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="88ef7-115">Attributes</span></span>  
  
|<span data-ttu-id="88ef7-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="88ef7-116">Attribute</span></span>|<span data-ttu-id="88ef7-117">Popis</span><span class="sxs-lookup"><span data-stu-id="88ef7-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88ef7-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="88ef7-118">activityName</span></span>|<span data-ttu-id="88ef7-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="88ef7-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="88ef7-120">name</span><span class="sxs-lookup"><span data-stu-id="88ef7-120">name</span></span>|<span data-ttu-id="88ef7-121">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="88ef7-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88ef7-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="88ef7-122">Child Elements</span></span>  
 <span data-ttu-id="88ef7-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="88ef7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88ef7-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="88ef7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="88ef7-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="88ef7-125">Element</span></span>|<span data-ttu-id="88ef7-126">Popis</span><span class="sxs-lookup"><span data-stu-id="88ef7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88ef7-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="88ef7-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="88ef7-128">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="88ef7-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88ef7-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="88ef7-129">See Also</span></span>  
 <span data-ttu-id="88ef7-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="88ef7-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="88ef7-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="88ef7-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>         
 [<span data-ttu-id="88ef7-132">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="88ef7-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="88ef7-133">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="88ef7-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
