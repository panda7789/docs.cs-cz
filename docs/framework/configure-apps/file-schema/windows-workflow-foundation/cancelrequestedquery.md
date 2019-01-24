---
title: '&lt;cancelRequestedQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: a3d24536589288ce9585901f3d955075bc856c97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520305"
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="76bec-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="76bec-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="76bec-103">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="76bec-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="76bec-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="76bec-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="76bec-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="76bec-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="76bec-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="76bec-106">\<system.serviceModel></span></span>  
<span data-ttu-id="76bec-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="76bec-107">\<tracking></span></span>  
<span data-ttu-id="76bec-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="76bec-108">\<trackingProfile></span></span>  
<span data-ttu-id="76bec-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="76bec-109">\<workflow></span></span>  
<span data-ttu-id="76bec-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="76bec-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="76bec-111">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="76bec-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76bec-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76bec-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76bec-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76bec-113">Attributes and Elements</span></span>  
 <span data-ttu-id="76bec-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76bec-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76bec-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="76bec-115">Attributes</span></span>  
  
|<span data-ttu-id="76bec-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="76bec-116">Attribute</span></span>|<span data-ttu-id="76bec-117">Popis</span><span class="sxs-lookup"><span data-stu-id="76bec-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76bec-118">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="76bec-118">activityName</span></span>|<span data-ttu-id="76bec-119">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="76bec-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="76bec-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="76bec-120">childActivityName</span></span>|<span data-ttu-id="76bec-121">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="76bec-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76bec-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76bec-122">Child Elements</span></span>  
 <span data-ttu-id="76bec-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="76bec-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76bec-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76bec-124">Parent Elements</span></span>  
  
|<span data-ttu-id="76bec-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="76bec-125">Element</span></span>|<span data-ttu-id="76bec-126">Popis</span><span class="sxs-lookup"><span data-stu-id="76bec-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76bec-127">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="76bec-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="76bec-128">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="76bec-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="76bec-129">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="76bec-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76bec-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76bec-130">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="76bec-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="76bec-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="76bec-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="76bec-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
