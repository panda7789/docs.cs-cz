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
ms.workload: dotnet
ms.openlocfilehash: 0c9ad0f766256d6507775c2cca1b9d54b474abc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="57386-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="57386-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="57386-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="57386-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="57386-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="57386-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="57386-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="57386-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="57386-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="57386-106">\<system.serviceModel></span></span>  
<span data-ttu-id="57386-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="57386-107">\<tracking></span></span>  
<span data-ttu-id="57386-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="57386-108">\<trackingProfile></span></span>  
<span data-ttu-id="57386-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="57386-109">\<workflow></span></span>  
<span data-ttu-id="57386-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="57386-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="57386-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="57386-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57386-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57386-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57386-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="57386-113">Attributes and Elements</span></span>  
 <span data-ttu-id="57386-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="57386-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57386-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="57386-115">Attributes</span></span>  
  
|<span data-ttu-id="57386-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="57386-116">Attribute</span></span>|<span data-ttu-id="57386-117">Popis</span><span class="sxs-lookup"><span data-stu-id="57386-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57386-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="57386-118">activityName</span></span>|<span data-ttu-id="57386-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="57386-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="57386-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="57386-120">childActivityName</span></span>|<span data-ttu-id="57386-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="57386-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57386-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="57386-122">Child Elements</span></span>  
 <span data-ttu-id="57386-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="57386-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57386-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="57386-124">Parent Elements</span></span>  
  
|<span data-ttu-id="57386-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="57386-125">Element</span></span>|<span data-ttu-id="57386-126">Popis</span><span class="sxs-lookup"><span data-stu-id="57386-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57386-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="57386-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="57386-128">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="57386-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="57386-129">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="57386-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57386-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="57386-130">See Also</span></span>  
 <span data-ttu-id="57386-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="57386-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="57386-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="57386-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="57386-133">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="57386-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="57386-134">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="57386-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
