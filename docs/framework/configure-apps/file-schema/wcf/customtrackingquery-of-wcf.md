---
title: "&lt;customTrackingQuery&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 350ebbd0cc7be66f27ed2f70e1369e249267f359
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="94d4e-102">&lt;customTrackingQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="94d4e-102">&lt;customTrackingQuery&gt; of WCF</span></span>
<span data-ttu-id="94d4e-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="94d4e-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="94d4e-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="94d4e-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="94d4e-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="94d4e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="94d4e-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="94d4e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="94d4e-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="94d4e-107">\<tracking></span></span>  
<span data-ttu-id="94d4e-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="94d4e-108">\<trackingProfile></span></span>  
<span data-ttu-id="94d4e-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="94d4e-109">\<workflow></span></span>  
<span data-ttu-id="94d4e-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="94d4e-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="94d4e-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="94d4e-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d4e-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94d4e-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94d4e-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="94d4e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="94d4e-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="94d4e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94d4e-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="94d4e-115">Attributes</span></span>  
  
|<span data-ttu-id="94d4e-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="94d4e-116">Attribute</span></span>|<span data-ttu-id="94d4e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="94d4e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94d4e-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="94d4e-118">activityName</span></span>|<span data-ttu-id="94d4e-119">Řetězec, který určuje název aktivity, která generovala záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="94d4e-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="94d4e-120">name</span><span class="sxs-lookup"><span data-stu-id="94d4e-120">name</span></span>|<span data-ttu-id="94d4e-121">Řetězec, který určuje název záznamu vlastní sledování, které jsou vydávány.</span><span class="sxs-lookup"><span data-stu-id="94d4e-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94d4e-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="94d4e-122">Child Elements</span></span>  
 <span data-ttu-id="94d4e-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="94d4e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94d4e-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="94d4e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="94d4e-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="94d4e-125">Element</span></span>|<span data-ttu-id="94d4e-126">Popis</span><span class="sxs-lookup"><span data-stu-id="94d4e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94d4e-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="94d4e-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="94d4e-128">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="94d4e-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94d4e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="94d4e-129">See Also</span></span>  
 <span data-ttu-id="94d4e-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="94d4e-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>      
 <span data-ttu-id="94d4e-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="94d4e-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="94d4e-132">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="94d4e-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="94d4e-133">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="94d4e-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
