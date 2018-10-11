---
title: '&lt;bookmarkResumptionQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 07215347da19a05d5915296668d990853fdae646
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087788"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="57452-102">&lt;bookmarkResumptionQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="57452-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="57452-103">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="57452-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="57452-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="57452-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="57452-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="57452-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="57452-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="57452-106">\<system.serviceModel></span></span>  
<span data-ttu-id="57452-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="57452-107">\<tracking></span></span>  
<span data-ttu-id="57452-108">\<profil trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="57452-108">\<trackingProfile></span></span>  
<span data-ttu-id="57452-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="57452-109">\<workflow></span></span>  
<span data-ttu-id="57452-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="57452-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="57452-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="57452-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57452-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57452-112">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="57452-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="57452-113">Attributes and Elements</span></span>  
 <span data-ttu-id="57452-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="57452-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57452-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="57452-115">Attributes</span></span>  
  
|<span data-ttu-id="57452-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="57452-116">Attribute</span></span>|<span data-ttu-id="57452-117">Popis</span><span class="sxs-lookup"><span data-stu-id="57452-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57452-118">name</span><span class="sxs-lookup"><span data-stu-id="57452-118">name</span></span>|<span data-ttu-id="57452-119">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="57452-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57452-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="57452-120">Child Elements</span></span>  
 <span data-ttu-id="57452-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="57452-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57452-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="57452-122">Parent Elements</span></span>  
  
|<span data-ttu-id="57452-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="57452-123">Element</span></span>|<span data-ttu-id="57452-124">Popis</span><span class="sxs-lookup"><span data-stu-id="57452-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57452-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="57452-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="57452-126">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="57452-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57452-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="57452-127">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="57452-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="57452-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="57452-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="57452-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
