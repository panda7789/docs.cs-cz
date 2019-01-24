---
title: '&lt;bookmarkResumptionQueries&gt; služby WCF'
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 80d1c1e4bc61972d44c27bcbdd0eba14d97c2d6c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493947"
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="fd5f6-102">&lt;bookmarkResumptionQueries&gt; služby WCF</span><span class="sxs-lookup"><span data-stu-id="fd5f6-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
  
<span data-ttu-id="fd5f6-103">Představuje kolekci dotazů, které se používají ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fd5f6-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fd5f6-104">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="fd5f6-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="fd5f6-105">Další informace o sledování profil dotazy naleznete v tématu [sledování profilů](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="fd5f6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="fd5f6-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fd5f6-106">\<system.serviceModel></span></span>  
<span data-ttu-id="fd5f6-107">\<sledování ></span><span class="sxs-lookup"><span data-stu-id="fd5f6-107">\<tracking></span></span>  
<span data-ttu-id="fd5f6-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="fd5f6-108">\<profiles></span></span>  
<span data-ttu-id="fd5f6-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="fd5f6-109">\<trackingProfile></span></span>  
<span data-ttu-id="fd5f6-110">\<pracovní postup ></span><span class="sxs-lookup"><span data-stu-id="fd5f6-110">\<workflow></span></span>  
<span data-ttu-id="fd5f6-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="fd5f6-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="fd5f6-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="fd5f6-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5f6-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd5f6-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd5f6-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fd5f6-114">Attributes and elements</span></span>  
  
<span data-ttu-id="fd5f6-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fd5f6-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd5f6-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="fd5f6-116">Attributes</span></span>  
  
<span data-ttu-id="fd5f6-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="fd5f6-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fd5f6-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="fd5f6-118">Child elements</span></span>  
  
|<span data-ttu-id="fd5f6-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="fd5f6-119">Element</span></span>|<span data-ttu-id="fd5f6-120">Popis</span><span class="sxs-lookup"><span data-stu-id="fd5f6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd5f6-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="fd5f6-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="fd5f6-122">Dotaz, který se používá ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fd5f6-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="fd5f6-123">Dotaz, je nezbytné pro sledování účastníka přihlásit k odběru záložku obnovení záznamů.</span><span class="sxs-lookup"><span data-stu-id="fd5f6-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd5f6-124">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="fd5f6-124">Parent elements</span></span>  
  
|<span data-ttu-id="fd5f6-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="fd5f6-125">Element</span></span>|<span data-ttu-id="fd5f6-126">Popis</span><span class="sxs-lookup"><span data-stu-id="fd5f6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd5f6-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="fd5f6-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="fd5f6-128">Konfigurace element, který obsahuje všechny dotazy týkající se konkrétního pracovního postupu identifikovaný `activityDefinitionId` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fd5f6-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd5f6-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd5f6-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fd5f6-130">Sledování a trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="fd5f6-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fd5f6-131">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="fd5f6-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
