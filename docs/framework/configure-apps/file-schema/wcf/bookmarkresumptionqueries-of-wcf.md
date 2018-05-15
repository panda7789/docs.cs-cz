---
title: '&lt;bookmarkResumptionQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 8a83f521e444838b6495221c00211710dd99ab6b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="9b98d-102">&lt;bookmarkResumptionQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="9b98d-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="9b98d-103">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9b98d-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="9b98d-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="9b98d-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="9b98d-105">Další informace o sledování profil dotazů najdete v tématu [sledování profily](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9b98d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="9b98d-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9b98d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="9b98d-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="9b98d-107">\<tracking></span></span>  
<span data-ttu-id="9b98d-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9b98d-108">\<trackingProfile></span></span>  
<span data-ttu-id="9b98d-109">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9b98d-109">\<workflow></span></span>  
<span data-ttu-id="9b98d-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="9b98d-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="9b98d-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="9b98d-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b98d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b98d-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b98d-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9b98d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9b98d-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9b98d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b98d-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="9b98d-115">Attributes</span></span>  
 <span data-ttu-id="9b98d-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="9b98d-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9b98d-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9b98d-117">Child Elements</span></span>  
  
|<span data-ttu-id="9b98d-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="9b98d-118">Element</span></span>|<span data-ttu-id="9b98d-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9b98d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b98d-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="9b98d-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="9b98d-121">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9b98d-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="9b98d-122">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="9b98d-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b98d-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9b98d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9b98d-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="9b98d-124">Element</span></span>|<span data-ttu-id="9b98d-125">Popis</span><span class="sxs-lookup"><span data-stu-id="9b98d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b98d-126">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="9b98d-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9b98d-127">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9b98d-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b98d-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b98d-128">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="9b98d-129">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="9b98d-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9b98d-130">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="9b98d-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
