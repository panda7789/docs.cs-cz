---
title: '&lt;bookmarkResumptionQuery&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 083b42efdd2b10dad870b6590fc20331a090f8aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748253"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="862cb-102">&lt;bookmarkResumptionQuery&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="862cb-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="862cb-103">Představuje dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="862cb-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="862cb-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="862cb-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="862cb-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="862cb-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="862cb-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="862cb-106">\<system.serviceModel></span></span>  
<span data-ttu-id="862cb-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="862cb-107">\<tracking></span></span>  
<span data-ttu-id="862cb-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="862cb-108">\<trackingProfile></span></span>  
<span data-ttu-id="862cb-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="862cb-109">\<workflow></span></span>  
<span data-ttu-id="862cb-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="862cb-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="862cb-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="862cb-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="862cb-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="862cb-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="862cb-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="862cb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="862cb-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="862cb-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="862cb-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="862cb-115">Attributes</span></span>  
  
|<span data-ttu-id="862cb-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="862cb-116">Attribute</span></span>|<span data-ttu-id="862cb-117">Popis</span><span class="sxs-lookup"><span data-stu-id="862cb-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="862cb-118">name</span><span class="sxs-lookup"><span data-stu-id="862cb-118">name</span></span>|<span data-ttu-id="862cb-119">Řetězec, který určuje název záložky záznam, který chcete-li se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="862cb-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="862cb-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="862cb-120">Child Elements</span></span>  
 <span data-ttu-id="862cb-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="862cb-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="862cb-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="862cb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="862cb-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="862cb-123">Element</span></span>|<span data-ttu-id="862cb-124">Popis</span><span class="sxs-lookup"><span data-stu-id="862cb-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="862cb-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="862cb-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="862cb-126">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="862cb-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="862cb-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="862cb-127">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="862cb-128">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="862cb-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="862cb-129">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="862cb-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
