---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 5f2e46d5e4cdd64c37219476790b9ff92c606b6b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215310"
---
# <a name="cancelrequestedquery"></a><span data-ttu-id="6e6a8-101">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="6e6a8-101">\<cancelRequestedQuery></span></span>
<span data-ttu-id="6e6a8-102">Představuje dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="6e6a8-102">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6e6a8-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="6e6a8-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="6e6a8-104">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6e6a8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="6e6a8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6e6a8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="6e6a8-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="6e6a8-106">\<tracking></span></span>  
<span data-ttu-id="6e6a8-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="6e6a8-107">\<trackingProfile></span></span>  
<span data-ttu-id="6e6a8-108">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="6e6a8-108">\<workflow></span></span>  
<span data-ttu-id="6e6a8-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="6e6a8-109">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="6e6a8-110">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="6e6a8-110">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e6a8-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e6a8-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e6a8-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6e6a8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6e6a8-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6e6a8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e6a8-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="6e6a8-114">Attributes</span></span>  
  
|<span data-ttu-id="6e6a8-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="6e6a8-115">Attribute</span></span>|<span data-ttu-id="6e6a8-116">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6a8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e6a8-117">Název aktivity activityName</span><span class="sxs-lookup"><span data-stu-id="6e6a8-117">activityName</span></span>|<span data-ttu-id="6e6a8-118">Řetězec, který určuje název aktivity, která žádá o zrušení.</span><span class="sxs-lookup"><span data-stu-id="6e6a8-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="6e6a8-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="6e6a8-119">childActivityName</span></span>|<span data-ttu-id="6e6a8-120">Řetězec, který určuje název podřízenou aktivitu, pro který bylo zrušení požadováno.</span><span class="sxs-lookup"><span data-stu-id="6e6a8-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e6a8-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6e6a8-121">Child Elements</span></span>  
 <span data-ttu-id="6e6a8-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="6e6a8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e6a8-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6e6a8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6e6a8-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e6a8-124">Element</span></span>|<span data-ttu-id="6e6a8-125">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6a8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e6a8-126">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="6e6a8-126">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="6e6a8-127">Představuje seznam konfigurační prvky, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="6e6a8-127">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6e6a8-128">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="6e6a8-128">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e6a8-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e6a8-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6e6a8-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6e6a8-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6e6a8-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="6e6a8-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
