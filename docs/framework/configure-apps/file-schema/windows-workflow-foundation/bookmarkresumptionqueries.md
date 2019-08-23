---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: f048612673a9b6b69c3cdded6526c76359c444e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945980"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="f97a0-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="f97a0-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="f97a0-102">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f97a0-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f97a0-103">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="f97a0-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="f97a0-104">Další informace o sledování dotazů profilů najdete v tématu [sledování profilů](../../../windows-workflow-foundation/tracking-profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="f97a0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f97a0-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f97a0-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f97a0-106">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="f97a0-106">\<tracking></span></span>  
<span data-ttu-id="f97a0-107">\<Profil TrackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f97a0-107">\<trackingProfile></span></span>  
<span data-ttu-id="f97a0-108">\<> pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="f97a0-108">\<workflow></span></span>  
<span data-ttu-id="f97a0-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="f97a0-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="f97a0-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="f97a0-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f97a0-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f97a0-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f97a0-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f97a0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f97a0-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f97a0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f97a0-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="f97a0-114">Attributes</span></span>  
 <span data-ttu-id="f97a0-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="f97a0-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f97a0-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f97a0-116">Child Elements</span></span>  
  
|<span data-ttu-id="f97a0-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="f97a0-117">Element</span></span>|<span data-ttu-id="f97a0-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f97a0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f97a0-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="f97a0-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="f97a0-120">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f97a0-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f97a0-121">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="f97a0-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f97a0-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f97a0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f97a0-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="f97a0-123">Element</span></span>|<span data-ttu-id="f97a0-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f97a0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f97a0-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="f97a0-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="f97a0-126">Prvek konfigurace, který obsahuje všechny dotazy pro konkrétní pracovní postup identifikovaný vlastností **ID definice aktivity**</span><span class="sxs-lookup"><span data-stu-id="f97a0-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f97a0-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f97a0-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f97a0-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="f97a0-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f97a0-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="f97a0-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
