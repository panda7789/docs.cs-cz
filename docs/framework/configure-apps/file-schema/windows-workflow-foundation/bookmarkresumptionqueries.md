---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fb3cf8457dc19081e9eb51091453764513da8ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="80410-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="80410-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="80410-103">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="80410-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="80410-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="80410-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="80410-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="80410-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="80410-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="80410-106">\<system.serviceModel></span></span>  
<span data-ttu-id="80410-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="80410-107">\<tracking></span></span>  
<span data-ttu-id="80410-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="80410-108">\<trackingProfile></span></span>  
<span data-ttu-id="80410-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="80410-109">\<workflow></span></span>  
<span data-ttu-id="80410-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="80410-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="80410-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="80410-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80410-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80410-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80410-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="80410-113">Attributes and Elements</span></span>  
 <span data-ttu-id="80410-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="80410-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80410-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="80410-115">Attributes</span></span>  
 <span data-ttu-id="80410-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="80410-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80410-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="80410-117">Child Elements</span></span>  
  
|<span data-ttu-id="80410-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="80410-118">Element</span></span>|<span data-ttu-id="80410-119">Popis</span><span class="sxs-lookup"><span data-stu-id="80410-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80410-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="80410-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="80410-121">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="80410-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="80410-122">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="80410-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80410-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="80410-123">Parent Elements</span></span>  
  
|<span data-ttu-id="80410-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="80410-124">Element</span></span>|<span data-ttu-id="80410-125">Popis</span><span class="sxs-lookup"><span data-stu-id="80410-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80410-126">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="80410-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="80410-127">Konfigurace elementu, který obsahuje všechny dotazy pro konkrétní pracovní tok identifikovaný **activityDefinitionId** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="80410-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80410-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="80410-128">See Also</span></span>  
 <span data-ttu-id="80410-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="80410-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="80410-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="80410-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="80410-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="80410-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="80410-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="80410-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
