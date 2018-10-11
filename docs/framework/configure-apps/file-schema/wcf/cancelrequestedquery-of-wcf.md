---
title: '&lt;cancelRequestedQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 38d946a213131e8dcb6f4100d0ad67f7c167f342
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086398"
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="473eb-102">&lt;cancelRequestedQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="473eb-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="473eb-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="473eb-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="473eb-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="473eb-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="473eb-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="473eb-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="473eb-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="473eb-106">\<system.serviceModel></span></span>  
<span data-ttu-id="473eb-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="473eb-107">\<tracking></span></span>  
<span data-ttu-id="473eb-108">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="473eb-108">\<trackingProfile></span></span>  
<span data-ttu-id="473eb-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="473eb-109">\<workflow></span></span>  
<span data-ttu-id="473eb-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="473eb-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="473eb-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="473eb-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="473eb-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="473eb-112">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="473eb-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="473eb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="473eb-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="473eb-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="473eb-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="473eb-115">Attributes</span></span>  
  
|<span data-ttu-id="473eb-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="473eb-116">Attribute</span></span>|<span data-ttu-id="473eb-117">Popis</span><span class="sxs-lookup"><span data-stu-id="473eb-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="473eb-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="473eb-118">activityName</span></span>|<span data-ttu-id="473eb-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="473eb-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="473eb-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="473eb-120">childActivityName</span></span>|<span data-ttu-id="473eb-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="473eb-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="473eb-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="473eb-122">Child Elements</span></span>  
 <span data-ttu-id="473eb-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="473eb-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="473eb-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="473eb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="473eb-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="473eb-125">Element</span></span>|<span data-ttu-id="473eb-126">Popis</span><span class="sxs-lookup"><span data-stu-id="473eb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="473eb-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="473eb-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="473eb-128">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="473eb-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="473eb-129">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="473eb-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="473eb-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="473eb-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>     
 [<span data-ttu-id="473eb-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="473eb-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="473eb-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="473eb-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
