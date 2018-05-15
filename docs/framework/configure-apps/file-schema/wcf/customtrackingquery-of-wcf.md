---
title: '&lt;customTrackingQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: ed29ff039cd7fd4eb0acccea1b0adf8995c3e1f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="bc8d2-102">&lt;customTrackingQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="bc8d2-102">&lt;customTrackingQuery&gt; of WCF</span></span>
<span data-ttu-id="bc8d2-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="bc8d2-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="bc8d2-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="bc8d2-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="bc8d2-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bc8d2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="bc8d2-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bc8d2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="bc8d2-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="bc8d2-107">\<tracking></span></span>  
<span data-ttu-id="bc8d2-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="bc8d2-108">\<trackingProfile></span></span>  
<span data-ttu-id="bc8d2-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="bc8d2-109">\<workflow></span></span>  
<span data-ttu-id="bc8d2-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="bc8d2-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="bc8d2-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="bc8d2-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc8d2-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc8d2-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc8d2-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bc8d2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="bc8d2-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bc8d2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc8d2-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="bc8d2-115">Attributes</span></span>  
  
|<span data-ttu-id="bc8d2-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="bc8d2-116">Attribute</span></span>|<span data-ttu-id="bc8d2-117">Popis</span><span class="sxs-lookup"><span data-stu-id="bc8d2-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc8d2-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="bc8d2-118">activityName</span></span>|<span data-ttu-id="bc8d2-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="bc8d2-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="bc8d2-120">name</span><span class="sxs-lookup"><span data-stu-id="bc8d2-120">name</span></span>|<span data-ttu-id="bc8d2-121">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="bc8d2-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc8d2-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bc8d2-122">Child Elements</span></span>  
 <span data-ttu-id="bc8d2-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="bc8d2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc8d2-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bc8d2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bc8d2-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc8d2-125">Element</span></span>|<span data-ttu-id="bc8d2-126">Popis</span><span class="sxs-lookup"><span data-stu-id="bc8d2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc8d2-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="bc8d2-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="bc8d2-128">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="bc8d2-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc8d2-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc8d2-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>      
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="bc8d2-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bc8d2-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="bc8d2-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="bc8d2-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
