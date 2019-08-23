---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 429940b2ed69d8be497626f634a21adca540b529
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945838"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="6e6db-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="6e6db-101">\<customTrackingQueries></span></span>
<span data-ttu-id="6e6db-102">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="6e6db-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="6e6db-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="6e6db-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="6e6db-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="6e6db-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="6e6db-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6e6db-105">\<system.serviceModel></span></span>  
<span data-ttu-id="6e6db-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="6e6db-106">\<tracking></span></span>  
<span data-ttu-id="6e6db-107">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6e6db-107">\<trackingProfile></span></span>  
<span data-ttu-id="6e6db-108">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6e6db-108">\<workflow></span></span>  
<span data-ttu-id="6e6db-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="6e6db-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e6db-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e6db-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e6db-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6e6db-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6e6db-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6e6db-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e6db-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="6e6db-113">Attributes</span></span>  
 <span data-ttu-id="6e6db-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="6e6db-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6e6db-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6e6db-115">Child Elements</span></span>  
  
|<span data-ttu-id="6e6db-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e6db-116">Element</span></span>|<span data-ttu-id="6e6db-117">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6db-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e6db-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="6e6db-118">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="6e6db-119">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="6e6db-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e6db-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6e6db-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6e6db-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e6db-121">Element</span></span>|<span data-ttu-id="6e6db-122">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6db-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e6db-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="6e6db-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="6e6db-124">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="6e6db-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e6db-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e6db-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6e6db-126">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="6e6db-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6e6db-127">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="6e6db-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
