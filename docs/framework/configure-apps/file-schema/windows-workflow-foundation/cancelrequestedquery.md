---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: d9c3f91edb41bd034bcd978b075d62f74b6e308d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945886"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="b86fc-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="b86fc-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="b86fc-102">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="b86fc-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b86fc-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="b86fc-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="b86fc-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b86fc-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b86fc-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b86fc-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b86fc-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="b86fc-106">\<tracking></span></span>  
<span data-ttu-id="b86fc-107">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b86fc-107">\<trackingProfile></span></span>  
<span data-ttu-id="b86fc-108">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b86fc-108">\<workflow></span></span>  
<span data-ttu-id="b86fc-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="b86fc-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="b86fc-110">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="b86fc-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b86fc-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b86fc-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b86fc-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b86fc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b86fc-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b86fc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b86fc-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="b86fc-114">Attributes</span></span>  
  
|<span data-ttu-id="b86fc-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="b86fc-115">Attribute</span></span>|<span data-ttu-id="b86fc-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b86fc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b86fc-117">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="b86fc-117">activityName</span></span>|<span data-ttu-id="b86fc-118">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="b86fc-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="b86fc-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="b86fc-119">childActivityName</span></span>|<span data-ttu-id="b86fc-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="b86fc-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b86fc-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b86fc-121">Child Elements</span></span>  
 <span data-ttu-id="b86fc-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="b86fc-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b86fc-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b86fc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b86fc-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="b86fc-124">Element</span></span>|<span data-ttu-id="b86fc-125">Popis</span><span class="sxs-lookup"><span data-stu-id="b86fc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b86fc-126">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="b86fc-126">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="b86fc-127">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="b86fc-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b86fc-128">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="b86fc-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b86fc-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b86fc-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b86fc-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="b86fc-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b86fc-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="b86fc-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
