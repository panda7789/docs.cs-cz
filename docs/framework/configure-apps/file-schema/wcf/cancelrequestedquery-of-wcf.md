---
title: "&lt;cancelRequestedQuery&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6fc9df52c691e13802607714977f3aa778cde84e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="94364-102">&lt;cancelRequestedQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="94364-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="94364-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="94364-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="94364-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="94364-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="94364-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="94364-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="94364-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="94364-106">\<system.serviceModel></span></span>  
<span data-ttu-id="94364-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="94364-107">\<tracking></span></span>  
<span data-ttu-id="94364-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="94364-108">\<trackingProfile></span></span>  
<span data-ttu-id="94364-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="94364-109">\<workflow></span></span>  
<span data-ttu-id="94364-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="94364-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="94364-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="94364-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94364-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94364-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94364-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="94364-113">Attributes and Elements</span></span>  
 <span data-ttu-id="94364-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="94364-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94364-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="94364-115">Attributes</span></span>  
  
|<span data-ttu-id="94364-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="94364-116">Attribute</span></span>|<span data-ttu-id="94364-117">Popis</span><span class="sxs-lookup"><span data-stu-id="94364-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94364-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="94364-118">activityName</span></span>|<span data-ttu-id="94364-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="94364-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="94364-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="94364-120">childActivityName</span></span>|<span data-ttu-id="94364-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="94364-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94364-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="94364-122">Child Elements</span></span>  
 <span data-ttu-id="94364-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="94364-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94364-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="94364-124">Parent Elements</span></span>  
  
|<span data-ttu-id="94364-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="94364-125">Element</span></span>|<span data-ttu-id="94364-126">Popis</span><span class="sxs-lookup"><span data-stu-id="94364-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94364-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="94364-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="94364-128">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="94364-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="94364-129">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="94364-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94364-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="94364-130">See Also</span></span>  
 <span data-ttu-id="94364-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="94364-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="94364-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="94364-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="94364-133">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="94364-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="94364-134">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="94364-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
