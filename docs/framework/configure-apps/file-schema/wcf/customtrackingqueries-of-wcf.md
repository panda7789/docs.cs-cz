---
title: <customTrackingQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: abc0c7dfb426338ec6bca61b0a4b87754bb63588
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925942"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="bea93-102">\<customTrackingQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="bea93-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="bea93-103">Představuje kolekci dotazů, které se používají ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="bea93-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="bea93-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="bea93-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="bea93-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="bea93-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="bea93-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bea93-106">\<system.serviceModel></span></span>  
<span data-ttu-id="bea93-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="bea93-107">\<tracking></span></span>  
<span data-ttu-id="bea93-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="bea93-108">\<profiles></span></span>  
<span data-ttu-id="bea93-109">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="bea93-109">\<trackingProfile></span></span>  
<span data-ttu-id="bea93-110">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bea93-110">\<workflow></span></span>  
<span data-ttu-id="bea93-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="bea93-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea93-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bea93-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bea93-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bea93-113">Attributes and elements</span></span>

<span data-ttu-id="bea93-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bea93-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bea93-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="bea93-115">Attributes</span></span>

<span data-ttu-id="bea93-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="bea93-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="bea93-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="bea93-117">Child elements</span></span>
  
|<span data-ttu-id="bea93-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="bea93-118">Element</span></span>|<span data-ttu-id="bea93-119">Popis</span><span class="sxs-lookup"><span data-stu-id="bea93-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bea93-120">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="bea93-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="bea93-121">Dotaz, který se používá ke sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="bea93-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bea93-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="bea93-122">Parent elements</span></span>  
  
|<span data-ttu-id="bea93-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="bea93-123">Element</span></span>|<span data-ttu-id="bea93-124">Popis</span><span class="sxs-lookup"><span data-stu-id="bea93-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bea93-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="bea93-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="bea93-126">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bea93-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bea93-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bea93-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bea93-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bea93-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bea93-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="bea93-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
