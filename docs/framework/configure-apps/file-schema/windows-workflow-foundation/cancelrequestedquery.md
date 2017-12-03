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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c6b1137e89799af34d0808d83e56c7c333a49635
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="a0268-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="a0268-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="a0268-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="a0268-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a0268-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="a0268-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="a0268-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a0268-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a0268-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a0268-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a0268-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="a0268-107">\<tracking></span></span>  
<span data-ttu-id="a0268-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a0268-108">\<trackingProfile></span></span>  
<span data-ttu-id="a0268-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="a0268-109">\<workflow></span></span>  
<span data-ttu-id="a0268-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="a0268-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="a0268-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="a0268-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0268-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0268-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0268-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a0268-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a0268-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a0268-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0268-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="a0268-115">Attributes</span></span>  
  
|<span data-ttu-id="a0268-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="a0268-116">Attribute</span></span>|<span data-ttu-id="a0268-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a0268-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0268-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="a0268-118">activityName</span></span>|<span data-ttu-id="a0268-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="a0268-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="a0268-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="a0268-120">childActivityName</span></span>|<span data-ttu-id="a0268-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="a0268-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0268-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a0268-122">Child Elements</span></span>  
 <span data-ttu-id="a0268-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="a0268-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0268-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a0268-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a0268-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0268-125">Element</span></span>|<span data-ttu-id="a0268-126">Popis</span><span class="sxs-lookup"><span data-stu-id="a0268-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0268-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="a0268-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="a0268-128">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="a0268-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a0268-129">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="a0268-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0268-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0268-130">See Also</span></span>  
 <span data-ttu-id="a0268-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a0268-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="a0268-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a0268-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="a0268-133">Pracovní postup sledování a trasování</span><span class="sxs-lookup"><span data-stu-id="a0268-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a0268-134">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="a0268-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
