---
title: '&lt;cancelRequestedQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e1697b245f9ab61cab3e4b26b1756259f0eba9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="f2ec3-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="f2ec3-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="f2ec3-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="f2ec3-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="f2ec3-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="f2ec3-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="f2ec3-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f2ec3-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f2ec3-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f2ec3-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f2ec3-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="f2ec3-107">\<tracking></span></span>  
<span data-ttu-id="f2ec3-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f2ec3-108">\<trackingProfile></span></span>  
<span data-ttu-id="f2ec3-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="f2ec3-109">\<workflow></span></span>  
<span data-ttu-id="f2ec3-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="f2ec3-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="f2ec3-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="f2ec3-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2ec3-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2ec3-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2ec3-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f2ec3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f2ec3-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f2ec3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2ec3-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="f2ec3-115">Attributes</span></span>  
  
|<span data-ttu-id="f2ec3-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="f2ec3-116">Attribute</span></span>|<span data-ttu-id="f2ec3-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f2ec3-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2ec3-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="f2ec3-118">activityName</span></span>|<span data-ttu-id="f2ec3-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="f2ec3-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="f2ec3-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="f2ec3-120">childActivityName</span></span>|<span data-ttu-id="f2ec3-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="f2ec3-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2ec3-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f2ec3-122">Child Elements</span></span>  
 <span data-ttu-id="f2ec3-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="f2ec3-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2ec3-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f2ec3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f2ec3-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="f2ec3-125">Element</span></span>|<span data-ttu-id="f2ec3-126">Popis</span><span class="sxs-lookup"><span data-stu-id="f2ec3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2ec3-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="f2ec3-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="f2ec3-128">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="f2ec3-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="f2ec3-129">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="f2ec3-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2ec3-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2ec3-130">See Also</span></span>  
 <span data-ttu-id="f2ec3-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f2ec3-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f2ec3-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f2ec3-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="f2ec3-133">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="f2ec3-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f2ec3-134">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="f2ec3-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
