---
title: <bookmarkResumptionQuery> služby WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 38c87cefc49821b03d119299ef60e3fbbad21d7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704385"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="c2afe-102">\<bookmarkResumptionQuery> of WCF</span><span class="sxs-lookup"><span data-stu-id="c2afe-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="c2afe-103">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c2afe-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="c2afe-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="c2afe-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="c2afe-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c2afe-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="c2afe-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c2afe-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c2afe-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="c2afe-107">\<tracking></span></span>  
<span data-ttu-id="c2afe-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="c2afe-108">\<profiles></span></span>  
<span data-ttu-id="c2afe-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c2afe-109">\<trackingProfile></span></span>  
<span data-ttu-id="c2afe-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="c2afe-110">\<workflow></span></span>  
<span data-ttu-id="c2afe-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="c2afe-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="c2afe-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="c2afe-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2afe-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2afe-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2afe-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c2afe-114">Attributes and elements</span></span>

<span data-ttu-id="c2afe-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c2afe-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2afe-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="c2afe-116">Attributes</span></span>  
  
|<span data-ttu-id="c2afe-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="c2afe-117">Attribute</span></span>|<span data-ttu-id="c2afe-118">Popis</span><span class="sxs-lookup"><span data-stu-id="c2afe-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c2afe-119">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="c2afe-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2afe-120">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="c2afe-120">Child elements</span></span>

<span data-ttu-id="c2afe-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2afe-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="c2afe-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="c2afe-122">Parent elements</span></span>  
  
|<span data-ttu-id="c2afe-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2afe-123">Element</span></span>|<span data-ttu-id="c2afe-124">Popis</span><span class="sxs-lookup"><span data-stu-id="c2afe-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2afe-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="c2afe-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="c2afe-126">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c2afe-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2afe-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2afe-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c2afe-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c2afe-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c2afe-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="c2afe-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
