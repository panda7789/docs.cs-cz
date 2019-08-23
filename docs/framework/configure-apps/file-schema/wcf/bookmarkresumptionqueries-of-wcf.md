---
title: <bookmarkResumptionQueries>služby WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 5ec9827e9862866096265da576c91b10573012d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919739"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="c8ad9-102">\<bookmarkResumptionQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="c8ad9-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="c8ad9-103">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c8ad9-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c8ad9-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="c8ad9-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="c8ad9-105">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c8ad9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="c8ad9-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c8ad9-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c8ad9-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="c8ad9-107">\<tracking></span></span>  
<span data-ttu-id="c8ad9-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="c8ad9-108">\<profiles></span></span>  
<span data-ttu-id="c8ad9-109">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c8ad9-109">\<trackingProfile></span></span>  
<span data-ttu-id="c8ad9-110">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c8ad9-110">\<workflow></span></span>  
<span data-ttu-id="c8ad9-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="c8ad9-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="c8ad9-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="c8ad9-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8ad9-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8ad9-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8ad9-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c8ad9-114">Attributes and elements</span></span>  
  
<span data-ttu-id="c8ad9-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c8ad9-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8ad9-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="c8ad9-116">Attributes</span></span>  
  
<span data-ttu-id="c8ad9-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="c8ad9-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c8ad9-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="c8ad9-118">Child elements</span></span>  
  
|<span data-ttu-id="c8ad9-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="c8ad9-119">Element</span></span>|<span data-ttu-id="c8ad9-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c8ad9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8ad9-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="c8ad9-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="c8ad9-122">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c8ad9-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c8ad9-123">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="c8ad9-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c8ad9-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="c8ad9-124">Parent elements</span></span>  
  
|<span data-ttu-id="c8ad9-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="c8ad9-125">Element</span></span>|<span data-ttu-id="c8ad9-126">Popis</span><span class="sxs-lookup"><span data-stu-id="c8ad9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8ad9-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c8ad9-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="c8ad9-128">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c8ad9-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8ad9-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8ad9-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c8ad9-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c8ad9-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c8ad9-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="c8ad9-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
