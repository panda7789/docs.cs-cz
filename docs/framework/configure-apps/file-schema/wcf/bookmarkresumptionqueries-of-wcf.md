---
title: "&lt;bookmarkResumptionQueries&gt; služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c29f4c0cd92b2c4e8263e1893e7deefc2f14624a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="66972-102">&lt;bookmarkResumptionQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="66972-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="66972-103">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="66972-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="66972-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="66972-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="66972-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="66972-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="66972-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="66972-106">\<system.serviceModel></span></span>  
<span data-ttu-id="66972-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="66972-107">\<tracking></span></span>  
<span data-ttu-id="66972-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="66972-108">\<trackingProfile></span></span>  
<span data-ttu-id="66972-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="66972-109">\<workflow></span></span>  
<span data-ttu-id="66972-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="66972-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="66972-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="66972-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66972-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66972-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="66972-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="66972-113">Attributes and Elements</span></span>  
 <span data-ttu-id="66972-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="66972-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66972-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="66972-115">Attributes</span></span>  
 <span data-ttu-id="66972-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="66972-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="66972-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="66972-117">Child Elements</span></span>  
  
|<span data-ttu-id="66972-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="66972-118">Element</span></span>|<span data-ttu-id="66972-119">Popis</span><span class="sxs-lookup"><span data-stu-id="66972-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66972-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="66972-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="66972-121">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="66972-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="66972-122">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="66972-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66972-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="66972-123">Parent Elements</span></span>  
  
|<span data-ttu-id="66972-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="66972-124">Element</span></span>|<span data-ttu-id="66972-125">Popis</span><span class="sxs-lookup"><span data-stu-id="66972-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66972-126">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="66972-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="66972-127">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="66972-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66972-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="66972-128">See Also</span></span>  
 <span data-ttu-id="66972-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="66972-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="66972-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="66972-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="66972-131">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="66972-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="66972-132">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="66972-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
