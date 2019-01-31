---
title: <bookmarkResumptionQuery> služby WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 38c87cefc49821b03d119299ef60e3fbbad21d7e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255113"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="ff86b-102">\<bookmarkResumptionQuery> of WCF</span><span class="sxs-lookup"><span data-stu-id="ff86b-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="ff86b-103">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff86b-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ff86b-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="ff86b-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="ff86b-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ff86b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="ff86b-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ff86b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ff86b-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="ff86b-107">\<tracking></span></span>  
<span data-ttu-id="ff86b-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="ff86b-108">\<profiles></span></span>  
<span data-ttu-id="ff86b-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ff86b-109">\<trackingProfile></span></span>  
<span data-ttu-id="ff86b-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="ff86b-110">\<workflow></span></span>  
<span data-ttu-id="ff86b-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="ff86b-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="ff86b-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="ff86b-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff86b-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff86b-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff86b-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ff86b-114">Attributes and elements</span></span>

<span data-ttu-id="ff86b-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ff86b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff86b-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="ff86b-116">Attributes</span></span>  
  
|<span data-ttu-id="ff86b-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="ff86b-117">Attribute</span></span>|<span data-ttu-id="ff86b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ff86b-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="ff86b-119">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="ff86b-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff86b-120">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ff86b-120">Child elements</span></span>

<span data-ttu-id="ff86b-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="ff86b-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="ff86b-122">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="ff86b-122">Parent elements</span></span>  
  
|<span data-ttu-id="ff86b-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="ff86b-123">Element</span></span>|<span data-ttu-id="ff86b-124">Popis</span><span class="sxs-lookup"><span data-stu-id="ff86b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff86b-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="ff86b-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="ff86b-126">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ff86b-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff86b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff86b-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ff86b-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="ff86b-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ff86b-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="ff86b-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
