---
title: '&lt;customTrackingQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 241684a3a2344d6eb7f3b34c81c581b0ec5130f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="7013f-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="7013f-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="7013f-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="7013f-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="7013f-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="7013f-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="7013f-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7013f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7013f-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7013f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7013f-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="7013f-107">\<tracking></span></span>  
<span data-ttu-id="7013f-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7013f-108">\<trackingProfile></span></span>  
<span data-ttu-id="7013f-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="7013f-109">\<workflow></span></span>  
<span data-ttu-id="7013f-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="7013f-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7013f-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7013f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7013f-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7013f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7013f-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7013f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7013f-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="7013f-114">Attributes</span></span>  
 <span data-ttu-id="7013f-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="7013f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7013f-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7013f-116">Child Elements</span></span>  
  
|<span data-ttu-id="7013f-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="7013f-117">Element</span></span>|<span data-ttu-id="7013f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="7013f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7013f-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="7013f-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="7013f-120">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="7013f-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7013f-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7013f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7013f-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="7013f-122">Element</span></span>|<span data-ttu-id="7013f-123">Popis</span><span class="sxs-lookup"><span data-stu-id="7013f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7013f-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="7013f-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7013f-125">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **activityDefinitionId** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7013f-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7013f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7013f-126">See Also</span></span>  
 <span data-ttu-id="7013f-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7013f-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="7013f-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7013f-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="7013f-129">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="7013f-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7013f-130">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="7013f-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
