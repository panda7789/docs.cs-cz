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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19a4a58a15db72129f17655e7043f2ee3ae7ffa2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="6d679-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="6d679-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="6d679-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="6d679-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="6d679-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="6d679-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="6d679-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6d679-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="6d679-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6d679-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6d679-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="6d679-107">\<tracking></span></span>  
<span data-ttu-id="6d679-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6d679-108">\<trackingProfile></span></span>  
<span data-ttu-id="6d679-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="6d679-109">\<workflow></span></span>  
<span data-ttu-id="6d679-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="6d679-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d679-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d679-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d679-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6d679-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6d679-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6d679-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d679-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d679-114">Attributes</span></span>  
 <span data-ttu-id="6d679-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="6d679-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6d679-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6d679-116">Child Elements</span></span>  
  
|<span data-ttu-id="6d679-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d679-117">Element</span></span>|<span data-ttu-id="6d679-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6d679-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d679-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="6d679-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="6d679-120">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="6d679-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d679-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6d679-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6d679-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d679-122">Element</span></span>|<span data-ttu-id="6d679-123">Popis</span><span class="sxs-lookup"><span data-stu-id="6d679-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d679-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="6d679-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="6d679-125">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **activityDefinitionId** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6d679-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d679-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d679-126">See Also</span></span>  
 <span data-ttu-id="6d679-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6d679-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="6d679-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6d679-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="6d679-129">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="6d679-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6d679-130">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="6d679-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
