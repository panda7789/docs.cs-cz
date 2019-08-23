---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 628dbf801cae5f61dc7d518c27df3380dd2d3d23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945952"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="70e8e-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="70e8e-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="70e8e-102">Představuje kolekci dotazů, které se používají ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="70e8e-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="70e8e-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru zrušit požadavek záznam objekty.</span><span class="sxs-lookup"><span data-stu-id="70e8e-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="70e8e-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="70e8e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="70e8e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="70e8e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="70e8e-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="70e8e-106">\<tracking></span></span>  
<span data-ttu-id="70e8e-107">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="70e8e-107">\<trackingProfile></span></span>  
<span data-ttu-id="70e8e-108">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="70e8e-108">\<workflow></span></span>  
<span data-ttu-id="70e8e-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="70e8e-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70e8e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70e8e-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70e8e-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="70e8e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="70e8e-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="70e8e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70e8e-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="70e8e-113">Attributes</span></span>  
 <span data-ttu-id="70e8e-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="70e8e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70e8e-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="70e8e-115">Child Elements</span></span>  
  
|<span data-ttu-id="70e8e-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="70e8e-116">Element</span></span>|<span data-ttu-id="70e8e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="70e8e-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70e8e-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="70e8e-118">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="70e8e-119">Dotaz, který se používá ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="70e8e-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70e8e-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="70e8e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="70e8e-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="70e8e-121">Element</span></span>|<span data-ttu-id="70e8e-122">Popis</span><span class="sxs-lookup"><span data-stu-id="70e8e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70e8e-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="70e8e-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="70e8e-124">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="70e8e-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70e8e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70e8e-125">See also</span></span>

- [<span data-ttu-id="70e8e-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="70e8e-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="70e8e-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="70e8e-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
