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
ms.openlocfilehash: 8a7a69b481da7315c8d26b00c171d030f77d9b63
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="d736c-102">&lt;customTrackingQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="d736c-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="d736c-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="d736c-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d736c-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="d736c-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="d736c-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d736c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="d736c-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d736c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d736c-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="d736c-107">\<tracking></span></span>  
<span data-ttu-id="d736c-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d736c-108">\<trackingProfile></span></span>  
<span data-ttu-id="d736c-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="d736c-109">\<workflow></span></span>  
<span data-ttu-id="d736c-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="d736c-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d736c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d736c-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d736c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d736c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d736c-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d736c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d736c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d736c-114">Attributes</span></span>  
 <span data-ttu-id="d736c-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="d736c-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d736c-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d736c-116">Child Elements</span></span>  
  
|<span data-ttu-id="d736c-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="d736c-117">Element</span></span>|<span data-ttu-id="d736c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d736c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d736c-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="d736c-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="d736c-120">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="d736c-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d736c-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d736c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d736c-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d736c-122">Element</span></span>|<span data-ttu-id="d736c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d736c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d736c-124">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="d736c-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="d736c-125">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d736c-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d736c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d736c-126">See Also</span></span>  
 <span data-ttu-id="d736c-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d736c-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="d736c-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d736c-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="d736c-129">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="d736c-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d736c-130">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="d736c-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
