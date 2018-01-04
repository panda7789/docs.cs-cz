---
title: "&lt;customTrackingQueries&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a64a155f435fb61c19a50f1b047c7dd28b603716
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="e3735-102">&lt;customTrackingQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="e3735-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="e3735-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="e3735-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="e3735-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="e3735-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="e3735-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e3735-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="e3735-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e3735-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e3735-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="e3735-107">\<tracking></span></span>  
<span data-ttu-id="e3735-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e3735-108">\<trackingProfile></span></span>  
<span data-ttu-id="e3735-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="e3735-109">\<workflow></span></span>  
<span data-ttu-id="e3735-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="e3735-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3735-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3735-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3735-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e3735-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e3735-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e3735-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3735-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="e3735-114">Attributes</span></span>  
 <span data-ttu-id="e3735-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="e3735-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e3735-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e3735-116">Child Elements</span></span>  
  
|<span data-ttu-id="e3735-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3735-117">Element</span></span>|<span data-ttu-id="e3735-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e3735-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3735-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="e3735-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="e3735-120">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="e3735-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3735-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e3735-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e3735-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="e3735-122">Element</span></span>|<span data-ttu-id="e3735-123">Popis</span><span class="sxs-lookup"><span data-stu-id="e3735-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3735-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="e3735-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e3735-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e3735-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3735-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3735-126">See Also</span></span>  
 <span data-ttu-id="e3735-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e3735-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e3735-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e3735-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e3735-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e3735-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e3735-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="e3735-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
