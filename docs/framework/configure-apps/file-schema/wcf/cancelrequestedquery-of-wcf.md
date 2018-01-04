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
ms.workload: dotnet
ms.openlocfilehash: 2af49aab76e82a97aeee92b4799b91011f70c509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="38fda-102">&lt;cancelRequestedQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="38fda-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="38fda-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="38fda-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="38fda-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="38fda-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="38fda-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="38fda-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="38fda-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="38fda-106">\<system.serviceModel></span></span>  
<span data-ttu-id="38fda-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="38fda-107">\<tracking></span></span>  
<span data-ttu-id="38fda-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="38fda-108">\<trackingProfile></span></span>  
<span data-ttu-id="38fda-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="38fda-109">\<workflow></span></span>  
<span data-ttu-id="38fda-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="38fda-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="38fda-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="38fda-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38fda-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38fda-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38fda-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="38fda-113">Attributes and Elements</span></span>  
 <span data-ttu-id="38fda-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="38fda-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38fda-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="38fda-115">Attributes</span></span>  
  
|<span data-ttu-id="38fda-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="38fda-116">Attribute</span></span>|<span data-ttu-id="38fda-117">Popis</span><span class="sxs-lookup"><span data-stu-id="38fda-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38fda-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="38fda-118">activityName</span></span>|<span data-ttu-id="38fda-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="38fda-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="38fda-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="38fda-120">childActivityName</span></span>|<span data-ttu-id="38fda-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="38fda-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38fda-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="38fda-122">Child Elements</span></span>  
 <span data-ttu-id="38fda-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="38fda-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38fda-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="38fda-124">Parent Elements</span></span>  
  
|<span data-ttu-id="38fda-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="38fda-125">Element</span></span>|<span data-ttu-id="38fda-126">Popis</span><span class="sxs-lookup"><span data-stu-id="38fda-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38fda-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="38fda-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="38fda-128">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="38fda-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="38fda-129">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="38fda-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38fda-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="38fda-130">See Also</span></span>  
 <span data-ttu-id="38fda-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="38fda-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="38fda-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="38fda-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="38fda-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="38fda-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="38fda-134">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="38fda-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
